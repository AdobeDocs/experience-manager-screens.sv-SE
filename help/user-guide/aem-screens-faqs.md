---
title: Vanliga frågor om AEM Screens
description: Läs svar på vanliga frågor om ett AEM Screens-projekt.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 0%

---

# Vanliga frågor om AEM Screens {#aem-screens-faqs}

I det här avsnittet finns svar på vanliga frågor och svar om ett AEM Screens-projekt.

## Problem med tom skärm {#blank-screen}

>[!NOTE]
>De obligatoriska kontroller som anges ovan gör att den primära supporten eller kundsupporten bör försöka innan ett problem uppstår.

### 1. Vilka är de första felsökningsstegen för att hitta kunder som ser en svart skärm eller som inte spelar upp innehåll? {#troubleshooting-blank-screen}

* Kontrollera om kanalförhandsgranskningen fungerar.
* Kontrollera om förhandsvisningen fungerar
* Prova att registrera spelaren som ett webbläsartillägg på datorn på samma skärm och kontrollera om den fungerar.
* Navigera till `http://localhost:24502` när spelaren körs på datorn. Kontrollera om allt innehåll har laddats ned korrekt.
* Kontrollera resurserna så att du kan kontrollera att rätt återgivningar skapas och att rätt återgivning spelas upp.
* Kontrollera om det finns schemalagt innehåll och om tiderna är korrekta. Kontrollera om tiden som är inställd i spelaren är korrekt.
* Inspect spelarkonsolen loggar och söker efter eventuella fel. Högerklicka och inspektera för att se konsolloggarna. Om du använder Windows Player kan du visa loggarna genom att trycka på `CTRL + ALT +I`.

### 2. Hur löser jag problem med gråskärm i AEM Screens genom att skapa en standardkanal eller ett schema?

För att undvika tomma eller grå skärmar i fältet skapar du en global standardkanal eller ett standardschema som tilldelas alla skärmar med lägst prioritet 1. Om något skulle gå fel med innehållsuppdateringar eftersom spelarna redan har det här innehållet cachelagrat på skivan. Den ska spelas upp som den ska och de grå skärmarna ska undvikas.

Allt annat innehåll, t.ex. kanaler eller scheman, prioriteten är större än 1, så det andra innehållet får prioritet och globalt kanalinnehåll eller schemaläggningsinnehåll (med prioritet 1) spelas endast upp som ett alternativ för återfall.

## Kanalhantering {#channel-management}

### 1. Vad är skillnaden mellan en online- och en offlinekanal? {#what-is-the-difference-between-an-online-and-an-offline-channel}

En ***onlinekanal*** visar det uppdaterade innehållet i realtidsmiljön, medan en ***offlinekanal*** visar det cachelagrade innehållet.

### 2. Hur skapar jag en kanal online? {#how-do-i-make-a-channel-online}

Klicka på kanalen och navigera till kanalegenskaper från åtgärdsfältet. Markera **Utvecklarläge (tvinga kanalen att vara online)** under fliken **Kanal** för att göra kanalen online.

### 3. Hur används fältet Kanalroll? {#what-is-the-use-of-the-channel-role-field}

Kanalrollen är förkortningen av den faktiska kanal som körs så att författaren kan fokusera direkt på den generiska upplevelsen. Du kan tänka dig det som en typ av tagg som unikt identifierar kanalen i sitt sammanhang (visning eller schema).

### 4. Hur sker faktisk kanalupplösning? {#how-does-actual-channel-resolution-happen}

För *statiska referenser* följer upplösningen den angivna sökvägen.

För *dynamiska referenser* inträffar upplösningen när kanalen har tilldelats till visningen (inte schemat). Visningsbanan blir kontext för kanalen och upplösningen sker enligt följande (högsta till lägsta prioritet):

1. Visningen har en underordnad nod som matchar det refererade kanalnamnet
1. Visningen har en nod på samma nivå som det refererade kanalnamnet
1. Visningens överordnade plats har en underordnad nod som matchar det refererade kanalnamnet
1. Den överordnade platsen för visningen har en underordnad nod som matchar det refererade kanalnamnet

