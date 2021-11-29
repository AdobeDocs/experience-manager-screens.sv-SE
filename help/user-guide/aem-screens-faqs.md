---
title: Vanliga frågor om AEM Screens
seo-title: AEM Screens FAQs
description: Följ den här sidan för att få svar på vanliga frågor om ett AEM Screens-projekt.
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: fc120c02e01d0159ca0294a9b5326b53a0fa48f0
workflow-type: tm+mt
source-wordcount: '2120'
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
* Navigera till `http://localhost:24502`. Kontrollera om allt innehåll har laddats ned korrekt.
* Kontrollera de resurser som de lämpliga återgivningarna skapas för och att rätt återgivning spelas upp.
* Kontrollera om det finns schemalagt innehåll och om tiderna är korrekta. Kontrollera om tiden som är inställd i spelaren är korrekt.
* Inspect spelarkonsolen loggar och söker efter eventuella fel. Högerklicka och inspektera för att se konsolloggarna. Om du använder Windows Player trycker du på `CTRL + ALT +I` för att öppna dev-konsolen för att visa loggarna.

### 2. Hur löser jag problem med gråskärm i AEM Screens genom att skapa en standardkanal eller ett schema?

För att undvika tomma eller grå skärmar i fältet skapar du en global standardkanal eller ett standardschema som tilldelas alla skärmar med lägst prioritet 1. Om något skulle gå fel med innehållsuppdateringar (på grund av nätverk, spelare, server eller replikering), eftersom spelarna redan har det här innehållet cachelagrat på disken, som ska spelas upp korrekt och undvika de grå skärmarna.

Allt annat innehåll, som kanaler eller scheman, har högre prioritet än 1, så det andra innehållet har högre prioritet och globalt kanalinnehåll eller schemaläggningsinnehåll (med prioritet 1) spelas endast upp som ett reservalternativ.

## Kanalhantering {#channel-management}

### 1. Vad är skillnaden mellan en online- och en offlinekanal? {#what-is-the-difference-between-an-online-and-an-offline-channel}

An ***Onlinekanal***, visar det uppdaterade innehållet i realtidsmiljön medan en ***Offlinekanal***, visar det cachelagrade innehållet.

### 2. Hur gör jag en kanal online? {#how-do-i-make-a-channel-online}

Markera kanalen och navigera till kanalegenskaper i åtgärdsfältet. Kontrollera **Utvecklarläge (tvinga kanalen att vara online)** under **Kanal** för att göra kanalen online.

### 3. Hur används fältet Kanalroll? {#what-is-the-use-of-the-channel-role-field}

Kanalrollen är förkortningen av den faktiska kanal som körs så att författaren kan fokusera direkt på den generiska upplevelsen. Du kan tänka dig det som en typ av tagg som unikt identifierar kanalen i sitt sammanhang (visning eller schema).

### 4. Hur sker faktisk kanalupplösning? {#how-does-actual-channel-resolution-happen}

För *statiska referenser*, följer upplösningen bara den angivna sökvägen.

För *dynamiska referenser*, inträffar upplösningen när kanalen har tilldelats visningen (inte schemat). Visningsbanan blir kontext för kanalen och upplösningen sker enligt följande (högsta till lägsta prioritet):

1. Visningen har en underordnad nod som matchar det refererade kanalnamnet
1. Visningen har en nod på samma nivå som det refererade kanalnamnet
1. Visningens överordnade plats har en underordnad nod som matchar det refererade kanalnamnet
1. Den överordnade platsen för visningen har en underordnad nod som matchar det refererade kanalnamnet

Och så vidare, tills du når platsmappen och stoppar den där just nu (så att du inte kan referera till en kanal som till exempel finns i kanalmappen, är det bara kanaler i platsernas underträd).

### 5. Hur konfigurerar man en anpassad klientlib offline-konfiguration i AEM Screens Channel?

När du använder en anpassad klientkod `clientlib` i en AEM Screens-kanal måste du följa de här stegen för att säkerställa att `clientlib` -filerna har lästs in i kanalen (`manifest.json`) och innehåller sökvägen till `clientlib`.

Följ stegen nedan i kanalredigeraren:

1. Välj en kanal och klicka på **Redigera** i åtgärdsfältet för att öppna kanalredigeraren.
1. Markera komponenten där du vill lägga till den anpassade `clientlib`.
1. Klicka på knappen Konfigurera (skiftnyckelsikonen).
1. Navigera till **Offlinekonfiguration** och lägga till sökvägen till din anpassade klientlib i **Bibliotek på klientsidan**.

