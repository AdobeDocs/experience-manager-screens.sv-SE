---
title: Miljöer för [!UICONTROL AEM Screens]
description: Läs mer om miljöerna i ett AEM Screens-projekt.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---


# Miljö {#environments}

Avgör i förväg vilka AEM som kunden har och väntar sig att du ska använda, båda för *utveckling* och *distribution*.

>[!NOTE]
>
>AEM Screens kräver flera paket för att projekt ska fungera. Alla miljöer bör ha samma version av Adobe Experience Manager.

Följ riktlinjerna nedan för att konfigurera miljön för ditt AEM Screens-projekt:

1. Kör de senaste versionerna av följande paket för din version av Adobe Experience Manager:

   * **AEM Service Pack**
   * **Funktionspaket för skärmar**
   * **AEM Kumulativt korrigeringspaket**

1. Identifiera eventuella utvecklingspaket (till exempel WCM Core-komponenter) eller verktygspaket från tredje part (till exempel SAP Hybris) som krävs.

1. Installera samma programvarupaket i den lokala utvecklingsmiljön.

1. Instruera klienten att använda samma konfiguration på alla QA-, Stage- och Production-servrar. Felmatchade serverkonfigurationer skapar problem vid distribuering och testning.
