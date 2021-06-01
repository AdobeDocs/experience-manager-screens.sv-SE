---
title: Utöka en AEM Screens-komponent
seo-title: Utöka en AEM Screens-komponent
description: I följande självstudiekurs går du igenom de olika stegen och de bästa sätten att utöka AEM Screens-komponenterna direkt. Bildkomponenten utökas för att lägga till en redigerbar textövertäckning.
seo-description: I följande självstudiekurs går du igenom de olika stegen och de bästa sätten att utöka AEM Screens-komponenterna direkt. Bildkomponenten utökas för att lägga till en redigerbar textövertäckning.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: Utveckla skärmar
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1854'
ht-degree: 0%

---


# Utöka en AEM Screens-komponent {#extending-an-aem-screens-component}

I följande självstudiekurs går du igenom de olika stegen och de bästa sätten att utöka AEM Screens-komponenterna direkt. Bildkomponenten utökas för att lägga till en redigerbar textövertäckning.

## Översikt {#overview}

Den här självstudiekursen är avsedd för utvecklare som inte har använt AEM Screens tidigare. I den här självstudiekursen utökas komponenten Skärmbild för att skapa en Poster-komponent. En titel, beskrivning och logotyp läggs ovanpå en bild för att skapa en övertygande upplevelse i en sekvenskanal.

>[!NOTE]
>
>Innan du startar den här självstudiekursen rekommenderar vi att du slutför självstudiekursen: [Utveckla en anpassad komponent för AEM Screens](developing-custom-component-tutorial-develop.md).

![Egen förhandsgranskningskomponent](assets/2018-05-07_at_4_09pm.png)

En anpassad filmminiatyrkomponent skapas genom att bildkomponenten utökas.

## Förutsättningar {#prerequisites}

För att slutföra den här självstudiekursen behöver du följande:

