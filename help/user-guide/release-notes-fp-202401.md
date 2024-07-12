---
title: Versionsinformation om Screens Feature Pack 202401
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

Du kan hämta det senaste funktionspaketet för AEM Screens 6.5.11.1 från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Gå till fliken **Adobe Experience Manager** och sök efter **Screens** för att få den senaste funktionspaketet med namnet **AEM 6.5 Screens FP11.1**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202204 är 2 januari 2024.

### Nyheter {#what-is-new}

Den här versionen innehåller endast säkerhetskorrigeringar.

### Felkorrigeringar {#bug-fixes}

* XSS-problem i fältet&quot;Inaktiv text&quot; på AEM Screens-enheten. (SCRNS-2614)

* XSS-problem vid `screens/dashboard/device.html` via åtgärdsdialogrutan `Clear cache`. (SCRNS-2632)

* XSS-problem i skärmuppspelningskonfigurationen på `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Lagrad XSS i enhetens titel utlöses när en enhet tas bort. (SCRNS-2653)

* XSS-utgåva `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* Speglade XSS med parametern `item` vid `/screens/register-device-wizard.html`. (SCRNS-2670)

* Speglade XSS i `screens/dashboard/device.html` med parametern `returnPage`. (SCRNS-3056)

* Öppna Omdirigering om assign-device-wizard.html. (SCRNS-3444)

* Öppna omdirigering på enhetspanelen. (SCRNS-3443)

* XSS-utgåva `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Åtgärdade, saknade upprepningsschema och Lägg till schemaknappar: Ett problem upptäcktes i kanalschemaläggningen. (SCRNS-2739)
