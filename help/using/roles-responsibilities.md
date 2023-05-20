---
title: AEM Screens projektroller och ansvarsområden
seo-title: AEM Screens Project Roles  and Responsibilities
description: På sidan beskrivs AEM Screens Project Rolands and Responsibility
seo-description: The page describes AEM Screens Project Roles  and Responsibilities
exl-id: 9377625b-529a-4b46-89d9-f526de398639
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 3%

---

# Projektroller och ansvarsområden {#roles-responsibilities}

Som erfaren AEM-implementerare har du troligtvis sett rollerna, som kallas *författare*, *utvecklare* och *IT/tekniker*.

I ett typiskt AEM Screens-projekt har rollerna förfinats ytterligare eftersom de har ett viktigt syfte i projektet.

Diagrammet nedan visar rollerna som vi kommer att hänvisa till i hela guiden.

![](/help/assets/project-roles-revised.png)

>[!NOTE]
>
> Många av dessa roller kan vara antingen interna eller externa beroende på hur respektive projekt är konfigurerat.

## Definiera roller {#roles}

I följande avsnitt finns en översikt över målgruppen:

### Adobe {#adobe-audience}

Adobe innehåller Adobe Managed Services-resurser som CSE (Customer Success Engineer) och Adobe Support.

### AEM {#aem-implementors}

AEM implementerare ansvarar för utvecklings- och integreringsuppgifter för att utveckla användarupplevelsen, anpassade mallar och bakomliggande integreringar för AEM.

Anpassade funktioner som krävs för att hantera parametrar för användarupplevelse hämtas och levereras via den här processen.

AEM implementerare distribuerar vanligtvis anpassade funktioner i faser över tid till platser. De kan till exempel först skapa stöd för uppspelning av grundläggande loopad video eller statiskt grafiskt innehåll. I nästa fas kan det finnas funktioner för uppspelning av lokaliserat innehåll via dynamiska mallar och metadatataggar, med ytterligare faser som har stöd för interaktiva element via pekskärmar, sensorer, dynamiska utlösare osv.

### AV-integratörer {#av-integrators}

A/V-integratorn är maskinvaruleverantör/partner. Det här är den part som arbetar med design och förberedelse av webbplatser i detaljhandeln, inklusive maskinvaruförvärv, konfigurering och driftsättning. Det är vanligtvis en avtalad tredje part som har åtkomst till ett Network Operations Center (NOC). I många fall är A/V-integratorn projektägare på grund av dess kontinuerliga engagemang efter lanseringen.

En AV-integratör ansvarar för att utföra identifieringar med slutkunder för att definiera krav som avgör projektets omfattning för att utforma, bygga och effektivt hantera driftsättningar kring maskinvara för digitala signaturer.

#### Övervägande av maskinvarupartner {#selecting-hardware-partner}

Det är viktigt att välja rätt maskinvarupartner. Följande frågor måste beaktas:

1. Vilka är villkoren i servicenivåavtalet?

1. Vad är Global täckning?

1. Är det 24 timmars support?

1. Hur hanteras enheterna?

1. Vilka är de aktiva övervaknings- och varningssystemen?

### Affärsstrategier {#business-strategist}

Affärsstrategierna representerar företagets beslutsfattare. Denna roll är mycket involverad i de olika stadierna av identifiering och krav och är den viktigaste drivkraften för projektet.

Det är de som definierar krav och ställer in KPI-mått. Affärsstrategi kan vara följande:

* Marknadsföring eller
* Sales Manager Digital Strategy Manager Creatives / Content Management.

Kreatörerna och Content Management-teamet samarbetar nära med strategigruppen och omvandlar kraven till kundupplevelser. De driver den övergripande UX-designen och kuraterar innehåll som kompletterar varumärket.

Kreatörerna och Content Management kan vara följande:

* eller
* Varumärkeshanteraren

### Projektledare {#project-managers}

Projektledare hanterar vanligtvis hela distributionen av AEM Screens. En projektledare är punktpersonen för hela genomförandet av det utsedda projektet och har ett viktigt ansvar, till exempel att ställa in tidslinjer, hantera teambehov och kommunikation, möta utmaningar och se till att målen uppfylls.

