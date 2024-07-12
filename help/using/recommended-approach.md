---
title: Rekommenderat tillvägagångssätt
description: Läs mer om det rekommenderade tillvägagångssättet i ett AEM Screens-projekt.
exl-id: 28aacffa-e9c9-4ccb-8038-720bb3e02a3f
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Rekommenderat tillvägagångssätt {#recommended-approach}

Det är god praxis att se alla AEM Screens-projekt på företagsnivå som ett långsiktigt företag. Det är troligt att projektet varar i ett eller flera år, särskilt om lösningen tillåter komplex användarinteraktion eller distribueras till olika enheter och platser.

## Riktlinjer för utveckling av en strategi för digitala signaturer {#signage-strategy}

Se de få rekommendationerna innan du börjar utveckla och driftsätta ett projekt för digitala signaturer:

* **Omfångskontroll**:
Om lösningen är ambitiös bör du dela upp slutprodukterna i separata faser för att styra projektets omfattning.

* **Exempel på definierad användning**:
Projektfaserna bör ge väldefinierade användningsfall med tydligt identifierade kriterier.

* **Inkrementella slutprodukter**:
Fokusera på att leverera funktioner stegvis.

* **Uppskattar önskat resultat**:
Börja med färdiga AEM Screens-funktioner innan du skapar anpassade komponenter och integreringar. Brainstorm om önskat resultat kan uppnås med de komponenter och funktioner som medföljer som standard med AEM Screens.

* **Definierar piloter, rollouts och POC:er**:
Utveckla ett konceptbevis (Proof of Concept, POC) och anpassa efter behov genom en pilot och utrullning.

* **Fördefinierad innehållsstrategi**:
Upprätta en innehållsstrategi, inklusive kortsiktiga och långsiktiga mål. Anpassa också varumärkesmål/nyckeltal till funktionsförbättringar.

  >[!NOTE]
  >
  > Startkostnaderna för ett AEM Screens-projekt är ofta högre på grund av behovet av att investera i maskinvara, korrigeringar och webbplatsdesign. Det innebär att enklare innehållslösningar kan hjälpa er att hantera budgetens förväntningar.

* **Beräknar slutprodukter i stor skala**:
Om lösningen levereras i stor skala kan du rulla ut komponenterna i applikationen till noggrant utvalda pilotplatser för testanvändning. Leverera till nya platser och enheter när programmet godkänns i valideringen.

  >[!NOTE]
  >
  > Börja samla in analyser under piloten så att affärsteamen kan validera lösningens framgångar mot de specifika mätvärden de försöker uppnå. Genom att veta hur pilotprojektet fungerar kan affärsteamet avgöra vilka förbättringar som måste göras.

* **Dela upp slutprodukter i mätbara uppgifter**:
Genom att dela upp leveransen av funktioner i mätbara uppgifter kan du få feedback, nå mer uppnåeliga mål och minska de totala projektriskerna.

* **Utveckla en färdplan**:
Om kunden vill ha en funktionsrik produkt kan ni leverera en del av den planerade funktionaliteten tidigt i projektet och planera in andra funktioner för framtida faser. En funktionsrik första leverans medför större risk och är svårare att validera med kunden.

* **Förstå omfattningen av anpassade integreringar**:
Interaktiva komponenter med pekskärmsinteraktion, rörelsesensor eller RFID kräver en betydande anpassad utveckling i implementeringsmetoden. Ett bildspel, en videoannons eller en statisk meny kan levereras som grafiskt innehåll eller HTML i en Screens-kanal.
