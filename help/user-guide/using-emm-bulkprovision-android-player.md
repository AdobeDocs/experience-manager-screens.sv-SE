---
title: Använda MDM eller EMM för att massdistribuera Android Player
seo-title: Massetablering av Android Player med EMM eller MDM
description: Följ den här sidan om du vill veta mer om massetablering av Android-spelare med EMM eller MDM
translation-type: tm+mt
source-git-commit: 793507b266b99051544b377e4a7effb92dc6feb6
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# Massetablering av Android Player med Enterprise Mobility Management {#bulk-provisioning}

När du distribuerar Android-spelaren i grupp blir det omständligt att manuellt registrera alla spelare med AEM. Vi rekommenderar att du använder en EMM-lösning (Enterprise Mobility Management), som VMWare Airwatch, MobileIron eller Samsung Knox, för att fjärrdistribuera och hantera distributionen. AEM Screens Android-spelaren har stöd för den branschledande EMM AppConfig som tillåter fjärretablering.

## Implementera massetablering av Android Player med Enterprise Mobility Management {#implementation}

Följ stegen nedan för att tillåta massetablering i Android Player:

1. Kontrollera att din Android-enhet har stöd för Google Play-tjänster.
1. Registrera dina Android-enheter med din EMM-favoritlösning som stöder AppConfig.
1. Logga in på EMM-konsolen och hämta AEM Screens Player från Google Play.
1. Välj hanterad konfiguration (eller relaterat alternativ).
1. Nu bör du se en lista över spelaralternativ som kan konfigureras (till exempel serverkod och bulkregistreringskod).
1. Konfigurera de här parametrarna, spara och distribuera principen till enheterna.

   >[!NOTE]
   >Enheterna bör ta emot programmet tillsammans med konfigurationen och peka på rätt AEM med den valda konfigurationen. Om du väljer att konfigurera gruppregistreringskoden och behåller den som den konfigurerats i AEM, bör spelaren kunna registrera sig automatiskt. Om du har konfigurerat en standardskärm kan den även hämta och visa visst standardinnehåll (som senare kan ändras efter behov).

Dessutom bör du höra med din EMM-leverantör om AppConfig-stöd. De vanligaste är till exempel [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) och [Samsung Knox a11/> stöder bland annat denna branschstandard.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)


