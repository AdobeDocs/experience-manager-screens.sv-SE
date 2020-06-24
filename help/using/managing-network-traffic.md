---
title: Hantera nätverkstrafik
description: På sidan beskrivs standardnätverksinställningar och hur du hanterar nätverkstrafik.
translation-type: tm+mt
source-git-commit: 93cc11459e23d3eb22d865bedeb26deaf7135636
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---


# Hantera nätverkstrafik {#managing-network-traffic}

En nätverksinställning kan ha olika strukturer. I det här avsnittet beskrivs de vanligaste nätverksinställningarna i en organisations nätverkskonfiguration.

Den här guiden belyser en introduktion till proxyservrar följt av olika nätverksstrukturer som är konfigurerade inom olika organisationer.

>[!NOTE]
>
>**AEM Screens nätverkskrav**
>
>AEM Screens kommunicerar direkt med AEM som Cloud Service, och det finns därför ett behov av att upprätta en stabil koppling mellan de båda noderna. Brandväggar är absolut obligatoriska för kommersiell internetåtkomst och som kund måste du förstå vilka kommunikationsportar som måste öppnas i brandväggar och andra IT-säkerhetsrelaterade nätverkskomponenter.

## Översikt över proxyservrar {#proxy-servers}

En Internetanslutning är beroende av att en proxyserver används. En proxyserver är en dedikerad dator eller ett programvarusystem som körs på en dator som fungerar som mellanhand mellan en slutpunktsenhet, till exempel en dator, och en annan server från vilken en användare eller klient begär en tjänst. Proxyservern kan finnas på samma dator som en brandväggsserver eller på en separat server som vidarebefordrar begäranden via brandväggen.

En fördel med en proxyserver är att dess cache kan användas av alla användare. Om en eller flera Internet-platser ofta efterfrågas, kommer dessa förmodligen att finnas i proxyns cacheminne, vilket förbättrar användarens svarstid. En proxy kan också logga interaktionen som används för felsökning.

## Förstå standardnätverksinställningarna {#network-setups}

Om du vill implementera en nätverksinstallation måste du hänvisa till följande scenarier med deras styrkor och distributionsinformation.

Det finns fyra huvudtyper av nätverksinställningar:

1. [Direkt Internet-nätverk (trådlöst/trådlöst)](/help/using/direct-internet-network.md)
1. [Direkt mobilnätverk](/help/using/mobile-network.md)
1. [Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter](/help/using/mobile-network-router.md)
1. [Enclosed Corporate Network (Wired/Wireless)](/help/using/enclosed-corporate-network.md)

I följande tabell visas de olika typerna av nätverksinställningar med fördelar och nackdelar:

| Nätverksinställningar | Fördelar | Nackdelar |
|--- |--- |--- |
| Direkt Internet-nätverk (trådlöst/trådlöst) | Enkelt och rakt fram till<br>SetUpGood för medelstora eller större<br>installationerDedikerat nätverk kan vara<br>EncapsulatedNågra<br>felpunkterRelativt<br>InfoodGood Scalability | Obligatorisk internetdataplan |
| Direkt mobilnätverk | Enkelt att<br>installeraBra val för medelstora eller större<br>installationerBra<br>skalbarhetEncapsulated Screens | Obligatorisk internetuppkoppling |
| Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter | Enkelt att<br>ställa inGood Choice för medelstora eller större<br>installationerDedikerat nätverk kan<br>kapslas inEtt antal felpunkter<br>relativt<br>billigtBra skalbarhet | Obligatorisk internetdataplan |
| Enclosed Corporate Network (Wired/Wireless) | Hög flexibilitet och<br>skalbarhetHög säkerhet tack vare olika rader i<br>DefenseEncapsulated<br>NetworksEnkelt att övervaka och<br>underhållaTillförlitligt | Komplicerad och<br>dyrRekommenderas för nätverksspecialister eller systemintegratörer |
