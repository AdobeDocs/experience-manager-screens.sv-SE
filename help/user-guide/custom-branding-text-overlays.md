---
title: Använda anpassad profilering och formatering för textövertäckningar
seo-title: Använda anpassad profilering och formatering för textövertäckningar
description: Följ den här sidan om du vill veta mer om hur du använder anpassad profilering och formatering för textövertäckningar.
seo-description: Följ den här sidan om du vill veta mer om hur du använder anpassad profilering och formatering för textövertäckningar.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 099000dea848810c7ab12a32f0235ca478c0d5dd
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 1%

---


# Anpassad profilering och formatering för textövertäckningar {#creating-custom-branding-styling}

Följ den här sidan om du vill lära dig hur du använder anpassade märkesinställningar och format för textövertäckningar på dina resurser i en AEM Screens-kanal.

## Skapa anpassad profilering och formatering för textövertäckningar {#steps-custom-branding}

Följ stegen nedan för att skapa anpassade märkesnamn och format för textövertäckningar:

1. Skapa ett AEM Screens-projekt. I det här exemplet visas funktionaliteten genom att ett projekt med namnet **customStyle** och en kanal med namnet **DemoBrand** skapas, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dra och släpp en bild från redigeraren och lägg till textövertäckning till resursen.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Mer information om hur du lägger till en textövertäckning i resursen i en kanalredigerare finns i [Textövertäckning](/help/user-guide/text-overlay.md).

1. Navigera till CRXDE Lite från din AEM instans —> tools —> **CRXDE Lite**.

1. Du måste skapa en anpassad design i `/apps/settings/wcm/designs/<your-project>/`, t.ex. navigera till `/apps/settings/wcm/designs/customstyle/`

   ![bild](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Skapa filen *static.css* och ange följande css-regler. Visas också som ett exempel i figuren under CSS-reglerna.

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![bild](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Kopiera sökvägen till ditt projekt. I det här fallet är sökvägen `/apps/settings/wcm/designs/customstyle`.

1. Navigera till kanalen **DemoBrand** (skapad i steg(1)) och klicka på **Egenskaper** i åtgärdsfältet när du har valt kanalen.

1. Gå till fliken **Avancerat** och kontrollera fältet **Design**.
   ![bild](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Som standard visar fältet **Design** sökvägen till designen i mappen libs.

1. Uppdatera fältet **Design** med sökvägen till projektmappen. I det här fallet blir det `/apps/settings/wcm/designs/customstyle`.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Klicka på **Spara och stäng** för att uppdatera designsökvägen.

   >[!IMPORTANT]
   >Du kan välja att täcka över de befintliga skärmmallarna för att mata in dina egna designer som standard eller skapa en egen mall helt och hållet. Mer information finns i stegen nedan.

1. Så här övertäcker du de befintliga skärmmallarna så att du kan mata in din egen design som standard:

   1. Lägg över `/libs/screens/core/templates/sequencechannel` i `/apps/screens/core/templates/sequencechannel`.
   1. Ändra egenskapen *cq:designPath* i `/apps/screens/core/templates/sequencechannel/jcr:content` så att den pekar på den nya designen.

1. Så här skapar du en egen mall:
   1. Kopiera `/libs/screens/core/templates/sequencechannel` till `/apps/customstyle/templates/styled-sequencechannel`.
   1. Ändra egenskapen *cq:designPath* i `/apps/customstyle/templates/styled-sequencechannel/jcr:content` så att den pekar på den nya designen.


### Uppdaterar åtkomstkontrollistor {#updating-acls}

Du måste uppdatera åtkomstkontrollistorna för dessa designer så att de kan hämtas av spelaren.

1. Navigera till användaradministratören och välj `screens-<project>-devices group` och ge den läsbehörighet till den anpassade designsökvägen.

1. Ange `screens-<project>-administrators`-gruppbehörighet för att läsa och ändra i den här sökvägen.

## Visa resultatet {#viewing-the-result}

När du har utfört de föregående stegen kan du uppdatera din *statis.css*-fil från **CRXDE Lite** och följaktligen visa uppdateringen av textöverlägget som redan har lagts till i resursen.

Följ stegen nedan för att visa den uppdaterade designen för textövertäckning:

1. Gå till ditt AEM Screens-projekt med namnet **custom style** —> **Channels** —> **DemoBrand**. Markera kanalen och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.

1. Eftersom du nu har lagt till designen i fältet **Designs**, som nämnts ovan, klickar du på **Förhandsgranska** för att visa den aktuella formateringen i bilden med textövertäckning.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navigera till filen *static.css* i CRXDE Lite och lägg till teckensnittet `font-family: "Lucida Console", Courier, monospace;` i den här filen, som visas nedan.
   ![bild](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. När du har sparat ändringarna och läst in förhandsvisningen igen visas en uppdatering av teckensnittet för textövertäckning, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Du kan även ta bort de två sista kodblocken från filen *static.css* för att ta bort den rutformade formateringen runt textövertäckningen.
   ![bild](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Du kommer att se den uppdaterade ändringen i förhandsvisningen där textöverlägget läggs till i bilden.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Nu kan ni uppdatera ert varumärke och anpassa formateringen för textöverlägg som läggs till i ert material.









