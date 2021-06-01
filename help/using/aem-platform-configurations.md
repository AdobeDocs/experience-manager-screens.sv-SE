---
title: AEM plattformskonfigurationer
seo-title: AEM plattformskonfigurationer
description: Sidan beskriver AEM plattformskonfigurationer
seo-description: Sidan beskriver AEM plattformskonfigurationer
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 18%

---

# AEM plattformskonfigurationer {#platform-configurations}

>[!NOTE]
>
>En typisk intressent för den här aktiviteten är en AEM implementerare.

Följ avsnitten nedan för att konfigurera AEM plattformskonfigurationer för att komma igång med AEM Screens.

## Serverkonfigurationer {#server-configurations}

Information om hur du konfigurerar servrar finns i [Serverkonfigurationer](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Författare-Publicera {#author-publish}

Mer information om hur du konfigurerar författarpublicering finns i [Konfigurera författare och publicera i AEM Screens](https://helpx.adobe.com/se/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Om det bara finns en författare och en publicering behöver du bara följa stegen under **Konfigurera replikeringsagenter på författare** på sidan [Konfigurera redigering och publicering i AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html).

## Dispatcher Configurations {#dispatcher-configurations}

Dispatcher är Adobe Experience Managers verktyg för cachelagring och/eller belastningsutjämning. AEM:s Dispatcher skyddar också AEM-servern mot angrepp. Därför kan du öka säkerheten för din AEM-instans genom att använda Dispatcher tillsammans med en företagswebbserver.

Mer information finns i **[Dispatcher Configurations for AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** som beskriver riktlinjer för konfigurering av dispatcher för ett AEM Screens-projekt.

## Installerar FFMpeg och videoåtergivningar {#installing-ffmpeg}

Installera FFMpeg genom att följa stegen för lämpligt operativsystem (vanligen RHEL):

1. Om du installerar genom att aktivera EPEL och RPMFusion kan du installera alla gstreamer-kodekar för att bredda stödet för FFmpeg-konverteringar
1. Om AAC-kodeken markeras som experimentell misslyckas ffmpeg-konverteringarna. För att undvika detta lägger du till -strict -2 i videoprofilerna (/etc/dam/video i AEM 6.3 och flyttar till /libs/settings/dam/video i AEM 6.4)
   >[!NOTE]
   >
   > Observera att -strict -2 måste vara den sista parametern i parameterlistan. I AEM 6.4 måste du dessutom kopiera noderna under */libs/settings/dam/video* till */conf/global/settings/dam/video* som anges i [Videoåtergivningar](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Kontrollera att videokonverteringar pågår och att återgivningar skapas.

## Lösenordsbegränsningar {#password-restrictions}

Lösenordsprincipen för AEM måste inaktiveras för AMS-instansen. Detta kan konfigureras växelvis i webbkonsolen med hjälp av skärmenhetstjänsten *com.adobe.cq.screens.device.impl.DeviceService*
Se **Lösenordsbegränsningar** i[Konfigurera författare och publicera i AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

## Konfigurera miljöer {#setting-up-environments}

Installera och kör de senaste versionerna av följande paket för din version av Adobe Experience Manager (AEM):

* AEM Service Pack
* Funktionspaket för skärmar
* AEM Kumulativt korrigeringspaket

Förutom ovanstående kan du även identifiera utvecklingspaket (t.ex. WCM Core
-komponenter) eller tredjepartsverktyg (till exempel SAP Hybris) som krävs.
Installera samma programvarupaket i dina lokala utvecklingsmiljöer. Instruera klienten att använda samma konfiguration på alla QA-, Stage- och Production-servrar. Serverkonfigurationer som inte matchar skapar problem vid distribution och testning.

>[!NOTE]
>
>Information om hur du installerar det senaste funktionspaketet för AEM Screens finns i [Versionsinformation](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Konfigurera åtkomstkontrollistor {#setting-up-acls}

När du konfigurerar åtkomstkontrollistor beskrivs hur du skiljer ut projekt så att varje enskild person eller grupp hanterar sitt eget projekt.

Mer information finns i [Konfigurera åtkomstkontrollistor](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html).
