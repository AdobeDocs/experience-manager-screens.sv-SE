---
title: Grunderna för digital signering för [!UICONTROL AEM Screens]
description: Lär dig grunderna i ett digitalt signeringsprojekt.
exl-id: e3913be2-9028-4773-a034-e16924a71e04
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Grunderna i ett projekt för digital signering {#basics-digital-signage}

Innan man börjar använda sig av AEM Screens bästa praxis för implementering är det viktigt att tänka på projektet som ett digitalt signeringsprojekt, i stället för som en traditionell programvaruutveckling.

I det här avsnittet ges rekommendationer om viktiga nyckelelement som är viktiga för en implementering av AEM Screens-projekt.

## Viktiga element i digital signering {#key-elements}

*Nyckelelement* i ett projekt för digital signatur är:

![](/help/assets/Elements-Revised.png)

Det är viktigt att du definierar nyckelelementen innan du implementerar ett projekt för digitala signaturer:

1. **Maskinvara**

   Maskinvaran definierar vilka maskinvarukomponenter som är idealiska för implementering av projekt för digitala signaturer:
   * Har enheten tillräckligt med lagringsutrymme för att köra alla varianter av upplevelserna offline?
   * Har du tillåtit typ och längd av videokabel? Och har enheten stöd för både önskad upplösning (HD, FullHD, `4K` och så vidare) och videokodekar som jag planerar att distribuera (h.264, h.265 och så vidare)
   * Användning av fysisk koppartråd
   * Skärmstorlek
   * Antal skärmar
      * orientering
      * proportioner
      * upplösning, inställning

1. **Anslutning**

   Anslutningsmöjligheterna fokuserar på följande frågor:
   * Nätverksansluten (cell eller wi-fi) eller fristående?
      * Vill du tillåta USB-innehållsuppdateringar?
      * Ska ni tillåta användning av datainsamling?

1. **Installation**

   Installationen omfattar:
   * Bildskärmar: liggande eller stående
   * Hur monteras skärmen?
      * Stående orientering kontra liggande orientering
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

   Miljön fokuserar på:
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
