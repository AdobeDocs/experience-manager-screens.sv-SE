---
title: Dispatcher Configurations for AEM Screens
seo-title: Dispatcher Configurations for AEM Screens
description: På den här sidan hittar du riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.
seo-description: This page highlights guidelines for configuring dispatcher for an AEM Screens project.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Dispatcher Configurations for AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher är Adobe Experience Managers verktyg för cachelagring och/eller belastningsutjämning.

Följande sida innehåller riktlinjer för hur du konfigurerar dispatcher för ett AEM Screens-projekt.

>[!NOTE]
>
>Om en dispatcher är tillgänglig kan anslutningar till registreringsservern förhindras genom filtrering i dispatcherreglerna.
>
>Om det inte finns någon dispatcher inaktiverar du registreringstjänsten i OSGi-komponentlistan.

Innan du konfigurerar dispatcher för ett AEM Screens-projekt måste du ha tidigare kunskaper om Dispatcher.
Se [Konfigurera Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) för mer information.

## Konfigurera Dispatcher för manifestversion v2 {#configuring-dispatcher}

>[!IMPORTANT]
>Följande Dispatcher-konfigurationer gäller endast Manifest version v2. Se [Dispatcher Configurations for Manifest version v3](#configuring-dispatcherv3) för manifestversion v3.

AEM Screens spelare eller enheter använder autentiserad session för att få tillgång till resurserna i publiceringsinstanserna. Om du har flera publiceringsinstanser bör förfrågningarna alltid gå till samma publiceringsinstans så att den autentiserade sessionen är giltig för alla förfrågningar som kommer från AEM Screens spelare/enheter.

Följ stegen nedan för att konfigurera dispatcher för ett AEM Screens-projekt.

### Aktivera anteckningssessioner {#enable-sticky-session}

Om du vill använda flera publiceringsinstanser som föregås av en enda dispatcher måste du uppdatera `dispatcher.any` fil för att aktivera klickbarhet

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Om du har en publiceringsinstans framför en dispatcher kommer det inte att hjälpa om du aktiverar klisterlappningen vid dispatchern eftersom belastningsutjämnaren kan skicka varje begäran till dispatchern. I så fall klickar du på **Aktivera** in **Stickande** -fält för att aktivera det på belastningsutjämnarnivå, enligt bilden nedan:

![bild](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Om du t.ex. använder AWS ALB, se [Målgrupper för programmets belastningsutjämnare](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) för att möjliggöra klisterhet på ALB-nivå. Aktivera klibbighet i en dag.

### Steg 1: Konfigurera klienthuvuden {#step-configuring-client-headers}

Lägg till följande i `/clientheaders`avsnitt:

**X-requested-with**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Steg 2: Konfigurera skärmfilter {#step-configuring-screens-filters}

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

### Steg 3: Inaktiverar Dispatcher Cache {#step-disabling-dispatcher-cache}

Inaktivera dispatcher-cachning för ***/content/screens sökväg***.

Skärmspelare använder autentiserad session, så dispatchern cachelagrar inte någon av skärmspelarförfrågningarna för `channels/assets`.

Om du vill aktivera cacheminnet för resurserna så att resurserna hanteras från dispatcherns cacheminne måste du:

* Lägg till `/allowAuthorization 1` in `/cache` section
* Lägg till nedanstående regler i `/rules` avsnitt i `/cache`

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

## Konfigurera Dispatcher för manifestversion v3{#configuring-dispatcherv3}

Se till att tillåta dessa filter och cachelagra regler i utskickare som kör publiceringsinstanserna för att fungera med skärmar.

### Krav för manifestversion v3{#prerequisites3}

Följ dessa två krav innan du konfigurerar Dispatcher (manifestversion v3) för AEM Screens:

* Se till att du använder `v3 manifests`. Navigera till `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` och se till att `Enable ContentSync Cache` är inte markerad.

* Kontrollera att agenten för rensning av dispatcher är konfigurerad på `/etc/replication/agents.publish/dispatcher1useast1Agent` i publiceringsinstans.

   ![bild](/help/user-guide/assets/dispatcher/dispatcher-1.png)

   ![bild](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filter  {#filter-v3}

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
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### Cache-regler {#cache-rules-v3}

* Lägg till `/allowAuthorized "1"` till `/cache` avsnitt i `publish_farm.any`.

* Alla skärmspelare använder autentiserad session för att ansluta till AEM (författare/publicering). Den färdiga Dispatcher cachelagrar inte dessa URL:er, så vi bör aktivera dessa.

* Lägg till `statfileslevel "10"` till `/cache` avsnitt i `publish_farm.any`
Detta stöder cachelagring av upp till 10 nivåer från cachedokumentroten och gör innehållet ogiltigt när innehållet publiceras, i stället för att göra allt ogiltigt. Du kan ändra den här nivån baserat på hur detaljerad innehållsstrukturen är

* Lägg till följande i `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Lägg till följande regler i `/rules` avsnitt i `/cache` in `publish_farm.any` eller i en fil som inkluderas från `publish_farm.any`:

   ```
   ## Don't cache CSRF login tokens
   /0001
       {
       /glob "/libs/granite/csrf/token.json"
       /type "deny"
       }
   ## Allow Dispatcher Cache for Screens channels
   /0002
       {
           /glob "/content/screens/*.html"
           /type "allow"
       }
   ## Allow Dispatcher Cache for Screens offline manifests
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   ## Allow Dispatcher Cache for Assets
   /0004
       {
   
       /glob "/content/dam/*"
       /type "allow"
       }
   ## Disable Dispatcher Cache for Screens devices json
   /0005
       {
       /glob "/home/users/screens/*.json"
       /type "deny"
       }
   ## Disable Dispatcher Cache for Screens svc json
   /0006
       {
       /glob "/content/screens/svc.json"
       /type "deny"
       }
   ```

### Lägg till ogiltighetsregel för segment.js {#invalidsegmentjs}

Om ni använder målinriktade kampanjer med AEM Screens `segments.js file` som skickas av avsändaren måste ogiltigförklaras när du lägger till och publicerar nya segment på AEM. Utan den här ogiltigförklaringsregeln kommer nya riktade kampanjer inte att fungera i skärmspelaren (standardinnehållet visas i stället).

* Lägg till en ogiltigförklaringsregel i `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Här följer en regel som ska läggas till:

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* Den här regeln säkerställer att `segments.js` filen är ogiltig och den senaste hämtas när den ändras.
