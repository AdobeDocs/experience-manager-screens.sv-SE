---
title: Bädda in ett REACT-program med AEM SPA Editor och Integrera med AEM Screens Analytics
seo-title: Embedding a REACT application using the AEM SPA Editor and Integrating with AEM Screens Analytics
description: Följ den här sidan för att lära dig hur du bäddar in en interaktiv single page-applikation med REACT (eller Angular) med den AEM SPA redigeraren som kan konfigureras av affärsfolk i AEM och även hur du integrerar ditt interaktiva program med Adobe Analytics offline.
seo-description: Follow this page to learn how to embed an interactive single page application using REACT (or Angular) using the AEM SPA editor that can be configured by business professionals in AEM and also how to integrate your interactive application with offline Adobe Analytics.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: ffc44dbf1822ff4d0e875ef693d48dece248d555
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Bädda in ett REACT-program med AEM SPA Editor och Integrera med AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

I det här avsnittet beskrivs hur du bäddar in en interaktiv single page-applikation med hjälp av REACT (eller Angular) med AEM redigerare som kan konfigureras av affärsfolk i AEM och hur du integrerar dina interaktiva applikationer med Adobe Analytics offline.

## Använda AEM SPA Editor {#using-the-aem-spa-editor}

Följ stegen nedan för att använda AEM SPA Editor:

1. Klona AEM SPA Editor-rapporten på [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Denna arkityp skapar ett minimalt Adobe Experience Manager-projekt som utgångspunkt för dina egna SPA. De egenskaper som måste anges när den här typen av arkivtyp används gör att du kan namnge alla delar av projektet som du vill.

1. Följ Viktigt-instruktionerna för att skapa ett projekt av typen AEM SPA editor:

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >Vi använder **GroupId** as ***com.adobe.aem.screens*** och **ArtifactId** as ***Mitt SPA*** (som är standard). Du kan välja egna efter behov.

1. När projektet har skapats kan du antingen använda en utvecklingsmiljö eller en redigerare och importera det genererade Maven-projektet.
1. Distribuera till den lokala AEM med kommandot ***mvn clean install -PautoInstallPackage***.

### Redigera innehåll i REACT-appen {#editing-content-in-the-react-app}

Så här redigerar du innehållet i REACT-appen:

1. Navigera till `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (ersätt värdnamnet, porten och projektnamnet efter behov).
1. Du bör kunna redigera texten som visas i Hello world-programmet.

### Lägga till den interaktiva REACT-appen i AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Följ stegen nedan för att lägga till den interaktiva REACT-appen i AEM Screens:

1. Skapa ett nytt AEM Screens-projekt. Se [Skapa och hantera projekt](creating-a-screens-project.md) för mer information.

1. Skapa ett nytt **Programkanal** (helst) (eller 1x1-mall eller flerzonskanal) i **Kanaler** i Screens-projektet.

   >[!NOTE]
   >**Sekvenskanaler** är inte lämpliga att använda eftersom de i sig har en bildspelslogik som kan skapa en konflikt med upplevelsens interaktiva karaktär
   >Se [Skapa och hantera kanaler](managing-channels.md) för mer information.


1. Redigera valfri sekvenskanal och dra och släpp en inbäddad sidkomponent.

   Se [Lägga till komponenter i en kanal](adding-components-to-a-channel.md) för mer information.

   >[!NOTE]
   >
   >Se till att du lägger till användarinteraktionshändelsen när du tilldelar kanalen till visningen.

1. Klicka på **Redigera** i åtgärdsfältet för att redigera kanalens egenskaper.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Dra och släpp **Inbäddad sida** eller återanvända den befintliga komponenten i en programkanal, och välj startsidan under mysamplespa-programmet, till exempel ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at10104am](assets/screen_shot_2019-02-15at101104am.png)

1. Tilldela kanalen till en skärm.

   >[!NOTE]
   >Se till att du lägger till användarinteraktionshändelsen när du tilldelar kanalen till visningen.

1. Registrera en spelare för det här projektet och tilldela den till visningen. Nu bör du kunna se hur ditt interaktiva program körs på AEM Screens.

   Se [Enhetsregistrering](device-registration.md) om du vill lära dig mer om hur du registrerar en enhet.

## Integrera SPA med Adobe Analytics med offlinefunktioner via AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Följ stegen nedan för att integrera SPA med Adobe Analytics med offlinefunktioner via AEM Screens:

1. Konfigurera Adobe Analytics i AEM Screens.

   Se [Konfigurera Adobe Analytics med AEM Screens](configuring-adobe-analytics-aem-screens.md) om du vill veta hur du utför sekvensering i Adobe Analytics med AEM Screens och skickar anpassade händelser med Adobe Analytics offline.

1. Redigera din reaktionsapp i den utvecklingsmiljö/redigerare du väljer (särskilt textkomponenten eller någon annan komponent som du vill börja skicka händelser för).
1. Lägg till analysinformationen med standarddatamodellen i klickhändelsen eller i någon annan händelse som du vill hämta för komponenten.

   Se [Konfigurera Adobe Analytics med AEM Screens](configuring-adobe-analytics-aem-screens.md)s för mer information.

1. Anropa AEM Screens Analytics API för att spara händelsen offline och skicka den i bursts till Adobe Analytics.

   Till exempel,

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >Den inbyggda spelarprogramvaran lägger automatiskt till mer information om spelaren och dess körningsmiljö till de anpassade analysdata som du skickar. Därför behöver du kanske inte hämta information om operativsystem/enheter på låg nivå, såvida det inte är absolut nödvändigt. Ni behöver bara fokusera på affärsanalysdata.
