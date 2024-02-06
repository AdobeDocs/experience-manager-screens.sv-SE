---
title: Versionsinformation för skärmar, funktionspaket 202401
description: Följ den här sidan för att få information om AEM Screens Feature Pack 202401 släppt den 2 januari 2024.
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: bdc8ff6c1291b7f0dc749e4a9f3a4c1d21678303
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Du bör uppgradera till den senaste versionen av 6.5 Adobe Experience Manager (AEM 6.5). Vi kan hämta den senaste versionsinformationen från [här](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=en)

## Tillgänglighet {#availability}

AEM Screens har släppt AEM 6.5 Feature Pack 11.1.

Du kan ladda ned den senaste funktionspaketet för AEM Screens 6.5.11.1 från [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Navigera till **Adobe Experience Manager** flik och sök efter **Skärmar** för att få det senaste funktionspaketet med namnet **AEM 6.5 skärmar FP11.1**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202204 är 2024-01-01.

### Nyheter {#what-is-new}

Den här versionen innehåller endast säkerhetskorrigeringar.

### Felkorrigeringar {#bug-fixes}

* XSS-problem i fältet&quot;Inaktiv text&quot; på AEM Screens-enheten. (SCRNS-2614)

* XSS-problem `screens/dashboard/device.html` via `Clear cache` åtgärdsdialogrutan. (SCRNS-2632)

* XSS-problem i skärmuppspelningskonfiguration på `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Lagrad XSS i enhetens titel utlöses när en enhet tas bort. (SCRNS-2653)

* XSS-problem `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* Speglad XSS med parametern `item` på `/screens/register-device-wizard.html`. (SCRNS-2670)

* Speglad XSS i `screens/dashboard/device.html` via `returnPage` parameter. (SCRNS-3056)

* Öppna Omdirigering om assign-device-wizard.html. (SCRNS-3444)

* Öppna omdirigering på enhetspanelen. (SCRNS-3443)

* XSS-problem `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Åtgärdade, saknade upprepningsschema och Lägg till schemaknappar: Ett problem upptäcktes i kanalschemaläggningen. (SCRNS-2739)
