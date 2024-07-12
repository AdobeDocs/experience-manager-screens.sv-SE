---
title: Dispatcher Configurations for AEM Screens
description: På den här sidan hittar du riktlinjer för hur du konfigurerar Dispatcher för ett AEM Screens-projekt.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Dispatcher Configurations for AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher är Adobe Experience Manager cachning, eller belastningsutjämningsverktyg, eller båda.

Följande sida innehåller riktlinjer för hur du konfigurerar en Dispatcher för ett AEM Screens-projekt.

>[!NOTE]
>
>Om det finns en Dispatcher kan du förhindra anslutningar till registreringsservern genom att filtrera i Dispatcher-reglerna.
>
>Om det inte finns någon Dispatcher inaktiverar du registreringstjänsten i OSGi-komponentlistan.

Innan du konfigurerar Dispatcher för ett AEM Screens-projekt måste du ha kunskap om Dispatcher.
Mer information finns i [Konfigurera Dispatcher](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration).

## Konfigurera Dispatcher för manifestversion v2 {#configuring-dispatcher}

>[!IMPORTANT]
>Följande Dispatcher-konfigurationer gäller endast Manifest version v2. Se [Dispatcher Configurations for Manifest version v3](#configuring-dispatcherv3) för Manifest version v3.

AEM Screens spelare eller enheter använder en autentiserad session för att få tillgång till resurserna i publiceringsinstanserna. Om du har flera publiceringsinstanser bör förfrågningarna alltid gå till samma Publishing-instans så att den autentiserade sessionen är giltig för alla förfrågningar som kommer från AEM Screens spelare eller enheter.

Följ stegen nedan för att konfigurera Dispatcher för ett AEM Screens-projekt.

### Aktivera anteckningssessioner {#enable-sticky-session}

Om du vill använda flera publiceringsinstanser som föregås av en enda Dispatcher uppdaterar du filen `dispatcher.any` så att den blir densamma.

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Om du har en publiceringsinstans som föregås av en Dispatcher hjälper inte aktiveringen av klisterlappningen på Dispatcher eftersom belastningsutjämnaren kan skicka varje begäran till Dispatcher. I det här fallet klickar du på **Aktivera** i fältet **Stickiness** för att aktivera det på belastningsutjämnarnivån, vilket visas i bilden nedan:

![bild](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Om du till exempel använder AWS ALB läser du [Målgrupper för Application Load Balancers](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) för att aktivera klisterhet på ALB-nivå. Gör klivet i en dag.

### Steg 1: Konfigurera klienthuvuden {#step-configuring-client-headers}

Lägg till följande i avsnittet `/clientheaders`:

**x-requested-with**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Steg 2: Konfigurera Screens-filter {#step-configure-screens-filters}

Om du vill konfigurera Screens-filter lägger du till följande i ***`/filter`***.

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

### Steg 3: Inaktivera Dispatcher Cache {#step-disabling-dispatcher-cache}

Inaktivera Dispatcher-cachelagring för sökvägen ***/content/screens***.

Screens-spelare använder autentiserade sessioner, så Dispatcher cachelagrar inte någon av skärmspelarförfrågningarna för `channels/assets`.

Så här aktiverar du cacheminnet för resurserna så att resurserna hanteras från Dispatcher-cachen:

* Lägg till `/allowAuthorization 1` i avsnittet `/cache`
* Lägg till nedanstående regler i avsnittet `/rules` i `/cache`

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

Se till att tillåta dessa filter och cachelagra regler i utskickare som kör Publishing-instanser för att Screens ska fungera.

### Krav för manifestversion v3{#prerequisites3}

Följ dessa två krav innan du konfigurerar en Dispatcher (manifestversion v3) för AEM Screens:

* Kontrollera att du använder `v3 manifests`. Navigera till `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` och kontrollera att `Enable ContentSync Cache` inte är markerad.

* Kontrollera att Dispatcher rensningsagent har konfigurerats på `/etc/replication/agents.publish/dispatcher1useast1Agent` i publiceringsinstansen.

  ![bild](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![bild](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filter {#filter-v3}

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

* Lägg till `/allowAuthorized "1"` i avsnittet `/cache` i `publish_farm.any`.

* Alla AEM Screens-spelare använder en autentiserad session för att ansluta till AEM (författare/publicering). En Dispatcher cachelagrar inte dessa URL:er och du bör aktivera dem.

* Lägg till `statfileslevel "10"` i avsnittet `/cache` i `publish_farm.any`
Den här regeln stöder cachelagring av upp till tio nivåer från cache-dokumentet och gör innehållet ogiltigt i enlighet därmed när innehållet publiceras, i stället för att göra allt ogiltigt. Du kan ändra den här nivån baserat på hur detaljerad innehållsstrukturen är

* Lägg till följande i `/invalidate section in publish_farm.any`

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* Lägg till följande regler i avsnittet `/rules` i `/cache` i `publish_farm.any` eller i en fil som inkluderas från `publish_farm.any`:

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

Om du använder riktade kampanjer med AEM Screens måste `segments.js file` som hanteras av Dispatcher ogiltigförklaras när du lägger till och publicerar nya segment på AEM. Utan den här ogiltighetsregeln fungerar inte nya riktade kampanjer i AEM Screens Player (standardinnehållet visas i stället).

* Lägg till en ogiltighetsregel i `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Här följer en regel som ska läggas till:

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

* Den här regeln ser till att filen `segments.js` blir ogiltig och att den senaste hämtas när den ändras.
