---
title: Hantera nätverkstrafik
description: På sidan beskrivs standardnätverksinställningar och hur du hanterar nätverkstrafik.
exl-id: b6d8f4a3-fca2-4556-9455-b9e27b138154
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Hantera nätverkstrafik {#managing-network-traffic}

En nätverksinställning kan ha olika strukturer. I det här avsnittet beskrivs de vanligaste nätverksinställningarna och de allmänna strategier som används inom en organisation.

Den här guiden belyser en introduktion till proxyservrar följt av de olika nätverksstrukturer som är konfigurerade inom olika organisationer.

>[!NOTE]
>**AEM Screens nätverkskrav**
>AEM Screens kommunicerar direkt med AEM as a Cloud Service och måste därför upprätta en stabil anslutning mellan de båda noderna. Brandväggar är obligatoriska för kommersiell internetåtkomst. Kunden måste förstå vilka kommunikationsportar som måste öppnas i dessa brandväggar och andra IT-säkerhetsrelaterade nätverkskomponenter.

## Översikt över proxyservrar {#proxy-servers}

En Internetanslutning är beroende av att en proxyserver används. En proxyserver är en dedikerad dator eller ett programvarusystem som körs på en dator. Den fungerar som en mellanhand mellan en slutpunktsenhet, till exempel en dator, och en annan server från vilken en användare eller klient begär en tjänst. Proxyservern kan finnas på samma dator som en brandväggsserver eller på en separat server som vidarebefordrar begäranden via brandväggen.

En fördel med en proxyserver är att dess cache kan användas av alla användare. Om en eller flera webbplatser ofta efterfrågas finns de förmodligen i proxyns cacheminne. Sådan cachelagring förbättrar användarens svarstid ytterligare. En proxy kan också logga interaktionen som kan användas för felsökning.

När en proxyserver tar emot en begäran om en Internet-resurs (till exempel en webbsida eller vid anslutning till en AEM Publisher), söker den i sin lokala cache efter tidigare anropade URL:er. Om sidan hittas returneras den till användaren utan att begäran vidarebefordras till Internet. Om sidan inte finns i cachen fungerar proxyservern som en klient för användaren och begär sidan från servern på Internet. När innehållet returneras relaterar proxyservern det till den ursprungliga begäran och vidarebefordrar det till användaren.

## Standardnätverksinställningarna {#network-setups}

Om du vill implementera en nätverksinstallation läser du följande scenarier med deras styrkor och distributionsinformation.

I den här guiden beskrivs fyra olika typer av nätverksinställningar inom en organisation:

* **[Direkt Internet-nätverk (kabelanslutet/trådlöst)](/help/using/direct-internet-network.md)**
* **[Direkt mobilt nätverk](/help/using/mobile-network.md)**
* **[Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter](/help/using/mobile-network-router.md)**
* **[Enclosed Corporate Network (Wired/Wireless)](/help/using/enclosed-corporate-network.md)**

I följande tabell visas de olika typerna av nätverksinställningar med fördelar och nackdelar:

| Nätverksinställningar | Fördelar | Nackdelar |
|--- |--- |--- |
| **Direkt Internet-nätverk (kabelanslutet/trådlöst)** | Enkelt och rakt fram till SetUp<br>Bra val för medelstora eller större installationer<br>Dedikerat nätverk kan kapslas in<br>Ett fåtal felpunkter<br>relativt lågt<br>Bra skalbarhet | Obligatorisk internetdataplan |
| **Direkt mobilt nätverk** | Enkelt att installera<br>Bra val för medelstora eller större installationer<br>Bra skalbarhet<br>Encapsulated Screens | Obligatorisk internetuppkoppling |
| **Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter** | Enkelt att installera<br>Bra val för medelstora eller större installationer<br>Dedikerat nätverk kan kapslas in<br>Ett fåtal felpunkter<br>relativt billigt<br>Bra skalbarhet | Obligatorisk internetdataplan |
| **Enclosed Corporate Network (Wired/Wireless)** | Hög flexibilitet och skalbarhet<br>Hög säkerhet på grund av olika försvarsrader<br>Encapsulated Networks<br>Enkelt att övervaka och underhålla<br>Tillförlitligt | Komplicerade och dyra<br>rekommenderas för nätverksspecialister eller systemintegratörer |
