---
title: Direkt mobilt nätverk
description: Läs mer om Direct Mobile Network Setup i AEM Screens.
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# Direkt mobilt nätverk {#mobile-network-setup}

AEM Screens-spelare kan också anslutas med mobilnätverk eller mobilnätverk som kör minst ett 3G-nätverk.

Inom AEM Screens hämtas det nödvändiga innehållet fysiskt till spelarstyrenheten eller datorn och lagras på rätt sätt i det underliggande operativsystemet. Den angivna bandbredden påverkar därför bara inledande hämtningstider och innehållsuppdateringar, och påverkar inte prestanda för vanlig uppspelning av bildskärmar.

Fördelen med att ansluta AEM Screens-spelare via mobiltelefon 3/4/5G till din mobiltjänstleverantör är att mobilroutern kan placeras på en optimerad plats för att få bästa möjliga nätverkstäckning. Detta är vanligtvis i upphöjt och öppet läge med så få omgivande bete- eller metallstrukturer som möjligt.

Med den här inställningen kan användare av AEM skärmbild få stor flexibilitet eftersom det inte krävs någon fast anslutning för att ansluta till AEM Screens. Det här är intressant för tillfälliga eller mobila miljöer.

I följande diagram visas Direct Mobile Network Setup och består av ett enda nätanslutningssegment och anslutningen av varje spelare till det mobila eller mobila datanätverket.

![](/help/using/assets/direct-mobile-1.png)

## Ansluta AEM Screens Player till Direct Mobile Network

Följ stegen nedan för att se till att AEM skärmspelare är korrekt anslutna i den här konfigurationen:

1. Kontrollera att alla AEM skärmspelare är anslutna till routerns nätverk.

1. Testa Internetanslutningen genom att anropa en URL i systemets webbläsare.

   >[!NOTE]
   >Om du får ett felmeddelande kontrollerar du nätverksinställningarna och kontrollerar om det finns en tillräcklig nätverkslänk. Kontrollera också att operativsystemets brandvägg är konfigurerad att tillåta nätverksåtkomst när du använder de konfigurerade AEM Screens-kommunikationsportarna.

1. Om URL-anropet lyckas kan du fortsätta installera AEM Screens och registrera dig. Starta AEM Screens.

## Konfigurera Direct Mobile Network {#requirements-direct}

Nätverksinstallationen kan logiskt separeras i två block:

* Mobil Internetanslutning

* Lokalt nätverk

### Mobil Internetanslutning {#mobile-internet-connection}

Prestandan för internetanslutningen ger inte bara tillräcklig bandbredd för att AEM Screens ska fungera smidigt.

I Direct Mobile Network är varje spelare ansluten med ett mobildatakort till leverantörens datanätverk.

Följande tabell visar datanätverken med deras standardbandbredd:

| Datanätverk | Bandbredd |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5 G | 1 000 - 1 000 Mbit/s |

Tänk på följande när du funderar på vilket datanätverk som ska användas:

Vilken nätverkshastighet som är tillgänglig beror på den specifika mobildataproviderplanen och på vilken täckning som är tillgänglig på platsen för AEM Screens Controller.
När du följer den här konfigurationen bör du tänka på att förutom den tillgängliga bandbredden så begränsar vissa mobildataproviderplaner den tillgängliga mängden data som kommer över anslutningen inom en viss tid. Det måste säkerställas att det finns tillräcklig kapacitet i data- och bandbreddsmängden.
Som en uppföljning måste det nödvändiga datapaketet vara minst:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>För inledande överföring av mediefiler, till exempel, måste en högre datamängd och en ökad hämtningstid förväntas och återspeglas i ovanstående antaganden, samtidigt som nya spelare integreras. Ett 4G-nätverk med *bra* täckning och *obegränsad* data ska överensstämma med de vanligaste installationerna i den här nätverksinställningarna.

>[!NOTE]
>En lägsta 3G-plan med bra nätverkstäckning bör leda till acceptabel nedladdningsprestanda för en AEM Screens Player. Om det bara finns en rimlig täckning tillgänglig på en viss plats kan du överväga att byta den övergripande nätverksinställningarna till [Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter](/help/using/mobile-network-router.md).


### Lokalt nätverk {#lan-connection}

Prestandaproblemen i det lokala nätverket (LAN), förutom nätverksnåbarheten, är att tillhandahålla tillräcklig bandbredd för att AEM Screens ska fungera smidigt. Rekommendationen för LAN-nätverkshastigheterna är att börja vid minst 100 Mbit/s nätverk, så att det finns tillräckligt med bandbredd för att ansluta många enheter med bra prestanda till systemet.

När du använder andra aktiva nätverkskomponenter är det obligatoriskt att alla dessa stämmer överens med kraven för nätverksbandbredd. Nätverkskomponenterna bör till exempel minst matcha 100 Mbit/s-standarden och matcha den bandbredd som anges i Internet-åtkomsten eller routerspecifikationen. I annat fall begränsas den totala bandbredden av den svagaste länken i nätverkskedjan.

## Hämta media och resurser {#download}

AEM Screens ger användare av digitala signaturer en stor fördel. Den hämtar och sparar alla nödvändiga mediefiler lokalt, till exempel bilder och videor. Den största nätverkstrafiken inträffar när det finns nytt innehåll som ska visas på en viss skärm.

För vanliga åtgärder, till exempel, erbjuder en definierad spellista som uppdateras ofta under dagen en nästan nätverksoberoende åtgärd när alla filer har sparats i spelaren.

För scenarier där det förekommer mer interaktion med sensorer eller utlösare och dynamiskt innehåll är en snabb och tillförlitlig nätverksanslutning avgörande för en omedelbar skärmreaktion som säkerställer bästa möjliga kundupplevelse.

Följande tabell ger en översikt över data för nätverksanslutningsnycklar.

>[!NOTE]
>
>All information avser användningen av varje enhet i nätverket som begär och hämtar en Internetkälla. Var och en av dessa förfrågningar sammanfattar och förlänger hämtningstiden.

![](/help/using/assets/download-times-mobile.png)
