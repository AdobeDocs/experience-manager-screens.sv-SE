---
title: Direktåtkomst till Internet
description: Direktåtkomst till Internet
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 0%

---


# Direktåtkomst till Internet {#direct-internet-access}

SetUp för Direct Internet Access innehåller en åtkomstpunkt för Internet-åtkomst för att nå den AEM cloud services som AEM Screens behöver ansluta till.

Standardportarna för AEM Screens-kommunikation är:
* `http (TCP Port 80)`
Eller
* `ssl-secured https (TCP Port 443)`

Portarna kan variera beroende på konfigurationen av din dedikerade AEM-konfiguration. I denna SetUp är alla enheter direkt anslutna till din internetrouter, vilket visas i bilden nedan.

![](/help/assets/direct-access-2.png)

I konfigurationen ingår även Internet-åtkomst från alla Internet-leverantörer (ISP) och Internet Line. De flesta Internet-leverantörer har en Internetrouter som omfattar Internet-modem, nätverksswitchar, WIFI-åtkomstpunkter, brandväggar och andra nätverksfunktioner (beroende på tillverkare och modell).

## Ansluta AEM Screens Player till Direct Internet Access {#connecting-aem-screens-players}

Följ stegen nedan för att ansluta AEM Screen-spelare i den här konfigurationen:

1. Kontrollera att alla AEM Screen-spelare är anslutna till Routers Network.
1. Testa internetanslutningen genom att ringa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett felmeddelande bör du kontrollera nätverksinställningarna.Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration


1. Kontrollera att nätverkskortsinställningen matchar routerinställningen och kontrollera om det maximala antalet tillgängliga IP-adresser i nätverket inte nås.

1. Kontrollera om routern är korrekt ansluten till ISP Wide Area Network (Internet Link). Detta kan vanligtvis också identifieras med en Signal LED på standardroutrar.
1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera det därefter
1. Starta AEM Screens.

   >[!NOTE]
   >**Felsökningstips**
   >Om AEM Screens inte ansluter korrekt och inte visar det förväntade innehållet:
   >
   >1. Kontrollera brandväggen för Internetroutern om det finns några begränsningar för `TCP/IP Port 80/443`.
   >1. Kontrollera att alla portar som behövs tillåts.


## Krav för konfiguration av Direct Access Network {#requirements-direct}

Direct Access Network Setup kan logiskt separeras i två block:

* Wide Area Network

* Lokalt nätverk

### Wide Area Network {#wan-connection}

Prestandan för internetanslutningen är att den inte bara ska kunna nå nätverket, utan också att den ska ge tillräcklig bandbredd så att AEM Screens kan fungera smidigt och smidigt. I detalj beror&quot;tillräcklig&quot; på mängden anslutna AEM-skärmar och på hur andra konsumenter använder nätverket, till exempel smarttelefoner, surfplattor, kassörer, datorer eller Guest WIFI-nätverk.

>[!NOTE]
>Alla enheter har samtidig åtkomst till internetanslutningen och bandbredden minskar vanligtvis linjärt när du lägger till fler konsumenter/datorer i nätverket.

### Lokalt nätverk {#lan-connection}

Prestandan hos LAN (Local Area Network) ger, förutom nätverksnåbarheten, tillräcklig bandbredd för att AEM Screens ska fungera smidigt och smidigt.

LAN-nätverket matchar vanligtvis minst ett 100 MBit/sek-nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet.
Om en WIFI-lösning planeras för att ansluta AEM Screens till Internet Link bör man använda moderna WIFI-standarder som IEEE 802.11g som minimum. Den här standarden stöder anslutningar på upp till 54 Mbit/s. Alla *nyare* standarder som 802.11h-n har bättre kvalitet.

>[!NOTE]
>Om en WIFI-repeater krävs rekommenderar vi starkt åtkomstpunktstekniker för Mesh WIFI som Google Nest Mesh WIFI eller liknande. Andra WiFi-upprepande tekniker leder till en enorm förlust av bandbredd i hela nätverket.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. På grund av detta koncept inträffar den största nätverkstrafiken när det finns nytt innehåll som ska visas på en viss skärm.
För normal åtgärd, till exempel om du har definierat en spellista som inte ändras särskilt ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.
För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnyckel:

![](/help/assets/download-times-direct.png)

>[!NOTE]
>Med hjälp av informationen kan du visa förbrukningen för varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.