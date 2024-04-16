---
title: Skapa anpassade mallar i MultiZone-layouter
description: Lär dig hur du skapar egna mallar i MultiZone-layouter för AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 1%

---

# Skapa anpassade mallar för MultiZone-layouter {#creating-custom-templates-multizone}

På den här sidan visas hur du kan skapa en anpassad mall för en layout med flera zoner.

## Viktiga överväganden {#considerations}

Det finns två viktiga saker att tänka på innan du skapar en anpassad mall i en layout med flera zoner:

1. **Fastställd pixelstorlek eller procenttal**:

   Bestäm om du vill använda fast pixelstorlek för olika zoner för den anpassade layouten eller om du vill skapa en anpassad layout med procentandelar.

   >[!NOTE]
   >Fördelen med att använda procent för att ange zoner för din anpassade layout gör att du kan återanvända mallen på olika skärmstorlekar.

1. **Namngivningskonvention**:

   Innan du vet hur du skapar anpassade mallar för flera zoner som ska användas i ett AEM Screens-projekt bör du förstå variationen i mallarna som du vill skapa.

   | **Layoutnamn** | **Beskrivning** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | En liggande layout med tre zoner där du kan skapa tre zoner:<br>* Zon 1 som 20 % av den vågräta och lodräta skärmen från vänster<br>* Zon 2 som 80 % av den horisontella skärmen och 20 % av den vertikala skärmen som är högerjusterad<br>* Zon 3 som 100 % av den horisontella och 80 % av den vertikala skärmen med proportionen 16:9 |
   | `Upper20-PortraitHD2Zone` | En mall med stående orientering i två zoner som täcker 20 % av skärmen uppifrån, med proportionerna 16:9 |
   | `Right20-LandscapeSD3Zone` | En mall med tre zoner som täcker 20 % av skärmen från höger, med proportionerna 4:3 |

   >[!IMPORTANT]
   >De zoner som definieras i den anpassade layouten kanske inte matchar den övergripande bildproportionen för hela layouten. Den namnkonvention som följs i det här dokumentet anger proportionerna för den anpassade layouten som helhet.

## Exempel på användningsfall `Left20-LandscapeHD3Zone` Layout {#custom-template-one}

Skapa en egen mall genom att följa avsnittet nedan *`Left20-LandscapeHD3Zone`* med följande konfiguration:

* **`Left20`** - Den övre zon till vänster som täcker 20 % av den vågräta och lodräta skärmstorleken.
* **`Landscape`** - Skärmorienteringen.
* **`HD`** - Proportionerna är 16:9.
* **`3Zone`** - Tre zoner på skärmen.

## Visuell representation av MultiZone-layout {#multi-layout-visual-one}

The `Left20-LandscapeHD3Zone` Med layout kan du skapa följande layout för flera zoner i ditt projekt:

