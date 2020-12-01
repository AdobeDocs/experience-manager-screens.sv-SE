---
title: Uppspelningstid för bild på projektnivå
seo-title: Uppspelningstid för bild på projektnivå
description: 'Med den här funktionen kan du definiera längden för bilduppspelningen på projektnivå. '
seo-description: 'Med den här funktionen kan du definiera längden för bilduppspelningen på projektnivå. '
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---


# Uppspelningstid för bild på projektnivå {#project-level-image-playback}

## Översikt {#overview}

Med den här funktionen kan du definiera längden för bilduppspelningen på projektnivå. Alla bilder ärver den här uppspelningstiden som standard. Om ingen varaktighet definieras på projektnivå fortsätter standarduppspelningen på 8 sekunder.

### Förutsättningar {#prerequisites}

Innan du använder den här funktionen måste du konfigurera ett projekt som en förutsättning för att du ska kunna börja implementera den här funktionen. Till exempel,

1. Skapa ett AEM Screens-projekt (i det här exemplet **ProjectLevelPlayback**)

1. Skapa en sekvenskanal som **PlayBackChannel** under **Kanaler**-mapp

1. Lägg till innehåll i **PlayBackChannel**

   ![resurser](assets/image_playback1.png)

   I följande bild visas de bilder som har lagts till i redigeraren **PlayBackChannel**:

   ![resurser](assets/image_playback2.png)

## Redigera bilduppspelningens varaktighet på projektnivå {#editing-project-level-image-playback-duration-assignment}

I avsnittet nedan beskrivs hur du redigerar uppspelningstiden för innehåll i ett AEM Screens-projekt.

### Uppdatera uppspelningstiden för bilder på projektnivå {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Om du vill uppdatera uppspelningstiden på bild- eller kanalnivå läser du [Bilduppspelningstid på kanalnivå](channel-level-image-playback.md).

Följ stegen nedan för att lära dig hur du uppdaterar bilduppspelningstiden på projektnivå:

1. Navigera till ditt projekt **ProjectLevelPlayback** och klicka på **Egenskaper** i åtgärdsfältet.
   ![resurser](assets/image_playback3.png)

1. Markera alla bilder i kanalen och klicka på skiftnyckelsikonen i det övre vänstra hörnet (som visas i bilden nedan) för att öppna dialogrutan Konfigurera på kanalnivå.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Dialogrutan** Sidor öppnas.

   >[!NOTE]
   >
   >Som standard är bilderna i en kanal inställda på 8 sekunders uppspelningstid och videoklippen spelas upp med standardlängden.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Redigera **Varaktighet** från 8 000 (ms) till 3 000 (ms), d.v.s. 3 sekunder. Klicka på bockmarkeringen längst upp till höger i dialogrutan **Sida** för att spara ändringarna.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visa resultatet {#viewing-the-result}

När du har uppdaterat kanalens uppspelningstid (i det här exemplet alla tre bilderna) kommer du att märka att bilderna nu spelas upp i 3 sekunder i stället för 8 sekunder (standardvärde).

![channel_preview](assets/channel_preview.gif)

