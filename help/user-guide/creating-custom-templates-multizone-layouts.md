---
title: Skapa anpassade mallar i MultiZone-layouter
seo-title: Skapa anpassade mallar i MultiZone-layouter
description: Följ den här sidan om du vill veta mer om hur du skapar egna mallar i MultiZone-layouter.
seo-description: Följ den här sidan om du vill veta mer om hur du skapar egna mallar i MultiZone-layouter.
contentOwner: Jyotika Syal
feature: Utveckla skärmar
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 1%

---


# Skapa anpassade mallar för MultiZone-layouter {#creating-custom-templates-multizone}

På den här sidan visas hur du kan skapa en anpassad mall för en layout med flera zoner.

## Viktiga överväganden {#considerations}

Det finns två viktiga saker att tänka på innan du skapar en anpassad mall i en layout med flera zoner:

1. **Fasta pixelstorlekar eller procenttal**:

   Du måste bestämma om du ska använda fast pixelstorlek för olika zoner för den anpassade layouten eller om du vill skapa en anpassad layout med procentandelar.

   >[!NOTE]
   >Fördelen med att använda procent för att ange zoner för din anpassade layout gör att du kan återanvända mallen på flera olika skärmstorlekar.

1. **Namngivningskonvention**:

   Innan du vet hur du skapar anpassade mallar för flera zoner som ska användas i ett AEM Screens-projekt bör du förstå variationen i de mallar du vill skapa.

   | **Layoutnamn** | **Beskrivning** |
   |---|---|
   | Left20-LandscapeHD3Zone | Avser en liggande layout med 3 zoner där du kan skapa 3 zoner med zon 1 som 20 % av den horisontella och vertikala skärmen från vänster, zon 2 som 80 % av den horisontella skärmen och 20 % av den vertikala skärmen till höger, zon 3 som 100 % av den horisontella och 80 % av den vertikala skärmen med proportionen 16:9 |
   | Upper20-PortraitHD2Zone | Avser en porträttmall med två zoner som täcker 20 % av skärmen uppifrån, med proportionerna 16:9 |
   | Right20-LandscapeSD3Zone | Avser en mall med tre zoner som täcker 20 % av skärmen från höger, med proportionerna 4:3 |

   >[!IMPORTANT]
   >De zoner som definieras i den anpassade layouten kanske inte matchar den övergripande bildproportionen för hela layouten. Den namnkonvention som följs i det här dokumentet anger proportionerna för den anpassade layouten som helhet.

## Exempel: Använd skiftläge vänster20-liggandeHD3Zonlayout {#custom-template-one}

Följ avsnittet nedan för att skapa en anpassad mall *Left20-LandscapeHD3Zone* med följande konfiguration:

* **Left20** hänvisar till den övre zonen till vänster som täcker 20 % av den vågräta och lodräta skärmstorleken.
* **Liggande** orientering avser skärmorienteringen
* **HD** motsvarar proportionerna 16:9
* **3** Zonereferenser till tre zoner på skärmen

## Visuell representation av MultiZone-layout {#multi-layout-visual-one}

Med Left20-LandscapeHD3Zone-layouten kan du skapa följande layout för flera zoner i ditt projekt:

