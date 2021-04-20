---
title: Bädda in ett REACT-program med AEM SPA Editor och Integrera med AEM Screens Analytics
seo-title: Bädda in ett REACT-program med AEM SPA Editor och Integrera med AEM Screens Analytics
description: Följ den här sidan för att lära dig hur du bäddar in en interaktiv single page-applikation med REACT (eller Angular) med den AEM SPA redigeraren som kan konfigureras av affärsfolk i AEM och även hur du integrerar ditt interaktiva program med Adobe Analytics offline.
seo-description: Följ den här sidan för att lära dig hur du bäddar in en interaktiv single page-applikation med REACT (eller Angular) med den AEM SPA redigeraren som kan konfigureras av affärsfolk i AEM och även hur du integrerar ditt interaktiva program med Adobe Analytics offline.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---


# Bädda in ett REACT-program med AEM SPA Editor och Integrera med AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

I det här avsnittet beskrivs hur du bäddar in en interaktiv single page-applikation med hjälp av REACT (eller Angular) med AEM redigerare som kan konfigureras av affärsfolk i AEM och hur du integrerar dina interaktiva applikationer med Adobe Analytics offline.

## Använda AEM SPA Editor {#using-the-aem-spa-editor}

Följ stegen nedan för att använda AEM SPA Editor:

1. Klona AEM redigerarens SPA på [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

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
   >Vi använder **GroupId** som ***com.adobe.aem.screens*** och **ArtifactId** som ***My Sample SPA*** (som är standardvärdena). Du kan välja egna efter behov.

1. När projektet har skapats kan du antingen använda en utvecklingsmiljö eller en redigerare och importera det genererade Maven-projektet.
1. Distribuera till den lokala AEM med kommandot ***mvn clear install -PautoInstallPackage***.

### Redigera innehåll i REACT-appen {#editing-content-in-the-react-app}

Så här redigerar du innehållet i REACT-appen:

1. Navigera till `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (ersätt värdnamnet, porten och projektnamnet efter behov).
1. Du bör kunna redigera texten som visas i Hello world-programmet.

### Lägga till den interaktiva REACT-appen i AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Följ stegen nedan för att lägga till den interaktiva REACT-appen i AEM Screens:

1. Skapa ett nytt AEM Screens-projekt. Mer information finns i [Skapa och hantera projekt](creating-a-screens-project.md).

   >[!NOTE]
   >
   >Skapa en **sekvenskanal** när du skapar en kanal i mappen **Kanaler** i skärmprojektet.
   >
   >
   >Mer information finns i [Skapa och hantera kanaler](managing-channels.md).

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. Redigera valfri sekvenskanal och dra och släpp en inbäddad sidkomponent.

   Mer information finns i [Lägga till komponenter i en kanal](adding-components-to-a-channel.md).

   >[!NOTE]
   >
   >Se till att du lägger till användarinteraktionshändelsen när du tilldelar kanalen till visningen.

1. Klicka på **Redigera** i åtgärdsfältet för att redigera egenskaperna för sekvenskanalen.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Dra och släpp **den inbäddade sidan** och välj hemsidan under mysamplespa-programmet, till exempel ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at10104am](assets/screen_shot_2019-02-15at101104am.png)

1. Registrera en spelare för det här projektet så bör du nu kunna se att ditt interaktiva program körs på AEM Screens.

   Mer information om hur du registrerar en enhet finns i [Device Registration](device-registration.md).

## Integrera SPA med Adobe Analytics med offlinefunktioner via AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Följ stegen nedan för att integrera SPA med Adobe Analytics med offlinefunktioner via AEM Screens:

1. Konfigurera Adobe Analytics i AEM Screens.

   Läs [Konfigurera Adobe Analytics med AEM Screens](configuring-adobe-analytics-aem-screens.md) om du vill veta hur du utför sekvensering i Adobe Analytics med AEM Screens och skickar anpassade händelser med Adobe Analytics offline.

1. Redigera din reaktionsapp i den utvecklingsmiljö/redigerare du väljer (särskilt textkomponenten eller någon annan komponent som du vill börja skicka händelser för).
1. Lägg till analysinformationen med standarddatamodellen i klickhändelsen eller i någon annan händelse som du vill hämta för komponenten.

   Mer information finns i [Konfigurera Adobe Analytics med AEM Screens](configuring-adobe-analytics-aem-screens.md)s.

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

