---
title: Introduktion till standardnätverksinställningar
description: Sidan beskriver standardnätverksinställningar
translation-type: tm+mt
source-git-commit: 8e62b3fc4ce324e02aaec6fca9df79b1aaf94d72
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# Hantera nätverkstrafik {#managing-network-traffic}

En nätverksinställning kan ha olika strukturer. I det här avsnittet beskrivs de vanligaste nätverksinställningarna i en organisations nätverkskonfiguration.

Den här guiden belyser en introduktion till proxyservrar följt av olika nätverksstrukturer som är konfigurerade inom olika organisationer.

>[!NOTE]
>**AEM Screens nätverkskrav **>AEM Screens kommunicerar direkt med AEM som Cloud Service, och det finns därför ett behov av att upprätta en stabil koppling mellan de båda noderna. Brandväggar är absolut obligatoriska för kommersiell internetåtkomst och som kund måste du förstå vilka kommunikationsportar som måste öppnas i brandväggar och andra IT-säkerhetsrelaterade nätverkskomponenter.

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

<table>
 <tbody>
  <tr>
   <td><strong>Nätverksinställningar</strong></td>
   <td><strong>Fördelar</strong></td>
   <td><strong>Nackdelar</strong></td>
  </tr>
  <tr>
   <td><strong>Direkt Internet-nätverk (trådlöst/trådlöst)</strong></td>
   <td>Enkelt och rakt fram till SetUp<br>Bra val för medelstora eller större installationer<br>Dedicated Network kan kapslas in<br>några felpunkter<br>relativt billigt<br>bra skalbarhet</td>
   <td>Obligatorisk internetdataplan </td>
  </tr>
    <tr>
   <td><strong>Direkt mobilnätverk</strong></td>
   <td>Enkelt att installera<br>Bra val för medelstora eller större installationer<br>Bra skalbarhet<br>för inkapslade skärmar
</td>
   <td>Obligatorisk internetuppkoppling</td>
  </tr>
    <tr>
<tr>
   <td><strong>Mobilnätverk med mobil datarouter och aktiva nätverkskomponenter</strong></td>
   <td>Enkelt att installera<br>bra alternativ för medelstora eller större installationer<br>dedikerade nätverk kan kapslas<br>in några felpunkter<br>relativt billigt<br>bra skalbarhet</br></td>
   <td>Obligatorisk internetdataplan</td>
  </tr>
    <tr>

<td><strong>Enclosed Corporate Network (Wired/Wireless)</strong></td>
   <td>Hög flexibilitet och skalbarhet<br>Mycket säker tack vare olika försvarsnivåer<br>Encapsulated Networks<br>Enkelt att övervaka och underhålla<br>tillförlitligt</td>
   <td>Komplicerade och dyra<br>rekommenderas för nätverksspecialister eller systemintegratörer</td>
  </tr>
  </tr>
 </tbody>
</table>


