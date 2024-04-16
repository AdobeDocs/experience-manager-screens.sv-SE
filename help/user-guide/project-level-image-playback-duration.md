---
title: Uppspelningstid för bild på projektnivå
description: Lär dig hur du definierar uppspelningstiden för bilder på projektnivå.
contentOwner: jsyal
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# Uppspelningstid för bild på projektnivå {#project-level-image-playback}

## Ökning {#overview}

Med den här funktionen kan du definiera längden för bilduppspelningen på projektnivå. Alla bilder ärver den här uppspelningstiden som standard. Om ingen varaktighet definieras på projektnivå fortsätter standarduppspelningen på 8 sekunder.

### Förutsättningar {#prerequisites}

Innan du använder den här funktionen måste du konfigurera ett projekt som en förutsättning för att du ska kunna börja implementera den här funktionen. Exempel:

1. Skapa ett AEM Screens-projekt (i det här exemplet **ProjektNivåUppspelning**).
1. Skapa en sekvenskanal som **PlayBackChannel** under **Kanaler** mapp.
1. Lägg till innehåll i **PlayBackChannel**.

   ![resurser](assets/image_playback1.png)

   I följande bild visas de bilder som lagts till i **PlayBackChannel** redigerare:

   ![resurser](assets/image_playback2.png)

## Redigera bilduppspelningens varaktighet på projektnivå {#editing-project-level-image-playback-duration-assignment}

I avsnittet nedan beskrivs hur du redigerar uppspelningstiden för innehåll i ett AEM Screens-projekt.

### Uppdatera uppspelningstiden för bilder på projektnivå {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Om du vill uppdatera uppspelningstiden på bild- eller kanalnivå läser du [Uppspelningstid för bild på kanalnivå](channel-level-image-playback.md).

Följ stegen nedan för att lära dig hur du uppdaterar bilduppspelningstiden på projektnivå:

1. Navigera till ditt projekt **ProjektNivåUppspelning** och klicka **Egenskaper** i åtgärdsfältet.
   ![resurser](assets/image_playback3.png)

1. Klicka på alla bilder i kanalen och klicka på skiftnyckelsikonen högst upp till vänster (som bilden nedan visar) så att du kan öppna dialogrutan Konfigurera kanalnivå.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. The **Sida** öppnas.

   >[!NOTE]
   >
   >Som standard är bilderna i en kanal inställda på 8 sekunders uppspelningstid och videoklippen spelas upp med standardlängden.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Redigera **Varaktighet** från 8 000 (millisekunder) till 3 000 (millisekunder), dvs. 3 sekunder. Markera bockmarkeringen längst upp till höger på sidan **Sida** så att ändringarna sparas.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visa resultatet {#viewing-the-result}

När du har uppdaterat kanalens uppspelningstid (i det här exemplet alla tre bilderna) kan du se att bilderna spelas upp i 3 sekunder i stället för 8 sekunder (standardvärde).

![channel_preview](assets/channel_preview.gif)

