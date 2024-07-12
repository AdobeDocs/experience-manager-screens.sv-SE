---
title: Varaktighet för bilduppspelning
description: Lär dig mer om hur länge bilderna spelas upp i AEM Screens.
contentOwner: jsyal
source-git-commit: 8a914d4b0237c327b7954c936c84a2c1aa719603
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Varaktighet för bilduppspelning {#image-playback-duration}

## Ökning {#overview}

När du har skapat en sekvenskanal och lagt till bilder i den får alla bilder som standard den uppspelningstid som definieras i konfigurationen på kanalnivå. Alla enskilda bilder kan fortfarande åsidosätta standardinställningen och ha en annan uppspelningstid. Detta uppnås genom att du redigerar uppspelningstiden för den specifika bildkomponenten.

### Förutsättningar {#prerequisites}

Innan du implementerar den här funktionen bör du kontrollera att du har konfigurerat ett projekt som en förutsättning för att börja implementera den här funktionen. Exempel:

1. Skapa ett AEM Screens-projekt (i det här exemplet **ChannelLevelPlayback**)
1. Skapa en sekvenskanal som **PlaybackChannel** under mappen **Kanaler**
1. Lägg till innehåll i **PlaybackChannel**

## Redigera bilduppspelningens varaktighet på kanalnivå {#editing-channel-level-image-playback-duration-assignment}

I avsnittet nedan beskrivs hur du redigerar uppspelningstiden för innehåll i en AEM Screens-kanal.

### Uppdatera uppspelningstiden för bilder i en kanal {#updating-the-playback-duration-for-images-in-a-channel}

Följ stegen nedan för att lära dig hur du uppdaterar tilldelning för bildspelets varaktighet på kanalnivå:

1. Navigera till sekvenskanalen **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Klicka på **Redigera** i åtgärdsfältet.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Lägg till två eller flera bilder i kanalredigeraren, enligt bilden nedan.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Klicka på alla bilder i kanalen och klicka på skiftnyckelsikonen i det övre vänstra hörnet (som bilden nedan visar). Dialogrutan Konfigurera på kanalnivå öppnas.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. Dialogrutan **Sida** öppnas.

   >[!NOTE]
   >
   >Som standard är bilderna i en kanal inställda på 8 sekunders uppspelningstid.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Redigera **Varaktighet** från 8 000 (millisekunder) till 3 000 (millisekunder), d.v.s. 3 sekunder. Klicka på bockmarkeringen högst upp till höger i dialogrutan **Sida** så att du kan spara ändringarna.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visa resultatet {#viewing-the-result}

När du har uppdaterat kanalens uppspelningstid (i det här exemplet alla tre bilderna) kan du se att bilderna spelas upp i 3 sekunder i stället för 8 sekunder (standardvärdet).

![channel_preview](assets/channel_preview.gif)

