---
title: Versionsinformation för funktionspaket 2013
description: Läs mer om AEM Screens Feature Pack 202103 som släpptes den 5 mars 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 2013 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). AEM Screens har underhållsstöd för AEM 6.3 Screens Platform.

## Tillgänglighet {#availability}

AEM Screens AEM 6.5 Feature Pack 7.

Du kan ladda ned det senaste funktionspaketet för AEM Screens 6.5.7 från [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Navigera till **Adobe Experience Manager** flik och sök efter **Skärmar** för att få det senaste funktionspaketet med namnet **AEM 6.5-skärmar FP7**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202103 är 5 mars 2021.

### Nyheter {#what-is-new}

* **Automatisk registrering av spelare i AEM Screens**

  Att manuellt registrera tusentals spelare är krångligt och kostar mer tid och pengar. För att förenkla processen kan du med funktionen Automatisk registrering av spelare ange en i förväg delad nyckel i AEM. Nyckeln kan tilldelas till en spelare antingen via en konfigurationsfil eller en MDM-lösning (Mobile Device Management).

  Se [Automatisk registrering av spelare](/help/user-guide/auto-registration-players.md) för mer information.


* **Massetablering av Android™ Player med Enterprise Mobility Management**

  När du distribuerar Android™-spelaren i grupp blir det omständligt att manuellt registrera alla spelare med AEM. Vi rekommenderar starkt att du använder en EMM-lösning (Enterprise Mobility Management) som `VMWare Airwatch`, `MobileIron`, eller `Samsung Knox` för att fjärrdistribuera och hantera din distribution. AEM Screens Android™-spelaren har stöd för den branschledande EMM AppConfig som tillåter fjärretablering.

  Se [Massetablering av Android™ Player med Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation) för mer information.


### Felkorrigeringar {#bug-fixes}

* Förbättrade prestanda för datoranvändning `clientlib` och `asset hashes`.

* SmartSync-migrering skulle bryta spelaren om cachen inte blev ogiltig.

* Offlinecache skapades inte om tilldelningen hade *OfflineConfig*.

* Uppdateringar till `Tizen` spelaren som gick sönder eftersom referenspolicyn strikt origo-when-cross-origin inte stöds.

* Ändra schemat för den tilldelade kanalen *Upprepningar* fältet bröt användargränssnittet.

* Uppdatering av offlineinnehåll misslyckades med frågeundantag.

* Tidsfördröjning mellan övergångar under interaktionen i den interaktiva upplevelsen har nu åtgärdats.

* Det gick inte att uppdatera konfigurationsbegäran vilket orsakade den tomma skärmen.

### Släppta AEM Screens-spelare

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 7:

* Chrome OS
* Windows
* Linux®

#### AEM Screens Player - nedladdningar

Om du vill hämta den senaste AEM Screens-spelaren och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/index.html)**.
