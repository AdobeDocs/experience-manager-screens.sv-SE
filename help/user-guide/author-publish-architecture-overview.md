---
title: Författare och Publish - Översikt över arkitekturen
description: AEM Screens arkitektur liknar traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM författarinstans och sedan vidarebefordras till flera publiceringsinstanser.
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# Författare och Publish - Översikt över arkitekturen {#author-and-publish-architectural-overview}

På den här sidan beskrivs följande ämnen:

* **Introduktion till Publish-servrar**
* **Arkitekturöversikt**
* **Registreringsprocess**

## Förutsättningar {#prerequisites}

Innan du börjar med författarservrar och publiceringsservrar bör du ha kunskap om:

* **AEM topologi**
* **Skapa och hantera AEM Screens-projekt**
* **Device Registration Process**

>[!NOTE]
>
>Den här AEM Screens-funktionen är bara tillgänglig om du har AEM 6.4 Screens Feature Pack 2 installerat. Kontakta Adobe Support och begär åtkomst till detta funktionspaket. När du har behörighet hämtar du den från Package Share.

## Introduktion {#introduction}

AEM Screens arkitektur liknar traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM författarinstans och sedan vidarebefordras till flera publiceringsinstanser. Enheter på AEM Screens kan nu ansluta till en AEM publiceringsgrupp via en belastningsutjämnare. Det går att lägga till flera AEM publiceringsinstanser för att fortsätta att skala publiceringsgruppen.

*Till exempel* skickar en AEM Screens Content Author ett kommando i redigeringssystemet för en viss enhet. Enheten är konfigurerad för att interagera med en publiceringsgrupp. Eller interagera med en AEM Screens Content Author som får information om enheter som är konfigurerade att interagera med publiceringsgrupper.

I följande diagram visas både författarmiljön och publiceringsmiljön.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Arkitektur {#architectural-design}

Det finns fem arkitektoniska komponenter som underlättar denna lösning:

* ***Replikerar innehåll*** från författare till publicering för visning på enheter

* ***Återför*** binärt innehåll som replikeras från publiceringsmiljön (tas emot från enheter) till redigeringsmiljön.
* ***Skickar*** kommandon från författaren för att publicera via särskilda REST API:er.
* ***Meddelanden*** mellan publiceringsinstanser om du vill synkronisera uppdateringar och kommandon för enhetsinformation.
* ***Avsöker*** av författaren till publiceringsinstanser för att få enhetsinformation via specifika REST API:er.

### Replikering (framåt) av innehåll och konfigurationer {#replication-forward-of-content-and-configurations}

Standardreplikeringsagenter används för att replikera AEM Screens-kanalinnehåll, platskonfigurationer och enhetskonfigurationer. Med den här funktionen kan författare uppdatera innehållet i en kanal och eventuellt gå igenom någon sorts arbetsflöde för godkännande innan kanaluppdateringar publiceras. En replikeringsagent måste skapas för varje publiceringsinstans i publiceringsgruppen.

I följande diagram visas replikeringsprocessen:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>En replikeringsagent måste skapas för varje publiceringsinstans i publiceringsgruppen.

### Screens replikeringsagenter och kommandon {#screens-replication-agents-and-commands}

Anpassade Screens-specifika replikeringsagenter skapas för att skicka kommandon från författarinstansen till AEM Screens-enheten. De AEM Publish-instanserna fungerar som en mellanhand för att vidarebefordra dessa kommandon till enheten.

Med det här arbetsflödet kan författare fortsätta att hantera enheten, till exempel skicka enhetsuppdateringar och ta skärmbilder från redigeringsmiljön. AEM Screens replikeringsagenter har en anpassad transportkonfiguration, som vanliga replikeringsagenter.

### Meddelanden mellan Publish-instanser {#messaging-between-publish-instances}

Ofta är det bara meningen att ett kommando ska skickas till en enhet en gång. I en belastningsutjämnad publiceringsarkitektur är dock den publiceringsinstans som enheten ansluter till okänd.

Därför skickar författarinstansen meddelandet till alla Publish-instanser. Sedan bör bara ett meddelande skickas till enheten. För att meddelandet ska fungera på rätt sätt måste kommunikationen ske mellan publiceringsinstanser. Den här kommunikationen uppnås med *Apache ActiveMQ Artemis*. Varje publiceringsinstans placeras i en löst kopplad topologi med hjälp av den Oak-baserade Sling-identifieringstjänsten. ActiveMQ har konfigurerats så att varje publiceringsinstans kan kommunicera och skapa en enda meddelandekö. AEM Screens-enheten avsöker den AEM publiceringsgruppen med hjälp av belastningsutjämnaren och hämtar kommandot från köens övre del.

### Omvänd replikering {#reverse-replication}

Efter ett kommando förväntas ett visst svar från Screens-enheten att vidarebefordras till Author-instansen. För att uppnå detta AEM används ***Omvänd replikering***.

* Skapa en omvänd replikeringsagent för varje publiceringsinstans, precis som standardsreplikeringsagenterna och AEM Screens replikeringsagenter.
* En arbetsflödeskonfiguration lyssnar efter noder som ändrats på den AEM publiceringsinstansen och utlöser i sin tur ett arbetsflöde för att placera enhetens svar i AEM publiceringsinstansens utkorg.
* En omvänd replikering i det här sammanhanget används bara för binära data (till exempel loggfiler och skärmbilder) som tillhandahålls av enheterna. Avsökning av icke-binära data hämtas.
* Omvänd replikeringsomröstning från AEM författarinstans hämtar svaret och sparar det i författarinstansen.

### Avsökning av Publish-instanser {#polling-of-publish-instances}

Författarinstanserna måste kunna avfråga enheterna för att få pulsslag och veta hälsostatusen för en ansluten enhet.

Enheter som pingar belastningsutjämnaren och dirigeras till en publiceringsinstans. Enhetens status visas sedan av den AEM publiceringsinstansen via ett Publish-API som opereras med **api/screens-dcc/devices/static** för alla aktiva enheter och **api/screens-dcc/devices/&lt;device_id>/status.json** för en enskild enhet.

Författarinstansen avsöker alla publiceringsinstanser och sammanfogar enhetsstatussvaren till en enda status. Det schemalagda jobbet som avfrågar författaren är `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` och kan konfigureras baserat på ett cron-uttryck.

## Registrering {#registration}

Registreringen fortsätter att ha sitt ursprung i AEM författarinstans. AEM Screens-enheten skickas till författarinstansen och registreringen är klar.

När en enhet har registrerats i AEM redigeringsmiljö replikeras enhetskonfigurationen och tilldelningarna av kanaler/scheman till AEM publiceringsinstanser. Konfigurationen av AEM Screens-enheten uppdateras sedan så att den pekar på belastningsutjämnaren framför den AEM publiceringsgruppen. Detta är avsett som en engångsinstallation. När Screens-enheten har anslutits till publiceringsmiljön kan den fortsätta att ta emot kommandon från författarmiljön. Du behöver inte ansluta AEM Screens-enheten direkt till AEM.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Nästa steg {#the-next-steps}

När du förstår arkitekturdesignen för författare och publiceringsinställningar i AEM Screens kan du läsa [Konfigurera författare och Publish för AEM Screens](author-and-publish.md) om du vill ha mer information.
