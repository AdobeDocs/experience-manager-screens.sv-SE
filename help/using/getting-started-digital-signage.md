---
title: Grunderna för digital signering för [!UICONTROL AEM Screens]
seo-title: Basics Of Digital  Signage for [!UICONTROL AEM Screens]
description: Guiden beskriver grunderna i ett digitalt signeringsprojekt
seo-description: The guide describes the basics of a digital signage project
exl-id: e3913be2-9028-4773-a034-e16924a71e04
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '409'
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
   * Har vi tillåtit typ och längd av videokabel? Och har enheten stöd för båda upplösningarna (HD, FullHD, 4K osv.) och videokodekar som jag planerar att driftsätta (h.264, h.265 osv.)
   * Användning av fysisk koppartråd
   * Skärmstorlek
   * Antal skärmar
      * orientering
      * proportioner
      * upplösning, inställning

1. **Anslutningar**

   Anslutningsmöjligheterna fokuserar på följande frågor:
   * Nätverksansluten (cell eller wi-fi) eller fristående?
      * måste vi tillåta USB-innehållsuppdateringar?
      * måste vi tillåta insamling av användningsdata?

1. **Installation**

   Installationen omfattar:
   * Skärmar: liggande eller stående
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
      * Definiera gränssnittsslingan
      * Datadrivet innehåll?
   * Versionskontroll

1. **Interaktiv**

   Interaktiva funktioner:
   * Önskad typ av pekskärm?(resistiv, kapacitiv, multitouch)?
      * Knapptryck
      * Gesture
   * Datautlösare (I/O)?
      * Skicka och ta emot seriella kommandon (kontaktstängning, PLC osv.)
      * Inkommande data visas på skärmen (RSS) eller utlöser innehåll
      * RFID/NFC/Bluetooth/iBeacon
      * Externa tjänster (väder, trafik)

1. **Miljö**

   Miljön fokuserar på:
   * Visningsplats?
      * Insida kontra utsida
      * Oåtkomlig eller direkt exponerad
   * Särskilt tillfälligt krav?
   * Vandalbevis?
   * Högt omgivningsljus? Starka kontraster?

1. **Underhåll**

   Underhållet fokuserar på:

   * Krävs detaljerade installationsguider/användarhandböcker?
   * Konfigurerar (programmerar) vi enheten före leveransen?
   * Behöver vi samla in varje serienummer för spårning?
   * Finns det några krav på reservkraft (strömförsörjning utan avbrott)?
   * Hur distribueras systemuppdateringar? Och hur fjärrövervakas enheter? Krävs en MDM-lösning?
