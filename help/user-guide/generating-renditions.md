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
source-git-commit: 97084aee861e152abcc5f117a2a4759dced038cc
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Videoåtergivningar {#video-renditions}

Du kan generera manuella och automatiska Full HD-renderingar. I följande avsnitt beskrivs arbetsflödet för att lägga till återgivningar i dina resurser.

## Generera återgivningar med full HD automatiskt  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Om AEM Screens videoåtergivningar inte spelas upp optimalt på din enhet kontaktar du maskinvaruleverantören för specifikationerna för videon. Detta hjälper till att få bästa prestanda på enheten och skapar därför en egen anpassad videoprofil där du anger lämpliga parametrar för att FFMPEG ska kunna generera din återgivning. Använd sedan stegen nedan för att lägga till din anpassade videoprofil i listan med profiler.
>
>Se även [Felsöka videoklipp](troubleshoot-videos.md) för att felsöka och felsöka videouppspelning i din kanal.

Följ stegen nedan för att automatiskt generera fullständiga HD-renderingar:

1. Markera länken Adobe Experience Manager (överst till vänster) och klicka på hammarikonen så att du kan välja **Arbetsflöde**.

   Klicka **Models**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. I arbetsflödesmodellhanteringen väljer du **DAM-uppdateringsresurs** modell och klicka **Redigera** i åtgärdsfältet.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. I **DAM-uppdateringsresurs** fönster, dubbelklicka på **FFmpeg-omkodning** steg.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Välj **Process** -fliken.
1. Ange de fullständiga HD-profilerna i listan **Argument** som följande:
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Klicka **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Klicka **Spara** längst upp till vänster i **DAM-uppdateringsresurs** skärm.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Navigera till **Resurser** och ladda upp en ny video. Klicka på videon och öppna sidolisten Återgivningar. Lägg märke till de två HD-videorna.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Öppna **Återgivningar** från sidospåret.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Lägg märke till två nya fullständiga HD-renderingar.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generera fullständiga HD-återgivningar manuellt {#manually-generating-full-hd-renditions}

Följ stegen nedan om du vill generera fullständiga HD-renderingar manuellt:

1. Markera länken Adobe Experience Manager (längst upp till vänster) och klicka på hammarikonen så att du kan välja verktyg och välja **Arbetsflöde**.

   Klicka **Models**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. I arbetsflödesmodellhantering väljer du **Skärmar - uppdatera resurs** och klicka på **Starta arbetsflöde** för att öppna **Kör arbetsflöde** -dialogrutan.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Välj önskad video i **Nyttolast** och klicka **Kör**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Navigera till **Resurser**, gå ned till resursen och klicka på den.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Öppna **Återgivningar** sidospår. Lägg märke till de nya renderingarna med full HD.

   ![step8_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
