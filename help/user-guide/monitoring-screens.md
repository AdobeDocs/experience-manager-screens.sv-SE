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

Du kan övervaka och felsöka prestanda för din aktivitet och enhet i AEM Screens Player med hjälp av enhetskonsolen. Den här sidan innehåller information om hur du övervakar och felsöker upplevda prestandaproblem för skärmspelaren och de tilldelade enheterna.

## Övervaka och felsök från Device Control Center {#monitor-and-troubleshoot-from-device-control-center}

Du kan övervaka aktiviteten och därmed felsöka din AEM Screens Player med hjälp av Device Dashboard.

### Instrumentpanel för enhet {#device-dashboard}

Följ stegen nedan för att navigera till kontrollpanelen för enheter:

1. Navigera till kontrollpanelen för enheten från ditt projekt, till exempel ***Testa projekt*** > ***Enheter***.

   Klicka **Enheter** och **Enhetshanteraren** i åtgärdsfältet.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. I listan visas de tilldelade och ej tilldelade enheterna, vilket visas i bilden nedan.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Klicka på enheten (**NewTestDevice**) och klicka på **Kontrollpanel** i åtgärdsfältet.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. På sidan visas enhetsinformation, aktivitet och enhetsinformation som gör att du kan övervaka enhetsaktiviteter och -funktioner.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Övervaka enhetsaktivitet {#monitor-device-activity}

The **Aktivitet** visas den senaste pingen av AEM Screens Player med tidsstämpeln. Den senaste pinghändelsen motsvarar den senaste gången som enheten kontaktade servern.

![chlimage_1](assets/chlimage_1.png)

Klicka också på **Samla in loggar** från det övre högra hörnet av **Aktivitet** för att visa loggarna för spelaren.

### Uppdatera enhetsinformation {#update-device-details}

Kontrollera **Enhetsinformation** så att du kan visa enhetens IP-adress, lagringsanvändning, firmware-version och spelarens drifttid för enheten.

![chlimage_1-1](assets/chlimage_1-1.png)

Klicka också på **Rensa cache** och **Uppdatera** för att rensa cacheminnet på din enhet och uppdatera [firmware](screens-glossary.md) från den här panelen.

Klicka också på **...** från det övre högra hörnet av **Enhetsinformation** för att starta om eller uppdatera spelarens status.

![chlimage_1-2](assets/chlimage_1-2.png)

### Uppdatera enhetsinformation {#update-device-information}

Kontrollera **ENHETSINFORMATION** -panelen. Här kan du visa konfigurationsuppdateringen, enhetsmodellen, enhets-OS och gränssnittsinformationen.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Klicka också på (**...**) i det övre högra hörnet av panelen Enhetsinformation för att visa egenskaper eller uppdatera enheten.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Klicka **Egenskaper** så att du kan se **Enhetsegenskaper** -dialogrutan. Du kan redigera enhetens titel eller välja alternativet för konfigurationsuppdateringar som **Manuell** eller **Automatisk**.

>[!NOTE]
>
>Mer information om de händelser som är associerade med enhetens automatiska eller manuella uppdateringar finns i avsnittet ***Automatiska eller manuella uppdateringar från enhetskontrollpanelen*** in [Hantera kanaler](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### View Player Screenshot {#view-player-screenshot}

Du kan visa skärmbilden för spelaren från enheten från **SPELARSKÄRMBILD** -panelen.

Klicka (**...**) i det övre högra hörnet av panelen Spelarbild och klicka på **Uppdatera skärmbild** för att visa ögonblicksbilden av spelaren som körs.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Hantera inställningar {#manage-preferences}

The **INSTÄLLNINGAR** kan användaren ändra inställningar för **Administratörsgränssnitt**, **Kanalväljare** och **Fjärrfelsökning** för enheten.

>[!NOTE]
>Mer information om de här alternativen finns i [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Klicka också på **Inställningar** från det övre högra hörnet för att uppdatera enhetsinställningarna. Du kan uppdatera följande inställningar:

* **Server-URL**
* **Upplösning**
* **Starta om schemat**
* **Max. nr av loggfiler som ska behållas**
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

Vissa av dessa funktioner är för närvarande bara tillgängliga om *Apache Sling Referer-filtret Tillåt tomt* är aktiverat i OSGi-konfigurationen. Kontrollpanelen kan visa en varning om att skyddsinställningarna kan förhindra vissa av dessa funktioner från att fungera.

Följ stegen nedan för att aktivera filtret Tillåt tomt för Apache Sling Referrer

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console**, det vill säga `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Kontrollera **allow.empty** alternativ.
1. Klicka **Spara**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recommendations {#recommendations}

I följande avsnitt rekommenderas övervakning av nätverkslänkar, servrar och spelare för att förstå hälsan och reagera på problem.

AEM har inbyggd övervakning för:

* *Hjärtslag* var 5:e sekund för att ange att AEM Screens Player är i drift.
* *Skärmbild* från spelaren som visar vad som visas i spelaren.
* The *AEM Screens Player Firmware* versionen är installerad på spelaren.
* *Ledigt lagringsutrymme* på spelaren.

Recommendations för fjärrövervakning med tredjepartsprogram:

* CPU-användning i spelare.
* Kontrollera om AEM Screens Player-processen körs.
* Fjärrstarta om/starta om spelaren.
* Realtidsmeddelanden.

Vi rekommenderar att du driftsätter Player-maskinvaran och operativsystemet på ett sätt som gör att fjärrinloggning kan diagnostisera problem och starta om spelaren.

#### Andra resurser {#additional-resources}

Se [Konfiguration och felsökning av videouppspelning](troubleshoot-videos.md) om du vill felsöka och felsöka videor som spelas upp i din kanal.
