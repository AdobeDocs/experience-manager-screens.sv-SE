---
title: Felsökning av Device Control Center
seo-title: Övervaka skärmar
description: Följ den här sidan för att övervaka och felsöka prestanda för din aktivitet och enhet för skärmuppspelning med hjälp av enhetskonsolen.
seo-description: Följ den här sidan för att övervaka och felsöka prestanda för din aktivitet och enhet för skärmuppspelning med hjälp av enhetskonsolen.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 1%

---


# Felsökning av Device Control Center {#troubleshooting-device-control-center}

Du kan övervaka och felsöka prestanda för din aktivitet och enhet för skärmuppspelning med hjälp av kontrollpanelen för enheter. Den här sidan innehåller information om hur du övervakar och felsöker upplevda prestandaproblem för skärmspelaren och de tilldelade enheterna.

## Övervaka och felsök från Device Control Center {#monitor-and-troubleshoot-from-device-control-center}

Du kan övervaka aktiviteten och därmed felsöka skärmspelaren med Device Dashboard.

### Enhetens instrumentpanel {#device-dashboard}

Följ stegen nedan för att navigera till kontrollpanelen för enheter:

1. Navigera till enhetskonsolen från ditt projekt, till exempel ***Testa projekt*** —> ***Enheter***.

   Välj **Enheter** och **Enhetshanteraren** i åtgärdsfältet.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. I listan visas de tilldelade och ej tilldelade enheterna, vilket visas i bilden nedan.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Markera enheten (**NewTestDevice**) och klicka på **Kontrollpanel** i åtgärdsfältet.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. På sidan visas enhetsinformation, aktivitet och enhetsinformation som gör att du kan övervaka enhetsaktiviteter och -funktioner.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Övervaka enhetsaktivitet {#monitor-device-activity}

På panelen **Aktivitet** visas den senaste pingen av skärmspelaren med tidsstämpeln. Den senaste penseln motsvarar den senaste gången som enheten kontaktade servern.

![chlimage_1](assets/chlimage_1.png)

Klicka på **Samla in loggar** i det övre högra hörnet av panelen **Aktivitet** för att visa loggarna för spelaren.

### Uppdatera enhetsinformation {#update-device-details}

Kontrollera panelen **Enhetsinformation** för att visa enhetens IP-adress, lagringsanvändning, version av inbyggd programvara och spelarens drifttid för enheten.

![chlimage_1-1](assets/chlimage_1-1.png)

Klicka dessutom på **Rensa cacheminne** och **Uppdatera** för att rensa cacheminnet för enheten och uppdatera [versionen av den inbyggda programvaran](screens-glossary.md) från den här panelen.

Klicka på **..** i det övre högra hörnet av panelen **Enhetsinformation** om du vill starta om eller uppdatera spelarens status.

![chlimage_1-2](assets/chlimage_1-2.png)

### Uppdatera enhetsinformation {#update-device-information}

Kontrollera panelen **ENHETSINFORMATION** för att visa konfigurationsuppdateringen, enhetsmodellen, enhets-OS och gränssnittsinformationen.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Klicka på (**)..**) i det övre högra hörnet av panelen Enhetsinformation om du vill visa egenskaper eller uppdatera enheten.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Klicka på **Egenskaper** för att visa dialogrutan **Enhetsegenskaper**. Du kan redigera enhetens titel eller välja alternativet för konfigurationsuppdateringar som **Manuell** eller **Automatisk**.

>[!NOTE]
>
>Mer information om de händelser som är associerade med enhetens automatiska eller manuella uppdateringar finns i avsnittet ***Automatiska eller Manuella uppdateringar från Device Dashboard*** i [Hantera kanaler](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Visa skärmbild för spelaren {#view-player-screenshot}

Du kan visa skärmbilden för spelaren från enheten på panelen **PLAYER SCREENSHOT**.

Klicka på (**)...**) i det övre högra hörnet av panelen Player-skärmbild och välj **Uppdatera skärmbild** för att visa ögonblicksbilden av spelaren som körs.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Hantera inställningar {#manage-preferences}

På panelen **INSTÄLLNINGAR** kan användaren ändra inställningar för **Admin-användargränssnitt**, **kanalväxlare** och **fjärrfelsökning** för enheten.

>[!NOTE]
>Mer information om detta alternativ finns i [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Klicka dessutom på **Inställningar** i det övre högra hörnet för att uppdatera enhetsinställningarna. Du kan uppdatera följande inställningar:

* **Server-URL**
* **Upplösning**
* **Starta om schemat**
* **Max. nr av loggfiler som ska sparas**
* **Loggnivå**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>Du kan välja någon av följande loggnivåer:
>* **Inaktivera**
>* **Felsök**
>* **Information**
>* **Varning**
>* **Fel**


![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Felsöka OSGi-inställningar {#troubleshoot-osgi-settings}

Du måste aktivera den tomma referenten för att enheten ska kunna skicka data till servern. Om t.ex. den tomma refereraregenskapen är inaktiverad, kan enheten inte publicera en skärmdump.

Vissa av dessa funktioner är för närvarande bara tillgängliga om *Refererarfiltret för Apache Sling Tillåt tom* är aktiverat i OSGi-konfigurationen. Kontrollpanelen kan visa en varning om att skyddsinställningarna kan förhindra vissa av dessa funktioner från att fungera.

Följ stegen nedan för att aktivera filtret Tillåt tomt för Apache Sling Referrer-filtret

1. Navigera till **Adobe Experience Manager Web Console Configuration**, d.v.s. `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Markera alternativet **allow.empty**.
1. Klicka på **Spara**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recommendations {#recommendations}

I följande avsnitt rekommenderas övervakning av nätverkslänkar, servrar och spelare för att förstå hälsan och reagera på problem.

AEM har inbyggd övervakning för:

* *Varannan* sekund visar att AEM Screens Player är i drift.
* *Skärmbild* från spelaren som visar vad som för närvarande visas i spelaren.
* Den version av *AEM Screens Player Firmware* som är installerad på spelaren.
* *Spelaren har* lagringsutrymme utan extra kostnad.

Recommendations för fjärrövervakning med program från tredje part:

* CPU-användning för spelare.
* Kontrollera om AEM Screens Player-processen körs.
* Fjärrstarta om/starta om spelaren.
* Realtidsmeddelanden.

Vi rekommenderar att du driftsätter Player-maskinvaran och operativsystemet på ett sätt som gör att fjärrinloggning kan diagnostisera problem och starta om spelaren.

#### Ytterligare resurser {#additional-resources}

Se [Konfiguration av videouppspelning och felsökning](troubleshoot-videos.md) för att felsöka och felsöka videoklipp som spelas upp i din kanal.