Och så vidare, tills du når platsmappen. Stoppa där för tillfället (så du kan inte referera till en kanal som skulle finnas i kanalmappen, till exempel, bara kanaler i platsunderträdet).

### 5. Hur konfigurerar jag en anpassad klientlib offline i AEM Screens Channel?

När du använder en anpassad klientkod `clientlib` i en AEM Screens-kanal krävs följande steg. Stegen kontrollerar att `clientlib`-filerna har lästs in i kanalen (`manifest.json`) och innehåller sökvägen till `clientlib`.

Följ stegen nedan i kanalredigeraren:

1. Klicka på en kanal och sedan på **Redigera** i åtgärdsfältet.
1. Klicka på den komponent där du vill lägga till den anpassade `clientlib`.
1. Klicka på knappen Konfigurera (skiftnyckelsikonen).
1. Navigera till fliken **Offlinekonfiguration** och lägg till sökvägen till ditt anpassade klientbibliotek i **Bibliotek på klientsidan**.

## Enhetsregistrering {#device-registration}

### 1. Om jag upptäcker slutpunkter som begäran om registrering och registrering av enheter kan jag skripta många enheter och registrera dessa enheter. Är det möjligt att skydda dessa förfrågningar förutom att låsa dem till en gren-Wi-Fi? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Registrering är för närvarande bara möjligt på författarinstansen. Registreringstjänsten är inte autentiserad, men skapar bara en väntande enhet i AEM och registrerar inte enheten eller tilldelar någon skärm.

Om du vill registrera en enhet (skapa en användare för enheten i AEM) autentiserar du AEM och följer registreringsguiden manuellt för att slutföra registreringen. Teoretiskt sett kan en oärlig användare skapa flera väntande enheter, men kan inte registrera några om de inte har någon AEM inloggning.

### 2. Finns det något sätt att omvandla HTTP GET-begäranden till HTTP-POST med någon form av autentisering? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

Registreringsbegäran är en begäran om POST.

Vi rekommenderar att du hämtar enhets-ID från sessionen i stället för att skicka det som en parameter. Om du gör det rensas serverloggarna, webbläsarcachen och så vidare. Det är inte ett säkerhetsproblem. Semantiskt. GET används när ingen lägesändring görs på servern och POST används när en lägesändring görs.

### 3. Finns det något sätt att neka en enhetsregistreringsbegäran? {#is-there-a-way-to-decline-a-device-registration-request}

Du kan inte avböja registreringsbegäran. Registreringsbegäranden ska i stället upphöra att gälla efter en tidsgräns som har konfigurerats i `Adobe Experience Manager Web Console`. Som standard är det här värdet inställt på en dag och lagras i en minnescache.

## Enhetsövervakning och hälsorapporter {#device-monitoring-and-health-reports}

### 1. Hur felsöker jag om min AEM Screens Player visar en tom skärm?

Kontrollera om det finns följande möjligheter att felsöka det tomma skärmproblemet:

* AEM kan inte skicka offlineinnehållet
* Kanalen har inget innehåll
* Ingen resurs är schemalagd att visas vid den aktuella tidpunkten

### 2. Vad gör jag om AEM Screens Player inte kan registrera sig och dess status visas som Fel?

Aktivera filtret Apache Sling Referrer Tillåt tomt. Krävs för att kontrollprotokollet mellan AEM Screens Player och AEM Screens-servern ska fungera optimalt.

1. Navigera till **Adobe Experience Manager Web Console Configuration**
1. Markera alternativet **allow.empty**.
1. Klicka på **Spara**.

### 3. Hur felsöker man om enheten uppvisar fel när en AEM Screens Player registreras och konsolloggarna visar ett ENAME_NOT_FOUND-fel?

Detta kan inträffa om spelaren inte kan hitta DNS-servern för AEM Screens. Du kan försöka använda IP-adressen för att ansluta. Använd *arp &lt;server_dns_name>* om du vill hämta serverns IP-adress.

### 4. Rekommenderar AMS att man implementerar en Android™ Watchdog på alla enheter? Ingår Watchdog-pluginen (Cordova) som en del av APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

