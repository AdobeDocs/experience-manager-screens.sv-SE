---
title: Videoåtergivningar
description: Lär dig hur du skapar fullständiga HD-renderingar för ditt AEM Screens-projekt.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Videoåtergivningar {#video-renditions}

Du kan generera manuella och automatiska HD-renderingar. I följande avsnitt beskrivs arbetsflödet för att lägga till återgivningar i dina resurser.

## Generera återgivningar med full HD automatiskt {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Om AEM Screens videoåtergivningar inte spelas upp optimalt på din enhet kontaktar du maskinvaruleverantören för specifikationerna för videon. Det hjälper dig att få bästa prestanda på enheten. Det hjälper dig att skapa en egen anpassad videoprofil där du anger lämpliga parametrar för att FFMPEG ska kunna generera din återgivning. Använd sedan stegen nedan för att lägga till din anpassade videoprofil i listan med profiler.
>
>Se även [Felsöka videoklipp](troubleshoot-videos.md) för att felsöka och felsöka videouppspelning i din kanal.

Följ stegen nedan för att generera fullständiga HD-renderingar automatiskt:

1. Klicka på länken Adobe Experience Manager (överst till vänster) och klicka på hamsikonen så att du kan klicka på **Arbetsflöde**.

   Klicka på **Modeller**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Klicka på modellen **DAM Update Asset** i arbetsflödesmodellhanteringen och klicka på **Redigera** i åtgärdsfältet.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. I fönstret **DAM Update Asset** dubbelklickar du på **FFmpeg-omkodningssteget**.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Klicka på fliken **Process**.
1. Ange de fullständiga HD-profilerna i listan i **Arguments** enligt följande:
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Klicka på **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Klicka på **Spara** överst till vänster på skärmen **DAM-uppdatering**.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Navigera till **Assets** och överför en ny video. Klicka på videon och öppna sidolisten Återgivningar. Lägg märke till de två HD-videorna.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Öppna **Återgivningar** från sidospåret.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Lägg märke till två nya fullständiga HD-renderingar.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generera fullständiga HD-återgivningar manuellt {#manually-generating-full-hd-renditions}

Följ stegen nedan för att generera fullständiga HD-renderingar manuellt:

1. Klicka på länken Adobe Experience Manager (överst till vänster) och klicka på hammikonen så att du kan klicka på verktyg och klicka på **Arbetsflöde**.

   Klicka på **Modeller**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Klicka på **Screens Update Asset**-modellen i arbetsflödesmodellhantering och klicka sedan på **Starta arbetsflöde** för att öppna dialogrutan **Kör arbetsflöde**.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Klicka på önskad video i **nyttolasten** och klicka på **Kör**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Navigera till **Assets**, gå ned till resursen och klicka på den.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Öppna sidospåret **Återgivningar**. Lägg märke till de nya renderingarna med full HD.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
