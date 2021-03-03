---
title: Versionsinformation för funktionspaket 2013
description: Sidan innehåller versionsinformation för funktionspaket 2013.
translation-type: tm+mt
source-git-commit: 5f8938bfd092197391aefcd2d730d47fa06c214d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Versionsinformation för funktionspaket 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Vi rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). Skärmar har underhållsstöd för AEM 6.3 Screens-plattformen.

## Tillgänglighet {#availability}

AEM Screens har släppt AEM 6.5 Feature Pack 7.

Du kan hämta det senaste funktionspaketet för AEM Screens 6.5.7 från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Gå till fliken **Adobe Experience Manager** och sök efter **skärmar** för att få den senaste funktionspaketet med namnet **AEM 6.5 skärmar FP7**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202103 är 8 mars 2021.

### Nyheter {#what-is-new}

* **AEM Screens Bulk Registration and Assignation**

   Att manuellt registrera tusentals spelare är mycket krångligt och kostar mer och mer. För att förenkla den här processen kan du med funktionen för massregistrering ange en i förväg delad nyckel i AEM som kan etableras i en spelare antingen via en konfigurationsfil eller en MDM-lösning (Mobile Device Management).

* **Massetablering av Android Player med Enterprise Mobility Management**

   När du distribuerar Android-spelaren i grupp blir det omständligt att manuellt registrera alla spelare med AEM. Vi rekommenderar att du använder en EMM-lösning (Enterprise Mobility Management), som VMWare Airwatch, MobileIron eller Samsung Knox, för att fjärrdistribuera och hantera distributionen. AEM Screens Android-spelaren har stöd för den branschledande EMM-appconfig som tillåter fjärretablering.

* **Lås sida i en AEM Screens-kanal**

   AEM Screens har nu stöd för *Låsning av en sida*, som redan har implementerats i AEM Sites. Med Adobe Experience Manager (AEM) kan du låsa en sida så att ingen annan kan ändra innehållet. Det här är användbart när du gör många ändringar på en viss sida eller när du behöver frysa en sida en kort stund.

### Felkorrigeringar {#bug-fixes}

* Förbättrade prestanda för beräkning av `clientlib` och `asset hashes`.

* SmartSync-migrering skulle bryta spelaren om cachen inte blev ogiltig.

* Offlinecache skapades inte om tilldelningen hade *OfflineConfig*.

### Lanserade AEM Screens Players {#released-aem-screens-players}

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 7:

* Chrome OS
* Windows
* Android
* Tizen
* Linux

#### AEM Screens Player Downloads {#aem-screens-player-downloads}

Om du vill hämta den senaste AEM Screens-spelaren och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player Downloads](https://download.macromedia.com/screens/index.html)**.
