---
title: Direkt mobilnätverk
description: Sidan beskriver Direct Mobile Network Setup
translation-type: tm+mt
source-git-commit: 8e62b3fc4ce324e02aaec6fca9df79b1aaf94d72
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# Direkt mobilnätverk {#mobile-network-setup}

AEM Screens Player kan också anslutas via mobilnätverk eller mobilnätverk som kör minst ett 3G-nätverk.

Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till spelarstyrenheten eller datorn och lagras korrekt i det underliggande operativsystemet. Den angivna bandbredden påverkar därför bara den inledande hämtningstiden och påverkar inte bildskärmens prestanda.

Anslutning av AEM Screens-spelare med en mobil 3/4/5G-anslutning till din dataleverantör för mobiltjänster. Fördelen med den här installationen är att mobilroutern kan placeras på en optimerad plats för att få bästa möjliga nätverkstäckning. Detta är vanligtvis i upphöjt och öppet läge med så optimal omgivande betong- eller metallkonstruktion som möjligt.

Med denna SetUp får AEM Screen-användare stor flexibilitet eftersom det inte krävs någon fast anslutning för att ansluta till AEM Screens.

I följande diagram visas Direct Mobile Network Setup och består av ett enda nätanslutningssegment, anslutningen för varje spelare till det mobila/mobila datanätverket.

![](/help/using/assets/direct-mobile-1.png)

## Ansluta AEM Screens Player till Direct Mobile Network {#connecting-aem-screens-players}

Följ stegen nedan för att ansluta AEM Screens-spelare i den här konfigurationen:

1. Kontrollera att alla AEM Screen-spelare är anslutna till Routers Network.

1. Testa internetanslutningen genom att ringa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett felmeddelande bör du kontrollera nätverksinställningarna.Det finns i princip två alternativ för en korrekt nätverksanslutning:
   >* DHCP
   >* Manuell IP-konfiguration


1. Kontrollera att nätverkskortsinställningen matchar routerinställningen.

1. Kontrollera om routern är korrekt ansluten till Internet Wide Area Network (Internet Link). Detta kan också identifieras med en signallampa på standardroutrar.

1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

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

Internet-anslutningens prestanda, förutom nätverksanslutning, ger tillräcklig bandbredd för att AEM Screens ska fungera smidigt.

*Tillräckligt* beroende på hur många anslutna AEM-skärmar som används och på hur andra användare i nätverket använder sig, till exempel smarttelefoner, surfplattor, kassörer, datorer eller WIFI-nätverk för gäster.

>[!NOTE]
>Alla enheter har samtidig åtkomst till internetanslutningen och bandbredden minskar linjärt samtidigt som fler konsumenter eller datorer läggs till i nätverket.

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

Prestandan för det lokala nätverket (LAN) är att, förutom att det är möjligt att nå nätverket, tillhandahålla tillräcklig bandbredd för att AEM Screens ska fungera smidigt. LAN-nätverket matchar vanligtvis minst ett 100 Mbit/s-nätverk, så att det ska finnas tillräcklig bandbredd för att ansluta många enheter med bra prestanda till systemet.

När du använder andra aktiva nätverkskomponenter är det obligatoriskt att alla dessa stämmer överens med kraven för nätverksbandbredd. Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i specifikationen Internet Access/Router.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. På grund av detta inträffar större nätverkstrafik om det finns nytt innehåll som ska visas på en viss skärm.
För normal åtgärd, till exempel, erbjuder en definierad spellista som inte uppdateras ofta under dagen en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.
För de fall där det förekommer mer interaktion med sensorer eller andra utlösare och där innehållet är mycket dynamiskt är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion för att säkerställa bästa möjliga kundupplevelse.

I följande tabell visas en översikt över data för nätverksanslutningsnycklar som är ansvariga för prestanda som kan förväntas och möjliga väntetider.

>[!NOTE]
>All information avser förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/download-times-mobile.png)



