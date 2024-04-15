---
title: Felsöka Device Control Center
description: Lär dig hur du övervakar och felsöker prestanda för din AEM Screens-spelaraktivitet och enhet med hjälp av kontrollpanelen för enheter.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Felsökning av Device Control Center {#troubleshooting-device-control-center}

Du kan övervaka och felsöka prestanda för din AEM Screens-spelaraktivitet och enhet med hjälp av kontrollpanelen Enhet. Den här sidan innehåller information om hur du övervakar och felsöker upplevda prestandaproblem för skärmspelaren och de tilldelade enheterna.

## Övervaka och felsöka från Device Control Center {#monitor-and-troubleshoot-from-device-control-center}

Du kan övervaka aktiviteten och därmed felsöka AEM Screens-spelaren med hjälp av kontrollpanelen för enheten.

### Instrumentpanel för enheter {#device-dashboard}

Följ stegen nedan för att navigera till enhetens instrumentpanel:

1. Gå till instrumentpanelen för enheten från projektet, ***till exempel Testa Project*** > ***Enheter***.

   Välj **Enheter** och **Enhetshanteraren** i åtgärdsfältet.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. I listan visas de tilldelade och ej tilldelade enheterna, vilket visas i bilden nedan.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Välj enhet (**NewTestDevice**) och markera **Kontrollpanel** i åtgärdsfältet.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. På sidan visas enhetsinformation, aktivitet och enhetsinformation som gör att du kan övervaka enhetsaktiviteter och -funktioner.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Övervaka enhetsaktivitet {#monitor-device-activity}

The **Aktivitet** På panelen visas den senaste pingen av din AEM Screens-spelare med tidsstämpeln. Den senaste pinghändelsen motsvarar den senaste gången som enheten kontaktade servern.

![chlimage_1](assets/chlimage_1.png)

Välj **också Samla in loggar** i det övre högra hörnet av **aktivitetspanelen** för att visa loggarna för din spelare.

### Uppdatera enhetsinformation {#update-device-details}

Kontrollera **Enhetsinformation** så att du kan visa enhetens IP-adress, lagringsanvändning, firmware-version och spelarens drifttid för enheten.

![chlimage_1-1](assets/chlimage_1-1.png)

Välj även **Rensa cache** och **Uppdatera** för att rensa cacheminnet på din enhet och uppdatera [firmware](screens-glossary.md) från den här panelen.

Välj även **...** från det övre högra hörnet av **Enhetsinformation** för att starta om eller uppdatera spelarens status.

![chlimage_1-2](assets/chlimage_1-2.png)

### Uppdatera enhetsinformation {#update-device-information}

**Kontrollera panelen ENHETSINFORMATION**. Här kan du visa konfigurationsuppdateringen, enhetsmodellen, enhetens operativsystem och gränssnittsinformationen.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Välj också (**...**) i det övre högra hörnet på panelen Enhetsinformation för att visa egenskaper eller uppdatera enheten.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Välj **Egenskaper** så att du kan se **Enhetsegenskaper** -dialogrutan. Du kan redigera enhetens titel eller välja alternativet för konfigurationsuppdateringar som **Manuell** eller **Automatisk**.

>[!NOTE]
>
>Mer information om de händelser som är associerade med enhetens automatiska eller manuella uppdateringar finns i avsnittet ***Automatiska eller manuella uppdateringar från enhetskontrollpanelen*** in [Hantera kanaler](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### View Player Screenshot {#view-player-screenshot}

Du kan visa skärmbilden för spelaren från enheten från **SPELARSKÄRMBILD** -panelen.

Markera (**...**) i det övre högra hörnet av panelen Player-skärmbild och väljer **Uppdatera skärmbild** för att visa ögonblicksbilden av spelaren som körs.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Hantera inställningar {#manage-preferences}

The **INSTÄLLNINGAR** kan användaren ändra inställningar för **Administratörsgränssnitt**, **Kanalväljare** och **Fjärrfelsökning** för enheten.

>[!NOTE]
>Mer information om de här alternativen finns i [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Välj även **Inställningar** från det övre högra hörnet för att uppdatera enhetsinställningarna. Du kan uppdatera följande inställningar:

* **Server-URL**
* **Upplösning**
* **Schema för omstart**
* **Max. nr av loggfiler som ska behållas**
* **Loggnivå**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>Du kan välja någon av följande loggnivåer:
>* **Inaktivera**
>* **Felsök**
>* **Info**
>* **Varning**
>* **Fel**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Felsöka OSGi-inställningar {#troubleshoot-osgi-settings}

Aktivera den tomma referensen så att enheten kan skicka data till servern. Om t.ex. den tomma refereraregenskapen är inaktiverad, kan enheten inte publicera en skärmdump.

Vissa av dessa funktioner är för närvarande bara tillgängliga om *Apache Sling Referer-filtret Tillåt tomt* är aktiverat i OSGi-konfigurationen. Kontrollpanelen kan visa en varning om att skyddsinställningarna kan förhindra vissa av dessa funktioner från att fungera.

Följ stegen nedan för att aktivera filtret Tillåt tomt för Apache Sling Referrer

1. Navigera till **Adobe Experience Manager Web Console Configuration**, d.v.s. `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. **Markera alternativet allow.empty**.
1. Välj **Spara**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Rekommendationer {#recommendations}

I följande avsnitt rekommenderas övervakning av nätverkslänkar, servrar och spelare för att förstå hälsan och reagera på problem.

AEM har inbyggd övervakning för:

* *Hjärtslag* var 5:e sekund för att ange att AEM Screens Player är i drift.
* *Skärmbild* från spelaren som visar vad som visas i spelaren.
* The *AEM Screens Player Firmware* version som är installerad på spelaren.
* *Ledigt lagringsutrymme* på spelaren.

Recommendations för fjärrövervakning med tredjepartsprogram:

* CPU-användning för spelare.
* Kontrollera om AEM Screens Player-processen körs.
* Fjärrstarta om/starta om spelaren.
* Realtidsmeddelanden.

Vi rekommenderar att du driftsätter Player-maskinvaran och operativsystemet på ett sätt som gör att fjärrinloggning kan diagnostisera problem och starta om spelaren.

#### Andra resurser {#additional-resources}

Se [Konfiguration och felsökning](troubleshoot-videos.md) av videouppspelning om du vill felsöka och felsöka videor som spelas upp i din kanal.
