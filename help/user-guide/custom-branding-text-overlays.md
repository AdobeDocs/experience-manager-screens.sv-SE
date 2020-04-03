---
title: Använda anpassad profilering och formatering för textövertäckningar
seo-title: Använda anpassad profilering och formatering för textövertäckningar
description: Följ den här sidan om du vill veta mer om hur du använder anpassad profilering och formatering för textövertäckningar.
seo-description: Följ den här sidan om du vill veta mer om hur du använder anpassad profilering och formatering för textövertäckningar.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 835e801909d8d126042acd713fc68075ff598712

---


# Anpassad profilering och formatering för textövertäckningar {#creating-custom-branding-styling}

Följ den här sidan om du vill lära dig hur du använder anpassade märkesinställningar och format för textövertäckningar på dina resurser i en skärmkanal.

## Skapa anpassad profilering och formatering för textövertäckningar {#steps-custom-branding}

Följ stegen nedan för att skapa anpassade märkesnamn och format för textövertäckningar:

1. Skapa ett AEM Screens-projekt med namnet **custom style** och en kanal med namnet **DemoBrand**, vilket visas i bilden nedan.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dra och släpp en bild från redigeraren och lägg till textövertäckning till resursen.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Mer information om hur du lägger till en textövertäckning i resursen i en kanalredigerare finns i [Textövertäckning](/help/user-guide/text-overlay.md).

1. Navigera till CRXDE Lite från din AEM-instans —> Verktyg —> **CRXDE Lite**.

1. Du måste skapa en egen design i `/apps/settings/wcm/designs/<your-project>/`exempelvis navigera till `/apps/settings/wcm/designs/customstyle/`

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Navigera till filen *static.css* och ange följande css-regler. Visas också som ett exempel i figuren under CSS-reglerna.

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Kopiera sökvägen till ditt projekt, i det här fallet blir sökvägen `/apps/settings/wcm/designs/customstyle`.

1. Navigera till kanalen **DemoBrand** (skapad i steg 1) och klicka på **Egenskaper** i åtgärdsfältet när du har valt kanalen.

1. Navigera till fliken **Avancerat** och markera fältet **Design** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Som standard visar **designfältet** sökvägen till designen i mappen libs.

1. Uppdatera **designfältet** med sökvägen till projektmappen. I det här fallet kommer det att vara `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Klicka på **Spara och stäng** för att uppdatera designsökvägen.


## Visa resultatet {#viewing-the-result}

När du har slutfört de föregående stegen kan du uppdatera filen *statis.css* från **CRXDE Lite** och följaktligen visa uppdateringen av textöverlägget som redan har lagts till i resursen.

Följ stegen nedan för att visa den uppdaterade designen för textövertäckning:

1. Gå till ditt AEM Screens-projekt med namnet **custom** —> **Channels** —> **DemoBrand**. Markera kanalen och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.

1. Eftersom du nu har lagt till designen i fältet **Designer** klickar du på **Förhandsgranska** för att visa den aktuella stilen på bilden med textövertäckning.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navigera till filen *static.css* i CRXDE Lite och lägg till teckensnittet som, till exempel, `font-family: "Lucida Console", Courier, monospace;` till den här filen, som visas nedan.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. När du har sparat ändringarna och läst in förhandsvisningen igen visas en uppdatering av teckensnittet för textövertäckning, vilket visas i bilden nedan.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Dessutom kan du ta bort de två sista kodblocken från filen *static.css* för att ta bort den boxade stilen runt textövertäckningen.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Du kommer att se den uppdaterade ändringen i förhandsvisningen där textöverlägget läggs till i bilden.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

I självstudiekursen kan du nu uppdatera ditt varumärke och din anpassade stil för textöverlägg som läggs till i dina resurser.









