---
title: Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter
description: Sidan beskriver mobilnätverk med Mobile Data Router och Active Network Components
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter {#mobile-network-setup}

Adobe AEM Screens-spelare kan också anslutas med mobilnätverk eller mobilnätverk som kör minst ett 3G-nätverk.

Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till spelarstyrenheten eller datorn och lagras på rätt sätt i det underliggande operativsystemet. Därför påverkar den angivna bandbredden bara de inledande hämtningstiderna och innehållsuppdateringarna och påverkar inte prestanda för vanlig uppspelning av bildskärmar.

Fördelen med den här konfigurationen är att den mobila routern kan placeras på en optimerad plats för att få bästa möjliga nätverkstäckning. Denna fläck är vanligen i upphöjt och öppet läge med så få omgivande bete- eller metallstrukturer som möjligt.
Den här inställningen ger AEM skärmanvändare flexibilitet eftersom det inte krävs någon fasta linje för att ansluta till AEM Screens. Det är också intressant för tillfälliga eller mobila miljöer.

I följande diagram visas det mobila nätverket med konfigurationen Mobile Data Router och Active Network Components. Den innehåller Internet-åtkomst för alla AEM Screens-styrenheter genom direkt Internet-åtkomst med en egen 3/4/5G-datalänk.

![](/help/using/assets/mobile-network-1.png)

## Ansluta AEM Screens Player till mobilnätverk med mobil datarouter och aktiva nätverkskomponenter {#connecting-aem-screens-players}

Följ stegen nedan för att se till att AEM skärmspelare är korrekt anslutna i den här konfigurationen:

Konfigurationen tilldelar en Internet-åtkomst för varje AEM Screens-styrenhet genom direkt Internet-åtkomst med en dedikerad 3/4/5G-datalänk.

1. Kontrollera att mobildataroutern är korrekt ansluten till det mobila datanätverket enligt operativsystemets anvisningar. Och se till att alla AEM skärmspelare är anslutna till routernätverket.
1. Testa Internetanslutningen genom att anropa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett fel kontrollerar du nätverksinställningarna. Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration

1. Kontrollera att nätverkskortsinställningen matchar routerinställningen.

1. Kontrollera om routern är korrekt ansluten till Internet-leverantörens Wide Area Network (Internet Link). Du kan kontrollera med hjälp av en signallampa på standardroutrar.
1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

   >[!TIP]
   >Du kan upptäcka att AEM Screens-anslutningen inte fungerar som den ska. Det förväntade innehållet visas inte. I sådana fall bör du kontrollera Internet Router-brandväggen om det finns några begränsningar för `TCP/IP Port 80/443`.


## Konfigurera mobilnätverk med mobil datarouter och aktiva nätverkskomponenter {#requirements-direct}

Nätverksinstallationen kan logiskt separeras i två block:

* Mobil Internetanslutning

* Lokalt nätverk

### Mobil Internetanslutning {#mobile-internet-connection}

Prestandan för internetanslutningen måste, förutom den redan beskrivna nätverksanslutningen, tillhandahålla tillräcklig bandbredd för att AEM Screens-nedladdningar ska fungera smidigt.

*Tillräckligt* beror på antalet anslutna AEM Screens-enheter. Det beror också på användningen av andra konsumenter i nätverket, t.ex. smarttelefoner, surfplattor, kassörer, datorer eller Gästnätverk för Wi-Fi.
Tänk på att alla enheter har samtidig åtkomst till Internet och att bandbredden minskar linjärt samtidigt som fler konsumenter/datorer läggs till i nätverket.
Förutom den specifika teoretiska nätverksanslutningen måste det säkerställas att den mobila routerns täckning är minst *bra*. Dessutom måste den underliggande månadsplanen täcka in tillräckligt med datakapacitet och tillräcklig bandbredd för att alla anslutna klienter ska kunna betjäna det anslutna nätverket.

Följande tabell visar datanätverken med deras standardbandbredd:

| Datanätverk | Bandbredd |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5 G | 1 000 - 1 000 Mbit/s |

När du funderar på vilket datanätverk som ska användas rekommenderar Adobe att du besvarar följande frågor:

* Hur många klienter är anslutna till routern?
* Hur många innehållsändringar som förväntas och vilka är de genomsnittliga filstorlekarna?

>[!NOTE]
>
>Datapaketet måste vara minst:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>För inledande överföring av mediefiler och integrering av nya spelare måste man förvänta sig en högre datamängd och längre hämtningstid. Den återspeglas också i ovanstående antaganden. Ett 4G-nätverk med *bra* täckning och obegränsade data bör matcha de vanligaste installationerna i den här nätverksinstallationen.


### Lokalt nätverk {#lan-connection}

LAN-nätverkets prestanda, förutom den redan beskrivna nätverkets nåbarhet, måste ge tillräcklig bandbredd för att AEM Screens-nedladdningar ska fungera smidigt. I dessa dagar matchar LAN-nätverket vanligtvis minst ett 100 Mbit/s-nätverk, så att det bör finnas tillräcklig bandbredd för att ansluta många enheter med bra prestanda till systemet. När du använder andra aktiva nätverkskomponenter är det obligatoriskt att alla dessa stämmer överens med kraven för nätverkets bandbredd.

Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i specifikationen Internet Access/Router.

Om en Wi-Fi-lösning planeras för att ansluta skärmen till Internet Link rekommenderar vi att du använder moderna Wi-Fi-standarder som IEEE `802.11g` som minimum. Den här standarden stöder anslutningar på upp till 54 Mbit/s. Alla *nyare*-standarder som `802.11h-n` har bättre kvalitet. Om en Wi-Fi-repeater krävs rekommenderar Adobe att du använder Wi-Fi-åtkomstpunktsteknologier som Google Nest Mesh Wi-Fi eller liknande.

## Hämta media och Assets {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla mediefiler som behövs lokalt, till exempel bilder och video. På grund av detta koncept uppstår den största nätverkstrafiken om det finns nytt innehåll som ska visas på en viss skärm.
För normal drift, med en definierad spellista som inte uppdateras ofta, ger den en nästan nätverksoberoende åtgärd när alla filer sparas i spelaren.
I de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är dynamiskt är en snabb och tillförlitlig nätverksanslutning en förutsättning för en omedelbar skärmreaktion. Det ger bästa möjliga kundupplevelse.
Följande tabeller ger en god översikt över vilka data för nätverksanslutningsnyckel som kan användas för prestanda som kan förväntas och möjliga väntetider.

>[!NOTE]
>
>All information avser användningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/mobile-router-download.png)
