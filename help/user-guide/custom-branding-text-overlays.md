---
title: Använda anpassad profilering och formatering för textövertäckningar
description: Lär dig hur du använder anpassad varumärkesprofilering och formatering för textövertäckningar som tillämpas på resurser i en AEM Screens-kanal.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---

# Anpassad profilering och formatering för textövertäckningar {#creating-custom-branding-styling}

Lär dig hur du använder anpassad varumärkesprofilering och formatering för textövertäckningar för dina resurser i en AEM Screens-kanal.

## Skapa anpassad profilering och formatering för textövertäckningar {#steps-custom-branding}

Följ stegen nedan för att skapa anpassade märkesnamn och format för textövertäckningar:

1. Skapa ett AEM Screens-projekt. I det här exemplet visas funktionaliteten genom att ett projekt med namnet **`customstyle`** och en kanal med namnet **DemoBrand** skapas, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dra och släpp en bild från redigeraren och lägg till en textövertäckning till resursen.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Mer information om hur du lägger till en textövertäckning i resursen i en kanalredigerare finns i [Textövertäckning](/help/user-guide/text-overlay.md).

1. Navigera till CRXDE Lite från AEM > verktyg > **CRXDE Lite**.

1. Skapa en anpassad design i `/apps/settings/wcm/designs/<your-project>/`, till exempel navigera till `/apps/settings/wcm/designs/customstyle/` i det här fallet

   ![bild](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Skapa en *static.css*-fil och ange följande css-regler. Visas också som ett exempel i figuren under CSS-reglerna.

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

1. Kopiera sökvägen till ditt projekt, i det här fallet är sökvägen `/apps/settings/wcm/designs/customstyle`.

1. Navigera till kanalen **DemoBrand** (skapad i steg(1)) och klicka på **Egenskaper** i åtgärdsfältet när du har valt kanalen.

1. Navigera till fliken **Avancerat** och kontrollera fältet **Design**.
   ![bild](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Som standard visar fältet **Design** sökvägen till designen i mappen libs.

1. Uppdatera fältet **Design** med sökvägen till projektmappen. I det här fallet är det `/apps/settings/wcm/designs/customstyle`.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Klicka på **Spara och stäng** för att uppdatera designsökvägen.

   >[!IMPORTANT]
   >Om du vill kan du överlagra de befintliga Screens-mallarna så att du kan mata in dina egna bilder som standard eller skapa en egen mall helt och hållet. Se stegen nedan för mer information.

1. Så här övertäcker du de befintliga Screens-mallarna för att mata in din egen design som standard:

   1. Överlägg `/libs/screens/core/templates/sequencechannel` i `/apps/screens/core/templates/sequencechannel`.
   1. Ändra egenskapen *`cq:designPath`* i `/apps/screens/core/templates/sequencechannel/jcr:content` så att den pekar på den nya designen.

1. Så här skapar du en egen mall:
   1. Kopiera `/libs/screens/core/templates/sequencechannel` till `/apps/customstyle/templates/styled-sequencechannel`.
   1. Ändra egenskapen *`cq:designPath`* i `/apps/customstyle/templates/styled-sequencechannel/jcr:content` så att den pekar på den nya designen.


### Uppdaterar åtkomstkontrollistor {#updating-acls}

Uppdatera åtkomstkontrollistorna för dessa designer så att spelaren kan hämta dem.

1. Navigera till användaradministratören, välj `screens-<project>-devices group` och ge den läsbehörighet till den anpassade designsökvägen.

1. Ange `screens-<project>-administrators`-gruppens läs- och ändringsbehörigheter till den här sökvägen.

## Visa resultatet {#viewing-the-result}

När du har slutfört de föregående stegen kan du uppdatera filen *statis.css* från **CRXDE Lite** och därför visa uppdateringen av textöverlägget som redan har lagts till i resursen.

Följ stegen nedan för att visa den uppdaterade designen för textövertäckning:

1. Navigera till ditt AEM Screens-projekt med namnet **`customstyle`** > **Kanaler** > **DemoBrand**. Klicka på kanalen och klicka på **Redigera** i åtgärdsfältet.

1. Eftersom du nu har lagt till designen i fältet **Designs** klickar du på **Förhandsgranska** för att visa den aktuella stilen på bilden med textövertäckning.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navigera till filen *static.css* i CRXDE Lite och lägg till teckensnittet `font-family: "Lucida Console", Courier, monospace;` i den här filen, som visas nedan.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. När du sparar ändringarna och läser in förhandsvisningen igen visas en uppdatering av teckensnittet för textövertäckning, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Du kan även ta bort de två sista kodblocken från filen *static.css* för att ta bort den boxade formateringen runt textövertäckningen.

![bild](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Visa den uppdaterade ändringen i förhandsgranskningen där textöverlägget läggs till i bilden.

   ![bild](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Nu kan ni uppdatera ert varumärke och era anpassade format för textöverlägg som lagts till i era resurser.
