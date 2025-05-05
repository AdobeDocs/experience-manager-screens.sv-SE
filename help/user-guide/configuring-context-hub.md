---
title: ContextHub konfigureras i AEM Screens
description: Lär dig mer om ContextHub i målmotorn så att du kan definiera ett datalager för innehållsändring i utlösare.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 1%

---

# ContextHub konfigureras i AEM Screens {#configuring-contexthub-in-aem-screens}

I det här avsnittet betonas hur du skapar och hanterar datadrivna resursändringar med hjälp av ett datalager.

## Nyckeltermer {#key-terms}

Innan du får mer information om hur du skapar och hanterar lagerdrivna kanaler i ditt AEM Screens-projekt bör du lära dig några av nyckeltermerna till de olika scenarierna.

**Varumärke** - Din projektbeskrivning på hög nivå.

**Område** - Ditt AEM Screens-projektnamn, till exempel Digital Ad Signage

**Aktivitet** - Definierar kategoriregler som Inventory-Driven, Weather-Driven eller Department Availability-Driven.

**Målgrupp** - Definierar regeln.

**Segment** - Den version av en resurs som ska spelas upp för den angivna regeln. Om temperaturen till exempel är under 50 grader Fahrenheit visar skärmen en bild av en varm dryck, i annat fall en kall dryck.

