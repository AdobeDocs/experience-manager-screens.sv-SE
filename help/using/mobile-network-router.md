---
title: Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter
description: Sidan beskriver mobilnätverk med Mobile Data Router och Active Network Components
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter {#mobile-network-setup}

Adobe AEM Screens-spelare kan också anslutas med mobilnätverk eller mobilnätverk som kör minst ett 3G-nätverk.

Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till spelarstyrenheten eller datorn och lagras på rätt sätt i det underliggande operativsystemet. Därför påverkar den angivna bandbredden bara de inledande hämtningstiderna samt innehållsuppdateringar, och påverkar inte prestanda för regelbunden uppspelning av bildskärmar.

Fördelen med den här konfigurationen är att mobilroutern kan placeras på en optimerad plats för att säkerställa bästa möjliga tillgängliga nätverkstäckning. Detta är vanligtvis i upphöjt och öppet läge med så lite omgivande betong- eller metallkonstruktion som möjligt.
Med den här inställningen kan AEM skärmanvändare vara flexibla eftersom det inte krävs någon fasta linje för att ansluta till AEM Screens. Detta är särskilt intressant för tillfälliga eller mobila miljöer.

I följande diagram visas Mobile Network with Mobile Data Router and Active Network Components configuration and contains an Internet access of any of the AEM Screens controller by direct Internet access using an own 3/4/5G Data Link.

![](/help/using/assets/mobile-network-1.png)

## Ansluta AEM Screens Player till mobilnätverk med mobil datarouter och aktiva nätverkskomponenter {#connecting-aem-screens-players}

Följ stegen nedan för att se till att AEM skärmspelare är korrekt anslutna i den här konfigurationen:

Konfigurationen tilldelar en Internet-åtkomst för varje AEM Screens-styrenhet genom direkt Internet-åtkomst med en dedikerad 3/4/5G-datalänk.

1. Kontrollera att mobildataroutern är korrekt ansluten till det mobila datanätverket enligt operativsystemets anvisningar och att alla AEM är anslutna till routernätverket.
1. Testa Internetanslutningen genom att ringa en URL i systemwebbläsaren.
   >[!NOTE]
   >Om du får ett fel kontrollerar du nätverksinställningarna.Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration


1. Kontrollera att nätverkskortsinställningen matchar routerinställningen.

1. Kontrollera om routern är korrekt ansluten till Internet Wide Area Network (Internet Link). Detta kan också identifieras med en signallampa på standardroutrar.
1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

   >[!NOTE]
   >**Felsökningstips**
   >Om AEM Screens inte ansluter som det ska och det förväntade innehållet inte visas, bör du kontrollera om det finns några begränsningar för Internet Router-brandväggen `TCP/IP Port 80/443`.


## Konfigurera mobilnätverk med mobil datarouter och aktiva nätverkskomponenter {#requirements-direct}

Nätverksinstallationen kan logiskt separeras i två block:

* Mobil Internetanslutning

* Lokalt nätverk

### Mobil Internetanslutning {#mobile-internet-connection}

Prestandan för internetanslutningen måste, förutom den redan beskrivna nätverksanslutningen, tillhandahålla tillräcklig bandbredd för att AEM Screens-nedladdningar ska fungera smidigt.

*Tillräckligt* beror på mängden anslutna AEM skärmar och på hur andra användare i nätverket använder sig, t.ex. smarttelefoner, surfplattor, kassörer, datorer eller Gästnätverk för Wi-Fi.
Tänk på att alla enheter har samtidig åtkomst till Internet och att bandbredden vanligtvis minskar linjärt samtidigt som fler användare/datorer läggs till i nätverket.
Förutom den specifika teoretiska nätverksanslutningen måste det säkerställas att mobilrouterns täckning är åtminstone&quot;god&quot;. Den underliggande månadsplanen måste även täcka in tillräckligt med datapacitet och tillräcklig bandbredd för att alla anslutna klienter ska kunna betjäna det anslutna nätverket.

I följande tabell visas datanätverken med sin standardbandbredd:

| Datanätverk | Bandbredd |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 - 1 000 Mbit/s |

När du överväger vilket datanätverk som ska användas bör du svara på följande frågor:

* Hur många klienter är anslutna till routern?

* Hur många innehållsändringar som förväntas och vilka är de genomsnittliga filstorlekarna?

>[!NOTE]
>
>Datapaketet måste vara minst:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>För inledande överföring av mediefiler, till exempel, måste en högre datamängd och en ökad hämtningstid förväntas och återspeglas i ovanstående antaganden, samtidigt som nya spelare integreras. Ett 4G-nätverk med *bra* täckning och obegränsat antal data bör matcha de vanligaste installationerna i den här nätverksinställningarna.


### Lokalt nätverk {#lan-connection}

LAN-nätverkets prestanda, förutom den redan beskrivna nätverkets nåbarhet, måste ge tillräcklig bandbredd för att AEM Screens-nedladdningar ska fungera smidigt. Under dessa dagar matchar LAN-nätverket vanligtvis minst ett 100 Mbit/s-nätverk, så att det bör finnas tillräcklig bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder en annan aktiv nätverkskomponent är det obligatoriskt att alla dessa stämmer överens med kraven för nätverkets bandbredd.

Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i specifikationen Internet Access/Router.

Om en Wi-Fi-lösning planeras för att ansluta skärmen till Internet Link rekommenderar vi att du åtminstone använder moderna Wi-Fi-standarder som IEEE 802.11g. Den här standarden stöder anslutningar på upp till 54 Mbit/s. Alla *nyare* Standarder som 802.11h-n har bättre kvalitet. Om en Wi-Fi Repeater krävs rekommenderar vi starkt trådlös nätanslutningspunkt som Google Nest Mesh Wi-Fi eller liknande.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, som bilder och video. På grund av detta koncept uppstår den största nätverkstrafiken om det finns nytt innehåll som ska visas på en viss skärm.
För normal åtgärd, till exempel om du har definierat en spellista som inte uppdateras ofta under dagen, är detta en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.
För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.
Tabellerna nedan ger en god översikt över vilka data för nätverksanslutningsnyckel som krävs för prestanda som kan förväntas och möjliga väntetider.

>[!NOTE]
>
>All information avser förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/mobile-router-download.png)
