---
title: Varaktighet för bilduppspelning
seo-title: Varaktighet för bilduppspelning
description: Följ den här sidan om du vill veta mer om hur lång uppspelningen är.
seo-description: Följ den här sidan om du vill veta mer om hur lång uppspelningen är.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 1%

---


# Varaktighet för bilduppspelning {#image-playback-duration}

## Översikt {#overview}

När du har skapat en sekvenskanal och lagt till bilder i den får alla bilder som standard den uppspelningstid som definieras i konfigurationen på kanalnivå. Alla enskilda bilder kan fortfarande åsidosätta standardvärdet och ha en annan uppspelningstid. Detta uppnås genom att du redigerar uppspelningstiden för den specifika bildkomponenten.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen måste du se till att du har konfigurerat ett projekt som en förutsättning för att du ska kunna börja implementera den här funktionen. Till exempel,

1. Skapa ett AEM Screens-projekt (i det här exemplet **ChannelLevelPlayback**)

1. Skapa en sekvenskanal som **PlaybackChannel** under **Kanaler**-mapp

1. Lägg till innehåll i **PlaybackChannel**

## Redigera bilduppspelningens varaktighet på kanalnivå {#editing-channel-level-image-playback-duration-assignment}

I avsnittet nedan beskrivs hur du redigerar uppspelningstiden för innehåll i en AEM Screens-kanal.

### Uppdatera uppspelningstiden för bilder i en kanal {#updating-the-playback-duration-for-images-in-a-channel}

Följ stegen nedan för att lära dig hur du uppdaterar tilldelning för bildspelets varaktighet på kanalnivå:

1. Navigera till sekvenskanalen **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Lägg till två eller flera bilder i kanalredigeraren, enligt bilden nedan.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Markera alla bilder i kanalen och klicka på skiftnyckelsikonen i det övre vänstra hörnet (som visas i bilden nedan) för att öppna dialogrutan Konfigurera på kanalnivå.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Dialogrutan** Sidor öppnas.

   >[!NOTE]
   >
   >Som standard är bilderna i en kanal inställda på 8 sekunders uppspelningstid.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Redigera **Varaktighet** från 8 000 (ms) till 3 000 (ms), d.v.s. 3 sekunder. Klicka på bockmarkeringen längst upp till höger i dialogrutan **Sida** för att spara ändringarna.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visa resultatet {#viewing-the-result}

När du har uppdaterat kanalens uppspelningstid (i det här exemplet alla tre bilderna) kommer du att märka att bilderna nu spelas upp i 3 sekunder i stället för 8 sekunder (standardvärde).

![channel_preview](assets/channel_preview.gif)

