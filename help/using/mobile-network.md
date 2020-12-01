---
title: Direkt mobilnätverk
description: Sidan beskriver Direct Mobile Network Setup
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# Direkt mobilnätverk {#mobile-network-setup}

AEM Screens-spelare kan också anslutas med mobilnätverk eller mobilnätverk som kör minst ett 3G-nätverk.

Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till spelarstyrenheten eller datorn och lagras på rätt sätt i det underliggande operativsystemet. Den angivna bandbredden påverkar därför bara inledande hämtningstider samt innehållsuppdateringar, och påverkar inte prestanda för regelbunden uppspelning av bildskärmar.

Fördelen med att ansluta AEM Screens-spelare via mobiltelefon 3/4/5G till din mobiltjänstleverantör är att mobilroutern kan placeras på en optimerad plats för att få bästa möjliga nätverkstäckning. Detta är vanligtvis i upphöjt och öppet läge med så lite omgivande betong- eller metallkonstruktion som möjligt.

Med den här inställningen kan användare av AEM skärmbild få stor flexibilitet eftersom det inte krävs någon fast anslutning för att ansluta till AEM Screens. Detta är särskilt intressant för tillfälliga eller mobila miljöer.

I följande diagram visas Direct Mobile Network Setup och består av ett enda nätanslutningssegment och anslutningen av varje spelare till det mobila eller mobila datanätverket.

![](/help/using/assets/direct-mobile-1.png)

## Ansluta AEM Screens Player till Direct Mobile Network {#connecting-aem-screens-players}

Följ stegen nedan för att se till att AEM skärmspelare är korrekt anslutna i den här konfigurationen:

1. Kontrollera att alla AEM skärmspelare är anslutna till routerns nätverk.

1. Testa internetanslutningen genom att ringa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett felmeddelande kontrollerar du nätverksinställningarna och kontrollerar om det finns en tillräckligt stor nätverkslänk och operativsystemets brandvägg är konfigurerad för att tillåta nätverksåtkomst med de konfigurerade AEM Screens-kommunikationsportarna.

1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

## Konfigurera Direct Mobile Network {#requirements-direct}

Nätverksinstallationen kan logiskt separeras i två block:

* Mobil Internetanslutning

* Lokalt nätverk

### Mobil internetanslutning {#mobile-internet-connection}

Prestandan för internetanslutningen ger inte bara tillräcklig bandbredd för att AEM Screens ska fungera smidigt.

I Direct Mobile Network är varje spelare ansluten med ett mobildatakort till leverantörens datanätverk.

I följande tabell visas datanätverken med sin standardbandbredd:

| Datanätverk | Bandbredd |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5 G | 1 000 - 1 000 Mbit/s |

När du överväger vilket datanätverk som ska användas bör du svara på följande frågor:

Vilken nätverkshastighet som är tillgänglig beror på den specifika mobildataproviderplanen och på vilken täckning som är tillgänglig på platsen för AEM Screens Controller.
När du följer den här konfigurationen måste du också tänka på att förutom den tillgängliga bandbredden så begränsar en del mobildataproviderplaner den tillgängliga mängden data som kommer över anslutningen inom en viss tidsperiod. Det måste säkerställas att det finns tillräcklig kapacitet i fråga om datamängd och bandbredd.
Som en uppföljning måste det nödvändiga datapaketet vara minst:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>För inledande överföring av mediefiler, t.ex. genom integrering av nya spelare, måste en större mängd data och en ökad hämtningstid förväntas och återspeglas i ovanstående antaganden. Ett 4G-nätverk med *bra* täckning och *obegränsade* data bör matcha de vanligaste installationerna i den här nätverksinställningarna.

>[!NOTE]
>En lägsta 3G-plan med bra nätverkstäckning bör leda till acceptabel nedladdningsprestanda för en AEM Screens-spelare. Om det bara finns en rimlig täckning tillgänglig på en viss plats bör man överväga att ändra den övergripande nätverksinställningen till [Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter](/help/using/mobile-network-router.md).


### Lokalt nätverk {#lan-connection}

Prestandaproblemen i det lokala nätverket (LAN), förutom nätverksnåbarheten, är att tillhandahålla tillräcklig bandbredd för att AEM Screens ska fungera smidigt. Rekommendationen för LAN-nätverkshastigheterna är att börja vid minst 100 Mbit/s nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet.

När du använder andra aktiva nätverkskomponenter är det obligatoriskt att alla dessa stämmer överens med kraven för nätverksbandbredd. Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i Internet-åtkomsten eller routerspecifikationen. Annars begränsas den totala bandbredden av den svagaste länken i nätverkskedjan.

## Hämtar media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. Den största nätverkstrafiken inträffar när det finns nytt innehåll som ska visas på en viss skärm.

För vanliga åtgärder, till exempel, är en definierad spellista som uppdateras ofta under dagen en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.

För scenarier där det förekommer mer interaktion med sensorer eller utlösare och dynamiskt innehåll är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion som säkerställer bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnycklar.

>[!NOTE]
>
>All information avser förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/download-times-mobile.png)



