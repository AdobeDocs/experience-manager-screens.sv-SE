---
title: Direktåtkomst till Internet
description: Direktåtkomst till Internet
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# Direkt Internet-nätverk (trådlöst/trådlöst) {#direct-internet-access}

Direct Internet Network innehåller en ingångspunkt för Internet-åtkomst för att nå de AEM Cloud-tjänster som AEM Screens behöver för att ansluta till.

Standardportarna för kommunikation med AEM Screens är:
* `ssl-secured https (TCP Port 443)`

   <br>Eller</br>

* `http (TCP Port 80)`, om ditt specifika användningsfall inte kräver den säkerhetsnivån.

Portarna kan variera beroende på konfigurationen av den dedikerade AEM. I denna SetUp är alla enheter direkt anslutna till din Internet-router, vilket visas i bilden nedan.

![](/help/assets/direct-access-2.png)

I konfigurationen ingår även Internet-åtkomst från alla Internet-leverantörer (ISP) och dess Internet-linje. De flesta Internet-leverantörer tillhandahåller en Internetrouter som omfattar Internet-modem, nätverksswitchen, Wi-Fi-åtkomstpunkten, brandväggen och andra nätverksfunktioner (beroende på tillverkare och modell).

## Ansluta AEM Screens Player till Direct Internet Access {#connecting-aem-screens-players}

Följ stegen nedan för att se till att AEM skärmspelare är korrekt anslutna i den här konfigurationen:

1. Kontrollera att alla AEM skärmspelare är anslutna till routerns nätverk.
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


## Konfigurera Direct Access Network {#requirements-direct}

Direct Internet Network är logiskt uppdelat i två block:

* Wide Area Network

* Lokalt nätverk

### Wide Area Network {#wan-connection}

Prestandan för internetanslutningen, förutom att nätverket kan nås, är att tillhandahålla tillräcklig bandbredd för att AEM Screens ska fungera.

*Tillräcklig* effektivitet beror på antalet anslutna AEM och på hur andra konsumenter använder nätverket, till exempel smarttelefoner, surfplattor, kassörer, datorer eller Wi-Fi-gäster.

>[!NOTE]
>
>Alla enheter som nämns ovan har samtidig åtkomst till Internet-anslutningen och bandbredden minskar linjärt när du lägger till fler konsumenter eller datorer i nätverket.

### Lokalt nätverk {#lan-connection}

Prestandan för det lokala nätverket (LAN), förutom att nätverket kan nås, ger tillräcklig bandbredd för att AEM Screens ska fungera.

LAN-nätverket matchar vanligtvis minst ett 100 Mbit/s-nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet.
Om en Wi-Fi-lösning planeras för att ansluta AEM Screens till Internet Link rekommenderar vi att du åtminstone använder moderna Wi-Fi-standarder som `IEEE 802.11g`. Den här standarden stöder anslutningar på upp till 54 Mbit/s. Alla *nyare*-standarder som `802.11h-n` har bättre kvalitet.

>[!NOTE]
>
>Om en Wi-Fi Repeater krävs rekommenderas en trådlös nätanslutningspunkt som Google Nest Mesh Wi-Fi eller liknande. Andra Wi-Fi-upprepande tekniker slutar med en enorm förlust av bandbredd i hela nätverket.

## Hämtar media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. Den största nätverkstrafiken inträffar när det finns nytt innehåll som ska visas på en viss skärm.

För vanliga åtgärder, till exempel, är en definierad spellista som uppdateras ofta under dagen en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.

För scenarier där det förekommer mer interaktion med sensorer eller utlösare och dynamiskt innehåll är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion som säkerställer bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnycklar.

>[!NOTE]
>
>Med hjälp av informationen kan du visa förbrukningen för varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/assets/download-times-direct.png)

