---
title: Implementera Cloud Player
seo-title: Implementing Cloud Player
description: Följ den här sidan om du vill veta mer om implementeringen av Cloud Player.
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 5b64ab8eea274aa85c61311d34b1ce065a5ba601
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# Implementera Cloud Player  {#implementing-cloud-player}

AEM Screens har traditionellt erbjudit olika inbyggda spelarprogram för olika plattformar, bland annat ChromeOS, Windows, Android och Tizen. Men som svar på våra användares föränderliga behov har vi tagit fram en innovativ lösning - AEM Screens Cloud Player.

Molnspelaren utgör ett betydande avsteg från våra tidigare inbyggda program. Det är en progressiv webbapp (PWA) som ligger på en server. Detta omvandlingssätt ger våra kunder möjlighet att använda en plattformsoberoende spelare som kan köras direkt i en webbläsare.

Det är enkelt att få åtkomst till molnspelaren än att besöka https://player.adobescreens.com. Användarna kan installera det på sin enhet, oavsett plattform, och få smidiga digitala signeringsupplevelser. Kompatibiliteten med Cloud Player är beroende av att det finns en modern webbläsare med stöd för PWA, vilket ger enhetliga prestanda på olika enheter. Ta farväl av manuella uppdateringar och hälsa på en spelare som automatiskt utför korrigeringar och funktioner, så att du alltid har de senaste funktionerna nära till hands. Detta är en övergång till ett PWA-baserat molnspelarprogram som är en spännande utveckling av våra digitala signeringserbjudanden, vilket gör det mer tillgängligt, mångsidigt och användarvänligt än någonsin tidigare.

I det här avsnittet beskrivs hur du implementerar molnspelaren.

>[!NOTE]
>
>Kompatibiliteten med molnspelaren kräver en modern webbläsare med stöd för PWA för att du ska få enhetliga prestanda på olika enheter.

## Installerar Cloud Player {#installing-cloud-player}

Installationen av Cloud Player kan variera mellan olika plattformar. I allmänhet kan alla plattformar som har en modern webbläsare köra molnspelarprogrammet genom att följa dessa steg:

1. Öppna webbläsaren och ange [molnspelarens URL](https://player.adobescreens.com) i adressfältet.
1. Webbläsaren kontrollerar om molnspelaren är installerbar och visar sedan en installationsikon i adressfältet.

   ![bild](/help/user-guide/assets/cloud-player-install.png)

1. Klicka på installationsikonen och installationsknappen i bekräftelsedialogrutan. Cloud Player installeras som ett fristående program på enheten och kan startas med en ikon.

>[!NOTE]
>
>### Installationsalternativ för molnspelare {#cloud-player-install-option}
>
1. Installationsalternativet för en PWA kallas även&quot;Lägg till på hemskärmen&quot; eller A2HS-funktion.  Stödet för att installera PWA från webben varierar beroende på webbläsare och plattform.
1. Alla webbläsare har olika villkor för att kontrollera om appen PWA är installerbar eller inte. Webbläsaren kontrollerar vanligtvis dessa (mer information här):
>
* Om programmet har en manifest json-fil med minimalt antal nödvändiga nycklar för installation av programmet på plattformen, dvs. namn, ikoner, start_url, visa
* Om programmet har en servicearbetarfil med en hämtningshändelseavlyssnare.
* Appen måste serveras via https.
>
1. Installationsalternativet kan vara synligt på olika platser i olika webbläsare och på olika enheter. I vissa webbläsare kan installationsikonen döljas i alternativmenyraden.

## Massetablering av molnspelare {#bulk-provisioning}

Så här gör du massetablering av molnspelaren på flera enheter:

1. Välj en MDM-lösning som har stöd för att köra en webbläsare med en URL i Kiosk-läge.
1. Du kan använda samma konfigurationer på alla enheter genom att följa dessa steg:

   1. Värdconfig.json på en server så att den kan nås, till exempel: https://&lt;config_server_host>/config.json
   1. Om du vill installera molnspelaren och använda värdkonfigurationerna använder du molnspelarens URL-adress, till exempel: https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>
   1. Cloud Player-programmet söker efter config.json i roten av &lt;config_server_host>, tolka config.json för att hämta de anpassade konfigurationerna och tillämpa dessa konfigurationer.
   1. Dessa konfigurationer används vid varje omladdning av spelaren.

## Massetablering i Chrome OS {#bulk-provisioning-chrome}

Mer information om grupptilldelning i Chrome OS finns i: [Installera Cloud Player på Chrome OS](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## Konfiguration krävs för AEM instanser {#bulk-provisioning-config-aem}

Beroende på vilken typ av AEM som används väljer du en av följande stödlinjer för att aktivera CORS b/w AEM &amp; cloud player:
* [AEM On-Premises/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

>[!NOTE]
>
## Chrome Apps Deprecation by Google
>
1. Chrome Apps on Chrome OS Hardware:
>
Google har aktivt ersatt Chrome Apps med stöd för PWA-appar, med en planerad migrering fram till januari 2025. Därför kommer AEM Screens Player-appen i Chrome OS inte längre att fungera baserat på den delade tidslinjen. Vi uppmanar våra kunder som för närvarande använder Chrome Player i produktion att planera för övergång till Screens Cloud Player.
>
1. Chrome Extension Player på Mac, Windows och Linux:
>
På grund av Google borttagningsprocess, från och med Google Chrome version 114, stöds inte längre Screens Chrome Extension Player. Vi rekommenderar starkt att du går över till Adobe Screens Cloud Player för alla utvecklings- och testningskrav.

## Offline-stöd för extern innehållshämtning {#offline-support}

I olika användningsscenarier kan kanalerna kräva hämtning av innehåll från en extern källa (t.ex. väderwidgetar eller Commerce-integrerade Single Page-program) som inte kan tillhandahålla offlinesupport. För att aktivera offlinefunktioner för dessa specifika användningsområden har molnspelaren stöd för anpassade sidhuvuden.

I molnspelaren används en strategi för Network First Cache, vilket innebär att den försöker hämta innehåll från nätverket (och sedan uppdatera cachen med senaste) och återgå till cachelagrat innehåll om möjligt. Om du vill implementera offlinesupport för sådan innehållshämtning måste den anpassade rubriken inkluderas i begäran. Därefter cachelagras begäran med det anpassade huvudet i spelaren, vilket underlättar offlineåtkomst till innehållet samtidigt som strategin för nätverkets första cache bevaras.

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## Feedback

Vi värdesätter din feedback! Dela gärna dina tankar med oss genom detta [formulär](https://forms.office.com/r/MQXX9JsuEd).
