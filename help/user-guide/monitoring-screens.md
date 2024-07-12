---
title: Felsökning av Device Control Center
description: Lär dig hur du övervakar och felsöker prestanda för din AEM Screens Player-aktivitet och enhet med hjälp av kontrollpanelen för enheter.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Felsökning av Device Control Center {#troubleshooting-device-control-center}

Du kan övervaka och felsöka prestanda för din aktivitet och enhet i AEM Screens Player med hjälp av enhetskonsolen. På den här sidan finns information om hur du övervakar och felsöker prestandaproblem som upplevs som problem för Screens Player och de tilldelade enheterna.

## Övervaka och felsök från Device Control Center {#monitor-and-troubleshoot-from-device-control-center}

Du kan övervaka aktiviteten och därmed felsöka din AEM Screens Player med hjälp av Device Dashboard.

### Instrumentpanel för enhet {#device-dashboard}

Följ stegen nedan för att navigera till kontrollpanelen för enheter:

1. Navigera till enhetens kontrollpanel från ditt projekt, till exempel ***Testa projekt*** > ***Enheter***.

   Klicka på **Enheter** och **Enhetshanteraren** i åtgärdsfältet.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. I listan visas de tilldelade och ej tilldelade enheterna, vilket visas i bilden nedan.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Klicka på enheten (**NewTestDevice**) och klicka på **Dashboard** i åtgärdsfältet.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. På sidan visas enhetsinformation, aktivitet och enhetsinformation som gör att du kan övervaka enhetsaktiviteter och -funktioner.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Övervaka enhetsaktivitet {#monitor-device-activity}

På panelen **Aktivitet** visas den senaste pingen av AEM Screens Player med tidsstämpeln. Den senaste pinghändelsen motsvarar den senaste gången som enheten kontaktade servern.

![chlimage_1](assets/chlimage_1.png)

Klicka även på **Samla in loggar** i det övre högra hörnet av **aktivitetspanelen** för att visa loggarna för spelaren.

### Uppdatera enhetsinformation {#update-device-details}

Kontrollera panelen **Enhetsinformation** så att du kan visa enhetens IP-adress, lagringsanvändning, firmware-version och spelarens drifttid för enheten.

![chlimage_1-1](assets/chlimage_1-1.png)

Klicka även på **Rensa cache** och **Uppdatera** för att rensa cacheminnet för enheten och uppdatera versionen [firmware](screens-glossary.md) från den här panelen.

Klicka även på **..** i det övre högra hörnet av panelen **Enhetsinformation** för att starta om eller uppdatera spelarens status.

![chlimage_1-2](assets/chlimage_1-2.png)

### Uppdatera enhetsinformation {#update-device-information}

Kontrollera panelen **ENHETSINFORMATION**. Här kan du visa konfigurationsuppdateringen, enhetsmodellen, enhets-OS och gränssnittsinformationen.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Klicka också på (**..**) i det övre högra hörnet av panelen Enhetsinformation för att visa egenskaper eller uppdatera enheten.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Klicka på **Egenskaper** så att du kan visa dialogrutan **Enhetsegenskaper**. Du kan redigera enhetens titel eller välja alternativet för konfigurationsuppdateringar som **Manuell** eller **Automatisk**.

>[!NOTE]
>
>Mer information om de händelser som är associerade med enhetens automatiska eller manuella uppdateringar finns i avsnittet ***Automatiska eller Manuella uppdateringar från enhetskontrollpanelen*** i [Hantera kanaler](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### View Player Screenshot {#view-player-screenshot}

Du kan visa skärmbilden för spelaren från enheten på panelen **PLAYER SCREENSHOT** .

Klicka på (**...**) i det övre högra hörnet av panelen Player-skärmbild och klicka på **Uppdatera skärmbild** för att visa ögonblicksbilden av spelaren som körs.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Hantera inställningar {#manage-preferences}

På panelen **INSTÄLLNINGAR** kan användaren ändra inställningarna för **administratörsgränssnittet**, **kanalväljaren** och **fjärrfelsökning** för enheten.

>[!NOTE]
>Mer information om de här alternativen finns i [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Klicka även på **Inställningar** i det övre högra hörnet för att uppdatera enhetsinställningarna. Du kan uppdatera följande inställningar:

* **Server-URL**
* **Upplösning**
* **Starta om schemat**
* **Max antal av loggfiler som ska behållas**
* **Loggnivå**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>Du kan klicka på någon av följande loggnivåer:
>* **Inaktivera**
>* **Felsök**
>* **Info**
>* **Varning**
>* **Fel**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Felsöka OSGi-inställningar {#troubleshoot-osgi-settings}

Aktivera den tomma referenten så att enheten kan skicka data till servern. Om t.ex. den tomma refereraregenskapen är inaktiverad, kan enheten inte publicera en skärmdump.

Vissa av dessa funktioner är för närvarande bara tillgängliga om *Refererarfiltret för Apache Sling Tillåt tom* är aktiverat i OSGi-konfigurationen. Kontrollpanelen kan visa en varning om att skyddsinställningarna kan förhindra vissa av dessa funktioner från att fungera.

Följ stegen nedan för att aktivera filtret Tillåt tomt för Apache Sling Referrer

1. Navigera till **Adobe Experience Manager Web Console Configuration**, det vill säga `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Markera alternativet **allow.empty**.
1. Klicka på **Spara**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recommendations {#recommendations}

I följande avsnitt rekommenderas övervakning av nätverkslänkar, servrar och spelare för att förstå hälsan och reagera på problem.

AEM har inbyggd övervakning för:

* *pulsslag* var femte sekund för att ange att AEM Screens Player är i drift.
* *Skärmbild* från spelaren som visar vad som visas i spelaren.
* *AEM Screens Player-versionen* är installerad i spelaren.
* *Ledigt lagringsutrymme* i spelaren.

Recommendations för fjärrövervakning med tredjepartsprogram:

* CPU-användning i spelare.
* Kontrollera om AEM Screens Player-processen körs.
* Fjärrstarta om/starta om spelaren.
* Realtidsmeddelanden.

Vi rekommenderar att du driftsätter Player-maskinvaran och operativsystemet på ett sätt som gör att fjärrinloggning kan diagnostisera problem och starta om spelaren.

#### Andra resurser {#additional-resources}

Se [Konfiguration och felsökning för videouppspelning](troubleshoot-videos.md) om du vill felsöka och felsöka videor som spelas upp i din kanal.
