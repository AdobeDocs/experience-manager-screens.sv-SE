---
title: Support och underhåll dag två
seo-title: Support och underhåll för AEM-skärmar dag två
description: På sidan beskrivs Day Two Support and Maintenance
seo-description: På sidan beskrivs Day Two Support and Maintenance
translation-type: tm+mt
source-git-commit: 5c83a2b59769dfd3736a830f7d7d3cc35137c182

---


# Day Two Platform Support and Maintenance {#day-two-support-maintenance}

AEM-skärmar kräver flera paket för att projekten ska fungera. Alla miljöer bör ha samma version av Adobe Experience Manager.

Följ riktlinjerna för stöd och underhåll för dag två av projektutvecklingsfasen:

1. Kör de senaste versionerna av följande paket för din version av Adobe Experience Manager:

   * **AEM Service Pack**
   * **Funktionspaket för skärmar**
   * **AEM Cumulative Fix Pack**

1. Identifiera eventuella utvecklingspaket (till exempel WCM Core-komponenter) eller tredjepartsverktyg (till exempel SAP Hybris) som krävs.

1. Installera samma programvarupaket i dina lokala utvecklingsmiljöer.

1. Instruera klienten att använda samma konfiguration på alla QA-, Stage- och Production-servrar. Serverkonfigurationer som inte matchar skapar problem vid distribution och testning.
