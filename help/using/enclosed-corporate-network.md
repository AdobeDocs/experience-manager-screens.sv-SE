---
title: Enclosed Corporate Network
description: Enclosed Corporate Network
translation-type: tm+mt
source-git-commit: 31a6b202cae200e43e87db1df4e60f6f9d75c1bf
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Närstående företagsnätverk {#enclosed-corporate-networks}

Enclosed Corporate Network SetUp kan användas för mindre, större och större företag. Det kan vara teoretiskt mer komplext, men den logiska inställningen visas alltid som i ett förenklat exempel nedan.

## Krav för konfiguration av företagsnätverk {#requirements-enclosed-networks}

Enclosed Corporate Network Setup kan separeras logiskt i två block. WAN/Outer World/Internet Connection Block och det interna LAN/Local Area Network.

### WAN/Internetanslutning {#wan-connection}

Prestandan hos Internet Connection har, förutom att den redan beskrivna nätverksanslutningen är tillgänglig, även tillräcklig bandbredd för att AEM-skärmar ska fungera smidigt och smidigt.
I detalj beror&quot;tillräcklig&quot; på mängden anslutna AEM-skärmar och på hur andra konsumenter använder nätverket, till exempel smarttelefoner, surfplattor, kassörer, datorer eller Guest WIFI-nätverk.
Tänk på att alla enheter har samtidig åtkomst till Internet och att bandbredden vanligtvis minskar linjärt samtidigt som fler konsumenter/datorer läggs till i nätverket.

### LAN-anslutning {#lan-connection}

LAN-nätverkets prestanda har, utöver den redan beskrivna nätverkets nåbarhet, gett tillräcklig bandbredd för att AEM-skärmar ska fungera smidigt och smidigt. På den tiden matchar LAN-nätverket i företagsorganisationer vanligtvis minst ett 1 000 MBit/sek-nätverk, så att det bör finnas tillräcklig bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder en annan aktiv nätverkskomponent är det obligatoriskt att alla dessa stämmer överens med kraven för nätverkets bandbredd. Nätverkskomponenterna bör t.ex. minst motsvara standarden 1000 Mbit/s och motsvara den bandbredd som anges i specifikationen Internet Access/Router.

### Specifikationer för andra företagsnätverk {#other-networks}

Vanligtvis har företagsnätverk anslutna enheter, kan delas upp i olika undernätverk och kan ha redundanta eller multiplexade internetanslutningar för att ge tillräcklig prestanda för många tusen samtidiga åtkomster.
Ovanstående schema är förenklat och passar i de flesta fall den miljö som är tillgänglig för klienten.
Om en WiFI-lösning planeras att ansluta skärmen till Internet Link rekommenderar vi att du använder moderna WIFI-standarder som IEEE 802.11g som minimum. Den här standarden stöder anslutningar upp till 54 Mbit. Alla &quot;nyare&quot; standarder som 802.11h-n har bättre kvalitet. Om en WIFI-upprepning krävs rekommenderar vi varmt Mesh WIFI Accesspoint-teknik som Google Nest Mesh WIFI eller liknande.
Andra WiFi-upprepande tekniker leder till en enorm förlust av bandbredd i hela nätverket.

## Hämta media och resurser {#download}

AEM Screens ger stora fördelar för användare av digitala signaturer. Hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och video. På grund av detta koncept uppstår den största nätverkstrafiken om det finns nytt innehåll som ska visas på en viss skärm.
För normal drift, t.ex. när du har definierat en spellista som inte ändras särskilt ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren. För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

Tabellerna nedan ger en god översikt över vilka data för nätverksanslutningsnyckel som krävs för prestanda som kan förväntas och möjliga styrtider.

All information ska ses som förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.