---
title: Enclosed Corporate Network
description: Enclosed Corporate Network
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---


# Närstående företagsnätverk {#enclosed-corporate-networks}

Enclosed Corporate Network SetUp kan användas för mindre, större och större företag. Den kan vara teoretiskt mer komplex, men den logiska inställningen visas i figuren nedan.

![](/help/using/assets/enclosed-network-1.png)

## Krav för konfiguration av företagsnätverk {#requirements-enclosed-networks}

Enclosed Corporate Network Setup kan separeras logiskt i två block:

* WAN (Wide Area Network)
* Internt LAN (Local Area Network).

### Wide Area Network {#wan-connection}

Utförandet av internetanslutningen, förutom nätverkets nåbarhet, är att ge tillräcklig bandbredd för att AEM Screens ska fungera smidigt och smidigt.
*Tillräcklig bandbredd* beror på mängden anslutna AEM-skärmar och på hur andra användare använder nätverket, till exempel smarttelefoner, surfplattor, kassörer, datorer eller WIFI-gästnätverk.

>[!NOTE]
>Alla enheter har samtidig åtkomst till internetanslutningen och bandbredden minskar vanligtvis linjärt när du lägger till fler konsumenter eller datorer i nätverket.

### Lokalt nätverk {#lan-connection}

Prestandan hos LAN (Local Area Network) är, förutom att det är möjligt att nå nätverket, att tillhandahålla tillräcklig bandbredd för att fungera smidigt och smidigt med AEM Screens.

På den tiden matchar LAN-nätverket inom företagsorganisationer vanligtvis minst ett 1 000 MBit/sek-nätverk, så att det bör finnas tillräcklig bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder andra aktiva nätverkskomponenter är det obligatoriskt att alla dessa stämmer överens med kraven för nätverksbandbredd.

Nätverkskomponenterna bör till exempel minst matcha 1000 Mbit/s standard och matcha den bandbredd som anges i specifikationen Internet Access/Router.

### Specifikationer för andra företagsnätverk {#other-networks}

Vanligtvis har företagsnätverk anslutna enheter, kan delas upp i olika undernätverk och kan ha redundanta eller multiplexade internetanslutningar för att ge tillräcklig prestanda för många tusen samtidiga åtkomster.
Ovanstående schema är förenklat och passar i de flesta fall den miljö som är tillgänglig för klienten.
Om en WiFI-lösning planeras att ansluta skärmen till Internet Link rekommenderar vi att du använder moderna WIFI-standarder som IEEE 802.11g som minimum. Den här standarden stöder anslutningar på upp till 54 Mbit/s. Alla &quot;nyare&quot; standarder som 802.11h-n har bättre kvalitet. Om en WIFI-repeater krävs rekommenderar vi starkt åtkomstpunktstekniker för Mesh WIFI som Google Nest Mesh WIFI eller liknande.
Andra WiFi-upprepande tekniker leder till en enorm förlust av bandbredd i hela nätverket.

## Hämta media och resurser {#download}

AEM Screens har stora fördelar för användare av digitala signaturer. Hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och video. På grund av detta koncept uppstår den största nätverkstrafiken om det finns nytt innehåll som ska visas på en viss skärm.
För normal drift, t.ex. när du har definierat en spellista som inte ändras särskilt ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren. För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

Tabellerna nedan ger en god översikt över vilka data för nätverksanslutningsnyckel som krävs för prestanda som kan förväntas och möjliga väntetider.

All information ska ses som förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/enclosed-network-download.png)