---
title: Versionsinformation för funktionspaket 2013
description: "Följ den här sidan för att få information om AEM Screens Feature Pack 202103 släppt den 5 mars 2021."
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 2013 {#release-notes-for-feature-pack}

>[!CAUTION]
>Vi rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). Skärmar har underhållsstöd för AEM 6.3 Screens-plattformen.

## Tillgänglighet {#availability}

AEM Screens har släppt AEM 6.5 Feature Pack 7.

Du kan ladda ned det senaste funktionspaketet för AEM Screens 6.5.7 från [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Navigera till **Adobe Experience Manager** flik och sök efter **Skärmar** för att få det senaste funktionspaketet med namnet **AEM 6.5-skärmar FP7**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202103 är 5 mars 2021.

### Nyheter {#what-is-new}

* **AEM Screens - automatisk registrering av spelare**

   Att manuellt registrera tusentals spelare är mycket krångligt och kostar mer och mer. För att förenkla processen kan du med funktionen Automatisk registrering av spelare ange en i förväg delad nyckel i AEM som kan etableras i en spelare antingen via en konfigurationsfil eller en MDM-lösning (Mobile Device Management).

   Se [Automatisk registrering av spelare](/help/user-guide/auto-registration-players.md) för mer information.


* **Massetablering av Android Player med Enterprise Mobility Management**

   När du distribuerar Android-spelaren i grupp blir det omständligt att manuellt registrera alla spelare med AEM. Vi rekommenderar att du använder en EMM-lösning (Enterprise Mobility Management), som VMWare Airwatch, MobileIron eller Samsung Knox, för att fjärrdistribuera och hantera distributionen. AEM Screens Android-spelaren har stöd för den branschledande EMM AppConfig som tillåter fjärretablering.

   Se [Massetablering av Android Player med Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation) för mer information.


### Felkorrigeringar {#bug-fixes}

* Förbättrade prestanda för datoranvändning `clientlib` och `asset hashes`.

* SmartSync-migrering skulle bryta spelaren om cachen inte blev ogiltig.

* Offlinecache skapades inte om tilldelningen hade *OfflineConfig*.

* Uppdateringar till Tizen-spelaren som har avbrutits eftersom referenspolicyn har strikt ursprung vid korsursprung stöds inte.

* Ändra schemat för den tilldelade kanalen *Upprepningar* fältet bröt användargränssnittet.

* Uppdatering av offlineinnehåll misslyckades med frågeundantag.

* Tidsfördröjning mellan övergångar under interaktionen i den interaktiva upplevelsen har nu åtgärdats.

* Det gick inte att uppdatera konfigurationsbegäran vilket orsakade den tomma skärmen.

### Lanserade AEM Screens-spelare {#released-aem-screens-players}

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 7:

* Chrome OS
* Windows
* Linux

#### AEM Screens Player - nedladdningar  {#aem-screens-player-downloads}

Om du vill hämta den senaste AEM Screens-spelaren och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/index.html)**.
