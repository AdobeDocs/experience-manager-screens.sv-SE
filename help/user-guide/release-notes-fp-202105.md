---
title: Versionsinformation för funktionspaket 202105
description: "Följ den här sidan för att få information om AEM Screens Feature Pack 202105 släppt den 4 juni 2021."
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 02bc399d61f5666918caad9fce3d69d63f0782d7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Vi rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). Skärmar har underhållsstöd för AEM 6.3 Screens-plattformen.

## Tillgänglighet {#availability}

AEM Screens har släppt AEM 6.5 Feature Pack 8.

Du kan ladda ned det senaste funktionspaketet för AEM Screens 6.5.8 från [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Navigera till **Adobe Experience Manager** flik och sök efter **Skärmar** för att få det senaste funktionspaketet med namnet **AEM 6.5 skärmar FP8**.

>[!IMPORTANT]
>Du måste installera en minimiversion av AEM 6.5 Feature Pack 8 för att AMS-anslutningen ska fungera när du har installerat paketen `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` och `screens core bundles`.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202105 är 4 juni 2021.

### Nyheter {#what-is-new}

* **Låsa sida i en AEM Screens-kanal**

   AEM Screens stöder nu *Låsa en sida*, som redan implementerats i AEM Sites. Med Adobe Experience Manager (AEM) kan du låsa en sida så att ingen annan kan ändra innehållet. Det här är användbart när du gör många ändringar på en viss sida eller när du behöver frysa en sida en kort stund.

* **Namnge AEM Screens Player-enhet**

   AEM Screens-spelarna kan nu skicka ett enhetsnamn till Adobe Experience Manager (AEM).
När gruppregistrering används för att registrera en enhet anges som standard ett systemgenererat användarnamn i namnfältet. Som ett alternativ kan kunden använda en tillgångstagg eller ett annat användarvänligt namn så att den syns i AEM och är lättare att tilldela rätt innehåll.

   Läs följande dokumentation för att lära dig hur du konfigurerar namnet i varje operativsystem som stöds:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Generering av manifest**

   Snabbare generering av kanalmanifest med förbättrade prestanda, till exempel tilldelning av mindre resurser på servern.

### Felkorrigeringar {#bug-fixes}

* Spelaren visade en svart skärm vid växling till kanal som innehåller dynamisk inbäddad sekvens.
* Skärmspelarna blockerar nu bytet till en trasig kanal som ytterligare undviker 404-fel eller en sida med ett felmeddelande.

### Lanserade AEM Screens-spelare {#released-aem-screens-players}

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 8:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### AEM Screens Player - nedladdningar  {#aem-screens-player-downloads}

Om du vill hämta den senaste AEM Screens-spelaren och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/index.html)**.
