---
title: ContextHub konfigureras i AEM Screens
seo-title: ContextHub konfigureras i AEM Screens
description: Följ den här sidan för att lära dig mer om ContextHub i målmotorn för att definiera datalagring för innehållsändring för utlösare.
seo-description: Följ den här sidan för att lära dig mer om ContextHub i målmotorn för att definiera datalagring för innehållsändring för utlösare.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: Utveckla skärmar
role: Developer
level: Mellanliggande
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 1%

---


# ContextHub konfigureras i AEM Screens {#configuring-contexthub-in-aem-screens}

I det här avsnittet betonas hur du skapar och hanterar datadrivna resursändringar med hjälp av ett datalager.

## Nyckeltermer {#key-terms}

Innan vi får in mer ingående information om hur ni skapar och hanterar lagerdrivna kanaler i AEM Screens-projekt måste ni lära er några viktiga termer som är viktiga och relevanta för de olika scenarierna.

**** BrandAvser din projektbeskrivning på hög nivå.

**** AreaRefererar till ditt projektnamn från AEM Screens, t.ex. Digital Ad Signage

**Aktivitet** Definierar regelkategorin som Inventory-Driven, Weather-Driven, Department Availability-Driven och så vidare.

**Audience** Definierar regeln.

**** SegmentAvser den version av resursen som ska spelas upp för den angivna regeln, t.ex. om temperaturen är under 50 grader, så visar skärmen en bild av ett varmt kaffe, annars ett kallt glas.

