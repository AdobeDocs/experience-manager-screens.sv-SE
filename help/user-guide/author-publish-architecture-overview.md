---
title: Skapa och publicera arkitekturöversikt
seo-title: Skapa och publicera arkitekturöversikt
description: AEM Screens arkitektur liknar en traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM författarinstans och sedan vidarebefordras till flera publiceringsinstanser. Följ den här sidan om du vill veta mer om författare och publicera en översikt över arkitekturen.
seo-description: AEM Screens arkitektur liknar en traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM författarinstans och sedan vidarebefordras till flera publiceringsinstanser. Följ den här sidan om du vill veta mer om författare och publicera en översikt över arkitekturen.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---


# Skapa och publicera arkitekturöversikt {#author-and-publish-architectural-overview}

På den här sidan beskrivs följande ämnen:

* **Introduktion till publiceringsservrar**
* **Arkitektöversikt**
* **Registreringsprocess**

## Förutsättningar {#prerequisites}

Innan du börjar med författare och publiceringsservrar bör du ha kunskap om:

* **AEM Topology**
* **Skapa och hantera AEM Screens Project**
* **Enhetsregistreringsprocess**

>[!NOTE]
>
>Den här AEM Screens-funktionen är bara tillgänglig om du har installerat AEM 6.4 Screens Feature Pack 2. Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobe Support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

## Introduktion {#introduction}

AEM Screens arkitektur liknar en traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM författarinstans och sedan vidarebefordras till flera publiceringsinstanser. AEM Screens-enheter kan nu ansluta till en AEM publiceringsgrupp via belastningsutjämnaren. Det går att lägga till flera AEM publiceringsinstanser för att fortsätta att skala publiceringsgruppen.

*En AEM Screens-innehållsförfattare skapar till exempel* ett kommando i redigeringssystemet för en viss enhet som är konfigurerad att interagera med en publiceringsgrupp eller en AEM Screens-innehållsförfattare som hämtar information om enheter som är konfigurerade att interagera med publiceringsgrupper.

I följande diagram visas författarmiljön och publiceringsmiljön.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Arkitektur {#architectural-design}

Det finns fem arkitektoniska komponenter som underlättar denna lösning:

* ***Replikera innehåll*** från författare till publicering för visning på enheter

* ***Invertera*** replikerat binärt innehåll från publicering (tas emot från enheter) till författare
* ***Skicka*** kommandon från författaren för publicering via särskilda REST API:er
* ***Meddelanden*** mellan publiceringsinstanser för att synkronisera uppdateringar och kommandon för enhetsinformation
* ***Avsökning*** av författaren av publiceringsinstanser för att få enhetsinformation via specifika REST API:er

### Replikering (framåt) av innehåll och konfigurationer  {#replication-forward-of-content-and-configurations}

Standardreplikeringsagenter används för att replikera skärmens kanalinnehåll, platskonfigurationer och enhetskonfigurationer. Detta gör det möjligt för författare att uppdatera innehållet i en kanal och eventuellt gå igenom något slags godkännandearbetsflöde innan kanaluppdateringar publiceras. En replikeringsagent måste skapas för varje publiceringsinstans i publiceringsgruppen.

I följande diagram visas replikeringsprocessen:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>En replikeringsagent måste skapas för varje publiceringsinstans i publiceringsgruppen.

### Skärmreplikeringsagenter och kommandon  {#screens-replication-agents-and-commands}

Specifika replikeringsagenter för anpassade skärmar skapas för att skicka kommandon från författarinstansen till AEM Screens-enheten. AEM Publish-instanserna fungerar som en mellanhand för att vidarebefordra dessa kommandon till enheten.

Detta gör att författare kan fortsätta att hantera enheten, till exempel skicka enhetsuppdateringar och ta skärmbilder från redigeringsmiljön. AEM Screens replikeringsagenter har en anpassad transportkonfiguration, som vanliga replikeringsagenter.

### Meddelanden mellan publiceringsinstanser  {#messaging-between-publish-instances}

I många fall är det bara meningen att ett kommando ska skickas till en enhet en gång. I en belastningsutjämnad publiceringsarkitektur är det dock okänt vilken publiceringsinstans enheten ansluter till.

Därför skickar författarinstansen meddelandet till alla publiceringsinstanser. Sedan bör bara ett meddelande vidarebefordras till enheten. För att meddelandet ska bli korrekt måste viss kommunikation ske mellan publiceringsinstanser. Detta uppnås med *Apache ActiveMQ Artemis*. Varje publiceringsinstans placeras i en löst kopplad topologi med hjälp av Oak-baserad Sling-identifieringstjänst och ActiveMQ har konfigurerats så att varje publiceringsinstans kan kommunicera och skapa en enda meddelandekö. Enheten Skärmar avsöker publiceringsgruppen via belastningsutjämnaren och hämtar kommandot från köns övre del.

### Omvänd replikering {#reverse-replication}

I många fall, efter ett kommando, förväntas något svar från skärmenheten vidarebefordras till författarinstansen. För att uppnå detta AEM används ***omvänd replikering*** .

* Skapa en omvänd replikeringsagent för varje publiceringsinstans, precis som standardsreplikeringsagenterna och skärmreplikeringsagenterna.
* En arbetsflödeskonfiguration lyssnar efter noder som ändrats på publiceringsinstansen och utlöser i sin tur ett arbetsflöde för att placera enhetens svar i publiceringsinstansens utkorg.
* En omvänd replikering i det här sammanhanget används bara för binära data (till exempel loggfiler och skärmbilder) som tillhandahålls av enheterna. Icke-binära data hämtas genom avsökning.
* Omvänd replikering som avfrågas från AEM författarinstans hämtar svaret och sparar det i författarinstansen.

### Avsökning av publiceringsinstanser  {#polling-of-publish-instances}

Författarinstansen måste kunna avfråga enheterna för att få pulsslag och veta hälsostatusen för en ansluten enhet.

Enheter som pingar belastningsutjämnaren och dirigeras till en publiceringsinstans. Enhetens status visas sedan av publiceringsinstansen via ett publicerings-API som opereras med **api/screens-dcc/devices/static** för alla aktiva enheter och **api/screens-dcc/devices/&lt;device_id>/status.json** för en enskild enhet.

Författarinstansen avsöker alla publiceringsinstanser och sammanfogar enhetsstatussvaren till en enda status. Det schemalagda jobbet som avfrågar efter författare är `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` och kan konfigureras baserat på ett cron-uttryck.

## Registrering {#registration}

Registreringen fortsätter att ha sitt ursprung i AEM författarinstans. AEM Screens Device hänvisas till författarinstansen och registreringen är klar.

När en enhet har registrerats i redigeringsmiljön replikeras enhetskonfigurationen och tilldelningarna av kanaler/scheman till AEM publiceringsinstanser. AEM Screens-enhetskonfigurationen uppdateras sedan så att den pekar på belastningsutjämnaren framför AEM publiceringsgrupp. Detta är avsett att vara en engångskonfiguration, och när skärmenheten har anslutits till publiceringsmiljön kan den fortsätta att ta emot kommandon från författarmiljön och du behöver aldrig ansluta skärmenheten direkt till redigeringsmiljön.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Nästa steg {#the-next-steps}

När du har lärt dig den arkitektoniska designen för författare och publiceringskonfigurationen i AEM Screens finns mer information i [Konfigurera författare och publicera för AEM Screens](author-and-publish.md) .