En Android™-övervakning som kan användas på flera plattformar och som använder rena Android™-API:er är redan en del av paketet. Ingen ytterligare programvara behövs. Beroende på vilken enhet du använder kan du dock tilldela om appen för att få systembehörighet för en fullständig strömcykel (`Powermanager` api), om det behövs. Om det inte signeras om med hjälp av tillverkarens tangenter avslutas det och startar om programmet, men det startar inte om cykeln.

Mer information om hur du implementerar Android™ Player finns i [**Implementera Android™ Player**](implementing-android-player.md).

### 5. Vilka verktyg för fjärrövervakning och fjärrvarning (programvara) från tredje part rekommenderar Adobe/AMS för övervakning av varje enhet? {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Beroende på vad du vill ha ut av övervaknings- och aviseringsfunktionen får du ett meddelande från AEM Screens Notifications-tjänsten om en enhet inte har fästs på ett tag. Tredjepartsverktygen är beroende av operativsystemet, dess funktioner och kundens specifika behov.

Mer information om var du kan övervaka enhetsaktivitet finns i [**AEM Skärmmeddelandetjänst**](screens-notifications-service.md).

## AEM Screens Player

### 1. Hur installerar jag ChromeOS-spelaren som Chrome webbläsarplugin? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS-spelaren kan installeras som ett Chrome-plugin-program för webbläsare i utvecklarläge utan att du behöver en riktig Chrome Player-enhet. För installation, följ stegen nedan:

