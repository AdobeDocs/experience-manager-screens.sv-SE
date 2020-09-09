---
title: Konfigurera Adobe Analytics med AEM Screens
seo-title: Konfigurera Adobe Analytics med AEM Screens
description: 'Följ det här avsnittet om du vill veta mer om sekvensering och hur du skickar anpassade händelser med Offline Adobe Analytics '
seo-description: 'Följ det här avsnittet om du vill veta mer om sekvensering och hur du skickar anpassade händelser med Offline Adobe Analytics '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 8%

---


# Konfigurera Adobe Analytics med AEM Screens {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>Denna AEM Screens-funktionalitet är endast tillgänglig om du har installerat AEM 6.4.2 Feature Pack 2 och AEM 6.3.3 Feature Pack 4.
>
>Om du vill få tillgång till något av dessa funktionspaket måste du kontakta Adobe Support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

Detta avsnitt behandlar följande ämnen:

* **Sekvenser i Adobe Analytics med AEM Screens**
* **Skicka anpassade händelser med Adobe Analytics offline**

## Sekvenser i Adobe Analytics med AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

Sekvensprocessen ****** börjar med datalagringstjänsten som aktiverar Adobe Analytics-tjänsten. Kanalinnehåll skickar Adobe Analytics-händelser med lön, det vill säga datatestning som utförs i Windows I/O och stannar-händelser aktiveras. Händelserna sparas i indexdatabasen och placeras sedan i objektarkivet. Baserat på schemat klipper administratören in data från objektarkivet och överför dem vidare till segmentlagret. Den försöker skicka maximalt med data när den är ansluten.

### Sekvensdiagram {#sequencing-diagram}

I följande sekvensdiagram förklaras Adobe Analytics Integration med AEM Screens:

![analytics_chunking](assets/analytics_chunking.png)

## Skicka anpassade händelser med Adobe Analytics offline {#sending-custom-events-using-offline-adobe-analytics}

I följande tabell sammanfattas standarddatamodellen för händelser. Här visas alla fält som skickats till Adobe Analytics:

