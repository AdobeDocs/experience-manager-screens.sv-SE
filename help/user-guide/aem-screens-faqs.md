---
title: Vanliga frågor om AEM Screens
seo-title: Vanliga frågor om AEM Screens
description: Följ den här sidan för att få svar på vanliga frågor om ett AEM Screens-projekt.
seo-description: Följ den här sidan för att få svar på vanliga frågor om ett AEM Screens-projekt.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 3c78dd2f2f5cff421917eb5d657d8fd6fb2e3229
workflow-type: tm+mt
source-wordcount: '1819'
ht-degree: 0%

---


# Vanliga frågor om AEM Screens {#aem-screens-faqs}

I följande avsnitt ges svar på några av de vanligaste frågorna och svaren om ett AEM Screens-projekt.

## Problem med tom skärm {#blank-screen}

>[!NOTE]
>De obligatoriska kontroller som ska provas av primär support eller support på kundsidan innan ett problem uppstår.

### 1. Vilka är de första felsökningsstegen för hjälp till kunder som ser en svart skärm eller som inte spelar upp innehåll? {#troubleshooting-blank-screen}

* Kontrollera om kanalförhandsgranskningen fungerar.
* Kontrollera om förhandsvisningen fungerar
* Prova att registrera spelaren som ett webbläsartillägg på datorn på samma skärm och kontrollera om det fungerar.
* Navigera till `http://localhost:24502` när spelaren körs på datorn. Kontrollera om allt innehåll har laddats ned korrekt.
* Kontrollera de resurser som de lämpliga återgivningarna skapas för och att rätt återgivning spelas upp.
* Kontrollera om det finns schemalagt innehåll och om tiderna är korrekta. Kontrollera om tiden som är inställd i spelaren är korrekt.
* Inspect spelarkonsolen loggar och söker efter eventuella fel. Högerklicka och inspektera för att se konsolloggarna. Om du använder Windows-spelaren trycker du på `CTRL + ALT +I` för att öppna dev-konsolen för att visa loggarna.

### 2. Hur löser jag problem med gråskärm i AEM Screens genom att skapa en standardkanal eller ett schema?

För att undvika tomma eller grå skärmar i fältet skapar du en global standardkanal eller ett standardschema som tilldelas alla skärmar med lägst prioritet 1. Om något skulle gå fel med innehållsuppdateringar (på grund av nätverk, spelare, server eller replikering), eftersom spelarna redan har det här innehållet cachelagrat på disken, som ska spelas upp korrekt och undvika de grå skärmarna.

Allt annat innehåll, som kanaler eller scheman, har högre prioritet än 1, så det andra innehållet har högre prioritet och globalt kanalinnehåll eller schemaläggningsinnehåll (med prioritet 1) spelas endast upp som ett reservalternativ.

## Kanalhantering {#channel-management}

### 1. Vad är skillnaden mellan en online- och en offlinekanal? {#what-is-the-difference-between-an-online-and-an-offline-channel}

En ***onlinekanal*** visar det uppdaterade innehållet i realtidsmiljön medan en ***offlinekanal*** visar det cachelagrade innehållet.

### 2. Hur gör jag en kanal online? {#how-do-i-make-a-channel-online}

Markera kanalen och navigera till kanalegenskaper i åtgärdsfältet. Markera **Utvecklarläge (tvinga kanalen att vara online)** under fliken **Kanal** för att göra kanalen online.

### 3. Hur används fältet Kanalroll? {#what-is-the-use-of-the-channel-role-field}

Kanalrollen är förkortningen av den faktiska kanal som körs så att författaren kan fokusera direkt på den generiska upplevelsen. Du kan tänka dig det som en typ av tagg som unikt identifierar kanalen i sitt sammanhang (visning eller schema).

### 4. Hur sker faktisk kanalupplösning? {#how-does-actual-channel-resolution-happen}

För *statiska referenser* följer upplösningen bara den angivna sökvägen.

För *dynamiska referenser* inträffar upplösningen när kanalen har tilldelats till visningen (inte schemat). Visningsbanan blir kontext för kanalen och upplösningen sker enligt följande (högsta till lägsta prioritet):

1. Visningen har en underordnad nod som matchar det refererade kanalnamnet
1. Visningen har en nod på samma nivå som det refererade kanalnamnet
1. Visningens överordnade plats har en underordnad nod som matchar det refererade kanalnamnet
1. Den överordnade platsen för visningen har en underordnad nod som matchar det refererade kanalnamnet

Och så vidare, tills du når platsmappen och stoppar den där just nu (så att du inte kan referera till en kanal som till exempel finns i kanalmappen, är det bara kanaler i platsernas underträd).

