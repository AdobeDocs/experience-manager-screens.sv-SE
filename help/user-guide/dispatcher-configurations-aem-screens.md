---
title: Dispatcher Configurations for AEM Screens
seo-title: Dispatcher Configurations for AEM Screens
description: På den här sidan hittar du riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.
seo-description: På den här sidan hittar du riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.
translation-type: tm+mt
source-git-commit: 4a1fb81fa343983093590c36ccb6a4fd110cdad2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 4%

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

Mer information finns i [Konfigurera Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html).

## Konfigurerar Dispatcher {#configuring-dispatcher}

Följ stegen nedan för att konfigurera dispatcher för ett AEM Screens-projekt.

### Aktivera anteckningssessioner {#enable-sticky-session}

Om du vill använda mer än en publiceringsinstans med dispatcher måste du uppdatera `dispatcher.any`-filen.

```xml
/stickyConnections {
  /paths
  {
    "/content/screens"
    "/home/users/screens"
    "/libs/granite/csrf/token.json"
  }
}
```

### Steg 1: Konfigurerar klientrubriker {#step-configuring-client-headers}

Lägg till följande i `/clientheaders`avsnittet:

**X-requested-with**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Steg 2: Konfigurerar skärmfilter {#step-configuring-screens-filters}

Om du vill konfigurera skärmfilter lägger du till följande i ***/filter***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Steg 3: Inaktiverar Dispatcher-cache {#step-disabling-dispatcher-cache}

Inaktivera dispatcher-cachning för ***/content/screens path***.

Skärmspelare använder autentiserad session, så dispatchern cachelagrar inte någon av skärmspelarförfrågningarna för `channels/assets`.

Om du vill aktivera cacheminnet för resurserna så att resurserna hanteras från dispatcherns cacheminne måste du:

* Lägg till `/allowAuthorization 1` i `/cache`-avsnittet
* Lägg till nedanstående regler i `/rules`-avsnittet i `/cache`

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```
