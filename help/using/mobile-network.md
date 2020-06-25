---
title: Direkt mobilnätverk
description: Sidan beskriver Direct Mobile Network Setup
translation-type: tm+mt
source-git-commit: d12de8de2b7bb29d85ebb0e046f2d1fd5051e928
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 0%

---


# Direkt mobilnätverk {#mobile-network-setup}

AEM Screens Players kan också anslutas via mobilnätverk eller mobilnätverk som körs minst i ett 3G-nätverk.

Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till spelarstyrenheten eller datorn och lagras korrekt i det underliggande operativsystemet. Den angivna bandbredden påverkar därför bara den inledande hämtningstiden och påverkar inte bildskärmens prestanda.

Fördelen med att ansluta AEM Screens-spelare med en mobiltelefonanslutning med 3/4/5G är att mobilroutern kan placeras på en optimerad plats för att få bästa möjliga nätverkstäckning. Detta är vanligtvis i upphöjt och öppet läge med så optimal omgivande betong- eller metallkonstruktion som möjligt.

Med denna SetUp får AEM Screen-användare stor flexibilitet eftersom det inte krävs någon fast anslutning för att ansluta till AEM Screens.

I följande diagram visas Direct Mobile Network Setup och består av ett enda nätanslutningssegment och anslutningen av varje spelare till det mobila eller mobila datanätverket.

![](/help/using/assets/direct-mobile-1.png)

## Ansluta AEM Screens Player till Direct Mobile Network {#connecting-aem-screens-players}

Följ stegen nedan för att säkerställa att AEM Screen-spelarna är korrekt anslutna i den här konfigurationen:

1. Kontrollera att alla AEM Screen-spelare är anslutna till Routers Network.

1. Testa internetanslutningen genom att ringa en URL i datorns webbläsare.

   >[!NOTE]
   >Om du får ett felmeddelande kontrollerar du nätverksinställningarna och kontrollerar om det finns en tillräckligt stor nätverkslänk och operativsystemets brandvägg är konfigurerad för att tillåta nätverksåtkomst med de konfigurerade AEM Screens-kommunikationsportarna.

1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

## Konfigurera Direct Mobile Network {#requirements-direct}

Nätverksinstallationen kan logiskt separeras i två block:

* Mobil Internetanslutning

* Lokalt nätverk

### Mobil Internetanslutning {#mobile-internet-connection}

Internet-anslutningens prestanda, förutom nätverksanslutning, ger tillräcklig bandbredd för att AEM Screens ska fungera smidigt.

I Direct Mobile Network är varje spelare ansluten med ett mobildatakort till leverantörens datanätverk.

I följande tabell visas datanätverken med sin standardbandbredd:

| Datanätverk | Bandbredd |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 - 1 000 Mbit/s |

När du överväger vilket datanätverk som ska användas bör du svara på följande frågor:

Den tillgängliga nätverkshastigheten beror på den specifika mobildataproviderplanen och på den tillgängliga täckning som nås på AEM Screens Controller-enhetens plats.
När du följer den här konfigurationen måste du också tänka på att förutom den tillgängliga bandbredden så begränsar en del mobildataproviderplaner den tillgängliga mängden data som kommer över anslutningen inom en viss tidsperiod. Det måste säkerställas att det finns tillräcklig kapacitet i fråga om datamängd och bandbredd.
Som en uppföljning måste det nödvändiga datapaketet vara minst:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>För inledande överföring av mediefiler, t.ex. genom integrering av nya spelare, måste en större mängd data och en ökad hämtningstid förväntas och återspeglas i ovanstående antaganden.Ett 4G-nätverk med *bra* täckning och *obegränsade* data bör matcha de vanligaste installationerna i den här nätverksinstallationen.

>[!NOTE]
>En lägsta 3G-plan med bra nätverkstäckning bör leda till acceptabel hämtningsprestanda för en AEM Screens-spelare. Om det bara finns en rimlig täckning tillgänglig på en viss plats bör man överväga att byta den övergripande nätverksinställningen till [mobilt nätverk med mobil datarouter och aktiva nätverkskomponenter](/help/using/mobile-network-router.md).


### Lokalt nätverk {#lan-connection}

Prestandan för det lokala nätverket (LAN) är att, förutom att det är möjligt att nå nätverket, tillhandahålla tillräcklig bandbredd för att AEM Screens ska fungera smidigt. LAN-nätverket matchar vanligtvis ett 100 Mbit/s-nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet.

När du använder andra aktiva nätverkskomponenter är det obligatoriskt att alla dessa stämmer överens med kraven för nätverksbandbredd. Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i Internet-åtkomsten eller routerspecifikationen.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. Den största nätverkstrafiken inträffar när det finns nytt innehåll som ska visas på en viss skärm.

För vanliga åtgärder, till exempel, är en definierad spellista som uppdateras ofta under dagen en åtgärd som är nära nätverksoberoende när alla filer har sparats i spelaren.

För scenarier där det förekommer mer interaktion med sensorer eller utlösare och dynamiskt innehåll är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion som säkerställer bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnycklar.

>[!NOTE]
>All information avser förbrukningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/download-times-mobile.png)