## Enhetsregistrering {#device-registration}

### 1. Om jag upptäcker slutpunkter som begäran om registrering och registrering av enheter kan jag skripta ett stort antal enheter och registrera dessa enheter. Är det möjligt att skydda dessa förfrågningar förutom att låsa detta till en gren-Wi-Fi? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Registrering är för närvarande bara möjligt på författarinstansen. Registreringstjänsten är inte autentiserad, men skapar bara en väntande enhet i AEM och registrerar inte enheten eller tilldelar någon skärm.

Om du vill registrera en enhet (vilket innebär att du skapar en användare för enheten i AEM) måste du fortfarande autentisera till AEM och för närvarande följa registreringsguiden manuellt för att slutföra registreringen. Teoretiskt sett kan en oärlig användare skapa flera väntande enheter, men kan inte registrera några utan en AEM inloggning.

### 2. Finns det något sätt att omvandla HTTP GET-begäranden till HTTP-POST med någon form av autentisering? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

Registreringsbegäran är en begäran om POST.

Vi rekommenderar att du hämtar enhets-ID från sessionen i stället för att skicka som parameter. Detta rensar serverloggarna, webbläsarcachen och så vidare. Det är för närvarande inte något säkerhetsproblem. Observera att semantisk GET används när ingen lägesändring görs på servern och POST används när en lägesändring görs.

### 3. Finns det något sätt att neka en enhetsregistreringsbegäran? {#is-there-a-way-to-decline-a-device-registration-request}

Du kan inte avböja registreringsbegäran. Registreringsbegäranden ska i stället upphöra att gälla efter en tidsgräns som har konfigurerats i [Adobe Experience Manager Web Console](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl). Som standard är det här värdet inställt på en dag och lagras i en minnescache.

## Enhetsövervakning och hälsorapporter {#device-monitoring-and-health-reports}

### 1. Hur felsöker jag om min AEM Screens-spelare visas på en tom skärm? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Kontrollera om det finns följande möjligheter att felsöka det tomma skärmproblemet:

* AEM kan inte skicka offlineinnehållet
* Kanalen har inget innehåll
* Ingen resurs är schemalagd att visas vid den aktuella tidpunkten

### 2. Vad gör jag om AEM Screens-spelaren inte kan registrera sig och läget visas som Fel? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Du måste aktivera filtret Tillåt tomt för Apache Sling Referrer-filtret. Detta krävs för att kontrollprotokollet mellan AEM Screens Player och AEM Screens-servern ska fungera optimalt.

1. Navigera till **Adobe Experience Manager Web Console Configuration**
1. Markera alternativet **allow.empty**.
1. Klicka på **Spara**.

### 3. Hur felsöker jag om enheten visar fel när en AEM Screens-spelare registreras och om konsolloggarna visar ett ENAME_NOT_FOUND-fel? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Detta kan inträffa om spelaren inte kan hitta DNS-servern för AEM Screens. Du kan försöka använda IP-adressen för att ansluta. Använd följande för att hämta serverns IP-adress: *arp &lt;server_dns_name>*.

### 4. Rekommenderar AMS implementering av en Android-övervakare på alla enheter? Ingår Watchdog-pluginen (Cordova) som en del av APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

En Android-övervakare som använder rena Android-API:er på flera plattformar är redan en del av paketet. Ingen ytterligare programvara behövs, men beroende på vilken enhet du använder kan du behöva avregistrera appen för att få systembehörighet för en full strömcykel (PowerManager API). Om det inte signeras om med hjälp av tillverkarens nycklar kommer programmet att avslutas och startas om, men inte strömcykeln.

Mer information om hur du implementerar Android Player finns i [**Implementera Android Player**](implementing-android-player.md).

### 5. Vilka verktyg för fjärrövervakning och fjärrvarning (programvara) från tredje part rekommenderar Adobe/AMS för övervakning av varje enhet?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Beroende på vad du vill ha ut av övervaknings- och aviseringsfunktionen får du ett meddelande från AEM Screens Notifications-tjänsten om en enhet inte har fästs på ett tag. Tredjepartsverktygen beror på operativsystemet, dess funktioner och kundens specifika behov.

Mer information om var du kan övervaka enhetsaktivitet finns i [**AEM Screens Notifications Service**](screens-notifications-service.md).

## AEM Screens Player {#aem-screens-player}

### 1. Hur installerar jag ChromeOS-spelaren som Chrome Browser-plugin? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS-spelaren kan installeras som Chrome Browser-plugin i utvecklarläge utan att den faktiska enheten för Chrome Player krävs. För installation, följ stegen nedan:

