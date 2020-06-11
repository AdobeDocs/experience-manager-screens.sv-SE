---
title: Förstå proxyservrar
seo-title: Förstå proxyservrar
description: Sidan beskriver proxyservrar
seo-description: Sidan beskriver proxyservrar
translation-type: tm+mt
source-git-commit: e8161ece44fcc945b66713b3797935a505675104
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Introduktion till standardnätverksinställningar {#intro-standard-networks}

En nätverksinställning kan ha olika strukturer. I det här avsnittet finns en översikt över nätverksstrukturerna som distribueras i en miljö.

## Proxyservrar {#proxy-servers}

En proxyserver är en dedikerad dator eller ett programvarusystem som körs på en dator som fungerar som mellanhand mellan en slutpunktsenhet, till exempel en dator, och en annan server från vilken en användare eller klient begär en tjänst. Proxyservern kan finnas på samma dator som en brandväggsserver eller på en separat server som vidarebefordrar begäranden via brandväggen.

En fördel med en proxyserver är att dess cache kan användas av alla användare. Om en eller flera webbplatser ofta efterfrågas finns de förmodligen i proxyns cacheminne, vilket förbättrar användarens svarstid. En proxy kan också logga interaktionen, vilket kan vara praktiskt vid felsökning.

## Om nätverksinställningarna {#network-setups}

Om du vill implementera en nätverksinställning måste du referera till följande scenarier med pros och cons. Det finns tre huvudtyper av nätverksinställningar:

1. Internetåtkomst
1. Inställningar för mobilnätverk
1. Närstående företagsnätverk

