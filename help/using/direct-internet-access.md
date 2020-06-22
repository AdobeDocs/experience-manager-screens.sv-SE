---
title: Direktåtkomst till Internet
description: Direktåtkomst till Internet
translation-type: tm+mt
source-git-commit: 88ba9ab26c4ecc3f829f53244117041a9a1fd2b3
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---


# Direktåtkomst till Internet {#direct-internet-access}

SetUp för Direct Internet Access innehåller en åtkomstpunkt för Internet-åtkomst för att nå den AEM cloud services som AEM Screens måste ansluta till.

Standardportarna för AEM Screens-kommunikation är:
* `http (TCP Port 80)`
Eller
* `ssl-secured https (TCP Port 443)`

Portarna kan variera beroende på konfigurationen av din dedikerade AEM-konfiguration. I denna SetUp är alla enheter direkt anslutna till din internetrouter, vilket visas i bilden nedan.

![](/help/assets/direct-access-2.png)

I konfigurationen ingår även Internet-åtkomst från alla Internet-leverantörer (ISP) och Internet Line. De flesta Internet-leverantörer har en Internetrouter som omfattar Internet-modem, nätverksswitchar, WIFI-åtkomstpunkter, brandväggar och andra nätverksfunktioner (beroende på tillverkare och modell).

>[!NOTE]
>**Felsökningstips **>Om AEM Screens inte ansluter korrekt och inte visar det förväntade innehållet:
>
>1. Kontrollera brandväggen för Internetroutern om det finns några begränsningar för `TCP/IP Port 80/443`.
>1. Kontrollera att alla portar som behövs tillåts och försök igen.


## Krav för konfiguration av Direct Access Network {#requirements-direct}

Nätverksinställningarna för Direct Access kan logiskt separeras i två block. WAN/Outer World/Internet Connection Block och det interna LAN/Local Area Network.

### WAN/Internetanslutning {#wan-connection}

Prestandan hos Internet-anslutningen har, förutom att den redan beskrivna nätverksanslutningen är tillgänglig, gett tillräcklig bandbredd så att AEM Screens kan fungera smidigt och smidigt. I detalj beror&quot;tillräcklig&quot; på mängden anslutna AEM-skärmar och på hur andra konsumenter använder nätverket, till exempel smarttelefoner, surfplattor, kassörer, datorer eller Guest WIFI-nätverk.
Tänk på att alla enheter har samtidig åtkomst till Internet och att bandbredden vanligtvis minskar linjärt samtidigt som fler användare/datorer läggs till i nätverket.

### LAN-anslutning {#lan-connection}

LAN-nätverkets prestanda har, utöver den redan beskrivna nätverkets nåbarhet, gett tillräcklig bandbredd så att AEM Screens kan fungera smidigt och smidigt. Under dessa dagar matchar LAN-nätverket vanligtvis minst ett 100 MBit/sek-nätverk, så att det ska finnas tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet.
Om en WIFI-lösning planeras för att ansluta skärmen till Internet Link bör du använda moderna WIFI-standarder som IEEE 802.11g som ett minimum. Den här standarden stöder anslutningar upp till 54 Mbit. Alla *nyare* standarder som 802.11h-n har bättre kvalitet. Om en WIFI-repeater krävs rekommenderar vi starkt åtkomstpunktstekniker för Mesh WIFI som Google Nest Mesh WIFI eller liknande.
Andra WiFi-upprepande tekniker leder till en enorm förlust av bandbredd i hela nätverket.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videoklipp. På grund av detta koncept uppstår den största nätverkstrafiken om det finns nytt innehåll som ska visas på en viss skärm.
För normal åtgärd, till exempel om du har definierat en spellista som inte ändras särskilt ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.
För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnyckel:

![](/help/assets/download-times-direct.png)

>[!NOTE]
>Med hjälp av informationen kan du visa förbrukningen för varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger nedladdningstiden.