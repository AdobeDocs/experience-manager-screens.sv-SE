---
title: Grunderna för digital signering för [!UICONTROL AEM Screens]
seo-title: Grunderna för digital signering för [!UICONTROL AEM Screens]
description: Guiden beskriver grunderna i ett digitalt signeringsprojekt
seo-description: Guiden beskriver grunderna i ett digitalt signeringsprojekt
translation-type: tm+mt
source-git-commit: 30c724ea897fd2da5300bb5cad285d460af5de40

---


# Grunderna i ett projekt för digital signering {#basics-digital-signage}

Innan man börjar använda de bästa metoderna för implementering av AEM-skärmar är det viktigt att tänka på projektet som ett digitalt signeringsprojekt, i stället för som en traditionell programvaruutveckling.

I det här avsnittet ges rekommendationer om viktiga nyckelelement som är viktiga innan en AEM Screens-projektimplementering genomförs.

## Viktiga element i digital signering {#key-elements}

Nyckelelementen ** i ett projekt för digitala signaturer är:

![](/help/assets/Elements-Revised.png)

Det är viktigt att du definierar nyckelelementen innan du implementerar ett projekt för digitala signaturer:

1. **Maskinvara**

   Maskinvaran definierar vilka maskinvarukomponenter som är idealiska för implementering av projekt för digitala signaturer:
   * Har enheten tillräckligt med lagringsutrymme för att köra alla varianter av upplevelserna offline?
   * Har vi tillåtit typ och längd av videokabel? Och har enheten stöd för båda upplösningarna (HD, FullHD, 4K osv.) och videokodekar som jag planerar att driftsätta (h.264, h.265 osv.)
   * Användning av fysisk koppartråd
   * Skärmstorlek
   * Antal skärmar
      * orientation
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
      * Externa tjänster (väder, trafik osv.)

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
   * Finns det några krav på reservström (avbrottsfri strömförsörjning)?
   * Hur distribueras systemuppdateringar? Och hur fjärrövervakas enheter? Krävs en MDM-lösning?