I följande diagram visas hur ContextHub-konfigurationer sammanfaller med Activity, Audience och Channels.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Förhandsvillkor {#preconditions}

Innan du börjar konfigurera ContextHub-konfigurationer för ett AEM Screens-projekt måste du konfigurera Google Sheets (i demonstrationssyfte).

>[!IMPORTANT]
>
>Google Sheets används i följande exempel som ett exempeldatabassystem från vilket värdena hämtas och endast är avsett för utbildningsändamål. Adobe stöder inte användning av Google Sheets för produktionsmiljöer.
>
>Mer information finns i [Hämta API-nyckel](https://developers.google.com/maps/documentation/javascript/get-api-key) i Google-dokumentationen.

## Steg 1: Konfigurera ett datalager {#step-setting-up-a-data-store}

Du kan konfigurera datalagret som en lokal I/O-händelse eller som en lokal databashändelse.

Följande datanivådata utlöser exempel på en lokal databashändelse. Händelsen ställer in ett datalager, t.ex. ett Excel-blad, som gör att du kan använda ContextHub-konfigurationer och segmentsökvägar till AEM Screens-kanalen.

När du har konfigurerat bladet `google` korrekt, vilket visas i exemplet nedan:

![bild](/help/user-guide/assets/context-hub/context-hub1.png)

Följande validering är den du visar när du kontrollerar anslutningen genom att ange de två värdena, `*google sheet ID*` och `*API key*`, i formatet nedan:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![bild](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>I det specifika exemplet nedan visas Google Sheets som ett datalager som utlöser en resursändring om värdet är högre än 100 eller lägre än 50.

## Steg 2: Konfigurera butikskonfigurationer {#step-setting-store-configurations}

1. **Navigerar till ContextHub**

   Navigera till AEM och klicka på verktygsikonen i det vänstra sidfältet. Klicka på **Platser** > **ContextHub**, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Skapar en ContextHub Store-konfiguration**

   1. Navigera till konfigurationsbehållaren med namnet **screens**.

   1. Klicka på **Skapa** > **Skapa konfigurationsbehållare** och ange titeln som **ContextHubDemo**.

      ![bild](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Navigera** till **ContextHubDemo** > **Skapa** **ContentHub-konfiguration** och klicka på **Spara**.

      >[!NOTE]
      > När du har klickat på **Spara** visas skärmen **ContextHub Configuration** .

   1. På skärmen **ContextHub Configuration** klickar du på **Create** > **ContentHub Store Configuration**

   ![bild](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >Som en del av AEM 6.5 Feature Pack 4 eller AEM 6.4 Feature Pack 8, bör kunder uppdatera `/conf/screens/settings/cloudsettings` till `sling:Folder`.
   >
   >Följ stegen nedan:
   >
   >1. Navigera till CRXDE Lite och sedan till `/conf/screens/settings/cloudsettings`.
   >1. Kontrollera om `cloudsettings jcr:primaryType` finns i `sling:Folder`. Om `jcr:primaryType` inte finns i `sling:folder` fortsätter du till nästa steg.
   >1. Högerklicka på `/conf/screens/settings` och skapa en nod med *name* som **`cloudsettings1`** och *Type* som **`sling:Folder`** och spara ändringarna.
   >1. Flytta alla noder under `/conf/screens/settings/cloudsettings` till `cloudsettings1`.
   >1. Ta bort `cloudsettings` och spara.
   >1. Byt namn på `cloudsettings1` till `cloudsettings` och spara.
   >1. Observera att `/conf/screens/settings/cloudsettings` har `jcr:primaryType` som `sling:Folder`.
   >
   >Följ de här stegen i Författare och Publish före eller efter uppgraderingen.

   1. Ange **Titel** som **Google-blad**, **Butiksnamn** som **`googlesheets`** och **Lagringstyp** som **c`ontexthub.generic-jsonp`** och klicka på **Nästa**.

      >[!CAUTION]
      >Om du använder Adobe Experience Manager (AEM) 6.4 anger du **Configuration Title** som **`googlesheets`** och **Store Type** som **c`ontexthub.generic-jsonp`**.

      ![bild](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Ange din specifika json-konfiguration. Du kan till exempel använda följande json för demoändamål och klicka på **Spara**. Butikskonfigurationen visas med namnet **Google Sheets** i ContextHub-konfigurationen.

      >[!IMPORTANT]
      >Se till att ersätta koden med din `*<Sheet ID>*` och `*<API Key>*` som du hämtade när du konfigurerade Google-bladen.

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
      >
      >I ovanstående exempelkod definierar **pollInterval** den frekvens med vilken värdena uppdateras (i millisekunder).
      >
      >Ersätt koden med din `*<Sheet ID>*` och `*<API Key>*` som du hämtade när du konfigurerade Google Sheets.

      >[!CAUTION]
      >
      >Om du skapar dina Google-blad för att lagra konfigurationer utanför den globala mappen (till exempel i din egen projektmapp) fungerar inte målanpassning som det ska.

1. **Konfigurerar butikssegmentering**

   1. Navigera till **Konfiguration för ContentHub Store** och skapa en annan butikskonfiguration i AEM Screens-konfigurationsbehållaren och ange **Title** som **segmentation-contexthub**, **Store Name** som **segmentation** och **Store Type** som **aem.segmentation**.

      ![bild](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Klicka på **Nästa** och sedan på **Spara**.

      >[!NOTE]
      >Hoppa över processen att definiera json och lämna den tom.


## Steg 3: Konfigurera segment i målgruppen {#setting-up-audience}

1. **Skapa segment i publiker**

   1. Navigera från AEM till **Personalization** > **Publiker** > **skärmar**.

   1. Klicka på **Skapa** > **Skapa ContextHub-segment.** Dialogrutan **Nytt ContextHub-segment** öppnas.

   1. Ange **Titel** som `**Higherthan50**` och klicka på **Skapa**. Skapa på samma sätt ett annat segment med namnet `**Lowerthan50**`.

      ![bild](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Klicka på segmentet `**Higherthan50**` och klicka på **Egenskaper** i åtgärdsfältet.

      ![bild](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Klicka på fliken **Personalization** i **Segmentegenskaper**. Ange **ContextHub Path** till `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` och **Segments Path** till `/conf/screens/settings/wcm/segments` och klicka på **Save**, som bilden nedan visar.

   ![bild](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Ange på liknande sätt även **ContextHub Path** och **Segments Path** för `**Lowerthan50**` -segmentet.

## Steg 4: Konfigurera varumärke och område {#setting-brand-area}

Följ stegen nedan för att skapa ett varumärke i era aktiviteter och områden under varumärket:

1. **Skapa ett varumärke i aktiviteter**

   1. Navigera från din AEM till **Personalization** > **Aktiviteter**.

   1. Klicka på **Skapa** > **Skapa varumärke**.

   1. Klicka på **Varumärke** i guiden **Skapa sida** och klicka på **Nästa**.

   1. Ange **Title** som **ScreensBrand** och klicka på **Create**. Ditt varumärke har nu skapats enligt nedan.

      ![bild](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Känt fel:
      >Om du vill lägga till ett område tar du bort det primära området från URL:en, till exempel
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Skapa ett område i varumärket**

   Följ stegen nedan för att skapa ett område i varumärket:

   1. Klicka på **Skapa** och sedan på **Skapa område**.

      ![bild](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Klicka på **Område** i guiden **Skapa sida** och klicka på **Nästa**.

   1. Ange **Title** som **ScreensValue** och klicka på **Create**.
Ett område skapas i ert varumärke.

## Steg 5: Skapa segmenten i en aktivitet {#step-setting-up-audience-segmentation}

När du har konfigurerat ett datalager och definierat din aktivitet (varumärke och område) följer du stegen nedan för att skapa segment i din aktivitet.

1. **Skapar segment i aktiviteter**

   1. Navigera från AEM till **Personalization** > **Activity** > **ScreensBrand** >**ScreensValue**.

   1. Klicka på **Skapa** > **Skapa aktivitet.** **Guiden Konfigurera aktivitet** öppnas.

   1. Ange **Title** som **ValueCheck50** och **Name** som **valueCheck50**. Klicka på **målmotorn** som **ContextHub (AEM)** i listrutan och klicka på **Nästa**.

      ![bild](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Klicka på **Lägg till upplevelse** i guiden `**Configure Activity**`.

   1. Klicka på `**Higherthan50**` i **Publikerna** och klicka på **Lägg till upplevelse** och ange **Rubrik** som `**higherthan50**` **Namn** som `**higherthan50**`. Klicka på **OK**.

   1. Klicka på `**Lowerthan50**` i **Publikerna** och klicka på **Lägg till upplevelse** och ange **Rubrik** som `**lowerthan50**` **Namn** som `**lowerthan50**`. Klicka på **OK**.

   ![bild](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Klicka på **Nästa** och sedan på **Spara**. Aktiviteten `**ValueCheck50**` har nu skapats och konfigurerats.

      ![bild](/help/user-guide/assets/context-hub/context-hub16.png)

## Steg 5: Redigera segment i publiker{#editing-audience-segmentation}

1. **Redigera segmenten**

   1. Navigera från AEM till **Personalization** > **Publiker** > **skärmar**.

   1. Klicka på segmentet `**Higherthan50**` och klicka på **Redigera** i åtgärdsfältet.

   1. Dra och släpp komponenten **Comparison: Property - Value** till redigeraren.

   1. Klicka på skiftnyckelsikonen så att du kan öppna dialogrutan **Jämföra en egenskap med värdet** .

   1. Klicka på **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**.

      >[!NOTE]
      > **Googlesheets/value/1/0** refererar till rad 2 och kolumn som fylls i i `google` ark i figuren nedan:

      ![bild](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Klicka på **Operator** som **större än** i listrutan.

   1. Ange **Value** som **70**.

      >[!NOTE]
      >
      >AEM validerar data från Google Sheet genom att visa segmentet som grönt.

      ![bild](/help/user-guide/assets/context-hub/context-hub18.png)

   Redigera egenskapsvärdena till `**Lowerthan50**` på samma sätt.

   1. Dra och släpp komponenten **Comparison: Property - Value** till redigeraren.

   1. Klicka på skiftnyckelsikonen.

   1. I dialogrutan **Jämför en egenskap med värdet** klickar du på **googlesheets/value/1/0** i listrutan i **Egenskapsnamn**.

   1. Klicka på **Operator** som **mindre än** i listrutan.

   1. Ange **Value** som **50**.


## Aktivera mål i kanaler {#step-enabling-targeting-in-channels}

Följ stegen nedan för att aktivera målinriktning i dina kanaler.

1. Navigera till någon av AEM Screens-kanalerna. I följande steg visas hur du aktiverar mål genom att använda **DataDrivenChannel** som skapats i en AEM Screens-kanal.

1. Klicka på kanalen **TargetChannel** och klicka på **Egenskaper** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/context-hub/context-hub19.png)

1. Klicka på fliken **Personalization** så att du kan konfigurera ContextHub-konfigurationer.

   1. Ange **ContextHub Path** till `/conf/screens/settings/wcm/segments` och **Segments Path** till `/conf/screens/settings/wcm/segments`.
   1. Ange **ScreensBrand** i listrutan och **Ange områdesreferens** till **ScreensValue**.

   1. Klicka på **Spara och stäng**.

      >[!NOTE]
      >
      >Använd ContextHub och Segments-sökvägen, där du först sparade dina ContextHub-konfigurationer och segment.

      ![bild](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Navigera och klicka på kanalen **TargetChannel** och klicka på **Redigera** i åtgärdsfältet.

      >[!NOTE]
      >
      >Om du har konfigurerat allt korrekt visas alternativet **Mål** i listrutan från redigeraren, vilket visas i bilden nedan.

      ![bild](/help/user-guide/assets/context-hub/context-hub21.png)

## Läs mer: Exempel på användningsfall {#learn-more-example-use-cases}

När du har konfigurerat ContextHub för ditt AEM Screens-projekt kan du följa de olika användningsexemplen för att förstå hur datautlösande resurser spelar en viktig roll i olika branscher:

1. **[Målinställd aktivering för butikslager](retail-inventory-activation.md)**
1. **[Temperaturaktivering i resecentret](local-temperature-activation.md)**
1. **[Aktivering av hotell- och reservation](hospitality-reservation-activation.md)**