I följande diagram visas hur ContextHub-konfigurationer sammanfaller med Activity, Audience och Channels.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Förhandsvillkor {#preconditions}

Innan du börjar konfigurera Context Hub-konfigurationer för ett AEM Screens-projekt måste du konfigurera Google Sheets (i demonstrationssyfte).

>[!IMPORTANT]
>
>Google Sheets används i följande exempel som ett exempeldatabassystem från vilket värdena hämtas och är endast avsett för utbildningsändamål. Adobe stöder inte Google Sheets för produktionsmiljöer.
>
>Mer information finns i [Hämta API-nyckel](https://developers.google.com/maps/documentation/javascript/get-api-key) i Google-dokumentationen.

## Steg 1: Konfigurera ett datalager {#step-setting-up-a-data-store}

Du kan konfigurera datalagret som en lokal I/O-händelse eller som en lokal databashändelse.

Följande datanivådata utlöser ett exempel på en lokal databashändelse som ställer in ett datalager, t.ex. ett Excel-blad, som gör att du kan använda ContextHub-konfigurationer och segmentsökvägar till AEM Screens-kanalen.

När du har ställt in Google Sheet korrekt, till exempel enligt nedan:

![bild](/help/user-guide/assets/context-hub/context-hub1.png)

Följande validering är vad du kommer att se när du kontrollerar anslutningen genom att ange de två värdena *google sheet ID* och *API-nyckel* i formatet nedan:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![bild](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>I det specifika exemplet nedan visas Google-tabellerna som ett datalager som utlöser en resursändring om värdet är högre än 100 eller lägre än 50.

## Steg 2: Konfigurera lagringskonfigurationer {#step-setting-store-configurations}

1. **Navigera till ContextHub**

   Navigera till din AEM och klicka på verktygsikonen från vänster sidofält. Klicka på **Platser** —> **ContextHub**, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Skapa en ny konfiguration för ContextHub Store**

   1. Navigera till konfigurationsbehållaren med namnet **screens**.

   1. Klicka på **Skapa** > **Skapa konfigurationsbehållare** och ange titeln som **ContextHubDemo**.

      ![bild](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **** Navigera till  **ContextHubDemo** >  **** **CreateContentHub** Configurationoch klicka på  **Spara**.

      >[!NOTE]
      > När du har klickat på **Spara** visas du på skärmen **ContextHub Configuration**.

   1. På skärmen **ContextHub Configuration** klickar du på **Create** > **ContentHub Store Configuration..**

      ![bild](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >Som en del av AEM 6.5 Feature Pack 4 eller AEM 6.4 Feature Pack 8 ska kunderna uppdatera `/conf/screens/settings/cloudsettings` till `sling:Folder`.
      >
      >Följ stegen nedan:
      >
      >1. Navigera till CRXDE Lite och sedan till `/conf/screens/settings/cloudsettings`.
      >1. Kontrollera om `cloudsettings jcr:primaryType` är i `sling:Folder`. Om `jcr:primaryType` inte är i `sling:folder` fortsätter du till nästa steg.
      >1. Högerklicka på `/conf/screens/settings` och skapa en ny nod med *namn* som **molninställningar1** och *Skriv* som **sling:Folder** och spara ändringarna.
      >1. Flytta alla noder under `/conf/screens/settings/cloudsettings` till `cloudsettings1`.
      >1. Ta bort `cloudsettings` och spara.
      >1. Byt namn på `cloudsettings1` till `cloudsettings` och spara.
      >1. Du bör nu observera att /conf/screens/settings/cloudsettings har `jcr:primaryType` som `sling:Folder`.

      >
      >Följ dessa steg i programmet och publicera före eller efter uppgraderingen.

   1. Ange **titeln** som **Google Sheets**, **Store Name** as **googlesheets** och **Store Type** som **contexthub.generic-jsonp** och klicka på **Nästa**.

      >[!CAUTION]
      >Om du använder Adobe Experience Manager (AEM) 6.4 anger du **Configuration Title** som **googlesheets** och **Store Type** som **contexthub.generic-jsonp**.

      ![bild](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Ange din specifika json-konfiguration. Du kan t.ex. använda följande json som demoversion och klicka på **Spara** så visas butikskonfigurationen **Google Sheets** i ContextHub-konfigurationen.

      >[!IMPORTANT]
      >Se till att ersätta koden med *&lt;Sheet ID>* och *&lt;API Key>*, som du hämtade när du konfigurerade Google Sheets.

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      I ovanstående exempelkod definierar **pollInterval** den frekvens med vilken värdena uppdateras (i ms).
      Ersätt koden med *&lt;Sheet ID>* och *&lt;API Key>*, som du hämtade när du konfigurerade Google Sheets.

      >[!CAUTION]
      Om du skapar dina Google Sheets-lagringskonfigurationer utanför den globala mappen (t.ex. i din egen projektmapp) kommer målanpassning inte att fungera som den ska.


1. **Konfigurera butikssegmentering**

   1. Navigera till **Konfiguration av ContentHub Store.** och skapa en annan butikskonfiguration i skärmkonfigurationsbehållaren och ange  **** Titleas  **segmentation-contexthub**,  **Store** Name as  **** segmentation och  **Store** TypeAs  **aem.segmentation**.

      ![bild](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Klicka på **Nästa** och sedan **Spara**.

      >[!NOTE]
Du måste hoppa över processen att definiera json och lämna den tom.


## Steg 3: Konfigurera segment i målgruppen {#setting-up-audience}

1. **Skapa segment i målgrupper**

   1. Navigera från din AEM till **Personalisering** > **Publiker** > **skärmar**.

   1. Klicka på **Skapa** > **Skapa kontextnavsegment.** Dialogrutan  **Nytt ContextHub-** segment öppnas.

   1. Ange **titeln** som **högre än 50** och klicka på **Skapa**. Skapa på samma sätt ett annat segment med namnet **Lowerthan50**.

      ![bild](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Markera segmentet **högre än 50** och klicka på **Egenskaper** i åtgärdsfältet.
      ![bild](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Välj fliken **Personalisering** i **Segmentegenskaper**. Ange **ContextHub-sökvägen** till `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` och **Segmentsökvägen** till `/conf/screens/settings/wcm/segments` och klicka på **Spara**, enligt bilden nedan.

      ![bild](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Du kan även ställa in **ContextHub-sökvägen** och **Segmentsökvägen** för segmentet **Lowerthan50**.

## Steg 4: Konfigurera varumärke och område {#setting-brand-area}

Följ stegen nedan för att skapa ett varumärke i era aktiviteter och i ert område under varumärket:

1. **Skapa ett varumärke i aktiviteter**

   1. Gå från din AEM till **Personalisering** > **Aktiviteter**.

   1. Klicka på **Skapa** > **Skapa varumärke**.

   1. Välj **Varumärke** i guiden **Skapa sida** och klicka på **Nästa**.

   1. Ange **titeln** som **ScreensBrand** och klicka på **Skapa**. Ditt varumärke har nu skapats enligt nedan.

      ![bild](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Känt fel:
Om du vill lägga till ett område tar du bort överordnad från URL-adressen, till exempel
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Skapa ett område i ditt varumärke**

   Följ stegen nedan för att skapa ett område i varumärket:

   1. Klicka på **Skapa** och **Skapa område**.

      ![bild](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Välj **Område** i guiden **Skapa sida** och klicka på **Nästa**.

   1. Ange **titeln** som **Skärmvärde** och klicka på **Skapa**.
Ett område kommer att skapas i ert varumärke.

## Steg 5: Skapa segment i en aktivitet {#step-setting-up-audience-segmentation}

När du har konfigurerat ett datalager och definierat din aktivitet (varumärke och område) följer du stegen nedan för att skapa segment i din aktivitet.

1. **Skapa segment i aktiviteter**

   1. Gå från din AEM till **Personalisering** > **Aktiviteter** > **Skärmmärke** >**Skärmvärde**.

   1. Klicka på **Skapa** > **Skapa aktivitet.** The  **Configure Activity** Wizardopens.

   1. Ange **titeln** som **ValueCheck50** och **Namn** som **valueCheck50**. Välj **målmotorn** som **ContextHub (AEM)** i listrutan och klicka på **Nästa**.

      ![bild](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Klicka på **Lägg till upplevelse** i **guiden Konfigurera aktivitet**.

   1. I **Publiker** väljer du **Higher50** och klickar på **Lägg till upplevelse** och anger **titeln** som **högre än50** **Namn** som &lt;a a12/>högre än 50 **.** Klicka på **OK**.

   1. I **Publiker** väljer du **Nedre än50** och klickar på **Lägg till upplevelse** och anger **titeln** som **lägre än50** **Namn** som &lt;a a12/>lägre än 50 **.** Klicka på **OK**.

      ![bild](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Klicka på **Nästa** och sedan **Spara**. **ValueCheck50-** aktiviteten har nu skapats och konfigurerats.

      ![bild](/help/user-guide/assets/context-hub/context-hub16.png)

## Steg 5: Redigera segment i publiker{#editing-audience-segmentation}

1. **Redigera segment**

   1. Navigera från din AEM till **Personalisering** > **Publiker** > **skärmar**.

   1. Markera segmentet **högre än 50** och klicka på **Redigera** i åtgärdsfältet.

   1. Dra och släpp **jämförelsen: Egenskap - Värde**-komponent till redigeraren.

   1. Klicka på skiftnyckelsikonen för att öppna dialogrutan **Jämföra en egenskap med värdet**.

   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**.

      >[!NOTE]
Google  **heets/value/1/0** hänvisar till rad 2 och kolumn som fylls i i Google Sheets i figuren nedan:

      ![bild](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Välj **Operator** som **större än** i listrutan.

   1. Ange **värdet** som **70**.

      >[!NOTE]
      AEM validerar dina data från Google Sheet genom att visa ditt segment som grönt.

      ![bild](/help/user-guide/assets/context-hub/context-hub18.png)
   Redigera på samma sätt egenskapsvärdena till **Lowerthan50**.

   1. Dra och släpp **jämförelsen: Egenskap - Värde**-komponent till redigeraren.

   1. Klicka på skiftnyckelsikonen för att öppna dialogrutan **Jämföra en egenskap med värdet**.

   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**.

   1. Välj **Operator** som **mindre än** i listrutan.

   1. Ange **värdet** som **50**.



## Aktivera mål i kanaler {#step-enabling-targeting-in-channels}

Följ stegen nedan för att aktivera målinriktning i dina kanaler.

1. Navigera till en av AEM Screens-kanalerna. Följande steg visar hur du aktiverar mål genom att använda **DataDrivenChannel** som skapats i en AEM Screens-kanal.

1. Markera kanalen **TargetChannel** och klicka på **Egenskaper** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/context-hub/context-hub19.png)

1. Välj fliken **Personalisering** för att konfigurera ContextHub-konfigurationer.

   1. Ange **ContextHub-sökvägen** till `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` och **Segmentsökvägen** till `/conf/screens/settings/wcm/segments` och klicka på **Spara**.

   1. Klicka på **Spara och stäng**.

      >[!NOTE]
      Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

      ![bild](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Navigera till och markera kanalen **TargetChannel** och klicka på **Redigera** i åtgärdsfältet.

      >[!NOTE]
      Om du har konfigurerat allt korrekt visas alternativet **Målinriktning** i listrutan från redigeraren, vilket visas i bilden nedan.

      ![bild](/help/user-guide/assets/context-hub/context-hub21.png)

## Läs mer: Exempel på användningsfall {#learn-more-example-use-cases}

När du har konfigurerat ContextHub för ditt AEM Screens-projekt kan du följa de olika användningsexemplen för att förstå hur datautlösande resurser spelar en viktig roll i olika branscher:

1. **[Målinställd aktivering för butikslager](retail-inventory-activation.md)**
1. **[Temperaturaktivering i resecentret](local-temperature-activation.md)**
1. **[Aktivering av hotellreservation](hospitality-reservation-activation.md)**
