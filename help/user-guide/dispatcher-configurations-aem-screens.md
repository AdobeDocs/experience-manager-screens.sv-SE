---
title: Dispatcher Configurations for AEM Screens
seo-title: Dispatcher Configurations for AEM Screens
description: På den här sidan hittar du riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.
seo-description: På den här sidan hittar du riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.
feature: Administrera skärmar
role: Developer, Business Practitioner
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 3%

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

AEM Screens spelare/enheter använder autentiserad session för att få tillgång till resurserna i publiceringsinstanserna. Om du har flera publiceringsinstanser bör förfrågningarna alltid gå till samma publiceringsinstans så att den autentiserade sessionen är giltig för alla förfrågningar som kommer från AEM Screens spelare/enheter.

Följ stegen nedan för att konfigurera dispatcher för ett AEM Screens-projekt.

### Aktivera anteckningssessioner {#enable-sticky-session}

Om du vill använda flera publiceringsinstanser som körs med en enda dispatcher måste du uppdatera `dispatcher.any`-filen för att aktivera taggighet

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Om du har en publiceringsinstans framför en dispatcher kommer det inte att hjälpa om du aktiverar klisterlappningen vid dispatchern eftersom belastningsutjämnaren kan skicka varje begäran till dispatchern. I det här fallet klickar du på **Aktivera** i **aktivitetsfältet** för att aktivera det på belastningsutjämnarnivå, vilket visas i bilden nedan:

![bild](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Om du till exempel använder AWS ALB läser du [Målgrupper för Utjämning av programbelastning](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) för att aktivera klisterhet på ALB-nivå. Aktivera klibbighet i en dag.

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
