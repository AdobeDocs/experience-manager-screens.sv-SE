---
title: ContextHub konfigureras i AEM-skärmar
seo-title: ContextHub konfigureras i AEM-skärmar
description: Följ den här sidan för att lära dig mer om ContextHub i målmotorn för att definiera datalagring för innehållsändring för utlösare.
seo-description: Följ den här sidan för att lära dig mer om ContextHub i målmotorn för att definiera datalagring för innehållsändring för utlösare.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: 69dd2238562c00ab83e63e268515e24dee55f5ee

---


# ContextHub konfigureras i AEM-skärmar {#configuring-contexthub-in-aem-screens}

I det här avsnittet betonas hur du skapar och hanterar datadrivna resursändringar med hjälp av ett datalager.

## Nyckeltermer {#key-terms}

Innan vi får mer information om hur du skapar och hanterar lagerdrivna kanaler i ditt AEM Screens-projekt måste du lära dig några viktiga termer som är viktiga och relevanta för de olika scenarierna.

**Varumärke** hänvisar till din projektbeskrivning på hög nivå.

**Område** refererar till ditt projektnamn för AEM-skärmar, t.ex. Digital Ad Signage

**Aktivitet** definierar regelkategorin, t.ex. Lagerstyrd, Väderstyrd, Avdelningstillgänglighetsstyrd osv.

**Målgrupp** definierar regeln.

**Segment** Avser den version av resursen som ska spelas upp för den angivna regeln, t.ex. om temperaturen är under 50 grader, så visar skärmen en bild av ett varmt kaffe, i annat fall en kall dryck.