![bild](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Skapa en Left20-LandscapeHD3Zone-layout {#landscape-layout-one}

Följ stegen nedan för att skapa en Left20-LandscapeHD3Zone-layout för ett AEM Screens-projekt:

1. Skapa ett AEM Screens-projekt med namnet **anpassad mall**.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Gå till **CRXDE Lite** från din AEM instans —> Verktyg —> **CRXDE Lite**.

1. Skapa en mapp under **program** med namnet **anpassad mall**. Skapa på samma sätt en annan mapp med namnet **template** under **custom template**, som bilden nedan visar.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Vi rekommenderar att du klickar på **Spara alla** från åtgärdsfältet i CRXDE Lite varje gång du skapar, redigerar eller kopierar innehåll till någon av noderna, annars kommer du inte att kunna genomföra uppdateringarna.

1. Kopiera mallen för vänster fält från `/libs/screens/core/templates/splitscreenchannel/lbar-left` till `/apps/customtemplate/template`.

1. Byt namn på den kopierade **lbar-left** (`/apps/customtemplate/template`) till **my-custom-layout**.
   ![bild](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Navigera till `/apps/customtemplate/template/my-custom-layout` och uppdatera egenskaperna **jcr:description** till *Mall för Left20-LandscapeHD3Zone* och **jcr:title** till *Left20-LandscapeHD3Zone*.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Navigera till **offline-config**-noden från `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` och uppdatera **jcr:title** till *Left20-LandscapeHD3Zone*.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Navigera till egenskapen *jcr:content* för **my-custom-template** från `/apps/customtemplate/template/my-custom-layout/jcr:content` och uppdatera egenskapen **cq:cssClass** till **aem-Layout my-custom-layout**.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. I steg 4 där du kopierade mallen längst till vänster visas 3 responsiva stödraster under `my-custom-layout/jcr:content`. Lägg till en anpassad CSS-klass i vart och ett av de responsiva rutnäten i egenskapen *cq:cssClass*, till exempel *my-custom-layout—top-left* för *r1c1*-noden.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Lägg på liknande sätt till *my-custom-layout—top-right* för *r1c2* och, *my-custom-layout—bottom* för *r2c1*-nod.

   >[!NOTE]
   >Dessa anpassade klasser används i CSS för att ange bredd/höjd för dessa responsiva rutnät.

   >[!NOTE]
   >Du kan lägga till eller ta bort responsiva stödraster baserat på det antal stödraster du vill ha. I det här exemplet visar vi 2 stödraster i den första raden och 1 stödraster i den andra raden, så det finns totalt tre responsiva stödraster (r1c1, r1c2, r2c1).

1. Kopiera `/libs/settings/wcm/designs/screens` till `/apps/settings/wcm/designs/` och byt namn på den kopierade designen till **custom-template-designs**.

1. Navigera till `/apps/settings/wcm/designs/custom-template-designs` och uppdatera egenskapen *jcr:title* för **custom-template-designs** till **custom template-design**.

1. Navigera till `/apps/settings/wcm/designs/custom-template-designs` och skapa en fil som static.css.

1. Kopiera innehållet till filen `static.css`:

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   >Du kan uppdatera procentsatserna så att de matchar kraven för den anpassade mallen.

1. Navigera till `/apps/<project>/templates/my-custom-layout/jcr:content` och uppdatera egenskapen *cq:designPath* till `/apps/settings/wcm/designs/customtemplate-designs` för att läsa in formaten som konfigurerats i static.css

   >[!NOTE]
   >Vi rekommenderar att du skriver alla format i stället för att kopiera eller klistra in, vilket kan orsaka problem med blanktecken och CSS-format.

## Visa resultatet {#viewing-result}

Följ stegen nedan för att använda ovanstående anpassade mall i ditt AEM Screens-projekt:

1. Navigera till skärmsprojektet som du skapade i steg (1) och markera mappen **Kanaler**.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Klicka på **Skapa** i åtgärdsfältet och välj mallen **Left20-LandscapeHD3Zone** i guiden **Skapa**.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. När du har skapat en kanal med den anpassade mallen kan du lägga till resurser i kanalen från redigeraren. I följande förhandsvisning visas bilderna i en anpassad mall.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Infoga en bild som bakgrundslager {#inserting-image}

Du kan infoga en bild som bakgrundslager i layouten:

Du kan justera CSS-regeln så att den använder det som kallas&quot;data-uri&quot; och direkt infogar bilden (Base64-kodad) i CSS-filen som du skapade i (steg 13), *static.css*.

Detta görs på följande sätt:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Du kan också följa stegen nedan:

1. Kontrollera att bilden på något sätt ingår i kanalens offlinekonfiguration
1. Använd en direkt länk till bilden i CSS ovan i stället för varianten data-uri


## Uppdaterar bakgrundsfärg {#updating-color}

Om du vill ändra bakgrundsfärgen lägger du till följande kod i XML-filen (steg 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