1. Klicka [här](https://download.macromedia.com/screens/) om du vill hämta den senaste Chrome Player.
1. Zippa upp och spara det på disken.
1. Öppna webbläsaren Chrome och klicka på **Tillägg** på menyn eller navigera direkt till ***chrome://extensions***.
1. Aktivera **utvecklarläget** i det övre högra hörnet.
1. Klicka på **Läs in opackad** i det övre vänstra hörnet och läs in den uppackade Chrome Player.
1. Kontrollera **AEM Screens Chrome Player**-plugin-programmet om det finns i listan över tillägg.
1. Öppna en ny flik och klicka på ikonen **Apps** i det övre vänstra hörnet eller navigera direkt till ***chrome://apps***.
1. Klicka på plugin-programmet **AEM Screens**. Som standard startas spelaren i helskärmsläge. Tryck på **Esc** för att avsluta helskärmsläget.

### 2. Hur felsöker jag om Screens Player inte kan autentisera via en publiceringsinstans med en anpassad felhanterare?

När AEM Screens Player startas skickas en begäran till ***/content/screens/svc.ping.json*** när ett 404-fel inträffar. Spelaren initierar en autentiseringsbegäran att autentisera mot publiceringsinstansen. Om det finns en anpassad felhanterare i publiceringsinstansen måste du returnera 404-statuskoden för en anonym användare på ***/content/screens/svc.ping.json***.

### 3. Hur du aktiverar enhetsskärmen i en Android™-spelare? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Följ stegen nedan för att aktivera Fortsätt vara aktiv i valfri Android™-spelare:

1. Navigera till Android™-spelarinställningar > **Om**.
1. Tryck sju gånger på versionsnumret så att du kan aktivera **Utvecklaralternativ** i **Inställningar**.
1. Navigera till **Utvecklaralternativ**.
1. Aktivera **Håll dig vaken**.

### 4. Hur aktiverar jag fönsterläge för Windows Player?{#enable-player}

Det finns inget fönsterläge i Windows Player. Det är alltid i helskärmsläge.

### 5. Hur felsöker jag om en AEM Screens Player skickar inloggningsförfrågningar?

Följ stegen nedan för att felsöka en AEM Screens Player som kontinuerligt skickar begäranden till `/content/screens/svc.json` och `/libs/granite/core/content/login.validate/j_security_check`:

1. När AEM Screens Player startas begär den att `/content/screens/svc.json` ska köras. När spelaren får en 404-statuskod i svaret initierar den en autentiseringsbegäran genom att använda `/libs/granite/core/content/login.validate/j_security_check` mot *publish*-instansen. Om det finns en anpassad felhanterare i *publish* -instansen måste du returnera 404-statuskoden för anonym användare på `/content/screens/svc.json` eller `/content/screens/svc.ping.json`.

1. Kontrollera om din Dispatcher-konfiguration tillåter dessa förfrågningar i `/filters`.

   Mer information finns i [Konfigurera Screens-filter](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters).

1. Kontrollera om Dispatcher skrivregler skriver om några skärmsökvägar till en annan sökväg.

1. Kontrollera om du har `/etc/map` regler för instansen *author* eller *publish* och skärmsökvägarna matchas mot `sling:match` och omdirigeras internt till en annan sökväg. Att matcha den exakta URL:en i `/system/console/jcrresolver` hjälper till att identifiera om *publish*-instansen skriver om dessa URL:er till någon annan sökväg.

1. Kontrollera om konfigurationen av Apache Sling Resource Resolver Factory orsakar interna omskrivningar.

### 6. Hur får jag information om skärmen och enheten från spelarens API?

Du kan få information om skärmen och enheten genom att:

* **ett internt JS-API**
* **ett ContextHub-arkiv**: Tre ContextHub-butiker definieras i `/libs/screens/clientlibs/contexthub` för att visa kanaler, enheter och visningsinformation.

  Följ stegen nedan för att använda dessa ContentHub-butiksvärden:

   * Redigera kanalegenskaperna och ange ContextHub-sökvägen på fliken för anpassning till värdet (som nämns ovan)
   * I kanal-JS kan du använda:

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## Allmänna felsökningstips {#general-troubleshooting-tips}

### 1. Hur inaktiverar jag Livefyre för att undvika ett fel i A/P Screens?

Inaktivera Livefyre för att undvika loggfel genom att göra följande.

1. ***Inaktivera Livefyre-paketet:***

   * Navigera till `https://<host>:<port>/system/console/bundles`.
   * Sök efter AEM Livefyre-paketet: `com.adobe.cq.social.cq-social-livefyre`.
   * Klicka på **Stopp**.

1. ***Inaktivera Livefyre poller:***

   * Gå till `/etc/importers/polling/livefyre-poller/jcr:content` i CRXDE Lite.
   * Lägg till egenskapen *enabled* type *Boolean*.
   * Ange **den aktiverade egenskapen** som **false**.

### 2. Hur lägger jag till Oak Index-information? {#add-oak-index-info}

AEM Screens skapar indexdefinitioner för de frågor som används av produkten.
Om det finns några *WARN:er för genomgång av frågor* i `error.log` skapar du ett anpassat index för din fråga. Mer information finns i [Konfigurera index](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes).

Du kan även se ytterligare en resurs på [Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. Vad krävs för att konfigurera v3-manifestet? {#configure-v3}

Så här aktiverar du v3-manifestet:

* Uppdatera Dispatcher.
Mer information finns i [Konfigurera Dispatcher för manifestversion v3](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3).

* Uppdatera anpassad komponent.
Mer information finns i [Mall för anpassade hanterare](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers).

* Inaktivera ContentSync i `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Aktivera SmartSync i `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* Redigera `channel/experience fragment/page components`.

* Gå till fliken **Offlinekonfiguration**.

* Ange `clientlibs ` och mappar för statiska filer som måste läggas till i manifestet.

### 4. Vad ska du göra om, efter paketet screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 och skärmens kärnpaket är installerade men inte aktiva?

Installera minst AEM 6.5 Feature Pack 8 för att AMS-anslutningen ska fungera. Se [Tillgänglighet](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability) så att du kan hämta den lägsta versionen av AEM Screens Feature Pack.

### 5. Hur konfigurerar man CQ Link Externalizer-tjänsten i Screens?

Tjänsten används för att definiera det offentliga värdnamnet för författaren och publiceringsinstanserna, och värdena används sedan för att uppdatera enhetsserverns URL:er och även för ContextHub-mål.

CQ Link Externalizer-tjänsten i Screens kan konfigureras på följande sätt:

1. Navigera till `http://localhost:4502/system/console/configMgr`
1. Day CQ Link Externalizer
1. Ändra värdnamnet för `author/publish`-posterna efter behov