## Enhetsregistrering {#device-registration}

### 1. Om jag upptäcker slutpunkter som begäran om registrering och registrering av enheter kan jag skripta ett stort antal enheter och registrera dessa enheter. Är det möjligt att skydda dessa förfrågningar förutom att låsa detta till en gren-Wi-Fi? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Registrering är för närvarande bara möjligt på författarinstansen. Registreringstjänsten är inte autentiserad, men skapar bara en väntande enhet i AEM och registrerar inte enheten eller tilldelar någon skärm.

Om du vill registrera en enhet (vilket innebär att du skapar en användare för enheten i AEM) måste du fortfarande autentisera till AEM och för närvarande följa registreringsguiden manuellt för att slutföra registreringen. Teoretiskt sett kan en oärlig användare skapa flera väntande enheter, men kan inte registrera några utan en AEM inloggning.

### 2. Finns det något sätt att omvandla HTTP GET-begäranden till HTTP-POST med någon form av autentisering? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

Registreringsbegäran är en begäran om POST.

Vi rekommenderar att du hämtar enhets-ID från sessionen i stället för att skicka som parameter. Detta rensar serverloggarna, webbläsarcachen och så vidare. Det är för närvarande inte något säkerhetsproblem. Observera att semantisk GET används när ingen lägesändring görs på servern och POST används när en lägesändring görs.

### 3. Finns det något sätt att neka en enhetsregistreringsbegäran? {#is-there-a-way-to-decline-a-device-registration-request}

Du kan inte avböja registreringsbegäran. I stället bör registreringsförfrågningar upphöra att gälla efter en timeout som har konfigurerats i `Adobe Experience Manager Web Console`. Som standard är det här värdet inställt på en dag och lagras i en minnescache.

## Enhetsövervakning och hälsorapporter {#device-monitoring-and-health-reports}

### 1. Hur felsöker jag om min AEM Screens-spelare visas på en tom skärm? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Kontrollera om det finns följande möjligheter att felsöka det tomma skärmproblemet:

* AEM kan inte skicka offlineinnehållet
* Kanalen har inget innehåll
* Ingen resurs är schemalagd att visas vid den aktuella tidpunkten

### 2. Vad gör jag om AEM Screens-spelaren inte kan registrera sig och läget visas som Fel? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Du måste aktivera filtret Tillåt tomt för Apache Sling Referrer-filtret. Detta krävs för att kontrollprotokollet mellan AEM Screens Player och AEM Screens-servern ska fungera optimalt.

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console**
1. Kontrollera **allow.empty** alternativ.
1. Klicka **Spara**.

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

