---
title: Dispatcher Configurations for AEM Screens
seo-title: Dispatcher Configurations for AEM Screens
description: På den här sidan visas riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.
seo-description: På den här sidan visas riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.
uuid: ec5219b7-73f9-4026-99e5-e4a02201b128
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 1b1a36a4-4f95-41e3-b0a8-74249efb0119
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 6%

---


# Dispatcher Configurations for AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher är Adobe Experience Managers verktyg för cachelagring och/eller belastningsutjämning.

Följande sida innehåller riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.

>[!NOTE]
>
>Om en dispatcher är tillgänglig kan anslutningar till registreringsservern förhindras genom filtrering i dispatcherreglerna.
>
>Om det inte finns någon dispatcher inaktiverar du registreringstjänsten i OSGi-komponentlistan.

## Krav {#pre-requisites}

Innan du konfigurerar dispatcher för ett AEM Screens-projekt måste du ha tidigare kunskaper om Dispatcher.

Mer information finns i [Konfigurera Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) .

## Konfigurera Dispatcher {#configuring-dispatcher}

Följ stegen nedan för att konfigurera dispatcher för ett AEM Screens-projekt.

### Steg 1: Konfigurera klienthuvuden {#step-configuring-client-headers}

Lägg till följande i `/clientheaders`avsnittet:

**X-requested-with**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Steg 2: Konfigurera skärmfilter {#step-configuring-screens-filters}

Om du vill konfigurera skärmfilter lägger du till följande i ***/filter***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Steg 3: Inaktiverar Dispatcher Cache {#step-disabling-dispatcher-cache}

Inaktivera Dispatcher-cachning för ***/content/screens-sökväg***.