![bild](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Skapa en `Left20-LandscapeHD3Zone` Layout {#landscape-layout-one}

Följ stegen nedan för att skapa en `Left20-LandscapeHD3Zone` Layout för ett AEM Screens-projekt.

1. Skapa ett AEM Screens-projekt med namnet **`customtemplate`**.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Navigera till **CRXDE Lite** från AEM > Verktyg > **CRXDE Lite**.

1. Skapa en mapp under **appar** titled som **`customtemplate`**. Skapa en annan mapp med namnet som **mall** under **`customtemplate`**, vilket visas i figuren nedan.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Klicka **Spara alla** från åtgärdsfältet i CRXDE Lite varje gång du skapar, redigerar eller kopierar innehåll till någon av noderna. Annars kan du inte genomföra uppdateringarna.

1. Kopiera mallen längst till vänster från `/libs/screens/core/templates/splitscreenchannel/lbar-left` till `/apps/customtemplate/template`.

1. Byt namn på den kopierade **lbar-left** (`/apps/customtemplate/template`) till **min-anpassad-layout**.
   ![bild](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Navigera till `/apps/customtemplate/template/my-custom-layout` och uppdatera egenskaperna **`jcr:description`** till *Mall för`Left20-LandscapeHD3Zone`* och **`jcr:title`** till *`Left20-LandscapeHD3Zone`*.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Navigera till **`offline-config`** från `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` och uppdatera **`jcr:title`** till *`Left20-LandscapeHD3Zone`*.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Navigera till *`jcr:content`* egenskap för **my-custom-template** från `/apps/customtemplate/template/my-custom-layout/jcr:content` och uppdatera **`cq:cssClass`** så att du kan använda **aem-Layout my-custom-layout**.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. Med hänvisning till steg (4) där du kopierade mallen längst till vänster kan du visa tre responsiva rutnät under `my-custom-layout/jcr:content`. Lägg till en anpassad CSS-klass i vart och ett av de responsiva rutnäten i *`cq:cssClass`* egenskap, till exempel *my-custom-layout—top-left* for *r1c1* nod.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template7.png)

   På samma sätt lägger du till *my-custom-layout—top-right* for *r1c2*  och *my-custom-layout—bottom* for *r2c1* nod.

   >[!NOTE]
   >Dessa anpassade klasser används i CSS för att ange bredd/höjd för dessa responsiva rutnät.

   >[!NOTE]
   >Du kan lägga till eller ta bort responsiva stödraster baserat på det antal stödraster du vill ha. I det här exemplet visas två stödraster i den första raden och ett stödraster i den andra raden, så det finns totalt tre responsiva stödraster (r1c1, r1c2, r2c1).

1. Kopiera `/libs/settings/wcm/designs/screens` till `/apps/settings/wcm/designs/` och döp om den kopierade designen som **custom-template-designs**.

1. Navigera till `/apps/settings/wcm/designs/custom-template-designs` och uppdatera egenskapen *`jcr:title`* av **custom-template-designs** till **anpassad malldesign**.

1. Navigera till `/apps/settings/wcm/designs/custom-template-designs` och skapa en fil som static.css.

1. Kopiera innehållet till `static.css` fil:

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

1. Navigera till `/apps/<project>/templates/my-custom-layout/jcr:content` och uppdatera egenskapen *`cq:designPath`* till `/apps/settings/wcm/designs/customtemplate-designs` så att du kan läsa in de format som konfigurerats i static.css.

   >[!NOTE]
   >Skriv in alla format i stället för att kopiera eller klistra in, vilket kan orsaka problem med blanktecken som leder till CSS-format.

## Visa resultatet {#viewing-result}

Följ stegen nedan för att använda ovanstående anpassade mall i ditt AEM Screens-projekt:

1. Navigera till skärmsprojektet som du skapade i steg 1 och klicka på **Kanaler** mapp.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Klicka **Skapa** från åtgärdsfältet och klicka på mallen **`Left20-LandscapeHD3Zone`** från **Skapa** guide.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. När du har skapat en kanal med den anpassade mallen kan du lägga till resurser i kanalen från redigeraren. I följande förhandsvisning visas bilderna i en anpassad mall.

   ![bild](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Infoga en bild som bakgrundslager  {#inserting-image}

Du kan infoga en bild som bakgrundslager i layouten:

Du kan justera CSS-regeln så att den använder&quot;data-uri&quot; och infogar bilden direkt (`Base64` kodad) i CSS-filen som du skapade i (steg 13), *static.css*.

Detta görs på följande sätt:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Du kan också följa stegen nedan:

1. Kontrollera att bilden på något sätt ingår i kanalens offlinekonfiguration.
1. Använd en direkt länk till bilden i CSS ovan i stället för varianten data-uri.


## Uppdaterar bakgrundsfärg {#updating-color}

Om du vill ändra bakgrundsfärgen lägger du till följande kod i XML-filen (steg 13): *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