1. Klicka [här](https://download.macromedia.com/screens/) för att ladda ned den senaste Chrome Player.
1. Zippa upp och spara det på disken.
1. Öppna Chrome-webbläsaren och välj **Tillägg** från menyn eller direkt navigera till ***chrome://extensions***.
1. Aktivera **Utvecklarläge** från det övre högra hörnet.
1. Klicka på **Läs in opackad** från det övre vänstra hörnet och ladda uppzippad Chrome Player.
1. Kontrollera **AEM Screens Chrome Player** plugin-program, om det finns i listan över tillägg.
1. Öppna en ny flik och klicka på **Appar** ikonen i det övre vänstra hörnet eller direkt navigera till ***chrome://apps***.
1. Klicka på **AEM Screens** Plugin-program för att starta Chrome Player. Som standard startas spelaren i helskärmsläge. Tryck **esc** för att avsluta helskärmsläget.

### 2. Hur felsöker jag om skärmspelaren inte kan autentisera via en publiceringsinstans med en anpassad felhanterare? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

När AEM Screens-spelaren startas begär den att ***/content/screens/svc.ping.json*** när spelaren får ett 404-fel. Spelaren initierar en autentiseringsbegäran att autentisera mot publiceringsinstansen. Om det finns en anpassad felhanterare i en publiceringsinstans måste du returnera 404-statuskoden för anonym användare på ***/content/screens/svc.ping.json***.

### 3. Hur du aktiverar enhetsskärmen i en Android-spelare? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Följ stegen nedan om du vill aktivera Var aktiv i en Android-spelare:

1. Navigera till Android-spelarens inställningar —> **Om**
1. Tryck 7 gånger på build number för att aktivera **Utvecklaralternativ** in **Inställningar**
1. Navigera till **Utvecklaralternativ**
1. Aktivera **Håll dig vaken**

### 4. Hur aktiverar jag fönsterläge för Windows Player?{#enable-player}

Det finns inget fönsterläge i Windows Player. Det är alltid helskärmsläge.

### 5. Hur felsöker man om en AEM Screens-spelare kontinuerligt skickar inloggningsförfrågningar?{#requests-login}

Följ stegen nedan för att felsöka en AEM Screens-spelare som kontinuerligt skickar begäranden till `/content/screens/svc.json` och `/libs/granite/core/content/login.validate/j_security_check`:

1. När AEM Screens Player startas begär den att `/content/screens/svc.json`. När spelaren får en 404-statuskod i svaret initierar den en autentiseringsbegäran med `/libs/granite/core/content/login.validate/j_security_check` mot *publicera* -instans. Om det finns en anpassad felhanterare i *publicera* ska du se till att returnera 404-statuskoden för anonym användare på `/content/screens/svc.json` eller `/content/screens/svc.ping.json`.

1. Kontrollera om din dispatcher-konfiguration tillåter dessa förfrågningar i `/filters`.

   Se [Konfigurera skärmfilter](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) för mer information.

1. Kontrollera om din dispatcher skriver om regler för skärmsökvägar till en annan sökväg.

1. Kontrollera om du har `/etc/map` regler för *författare* eller *publicera* instans- och skärmbanor matchas mot `sling:match` och omdirigeras internt till en annan bana. Lösa den exakta URL:en i `/system/console/jcrresolver` hjälper till att identifiera om *publicera* den här instansen skriver om dessa URL:er till någon annan sökväg.

1. Kontrollera om konfigurationen av Apache Sling Resource Resolver Factory orsakar interna omskrivningar.

### 6. Hur får jag information om skärmen och enheten från spelarens API?

Du kan hämta information om skärmen och enheten via:

* **ett internt JS API**
* **ett ContextHub-arkiv**: Tre ContextHub-butiker har definierats i `/libs/screens/clientlibs/contexthub` för att visa kanaler, enheter och visningsinformation.

   Följ stegen nedan för att använda dessa ContentHub-butiksvärden:

   * Redigera kanalegenskaperna och ange ContextHub-sökvägen på fliken för anpassning till värdet (som nämns ovan)
   * I kanal-JS kan du använda:

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## Allmänna felsökningstips {#general-troubleshooting-tips}

### 1. Hur inaktiverar jag Livefyre för att undvika fel i A/P-skärmar? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Så här inaktiverar du Livefyre för att undvika loggfel:

1. ***Inaktivera Livefyre-paketet:***

   * Navigera till `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Sök efter AEM Livefyre-paketet: `com.adobe.cq.social.cq-social-livefyre`
   * Klicka **Stoppa**

1. ***Inaktivera Livefyre poller:***

   * I CRXDE Lite går du till `/etc/importers/polling/livefyre-poller/jcr:content`
   * Lägg till en ny egenskap *aktiverad* type *Boolean*
   * Ange **enabled, egenskap** till **false**

### 2. Hur lägger jag till information om Oak Index? {#add-oak-index-info}

AEM Screens skapar indexdefinitioner för de frågor som används av produkten.
Om det finns några *Frågespårningsvarningar* i `error.log`skapar du ett anpassat index för din fråga. Se [Konfigurera index](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) för mer information.

Du kan även referera till en ytterligare resurs på [Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. Vad krävs för att konfigurera v3-manifestationer? {#configure-v3}

Om du vill aktivera v3-manifestet måste du:

* Uppdatera Dispatcher.
Se [Konfigurera Dispatcher för manifestversion v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) för mer information.

* Uppdatera anpassad komponent.
Se [Mall för anpassade hanterare](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers) för mer information.

* Inaktivera ContentSync i `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Aktivera SmartSync i `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* Redigera `channel/experience fragment/page components`.

* Navigera till **Offlinekonfiguration** -fliken.

* Retur `clientlibs `och mappar för statiska filer som måste läggas till i manifestet.

### 4. Vad ska du göra om, efter paketet screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 och skärmens kärnpaket är installerade men inte aktiva?

Du måste installera minst AEM 6.5 Feature Pack 8 för att AMS-anslutningen ska fungera. Se [Tillgänglighet](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105.html?lang=en#availability) för att få den lägsta versionen av skärmfunktionspaketet.