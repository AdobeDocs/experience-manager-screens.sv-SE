---
title: Lagerstyrd kanal
seo-title: Lagerstyrd kanal
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Lagerstyrd kanal{#inventory-driven-channel}

## Komma igång med lagerstyrda kanaler {#getting-started-with-inventory-driven-channels}

I det här avsnittet beskrivs ett exempel på hur du använder Google Sheets för att skapa och hantera en datadriven resursändring.

### Förhandsvillkor {#preconditions}

Innan du börjar med det här användningsexemplet måste du förstå hur du gör:

* **[Skapa och hantera kanaler](managing-channels.md)**
* **[Skapa och hantera platser](managing-locations.md)**
* **[Skapa och hantera scheman](managing-schedules.md)**
* **[Enhetsregistrering](device-registration.md)**

### Primära aktörer {#primary-actors}

Innehållsförfattare

### Terminolgies {#terminolgies}

Följ villkoren nedan som spelar en viktig roll när det gäller att förstå och konfigurera projektet i de olika användningsfallen:

**Aktivitet** refererar till kategorin.

**Huvudprojekt för** områdesprojekt

**Målgruppsplats** för data

**Varumärkesreferenser**

**Segmentsegment** refererar till en behållare med resurser som du försöker rikta in dig på.

### Grundläggande flöde: Konfigurera projektet {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**Krav:**
>
>Innan du börjar fördjupa dig i detaljer om hur du konfigurerar och använder datadriven resursändring i ditt projekt måste du skapa ett AEM-skärmsprojekt med en sekvenskanal. För demoändamål skapas projektet **DataDrivenAsset** och sekvenskanalerna **DataDrivenRestaurant**, **DataDrivenTextOverlay**, **DataDrivenWeather** och **DataDrivenRetail** läggs till i projektet, vilket visas i bilden nedan.
>
>Att skapa fyra olika kanaler är bara till för demonstrationssyften och att visa upp fyra olika användningsfall i olika kanaler. Om du bara vill följa ett användningsexempel kan du skapa en enda sekvenskanal.

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

Följ avsnitten nedan för att skapa ett exempelprojekt om hur du skapar och hanterar en datadriven resursändring med Google Sheets i ett AEM Screens-projekt:

## Steg 1: Konfigurera databas {#step-setting-up-database}

>[!CAUTION]
>
>Google Sheets används i följande exempeldatabassystem från vilket värdena hämtas och är endast avsett för utbildningsändamål. Adobe stöder inte Google Sheets för produktionsmiljöer.
>
>Mer information finns i [Hämta API-nyckel](https://developers.google.com/maps/documentation/javascript/get-api-key) i Google-dokumentationen.

1. Logga in på Google Docs.

   >[!NOTE]
   >
   >Du måste ha ett konto i Google Drive innan du kan skapa ett nytt Google Sheet.

1. Starta ett nytt tomt kalkylblad. Lägg till innehåll i Google-bladet och spara det. I demonstrationssyfte får Google Sheet namnet **ContextHubDemo**.
1. Klicka på **Dela** i det övre högra hörnet av Google Sheet för att öppna dialogrutan **Dela med andra** . Klicka på alternativet **Avancerat** och ändra inställningarna till **På - Alla med länken**, vilket visas i bilden nedan.

   I det här steget kan du komma åt värden i Google Sheet.

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. När du klickar på **Spara** från föregående steg visas länken för Google Sheet. Spara klickningen för framtida referenser och klicka på **Klar**.

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>Google Sheets används i följande exempel i utbildningssyfte. Adobe stöder inte Google Sheets för produktionsmiljöer.

## Steg 2: Aktivera Google Sheets REST API:er {#step-enabling-the-google-sheets-rest-apis}

När du har konfigurerat ditt Google Sheet måste du aktivera Google Sheet REST API för att komma åt värdena.

Mer information om hur du aktiverar REST API:er för Google Sheets finns i dokumentationen för Google API:er.

1. Navigera till [Google API Console](https://console.developers.google.com/apis/credentials). Klicka på **SKAPA** för att skapa ett nytt projekt.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. Ange **projektnamnet** som **AssetChange** och klicka på **CREATE**.
1. När du har skapat projektet måste du konfigurera API-nyckeln. Klicka på **Skapa autentiseringsuppgifter** och välj **API-nyckel **för att generera API-nyckel för projektet. Spara API-nyckeln för framtida referenser.

   >[!NOTE]
   >
   >Det här demoprojektet använder den kostnadsfria Google API-nyckeln. Det kan finnas mer information om priser och begränsningar på Googles webbplats **Get API Key** .

### Verifiera inställningarna för Google Sheets {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;your sheet id>/values/Sheet1?key=&lt;your API key>

Exempel:

Om länken** Google Sheets** är *som följer:*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`och sedan

**Blad-ID** : `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**API-nyckeln** är: `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Lägg till båda värdena i syntaxen ovan:

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Nu bör du kunna visa data i bladet.

## Steg 2: Konfigurera AEM för hämtning av Google Sheets-innehållet {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

I följande avsnitt beskrivs hur du konfigurerar Adobe Experience Manager (AEM) att hämta innehåll från Google Sheets.

1. Navigera till din AEM-instans och klicka på verktygsikonen i det vänstra sidofältet. Klicka på **Webbplatser** —> **ContextHub**, som bilden nedan visar.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Skapa en ny konfiguration för ContextHub Store**

   1. Navigera till **global** > **default** > **ContextHub Configuration**.

   1. Klicka** Skapa > Konfigurationsbehållare **och ange titeln som** ContextHubDemo**.

   1. **Navigera** till **ContextHubDemo** > **Konfiguration för ContentHub Store..** för att öppna **konfigurationsguiden**
   1. Ange **titeln** som **Google Sheets**, **Store Name** som **googlesheets** och **Store Type** **som¥contexthub.generic-jsonp**
   1. Click **Next**
   1. Ange din specifika json-konfiguration. Du kan till exempel använda följande json för demoändamål.
   1. Click **Save**.

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >I ovanstående exempelkod definierar **pollInterval** den frekvens med vilken värdena uppdateras (i ms).
   >
   >
   >Ersätt koden med ditt *&lt;Sheet ID>* och *&lt;API Key>*, som du hämtade från **steg 1: Konfigurera databas.**

   >[!CAUTION]
   Om du skapar dina Google Sheets-lagringskonfigurationer utanför den gamla mappen (till exempel i din egen projektmapp) kommer målanpassning inte att fungera som de ska.
   Om du vill konfigurera Google Sheets-lagringskonfigurationer utanför den globala äldre mappen måste du ange **Store Name** som **segmentering** och **Store Type** som **aem.segmentation**. Dessutom måste du hoppa över processen att definiera json enligt definitionen ovan.

1. **Skapa ett varumärke i aktiviteter**

   1. Navigera från din AEM-instans till **Personalisering** > **Verksamheter**

   1. Klicka** Skapa** > **Skapa varumärke**

   1. Välj **Varumärke** i guiden **Skapa sida** och klicka på **Nästa**

   1. Ange **Title** som **ContextHubDemo** och klicka på **Create**. Ditt varumärke har nu skapats enligt nedan.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
Känt fel:
Om du vill lägga till ett område tar du bort mallen från URL:en, t.ex.
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. Skapa ett område i ert varumärke**

   1. Klicka på **Skapa** > **Skapa område**

   1. Välj **Område** i guiden** Skapa sida** och klicka på Nästa

   1. Ange **titeln** som **GoogleSheets** och klicka på **Skapa**. Området skapas i din aktivitet.

1. **Skapa segment i målgrupper**

   1. Navigera från din AEM-instans till **Personalisering** > **Publiker** > **We.Retail**.
   1. Klicka på **Skapa** > **Skapa kontextnavsegment**. Dialogrutan Nytt ContextHub-segment öppnas.
   1. Ange **titeln** som **BladA1 1** och klicka på **Skapa**. Du kan också skapa ett annat segment med namnet **SheetA2 2**.

1. **Redigera segment**

   1. Markera segmentmallarna **A1 1** (skapade i steg 5) och klicka på **Redigera** i åtgärdsfältet.

   1. Dra och släpp **jämförelsen: Egenskap - Värdekomponent** till redigeraren.
   1. Klicka på skiftnyckelsikonen för att öppna dialogrutan **Jämför en egenskap med ett värde** .
   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**.

   1. Välj **Operator** som **Equal **i listrutan.

   1. Ange **värdet** som **1**.
   >[!NOTE]
   AEM validerar dina data från Google Sheet genom att visa ditt segment som grönt.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   Du kan också redigera egenskapsvärdena till **Blad A1 2**.

   1. Dra och släpp **jämförelsen: Egenskap - Värdekomponent** till redigeraren.
   1. Klicka på skiftnyckelsikonen för att öppna dialogrutan **Jämför en egenskap med ett värde** .
   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**.

   1. Välj **Operator** som **Equal **i listrutan.

   1. Ange **värdet** som **2**.
   >[!NOTE]
   Reglerna som används i de föregående stegen är bara ett exempel på hur du ställer in segment för implementering av följande användningsexempel.

## Steg 3: Konfigurera konfigurationer av kontextnav i AEM Screens Channel {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

Följ stegen nedan för att konfigurera ContextHub-konfigurationer och segmentsökvägar till AEM Screens-kanalen.

1. Navigera som en förutsättning till en av de AEM-skärmar-kanaler (**DataDrivenRetail**) som du har skapat.
1. Markera kanalen (**DataDrivenRetail**) och klicka på **Egenskaper** i åtgärdsfältet.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Välj fliken **Personalisering** för att konfigurera ContextHub-konfigurationer.

   1. Välj **ContextHub Path** som **libs** > **settings** > **cloudsettings** > **default** **** ****>¥ContextHub Configurations¥ och klicka på¥Select¥.

   1. Välj **Segmentsökväg** som **conf** > **We.Retail **> **settings** > **wcm** > **segments** **** och klicka sedan på¥Select.

   1. Klicka på **Spara och stäng**.
   >[!NOTE]
   Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   Om du inte väljer **Varumärke** under **Målkonfiguration** i dialogrutan ovan måste du välja Varumärke och Aktivitet när du påbörjar målprocessen.

1. Navigera till och välj **DataDrivenRetail** från **DataDrivenAssets** > **Channels **och klicka på **Redigera** i åtgärdsfältet.

   >[!NOTE]
   Om du har konfigurerat allt korrekt visas alternativet **Riktning** i listrutan från redigeraren, vilket visas i bilden nedan.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   När du har konfigurerat ContextHub-konfigurationerna för din kanal måste du följa de föregående stegen från 1 till 4 för de andra tre sekvenskanalerna också om du vill följa alla användningsexempel nedan.

## Användningsfall 1: Aktivering av butikslager {#use-case-retail-inventory-activation}

I följande exempel visas tre olika bilder baserat på värdena i Google Sheet.

### Beskrivning {#description}

Denna Use Case visar butikslagret för tre olika färgade tröjor. Beroende på hur många tröjor som finns i lager och som spelats in på Google Sheets, visas bilden (röd, grön eller blå tröja) med det högsta antalet på skärmen.

I det här fallet visas den röda, gröna eller blå tröjan på skärmen baserat på det högsta antalet svettare som är tillgängliga.

### Förfarande {#procedure}

Följ stegen nedan för att implementera användningsexemplet för butikslageraktivering:

1. **Fylla i Google Sheets**

   1. Navigera till ContextHubDemo Google Sheet.
   1. Lägg till tre kolumner (röd, grön och blå) med motsvarande värden för tre olika tröjor.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Konfigurera publikerna enligt kraven**

   1. Navigera till segmenten i målgruppen (skapat i steg 5 i avsnitt ***Steg 2: Konfigurera AEM för att hämta innehållet i Google Sheets***).
   1. Lägg till tre nya segment **för_röd**, **för_grön** och **för_blå**.

   1. Välj **For_Red** och klicka på **Redigera** i åtgärdsfältet.

   1. Dra och släpp **jämförelsen: Egenskap - Egenskap** till redigeraren och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/2** i listrutan i namnet **för första egenskap**

   1. Välj **Operatör** som **större än **i listrutan

   1. Välj **datatyp** som **tal**

   1. Välj **Googlesheets/value/1/1** i listrutan i namnet på den **sekundära egenskapen**

   1. Dra och släpp **en annan jämförelse: Egenskap - Egenskap **till redigeraren och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/2** i listrutan i namnet **för första egenskap**

   1. Välj **Operatör** som **större än **i listrutan

   1. Välj **datatyp** som **nummer**

   1. Välj **Googlesheets/value/1/0** i listrutan i namnet på den **sekundära egenskapen**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Du kan på liknande sätt redigera och lägga till egenskapsregler för jämförelse i **For_Blue** -segmentet enligt figuren nedan:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Du kan på liknande sätt redigera och lägga till egenskapsregler för jämförelse i** For_Green **segment enligt bilden nedan:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   Du kommer att märka att för segment **For_Green** och **For_Green** går det inte att läsa in data i redigeraren eftersom endast den första jämförelsen är giltig från och med nu enligt värdena i Google Sheet.

1. Navigera till och markera din **DataDrivenRetail **kanal (en sekvenskanal) och klicka på **Redigera** i åtgärdsfältet.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   Du bör ha konfigurerat **ContextHub** **Configurations** med hjälp av fliken **Kanalegenskaper** —> **Personalisering** .

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Om du inte lägger till **Varumärke** under **Målkonfigurationer** när du konfigurerar **ContextHub-konfigurationer** för ditt projekt, som bilden ovan visar, måste du välja **Varumärke** och **Aktivitet** när du påbörjar målinriktningsprocessen i nästa steg.

1. **Lägga till en standardbild**

   1. Lägg till en standardbild i kanalen och klicka på **Mål**.
   1. Välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Start Targeting**.

   1. Klicka på **Starta mål**.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Innan du börjar med målinriktningen måste du lägga till segmenten (**For_Green**, **For_Red** och **For_Blue**) genom att klicka på **+ Lägg till** upplevelsemål från sidospåret enligt bilden nedan.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Lägg till bilderna i alla tre olika scenarier enligt nedan.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Kontrollera förhandsvisningen**

   1. Klicka på **Förhandsgranska.** Öppna även Google Sheet och uppdatera värdet.
   1. Ändra värdet för alla tre olika kolumner så kommer du att märka att visningsbilden uppdateras enligt det högsta värdet i lagret.
   ![retail_result](assets/retail_result.gif)

## Användningsfall 2: Resecenterväderaktivering {#use-case-travel-center-weather-activation}

I följande exempel visas två olika bilder baserat på värdena i Google Sheet.

### Beskrivning {#description-1}

Om ditt Google Sheets har ett värde under 50 visas en bild med varma drycker och om värdet är större än eller lika med 50 visas bilden med kalla drycker. Om något annat eller inget värde anges visas en standardbild.

### Förfarande {#procedure-1}

Följ stegen nedan för att implementera väderaktiveringsexemplet för ditt AEM Screens-projekt:

1. **Fylla i Google Sheets**

   1. Navigera till ContextHubDemo Google Sheet.
   1. Lägg till en kolumn med **Rubrik1** med motsvarande värde för temperatur.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Konfigurera segmenten i publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (skapat i steg 5 i avsnitt ***Steg 2: Konfigurera AEM för att hämta innehållet i Google Sheets***).
   1. Markera **blad A1 1** och klicka på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**

   1. Välj **Operatorn** som **större än eller lika med **i listrutan

   1. Ange **värdet** som **50**

   1. På samma sätt väljer du* Sheets A1 2 **och klickar på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**

   1. Välj **Operator** som **less-than **i listrutan

   1. Ange **värdet** som **50**

1. Navigera och markera kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel används **DataDrivenWeather** som en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   Din kanal bör redan ha en standardbild och publikerna bör vara förkonfigurerade enligt beskrivningen i steg 3

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   Du bör ha konfigurerat **ContextHub** **Configurations** med hjälp av fliken **Kanalegenskaper** —> **Personalisering** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   Om du inte lägger till **Varumärke** under **Målkonfigurationer** när du konfigurerar **ContextHub-konfigurationer** för ditt projekt, som bilden ovan visar, måste du välja **Varumärke** och **Aktivitet** när du påbörjar målinriktningsprocessen i nästa steg.

1. Välj **Riktning** i redigeraren och välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Start Targeting**.

   >[!NOTE]
   Om du lade till **Varumärke** under **Målkonfigurationer** när du konfigurerade **ContextHub-konfigurationer** för ditt projekt behöver du inte välja **Varumärke** och **Aktivitet** i det här steget.

   ![new_activity3](assets/new_activity3.gif)

1. Kontrollera förhandsvisningen

   1. Klicka på **Förhandsgranska.** Öppna även Google Sheet och uppdatera värdet.
   1. Om du ändrar värdet till mindre än 50 bör du kunna se en bild av sommardrycker. Om värdet i Google Sheet är 50 eller högre än vad som ska kunna visa bilden med en het drink.
   ![result3](assets/result3.gif)

## Användningsfall 3: Aktivering av hotellreservation {#use-case-hospitality-reservation-activation}

I följande exempel visas två olika bilder baserat på värdena och formeln som används i Google Sheet.

### Beskrivning {#description-2}

I det här användningsfallet fylls Google Sheet i med en procentandel reservationer på två restauranger **Restaurant1** och **Restaurant2**. En formel tillämpas baserat på värdena för Restaurant1 och Restaurant2 och baserat på formeln, så tilldelas värdet 1 eller 2 till **AdTarget** -kolumnen.

Om **Restaurant1** > **Restaurant2**&#x200B;är **AdTaget** -värdet 1, annars tilldelas **AdTarget** värdet 2. Värdet 1 genererar *alternativet Svag mat* och värdet 2 ger resultatet att *thailändska matalternativ* visas på skärmen.

### Procedurmetod {#procedural-approach}

Följ stegen nedan för att implementera användningsexemplet för aktivering av gästreservation för ditt AEM Screens-projekt:

1. Fylla i Google Sheets och lägga till formeln.

   Du kan t.ex. använda formeln på den tredje kolumnen **AdTarget**, vilket visas i figuren nedan.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Konfigurera segmenten i publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (skapat i steg 5 i avsnitt ***Steg 2: Konfigurera AEM för att hämta innehållet i Google Sheets***).
   1. Markera **blad A1 1** och klicka på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/2** i listrutan i **Egenskapsnamn**

   1. Välj **Operator** som **equal **i listrutan

   1. Ange **värdet** som **1**

   1. På samma sätt väljer du* Sheets A1 2 **och klickar på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/2** i listrutan i **Egenskapsnamn**

   1. Välj **operatorn** som **2**

1. Navigera och markera kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel, **DataDrivenRestaurant**, används en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   Din kanal bör redan ha en standardbild och publikerna bör vara förkonfigurerade enligt beskrivningen i steg 3.

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   Du bör ha konfigurerat **ContextHub** **Configurations** med hjälp av fliken **Kanalegenskaper** —> **Personalisering** .

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   Om du inte lägger till **Varumärke** under **Målkonfigurationer** när du konfigurerar **ContextHub-konfigurationer** för ditt projekt, som bilden ovan visar, måste du välja **Varumärke** och **Aktivitet** när du påbörjar målinriktningsprocessen i nästa steg.

1. Välj **Riktning** i redigeraren och välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Start Targeting**.
1. Kontrollera förhandsvisningen

   1. Klicka på **Förhandsgranska.** Öppna även Google Sheet och uppdatera värdet.
   1. Ändra värdet i Restaurant1 > Restaurant2, du bör kunna visa en bild av en högdager bild och Restaurant1 &lt; Restaurant12, du bör kunna visa den högklassiga bilden på skärmen.
   ![result5](assets/result5.gif)

## Användningsfall 4: Textövertäckning för den digitala menyraden {#use-case-digital-menu-board-text-overlay}

I följande exempel visas en digital menyrad som ofta används på restauranger och snabbmatsleder.

### Beskrivning {#description-3}

I följande Use Case (Använd skiftläge) beskrivs användningen av textövertäckning i en sekventiell kanal och hur värdeuppdateringen av priset i Google Sheets utlöser en uppdatering i textöverläggskomponentuppdateringen.

### Procedurmetod {#procedural-approach-1}

Följ stegen nedan för att implementera det digitala menykortet med textövertäckning för ditt AEM Screens-projekt:

1. **Fylla i Google Sheets**

   1. Navigera till dina Google Sheets.
   1. Lägg till en kolumn med prisvärde för användningsfallet, vilket visas i figuren nedan.
   ![screen_shot_2019-05-05at11344am](assets/screen_shot_2019-05-05at111344am.png)

1. **Lägga till en bild i sekvenskanalen**

   1. Navigera och markera kanalen (**DataDrivenAssets** —> **Kanaler** —> **DataDrivenTextOverlay**).

   1. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.
   1. Dra och släpp en äppelcirkelbild i redigeraren.
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **Lägga till textövertäckning i bilden**

   1. Markera bilden i redigeraren och klicka på Konfigurera.
   1. Navigera till fliken **Textövertäckning** och lägg till textöverlägget i bilden. För att få ut värdet från dina Google Sheets måste du se till att värdet omsluts av de aktuella parenteserna. Priset hämtas till exempel från Google Sheets och omnämns som **{price}** när textövertäckningen definieras.

   1. Navigera till **fliken ContextHub** och konfigurera värdet som ska hämtas från Google Sheets, vilket visas i bilden nedan.
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **Kontrollera förhandsvisningen**

   <!-- Edit text in steps below. wonky-->

   1. Klicka på **Förhandsgranska**. Öppna även Google Sheet och uppdatera värdet.
   1. Ändra under **Pris** så uppdateras värdet som används i textövertäckningen enligt bilden nedan.
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)
