---
title: Miljöer för [!UICONTROL AEM Screens]
seo-title: Miljöer för [!UICONTROL AEM Screens]
description: På den här sidan beskrivs miljöerna för ett AEM Screens-projekt.
seo-description: På den här sidan beskrivs miljöerna för ett AEM Screens-projekt.
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Miljöer {#environments}

Bestäm i förväg vilka AEM miljöer klienten har och kommer att förvänta sig att du använder, både för *utveckling* och *distribution*.

>[!NOTE]
>
>AEM Screens kräver flera paket för att projekt ska fungera. Alla miljöer bör ha samma version av Adobe Experience Manager.

Följ riktlinjerna nedan för att konfigurera miljön för ditt AEM Screens-projekt:

1. Kör de senaste versionerna av följande paket för din version av Adobe Experience Manager:

   * **AEM Service Pack**
   * **Funktionspaket för skärmar**
   * **AEM Kumulativt korrigeringspaket**

1. Identifiera eventuella utvecklingspaket (till exempel WCM Core-komponenter) eller verktygspaket från tredje part (till exempel SAP Hybris) som krävs.

1. Installera samma programvarupaket i dina lokala utvecklingsmiljöer.

1. Instruera klienten att använda samma konfiguration på alla QA-, Stage- och Production-servrar. Serverkonfigurationer som inte matchar skapar problem vid distribution och testning.