I följande diagram visas hur ContextHub-konfigurationer sammanfaller med Activity, Audience och Channels.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Förhandsvillkor {#preconditions}

Innan du börjar konfigurera Context Hub Configurations för ett AEM Screens-projekt måste du konfigurera Google Sheets (i demonstrationssyfte).

>[!CAUTION]
>
>Google Sheets används i följande exempel som ett exempeldatabassystem från vilket värdena hämtas och är endast avsett för utbildningsändamål. Adobe stöder inte Google Sheets för produktionsmiljöer.
>
>Mer information finns i [Hämta API-nyckel](https://developers.google.com/maps/documentation/javascript/get-api-key) i Google-dokumentationen.

## Steg 1: Konfigurera ett datalager {#step-setting-up-a-data-store}

Du kan konfigurera datalagret som en lokal I/O-händelse eller som en lokal databashändelse.

### Lokal I/O-händelse {#local-io-event}

Följ stegen nedan för att konfigurera ett datalager, t.ex. en ASCII-händelse, som gör att du kan använda ContextHub-konfigurationer och segmentsökvägar till AEM Screens-kanalen.

### Händelse för lokal databas {#local-db-event}

Följ stegen nedan för att konfigurera ett datalager, t.ex. ett Excel-blad, som gör att du kan använda ContextHub-konfigurationer och segmentsökvägar till AEM Screens-kanalen.

1. **Navigera till ContextHub**

   Navigera till din AEM-instans och klicka på verktygsikonen i det vänstra sidofältet. Klicka på **Webbplatser** —> **ContextHub**, som bilden nedan visar.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Skapa en ny konfiguration för ContextHub Store**

   1. Navigera till **global** > **default** > **ContextHub Configuration**.

   1. Klicka på **Skapa** > **Konfigurationsbehållare** och ange titeln som **ContextHubDemo**.

   1. **Navigera** till **ContextHubDemo** > **Konfiguration för ContentHub Store..** för att öppna **konfigurationsguiden**.

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
   >Ersätt koden med ditt *&lt;Sheet ID>* och *&lt;API Key>*, som du hämtade när du konfigurerade Google Sheets.

   >[!CAUTION]
   Om du skapar dina Google Sheets-lagringskonfigurationer utanför den gamla mappen (till exempel i din egen projektmapp) kommer målanpassning inte att fungera som de ska.
   Om du vill konfigurera Google Sheets-lagringskonfigurationer utanför den globala äldre mappen måste du ange **Store Name** som **segmentering** och **Store Type** som **aem.segmentation**. Dessutom måste du hoppa över processen att definiera json enligt definitionen ovan.

1. **Skapa ett varumärke i aktiviteter**

   1. Navigera från din AEM-instans till **Personalisering** > **Verksamheter**

   1. Klicka på **Skapa** > **Skapa varumärke**

   1. Välj **Varumärke** i guiden **Skapa sida** och klicka på **Nästa**

   1. Ange **Title** som **ContextHubDemo** och klicka på **Create**. Ditt varumärke har nu skapats enligt nedan.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)


   >[!CAUTION]
   Känt fel:
   Om du vill lägga till ett område tar du bort mallen från URL:en, t.ex.
   `https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master`

1. **Skapa ett område i ditt varumärke**

   Följ stegen nedan för att skapa ett område i varumärket:

   1. Klicka på **Skapa** och sedan **Skapa område**

   1. Välj **område** i guiden **Skapa sida** och klicka på Nästa

   1. Ange **titeln** som **GoogleSheets** och klicka på **Skapa**.
Området skapas i din aktivitet.

## Steg 2: Konfigurera målgruppssegmentering {#step-setting-up-audience-segmentation}

När ni väl har skapat en datalagring och definierat ert varumärke följer ni stegen nedan för att skapa målgruppssegment.

1. **Skapa segment i målgrupper**

   1. Navigera från din AEM-instans till **Personalisering** > **Publiker** > **We.Retail**.

   1. Klicka på **Skapa** > **Skapa kontextnavsegment.** Dialogrutan **Nytt ContextHub-segment** öppnas.

   1. Ange **titeln** som **BladA1 1** och klicka på **Skapa**. Du kan också skapa ett annat segment med namnet **SheetA2 2**.

1. **Redigera segment**

   1. Markera segmentmallarna **A1 1** (skapade i steg 5) och klicka på **Redigera** i åtgärdsfältet.

   1. Dra och släpp **jämförelsen: Egenskap - Värdekomponent** till redigeraren.
   1. Klicka på skiftnyckelsikonen för att öppna dialogrutan **Jämför en egenskap med ett värde** .
   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**.

   1. Välj **Operator** as **Equal** i listrutan.

   1. Ange **värdet** som **1**.
   >[!NOTE]
   AEM validerar dina data från Google Sheet genom att visa ditt segment som grönt.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   Du kan också redigera egenskapsvärdena till **Blad A1 2**.

   1. Dra och släpp **jämförelsen: Egenskap - Värdekomponent** till redigeraren.
   1. Klicka på skiftnyckelsikonen för att öppna dialogrutan **Jämför en egenskap med ett värde** .
   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**.

   1. Välj **Operator** as **Equal** i listrutan.

   1. Ange **värdet** som **2**.
   >[!NOTE]
   Reglerna som används i de föregående stegen är bara ett exempel på hur du ställer in segment för implementering av följande användningsexempel.

## Steg 3: Aktivera mål i kanaler {#step-enabling-targeting-in-channels}

Följ stegen nedan för att aktivera målinriktning i dina kanaler.

1. Navigera till en av AEM-skärmarna. Följande steg visar hur du aktiverar målinriktning genom att använda **DataDrivenRetail** som skapats i en AEM Screens Channel.

1. Välj kanalen **DataDrivenRetail** och klicka på **Egenskaper** i åtgärdsfältet.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Välj fliken **Personalisering** för att konfigurera ContextHub-konfigurationer.

   1. Välj **ContextHub Path** som **libs** > **settings** > **cloudsettings** > **default** **** ****>¥ContextHub Configurations¥ och klicka på¥Select¥.

   1. Välj **Segmentsökväg** som **conf** > **We.Retail** > **settings** > **wcm** **** ****>¥segments¥ och klicka¥Select.

   1. Klicka på **Spara och stäng**.
   >[!NOTE]
   Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navigera till och välj **DataDrivenRetail** från **DataDrivenAssets** > **Kanaler** och klicka på **Redigera** i åtgärdsfältet.

   >[!NOTE]
   Om du har konfigurerat allt korrekt visas alternativet **Riktning** i listrutan från redigeraren, vilket visas i bilden nedan.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   När du har konfigurerat ContextHub-konfigurationerna för din kanal måste du följa de föregående stegen från 1 till 4 för de andra tre sekvenskanalerna också om du vill följa alla användningsexempel nedan.

## Läs mer: Exempel på användningsfall {#learn-more-example-use-cases}

När du har konfigurerat ContextHub för ditt AEM Screens-projekt kan du följa de olika användningsexemplen för att förstå hur datautlösande resurser spelar en viktig roll i olika branscher:

1. **[Målinställd aktivering för butikslager](retail-inventory-activation.md)**
1. **[Temperaturaktivering i resecentret](local-temperature-activation.md)**
1. **[Aktivering av hotellreservation](hospitality-reservation-activation.md)**
