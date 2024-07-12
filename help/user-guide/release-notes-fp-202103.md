---
title: Versionsinformation för funktionspaket 2013
description: Läs mer om AEM Screens Feature Pack 202103 som släpptes den 5 mars 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 2013 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). AEM Screens ger underhållsstöd för Screens AEM 6.3.

## Tillgänglighet {#availability}

AEM Screens AEM 6.5 Feature Pack 7.

Du kan hämta det senaste funktionspaketet för AEM Screens 6.5.7 från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Gå till fliken **Adobe Experience Manager** och sök efter **Screens** för att få den senaste funktionspaketet med namnet **AEM 6.5 Screens FP7**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202103 är 5 mars 2021.

### Nyheter {#what-is-new}

* **AEM Screens Automatisk registrering av spelare**

  Att manuellt registrera tusentals spelare är krångligt och kostar mer tid och pengar. För att förenkla processen kan du med funktionen Automatisk registrering av spelare ange en i förväg delad nyckel i AEM. Nyckeln kan tilldelas till en spelare antingen via en konfigurationsfil eller en MDM-lösning (Mobile Device Management).

  Mer information finns i [Automatisk registrering av spelare](/help/user-guide/auto-registration-players.md).


* **Massetablering av Android™ Player med Enterprise Mobility Management**

  När du distribuerar Android™-spelaren i grupp blir det omständligt att registrera alla spelare manuellt med AEM. Vi rekommenderar att du använder en EMM-lösning (Enterprise Mobility Management) som `VMWare Airwatch`, `MobileIron` eller `Samsung Knox` för att fjärrdistribuera och hantera din distribution. AEM Screens Android™-spelaren stöder den branschledande EMM AppConfig för fjärrprovisionering.

  Mer information finns i [Massetablering av Android™ Player med Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation).


### Felkorrigeringar {#bug-fixes}

* Förbättrade prestanda för datoranvändning av `clientlib` och `asset hashes`.

* SmartSync-migrering skulle skada spelaren om cachen inte blev ogiltig.

* Offlinecache skapades inte om tilldelningen hade *OfflineConfig*.

* Uppdateringar till `Tizen`-spelaren som har avbrutits eftersom strikt origo-when-cross-origin inte stöds.

* Om den tilldelade kanalens schema *Upprepningar* ändras så bryts gränssnittet.

* Uppdatering av offlineinnehåll misslyckades med frågeundantag.

* Tidsfördröjningen mellan övergångar under interaktionen i en interaktiv upplevelse är nu åtgärdad.

* En misslyckad begäran om uppdatering av konfiguration orsakade tomma skärmar.

### Släppta AEM Screens-spelare

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 7:

* CHROME OS
* Windows
* Linux®

#### AEM Screens Player - nedladdningar

Om du vill hämta den senaste versionen av AEM Screens Player och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player-hämtningar](https://download.macromedia.com/screens/index.html)**.