<table>
 <tbody>
  <tr>
   <td><strong>Avsnitt</strong></td> 
   <td><strong>Egenskapsetikett</strong></td> 
   <td><strong>Egenskapsnamn/nyckel</strong></td> 
   <td><strong>Krävs</strong></td> 
   <td><strong>Datatyp</strong></td> 
   <td><strong>Egenskapstyp</strong><br /> </td> 
   <td><strong>Beskrivning</strong></td> 
  </tr>
  <tr>
   <td><strong><em>Core/Event</em></strong></td> 
   <td>Händelse-GUID</td> 
   <td>event.guid</td> 
   <td>rekommenderas</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>Unikt ID som identifierar en instans av en händelse</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Datum och tid för insamling av händelse</td> 
   <td>event.coll_dts</td> 
   <td>valfritt</td> 
   <td>string</td> 
   <td>tidsstämpel - UTC</td> 
   <td>Datum och tid för samling</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Datum och tid för händelse (start)</td> 
   <td>event.dts_start</td> 
   <td>rekommenderas</td> 
   <td>string</td> 
   <td>tidsstämpel - UTC</td> 
   <td>Händelsens startdatum och starttid, om du INTE anger detta, antas händelsetiden vara den tidpunkt då den togs emot av servern</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Datum och tid för händelse (slut)</td> 
   <td>event.dts_end</td> 
   <td>valfritt</td> 
   <td>string</td> 
   <td>tidsstämpel - UTC</td> 
   <td>Datum och tid för slutförande av händelse</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Arbetsflöde</td> 
   <td>event.workflow</td> 
   <td>rekommenderas</td> 
   <td>string</td> 
   <td> </td> 
   <td>Arbetsflödets namn (skärmar)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Main DMe Category</td> 
   <td>event.category</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Huvudkategori (DATOR, MOBIL, WEB, PROCESS, SDK, SERVICE, ECOSYSTEM) - Gruppering av händelsetyper - <strong>Vi skickar spelare</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Underkategori</td> 
   <td>event.subcategory</td> 
   <td>rekommenderas</td> 
   <td>string</td> 
   <td> </td> 
   <td>Underkategori - Avsnitt i ett arbetsflöde eller område på en skärm osv. (Senaste filer, CC-filer, mobila arbeten osv.)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Typ av händelse/åtgärd</td> 
   <td>event.type</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Händelsetyp (återge, klicka, nypa, zooma) - åtgärd för primär användare</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Undertyp</td> 
   <td>event.subtype</td> 
   <td>rekommenderas</td> 
   <td>string</td> 
   <td> </td> 
   <td>Händelsetyp (skapa, uppdatera, ta bort, publicera osv.) - Ytterligare information om användaråtgärden</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Offline</td> 
   <td>event.offline</td> 
   <td>valfritt</td> 
   <td>boolean</td> 
   <td> </td> 
   <td>Händelsen genererades när åtgärden var offline/online (true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Användaragent</td> 
   <td>event.user_agent</td> 
   <td>rekommenderas (webbegenskaper)</td> 
   <td>string</td> 
   <td> </td> 
   <td>Användaragent</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Språk/språk</td> 
   <td>event.language</td> 
   <td>rekommenderas</td> 
   <td>string</td> 
   <td> </td> 
   <td>Användarens språkområde är en sträng som baseras på konventionerna för språktaggning i RFC 3066 (t.ex. en-US, fr-FR eller es-ES)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Enhets-GUID</td> 
   <td>event.device_guid</td> 
   <td>valfritt</td> 
   <td>string<br /> </td> 
   <td>UUID</td> 
   <td>Identifierar enhets-GUID (t.ex. dator-ID eller hash för IP-adressen + nätmasken + nätverks-ID + användaragent) - Här skickar vi användarnamnet för spelaren som genereras vid registreringen.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Count</td> 
   <td>event.count</td> 
   <td>valfritt</td> 
   <td>tal</td> 
   <td> </td> 
   <td>Antal gånger händelsen har inträffat - Här skickar vi videons längd</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Värde</td> 
   <td>event.value</td> 
   <td>valfritt</td> 
   <td>string</td> 
   <td> </td> 
   <td>Händelsens värde (t.ex. på/av-inställningar)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sidnamn</td> 
   <td>event.pagename</td> 
   <td>krävs för AA</td> 
   <td>string</td> 
   <td> </td> 
   <td>Adobe Analytics-stöd för anpassat sidnamn</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Webbadress</td> 
   <td>event.url</td> 
   <td>valfritt</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL för webbegenskapen eller mobilschemat - måste innehålla en fullständigt kvalificerad URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Felkod</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Felkod</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Feltyp</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Feltyp</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Felbeskrivning</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Felbeskrivning<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>Källa/ursprunglig produkt</em></strong></td> 
   <td>Namn</td> 
   <td>source.name</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Programnamn (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Version</td> 
   <td>source.version</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Firmware-version</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Plattform</td> 
   <td>source.platform</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Enhet</td> 
   <td>source.device</td> 
   <td>obligatoriska med undantag</td> 
   <td>string</td> 
   <td> </td> 
   <td>Spelarnamn</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>OS-version</td> 
   <td>source.os_version</td> 
   <td>obligatoriska med undantag</td> 
   <td>string</td> 
   <td> </td> 
   <td>O/S-version</td> 
  </tr>
  <tr>
   <td><strong><em>Innehåll</em></strong></td> 
   <td>Åtgärd</td> 
   <td>content.action</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL:en till resursen inklusive återgivningen som spelades upp</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Mime-typ</td> 
   <td>content.mimetype</td> 
   <td>valfritt</td> 
   <td>string</td> 
   <td> </td> 
   <td>Innehållets Mime-typ</td> 
  </tr>
  <tr>
   <td><strong><em>Transaktion</em></strong></td> 
   <td>Transaktionsnummer</td> 
   <td>trn.number</td> 
   <td>required</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>Unikt ID som helst följer UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Produktbeskrivning</td> 
   <td>trn.product</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL:en till resursen (exklusive återgivning)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Kvantitet</td> 
   <td>trn.quantity</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Uppspelningens längd</td> 
  </tr>
 </tbody>
</table>

