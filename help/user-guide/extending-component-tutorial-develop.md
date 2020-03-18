---
title: Utöka en AEM-skärmkomponent
seo-title: Utöka en AEM-skärmkomponent
description: I följande självstudiekurs går du igenom stegen och de bästa sätten att utöka komponenter från AEM Screens. Bildkomponenten utökas för att lägga till en redigerbar textövertäckning.
seo-description: I följande självstudiekurs går du igenom stegen och de bästa sätten att utöka komponenter från AEM Screens. Bildkomponenten utökas för att lägga till en redigerbar textövertäckning.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ec8324ead3789a6cd5dde35a932c89e916709f70

---


# Utöka en AEM-skärmkomponent {#extending-an-aem-screens-component}

I följande självstudiekurs går du igenom stegen och de bästa sätten att utöka komponenter från AEM Screens. Bildkomponenten utökas för att lägga till en redigerbar textövertäckning.

## Översikt {#overview}

Den här självstudiekursen är avsedd för utvecklare som inte har använt AEM Screens tidigare. I den här självstudiekursen utökas komponenten Skärmbild för att skapa en Poster-komponent. En titel, beskrivning och logotyp läggs ovanpå en bild för att skapa en övertygande upplevelse i en sekvenskanal.

>[!NOTE]
>
>Innan du startar den här självstudiekursen rekommenderar vi att du slutför självstudiekursen: [Utveckla en anpassad komponent för AEM-skärmar](developing-custom-component-tutorial-develop.md).

![Egen förhandsgranskningskomponent](assets/2018-05-07_at_4_09pm.png)

En anpassad filmminiatyrkomponent skapas genom att bildkomponenten utökas.

## Förutsättningar {#prerequisites}

För att slutföra den här självstudiekursen behöver du följande:

