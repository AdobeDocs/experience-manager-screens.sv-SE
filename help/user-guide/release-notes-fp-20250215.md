---
title: Versionsinformation om Screens Feature Pack 20250327
description: Läs mer om AEM Screens Feature Pack 20250327 som släpptes den 27 mars 2025.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: cadd83cd-fe64-436d-b3fd-6d72b9565885
source-git-commit: 6cdf350fa4e45b816d50b64252b8ed6d5e0904d0
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 20250327 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe rekommenderar att du uppgraderar till den senaste versionen av 6.5 Adobe Experience Manager (AEM 6.5). Du kan hämta den senaste versionsinformationen från [här](https://experienceleague.adobe.com/sv/docs/experience-manager-65/content/release-notes/release-notes).
>&#x200B;>Adobe rekommenderar att du använder FP11.6 med SP(servicepack) >= 21.

## Tillgänglighet {#availability}

AEM Screens har släppt AEM 6.5 Feature Pack 11.6.

Du kan hämta det senaste funktionspaketet för AEM Screens 6.5.11.6 från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Gå till fliken **Adobe Experience Manager** och sök efter **Screens** för att få den senaste funktionspaketet med namnet **AEM 6.5 Screens FP11.6**.

## Releasedatum {#release-date}

Lanseringsdatumet för AEM Screens Feature Pack 20250327 är 27 mars 2025.

### Nyheter {#what-is-new}

* Den här versionen åtgärdar den paketkonflikt som användare möter med Service Pack 21 och senare.

* Den här versionen åtgärdar problemet med kortvyn med SP22 och senare.

* **Uppdatera i AEM Screens Players**
   * Den Linux-baserade AEM Screens Player är officiellt föråldrad. Användare rekommenderas att migrera till ett annat operativsystem som stöds av AEM Screens.
   * Inga fler uppdateringar eller förbättringar görs av den Android-baserade AEM Screens Player. Vi rekommenderar att man migrerar till ett annat operativsystem som AEM Screens stöder.

### Felkorrigeringar {#bug-fixes}

* Paketkonflikt med Service Pack 21 och Screens Feature Pack. (SCRNS-4638)

* Screens Dashboard fungerar inte. (SCRNS-4749)

* XSS-problem på /libs/screens/dcc/components/dashboard/clientlibs/device-clear-cache.js (SCRNS-4761)