1. [AEM 6.4 ](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/release-notes.html) eller  [AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + Senaste skärmar - funktionspaket
1. [AEM Screens Player](/help/user-guide/aem-screens-introduction.md)
1. Lokal utvecklingsmiljö

Självstudiestegen och skärmbilderna utförs med CRXDE-Lite. [Du kan också använda ](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) Eclipseor  [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) IntelliJIDE för att slutföra självstudiekursen. Mer information om hur du använder en IDE för att [utveckla med AEM finns här](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide).

## Projektinställningar {#project-setup}

Källkoden för ett skärmsprojekt hanteras vanligtvis som ett Maven-projekt med flera moduler. För att underlätta självstudiekursen har ett projekt förskapats med [AEM Project Archetype 13](https://github.com/adobe/aem-project-archetype). Mer information om hur du skapar ett projekt med Maven AEM Project Archetype finns här](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule).[

1. Hämta och installera följande paket med **CRX-pakethantering** `http://localhost:4502/crx/packmgr/index.jsp)r:`

[Hämta fil](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [Hämta fil](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Om du vill kan du** hämta källpaketet nedan om du arbetar med Eclipse eller någon annan utvecklingsmiljö. Distribuera projektet till en lokal AEM med kommandot Maven:

   **`mvn -PautoInstallPackage clean install`**

   SRC-startskärmar - webb.Kör projekt

[Hämta fil](assets/start-poster-screens-weretail-run.zip)

1. I **CRX Package Manager** `http://localhost:4502/crx/packmgr/index.jsp` är följande två paket installerade:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Skärmar, Web.Retail Kör Ui.Apps och Ui.Innehållspaket som installeras via CRX Package Manager](assets/crx-packages.png)

   Skärmar, Web.Retail Kör Ui.Apps och Ui.Innehållspaket som installeras via CRX Package Manager

## Skapa förhandsgranskningskomponenten {#poster-cmp}

Komponenten Poster utökar bildskärmskomponenten utanför rutan. En Sling-mekanism, `sling:resourceSuperType`, används för att ärva huvudfunktionerna i Image-komponenten utan att behöva kopiera och klistra in. Mer information om grunderna i [Behandling av delningsbegäran finns här.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

Komponenten Poster återges i helskärmsläge i förhandsgransknings-/produktionsläge. I redigeringsläge är det viktigt att återge komponenten på ett annat sätt för att underlätta redigeringen av sekvenskanalen.

1. I **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (eller valfri IDE) under `/apps/weretail-run/components/content`skapar du en ny `cq:Component` med namnet `poster`.

   Lägg till följande egenskaper i `poster`-komponenten:

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

   Genom att ställa in egenskapen `sling:resourceSuperType`på `screens/core/components/content/image` ärver Poster-komponenten alla funktioner i Image-komponenten. Likvärdiga noder och filer som hittas under `screens/core/components/content/image` kan läggas till under `poster`-komponenten för att åsidosätta och utöka funktionaliteten.

1. Kopiera noden `cq:editConfig` under `/libs/screens/core/components/content/image.`Klistra in `cq:editConfig` under komponenten `/apps/weretail-run/components/content/poster`.

   På `cq:editConfig/cq:dropTargets/image/parameters`-noden uppdaterar du egenskapen `sling:resourceType` till lika med `weretail-run/components/content/poster`.

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

1. Kopiera dialogrutan `image` för WCM Foundation som ska användas för komponenten `poster`.

   Det är enklast att börja från en befintlig dialogruta och sedan göra ändringar.

   1. Kopiera dialogrutan från: `/libs/wcm/foundation/components/image/cq:dialog`
   1. Klistra in dialogrutan under `/apps/weretail-run/components/content/poster`

   ![Dialogrutan har kopierats från /libs/wcm/foundation/components/image/cq:dialog till /apps/weretail-run/components/content/affisch](assets/2018-05-03_at_4_13pm.png)

   Dialogrutan har kopierats från /libs/wcm/foundation/components/image/cq:dialog till /apps/weretail-run/components/content/affisch

   Skärmkomponenten `image` är supertypad till WCM Foundation `image`-komponenten. Därför ärver `poster`-komponenten funktioner från båda. Dialogrutan för förhandsgranskningskomponenten består av en kombination av dialogrutorna Skärmar och Foundation. Funktionerna i **Sling Resource Merger** används för att dölja irrelevanta dialogrutefält och flikar som ärvs från de överordnade typkomponenterna.

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

   Egenskapen `sling:hideChildren`= `"[linkURL,size]` används på noden `items` för att säkerställa att fälten **linkURL** och **size** är dolda i dialogrutan. Det räcker inte att ta bort de här noderna från förhandsgranskningsdialogrutan. Egenskapen `sling:hideResource="{Boolean}true"` på fliken Tillgänglighet används för att dölja hela fliken.

   Två markeringsfält läggs till i dialogrutan så att författarna kan styra textpositionen och färgen för titeln och beskrivningen.

   ![Affisch - Slutlig dialogstruktur](assets/2018-05-03_at_4_49pm.png)

   Affisch - Slutlig dialogstruktur

   I det här läget kan en instans av komponenten `poster` läggas till på sidan **Inaktiv kanal** i Web.Retail Run-projektet: `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![Dialogrutefält för förhandsgranskning](assets/poster-dialog-full.png)

   Dialogrutefält för förhandsgranskning

1. Skapa en fil med namnet `production.html.` under `/apps/weretail-run/components/content/poster`

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

   Ovanför är produktionsmarkeringen för Poster Component. HTL-skriptet åsidosätter `screens/core/components/content/image/production.html`. `image.js` är ett serverskript som skapar ett POJO-liknande bildobjekt. Bildobjektet kan sedan anropas för att återge `src` som en bakgrundsbild i infogat format.

   `The h1` och h2-taggar läggs till visar titel och beskrivning baserat på komponentegenskaperna:  `${properties.jcr:title}` och  `${properties.jcr:description}`.

   Omgivande `h1`- och `h2`-taggar är en div-wrapper med tre CSS-klasser med variationer av `cmp-poster__text`. Värdet för egenskaperna `textPosition` och `textColor` används för att ändra CSS-klassen som återges baserat på författarens val i dialogrutan. I nästa avsnitt skrivs CSS från klientbibliotek för att aktivera dessa ändringar i visningen.

   En logotyp ingår också som ett överlägg i komponenten. I det här exemplet är sökvägen till logotypen We.Retail hårdkodad i DAM. Beroende på användningsfallet kan det vara mer praktiskt att skapa ett nytt dialogfält för att göra logotypsökvägen till ett dynamiskt ifyllt värde.

   Observera också att BEM-notation (Block Element Modifier) används med komponenten. BEM är en CSS-kodkonvention som gör det enklare att skapa återanvändbara komponenter. BEM är den syntax som används av [AEM kärnkomponenter](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions). Mer information finns här: [https://getbem.com/](https://getbem.com/)

1. Skapa en fil med namnet `edit.html.` under `/apps/weretail-run/components/content/poster`

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

   Ovanför är koden **edit** för Poster Component. HTL-skriptet åsidosätter `/libs/screens/core/components/content/image/edit.html`. Markeringen liknar `production.html`-koden och visar titeln och beskrivningen ovanpå bilden.

   `aem-Screens-editWrapper`läggs till så att komponenten inte återger helskärmsläge i redigeraren. Attributet `data-emptytext` ser till att platshållaren visas när ingen bild eller inget innehåll har fyllts i.

## Skapa bibliotek på klientsidan {#clientlibs}

Med bibliotek på klientsidan kan du ordna och hantera CSS- och JavaScript-filer som behövs för en AEM implementering. Mer information om hur du använder [klientbibliotek finns här.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

AEM Screens-komponenter återges annorlunda i redigeringsläget jämfört med i förhandsgransknings-/produktionsläget. Två uppsättningar klientbibliotek skapas, en för redigeringsläget och en andra för Förhandsvisa/Produktion.

1. Skapa en mapp för klientbibliotek för komponenten Poster.

   Under `/apps/weretail-run/components/content/poster,`skapar du en ny mapp med namnet `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. Under mappen `clientlibs` skapar du en ny nod med namnet `shared` av typen `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. Lägg till följande egenskaper i det delade klientbiblioteket:

   * `allowProxy` | Boolesk | `true`
   * `categories` | Sträng[] |  `cq.screens.components`

   ![Egenskaper för /apps/weretail-run/components/content/affisch/clientlibs/shared](assets/2018-05-03_at_1026pm-1.png)

   Egenskaper för /apps/weretail-run/components/content/affisch/clientlibs/shared

   Egenskapen `categories` är en sträng som identifierar klientbiblioteket. Kategorin `cq.screens.components` används i både redigeringsläget och läget Förhandsgranska/produktion. Alla CSS/JS som definierats i klientlib `shared` läses därför in i alla lägen.

   Det är en god vana att aldrig visa några sökvägar direkt för /apps i en produktionsmiljö. Egenskapen `allowProxy` ser till att klientbibliotekets CSS och JS refereras via ett prefix på `/etc.clientlibs`. Mer information om egenskapen [allowProxy finns här.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. Skapa filen `css.txt` under den delade mappen.

   Fyll filen med följande:

   ```
   #base=css
   
   styles.less
   ```

1. Skapa en mapp med namnet `css` under mappen `shared`. Lägg till en fil med namnet `style.less` under mappen `css`. Klientbibliotekens struktur bör nu se ut så här:

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   I stället för att skriva CSS direkt använder den här självstudien LESS. [LESS ](https://lesscss.org/) är en populär CSS-förkompilator som stöder CSS-variabler, mixiner och funktioner. AEM klientbibliotek stöder LESS-kompilering. Sass eller andra förkompilatorer kan användas men måste kompileras utanför AEM.

1. Fyll i `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` med följande:

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

1. Kopiera klientbiblioteksmappen `shared`. Klistra in det som ett jämordnat objekt och byt namn på det till `production`.

   ![2018-05-03_at_114pm](assets/2018-05-03_at_1114pm.png)

1. Uppdatera egenskapen `categories` för produktionsklientbiblioteket till `cq.screens.components.production.`

   Kategorin `cq.screens.components.production` säkerställer att formaten bara läses in i förhandsgransknings-/produktionsläge.

   ![Egenskaper för /apps/weretail-run/components/content/affisch/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Egenskaper för /apps/weretail-run/components/content/affisch/clientlibs/production

1. Fyll i `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` med följande:

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

En tredje klientbibliotekskategori: `cq.screens.components.edit` kan användas för att lägga till Redigera endast specifika format i komponenten.

| Kategorin Clientlib | Användning |
|---|---|
| `cq.screens.components` | Format och skript som delas mellan redigerings- och produktionslägen |
| `cq.screens.components.edit` | Format och skript som endast används i redigeringsläge |
| `cq.screens.components.production` | Format och skript som endast används i produktionsläge |

## Lägg till filmminiatyrkomponent i en sekvenskanal {#add-sequence-channel}

Poster-komponenten är avsedd att användas på en sekvenskanal. Startpaketet för kursen innehöll en inaktivitetskanal. Inaktivitetskanalen är förkonfigurerad för att tillåta komponenter i gruppen **Vi.Retail Run - Content**. Poster-komponentens grupp är inställd på `We.Retail Run - Content` och är tillgänglig för att läggas till i kanalen.

1. Öppna Idle Channel från projektet We.Retail Run: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. Dra och släpp en ny instans av komponenten **Poster** från sidofältet till sidan.

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. Redigera dialogrutan för förhandsgranskningskomponenten för att lägga till en bild, titel, beskrivning. Använd alternativen Textplacering och Textfärg för att säkerställa att titeln/beskrivningen kan läsas över bilden.

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. Upprepa stegen ovan om du vill lägga till några Poster-komponenter. Lägg till övergångar mellan komponenterna.

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## Samla allt {#putting-it-all-together}

I videon nedan visas den färdiga komponenten och hur den kan läggas till i en sekvenskanal. Kanalen läggs sedan till i en platsvisning och tilldelas till en skärmspelare.

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## Kod {#finished-code} slutförd

Nedan visas den färdiga koden från självstudiekursen. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** och **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** är de kompilerade AEM. **SRC-screens-weretail-run-0.0.1.zip **är den okompilerade källkoden som kan distribueras med Maven.

[Hämta fil](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[Hämta fil](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC Final Screens We.Retail Run Project

[Hämta fil](assets/src-screens-weretail-run-001.zip)
