---
title: Förstå proxyservrar
seo-title: Förstå proxyservrar
description: Sidan beskriver proxyservrar
seo-description: Sidan beskriver proxyservrar
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Introduktion till standardnätverksinställningar {#intro-standard-networks}

En nätverksinställning kan ha olika strukturer. I det här avsnittet finns en översikt över nätverksstrukturerna som distribueras i en miljö. Det finns olika inställningar som ibland implementeras från början.

I det här avsnittet beskrivs en introduktion till proxyservrar följt av olika nätverksstrukturer som är konfigurerade med olika organisationer.

## Proxyservrar {#proxy-servers}

En proxyserver är en dedikerad dator eller ett programvarusystem som körs på en dator som fungerar som mellanhand mellan en slutpunktsenhet, till exempel en dator, och en annan server från vilken en användare eller klient begär en tjänst. Proxyservern kan finnas på samma dator som en brandväggsserver eller på en separat server som vidarebefordrar begäranden via brandväggen.

En fördel med en proxyserver är att dess cache kan användas av alla användare. Om en eller flera webbplatser ofta efterfrågas finns de förmodligen i proxyns cacheminne, vilket förbättrar användarens svarstid. En proxy kan också logga interaktionen, vilket kan vara praktiskt vid felsökning.

## Om nätverksinställningarna {#network-setups}

Om du vill implementera en nätverksinställning måste du referera till följande scenarier med pros och cons.

Det finns tre huvudtyper av nätverksinställningar:

1. Inställningar för Internet Access
1. Inställningar för mobilnätverk
1. Nätverksinstallation av företagsnätverk

I följande tabell visas de olika typerna av nätverksinställningar med fördelar och nackdelar:

<table>
 <tbody>
  <tr>
   <td><strong>Nätverksinställningar</strong></td>
   <td><strong>Fördelar</strong></td>
   <td><strong>Nackdelar</strong></td>
  </tr>
  <tr>
   <td><strong>Inställningar för Internet Access</strong></td>
   <td>Enkelt och rakt fram till SetUp<br>Bra val för medelstora eller större installationer<br>Dedicated Network kan kapslas in<br>Några felpunkter<br>relativt Kontrollera<br>god skalbarhet</td>
   <td>Lämplig internetdataplan är obligatorisk</td>
  </tr>
    <tr>
   <td><strong>Inställningar för mobilnätverk</strong></td>
   <td>Enkelt och rakt fram till SetUp<br>Bra val för medelstora eller större installationer<br>Dedicated Network kan kapslas in<br>Några felpunkter<br>Relativt Cheap<br>Good-skalbarhet</br></td>
   <td>Lämplig internetuppkoppling krävs</td>
  </tr>
    <tr>
   <td><strong>Enclosed Corporate Network</strong></td>
   <td>Hög flexibilitet och skalbarhet<br>Mycket säker tack vare olika försvarsrader<br>i kapslade nätverk<br>Enkelt att övervaka och underhålla<br>tillförlitligt</td>
   <td>Komplicerade och dyra<br>nätverksspecialister eller systemintegratör rekommenderas</td>
  </tr>
  </tr>
 </tbody>
</table>


