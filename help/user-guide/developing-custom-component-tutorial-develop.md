---
title: Utveckla en anpassad komponent för AEM Screens
description: Lär dig skapa en anpassad komponent för AEM Screens.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: d14f8c55-dc09-4ac9-8d75-bafffa82ccc0
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '2161'
ht-degree: 0%

---

# Utveckla en anpassad komponent för AEM Screens {#developing-a-custom-component-for-aem-screens}

I följande självstudiekurs går du igenom stegen för att skapa en anpassad komponent för AEM Screens. AEM Screens återanvänder många befintliga designmönster och tekniker från andra AEM produkter. I självstudiekursen beskrivs skillnader och speciella överväganden när du utvecklar för AEM Screens.

## Ökning {#overview}

Den här självstudiekursen är avsedd för utvecklare som inte har använt AEM Screens tidigare. I den här självstudiekursen är en enkel Hello World-komponent byggd för en Sequence-kanal i AEM Screens. I en dialogruta kan författare uppdatera den visade texten.

![overviewhellow](assets/overviewhellow.png)

## Förutsättningar {#prerequisites}

För att slutföra den här självstudiekursen behöver du följande:

1. [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/release-notes) plus det senaste Screens-funktionspaketet.

1. [AEM Screens Player](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction)
1. Lokal utvecklingsmiljö

Självstudiestegen och skärmbilderna utförs med **CRXDE-Lite**. IDE kan också användas för att slutföra självstudiekursen. Mer information om hur du använder en IDE för att utveckla [med AEM finns här.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup)


## Projektinställningar {#project-setup}