>[!NOTE]
>
>Om du vill veta mer om olika roller och ansvarsområden och målgruppen för ett projekt för digitala signaturer kan du besöka **[Projektroller och ansvarsområden](https://helpx.adobe.com/experience-manager/6-5/screens/using/project-roles-responsibilities.html)**.


## Projektfaser {#project-stages}

För att stödja en framgångsrik driftsättning av digitala signaturer är det vanligt att segmentera projektet i tre faser.  Dessa stadier kallas ofta **Dagar**. Det rör sig inte om litterala dagar utan om benämningar för varje större del av projektet.

1. Den första fasen kallas *Dag noll*. I det här steget ingår alla förberedelser och identifieringsåtgärder som krävs för att helt definiera projektets omfattning.
1. Den andra etappen *Dag ett*, avser alla aktiviteter som ingår i driftsättningen.
1. Det tredje och sista steget *Dag två* avser alla pågående operationer och supportelement som en del av den totala lösningen.

>[!NOTE]
>
>Även om den här guiden främst fokuserar på *dag ett* och *dag två*, så är alla tre faserna viktiga för att lyckas med digitala skyltningsprojekt.
>
>Följ ytterligare en video på **[Projektledning och driftsättning](https://helpx.adobe.com/experience-manager/6-5/screens/using/project-management-and-deployment.html)** om du vill veta mer om förproduktion, projektinitiering och projektutveckling.

## RACI-diagram {#raci-chart}

Följande är ett exempel på RACI-diagram som använder rolldefinitionerna.

>[!NOTE]
>
>Diagrammet är inte avsett att följas exakt, utan är ett exempel på vanliga uppgifter och överväganden i ett AEM Screens-projekt.

### RACI-definitioner {#raci-definitions}

* **Ansvarig**: Slutför uppgiften.

* **Konto**: Delegerar arbete och är den sista parten som granskar uppgiften innan den är klar.

* **Samråd**: Granska uppgiften eller slutprodukten för att ange indata.

* **Informerad**: Håll dig informerad om arbetets förlopp, men är inte involverad i detaljerna i slutprodukten.

Följande är ett exempel på ett RACI-diagram som använder rolldefinitionerna och ger ett exempel på vanliga uppgifter och överväganden i ett AEM Screens-projekt.

I följande tabell sammanfattas **Dag noll: Överväganden före försäljning**:

| **Fas** | **A/V-integratör** | **AEM** | **Affärsstrategi** | **Innehållshantering** |
|---|---|---|---|---|
| Gruppformatering och leverantörsval | I | I | RA | RA |
| Avtal om roller och ansvar | RA | RA | RA | RA |
| Anpassning till strategiska mål | CI | I | RA | RA |
| Rapporteringsbehov och identifiering av avkastning | I | C | RA | C |
| Besök webbplatsen och maskinvarukrav | RA | I | C | C |
| Processdefinition för support | C | I | RA | I |
| Definiera arbets- och projektplan | RA | RA | C | C |

I följande tabell sammanfattas **Dag ett: Projektimplementering (programdesign)**:

| **Fas** | **A/V-integratör** | **AEM** | **Affärsstrategi** | **Innehållshantering** |
|---|---|---|---|---|
| Avtal om roller och ansvar | RA | RA | RA | RA |
| Justering av projektplan och schema | RA | RA | C | C |
| Utvärdera aktuella servermiljöer | I | RA | I | I |
| UX-designkrav | I | RA | C | RA |
| Validering av tekniska krav | I | RA | RA | C |
| Arkitektur | I | RA | I | I |
| Validera datastruktur med gränssnittsdesign | I | RA | C | C |
| Programutveckling | RA | RA | RA | RA |
| Konfigurera AEM Screens Project | I | RA | C | I |
| Implementering av analyser | I | RA | C | - |
| Testning och driftsättning | RA | C | RA | I |
| Serverkonfiguration | I | RA | I | I |
| Plan för innehållsuppdatering | I | RA | C | C |
| Plan för övergång från pilot till produktion | RA | RA | I | I |
| Kunskapsöverföring | RA | RA | I | I |

I följande tabell sammanfattas **Dag ett: Projektimplementering (butiksberedskap)**:

| **Fas** | **A/V-integratör** | **AEM** | **Affärsstrategi** | **Innehållshantering** |
|---|---|---|---|---|
| Maskinvarubeställning och lagring | RA | I | I | I |
| Butiksintroduktionsplan | I | I | C | RA |
| Testning av användargodkännande för mellanlagring | I | C | RA |  |
| Konfiguration av maskinvarugrupp | RA | I | C | I |
| Avtal om support efter start | RA | C | RA | C |

I följande tabell sammanfattas **Dag ett: Dag ett: Projektimplementering (maskinvara)**:

| **Fas** | **A/V-integratör** | **AEM** | **Affärsstrategi** | **Innehållshantering** |
|---|---|---|---|---|
| Avtal om roller och ansvar | RA | RA | RA | RA |
| Detaljhandelsdesign omfattar kabeldragningar | - | - | - | - |
| Välj maskinvara | RAC | - | - | - |
| Enhetshantering för överordnad | RA | I | - | - |
| Enhetsbeställning och lagring &amp; konfigurering | RA | CI | I | - |
| Processdefinition för support | RA | I | RA | C |

>[!NOTE]
>
>Roller ändras under dag två (stöd efter start).

* **Upphovsman**: Innehållshantering + strategi

* **Utvecklare**: Vanligtvis en medlem i AEM Screens implementeringsteam, eller lämna över till den interna utvecklingsgruppen

* **Tekniker**: Antingen har den avtalats av AV-integratorn eller är en del av samma företag.

I följande tabell sammanfattas **Dag två: RACI-diagram för stöd efter start**:

| **Fas** | **Författare** | **Developer** | **Tekniker** |
|---|---|---|---|
| *Dag två: Stöd efter start* |
| Avtal om roller och ansvar | RA | RA | RA |
| Stöd för nivå 1 | I | I | RA |
| Stöd för nivå 2 | I | C | RA |
| Stöd för nivå 3 | I | RA | C |
| Innehållsuppdatering | RA | I | I |
| Utvärdera hur användarupplevelsen fungerar och identifiera områden med förbättringar | RA | C | I |
