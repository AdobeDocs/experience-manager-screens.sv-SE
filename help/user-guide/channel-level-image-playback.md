---
title: Varaktighet för massbildsuppspelning på kanalnivå
description: Lär dig hur du kan redigera uppspelningstiden för en viss bildkomponent i AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Varaktighet för massbildsuppspelning på kanalnivå {#channel-level-bulk-image-playback-duration}

## Ökning {#overview}

När du skapar en sekvenskanal och lägger till bilder i den får alla bilder som standard den uppspelningstid som definieras i konfigurationen på kanalnivå. Alla enskilda bilder kan fortfarande åsidosätta standardvärdet och ha en annan uppspelningstid. Detta uppnås genom att du redigerar uppspelningstiden för den specifika bildkomponenten.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har konfigurerat ett projekt som en förutsättning för att börja implementera den här funktionen. Exempel:

1. Skapa ett exempel på ett AEM Screens-projekt **ChannelLevelPlayback**.

1. Skapa en sekvenskanal som **PlaybackChannel** under **Kanaler** mapp.

1. Lägg till innehåll i **PlaybackChannel**.

## Redigera bilduppspelningens varaktighet på kanalnivå {#editing-channel-level-image-playback-duration-assignment}

I avsnittet nedan beskrivs hur du kan redigera uppspelningstiden för innehåll i en AEM Screens-kanal.

### Uppdatera uppspelningstiden för bilder i en kanal {#updating-the-playback-duration-for-images-in-a-channel}

Följ stegen nedan för att lära dig hur du uppdaterar tilldelning för bildspelets varaktighet på kanalnivå:

1. Navigera till sekvenskanalen **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Välj **Redigera** i åtgärdsfältet.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Lägg till två eller flera bilder i kanalredigeraren, enligt bilden nedan.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Markera alla bilder i kanalen och välj skiftnyckelsikonen i det övre vänstra hörnet (som bilden nedan visar) så att du kan öppna dialogrutan Konfigurera på kanalnivå.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. The **Sida** öppnas.

   >[!NOTE]
   >Som standard är bilderna i en kanal inställda på 8 sekunders uppspelningstid.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Redigera **Varaktighet** från 8 000 (millisekunder) till 3 000 (millisekunder), dvs. 3 sekunder. Markera bockmarkeringen längst upp till höger i dialogrutan **Sida** så att du kan spara ändringarna.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visa resultatet {#viewing-the-result}

När du har uppdaterat kanalens uppspelningstid (i det här exemplet alla tre bilderna) kan du se att bilderna spelas upp i 3 sekunder i stället för 8 sekunder (standardvärde).

![channel_preview](assets/channel_preview.gif)
