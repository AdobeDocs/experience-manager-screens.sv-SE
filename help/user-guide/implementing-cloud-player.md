---
title: Implementera Cloud Player
description: Lär dig mer om implementeringen av molnspelaren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---

# Implementera Cloud Player  {#implementing-cloud-player}

AEM Screens har traditionellt erbjudit olika inbyggda spelarapplikationer för olika plattformar som ChromeOS, Windows, Android™ och `Tizen`. Som svar på användarnas föränderliga behov har Adobe dock introducerat en innovativ lösning - AEM Screens Cloud Player.

Molnspelaren utgör ett betydande avsteg från Adobe tidigare inbyggda program. Det är en progressiv webbapp (PWA) som finns på en server. Detta omvandlingssätt ger kunderna en plattformsoberoende spelare som kan köras direkt i en webbläsare.

Det är bara att besöka molnspelaren `https://player.adobescreens.com`. Användarna kan installera det på sin enhet, oavsett plattform, och få smidiga digitala signeringsupplevelser. Kompatibiliteten med Cloud Player är beroende av att det finns en modern webbläsare med stöd för PWA, vilket ger enhetliga prestanda på olika enheter. Ta farväl av manuella uppdateringar och hälsa på en spelare som automatiskt utför korrigeringar och funktioner, så att du alltid har de senaste funktionerna nära till hands. Det här bytet till ett PWA-baserat molnspelarprogram är en spännande utveckling av Adobe digitala signeringserbjudanden som gör det mer tillgängligt, mångsidigt och användarvänligt än någonsin tidigare.

I det här avsnittet beskrivs hur du implementerar molnspelaren.

>[!NOTE]
>
>Kompatibiliteten med molnspelaren kräver en modern webbläsare med stöd för PWA för att du ska få enhetliga prestanda på olika enheter.

## Installerar Cloud Player {#installing-cloud-player}

Installationen av Cloud Player kan variera mellan olika plattformar. I allmänhet kan alla plattformar som har en modern webbläsare köra molnspelarprogrammet genom att följa dessa steg:

1. Öppna webbläsaren och ange [molnspelarens URL](https://player.adobescreens.com) i adressfältet.
1. Webbläsaren kontrollerar om molnspelaren är installerbar och visar sedan en installationsikon i adressfältet.

   ![bild](/help/user-guide/assets/cloud-player-install.png)

1. Välj installationsikonen och installationsknappen i bekräftelsedialogrutan. Cloud Player installeras som ett fristående program på enheten och kan startas med en ikon.

>[!NOTE]
>
>### Installationsalternativ för molnspelare {#cloud-player-install-option}
>
1. Installationsalternativet för en PWA kallas även&quot;Lägg till på hemskärmen&quot; eller A2HS-funktion. Stödet för att installera PWA från webben varierar beroende på webbläsare och plattform.
1. Alla webbläsare har olika villkor för att kontrollera om appen PWA är installerbar eller inte. Webbläsaren kontrollerar vanligtvis dessa (mer information här):
>
* Om programmet har en manifest json-fil med minimalt antal nödvändiga nycklar för att installera programmet på plattformen, det vill säga namn, ikoner, start_url, visa
* Om programmet har en servicearbetsfil med en hämtningshändelseavlyssnare
* Appen måste serveras via https
>
1. Installationsalternativet kan vara synligt på olika platser i olika webbläsare och enhetstyper. I vissa webbläsare kan installationsikonen döljas i alternativmenyraden.

## Massetablering av molnspelare {#bulk-provisioning}

Så här gör du massetablering av molnspelaren på flera enheter:

1. Välj en MDM-lösning som har stöd för att köra en webbläsare med en URL i Kiosk-läge.
1. Du kan använda samma konfigurationer på alla enheter genom att följa dessa steg:

   1. Värdconfig.json på en server så att den är tillgänglig som: `https://<config_server_host>/config.json`
   1. Om du vill installera molnspelaren och använda värdkonfigurationerna använder du molnspelarens URL-adress, till exempel: `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. Cloud Player-programmet söker efter config.json i roten av &lt;config_server_host>, tolka config.json för att hämta de anpassade konfigurationerna och tillämpa dessa konfigurationer.
   1. Dessa konfigurationer används vid varje omladdning av spelaren.

## Massetablering i Chrome OS {#bulk-provisioning-chrome}

Läs mer om massetablering i Chrome OS på [Installera Cloud Player på Chrome OS](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

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
Google har aktivt ersatt Chrome Apps med stöd för PWA-appar, med en planerad migrering fram till januari 2025. Därför slutar AEM Screens Player-appen i Chrome OS att fungera baserat på den delade tidslinjen. Adobe uppmanar användare som för närvarande använder Chrome Player i produktion att planera för övergång till Screens Cloud Player.
>
1. Chrome Extension Player på Mac, Windows och Linux®:
>
På grund av Google borttagningsprocess, från och med Google Chrome version 114, stöds inte längre Screens Chrome Extension Player. Adobe rekommenderar att du går över till deras Screens Cloud Player för alla utvecklings- och testningskrav.

## Offline-stöd för extern innehållshämtning {#offline-support}

I olika användningsscenarier kan kanalerna kräva hämtning av innehåll från en extern källa (till exempel väderwidgetar eller Commerce-integrerade Single Page-program) som inte kan tillhandahålla offlinesupport. För att aktivera offlinefunktioner för dessa specifika användningsområden har molnspelaren stöd för anpassade sidhuvuden.

I molnspelaren används en strategi för Network First Cache, vilket innebär att den försöker hämta innehåll från nätverket (och sedan uppdatera cachen med senaste) och återgå till cachelagrat innehåll om möjligt. Om du vill implementera offlinesupport för sådan innehållshämtning måste den anpassade rubriken inkluderas i begäran. Begäran med det anpassade huvudet cachelagras sedan i spelaren, vilket underlättar offlineåtkomst till innehållet samtidigt som strategin för nätverkets första cache bevaras.

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

Adobe värdesätter din feedback. Dela dina tankar med oss genom detta [formulär](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).
