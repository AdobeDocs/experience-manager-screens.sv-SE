---
title: Direktåtkomst till Internet
description: Direktåtkomst till Internet
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# Direkt Internet-nätverk (trådlöst/trådlöst) {#direct-internet-access}

Direct Internet Network innehåller en ingångspunkt för Internet-åtkomst för att nå de AEM Cloud Service som AEM Screens måste ansluta till.

Standardportarna för kommunikation med AEM Screens är:

* `ssl-secured https (TCP Port 443)`
  <br>Eller</br>

* `http (TCP Port 80)`, om ditt specifika användningsfall inte kräver den säkerhetsnivån.

Portarna kan variera beroende på konfigurationen av den dedikerade AEM. I denna SetUp är alla enheter direkt anslutna till din Internet-router, vilket visas i bilden nedan.

![](/help/assets/direct-access-2.png)

I konfigurationen ingår även Internet-åtkomst från alla Internet-leverantörer (ISP) och dess Internet-linje. De flesta Internet-leverantörer har en Internet-router som omfattar Internet-modem, nätverksswitchen, Wi-Fi-åtkomstpunkten, brandväggen och andra nätverksfunktioner (beroende på tillverkare och modell).

## Ansluta AEM Screens Player till Direct Internet Access

Följ stegen nedan för att se till att AEM skärmspelare är korrekt anslutna i den här konfigurationen:

1. Kontrollera att alla AEM skärmspelare är anslutna till routerns nätverk.
1. Testa Internetanslutningen genom att anropa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett fel kontrollerar du nätverksinställningarna. Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration

1. Kontrollera att nätverkskortsinställningen matchar routerinställningarna. Kontrollera om det maximala antalet tillgängliga IP-adresser i nätverket inte nås.
1. Kontrollera om routern är korrekt ansluten till Internet Wide-Area-Network (Internet Link). Den kan också identifieras med en signallampa på standardroutrar.
1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

   >[!NOTE]
   >**Felsökningstips**
   >Om AEM Screens inte ansluter korrekt och det förväntade innehållet inte visas:
   >
   >1. Kontrollera brandväggen för Internet-routern om det finns begränsningar gällande `TCP/IP Port 80/443`.
   >1. Se till att alla portar som krävs tillåts.

## Konfigurera Direct Internet network {#requirements-direct}

Direct Internet Network är logiskt indelat i två block:

* Wide Area Network

* Lokalt nätverk

### Wide Area Network {#wan-connection}

Prestandan för internetanslutningen, förutom nätverkets nåbarhet, är att tillhandahålla tillräcklig bandbredd för att köra AEM Screens.

*Tillräckligt* beror på antalet anslutna AEM Screens. Det beror också på användningen av andra konsumenter i nätverket, t.ex. smarttelefoner, surfplattor, kassörer, datorer eller Wi-Fi-gäster.

>[!NOTE]
>
>De enheter som nämns ovan har samtidig åtkomst till internetanslutningen och bandbredden minskar linjärt när du lägger till fler konsumenter eller datorer i nätverket.

### Lokalt nätverk {#lan-connection}

Prestandan för det lokala nätverket (LAN), förutom nätverkets nåbarhet, är att tillhandahålla tillräcklig bandbredd för att AEM Screens ska fungera.

LAN-nätverket matchar vanligtvis minst ett 100 Mbit/s-nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet.
Om en Wi-Fi-lösning planeras för att ansluta AEM Screens till Internet Link rekommenderar vi att man använder moderna Wi-Fi-standarder som `IEEE 802.11g` som ett minimum. Den här standarden stöder anslutningar på upp till 54 Mbit/s. Alla *nyare* Standarder som `802.11h-n` är av bättre kvalitet.

>[!NOTE]
>
>Om en Wi-Fi-repeater krävs rekommenderar Adobe en trådlös nätanslutningspunkt som Google Nest Mesh Wi-Fi eller liknande. Andra Wi-Fi-upprepande tekniker slutar med en enorm förlust av bandbredd i hela nätverket.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. Den största nätverkstrafiken inträffar när det finns nytt innehåll som ska visas på en viss skärm.

För vanliga åtgärder, till exempel, erbjuder en definierad spellista som uppdateras ofta under dagen en nästan nätverksoberoende åtgärd när alla filer har sparats i spelaren.

För scenarier där det förekommer mer interaktion med sensorer eller utlösare och dynamiskt innehåll är en snabb och tillförlitlig nätverksanslutning en förutsättning för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnycklar.

>[!NOTE]
>
>Med hjälp av den här informationen kan du visa förbrukningen för varje enhet i nätverket genom att begära och hämta en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/assets/download-times-direct.png)
