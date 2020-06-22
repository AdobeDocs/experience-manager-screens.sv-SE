---
title: Inställningar för mobilnätverk
description: Sidan beskriver Mobile Network Setup
translation-type: tm+mt
source-git-commit: e24fa2fbec09cbe863a3615e722ae61b57da5012
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---


# Inställningar för mobilnätverk {#mobile-network-setup}

AEM Screens Player kan också anslutas via mobilnätverk eller mobilnätverk som kör minst ett 3G-nätverk.

Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till Player Controller eller Computer och lagras på rätt sätt i det underliggande operativsystemet. Den angivna bandbredden påverkar bara den inledande hämtningstiden och påverkar inte bildskärmens prestanda.

Anslutning av AEM Screens-spelare med en mobil 3/4/5G-anslutning till din mobiltjänstdataleverantör. Fördelen med den här installationen är att mobilroutern kan placeras på en optimerad plats för att få bästa möjliga nätverkstäckning. Detta är vanligtvis i upphöjt och öppet läge med så lite omgivande betong eller metallkonstruktion som möjligt.

Denna SetUp ger AEM Screen Users stor flexibilitet eftersom det inte krävs någon fast anslutning för att ansluta AEM Screens.

![](/help/using/assets/mobile-network-1.png)

>[!NOTE]
>**Felsökningstips **>Om AEM Screens inte ansluter korrekt och inte visar det förväntade innehållet:
>
>1. Kontrollera brandväggen för Internetroutern om det finns några begränsningar för `TCP/IP Port 80/443`.
>1. Kontrollera att alla portar som behövs tillåts och försök igen.



## Krav för konfiguration av mobilt nätverk {#requirements-direct}

Nätverksinställningarna som beskrivs i 5.5 kan logiskt separeras i tre block. WAN/Outer World/Internet Connection Block (här mobil dataanslutning), det interna LAN/Local Area Network och valfria underavsnitt i LAN avgränsade med Active Network Components.
För att få bästa möjliga prestanda måste man se till att båda avsnitten uppfyller de rekommenderade minimistandarderna.
Vad betyder&quot;bra prestanda&quot; i AEM Screens-miljön?
AEM Screens har stora fördelar för användare av digitala signaturer. Hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och video. På grund av detta koncept uppstår den största nätverkstrafiken om det finns nytt innehåll som ska visas på en viss skärm.
För normal drift, t.ex. när du har definierat en spellista som inte ändras särskilt ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.
För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.
Tabellerna nedan ger en god översikt över vilka data för nätverksanslutningsnyckel som krävs för prestanda som kan förväntas och möjliga styrtider.
All information ska ses som förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.


### WAN/Internetanslutning {#wan-connection}

Prestandan hos Internet-anslutningen har, förutom att den redan beskrivna nätverksanslutningen är tillgänglig, gett tillräcklig bandbredd så att AEM Screens kan fungera smidigt och smidigt. I detalj beror&quot;tillräcklig&quot; på mängden anslutna AEM-skärmar och på hur andra konsumenter använder nätverket, till exempel smarttelefoner, surfplattor, kassörer, datorer eller Guest Wifi-nätverk.
Tänk på att alla enheter har samtidig åtkomst till Internet och att bandbredden vanligtvis minskar linjärt samtidigt som fler konsumenter/datorer läggs till i nätverket.
Förutom den specifika teoretiska nätverksanslutningen måste man se till att den mobila routerns täckning är åtminstone&quot;god&quot; (se din mobilrouterhandbok). Dessutom måste den underliggande månadsplanen täcka in tillräckligt med datakapacitet och tillräcklig bandbredd för att alla anslutna klienter ska kunna betjäna det anslutna nätverket.
Datanätverken har en standardbandbredd på cirka. upp till:
・ 3Go 42 Mbit/s ・ 4Go 150 Mbit/sek ・ 5Go 1000Mbit/sek-10000Mbit/sekNär du funderar på vilket datanätverk som ska användas bör du svara på följande frågor:
・ Hur många klienter är anslutna till routern?
・ Hur många innehållsändringar kan jag förvänta mig och vilka är de genomsnittliga filstorlekarna?
Som en uppföljning måste det nödvändiga datapaketet vara minst:
Datapaketkapacitet = antal klienter * (# av innehållsfiler * genomsnittlig filstorlek)Kontrollera att det finns tillräckligt med buffert.
Obs! För inledande överföring av mediefiler, t.ex. genom integrering av nya spelare, måste en större mängd data och en ökad hämtningstid förväntas och återspeglas i ovanstående antaganden.
En tumregel är att ett 4G-nätverk med&quot;bra&quot; täckning och obegränsade data bör matcha de vanligaste installationerna i den här nätverksinstallationen


### LAN-anslutning {#lan-connection}

LAN-nätverkets prestanda har, utöver den redan beskrivna nätverkets nåbarhet, gett tillräcklig bandbredd så att AEM Screens kan fungera smidigt och smidigt. Under dessa dagar matchar LAN-nätverket vanligtvis minst ett 100 MBit/sek-nätverk, så att det ska finnas tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder en annan aktiv nätverkskomponent är det obligatoriskt att alla dessa stämmer överens med kraven för nätverkets bandbredd. Nätverkskomponenterna bör t.ex. minst motsvara standarden 100 Mbit/s och motsvara den bandbredd som anges i specifikationen Internet Access/Router.
Om en WiFI-lösning planeras att ansluta skärmen till Internet Link rekommenderar vi att du använder moderna WIFI-standarder som IEEE 802.11g som minimum. Den här standarden stöder anslutningar upp till 54 Mbit. Alla &quot;nyare&quot; standarder som 802.11h-n har bättre kvalitet. Om en Wifi Repeater krävs rekommenderar vi starkt åtkomstpunktstekniker för Mesh Wifi, som Google Nest Mesh Wifi eller liknande.
Andra WiFi-upprepande tekniker leder till en enorm förlust av bandbredd i hela nätverket.