Ett Screens-projekts källkod hanteras vanligtvis som ett Maven-projekt med flera moduler. För att underlätta självstudiekursen har ett projekt förskapats med [AEM Project Archetype 13](https://github.com/adobe/aem-project-archetype). Mer information om att [skapa ett projekt med Maven AEM Project Archetype finns här](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup).

1. Hämta och installera följande paket med [CRX Package Manager](http://localhost:4502/crx/packmgr/index.jsp):

[Hämta fil](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [Hämta fil](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **Om du vill** hämtar du källpaketet nedan om du arbetar med Eclipse eller någon annan IDE. Distribuera projektet till en lokal AEM med kommandot Maven:

   **`mvn -PautoInstallPackage clean install`**

   Starta HelloWorld SRC Screens `We.Retail` Kör projekt.

[Hämta fil](assets/src-screens-weretail-run.zip)

1. Kontrollera att följande två paket är installerade i [CRX Package Manager](http://localhost:4502/crx/packmgr/index.jsp):

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Screens Web.Retail Kör Ui.Apps och Ui.Content-paket som installeras med CRX Package Manager](assets/crx-packages.png)

   Screens `We.Retail` Kör `Ui.Apps`- och `Ui.Content`-paket som installeras med CRX Package Manager.

1. Paketet **screens-weretail-run.ui.apps** installerar kod under `/apps/weretail-run`.

   Det här paketet innehåller koden som ansvarar för att återge anpassade komponenter för projektet. Paketet innehåller komponentkod och eventuell JavaScript eller CSS som behövs. Det här paketet bäddar även in **screens-weretail-run.core-0.0.1-SNAPSHOT.jar** som innehåller all Java™-kod som krävs för projektet.

   >[!NOTE]
   >
   >I den här självstudiekursen skrivs ingen Java™-kod. Om mer komplex affärslogik behövs kan back-end Java™ skapas och driftsättas med Core Java™-paketet.

   ![Representation of the ui.apps code in CRXDE Lite](assets/uipps-contents.png)

   Representation av ui.apps-koden i CRXDE Lite

   Komponenten **Hello World** är bara en platshållare. Under kursen har funktioner lagts till som gör att en författare kan uppdatera det meddelande som visas av komponenten.

1. Paketet **screens-weretail-run.ui.content** installerar kod under:

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`

   Det här paketet innehåller det startinnehåll och den konfigurationsstruktur som krävs för projektet. **`/conf/we-retail-run`** innehåller alla konfigurationer för projektet `We.Retail` Run. **`/content/dam/we-retail-run`** innehåller inledande digitala resurser för projektet. **`/content/screens/we-retail-run`** innehåller innehållsstrukturen för Screens. Innehållet i alla dessa sökvägar uppdateras huvudsakligen i AEM. För att främja enhetlighet mellan miljöer (lokal, utvecklare, scen, produktion) sparas ofta en grundinnehållsstruktur i källkontrollen.

1. **Navigera till AEM Screens > `We.Retail` Kör projekt:**

   Klicka på ikonen Screens på AEM Start-meny. Verifiera att körningsprojektet `We.Retail` visas.

   ![we-retaiul-run-starter](assets/we-retaiul-run-starter.png)

## Skapa Hello World-komponenten {#hello-world-cmp}

Hello World-komponenten är en enkel komponent som gör att en användare kan ange ett meddelande som ska visas på skärmen. Komponenten är baserad på [AEM Screens-komponentmallen: https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

AEM Screens har intressanta begränsningar som inte nödvändigtvis är sanna för traditionella WCM-webbplatskomponenter.

* De flesta Screens-komponenter måste köras i helskärmsläge på målenheter för digitala signaturer
* De flesta Screens-komponenter måste kunna bäddas in i sekvenskanalerna för att bildspel ska kunna genereras
* Redigering bör tillåta redigering av enskilda komponenter i en sekvenskanal, så att återgivning av dem i helskärmsläge inte är möjligt

1. I **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (eller valfri IDE) navigerar du till `/apps/weretail-run/components/content/helloworld.`

   Lägg till följande egenskaper i komponenten `helloworld`:

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![Egenskaper för /apps/weretail-run/components/content/helpWorld](assets/2018-04-28_at_4_23pm.png)

   Egenskaper för /apps/weretail-run/components/content/helpWorld

   Komponenten **Hello World** utökar komponenten **grund, komponenter, parbase** så att den kan användas i en sekvenskanal.

1. Skapa en fil under `/apps/weretail-run/components/content/helloworld` med namnet `helloworld.html.`

   Fyll filen med följande:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   Screens-komponenter kräver två olika återgivningar beroende på vilket [redigeringsläge](https://experienceleague.adobe.com/en/docs/experience-manager-64/authoring/authoring/author-environment-tools) som används:

   1. **Produktion**: Förhandsgranska eller Publish-läge (wcmmode=disabled)
   1. **Redigera**: används för alla andra redigeringslägen, t.ex. redigering, design, ställningar, utvecklare...

   `helloworld.html`fungerar som en växel, kontrollerar vilket redigeringsläge som är aktivt och omdirigerar till ett annat HTML-skript. En vanlig konvention som används för skärmkomponenter är att ha ett `edit.html`-skript för redigeringsläget och ett `production.html`-skript för produktionsläget.

1. Skapa en fil under `/apps/weretail-run/components/content/helloworld` med namnet `production.html.`

   Fyll filen med följande:

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   Ovanstående är produktionsmarkeringen för Hello World-komponenten. Ett `data-duration`-attribut ingår eftersom komponenten används i en sekvenskanal. Attributet `data-duration` används av Sequence-kanalen för att ta reda på hur länge ett sekvensobjekt ska visas.

   Komponenten återger en `div`- och en `h1`-tagg med text. `${properties.message}` är en del av HTML-skriptet som matar ut innehållet i en JCR-egenskap med namnet `message`. En dialogruta skapas senare där användaren kan ange ett värde för egenskapstexten `message`.

   Observera också att BEM-notation (Block Element Modifier) används med komponenten. BEM är en CSS-kodkonvention som gör det enklare att skapa återanvändbara komponenter. BEM är den syntax som används av [AEM kärnkomponenter](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. Skapa en fil under `/apps/weretail-run/components/content/helloworld` med namnet `edit.html.`

   Fyll filen med följande:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   Ovanstående är den redigerade koden för Hello World-komponenten. Det första blocket visar en redigerad version av komponenten om dialogmeddelandet har fyllts i.

   Det andra blocket återges om inget dialogrutemeddelande har angetts. `cq-placeholder` och `data-emptytext` återger etiketten ***Hello World*** som platshållare i så fall. Strängen för etiketten kan internationaliseras med i18n som stöd för redigering på flera språk.

1. **Kopiera Screens Image Dialog som ska användas för Hello World-komponenten.**

   Det är enklast att börja från en befintlig dialogruta och sedan göra ändringar.

   1. Kopiera dialogrutan från: `/libs/screens/core/components/content/image/cq:dialog`
   1. Klistra in dialogrutan under `/apps/weretail-run/components/content/helloworld`

   ![copy-image-dialog](assets/copy-image-dialog.gif)

1. **Uppdatera dialogrutan Hello World så att den innehåller en flik för meddelandet.**

   Uppdatera dialogrutan så att den matchar följande. JCR-nodstrukturen i den slutliga dialogrutan presenteras nedan i XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image is shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (milliseconds)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   Textfältet för meddelandet sparas i egenskapen `message` och nummerfältet för Varaktighet sparas i egenskapen `duration`. Dessa två egenskaper refereras båda i `/apps/weretail-run/components/content/helloworld/production.html` av HTML som `${properties.message}` och `${properties.duration}`.

   ![Hello World - slutförd dialogruta](assets/2018-04-29_at_5_21pm.png)

   Hello World - slutförd dialogruta

## Skapa bibliotek på klientsidan {#clientlibs}

Med bibliotek på klientsidan kan du ordna och hantera CSS- och JavaScript-filer som behövs för en AEM implementering.

AEM Screens-komponenter återges annorlunda i redigeringsläget jämfört med i förhandsgranskningsläget. Två klientbibliotek skapas: ett för redigeringsläget och det andra för Preview-Production.

1. Skapa en mapp för klientbibliotek för Hello World-komponenten.

   Skapa en mapp med namnet `clientlibs` under `/apps/weretail-run/components/content/helloworld`.

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. Skapa en nod med namnet `shared` av typen `cq:ClientLibraryFolder` under mappen `clientlibs`.

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. Lägg till följande egenskaper i det delade klientbiblioteket:

   * `allowProxy` | Boolean | `true`

   * `categories`| Sträng [] | `cq.screens.components`

   ![Egenskaper för /apps/weretail-run/components/content/helpWorld/clientlibs/shared](assets/2018-05-03_at_1026pm.png)

   Egenskaper för /apps/weretail-run/components/content/helpWorld/clientlibs/shared

   Egenskapen categories är en sträng som identifierar klientbiblioteket. Kategorin cq.screens.component används i både Edit- och Preview-Production-läge. Därför läses alla CSS- och JS-format som definieras i SharedClientlib in i alla lägen.

   Som en god praxis bör sökvägar som är direkt till `/apps` i en produktionsmiljö aldrig exponeras. Egenskapen allowProxy ser till att klientbibliotekets CSS och JS refereras via prefixet `/etc.clientlibs`.

1. Skapa filen `css.txt` under den delade mappen.

   Fyll filen med följande:

   ```
   #base=css
   
   styles.less
   ```

1. Skapa en mapp med namnet `css` under mappen `shared`. Lägg till filen `style.less` under mappen `css`. Klientbibliotekens struktur bör nu se ut så här:

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   I stället för att skriva CSS direkt använder den här självstudien LESS. [LESS](https://lesscss.org/) är en populär CSS-förkompilator som stöder CSS-variabler, mixins och funktioner. AEM klientbibliotek stöder LESS-kompilering. Sass eller andra förkompilatorer kan användas men måste kompileras utanför AEM.

1. Fyll i `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` med följande:

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. Kopiera och klistra in klientbiblioteksmappen `shared` för att skapa ett klientbibliotek med namnet `production`.

   ![Kopiera det delade klientbiblioteket och skapa ett nytt produktionsklientbibliotek](assets/copy-clientlib.gif)

   Kopiera det delade klientbiblioteket för att skapa ett produktionsklientbibliotek.

1. Uppdatera egenskapen `categories` för produktionsklientbiblioteket till `cq.screens.components.production.`

   Om du gör det ser du till att formaten bara läses in i läget Förhandsvisa/producera.

   ![Egenskaper för /apps/weretail-run/components/content/helpWorld/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Egenskaper för `/apps/weretail-run/components/content/helloworld/clientlibs/production`.

1. Fyll i `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` med följande:

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   Ovanstående format visar meddelandet centrerat mitt på skärmen, men endast i produktionsläge.

En tredje klientbibliotekskategori: `cq.screens.components.edit` kan användas för att lägga till redigeringsspecifika format i komponenten.

| Kategorin Clientlib | Användning |
|---|---|
| `cq.screens.components` | Format och skript som delas mellan redigerings- och produktionslägen |
| `cq.screens.components.edit` | Format och skript som endast används i redigeringsläge |
| `cq.screens.components.production` | Format och skript som endast används i produktionsläge |

## Skapa en designsida {#design-page}

AEM Screens använder [statiska sidmallar](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-static) och [designkonfigurationer](https://experienceleague.adobe.com/en/docs/experience-manager-64/authoring/siteandpage/default-components-designmode) för globala ändringar. Designkonfigurationer används ofta för att konfigurera tillåtna komponenter för parsys i en kanal. Ett tips är att lagra dessa konfigurationer på ett appspecifikt sätt.

Under sidan `We.Retail` Run Design skapas en sida som lagrar alla konfigurationer som är specifika för projektet `We.Retail` Run.

1. Navigera till `/apps/settings/wcm/designs` i **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs`.
1. Skapa en nod under designmappen med namnet `we-retail-run` och typen `cq:Page`.
1. Under sidan `we-retail-run` lägger du till en annan nod med namnet `jcr:content` av typen `nt:unstructured`. Lägg till följande egenskaper i noden `jcr:content`:

   | Namn | Typ | Värde |
   |---|---|---|
   | `jcr:title` | Sträng | Kör `We.Retail` |
   | `sling:resourceType` | Sträng | `wcm`, `core`, `components`, `designer` |
   | `cq:doctype` | Sträng | html_5 |

   ![Designsida på /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1219pm.png)

   Designsida på `/apps/settings/wcm/designs/we-retail-run`.

## Skapa en sekvenskanal {#create-sequence-channel}

Komponenten Hello World är till för användning i en sekvenskanal. Om du vill testa komponenten skapas en ny sekvenskanal.

1. Gå till **Screens** > **`We.Retail`Kör** > och klicka på **Kanaler** på AEM Start-meny.

1. Klicka på knappen **Skapa**

   1. Välj **Skapa entitet**

   ![2018-04-30_at_5_18pm](assets/2018-04-30_at_5_18pm.png)

1. I guiden Skapa:

1. Mallsteg - välj **Sekvenskanal**

   1. Egenskapssteg

   * Fliken Grundläggande > Titel = **Inaktiv kanal**
   * Fliken Kanal > kontrollera **Gör kanalen online**

   ![inaktiv kanal](assets/idle-channel.gif)

1. Öppna sidegenskaperna för inaktivitetskanalen.
1. Uppdatera designfältet så att det pekar på `/apps/settings/wcm/designs/we-retail-run`, designsidan som skapades i föregående avsnitt.

   ![Designkonfiguration /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   Designkonfiguration som pekar på /apps/settings/wcm/designs/we-retail-run

1. Redigera den nya inaktivitetskanalen så att du kan öppna den.

1. Växla sidläge till **designläge**.

   1. Klicka på ikonen **wrench** i Parsys så att du kan konfigurera de tillåtna komponenterna.

   1. Klicka på gruppen **Screens** och gruppen **`We.Retail`Kör - innehåll** .

   ![2018-04-30_at_5_43pm](assets/2018-04-30_at_5_43pm.png)

1. Växla sidläge till **Redigera**. Komponenten Hello World kan nu läggas till på sidan och kombineras med andra Sequence Channel-komponenter.

   ![2018-04-30_at_5_53pm](assets/2018-04-30_at_5_53pm.png)

1. Navigera till `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par` i **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par`. Observera att egenskapen `components` nu innehåller `group:Screens`, `group:We.Retail Run - Content`.

   ![Designkonfiguration under /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1_14pm.png)

   Designkonfiguration under /apps/settings/wcm/designs/we-retail-run

## Mall för anpassade hanterare {#custom-handlers}

Om din anpassade komponent använder externa resurser som resurser (bilder, videoklipp, teckensnitt och ikoner), specifika resursåtergivningar eller klientbibliotek (css och js), läggs dessa resurser inte automatiskt till i offlinekonfigurationen. Orsaken är att endast markeringen HTML paketeras som standard.

För att du ska kunna anpassa och optimera de exakta resurserna som hämtas till spelaren har Adobe en tilläggsfunktion. Den här mekanismen används för att anpassade komponenter ska kunna visa sina beroenden för offlinecachelagringslogiken i AEM Screens.

I avsnittet nedan visas mallen för anpassade offline-resurshanterare. Den visar också minimikraven i `pom.xml` för det specifika projektet.

```java
package …;

import javax.annotation.Nonnull;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceUtil;
import org.apache.sling.api.resource.ValueMap;

import com.adobe.cq.screens.visitor.OfflineResourceHandler;

@Service(value = OfflineResourceHandler.class)
@Component(immediate = true)
public class MyCustomHandler extends AbstractResourceHandler {

 @Reference
 private …; // OSGi services injection

 /**
  * The resource types that are handled by the handler.
  * @return the handled resource types
  */
 @Nonnull
 @Override
 public String[] getSupportedResourceTypes() {
     return new String[] { … };
 }

 /**
  * Accept the provided resource, visit and traverse it as needed.
  * @param resource The resource to accept
  */
 @Override
 public void accept(@Nonnull Resource resource) {
     ValueMap properties = ResourceUtil.getValueMap(resource);
     
     /* You can directly add explicit paths for offline caching using the `visit`
        method of the visitor. */
     
     // retrieve a custom property from the component
     String myCustomRenditionUrl = properties.get("myCustomRenditionUrl", String.class);
     // adding that exact asset/rendition/path to the offline manifest
     this.visitor.visit(myCustomRenditionUrl);
     
     
     /* You can delegate handling for dependent resources so they are also added to
        the offline cache using the `accept` method of the visitor. */
     
     // retrieve a referenced dependent resource
     String referencedResourcePath = properties.get("myOtherResource", String.class);
     ResourceResolver resolver = resource.getResourceResolver();
     Resource referencedResource = resolver.getResource(referencedResourcePath);
     // let the handler for that resource handle it
     if (referencedResource != null) {
         this.visitor.accept(referencedResource);
     }
   }
}
```

Följande kod innehåller minimikraven i `pom.xml` för det specifika projektet:

```css
   <dependencies>
        …
        <!-- Felix annotations -->
        <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr.annotations</artifactId>
            <version>1.9.0</version>
            <scope>provided</scope>
        </dependency>

        <!-- Screens core bundle with OfflineResourceHandler/AbstractResourceHandler -->
        <dependency>
            <groupId>com.adobe.cq.screens</groupId>
            <artifactId>com.adobe.cq.screens</artifactId>
            <version>1.5.90</version>
            <scope>provided</scope>
        </dependency>
        …
      </dependencies>
```

**Obs!** Om det finns AEM as a Cloud Service använder du beroendet nedan i `pom.xml` för det specifika projektet.

```css
   <dependencies>
        …
        <!-- AEM Screens SDK API with OfflineResourceHandler/AbstractResourceHandler -->
        <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-screens-sdk-api</artifactId>
            <version>1.0.8</version>
        </dependency>
        …
      </dependencies>
```

## Sammanställ allt {#putting-it-all-together}

I videon nedan visas den färdiga komponenten och hur den kan läggas till i en sekvenskanal. Kanalen läggs sedan till i en platsvisning och tilldelas till en Screens-spelare.

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9)

## Andra överväganden för anpassade komponenter som bäddar in andra sidor eller fragment {#additional-considerations}

Om din anpassade komponent är avsedd att innehålla andra sidor eller Experience Fragments, och du vill att ändringar i det inbäddade innehållet automatiskt ska hämtas av spelaren - utan att kanalen behöver publiceras om - bör du överväga följande två begränsningar:

1. I stället för att utöka `foundation/components/parbase` direkt måste du utöka antingen `screens/core/components/content/page` eller `screens/core/components/content/experiencefragment`
2. Namnet på egenskapen som du använder för att referera till det inbäddade innehållet måste vara `pagePath`.

När du använder dessa två Screens kärnkomponenter får du dessutom en fördel av att de kan hantera alla beroenden du behöver (bibliotek på klientsidan, teckensnitt osv.). Den här funktionen görs med hjälp av deras offlinekonfigurationsalternativ i komponentdialogrutan. Sedan minskar det ansvaret för alla anpassade offlinehanterare som du skulle behöva använda för den. Det kan ibland till och med helt ta bort behovet av att använda en från början.

## Kod klar {#finished-code}

Nedan visas den färdiga koden från självstudiekursen. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** och **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** är de kompilerade AEM. **SRC-screens-weretail-run-0.0.1.zip &#x200B;** är den okompilerade källkoden som kan distribueras med Maven.

[Hämta fil](assets/screens-weretail-runuiapps-001-snapshot.zip)

[Hämta fil](assets/screens-weretail-runuicontent-001-snapshot.zip)

[Hämta fil](assets/screens-weretail-run.zip)
