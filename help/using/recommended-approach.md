---
title: Rekommenderat tillvägagångssätt
seo-title: Rekommenderat tillvägagångssätt i ett AEM Screens-projekt
description: Sidan beskriver rekommenderat tillvägagångssätt i ett AEM Screens-projekt
seo-description: Sidan beskriver rekommenderat tillvägagångssätt i ett AEM Screens-projekt
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# Rekommenderad metod {#recommended-approach}

Vi rekommenderar att man ser AEM Screens-projekt på företagsnivå som ett långsiktigt företag. Det är troligt att projektet varar i ett eller flera år, särskilt om lösningen tillåter komplex användarinteraktion eller kommer att användas på flera olika enheter och platser.

## Riktlinjer innan du utvecklar en strategi för digital signering {#signage-strategy}

Läs de få rekommendationerna innan du utvecklar och distribuerar ett projekt för digitala signaturer:

* **Omfångskontroll**: Om lösningen är ambitiös bör du dela upp slutprodukterna i separata faser för att styra projektets omfattning.

* **Exempel** på definierad användning: Projektfaserna bör ge väldefinierade användningsfall med tydligt identifierade kriterier.

* **Inkrementella slutprodukter**: Fokusera på att leverera funktioner stegvis.

* **Beräknar önskat resultat**: Börja med färdiga AEM Screens-funktioner innan du skapar anpassade komponenter och integreringar. Brainstorm om önskat resultat kan uppnås med de komponenter och funktioner som medföljer som standard med AEM Screens.

* **Definiera piloter, rollouts och POC**: Utveckla ett konceptbevis (Proof of Concept, POC) och anpassa efter behov genom en pilot och utrullning.

* **Fördefinierad innehållsstrategi**: Upprätta en innehållsstrategi, inklusive kortsiktiga och långsiktiga mål. Anpassa dessutom varumärkesmål/nyckeltal med funktionsförbättringar.

   >[!NOTE]
   >
   > Startkostnaderna är ofta högre för ett AEM Screens-projekt på grund av behovet av att investera i maskinvara, korrigeringar och webbplatsdesign. Därför kan ni lättare hantera budgetens förväntningar genom att hålla de ursprungliga innehållslösningarna enkla.

* **Beräknar slutprodukter i stor skala**: Om lösningen kommer att levereras i stor skala rekommenderar vi att du rullar ut komponenterna i programmet till noggrant utvalda pilotplatser för testanvändning. Leverera till nya platser och enheter när programmet godkänns i valideringen.

   >[!NOTE]
   >
   > Börja samla in analyser under piloten för att hjälpa affärsteamen att validera lösningens framgångar mot de specifika mätvärden de försöker uppnå. Genom att veta hur pilotprojektet fungerar kan affärsteamet avgöra vilka förbättringar som behöver göras.

* **Dela upp slutprodukter i mätbara uppgifter**: Genom att dela upp leveransen av funktioner i mätbara uppgifter kan man få snabb feedback, nå mer uppnåeliga mål och minska de övergripande projektriskerna.

* **Utveckla en färdplan**: Om kunden vill ha en funktionsrik produkt kan du leverera en del av den planerade funktionaliteten tidigt i projektet och schemalägga andra funktioner för framtida faser. En funktionsrik första leverans medför större risk och blir svårare att validera med kunden.

* **Förstå omfattningen av anpassade integreringar**: Interaktiva komponenter med pekskärmsinteraktion, rörelsesensor eller RFID kräver en betydande anpassad utveckling i implementeringsmetoden. Ett bildspel, en videoannons eller en statisk meny kan levereras som grafiskt innehåll eller HTML på en skärmkanal.

