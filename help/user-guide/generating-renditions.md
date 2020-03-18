---
title: Videoåtergivningar
seo-title: Videoåtergivningar
description: Följ den här sidan om du vill veta mer om hur du skapar fullständiga HD-renderingar för ditt skärmsprojekt.
seo-description: Följ den här sidan om du vill veta mer om hur du skapar fullständiga HD-renderingar för ditt skärmsprojekt.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Videoåtergivningar {#video-renditions}

Du kan generera manuella och automatiska Full HD-renderingar. I följande avsnitt beskrivs arbetsflödet för att lägga till återgivningar i dina resurser.

## Generera återgivningar med full HD automatiskt {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Om AEM Screen-videoåtergivningarna inte spelas upp optimalt på enheten kontaktar du maskinvaruleverantören för specifikationerna för videon. Detta hjälper till att få bästa prestanda på enheten och därmed skapa en egen anpassad videoprofil där du anger lämpliga parametrar för att FFMPEG ska kunna generera din återgivning. Använd sedan stegen nedan för att lägga till din anpassade videoprofil i listan med profiler.
>
>Se även [Felsöka videor](troubleshoot-videos.md) för att felsöka och felsöka videouppspelning i din kanal.

Följ stegen nedan för att automatiskt generera fullständiga HD-renderingar:

1. Välj länken Adobe Experience Manager (överst till vänster) och klicka på hammikonen för att välja verktyg för att välja **arbetsflöde**.

   Klicka på **Modeller** för att öppna hanteringen av arbetsflödesmodeller.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Välj **DAM Update Asset** -modellen och klicka på Redigera i åtgärdsfältet för att öppna fönstret **DAM Update Asset** .

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Dubbelklicka på **Fmpeg-omkodningssteget** .

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Klicka på fliken **Process** för att redigera processargumenten. Ange de fullständiga HD-profilerna i listan i **Arguments** som: ***,profile:fullhd-bp,profile:fullhd-hp*** och klicka på **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Klicka på **Spara** överst till vänster på skärmen **DAM-uppdatering** .

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Navigera till **Resurser** och ladda upp en ny video. Klicka på videon och öppna sidospåret Återgivningar så ser du de två HD-videofilmerna.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Öppna **återgivningar** från sidospåret.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Du kommer att märka två nya fullständiga HD-renderingar.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generera fullständiga HD-återgivningar manuellt {#manually-generating-full-hd-renditions}

Följ stegen nedan om du vill generera fullständiga HD-renderingar manuellt:

1. Välj länken Adobe Experience Manager (överst till vänster) och klicka på hammikonen för att välja verktyg för att välja **arbetsflöde**.

   Klicka på **Modeller** för att öppna hanteringen av arbetsflödesmodeller.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Välj **skärmuppdatering av resurs** och klicka på **Starta arbetsflöde** för att öppna dialogrutan **Kör arbetsflöde** .

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Markera önskad video i **nyttolasten** och klicka på **Kör**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Navigera till **Resurser**, gå ned till resursen och klicka på den.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Öppna sidospåret för **återgivningar** så ser du de nya återgivningarna i full HD.

   ![step8_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

