---
title: Direkt mobilnätverk
description: Sidan beskriver Direct Mobile Network Setup
translation-type: tm+mt
source-git-commit: 70dddffd46ebf1bd83b25515be548bc442e45fea
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 0%

---


# Direkt mobilnätverk {#mobile-network-setup}

AEM Screens Player kan också anslutas via mobilnätverk eller mobilnätverk som kör minst ett 3G-nätverk.

Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till spelarstyrenheten eller datorn och lagras korrekt i det underliggande operativsystemet. Den angivna bandbredden påverkar bara den inledande hämtningstiden och påverkar inte bildskärmens prestanda.

Anslutning av AEM Screens-spelare med en mobil 3/4/5G-anslutning till din mobiltjänstdataleverantör. Fördelen med den här installationen är att mobilroutern kan placeras på en optimerad plats för att få bästa möjliga nätverkstäckning. Detta är vanligtvis i upphöjt och öppet läge med så lite omgivande betong eller metallkonstruktion som möjligt.

Denna SetUp ger AEM Screen Users stor flexibilitet eftersom det inte krävs någon fast anslutning för att ansluta AEM Screens.

![](/help/using/assets/direct-mobile-1.png)

## Ansluta AEM Screens Player till Direct Mobile Network {#connecting-aem-screens-players}

Följ stegen nedan för att ansluta AEM Screen-spelare i den här konfigurationen:

1. Kontrollera att alla AEM Screen-spelare är anslutna till Routers Network.

1. Testa internetanslutningen genom att ringa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett felmeddelande bör du kontrollera nätverksinställningarna.Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration


1. Kontrollera att nätverkskortsinställningen matchar routerinställningen.

1. Kontrollera om routern är korrekt ansluten till Internet Wide Area Network (Internet Link). Detta kan också identifieras med en signallampa på standardroutrar.

1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera det därefter. Starta AEM Screens.

   >[!NOTE]
   >**Felsökningstips**
   >Om AEM Screens inte ansluter korrekt och inte visar det förväntade innehållet:
   >
   >1. Kontrollera brandväggen för Internetroutern om det finns några begränsningar för `TCP/IP Port 80/443`.
   >1. Kontrollera att alla portar som behövs tillåts.



## Krav för konfiguration av mobilt nätverk {#requirements-direct}

Nätverksinstallationen kan logiskt separeras i två block:

* Mobil Internetanslutning

* Lokalt nätverk

### Mobil Internetanslutning {#mobile-internet-connection}

Prestandan för Internet-anslutningen ger inte bara tillräcklig bandbredd för att AEM Screens ska fungera smidigt och smidigt.

*Tillräckligt* beroende på hur många anslutna AEM-skärmar som används och på hur andra användare i nätverket använder sig, till exempel smarttelefoner, surfplattor, kassörer, datorer eller WIFI-nätverk för gäster.
Tänk på att alla enheter har samtidig åtkomst till Internet och att bandbredden vanligtvis minskar linjärt samtidigt som fler användare/datorer läggs till i nätverket.
Förutom den specifika teoretiska nätverksanslutningen måste man se till att den mobila routerns täckning är åtminstone&quot;god&quot; (se din mobilrouterhandbok). Dessutom måste den underliggande månadsplanen täcka in tillräckligt med datakapacitet och tillräcklig bandbredd för att alla anslutna klienter ska kunna betjäna det anslutna nätverket.

Datanätverken ger standardbandbredd med:

**3G**
* 42 Mbit/s

**4G**
* 150 Mbit/s

**5G**
* 1000 Mbit/s-10000 Mbit/s

När du överväger vilket datanätverk som ska användas bör du svara på följande frågor:

* Hur många klienter är anslutna till routern?

* Hur många innehållsändringar som förväntas och vilka är de genomsnittliga filstorlekarna?

>[!NOTE]
>Datapaketet måste vara minst:
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Se till att det finns tillräckligt med buffert.
>För inledande överföring av mediefiler, t.ex. genom integrering av nya spelare, måste en större mängd data och en ökad hämtningstid förväntas och återspeglas i ovanstående antaganden.Ett 4G-nätverk med *bra* täckning och *obegränsade* data bör matcha de vanligaste installationerna i den här nätverksinstallationen.


### Lokalt nätverk {#lan-connection}

LAN-nätverkets prestanda har, utöver den redan beskrivna nätverkets nåbarhet, gett tillräcklig bandbredd så att AEM Screens kan fungera smidigt och smidigt. Under dessa dagar matchar LAN-nätverket vanligtvis minst ett 100 Mbit/s-nätverk, så att det bör finnas tillräcklig bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder en annan aktiv nätverkskomponent är det obligatoriskt att alla dessa stämmer överens med kraven för nätverkets bandbredd. Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i specifikationen Internet Access/Router.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, som bilder och video. På grund av detta koncept inträffar den största nätverkstrafiken om det finns nytt innehåll som ska visas på en viss skärm.
För normal åtgärd, till exempel en definierad spellista som inte ändras särskilt ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.
För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

I följande tabell visas en översikt över vilka data för nätverksanslutningsnyckel som kan användas för prestanda som kan förväntas och möjliga väntetider.
>[!NOTE]
>All information avser förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/download-times-mobile.png)



