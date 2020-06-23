---
title: Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter
description: Sidan beskriver mobilnätverk med Mobile Data Router och Active Network Components
translation-type: tm+mt
source-git-commit: 0be82fcc46166ec0613bd658a0caeab83bd72551
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---


# Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter {#mobile-network-setup}

Adobe AEM Screens-spelare kan också anslutas via mobilnätverk eller mobilnätverk som kör minst ett 3G-nätverk.
Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till spelarstyrenheten eller datorn och lagras korrekt i det underliggande operativsystemet. Den angivna bandbredden påverkar därför bara de inledande hämtningstiderna och påverkar inte Display Systems prestanda alls.

Fördelen med den här installationen är att mobilroutern kan placeras på en optimerad plats för att få bästa möjliga nätverkstäckning. Detta är vanligtvis i upphöjt och öppet läge med så lite omgivande betong eller metallkonstruktion som möjligt.
Denna SetUp ger AEM Screen Users stor flexibilitet eftersom det inte krävs någon fasta linje för att ansluta AEM Screens.

![](/help/using/assets/mobile-network-1.png)

## Ansluta AEM Screens Player till mobilnätverk med mobil datarouter och aktiva nätverkskomponenter {#connecting-aem-screens-players}

Följ stegen nedan för att ansluta AEM Screen-spelare i den här konfigurationen:

Konfigurationen innehåller en Internet-åtkomst för någon av AEM Screens-styrenheterna via direkt Internet-åtkomst med en egen 3/4/5G-datalänk.
Det är enkelt att ansluta AEM Screen-spelarna i den här konfigurationen:

1. Kontrollera att mobildataroutern är korrekt ansluten till det mobila datanätverket enligt operativsystemets anvisningar och att alla AEM-skärmspelare är anslutna till routernätverket.
1. Testa internetanslutningen genom att ringa en URL i systemwebbläsaren.
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



## Krav för konfiguration av mobilt nätverk med mobildatarouter och aktiva nätverkskomponenter {#requirements-direct}

Nätverksinstallationen kan logiskt separeras i två block:

* Mobil Internetanslutning

* Lokalt nätverk

### Mobil Internetanslutning {#mobile-internet-connection}

Prestandan hos Internet-anslutningen har, förutom att den redan beskrivna nätverksanslutningen är tillgänglig, gett tillräcklig bandbredd så att AEM Screens kan fungera smidigt och smidigt.

*Tillräckligt* beroende på hur många anslutna AEM-skärmar som används och på hur andra användare i nätverket använder sig, till exempel smarttelefoner, surfplattor, kassörer, datorer eller WIFI-nätverk för gäster.
Tänk på att alla enheter har samtidig åtkomst till Internet och att bandbredden vanligtvis minskar linjärt samtidigt som fler användare/datorer läggs till i nätverket.
Förutom den specifika teoretiska nätverksanslutningen måste man säkerställa att mobilrouterns täckning är åtminstone&quot;god&quot;. Dessutom måste den underliggande månadsplanen täcka in tillräckligt med datakapacitet och tillräcklig bandbredd för att alla anslutna klienter ska kunna betjäna det anslutna nätverket.
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
>För inledande överföring av mediefiler, till exempel, måste en högre datamängd och en ökad hämtningstid förväntas och återspeglas i ovanstående antaganden, samtidigt som nya spelare integreras. Ett 4G-nätverk med *bra* täckning och obegränsade data bör matcha de vanligaste installationerna i den här nätverksinstallationen.


### Lokalt nätverk {#lan-connection}

LAN-nätverkets prestanda har, utöver den redan beskrivna nätverkets nåbarhet, gett tillräcklig bandbredd så att AEM Screens kan fungera smidigt och smidigt. Under dessa dagar matchar LAN-nätverket vanligtvis minst ett 100 Mbit/s-nätverk, så att det bör finnas tillräcklig bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder en annan aktiv nätverkskomponent är det obligatoriskt att alla dessa stämmer överens med kraven för nätverkets bandbredd.

Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i specifikationen Internet Access/Router.
Om en WIFI-lösning planeras för att ansluta skärmen till Internet Link bör du använda moderna WIFI-standarder som IEEE 802.11g som minimum. Den här standarden stöder anslutningar på upp till 54 Mbit/s. Alla *nyare* standarder som 802.11h-n har bättre kvalitet. Om en WIFI-repeater krävs rekommenderar vi starkt åtkomstpunktstekniker för Mesh WIFI som Google Nest Mesh WIFI eller liknande.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, som bilder och video. På grund av detta koncept uppstår den största nätverkstrafiken om det finns nytt innehåll som ska visas på en viss skärm.
För normal drift, t.ex. när du har definierat en spellista som inte ändras särskilt ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.
För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.
Tabellerna nedan ger en god översikt över vilka data för nätverksanslutningsnyckel som krävs för prestanda som kan förväntas och möjliga väntetider.

>[!NOTE]
>All information avser förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/mobile-router-download.png)



