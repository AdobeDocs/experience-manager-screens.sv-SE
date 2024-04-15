---
title: AEM plattformskonfigurationer
description: Sidan beskriver AEM plattformskonfigurationer
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 2%

---

# AEM plattformskonfigurationer  {#platform-configurations}

>[!NOTE]
>
>En typisk intressent för den här aktiviteten är en AEM implementerare.

Kom igång med AEM Screens genom att följa avsnitten nedan för att konfigurera AEM plattformskonfigurationer

## Serverkonfigurationer {#server-configurations}

Information om hur du konfigurerar servrar finns i [Serverkonfigurationer](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Författare-Publicera {#author-publish}

Se [Konfigurera författare och publicera i AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>Om det bara finns en författare och en publicering följer du bara stegen under **Konfigurera replikeringsagenter på författare** in [Konfigurera författare och publicera i AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish) sida.

## Dispatcher Configurations {#dispatcher-configurations}

Dispatcher är ett Adobe Experience Manager verktyg för cachelagring och lastbalansering. AEM:s Dispatcher skyddar också AEM-servern mot angrepp. Därför kan du öka säkerheten för AEM genom att använda Dispatcher med en webbserver i företagsklass.

Se **[Dispatcher Configurations for AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** som innehåller riktlinjer för hur du konfigurerar Dispatcher för ett AEM Screens-projekt.

## Installera FFMpeg och videoåtergivningar {#installing-ffmpeg}

Installera FFMpeg genom att följa stegen för lämpligt operativsystem (vanligen RHEL):

1. Om du installerar genom att aktivera EPEL och RPMFusion kan du installera alla gstreamer-kodekar för att bredda stödet för FFmpeg-konverteringar
1. Om AAC-kodeken markeras som experimentell misslyckas ffmpeg-konverteringarna. För att undvika det här tillägget `-strict -2` till videoprofilerna (/etc/dam/video i AEM 6.3 och flyttad till /libs/settings/dam/video i AEM 6.4)

   >[!NOTE]
   >
   >The `-strict -2` måste vara den sista parametern i parameterlistan. I AEM 6.4 kan du även kopiera noderna under */libs/settings/dam/video* till */conf/global/settings/dam/video* som anges i [Videoåtergivningar](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Kontrollera att videokonverteringar pågår och att återgivningar skapas.

## Lösenordsbegränsningar {#password-restrictions}

Lösenordsprincipen för AEM måste inaktiveras för AMS-instansen. Detta kan konfigureras växelvis i webbkonsolen med enhetstjänsten Skärmar *com.adobe.cq.screens.device.impl.DeviceService*
Se **Lösenordsbegränsningar** avsnitt i[Konfigurera författare och publicera i AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Konfigurera miljöer {#setting-up-environments}

Installera och kör de senaste versionerna av följande paket för din version av Adobe Experience Manager (AEM):

* AEM Service Pack
* Funktionspaket för skärmar
* AEM Kumulativt korrigeringspaket

Förutom ovanstående bör du även identifiera eventuella utvecklingspaket (till exempel WCM Core-komponenter) eller tredjepartsverktyg (till exempel SAP Hybris) som krävs.
Installera samma programvarupaket på den lokala utvecklingsmiljön. Instruera klienten att använda samma konfiguration på alla QA-, Stage- och Production-servrar. Felmatchade serverkonfigurationer skapar problem vid distribuering och testning.

>[!NOTE]
>
>Information om hur du installerar det senaste funktionspaketet för AEM Screens finns i [Versionsinformation](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Konfigurera åtkomstkontrollistor {#setting-up-acls}

När du konfigurerar åtkomstkontrollistor beskrivs hur du skiljer ut projekt så att varje enskild person eller grupp hanterar sitt eget projekt.

Se [Konfigurera åtkomstkontrollistor](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls) för mer information.
