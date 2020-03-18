---
title: Miljöer för [!UICONTROL AEM Screens]
seo-title: Miljöer för [!UICONTROL AEM Screens]
description: Den här sidan beskriver miljöerna för ett AEM Screens-projekt.
seo-description: Den här sidan beskriver miljöerna i ett AEM Screens-projekt.
translation-type: tm+mt
source-git-commit: 0d91aa653508969cf1f4ccfba23a570e22e6414c

---


# Miljöer {#environments}

Bestäm i förväg vilka AEM-miljöer kunden har och kommer att förvänta sig att du använder, både för *utveckling* och *distribution*.

>[!NOTE]
>
>AEM-skärmar kräver flera paket för att projekten ska fungera. Alla miljöer bör ha samma version av Adobe Experience Manager.

Följ riktlinjerna nedan för att konfigurera miljön för ditt AEM Screens-projekt:

1. Kör de senaste versionerna av följande paket för din version av Adobe Experience Manager:

   * **AEM Service Pack**
   * **Funktionspaket för skärmar**
   * **AEM Cumulative Fix Pack**

1. Identifiera eventuella utvecklingspaket (till exempel WCM Core-komponenter) eller tredjepartsverktyg (till exempel SAP Hybris) som krävs.

1. Installera samma programvarupaket i dina lokala utvecklingsmiljöer.

1. Instruera klienten att använda samma konfiguration på alla QA-, Stage- och Production-servrar. Serverkonfigurationer som inte matchar skapar problem vid distribution och testning.
