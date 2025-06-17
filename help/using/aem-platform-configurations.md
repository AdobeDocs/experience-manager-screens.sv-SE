---
title: AEM Platform Configurations
description: På sidan beskrivs AEM Platform Configurations
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 2%

---

# AEM Platform Configurations {#platform-configurations}

>[!NOTE]
>
>En typisk aktör inom denna verksamhet är en AEM-implementerare.

Kom igång med AEM Screens genom att följa avsnitten nedan för att konfigurera AEM plattformskonfigurationer

## Serverkonfigurationer {#server-configurations}

Mer information om hur du konfigurerar servrar finns i [Serverkonfigurationer](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Författare-Publicera {#author-publish}

Se [Konfigurera författare och publicera i AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>Om det bara finns en författare och en publicering kan du bara följa stegen under **Konfigurera replikeringsagenter för författare** på sidan [Konfigurera författare och publicera i AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

## Dispatcher Configurations {#dispatcher-configurations}

Dispatcher är Adobe Experience Manager verktyg för cachning och lastbalansering. AEM:s Dispatcher skyddar också AEM-servern mot angrepp. Därför kan du öka säkerheten för din AEM-instans genom att använda Dispatcher med en webbserver i företagsklass.

Se **[Dispatcher Configurations for AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** som visar riktlinjer för hur du konfigurerar Dispatcher för ett AEM Screens-projekt.

## Installera FFMpeg och videoåtergivningar {#installing-ffmpeg}

Installera FFMpeg genom att följa stegen för lämpligt operativsystem (vanligen RHEL):

1. Om du installerar genom att aktivera EPEL och RPMFusion kan du installera alla gstreamer-kodekar för att bredda stödet för FFmpeg-konverteringar
1. Om AAC-kodeken markeras som experimentell misslyckas ffmpeg-konverteringarna. För att undvika det här problemet lägger du till `-strict -2` i videoprofilerna (`/etc/dam/video` i AEM 6.3 och flyttar till `/libs/settings/dam/video in AEM 6.4`)

   >[!NOTE]
   >
   >`-strict -2` måste vara den sista parametern i parameterlistan. I AEM 6.4 kopierar du även noderna under */libs/settings/dam/video* till */conf/global/settings/dam/video* som anges i [Videoåtergivningar](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Kontrollera att videokonverteringar pågår och att återgivningar skapas.

## Lösenordsbegränsningar {#password-restrictions}

AEM lösenordsprincip måste inaktiveras på AMS-instansen. Den kan också konfigureras växelvis i webbkonsolen med hjälp av Screens enhetstjänst *com.adobe.cq.screens.device.impl.DeviceService*
Se avsnittet **Lösenordsbegränsningar** i [Konfigurera författare och publicera i AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Konfigurera miljöer {#setting-up-environments}

Installera och kör de senaste versionerna av följande paket för din version av Adobe Experience Manager (AEM):

* AEM Service Pack
* Screens Feature Pack
* AEM Cumulative Fix Pack

Förutom ovanstående kan du även identifiera utvecklingspaket (t.ex. WCM Core
-komponenter) eller tredjepartsverktyg (till exempel SAP Hybris) som krävs.
Installera samma programvarupaket i den lokala utvecklingsmiljön. Instruera klienten att använda samma konfiguration på alla QA-, Stage- och Production-servrar. Felmatchade serverkonfigurationer skapar problem vid distribuering och testning.

>[!NOTE]
>
>Information om hur du installerar det senaste funktionspaketet för AEM Screens finns i [Versionsinformation](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Konfigurera åtkomstkontrollistor {#setting-up-acls}

När du konfigurerar åtkomstkontrollistor beskrivs hur du skiljer ut projekt så att varje enskild person eller grupp hanterar sitt eget projekt.

Mer information finns i [Konfigurera åtkomstkontrollistor](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls).
