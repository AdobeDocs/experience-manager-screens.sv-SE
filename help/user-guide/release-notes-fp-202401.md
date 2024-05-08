---
title: Versionsinformation för skärmar, funktionspaket 202401
description: Läs mer om AEM Screens Feature Pack 202401 släppt den 2 januari 2024.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe rekommenderar att du uppgraderar till den senaste versionen av 6.5 Adobe Experience Manager (AEM 6.5). Hämta den senaste versionsinformationen från [här](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/release-notes).

## Tillgänglighet {#availability}

AEM Screens AEM 6.5 Feature Pack 11.1.

Du kan hämta den senaste versionen av funktionspaketet för AEM Screens 6.5.11.1 från [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Navigera till **Adobe Experience Manager** flik och sök efter **Skärmar** för att få det senaste funktionspaketet med namnet **AEM 6.5 skärmar FP11.1**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202204 är 2 januari 2024.

### Nyheter {#what-is-new}

Den här versionen innehåller endast säkerhetskorrigeringar.

### Felkorrigeringar {#bug-fixes}

* XSS-problem i fältet&quot;Inaktiv text&quot; på AEM Screens-enheten. (SCRNS-2614)

* XSS-problem `screens/dashboard/device.html` genom `Clear cache` åtgärdsdialogrutan. (SCRNS-2632)

* XSS-problem i skärmuppspelningskonfiguration på `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Lagrad XSS i enhetens titel utlöses när en enhet tas bort. (SCRNS-2653)

* XSS-problem `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* Speglad XSS med parametern `item` på `/screens/register-device-wizard.html`. (SCRNS-2670)

* Speglad XSS i `screens/dashboard/device.html` genom `returnPage` parameter. (SCRNS-3056)

* Öppna Omdirigering om assign-device-wizard.html. (SCRNS-3444)

* Öppna omdirigering på enhetspanelen. (SCRNS-3443)

* XSS-problem `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Åtgärdade, saknade upprepningsschema och Lägg till schemaknappar: Ett problem upptäcktes i kanalschemaläggningen. (SCRNS-2739)