1. [AEM 6.4](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/release-notes.html) eller [AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + Senaste skärmar, funktionspaket
1. [AEM Screens Player](/help/user-guide/aem-screens-introduction.md)
1. Lokal utvecklingsmiljö

Självstudiestegen och skärmbilderna utförs med CRXDE-Lite. [Eclipse](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) eller [IntelliJ](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) IDE kan också användas för att slutföra självstudiekursen. Mer information om hur du använder en utvecklingsmiljö för att [utveckla med AEM finns här](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide).

## Projektinställningar {#project-setup}

Källkoden för ett skärmsprojekt hanteras vanligtvis som ett Maven-projekt med flera moduler. För att underlätta självstudiekursen har ett projekt förskapats med [AEM Project Archetype 13](https://github.com/adobe/aem-project-archetype). Mer information om hur du [skapar ett projekt med Maven AEM Project Archetype finns här](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule).

1. Hämta och installera följande paket med **CRX-pakethantering**`http://localhost:4502/crx/packmgr/index.jsp)r:`

   [Hämta fil](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [Hämta fil](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Om du arbetar med Eclipse eller någon annan IDE kan** du hämta källpaketet nedan. Distribuera projektet till en lokal AEM-instans med kommandot Maven:

   **`mvn -PautoInstallPackage clean install`**

   SRC-startskärmar - webb.Kör projekt

   [Hämta fil](assets/start-poster-screens-weretail-run.zip)

1. I **CRX Package Manager** är `http://localhost:4502/crx/packmgr/index.jsp` följande två paket installerade:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![Skärmar, Web.Retail Kör Ui.Apps och Ui.Innehållspaket som installeras via CRX Package Manager](assets/crx-packages.png)

   Skärmar, Web.Retail Kör Ui.Apps och Ui.Innehållspaket som installeras via CRX Package Manager

## Skapa förhandsgranskningskomponenten {#poster-cmp}

Komponenten Poster utökar bildskärmskomponenten utanför rutan. En mekanism som Sling, `sling:resourceSuperType`, används för att ärva huvudfunktionerna i Image-komponenten utan att behöva kopiera och klistra in. Mer information om grunderna för bearbetning av [skickningsbegäran finns här.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

Komponenten Poster återges i helskärmsläge i förhandsgransknings-/produktionsläge. I redigeringsläge är det viktigt att återge komponenten på ett annat sätt för att underlätta redigeringen av sekvenskanalen.

1. I **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (eller valfri IDE) nedan `/apps/weretail-run/components/content`skapar du ett nytt `cq:Component` namn `poster`.

   Lägg till följande egenskaper i `poster` komponenten:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![Egenskaper för /apps/weretail-run/components/content/affisch](assets/poster.png)

   Egenskaper för /apps/weretail-run/components/content/affisch

   Genom att ställa in `sling:resourceSuperType`egenskapen lika med `screens/core/components/content/image` komponenten Poster, ärvs alla funktioner i komponenten Image. Likvärdiga noder och filer som hittas under `screens/core/components/content/image` kan läggas till under `poster` komponenten för att åsidosätta och utöka funktionaliteten.

1. Kopiera `cq:editConfig` noden under `/libs/screens/core/components/content/image.`Klistra in `cq:editConfig` under `/apps/weretail-run/components/content/poster` komponenten.

   Uppdatera `cq:editConfig/cq:dropTargets/image/parameters` egenskapen till lika med på `sling:resourceType` noden `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   XML-representation av cq:editConfig som återges nedan:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="cq:EditConfig">
       <cq:dropTargets jcr:primaryType="nt:unstructured">
           <image
               jcr:primaryType="cq:DropTargetConfig"
               accept="[image/.*]"
               groups="[media]"
               propertyName="./fileReference">
               <parameters
                   jcr:primaryType="nt:unstructured"
                   sling:resourceType="weretail-run/components/content/poster"
                   imageCrop=""
                   imageMap=""
                   imageRotate=""/>
           </image>
       </cq:dropTargets>
   </jcr:root>
   ```

1. Kopiera `image` dialogrutan WCM Foundation som ska användas för `poster` komponenten.

   Det är enklast att börja från en befintlig dialogruta och sedan göra ändringar.

   1. Kopiera dialogrutan från: `/libs/wcm/foundation/components/image/cq:dialog`
   1. Klistra in dialogrutan under `/apps/weretail-run/components/content/poster`
   ![Dialogrutan har kopierats från /libs/wcm/foundation/components/image/cq:dialog till /apps/weretail-run/components/content/affisch](assets/2018-05-03_at_4_13pm.png)

   Dialogrutan har kopierats från /libs/wcm/foundation/components/image/cq:dialog till /apps/weretail-run/components/content/affisch

   Skärmkomponenten är `image` supertypad till WCM Foundation- `image` komponenten. Därför ärver komponenten funktioner från båda `poster` programmen. Dialogrutan för förhandsgranskningskomponenten består av en kombination av dialogrutorna Skärmar och Foundation. Funktionerna i **Sling Resource Merger** används för att dölja irrelevanta dialogrutefält och flikar som ärvs från de överordnade komponenterna.

1. Uppdatera cq:dialog under `/apps/weretail-run/components/content/poster` med följande ändringar representerade i XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Poster"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout
               jcr:primaryType="nt:unstructured"
               sling:resourceType="granite/ui/components/foundation/layouts/tabs"
               type="nav"/>
           <items jcr:primaryType="nt:unstructured">
               <image
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Elements"
                   sling:resourceType="granite/ui/components/foundation/section">
                   <layout
                       jcr:primaryType="nt:unstructured"
                       sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
                       margin="{Boolean}false"/>
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/foundation/container">
                           <items
                               jcr:primaryType="nt:unstructured"
                               sling:hideChildren="[linkURL,size]">
                               <file
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="cq/gui/components/authoring/dialog/fileupload"
                                   autoStart="{Boolean}false"
                                   class="cq-droptarget"
                                   fieldLabel="Image asset"
                                   fileNameParameter="./fileName"
                                   fileReferenceParameter="./fileReference"
                                   mimeTypes="[image]"
                                   multiple="{Boolean}false"
                                   name="./file"
                                   title="Upload Image Asset"
                                   uploadUrl="${suffix.path}"
                                   useHTML5="{Boolean}true"/>
                               <title
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textfield"
                                   fieldLabel="Title"
                                   name="./jcr:title"/>
                               <description
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textarea"
                                   fieldLabel="Description"
                                   name="./jcr:description"/>
                               <position
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Position"
                                   name="./textPosition">
                                   <items jcr:primaryType="nt:unstructured">
                                       <left
                                           jcr:primaryType="nt:unstructured"
                                           text="Left"
                                           value="left"/>
                                       <center
                                           jcr:primaryType="nt:unstructured"
                                           text="Center"
                                           value="center"/>
                                       <right
                                           jcr:primaryType="nt:unstructured"
                                           text="Right"
                                           value="right"/>
                                   </items>
                               </position>
                               <color
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Color"
                                   name="./textColor">
                                   <items jcr:primaryType="nt:unstructured">
                                       <light
                                           jcr:primaryType="nt:unstructured"
                                           text="Light"
                                           value="light"/>
                                       <dark
                                           jcr:primaryType="nt:unstructured"
                                           text="Dark"
                                           value="dark"/>
                                   </items>
                               </color>
                           </items>
                       </column>
                   </items>
               </image>
               <accessibility
                   jcr:primaryType="nt:unstructured"
                   sling:hideResource="{Boolean}true"/>
           </items>
       </content>
   </jcr:root>
   ```

   Egenskapen `sling:hideChildren`= `"[linkURL,size]`&quot; används på `items` noden för att säkerställa att fälten **linkURL** och **size** döljs i dialogrutan. Det räcker inte att ta bort de här noderna från förhandsgranskningsdialogrutan. Egenskapen `sling:hideResource="{Boolean}true"` på fliken Tillgänglighet används för att dölja hela fliken.

   Två markeringsfält läggs till i dialogrutan så att författarna kan styra textpositionen och färgen för titeln och beskrivningen.

   ![Affisch - Slutlig dialogstruktur](assets/2018-05-03_at_4_49pm.png)

   Affisch - Slutlig dialogstruktur

   I det här skedet kan en instans av `poster` komponenten läggas till på sidan **Inaktiv kanal** i projektet We.Retail Run: `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![Dialogrutefält för förhandsgranskning](assets/poster-dialog-full.png)

   Dialogrutefält för förhandsgranskning

1. Skapa en fil med `/apps/weretail-run/components/content/poster` namnet under `production.html.`

   Fyll filen med följande:

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/production.html
   
   */-->
   <div data-sly-use.image="image.js"
        data-duration="${properties.duration}"
        class="cmp-poster"
        style="background-image: url(${request.contextPath @ context='uri'}${image.src @ context='uri'});">
       <div class="cmp-poster__text
                   cmp-poster__text--${properties.textPosition @ context='attribute'}
                   cmp-poster__text--${properties.textColor @ context='attribute'}">
           <h1 class="cmp-poster__title">${properties.jcr:title}</h1>
            <h2 class="cmp-poster__description">${properties.jcr:description}</h2>
       </div>
    <img class="cmp-poster__logo" src="/content/dam/we-retail-run/logos/we-retail-run_dark.png" alt="we-retail-logo" />
   </div>
   ```

   Ovanför är produktionsmarkeringen för Poster Component. HTML-skriptet åsidosätter `screens/core/components/content/image/production.html`. Det `image.js` är ett skript på servern som skapar ett POJO-liknande bildobjekt. Bildobjektet kan sedan anropas för att återge bilden `src` som en bakgrundsbild i textformat.

   `The h1` och h2-taggar läggs till visar titel och beskrivning baserat på komponentegenskaperna: `${properties.jcr:title}` och `${properties.jcr:description}`.

   Omgivande `h1` - och `h2` -taggar är en div-wrapper med tre CSS-klasser med variationer av&quot; `cmp-poster__text`&quot;. Värdet för egenskaperna `textPosition` och `textColor` används för att ändra CSS-klassen som återges baserat på författarens dialogruteval. I nästa avsnitt skrivs CSS från klientbibliotek för att aktivera dessa ändringar i visningen.

   En logotyp ingår också som ett överlägg i komponenten. I det här exemplet är sökvägen till logotypen We.Retail hårdkodad i DAM. Beroende på användningsfallet kan det vara mer praktiskt att skapa ett nytt dialogfält för att göra logotypsökvägen till ett dynamiskt ifyllt värde.

   Observera också att BEM-notation (Block Element Modifier) används med komponenten. BEM är en CSS-kodkonvention som gör det enklare att skapa återanvändbara komponenter. BEM är den syntax som används av [AEM:s kärnkomponenter](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions). Mer information finns här: [https://getbem.com/](https://getbem.com/)

1. Skapa en fil med `/apps/weretail-run/components/content/poster` namnet under `edit.html.`

   Fyll filen med följande:

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/edit.html
   
   */-->
   
   <div class="aem-Screens-editWrapper ${image.cssClass} cmp-poster" data-sly-use.image="image.js" data-emptytext="${'Poster' @ i18n, locale=request.locale}">
       <img class="cmp-poster__image" src="${request.contextPath}${image.src @ context='uri'}" width="100%" />
       <div class="cmp-poster__text
              cmp-poster__text--${properties.textPosition @ context='attribute'}
          cmp-poster__text--${properties.textColor @ context='attribute'}">
         <p class="cmp-poster__title">${properties.jcr:title}</p>
         <p class="cmp-poster__description">${properties.jcr:description}</p>
       </div>
   </div>
   ```

   Ovanför är **redigeringskoden** för filmminiatyrkomponenten. HTML-skriptet åsidosätter `/libs/screens/core/components/content/image/edit.html`. Koden liknar `production.html` koden och visar titeln och beskrivningen ovanpå bilden.

   Komponenten `aem-Screens-editWrapper`läggs till så att den inte återger helskärm i redigeraren. Attributet `data-emptytext` ser till att platshållaren visas när ingen bild eller inget innehåll har fyllts i.

## Skapa bibliotek på klientsidan {#clientlibs}

Med klientbibliotek kan du ordna och hantera CSS- och JavaScript-filer som behövs för en AEM-implementering. Mer information om hur du använder [klientbibliotek finns här.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

AEM-skärmar-komponenter återges annorlunda i redigeringsläge jämfört med förhandsgransknings-/produktionsläge. Två uppsättningar klientbibliotek skapas, en för redigeringsläget och en andra för Förhandsvisa/Produktion.

1. Skapa en mapp för klientbibliotek för komponenten Poster.

   Skapa `/apps/weretail-run/components/content/poster,`en ny mapp med namnet `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. Under `clientlibs` mappen skapar du en ny nod med namnet `shared` av typen `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. Lägg till följande egenskaper i det delade klientbiblioteket:

   * `allowProxy` | Boolesk | `true`
   * `categories` | Sträng[] | `cq.screens.components`
   ![Egenskaper för /apps/weretail-run/components/content/affisch/clientlibs/shared](assets/2018-05-03_at_1026pm-1.png)

   Egenskaper för /apps/weretail-run/components/content/affisch/clientlibs/shared

   Egenskapen `categories` är en sträng som identifierar klientbiblioteket. Kategorin används `cq.screens.components` i både redigeringsläge och förhandsgransknings-/produktionsläge. Därför läses alla CSS/JS som definierats i `shared` clientlib in i alla lägen.

   Det är en god vana att aldrig visa några sökvägar direkt för /apps i en produktionsmiljö. Egenskapen ser till `allowProxy` att klientbibliotekets CSS och JS refereras via ett prefix till `/etc.clientlibs`. Mer information om egenskapen [allowProxy finns här.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. Skapa en fil med namnet `css.txt` under den delade mappen.

   Fyll filen med följande:

   ```
   #base=css
   
   styles.less
   ```

1. Skapa en mapp med namnet `css` under `shared` mappen. Lägg till en fil med namnet `style.less` under `css` mappen. Klientbibliotekens struktur bör nu se ut så här:

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   I stället för att skriva CSS direkt använder den här självstudien LESS. [LESS](https://lesscss.org/) är en populär CSS-förkompilator som stöder CSS-variabler, mixiner och funktioner. AEM-klientbibliotek stöder LESS-kompilering. Sass eller andra förkompilerare kan användas men måste kompileras utanför AEM.

1. Fyll `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` med följande:

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster Component - Shared Style
   */
   
   @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Open+Sans:400i');
   
   @text-light-color: #fff;
   @text-dark-color: #000;
   @title-font-family: 'Fjalla One', sans-serif;
   @description-font-family: 'Open Sans', sans-serif;
   
   .cmp-poster {
   
         &__text {
         position: absolute;
         color: @text-light-color;
         top: 0;
         text-align:center;
         width: 100%;
   
         &--left {
          text-align: left;
                margin-left: 1em;
         }
   
         &--right {
          text-align: right;
                margin-right: 1em;
         }
   
         &--dark {
          color: @text-dark-color;
         }
       }
   
       &__title {
         font-weight: bold;
            font-family: @title-font-family;
            font-size: 1.2em;
       }
   
       &__description {
     font-style: italic;
           font-family: @description-font-family;
    }
   
   }
   ```

   >[!NOTE]
   >
   >Google-webbteckensnitt används för teckensnittsfamiljer. Webbteckensnitt kräver internetanslutning och inte alla skärmimplementeringar är tillförlitliga. Planering för offlineläge är en viktig faktor för skärmdistributioner.

1. Kopiera biblioteksmappen för `shared` klienten. Klistra in det som ett jämlikhetsobjekt och byt namn på det till `production`.

   ![2018-05-03_at_114pm](assets/2018-05-03_at_1114pm.png)

1. Uppdatera egenskapen `categories` för produktionsklientbiblioteket som ska `cq.screens.components.production.`

   Med den här `cq.screens.components.production` kategorin kan du vara säker på att formaten bara läses in i förhandsvisnings-/produktionsläge.

   ![Egenskaper för /apps/weretail-run/components/content/affisch/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Egenskaper för /apps/weretail-run/components/content/affisch/clientlibs/production

1. Fyll `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` med följande:

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster Component - Production Style
   */
   
   .cmp-poster {
   
       background-size: cover;
    height: 100%;
    width: 100%;
    position:absolute;
   
        &__text {
   
           top: 2em;
   
           &--left {
               width: 40%;
               top: 5em;
           }
   
           &--right {
               width: 40%;
               right: 1em;
           }
       }
   
       &__title {
     font-size: 5rem;
     font-weight: 900;
     margin: 0.1rem;
    }
   
    &__description {
     font-size: 2rem;
     margin: 0.1rem;
     font-weight: 400;
   
    }
   
       &__logo {
     position: absolute;
     max-width: 200px;
     top: 1em;
     left: 0;
    }
   
   }
   ```

   Ovanstående format visar rubriken och beskrivningen på en absolut plats på skärmen. Titeln visas som betydligt större än beskrivningen. Komponentens BEM-notation gör det mycket enkelt att noggrant omforma formningarna inom klassen cmp-affisch.

En tredje klientbibliotekskategori: kan `cq.screens.components.edit` användas för att lägga till Redigera endast specifika format i komponenten.

| Kategorin Clientlib | Användning |
|---|---|
| `cq.screens.components` | Format och skript som delas mellan redigerings- och produktionslägen |
| `cq.screens.components.edit` | Format och skript som endast används i redigeringsläge |
| `cq.screens.components.production` | Format och skript som endast används i produktionsläge |

## Lägg till filmminiatyrkomponent i en sekvenskanal {#add-sequence-channel}

Poster-komponenten är avsedd att användas på en sekvenskanal. Startpaketet för kursen innehöll en inaktivitetskanal. Inaktivitetskanalen är förkonfigurerad för att tillåta komponenter i gruppen **We.Retail Run - Content**. Poster-komponentens grupp är inställd på `We.Retail Run - Content` och tillgänglig för att läggas till i kanalen.

1. Öppna Idle Channel från projektet We.Retail Run: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. Dra och släpp en ny instans av **filmminiatyrkomponenten** från sidlisten på sidan.

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. Redigera dialogrutan för förhandsgranskningskomponenten för att lägga till en bild, titel, beskrivning. Använd alternativen Textplacering och Textfärg för att säkerställa att titeln/beskrivningen kan läsas över bilden.

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. Upprepa stegen ovan om du vill lägga till några Poster-komponenter. Lägg till övergångar mellan komponenterna.

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## Sammanställ allt {#putting-it-all-together}

I videon nedan visas den färdiga komponenten och hur den kan läggas till i en sekvenskanal. Kanalen läggs sedan till i en platsvisning och tilldelas till en skärmspelare.

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## Kod klar {#finished-code}

Nedan visas den färdiga koden från självstudiekursen. screens-weretail-run.ui.ap **ps-0.0.1-SNAPSHOT.zip** och **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** är de kompilerade AEM-paketen. **SRC-screens-weretail-run-0.0.1.zip **är den okompilerade källkoden som kan distribueras med Maven.

[Hämta fil](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[Hämta fil](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC Final Screens We.Retail Run Project

[Hämta fil](assets/src-screens-weretail-run-001.zip)