1. Klicka [här](https://download.macromedia.com/screens/) för att hämta den senaste Chrome Player.
1. Zippa upp och spara det på disken.
1. Öppna webbläsaren Chrome och välj **Tillägg** på menyn eller navigera direkt till ***chrome://extensions***.
1. Aktivera **utvecklarläget** i det övre högra hörnet.
1. Klicka på **Läs in opackad** från det övre vänstra hörnet och läs in den uppackade Chrome Player.
1. Kontrollera **AEM Screens Chrome Player**-plugin om det finns i listan över tillägg.
1. Öppna en ny flik och klicka på ikonen **Apps** i det övre vänstra hörnet eller navigera direkt till ***chrome://apps***.
1. Klicka på **AEM Screens** Plugin för att starta Chrome Player. Som standard startas spelaren i helskärmsläge. Tryck på **esc** för att avsluta helskärmsläget.

### 2. Hur felsöker jag om skärmspelaren inte kan autentisera via en publiceringsinstans med en anpassad felhanterare? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

När AEM Screens-spelaren startas görs en begäran till ***/content/screens/svc.ping.json*** när spelaren får ett 404-fel. Spelaren initierar en autentiseringsbegäran att autentisera mot publiceringsinstansen. Om det finns en anpassad felhanterare i publiceringsinstansen måste du returnera 404-statuskoden för anonym användare på ***/content/screens/svc.ping.json***.

### 3. Hur du aktiverar enhetsskärmen i en Android-spelare? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Följ stegen nedan om du vill aktivera Var aktiv i en Android-spelare:

1. Navigera till Android-spelarens inställningar —> **Om**
1. Tryck 7 gånger på versionsnumret för att aktivera **Utvecklaralternativ** i **Inställningar**
1. Navigera till **Utvecklaralternativ**
1. Aktivera **Håll dig vaken**

### 4. Hur aktiverar jag fönsterläge för Windows Player?{#enable-player}

Det finns inget fönsterläge i Windows Player. Det är alltid helskärmsläge.

### 5. Hur felsöker man om en AEM Screens-spelare kontinuerligt skickar inloggningsbegäranden?{#requests-login}

Följ stegen nedan för att felsöka en AEM Screens-spelare som kontinuerligt skickar begäranden till `/content/screens/svc.json` och `/libs/granite/core/content/login.validate/j_security_check`:

1. När AEM Screens-spelaren startas begär den `/content/screens/svc.json`. När spelaren får en 404-statuskod i svaret initierar den en autentiseringsbegäran med `/libs/granite/core/content/login.validate/j_security_check` mot *publish*-instansen. Om det finns en anpassad felhanterare i *publish*-instansen måste du returnera 404-statuskoden för anonym användare på `/content/screens/svc.json` eller `/content/screens/svc.ping.json`.

1. Kontrollera om din dispatcherkonfiguration tillåter dessa förfrågningar i `/filters`.

   Mer information finns i [Konfigurera skärmfilter](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters).

1. Kontrollera om din dispatcher skriver om regler för skärmsökvägar till en annan sökväg.

1. Kontrollera om du har `/etc/map`-regler för *författaren* eller *publish*-instansen och skärmsökvägarna matchar `sling:match` och omdirigeras internt till en annan sökväg. Genom att matcha den exakta URL:en i `/system/console/jcrresolver` blir det lättare att identifiera om *publish*-instansen skriver om dessa URL:er till någon annan sökväg.

1. Kontrollera om konfigurationen av Apache Sling Resource Resolver Factory orsakar interna omskrivningar.

## Allmänna felsökningstips {#general-troubleshooting-tips}

### 1. Hur inaktiverar jag Livefyre för att undvika fel i A/P-skärmar? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Så här inaktiverar du Livefyre för att undvika loggfel:

1. ***Inaktivera Livefyre-paketet:***

   * Navigera till `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Sök efter AEM Livefyre-paketet: `com.adobe.cq.social.cq-social-livefyre`
   * Klicka på **Stopp**

1. ***Inaktivera Livefyre poller:***

   * I CRXDE Lite går du till `/etc/importers/polling/livefyre-poller/jcr:content`
   * Lägg till en ny egenskap *aktiverad* typ *Boolean*
   * Ange **den aktiverade egenskapen** till **false**

### 2. Hur lägger jag till information om Oak Index? {#add-oak-index-info}

AEM Screens skapar indexdefinitioner för frågor som används av produkten.
Om det finns *WARNs* i `error.log` skapar du ett anpassat index för frågan. Mer information finns i [Konfigurera index](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes).

Du kan även referera till en ytterligare resurs på [Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


