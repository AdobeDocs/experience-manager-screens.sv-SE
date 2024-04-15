---
title: Support och underhåll dag två
description: Läs mer om support och underhåll för AEM Screens dag två.
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Day Two Platform Support and Maintenance {#day-two-support-maintenance}

AEM Screens kräver flera paket för att projekt ska fungera. Alla miljöer måste ha samma version av Adobe Experience Manager.

Följ riktlinjerna för stöd och underhåll för dag två av projektutvecklingsfasen:

1. Kör de senaste versionerna av följande paket för din version av Adobe Experience Manager:

   * **AEM Service Pack**
   * **Funktionspaket för skärmar**
   * **AEM Kumulativt korrigeringspaket**

1. Identifiera eventuella utvecklingspaket (till exempel WCM Core-komponenter) eller verktygspaket från tredje part (till exempel SAP Hybris) som krävs.

1. Installera samma programvarupaket på den lokala utvecklingsmiljön.

1. Instruera klienten att använda samma konfiguration på alla QA-, Stage- och Production-servrar. Felmatchade serverkonfigurationer skapar problem vid distribuering och testning.
