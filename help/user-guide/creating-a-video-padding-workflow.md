---
title: Skapa ett arbetsflöde för videoutfyllnad
description: Lär dig mer om hur du skapar en videoutfyllnad i arbetsflödet för dina resurser.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Skapa ett arbetsflöde för videoutfyllnad {#creating-a-video-padding-workflow}

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Förutsättningar**
* **Skapa ett arbetsflöde för videoutfyllnad**
   * **Skapa ett arbetsflöde**
   * **Använda arbetsflödet i AEM Screens Project**

* **Verifierar arbetsflödets utdata**

## Ökning {#overview}

I följande exempel placeras en video (exempel: 1 280 x 720) i en kanal där skärmen är 1 920 x 1 080 och där videon är placerad på 0x0 (övre vänstra). Videon får inte sträckas ut eller ändras på något sätt och **Cover** ska inte användas i videokomponenten.

Videon visas som ett objekt från pixel 1 till pixel 1280 över och från pixel 1 till pixel 720 ned. Resten av kanalen är standardfärgen.

## Förutsättningar {#prerequisites}

Innan du skapar ett arbetsflöde för video ska du uppfylla följande krav:

1. Överför en video i mappen **Assets** i din AEM
1. Skapa ett AEM Screens-projekt (till exempel **TestVideoRendition**) och en kanal med namnet (**VideoRendering**), vilket visas i bilden nedan:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Skapa ett arbetsflöde för videoutfyllnad {#creating-a-video-padding-workflow-1}

Om du vill skapa ett arbetsflöde för videoutfyllnad skapar du ett arbetsflöde för videon och använder sedan samma arbetsflöde i din AEM Screens-projektkanal.

Följ stegen nedan för att skapa och använda arbetsflödet:

1. Skapa ett arbetsflöde
1. Använda arbetsflödet i ett AEM Screens-projekt

### Skapa ett arbetsflöde {#creating-a-workflow}

Följ stegen nedan för att skapa ett arbetsflöde för videon:

1. Navigera till AEM.
1. Klicka på verktygen från sidolisten.
1. Klicka på **Arbetsflöde** > **Modeller** så att du kan skapa en modell.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Klicka på **Modeller** > **Skapa** > **Skapa modell**. Ange **Title** (till exempel **VideoRendition**) och **Name** i **Add Workflow Model**. Klicka på **Klar** för att lägga till arbetsflödesmodellen.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. När du har skapat arbetsflödesmodellen klickar du på modellen (**VideoRendition**) och sedan på **Redigera** i åtgärdsfältet.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Dra och släpp **`Command Line`**-komponenten i arbetsflödet.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Klicka på komponenten **`Command Line`** och öppna dialogrutan för egenskaper.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Klicka på fliken **Argument**.
1. I dialogrutan **Kommandorad - stegegenskaper** anger du formatet i **Mime Types** (som ***video/mp4***) och kommandot som (**/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4***). Det här kommandot startar arbetsflödet i fältet **Kommandon**.

   Mer information om **Mime Types** och **Commands** finns i anteckningen nedan.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Klicka på arbetsflödet (**VideoRenditions**).
1. Klicka på **Starta arbetsflöde** i åtgärdsfältet.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. I dialogrutan **Kör arbetsflöde** klickar du på resursens sökväg i **Nyttolast** (som ***/content/dam/holyda-crossroad01_512kb 2.mp4***) och anger **Title** som ***RunVideo*** och klickar på **Run** .

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Använda arbetsflödet i ett AEM Screens-projekt {#using-the-workflow-in-an-aem-screens-project}

Följ stegen nedan för att använda arbetsflödet i ditt AEM Screens-projekt:

1. Navigera till ett AEM Screens-projekt (**TestVideoRendition** > **Kanaler** >**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Klicka på **Redigera** i åtgärdsfältet. Dra och släpp videon som du ursprungligen överförde till **Assets**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. När du har överfört videon klickar du på **Förhandsgranska** för att visa utdata.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validera arbetsflödets utdata {#validating-the-output-for-the-workflow}

Du kan validera dina utdata genom att:

* Kontrollera en förhandsgranskning av videon i kanalen
* Navigera till ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** i CRXDE Lite, enligt bilden nedan:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
