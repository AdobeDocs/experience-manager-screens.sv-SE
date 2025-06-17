---
title: Enclosed Corporate Network
description: Enclosed Corporate Network
exl-id: b8c52e72-86da-4089-ba02-0c643862419f
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Enclosed Corporate Network (Wired/Wireless) {#enclosed-corporate-networks}

Enclosed Corporate Network SetUp kan användas på mindre, större och större företag. Den kan vara teoretiskt mer komplex och den logiska inställningen visas i figuren nedan.

![](/help/using/assets/enclosed-network-1.png)


## Ansluta AEM Screens Player till Direct Internet Access

Följ stegen nedan för att säkerställa att AEM Screen Players är korrekt anslutna i den här konfigurationen:

1. Kontrollera att alla AEM Screen-spelare är anslutna till Routers Network.
1. Testa Internetanslutningen genom att anropa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett fel kontrollerar du nätverksinställningarna. Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration

1. Kontrollera att nätverkskortsinställningen matchar routerinställningarna och kontrollera om det maximala antalet tillgängliga IP-adresser i nätverket inte nås.

1. Kontrollera om routern är korrekt ansluten till ISP Wide-Area Network (Internet Link). Denna anslutning kan också identifieras med en signallampa på standardroutrar.
1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

   >[!NOTE]
   >**Felsökningstips**
   >Om AEM Screens inte ansluter korrekt och det förväntade innehållet inte visas:
   >
   >1. Kontrollera om det finns några begränsningar för `TCP/IP Port 80/443` i brandväggen för Internet Router.
   >1. Se till att alla portar som krävs tillåts.

## Konfigurera anslutna företagsnätverk {#requirements-enclosed-networks}

Enclosed Corporate Network Setup kan logiskt separeras i två block:

* WAN (Wide Area Network)
* Internt LAN.

### Wide Area Network {#wan-connection}

Prestandan för internetanslutningen måste, förutom nätverkets nåbarhet, tillhandahålla tillräcklig bandbredd för att AEM Screens-innehållsuppdateringar ska fungera smidigt.
*Tillräcklig bandbredd* beror på antalet anslutna AEM Screens. Det beror också på användningen av andra konsumenter i nätverket, till exempel smarttelefoner, surfplattor, kassörer, datorer eller Wi-Fi-gäster.

>[!NOTE]
>
>Alla enheter har samtidig åtkomst till internetanslutningen och bandbredden minskar linjärt när du lägger till fler konsumenter eller datorer i nätverket.

### Lokalt nätverk {#lan-connection}

Prestandan hos det lokala nätverket (LAN) måste, förutom att det går att nå nätverket, tillhandahålla tillräcklig bandbredd för att AEM Screens innehållsuppdateringar ska fungera smidigt.

LAN-nätverket inom företagsorganisationer är vanligtvis minst 1 000 MB/sek-nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder andra aktiva nätverkskomponenter är det obligatoriskt att alla matchar kraven för nätverksbandbredd.

Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i Internet-specifikationen för åtkomst/router.

### Specifikationer för andra företagsnätverk {#other-networks}

Företagsnätverk har flera anslutna enheter, är indelade i olika undernätverk och har redundanta eller multiplexade internetanslutningar som ger tillräcklig prestanda för många tusen samtidiga åtkomstmöjligheter.
Schemat är förenklat och passar de flesta miljöer som är tillgängliga för klienten.

Om en Wi-Fi-lösning planeras för att ansluta AEM Screens till Internet Link rekommenderar vi att du använder moderna Wi-Fi-standarder som `IEEE 802.11g` som ett minimum. Denna standard stöder anslutningar upp till 54 Mbit/s. Alla *nyare*-standarder som `802.11h-n` har bättre kvalitet. Om en Wi-Fi Repeater krävs rekommenderar Adobe åtkomstpunktsteknologier som Google Nest Mesh Wi-Fi eller liknande.
Andra Wi-Fi-upprepande tekniker slutar med en enorm förlust av bandbredd i hela nätverket.

## Hämta media och Assets {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. Den största nätverkstrafiken inträffar när det finns nytt innehåll som ska visas på en viss skärm.

För vanliga åtgärder, till exempel, erbjuder en definierad spellista som uppdateras ofta under dagen en nästan nätverksoberoende åtgärd när alla filer har sparats i spelaren.

För scenarier där det förekommer mer interaktion med sensorer eller utlösare och dynamiskt innehåll är en snabb och tillförlitlig nätverksanslutning en förutsättning för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnycklar.

>[!NOTE]
>Med hjälp av den här informationen kan du visa förbrukningen för varje enhet i nätverket genom att begära och hämta en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/enclosed-network-download.png)
