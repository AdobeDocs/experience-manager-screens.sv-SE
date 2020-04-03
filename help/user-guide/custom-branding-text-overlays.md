---
title: Använda anpassad profilering och formatering för textövertäckningar
seo-title: Använda anpassad profilering och formatering för textövertäckningar
description: Följ den här sidan om du vill veta mer om hur du använder anpassad profilering och formatering för textövertäckningar.
seo-description: Följ den här sidan om du vill veta mer om hur du använder anpassad profilering och formatering för textövertäckningar.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f91faa23c7c5c4f0f705c77251554b64efaf2611

---


# Anpassad profilering och formatering för textövertäckningar {#creating-custom-branding-styling}

Följ den här sidan om du vill veta mer om hur du använder anpassad profilering och formatering för textövertäckningar.

## Skapa anpassad profilering och formatering för textövertäckningar {#steps-custom-branding}

Följ stegen nedan för att skapa anpassade märkesnamn och format för textövertäckningar:

1. Skapa ett AEM Screens-projekt med namnet **custom style** och en kanal med namnet **DemoBrand**, vilket visas i bilden nedan.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dra och släpp en bild från redigeraren och lägg till textövertäckning till resursen.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Mer information om hur du lägger till en textövertäckning i resursen i en kanalredigerare finns i [Textövertäckning](/help/user-guide/text-overlay.md).

1. Navigera till CRXDE Lite från din AEM-instans —> Verktyg —> **CRXDE Lite**.

1. Du måste skapa en egen design i `/apps/settings/wcm/designs/<your-project>/`exempelvis det här fallet

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Navigera till filen static.css och ange följande css-regler. Visas också i figuren nedan.

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

1. Navigera till kanalen som heter **DemoBrand** (skapas i steg 1) och klicka på **Egenskaper** i åtgärdsfältet när du har valt kanalen.

1. Navigera till fliken **Avancerat** och markera fältet **Design** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Som standard visar **designfältet** sökvägen till designen i mappen libs.

1. Uppdatera **designfältet** med sökvägen till projektmappen. I det här fallet kommer det att vara `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Klicka på **Spara och stäng** för att uppdatera designsökvägen.


## Visa resultatet {#viewing-the-result}

När du har utfört de föregående stegen kan du uppdatera filen *statis.css* från **CRXDE Lite** och följaktligen visa uppdateringen av textlayouten som har lagts till i resursen.

Följ stegen nedan för att visa den uppdaterade designen i en textlayout:

1. Gå till ditt AEM Screens-projekt med namnet **custom style** och en kanal med namnet **DemoBrand** och klicka på **Edit** i åtgärdsfältet för att öppna redigeraren.

1. Eftersom du nu har lagt till designen i fältet **Designer** klickar du på **Förhandsgranska** för att visa den aktuella stilen på bilden med textövertäckning.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navigera till filen static.css i CRXDE Lite. Lägg till teckensnittet.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. När du har sparat ändringarna och läst in förhandsvisningen igen visas en uppdatering av teckensnittet för textövertäckning, vilket visas i bilden nedan.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Dessutom kan du ta bort de två sista kodblocken från filen static.css för att ta bort den boxade formateringen runt textövertäckningen.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Du kommer att se den uppdaterade ändringen i förhandsvisningen där textöverlägget läggs till i bilden, vilket visas nedan.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

Så om du följer stegen i de föregående avsnitten kan du uppdatera ditt varumärke och din anpassade stil för textövertäckningar som läggs till i dina resurser.









