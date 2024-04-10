---
title: ContextHub konfigureras i AEM Screens
description: Lär dig mer om ContextHub i målmotorn så att du kan definiera datalagring för innehållsändring i utlösare.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '1452'
ht-degree: 1%

---

# ContextHub konfigureras i AEM Screens {#configuring-contexthub-in-aem-screens}

I det här avsnittet betonas hur du skapar och hanterar datadrivna resursändringar med hjälp av ett datalager.

## Nyckeltermer {#key-terms}

Innan du får mer information om hur du skapar och hanterar lagerdrivna kanaler i ditt AEM Screens-projekt bör du lära dig några av nyckeltermerna till de olika scenarierna.

**Varumärke** - Din projektbeskrivning på hög nivå.

**Område** - Ditt projektnamn för AEM Screens, till exempel Digital Ad Signage

**Aktivitet** - Definierar kategoriregler som Inventory-Driven, Weather-Driven eller Department Availability-Driven.

**Målgrupp** - Definierar regeln.

**Segment** - Den version av resursen som ska spelas upp för den angivna regeln. Om temperaturen till exempel är under 50 grader Fahrenheit visar skärmen en bild av en varm dryck, i annat fall en kall dryck.

I följande diagram visas hur ContextHub-konfigurationer sammanfaller med Activity, Audience och Channels.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Förhandsvillkor {#preconditions}

Innan du börjar konfigurera Context Hub-konfigurationer för ett AEM Screens-projekt måste du konfigurera Google Sheets (i demonstrationssyfte).

>[!IMPORTANT]
>
>Google Sheets används i följande exempel som ett exempeldatabassystem från vilket värdena hämtas och endast är avsett för utbildningsändamål. Adobe stöder inte användning av Google Sheets för produktionsmiljöer.
>
>Mer information finns i [Hämta API-nyckel](https://developers.google.com/maps/documentation/javascript/get-api-key) i Google-dokumentationen.

## Steg 1: Konfigurera ett datalager {#step-setting-up-a-data-store}

Du kan konfigurera datalagret som en lokal I/O-händelse eller som en lokal databashändelse.

Följande datanivådata utlöser ett exempel på en lokal databashändelse som ställer in ett datalager, t.ex. ett Excel-blad, där du kan använda ContextHub-konfigurationer och segmentsökvägar till AEM Screens-kanalen.

När du har konfigurerat `google` korrekt kalkylblad, vilket visas i exemplet nedan:

![bild](/help/user-guide/assets/context-hub/context-hub1.png)

Följande validering är den du ser när du kontrollerar anslutningen genom att ange de två värdena: `*google sheet ID*` och `*API key*` i följande format:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![bild](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>I det specifika exemplet nedan visas Google Sheets som ett datalager som utlöser en resursändring om värdet är högre än 100 eller lägre än 50.

## Steg 2: Konfigurera butikskonfigurationer {#step-setting-store-configurations}

1. **Navigera till ContextHub**

   Navigera till din AEM och klicka på verktygsikonen från vänster sidofält. Klicka **Webbplatser** > **ContextHub**, vilket visas i figuren nedan.

   ![bild](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Skapa en ContextHub Store-konfiguration**

   1. Navigera till konfigurationsbehållaren med namnet som **skärmar**.

   1. Välj **Skapa** > **Skapa konfigurationsbehållare** och ange titeln som **ContextHubDemo**.

      ![bild](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Navigera** till **ContextHubDemo** > **Skapa** **Konfiguration av ContentHub** och klicka **Spara**.

      >[!NOTE]
      > När du har valt **Spara** finns du i **KontextHub-konfiguration** skärm.

   1. Från **KontextHub-konfiguration** skärm, välja **Skapa** > **Konfiguration av ContentHub Store**

   ![bild](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >Som en del av AEM 6.5 Feature Pack 4 eller AEM 6.4 Feature Pack 8 bör man uppdatera `/conf/screens/settings/cloudsettings` till `sling:Folder`.
   >
   >Följ stegen nedan:
   >
   >1. Navigera till CRXDE Lite och sedan till `/conf/screens/settings/cloudsettings`.
   >1. Kontrollera om `cloudsettings jcr:primaryType` är i `sling:Folder`. Om `jcr:primaryType` är inte i `sling:folder`fortsätter du till nästa steg.
   >1. Högerklicka `/conf/screens/settings` och skapa en nod med *name* as **molninställningar1** och *Typ* as **sling:mapp** och spara ändringarna.
   >1. Flytta alla noder under `/conf/screens/settings/cloudsettings` till `cloudsettings1`.
   >1. Ta bort `cloudsettings` och spara.
   >1. Byt namn `cloudsettings1` till `cloudsettings` och spara.
   >1. Observera att `/conf/screens/settings/cloudsettings` har `jcr:primaryType` as `sling:Folder`.
   >
   >Följ de här stegen i Författare och Publicera före eller efter uppgraderingen.

   1. Ange **Titel** as **Google Sheets**, **Butiksnamn** as **googlesheet** och **Butikstyp** as **contexthub.generic-jsonp** och klicka **Nästa**.

      >[!CAUTION]
      >Om du använder Adobe Experience Manager (AEM) 6.4 anger du **Konfigurationstitel** as **googlesheet** och **Butikstyp** as **contexthub.generic-jsonp**.

      ![bild](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Ange din specifika json-konfiguration. Du kan till exempel använda följande json för demoändamål och välja **Spara**. Du ser butikskonfigurationen som **Google Sheets** i ContextHub-konfigurationen.

      >[!IMPORTANT]
      >Se till att ersätta koden med `*<Sheet ID>*` och `*<API Key>*`, som du hämtade när du konfigurerade Google-bladen.

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
      >I ovanstående exempelkod **pollInterval** definierar den frekvens med vilken värdena uppdateras (i millisekunder).
      >
      >Ersätt koden med `*<Sheet ID>*` och `*<API Key>*`, som du hämtade när du konfigurerade Google-bladen.

      >[!CAUTION]
      >
      >Om du skapar dina Google Sheets-lagringskonfigurationer utanför den globala mappen (till exempel i din egen projektmapp) fungerar inte mål som det ska.

1. **Konfigurera butikssegmentering**

   1. Navigera till **Konfiguration av ContentHub Store** och skapa en annan butikskonfiguration i AEM Screens konfigurationsbehållare och ange **Titel** as **segmenteringssammanhang**, **Butiksnamn** as **segmentering** och **Butikstyp** as **aem.segmentation**.

      ![bild](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Klicka **Nästa** och sedan **Spara**.

      >[!NOTE]
      >Hoppa över processen att definiera json och lämna den tom.


## Steg 3: Konfigurera segment i målgruppen {#setting-up-audience}

1. **Skapa segment i målgrupper**

   1. Navigera från AEM till **Personalisering** > **Målgrupper** > **skärmar**.

   1. Klicka **Skapa** > **Skapa kontextnavsegment.** The **Nytt ContextHub-segment** öppnas.

   1. Ange **Titel** as `**Higherthan50**` och klicka **Skapa**. Skapa på samma sätt ett annat segment med namnet som `**Lowerthan50**`.

      ![bild](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Markera segmentet `**Higherthan50**` och klicka **Egenskaper** i åtgärdsfältet.
      ![bild](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Välj **Personalisering** -fliken från **Segmentegenskaper**. Ange **ContextHub-sökväg** till `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` och **Segmentsökväg** till `/conf/screens/settings/wcm/segments` och klicka **Spara**, vilket visas i figuren nedan.

   ![bild](/help/user-guide/assets/context-hub/context-hub13.png)

   1. På samma sätt anger du **ContextHub-sökväg** och **Segmentsökväg** for `**Lowerthan50**` segmentera också.

## Steg 4: Konfigurera varumärke och område {#setting-brand-area}

Följ stegen nedan för att skapa ett varumärke i era aktiviteter och områden under varumärket:

1. **Skapa ett varumärke i aktiviteter**

   1. Navigera från AEM till **Personalisering** > **Verksamhet**.

   1. Välj **Skapa** > **Skapa varumärke**.

   1. Välj **Varumärke** från **Skapa sida** guide och klicka **Nästa**.

   1. Ange **Titel** as **Skärmmärke** och klicka **Skapa**. Ditt varumärke har nu skapats enligt nedan.

      ![bild](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Känt fel:
      >Om du vill lägga till ett område tar du bort det primära området från URL:en, till exempel
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Skapa ett område i ditt varumärke**

   Följ stegen nedan för att skapa ett område i varumärket:

   1. Välj **Skapa** och sedan **Skapa område**.

      ![bild](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Välj **Område** från **Skapa sida** guide och välj **Nästa**.

   1. Ange **Titel** as **ScreensValue** och markera **Skapa**.
Ett område skapas i ert varumärke.

## Steg 5: Skapa segmenten i en aktivitet {#step-setting-up-audience-segmentation}

När du har konfigurerat ett datalager och definierat din aktivitet (varumärke och område) följer du stegen nedan för att skapa segment i din aktivitet.

1. **Skapa segment i aktiviteter**

   1. Navigera från AEM till **Personalisering** > **Verksamhet** > **Skärmmärke** >**ScreensValue**.

   1. Välj **Skapa** > **Skapa aktivitet.** The **Guiden Konfigurera aktivitet** öppnas.

   1. Ange **Titel** as **ValueCheck50** och **Namn** as **valuecheck50**. Välj **Målmotor** as **ContextHub (AEM)** i listrutan och välj **Nästa**.

      ![bild](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Välj **Lägg till upplevelse** från `**Configure Activity**` guide.

   1. Från **Målgrupper** väljer du `**Higherthan50**` och markera **Lägg till upplevelse** och anger **Titel** as `**higherthan50**` **Namn** as `**higherthan50**`. Välj **OK**.

   1. Från **Målgrupper** väljer du `**Lowerthan50**` och markera **Lägg till upplevelse** och anger **Titel** as `**lowerthan50**` **Namn** as `**lowerthan50**`. Välj **OK**.

   ![bild](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Välj **Nästa** och sedan **Spara**. `**ValueCheck50**` aktiviteten har nu skapats och konfigurerats.

      ![bild](/help/user-guide/assets/context-hub/context-hub16.png)

## Steg 5: Redigera segment i publiker{#editing-audience-segmentation}

1. **Redigera segmenten**

   1. Navigera från AEM till **Personalisering** > **Målgrupper** > **skärmar**.

   1. Markera segmentet `**Higherthan50**`och markera **Redigera** i åtgärdsfältet.

   1. Dra och släpp **Jämförelse: Egenskap - värde** till redigeraren.

   1. Klicka på skiftnyckelsikonen så att du kan öppna **Jämföra en egenskap med ett värde** -dialogrutan.

   1. Välj **googlesheets/value/1/0** från listrutan i **Egenskapsnamn**.

      >[!NOTE]
      > The **googlesheets/value/1/0** refererar till rad 2 och kolumn som är ifylld i `google` ark i figuren nedan:

      ![bild](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Välj **Operator** as **större än** i listrutan.

   1. Ange **Värde** as **70**.

      >[!NOTE]
      >
      >AEM validerar data från Google Sheet genom att visa segmentet som grönt.

      ![bild](/help/user-guide/assets/context-hub/context-hub18.png)

   Redigera på samma sätt egenskapsvärdena till `**Lowerthan50**`.

   1. Dra och släpp **Jämförelse: Egenskap - värde** till redigeraren.

   1. Välj skiftnyckelsikonen.

   1. I **Jämföra en egenskap med ett värde** väljer **googlesheets/value/1/0** från listrutan i **Egenskapsnamn**.

   1. Välj **Operator** as **mindre än** i listrutan.

   1. Ange **Värde** as **50**.


## Aktivera mål i kanaler {#step-enabling-targeting-in-channels}

Följ stegen nedan för att aktivera målinriktning i dina kanaler.

1. Navigera till någon av AEM Screens-kanalerna. I följande steg visas hur du aktiverar målinriktning genom att använda **DataDrivenKanal** som har skapats i en AEM Screens-kanal.

1. Välj kanalen **TargetChannel** och klicka **Egenskaper** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/context-hub/context-hub19.png)

1. Välj **Personalisering** så att du kan konfigurera ContextHub-konfigurationer.

   1. Ange **ContextHub-sökväg** till `/conf/screens/settings/wcm/segments` och **Segmentsökväg** till `/conf/screens/settings/wcm/segments`.
   1. Ställ in varumärket till **Skärmmärke** från listrutan och **Ange områdesreferens** till **ScreensValue**.

   1. Klicka **Spara och stäng**.

      >[!NOTE]
      >
      >Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

      ![bild](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Navigera och markera **TargetChannel** och klicka på **Redigera** i åtgärdsfältet.

      >[!NOTE]
      >
      >Om du har konfigurerat allt korrekt visas **Målinriktning** i listrutan i redigeraren, vilket visas i bilden nedan.

      ![bild](/help/user-guide/assets/context-hub/context-hub21.png)

## Läs mer: Exempel på användningsfall {#learn-more-example-use-cases}

När du har konfigurerat ContextHub för ditt AEM Screens-projekt kan du följa de olika användningsexemplen för att förstå hur datautlösande resurser spelar en viktig roll i olika branscher:

1. **[Målinställd aktivering för butikslager](retail-inventory-activation.md)**
1. **[Temperaturaktivering i resecentret](local-temperature-activation.md)**
1. **[Aktivering av hotellreservation](hospitality-reservation-activation.md)**
