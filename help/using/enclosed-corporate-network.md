---
title: Enclosed Corporate Network
description: Enclosed Corporate Network
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# Enclosed Corporate Network (Wired/Wireless) {#enclosed-corporate-networks}

Enclosed Corporate Network SetUp är tillgängligt för mindre, större och större företag. Den kan vara teoretiskt mer komplex och den logiska inställningen visas i figuren nedan.

![](/help/using/assets/enclosed-network-1.png)


## Ansluta AEM Screens Player till Direct Internet Access {#connecting-aem-screens-players}

Följ stegen nedan för att se till att AEM skärmspelare är korrekt anslutna i den här konfigurationen:

1. Kontrollera att alla AEM skärmspelare är anslutna till routernätverket.
1. Testa internetanslutningen genom att ringa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett fel kontrollerar du nätverksinställningarna.Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration


1. Kontrollera att nätverkskortsinställningen matchar routerinställningarna och kontrollera om det maximala antalet tillgängliga IP-adresser i nätverket inte nås.

1. Kontrollera om routern är korrekt ansluten till Internet (Internet Link). Detta kan också identifieras med en signallampa på standardroutrar.
1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

   >[!NOTE]
   >**Felsökningstips**
   >Om AEM Screens inte ansluter korrekt och det förväntade innehållet inte visas:
   >
   >1. Kontrollera brandväggen för Internetroutern om det finns begränsningar för `TCP/IP Port 80/443`.
   >1. Kontrollera att alla portar som krävs tillåts.


## Konfigurera Enclosed Corporate Networks {#requirements-enclosed-networks}

Enclosed Corporate Network Setup kan separeras logiskt i två block:

* WAN (Wide Area Network)
* Internt LAN (Local Area Network).

### Wide Area Network {#wan-connection}

Prestandan för internetanslutningen måste, förutom nätverkets nåbarhet, tillhandahålla tillräcklig bandbredd för att AEM Screens-innehållsuppdateringar ska fungera smidigt.
*Tillräcklig* bandbredd beror på mängden anslutna AEM och hur många andra användare som använder nätverket, till exempel smarttelefoner, surfplattor, kassörer, datorer eller Wi-Fi-gäster.

>[!NOTE]
>
>Alla enheter har samtidig åtkomst till internetanslutningen och bandbredden minskar linjärt när du lägger till fler konsumenter eller datorer i nätverket.

### Lokalt nätverk {#lan-connection}

Prestandan hos det lokala nätverket (LAN) måste, förutom att det går att nå nätverket, tillhandahålla tillräcklig bandbredd för att AEM Screens innehållsuppdateringar ska fungera smidigt.

LAN-nätverket inom företagsorganisationer är vanligtvis minst 1 000 MB/sek-nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder andra aktiva nätverkskomponenter är det obligatoriskt att alla dessa stämmer överens med kraven för nätverksbandbredd.

Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i specifikationen Internet-åtkomst/router.

### Specifikationer för andra företagsnätverk {#other-networks}

Företagsnätverk har ett antal anslutna enheter, är indelade i olika undernätverk och har redundanta eller multiplexade internetanslutningar för att ge tillräcklig prestanda för många tusen samtidiga åtkomster.
Det här schemat är förenklat och passar de flesta miljöer som är tillgängliga för klienten.

Om en Wi-Fi-lösning planeras för att ansluta skärmar till Internet Link rekommenderar vi att du åtminstone använder moderna Wi-Fi-standarder som `IEEE 802.11g`. Denna standard stöder anslutningar upp till 54 Mbit/s. Alla *nyare*-standarder som `802.11h-n` har bättre kvalitet. Om en Wi-Fi Repeater krävs rekommenderar vi starkt åtkomstpunktsteknologier som Google Nest Mesh Wi-Fi eller liknande.
Andra Wi-Fi-upprepande tekniker slutar med en enorm förlust av bandbredd i hela nätverket.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. Den största nätverkstrafiken inträffar när det finns nytt innehåll som ska visas på en viss skärm.

För vanliga åtgärder, till exempel, är en definierad spellista som uppdateras ofta under dagen en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.

För scenarier där det förekommer mer interaktion med sensorer eller utlösare och dynamiskt innehåll är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion som säkerställer bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnycklar.

>[!NOTE]
>Med hjälp av informationen kan du visa förbrukningen för varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/enclosed-network-download.png)
