---
title: Adobe Analytics Integration med AEM Screens
description: Lär dig mer om hur AEM Screens är integrerat med Adobe Analytics och ger dig ett spelbevis.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Adobe Analytics Integration med AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Den här AEM Screens-funktionen är endast tillgänglig om du har installerat minimiversionen av AEM 6.4.2 Feature Pack 2 eller AEM 6.3.3 Feature Pack 4. För kunder som har AEM Screens Cloud-tjänster kontaktar du din Adobe Relationship Manager för att aktivera Adobe Analytics i Screens Cloud.

>[!NOTE]
>
>Om du vill få tillgång till något av dessa funktionspaket kontaktar du Adobe Support och begär åtkomst. Du kan hämta det senaste funktionspaketet för AEM Screens från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID.

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Arkitekturinformation**
* **Konfigurerar egenskaperna**

## Ökning {#overview}

***AEM Screens*** använder Adobe Analytics och med det kan du uppnå något unikt på marknaden - kanalövergripande analyser som hjälper till att korrelera innehåll som visas på plats med andra datakällor.

AEM Screens är en färdig integrerad lösning med Adobe Analytics och ger dig ett bevis på uppspelning.

I det här avsnittet beskrivs följande funktioner som används för att ansluta ett AEM Screens-projekt till Adobe Analytics:

* Tillåter att uppspelningsrapportering kan styrkas per enhet
* Tillåter granskning av uppspelningsrapportering efter tillgång
* Ser till att alla spelarhändelser hämtas och tidsstämplas
* Ser till att alla spelarhändelser lagras lokalt om uppspelningen inte är ansluten till ett nätverk
* Det går att skapa feedbackslingor som spårar uppspelningshändelser över tiden
* Innebär att systemet kan redigera innehåll och layouter baserat på kriterier för lyckade resultat som definierats av innehållsförfattaren

Adobe Analytics-integrering med AEM Screens tvingar alltså följande *mål*:

* Aktivera ROI från implementering av digitala signaturer
* Integrera Analytics som grund för att i framtiden kunna samla in och analysera användningsinformation

## Arkitekturinformation {#architectural-details}

En AEM Screens-kund vill förstå vilket innehåll som visades vid vilken tidpunkt och hur länge (aggregerat). Denna nödvändighet är en gemensam funktion i en signeringslösning. I stället för att bygga ett separat analysprogram använder AEM Screens Adobe Analytics. Med kombinationen kan vi uppnå något unikt på marknaden - flerkanalsanalyser som hjälper oss att korrelera innehåll som visas på plats med andra datakällor.

I följande diagram förklaras Adobe Analytics Integration med AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Aktivera Adobe Analytics i AEM Screens {#enabling-adobe-analytics-in-aem-screens}

Adobe Analytics-inställningarna kan konfigureras från OSGi-konsolen.

Navigera till **Adobe Experience Manager Web Console Configuration** så att du kan konfigurera Adobe Analytics för AEM Screens.

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics: Aktiveringsflöde {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Innan du konfigurerar egenskaperna bör du kontakta din Adobe Relationship Manager och skapa en biljett för att få en **API-nyckel för analyser** och ett **analysprojekt** som kan användas med AEM Screens.

### Konfigurera egenskaperna {#configuring-the-properties}

>[!CAUTION]
>
>Innan du konfigurerar egenskaperna bör du kontakta din Adobe Relationship Manager och skapa en biljett för att få en **API-nyckel för analyser** och ett **analysprojekt** som kan användas med AEM Screens.

I följande tabell visas egenskaperna med en beskrivning av hur du konfigurerar Adobe Analytics för AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Egenskap</strong></td>
   <td><strong>Beskrivning</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics-URL</strong></td>
   <td>URL för att publicera analysdata från spelaren. <br>
   För utveckling/scen </em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>För produktion</em> - https://cc-api-data.adobe.io/ingest/<br /> <br /></td>
  </tr>
  <tr>
   <td><strong>API-nyckel för analyser</strong></td>
   <td>API-nyckel för autentisering till Adobe Analytics-servern (tillhandahålls av kontohanteraren).</td>
  </tr>
  <tr>
   <td><strong>Analysprojekt</strong></td>
   <td>AEM Screens-projekt konfigurerat på din analys för att ta emot data (tillhandahålls av kontohanteraren).</td>
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

#### Använda Adobe Analytics-tjänsten i AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Detta scenario anropar Analytics API via REST-anrop från en analystjänst i den inbyggda programvaran. Den AEM också skärmar-kärnkomponenter för att skapa och skicka händelser som är specifika för ett visst användningsfall. All den här funktionaliteten samtidigt som den tillåter utbyggbarhet där anpassade meddelanden kan skickas till Analytics från en anpassad kanal.

Analyshändelser lagras offline i indexedDB och sedan i chunked-läge och skickas till molnet.

>[!NOTE]
>
>Mer information om ***sekvensering*** och ***standarddatamodell för händelser*** finns i **[Konfigurera Adobe Analytics för AEM Screens](configuring-adobe-analytics-aem-screens.md)**.
