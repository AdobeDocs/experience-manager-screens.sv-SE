---
title: Skapa och hantera en Live-kopia
seo-title: Hantera LiveCopy
description: På den här sidan beskrivs hur du skapar och hanterar Live-kopior av kanaler.
seo-description: Följ den här sidan när du vill skapa en live-kopia av en kanal, visa egenskaper, kontrollera status och sprida ändringar från en kanal till dess live-kopia.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Skapa och hantera en Live-kopia {#creating-and-managing-a-live-copy}

På den här sidan beskrivs hur du skapar och hanterar Live-kopior av kanaler.

En ***Live-kopia*** är en kopia av specifikt webbplatsinnehåll som har en aktiv relation till den ursprungliga källan. Den här realtidsrelationen gör att den aktiva kopian kan ärva innehåll och sidegenskaper från källan.

På den här sidan beskrivs hur du skapar en live-kopia av en kanal, visar egenskaper, kontrollerar status och sprider ändringar från en kanal till dess live-kopia.


## Skapa en Live Copy {#creating-a-live-copy}

Följ stegen nedan för att skapa en live-kopia av en kanal i projektmappen.

1. Markera Adobe Experience Manager-länken (överst till vänster) och sedan **Skärmar**. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.

1. Navigera till Skärmprojekt och klicka på **Kanaler**.
1. Klicka på **Skapa** och välj **Live-kopia** för att skapa en live-kopia av kanalen.

1. Markera målet och klicka på **Nästa**.
1. Välj den plats där live-kopian finns.
1. Ange **Titel** och **namn** på sidan **Skapa Live-kopia** .

1. Klicka på **Öppna** för att visa innehållet i den nya live-kopian eller **Klar** för att återgå till huvudsidan.

Du kan även se stegen nedan för visuell representation av hur du skapar en ny live-kopia av en kanal.

I följande exempel visas hur en live-kopia (***IdleLiveCopy***) för ***Indle Channel*** med målmappen skapas som ***Kanaler***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Visa innehåll i Live Copy-kanalen {#viewing-content-of-the-live-copy-channel}

En Live-kopia är en kopia av en kanal som redan finns.

Om du vill visa innehållet i din live-kopia, se stegen nedan:

1. Navigera till Skärmprojekt och klicka på den plats där du ursprungligen skapade en Live-kopia, som visas i avsnittet ovan. (Här valdes platsen som **kanalmapp** )

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Klicka på **Redigera** i åtgärdsfältet för att visa innehållet i kanalen.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >När du visar innehåll för en direktkopieringskanal visas ett extra alternativ på menyn som **Live-kopieringsstatus**. Mer information finns i avsnittet nedan.

### Visa egenskaper för en Live-kopia {#viewing-properties-of-a-live-copy}

Dessutom kan du visa egenskaperna för den aktiva kopiekanalen.

1. Navigera till den aktiva kopiekanalen och klicka på **Egenskaper** i åtgärdsfältet.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Välj fliken **Live-kopia** om du vill visa information om kanalen.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Live Copy-status {#live-copy-status}

I läget **Live Copy-status**, som visas i figuren nedan, kan du visa relationsstatus för alla resurser i kanalen.

1. Klicka på **Redigera** för att välja **Live-kopieringsstatus** och visa associationen mellan kanalinnehållet och den ursprungliga kanalen (som live-kopian genereras från).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Välj **Live Copy Status** för förhandsgranskning.

   Alla resurser med grön kant visar att innehållet ärvs från den ursprungliga kanalen.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Bryta arvet {#breaking-the-inheritance}

Du kan också avbryta arvet från livecopy, så att innehållet blir oberoende av den ursprungliga grenen.

I följande exempel visas att du markerar bilden i redigeringsläget och klickar på symbolen för att avbryta arv överst till höger.

![chlimage_1-24](assets/chlimage_1-24.png)

### Sprida ändringar i Live Copy-kanalen {#propagating-changes-to-the-live-copy-channel}

Om du gör ändringar eller uppdateringar i den ursprungliga kanalen måste du också sprida dessa ändringar till din Live Copy-kanal.

Följ stegen nedan för att se till att dina ändringar sprids från den ursprungliga kanalen till den aktiva kopiekanalen:

1. Markera den ursprungliga kanalen (***inaktiv kanal***) och klicka på **Redigera** i åtgärdsfältet.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Redigera kanalinnehållet. Ta till exempel bort en bild från den här kanalen.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Markera den aktiva kopian av kanalen (***IdleLiveCopy***) och klicka på **Redigera** i åtgärdsfältet. Du kommer att märka att den bild du tog bort fortfarande visas i den aktiva kopian.

   För att kunna sprida ändringarna måste du synkronisera kanalen.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Navigera till AEM-kontrollpanelen och markera den aktiva kopieringskanalen och klicka på **Egenskaper** i åtgärdsfältet för att sprida ändringarna till den aktiva kopieringskanalen.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Välj fliken **Live-kopia** och klicka på **Synkronisera** i åtgärdsfältet.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Bekräfta ändringarna genom att klicka på **Synkronisera** . Klicka på **Spara och stäng** för att gå tillbaka till AEM-kontrollpanelen.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Du kommer att märka att bilden nu även tas bort från den aktiva kopiekanalen.

