---
title: On Demand Content Update
description: Läs mer om innehållsuppdatering on-demand för hantering av publikationer.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# On Demand Content Update {#on-demand}

I det här avsnittet beskrivs on-demand-innehåll för hantering av publikationer.

## Hantera publikation: Leverera innehållsuppdateringar från författare till publicering på enhet {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Du kan publicera och avpublicera innehåll från AEM Screens. Med funktionen Hantera publikation kan du leverera innehållsuppdateringar från författare till publiceringsenhet. Du kan publicera/avpublicera innehåll för hela AEM Screens-projektet eller bara för en av dina kanaler, platser, enheter, program eller scheman.

### Hantera publikationer för ett AEM Screens-projekt {#managing-publication-for-an-aem-screens-project}

Följ stegen nedan för att leverera innehållsuppdateringar från författare till publiceringsenhet för ett AEM Screens-projekt:

1. Gå till ditt AEM Screens-projekt.
1. Klicka **Hantera publikation** i åtgärdsfältet så att du kan publicera projektet i din Publish-instans.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. The **Hantera publikation** Guiden öppnas. Du kan klicka på **Åtgärd** och schemalägger även publiceringstiden för tillfället eller senare. Klicka på **Nästa**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Markera kryssrutan så att du kan klicka på hela projektet från **`Manage Publication`** guide.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Klicka **+ Inkludera underordnade** från åtgärdsfältet och avmarkera alla alternativ så att du kan publicera alla moduler i projektet och klicka på **Lägg till** att publicera.

   >[!NOTE]
   >
   >Som standard är alla rutor markerade och du måste avmarkera rutorna manuellt för att publicera alla moduler i projektet.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Dialogrutan Inkludera underordnade**

   Stegen ovan visar hur du kan publicera hela innehållet. Om du vill använda de andra tre alternativen måste du markera det alternativet.
I följande bild visas hur du kan hantera och uppdatera endast de ändrade sidorna i ditt projekt:
   ![bild](assets/author-publish-manage.png)

   Följ förklaringarna nedan för att förstå vilka alternativ som är tillgängliga:

   1. **Inkludera endast omedelbart underordnade**: Med det här alternativet kan du bara hantera uppdateringar av delnoderna i projektstrukturen.
   1. **Inkludera endast ändrade sidor**: Med det här alternativet kan du bara hantera uppdateringar av de ändrade sidorna i projektet där ändringarna finns i projektstrukturen.
   1. **Inkludera endast redan publicerade sidor**: Med det här alternativet kan du bara hantera uppdateringar av sidor som publicerats tidigare.


1. Från **`Manage Publication wizard`**, klicka **Publicera**.

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Vänta i några sekunder/minuter så att innehållet når publiceringsinstansen.
   >
   >
   >    1. Arbetsflödet fungerar inte om det inte finns några ändringar i projektet och inget för **Uppdatera offlineinnehåll**.
   >    1. Arbetsflödet fungerar inte om författaren inte har slutfört replikeringsprocessen (innehållet överförs fortfarande till publiceringsinstansen) efter att ha valt **Publicera** i arbetsflödet för publicering.

   >[!CAUTION]
   >Om du som innehållsskapare vill se ändringarna i enheterna som är kopplade till författarinstansen klickar du på **Uppdatera offlineinnehåll** från kanalkontrollpanelen eller genom att välja projektet. I det här fallet utförs uppdateringen av offlineinnehåll endast i författarinstansen.

1. Navigera till projektet och klicka på **Uppdatera offlineinnehåll** i åtgärdsfältet. Den här åtgärden vidarebefordrar samma kommando till publiceringsinstansen, så att offlinepostmeddelandena skapas även i din Publish-instans.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >När du har slutfört arbetsflödet för publicering, och om det finns en spelare som pekar på Author-instansen, utlöser du uppdateringen av offlineinnehåll i författaren. När du gör det skapas uppdateringen offline på författarinstansen.

   >[!CAUTION]
   >
   >Utlös uppdateringsinnehållet offline i Author-instansen om du har en spelare registrerad på författarservern. Uppdatering av offlineinnehåll krävs inte för spelaren som är registrerad på Publishing-instansen.

### Hantera publikation för en kanal {#managing-publication-for-a-channel}

Följ stegen nedan för att leverera innehållsuppdateringar från författare > Publicera > enhet för en kanal i ett AEM Screens-projekt:

>[!NOTE]
>
>Följ bara det här avsnittet om en kanal har ändrats. Om en kanal inte har några ändringar efter den tidigare uppdateringen av offlineinnehåll, kommer arbetsflödet för att hantera publicering för en enskild kanal inte att fungera.

1. Navigera till ditt AEM Screens-projekt och klicka på kanalen.
1. Klicka **Hantera publikation** från åtgärdsfältet så att du kan publicera kanalen till din Publish-instans.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. The **Hantera publikation** Guiden öppnas. Du kan klicka på **Åtgärd** och schemalägger även publiceringstiden för tillfället eller senare. Klicka på **Nästa**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Klicka **Publicera** från **`Manage Publication`** guide.

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Vänta i några sekunder/minuter så att innehållet når publiceringsinstansen.

1. Utlösande **Uppdatera offlineinnehåll** i kanalkontrollpanelen skickar bara offlineinnehållet till författarinstansen, men inte till publiceringsinstansen. Steg 1-4 används för att överföra offlineinnehåll till Publish-instansen.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Publicera först och utlösa sedan uppdateringen av offlineinnehåll enligt sammanfattningen i föregående steg.

### Kanal- och enhetsomtilldelning: {#channel-and-device-re-assignment}

Om du har tilldelat om en enhet kan du publicera både den första och den nya skärmen när enheten har tilldelats om till den nya skärmen.

Om du har omtilldelat en kanal kan du publicera både den inledande och den nya visningen när kanalen har omtilldelats till den nya skärmen.
