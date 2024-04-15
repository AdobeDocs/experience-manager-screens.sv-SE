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
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Skapa ett arbetsflöde för videoutfyllnad {#creating-a-video-padding-workflow}

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Förutsättningar**
* **Skapa ett arbetsflöde för videoutfyllnad**
   * **Skapa ett arbetsflöde**
   * **Använda arbetsflödet i AEM Screens Project**

* **Validera arbetsflödets utdata**

## Ökning {#overview}

I följande exempel placeras en video (exempel: 1 280 x 720) i en kanal där skärmen är 1 920 x 1 080 och där videon är placerad på 0x0 (övre vänstra). Videon får inte sträckas ut eller ändras på något sätt och får inte användas **Omslag** i videokomponenten.

Videon visas som ett objekt från pixel 1 till pixel 1280 över och från pixel 1 till pixel 720 ned och resten av kanalen är standardfärgen.

## Förutsättningar {#prerequisites}

Innan du skapar ett arbetsflöde för video ska du uppfylla följande krav:

1. Överföra en video i **Resurser** mapp i AEM
1. Skapa ett AEM Screens-projekt (till exempel **TestVideoRendition**) och en kanal med namnet (**VideoRendering**), vilket visas i figuren nedan:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Skapa ett arbetsflöde för videoutfyllnad {#creating-a-video-padding-workflow-1}

Om du vill skapa ett arbetsflöde för videoutfyllnad skapar du ett arbetsflöde för videon och använder sedan samma arbetsflöde i din AEM Screens-projektkanal.

Följ stegen nedan för att skapa och använda arbetsflödet:

1. Skapa ett arbetsflöde
1. Använda arbetsflödet i ett AEM Screens-projekt

### Skapa ett arbetsflöde {#creating-a-workflow}

Följ stegen nedan för att skapa ett arbetsflöde för videon:

1. Navigera till AEM.
1. Välj verktyg från sidospåret.
1. Välj **Arbetsflöde** > **Models** så att du kan skapa en modell.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Välj **Models** > **Skapa** > **Skapa modell**. Ange **Titel** (as **VideoRendition**) och **Namn** i **Lägg till arbetsflödesmodell**. Välj **Klar** för att lägga till arbetsflödesmodellen.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. När du har skapat arbetsflödesmodellen väljer du modellen (**VideoRendition**), och markera **Redigera** i åtgärdsfältet.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Dra och släpp **`Command Line`** till arbetsflödet.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Välj **`Command Line`** och öppna egenskapsdialogrutan.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Välj **Argument** -fliken.
1. I **Kommandorad - Stegegenskaper** anger du formatet i dialogrutan **Mime-typer** (as ***video/mp4***) och kommandot som (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4**). Det här kommandot startar arbetsflödet i **Kommandon** fält.

   Läs mer om **Mime-typer** och **Kommandon** i anmärkningen nedan.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Välj arbetsflöde (**VideoRenditions**).
1. Välj **Starta arbetsflöde** i åtgärdsfältet.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. I **Kör arbetsflöde** väljer du resursens sökväg i dialogrutan **Nyttolast** (as ***/content/dam/huseinpeyda-crossroad01_512kb 2.mp4***) och anger **Titel** as ***RunVideo*** och markera **Kör**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Använda arbetsflödet i ett AEM Screens-projekt {#using-the-workflow-in-an-aem-screens-project}

Följ stegen nedan för att använda arbetsflödet i ditt AEM Screens-projekt:

1. Navigera till ett AEM Screens-projekt (**TestVideoRendition** > **Kanaler** >**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Välj **Redigera** i åtgärdsfältet. Dra och släpp videon som du ursprungligen överförde till **Resurser**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. När du har överfört videon väljer du **Förhandsgranska** för att visa utdata.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validera arbetsflödets utdata {#validating-the-output-for-the-workflow}

Du kan validera dina utdata genom att:

* Kontrollera förhandsgranskning av videon i kanalen
* Navigera till ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** i CRXDE Lite, enligt bilden nedan:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
