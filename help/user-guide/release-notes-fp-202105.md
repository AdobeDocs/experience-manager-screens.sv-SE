---
title: Versionsinformation för funktionspaket 202105
description: Läs om AEM Screens Feature Pack 202105 som släpptes den 4 juni 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). AEM Screens ger underhållsstöd för Screens AEM 6.3.

## Tillgänglighet {#availability}

AEM Screens AEM 6.5 Feature Pack 8.

Du kan hämta det senaste funktionspaketet för AEM Screens 6.5.8 från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Gå till fliken **Adobe Experience Manager** och sök efter **Screens** för att få den senaste funktionspaketet med namnet **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>Installera den lägsta versionen av AEM 6.5 Feature Pack 8 så att AMS-anslutningen fungerar när du har installerat paketen `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` och `screens core bundles`.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202105 är 4 juni 2021.

### Nyheter {#what-is-new}

* **Låser sidan i en AEM Screens-kanal**

  AEM Screens har nu stöd för *Låsning av en sida*, vilket redan har implementerats i AEM Sites. Med Adobe Experience Manager (AEM) kan du låsa en sida så att ingen annan kan redigera innehållet. Den här funktionen är användbar när du gör flera ändringar på en viss sida eller när du måste frysa en sida en kort stund.

* **Namnger AEM Screens Player-enhet**

  AEM Screens-spelarna kan nu skicka ett enhetsnamn till Adobe Experience Manager (AEM).
När gruppregistrering används som standard för att registrera en enhet anges ett systemgenererat användarnamn i namnfältet. Som ett alternativ kan kunden använda en tillgångstagg eller ett annat användarvänligt namn så att den syns i AEM och är lättare att tilldela rätt innehåll.

  I följande dokumentation finns information om hur du konfigurerar namnet i varje operativsystem som stöds:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [CHROME OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Generering av manifest**

  Snabbare generering av kanaler med förbättrade prestanda, till exempel tilldelning av mindre resurser på servern.

### Felkorrigeringar {#bug-fixes}

* Spelaren visade en svart skärm vid växling till en kanal som innehåller en dynamisk inbäddad sekvens.
* Screens-spelarna blockerar nu bytet till en trasig kanal som ytterligare undviker ett 404-fel eller en sida med ett felmeddelande.

### Släppta AEM Screens-spelare

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 8:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens Player - nedladdningar

Om du vill hämta den senaste versionen av AEM Screens Player och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player-hämtningar](https://download.macromedia.com/screens/index.html)**.
