---
title: Skapa ett arbetsflöde för videoutfyllnad
seo-title: Skapa ett arbetsflöde för videoutfyllnad
description: Följ den här sidan om du vill veta mer om hur du skapar en videoutfyllnad i arbetsflödet för dina resurser.
seo-description: Följ den här sidan om du vill veta mer om hur du skapar en videoutfyllnad i arbetsflödet för dina resurser.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Skapa ett arbetsflöde för videoutfyllnad {#creating-a-video-padding-workflow}

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Förutsättningar**
* **Skapa ett arbetsflöde för videoutfyllnad**
   * **Skapa ett arbetsflöde**
   * **Använda arbetsflödet i AEM-skärmsprojekt**

* **Validera arbetsflödets utdata**

## Översikt {#overview}

I följande exempel används montering av en video (exempel: 1 280 x 720) i en kanal där skärmen är 1 920 x 1 080 och där videon ska placeras på 0x0 (övre vänstra). Videon ska inte sträckas ut eller ändras på något sätt och inte användas för **omslag** i videokomponenten.

Videon visas som ett objekt från pixel 1 till pixel 1280 över och från pixel 1 till pixel 720 ned och resten av kanalen blir standardfärg.

## Förutsättningar {#prerequisites}

Innan du skapar ett arbetsflöde för video måste du uppfylla följande krav:

1. Överför en video i **resursmappen** i din AEM-instans
1. Skapa ett AEM Screens-projekt (till exempel **TestVideoRendition**) och en kanal med namnet (**VideoRendering**) enligt bilden nedan:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Skapa ett arbetsflöde för videoutfyllnad {#creating-a-video-padding-workflow-1}

Om du vill skapa ett arbetsflöde för videoutfyllnad måste du skapa ett arbetsflöde för videon och sedan använda samma arbetsflöde i projektkanalen för AEM Screens.

Följ stegen nedan för att skapa och använda arbetsflödet:

1. Skapa ett arbetsflöde
1. Använda arbetsflödet i ett AEM-skärmsprojekt

### Skapa ett arbetsflöde {#creating-a-workflow}

Följ stegen nedan för att skapa ett arbetsflöde för videon:

1. Navigera till din AEM-instans och klicka på verktyg från sidospåret. Välj **Arbetsflöde** —> **Modeller** för att skapa en ny modell.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Klicka på **Models** —> **Create** —> **Create Model**. Ange **Titel** (som **VideoRendition**) och **Namn** i **Lägg till arbetsflödesmodell**. Klicka på **Klar** för att lägga till arbetsflödesmodellen.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. När du har skapat arbetsflödesmodellen markerar du modellen (**VideoRendition**) och klickar på **Redigera** i åtgärdsfältet.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Dra och släpp **Command Line **-komponenten i ditt arbetsflöde.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Markera **kommandoradskomponenten** och öppna dialogrutan Egenskaper.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Klicka på fliken **Argument** för att ange fälten i dialogrutan **Kommandorad - Stegegenskaper** .

   Ange formatet i **Mime Types** (som ***video/mp4***) och kommandot som (**/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.video fullhd-hp.mp4***) för att starta arbetsflödet i fältet **Kommandon** .

   Se informationen om **Mime Types** och **Commands** i nedanstående kommentar.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Markera arbetsflödet (**VideoRenditions**) och klicka på **Starta arbetsflöde** i åtgärdsfältet för att öppna dialogrutan **Kör arbetsflöde** .

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Välj sökvägen till resursen i **nyttolasten** (som ***/content/dam/huseinpeyda-crossroad01_512kb 2.mp4***) och ange **Title **(as ***RunVideo***) och klicka på **Run**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Använda arbetsflödet i ett AEM-skärmsprojekt {#using-the-workflow-in-an-aem-screens-project}

Följ stegen nedan för att använda arbetsflödet i ditt AEM Screens-projekt:

1. Navigera till ett AEM-skärmsprojekt (**TestVideoRendition** —> **Kanaler** —>**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Klicka på **Redigera** i åtgärdsfältet. Dra och släpp videon som du ursprungligen överförde till **Assets**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. När du har överfört videon klickar du på **Förhandsgranska** för att visa utdata.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validera arbetsflödets utdata {#validating-the-output-for-the-workflow}

Du kan validera dina utdata genom att:

* Kontrollera förhandsgranskning av videon i kanalen
* Gå till ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** i CRXDE Lite, som i bilden nedan:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
