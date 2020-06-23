---
title: Direktåtkomst till Internet
description: Direktåtkomst till Internet
translation-type: tm+mt
source-git-commit: 77cf87cbce39a00528b2690d9689861b91e61fc5
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---


# Direkt Internet-nätverk (trådlöst/trådlöst) {#direct-internet-access}

Direct Internet Network innehåller en ingångspunkt för Internet-åtkomst för att nå AEM cloud services som AEM Screens måste ansluta till.

Standardportarna för AEM Screens-kommunikation är:
* `http (TCP Port 80)`
Eller
* `ssl-secured https (TCP Port 443)`

Portarna kan variera beroende på konfigurationen av din dedikerade AEM-konfiguration. I denna SetUp är alla enheter direkt anslutna till din Internet-router, vilket visas i bilden nedan.

![](/help/assets/direct-access-2.png)

I konfigurationen ingår även Internet-åtkomst från alla Internet-leverantörer (ISP) och dess Internet-linje. De flesta Internet-leverantörer tillhandahåller en Internetrouter som omfattar Internet-modem, nätverksswitchar, WIFI-åtkomstpunkter, brandväggar och andra nätverksfunktioner (beroende på tillverkare och modell).

## Ansluta AEM Screens Player till Direct Internet Access {#connecting-aem-screens-players}

Följ stegen nedan för att ansluta AEM Screen-spelare i den här konfigurationen:

1. Kontrollera att alla AEM Screen-spelare är anslutna till Routers Network.
1. Testa internetanslutningen genom att ringa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett felmeddelande bör du kontrollera nätverksinställningarna.Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration


1. Kontrollera att nätverkskortsinställningen matchar routerinställningen och kontrollera om det maximala antalet tillgängliga IP-adresser i nätverket inte nås.

1. Kontrollera om routern är korrekt ansluten till Internet (Internet Link). Detta kan också identifieras med en signallampa på standardroutrar.
1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

   >[!NOTE]
   >**Felsökningstips**
   >Om AEM Screens inte ansluter korrekt och inte visar det förväntade innehållet:
   >
   >1. Kontrollera brandväggen för Internetroutern om det finns några begränsningar för `TCP/IP Port 80/443`.
   >1. Kontrollera att alla portar som behövs tillåts.


## Krav för konfiguration av Direct Access Network {#requirements-direct}

Direct Internet Network kan logiskt separeras i två block:

* Wide Area Network

* Lokalt nätverk

### Wide Area Network {#wan-connection}

Utöver att nätverksanslutningen kan nås på Internet ska den tillhandahålla tillräcklig bandbredd för att AEM Screens ska fungera.

*Tillräckligt* beroende på hur många anslutna AEM-skärmar som används och hur andra konsumenter i nätverket använder sig av, till exempel smarttelefoner, surfplattor, kassörer, datorer eller WIFI-gäster.

>[!NOTE]
>Alla enheter har samtidig åtkomst till Internet-anslutningen och bandbredden minskar linjärt när du lägger till fler konsumenter eller datorer i nätverket.

### Lokalt nätverk {#lan-connection}

Prestandan för det lokala nätverket (LAN), förutom att nätverket är tillgängligt, ger tillräcklig bandbredd för att köra AEM Screens.

LAN-nätverket matchar vanligtvis minst ett 100 Mbit/s-nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet.
Om en WIFI-lösning planeras för att ansluta AEM Screens till Internet Link rekommenderar vi att man använder moderna WIFI-standarder som `IEEE 802.11g` ett minimum. Den här standarden stöder anslutningar på upp till 54 Mbit/s. Alla *nyare* standarder som `802.11h-n` är av bättre kvalitet.

>[!NOTE]
>Om en WIFI-repeater krävs rekommenderar vi starkt åtkomstpunktstekniker för Mesh WIFI som Google Nest Mesh WIFI eller liknande. Andra WiFi-upprepande tekniker slutar med en enorm förlust av bandbredd i hela nätverket.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. Den största nätverkstrafiken inträffar när det finns nytt innehåll som ska visas på en viss skärm.

För normala åtgärder, till exempel när du har definierat en spellista som uppdateras ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.

För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnycklar.

>[!NOTE]
>Med hjälp av informationen kan du visa förbrukningen för varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/assets/download-times-direct.png)

