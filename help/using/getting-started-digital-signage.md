---
title: Grunderna för digital signering för [!UICONTROL AEM Screens]
description: Lär dig grunderna i ett digitalt signeringsprojekt.
exl-id: e3913be2-9028-4773-a034-e16924a71e04
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Grunderna i ett projekt för digital signering {#basics-digital-signage}

Innan man börjar använda sig av AEM Screens bästa praxis för implementering är det viktigt att tänka på projektet som ett digitalt signeringsprojekt, i stället för som en traditionell programvaruutveckling.

I det här avsnittet ges rekommendationer om viktiga nyckelelement som är viktiga innan AEM Screens implementeras.

## Viktiga element i digital signering {#key-elements}

The *Nyckelelement* i ett digitalt signeringsprojekt:

![](/help/assets/Elements-Revised.png)

Det är viktigt att du definierar nyckelelementen innan du implementerar ett projekt för digitala signaturer:

1. **Maskinvara**

   Maskinvaran definierar vilka maskinvarukomponenter som är idealiska för implementering av projekt för digitala signaturer:
   * Har enheten tillräckligt med lagringsutrymme för att köra alla varianter av upplevelserna offline?
   * Har du tillåtit typ och längd av videokabel? Och har enheten stöd för båda upplösningarna (HD, FullHD, `4K`och så vidare) och videokodekar som jag planerar att driftsätta (h.264, h.265 och så vidare)
   * Användning av fysisk koppartråd
   * Skärmstorlek
   * Antal skärmar
      * orientering
      * proportioner
      * upplösning, inställning

1. **Anslutningar**

   Anslutningsmöjligheterna fokuserar på följande frågor:
   * Nätverksansluten (cell eller wi-fi) eller fristående?
      * Vill du tillåta USB-innehållsuppdateringar?
      * Måste ni tillåta insamling av användningsdata?

1. **Installation**

   Installationen omfattar:
   * Bildskärmar: liggande eller stående
   * Hur monteras skärmen?
      * Stående jämfört med liggande
      * Fullständigt hölje
      * Täckplåt
   * Fixeringsstöd
   * Personal: ansvarar för att installera utrustningen och ansluta den till nätverket
   * Hur långt borta är strömkällan från fixturen?
   * Hur långt borta är den fysiska panelen från den faktiska enheten?

1. **Innehåll**

   Innehåll:
   * En eller flera zoner?
      * Hur många mediefiler finns på skärmen samtidigt?
      * Hur många sidor finns det för interaktiva program?
      * Definiera UI-slingan
      * Datadrivet innehåll?
   * Versionskontroll

1. **Interaktiv**

   Interaktiva funktioner:
   * Önskad typ av pekskärm?(resistiv, kapacitiv, multitouch)?
      * Knapptryck
      * Gesture
   * Datautlösare (I/O)?
      * Skicka/ta emot seriella kommandon (kontaktstängning, PLC osv.)
      * Inkommande data visas på skärmen (RSS) eller utlöser innehåll
      * RFID/NFC/Bluetooth/iBeacon
      * Externa tjänster (väder, trafik)

1. **Miljö**

   Miljön betonar:
   * Visningsplats?
      * Insida kontra utsida
      * Oåtkomlig eller direkt exponerad
   * Särskilt tillfälligt krav?
   * Vandalbevis?
   * Högt omgivande ljus? Starka kontraster?

1. **Underhåll**

   Underhållet fokuserar på:

   * Krävs installationsguider och användarhandböcker?
   * Konfigurerar (programmerar) du enheten före leverans?
   * Måste du hämta varje serienummer för spårning?
   * Finns det några krav på reservström (oavbruten strömförsörjning)?
   * Hur distribueras systemuppdateringar? Och hur fjärrövervakas enheter? Krävs en MDM-lösning?
