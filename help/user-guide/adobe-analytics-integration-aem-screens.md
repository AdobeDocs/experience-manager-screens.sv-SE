---
title: Adobe Analytics-integrering med AEM-skärmar
seo-title: Adobe Analytics-integrering med AEM-skärmar
description: Följ den här sidan om du vill veta mer om hur AEM Screens kan integreras med Adobe Analytics och få ett spelbevis.
seo-description: Följ den här sidan om du vill veta mer om hur AEM Screens kan integreras med Adobe Analytics och få ett spelbevis.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: 3621082c7880e61f659d3bca956159d22d7df6de

---


# Adobe Analytics-integrering med AEM-skärmar {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Den här AEM-skärmfunktionen är bara tillgänglig om du har installerat AEM 6.4.2 Feature Pack 2 och AEM 6.3.3 Feature Pack 4.

>[!NOTE]
>Om du vill få tillgång till något av dessa funktionspaket måste du kontakta Adobes support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Arkitekturinformation**
* **Konfigurera egenskaperna**

## Översikt {#overview}

***AEM Screens*** använder Adobe Analytics och med det kan ni uppnå något unikt på marknaden - flerkanalsanalyser som hjälper er att korrelera innehåll som visas på plats med andra datakällor.

Med AEM Screens får du en färdig integrering med Adobe Analytics och ett spelbevis.

I det här avsnittet beskrivs följande funktioner som används för att ansluta ett AEM Screens-projekt till Adobe Analytics:

* Tillåter att uppspelningsrapportering kan styrkas per enhet
* Tillåter granskning av uppspelningsrapportering efter tillgång
* Ser till att alla spelarhändelser hämtas och tidsstämplas
* Ser till att alla spelarhändelser lagras lokalt om uppspelningen inte är ansluten till ett nätverk
* Gör det möjligt att skapa feedbackslingor som spårar uppspelningshändelser över tid
* Tillåter systemet att ändra innehåll och layouter baserat på kriterier som innehållets författare har definierat

Adobe Analytics-integrering med AEM Screens har därför följande *mål*:

* Aktivera ROI från implementering av digitala signaturer
* Integrera Analytics som grund för att i framtiden kunna samla in och analysera användningsinformation

## Arkitekturinformation {#architectural-details}

En AEM Screens-kund vill förstå vilket innehåll som visades vid vilken tidpunkt och hur länge (aggregerat). Detta är en vanlig funktion för signeringslösning. I stället för att bygga upp egna analyser utnyttjar AEM Screens Adobe Analytics, och med det kan vi uppnå något unikt på marknaden - flerkanalsanalyser som hjälper till att korrelera innehåll som visas på plats med andra datakällor.

I följande arkitekturdiagram förklaras Adobe Analytics-integreringen med AEM-skärmar:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Aktivera Adobe Analytics i AEM-skärmar {#enabling-adobe-analytics-in-aem-screens}

Adobe Analytics-inställningarna kan konfigureras från OSGi-konsolen.

Navigera till **Adobe Experience Manager Web Console Configuration** och konfigurera Adobe Analytics för AEM-skärmar enligt bilden nedan:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Skärmanalys: Aktivera flöde {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Innan du konfigurerar egenskaperna bör du kontakta din Adobe Relationship Manager och skapa en biljett för att få ett **API-nyckel** och **analysprojekt** för AEM-skärmar.

![]()

### Konfigurera egenskaperna {#configuring-the-properties}

>[!CAUTION]
>
>Innan du konfigurerar egenskaperna bör du kontakta din Adobe Relationship Manager och skapa en biljett för att få ett **API-nyckel** och **analysprojekt** för AEM-skärmar.

I följande tabell visas egenskaperna med en beskrivning av hur du konfigurerar Adobe Analytics för AEM-skärmar:

<table>
 <tbody>
  <tr>
   <td><strong>Egenskap</strong></td>
   <td><strong>Beskrivning</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>URL för att publicera analysdata från spelaren. <br>
   För utveckling/scen</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>för produktion</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>API-nyckel för analyser</strong></td>
   <td>API-nyckel för autentisering till Adobe Analytics-servern (tillhandahålls av kontohanteraren).</td>
  </tr>
  <tr>
   <td><strong>Analysprojekt</strong></td>
   <td>AEM Screens-projektet har konfigurerats på din analys för att ta emot data (tillhandahålls av kontohanteraren).</td>
  </tr>
  <tr>
   <td><strong>Miljö</strong></td>
   <td><p>Scen- eller produktionsmiljö (välj antingen scen eller produktion).</p></td>
  </tr>
  <tr>
   <td><strong>Sändningsfrekvens för analyser</strong></td>
   <td>Frekvens i minuter för att skicka analysdata från spelarna. Som standard är den inställd på 15 minuter.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Som standard är **Analytics-sändningsfrekvensen** 15 minuter.

#### Använda Adobe Analytics Service i AEM-skärmar {#using-adobe-analytics-service-in-aem-screens}

Det här scenariot anropar Analytics API via REST-anrop från en analystjänst i komponenterna firmware och instrumentskärmar för att explicit skapa och skicka händelser som är specifika för ett visst användningsfall, samtidigt som det tillåter utökningsmöjligheter där alla anpassade meddelanden kan skickas till Analytics från en anpassad utvecklad kanal.

Analyshändelser lagras offline i indexedDB och sedan i chunked-läge och skickas till molnet.

>[!NOTE]
>
>Mer information om ***sekvensering*** och ***standarddatamodell för händelser*** finns i **[Konfigurera Adobe Analytics för AEM-skärmar](configuring-adobe-analytics-aem-screens.md)**.
