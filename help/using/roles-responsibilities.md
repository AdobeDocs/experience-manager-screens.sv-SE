---
title: AEM Screens projektroller och ansvarsområden
description: Läs om AEM Screens projektroller och ansvarsområden.
exl-id: 9377625b-529a-4b46-89d9-f526de398639
source-git-commit: 7eae5038cb836219447d900bacf8af2faab51a43
workflow-type: tm+mt
source-wordcount: '1255'
ht-degree: 0%

---

# Projektroller och ansvarsområden {#roles-responsibilities}

Som erfaren AEM har du antagligen sett rollerna kallas *Författare*, *Utvecklare* och *IT-tekniker*.

I ett typiskt AEM Screens-projekt har rollerna förfinats ytterligare eftersom de har ett viktigt syfte i projektet.

I följande diagram visas vilka roller du kan förvänta dig att se i hela guiden.

![](/help/assets/project-roles-revised.png)

>[!NOTE]
>
> Många av dessa roller kan vara antingen interna eller externa beroende på hur respektive projekt är konfigurerat.

## Definiera roller {#roles}

I följande avsnitt finns en översikt över målgruppen:

### Adobe {#adobe-audience}

Adobe omfattar Adobe Managed Services-resurser som CSE (Customer Success Engineer) och Adobe Support.

### AEM {#aem-implementors}

AEM implementerare ansvarar för utvecklings- och integreringsuppgifter för att utveckla användarupplevelsen, anpassade mallar och bakomliggande integreringar för AEM.

Anpassade funktioner som krävs för att hantera parametrar för användarupplevelse hämtas och levereras via den här processen.

AEM implementerare distribuerar vanligtvis anpassade funktioner i faser över tid till platser. De kan till exempel först skapa stöd för uppspelning av grundläggande loopad video eller statiskt grafiskt innehåll. I nästa fas finns möjligheten att stödja uppspelning av lokaliserat innehåll via dynamiska mallar och metadatataggar. Andra faser har stöd för interaktiva element via pekskärmar, sensorer, dynamiska utlösare osv.

### Audio-Video-integratörer {#av-integrators}

Audio-Video Integrator är maskinvaruleverantör-partner. De är de som arbetar med design och förberedelser av webbplatser, inklusive maskinvaruförvärv, konfigurering och driftsättning. Det är vanligtvis en avtalad tredje part som har tillgång till ett Network Operations Center (NOC). Audio-Video Integrator är ofta projektägare på grund av dess kontinuerliga engagemang efter lanseringen.

En Audio-Video-integratör ansvarar för att utföra identifiering med slutkunder för att definiera krav, fastställa projektets omfattning för att utforma, bygga och effektivt hantera driftsättningar kring maskinvara för digitala signaturer.

>[!NOTE]
>
> Du måste ha en ljudvideointegratör som en del av AEM Screens-distributionen.

#### Övervägande av maskinvarupartner {#selecting-hardware-partner}

Det är viktigt att klicka på rätt maskinvarupartner. Följande frågor måste beaktas:

1. Vilka är villkoren i servicenivåavtalet?

1. Vad är Global täckning?

1. Är det 24-timmarsstöd?

1. Hur hanteras enheterna?

1. Vilka är de aktiva övervaknings- och varningssystemen?

### Affärsstrategier {#business-strategist}

Business Strategists är företagets beslutsfattare. Denna roll är mycket involverad i de olika stadierna av identifiering och krav och är den viktigaste drivkraften för projektet.

Det är de som definierar krav och ställer in KPI-mått. Affärsstrategi kan vara följande:

* Marknadsföring eller
* Sales Manager Digital Strategy Manager Creatives / Content Management.

Kreatörerna och Content Management-teamet samarbetar nära med strategigruppen och omvandlar kraven till kundupplevelser. De driver den övergripande UX-designen och kuraterar innehåll som kompletterar varumärket.

Kreatörerna och Content Management kan vara följande:

* eller
* Varumärkeshanteraren

### Projektledare {#project-managers}

Projektledare hanterar vanligtvis hela distributionen av AEM Screens. En projektledare är punktperson för hela genomförandet av det utsedda projektet. De har ett viktigt ansvar som att ställa in tidslinjer och hantera teamets behov. De påverkar också kommunikationen, löser problem och ser till att målen uppfylls.

>[!NOTE]
>
>Om du vill veta mer om olika roller och ansvarsområden och målgruppen för ett projekt för digitala signaturer kan du gå till **[Projektroller och ansvarsområden](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/project-roles-responsibilities)**.


## Projektfaser {#project-stages}

För att stödja en framgångsrik installation av digitala signaturer är det vanligt att segmentera projektet i tre steg. Dessa steg kallas vanligtvis **Dagar**. Det rör sig inte om litterala dagar utan om benämningar för varje större del av projektet.

1. Den första fasen kallas *dag noll*. I det här steget ingår alla aktiviteter före och efter försäljningen som krävs för att definiera projektets omfattning.
1. Den andra fasen, *Dag ett*, refererar till alla aktiviteter som ingår i distributionsinsatsen.
1. Den tredje och sista fasen är *Dag två*. Det avser alla pågående operationer och stödinslag som en del av den totala lösningen.

>[!NOTE]
>
>Den här guiden fokuserar främst på *Dag ett* och *Dag två*, men du måste tänka på alla tre faserna för att kunna köra ett digitalt signeringsprojekt.
>
>Titta på en video om **[Projektledning och distribution](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/project-management-and-deployment)** om du vill veta mer om förproduktion, projektinitiering och projektförlopp.

## RACI-diagram {#raci-chart}

Följande är ett exempel på RACI-diagram som använder rolldefinitionerna.

>[!NOTE]
>
>Du behöver inte följa diagrammet exakt. Istället ska den ge ett exempel på vanliga uppgifter och överväganden i ett AEM Screens-projekt.

### RACI-definitioner {#raci-definitions}

* **Ansvarig**: Utför arbetet med att slutföra uppgiften.

* **Konto**: Delegerar arbete och är den sista parten som granskar aktiviteten innan den är klar.

* **Konsulterad**: Granska aktiviteten eller slutprodukten för att ange indata.

* **Informerad**: Håll dig informerad om aktivitetens förlopp, men är inte involverad i detaljerna för slutprodukten.

Följande är ett exempel på ett RACI-diagram som använder rolldefinitionerna och ger ett exempel på vanliga uppgifter och överväganden i ett AEM Screens-projekt.

I följande tabell sammanfattas **Day Zero: Pre-sales Considerations**:

| **Fas** | **Integrator för ljud och video** | **AEM Implementor** | **Affärsstrategi** | **Innehållshantering** |
|---|---|---|---|---|
| Gruppformatering och leverantörsval | I | I | RA | RA |
| Avtal om roller och ansvar | RA | RA | RA | RA |
| Anpassning till strategiska mål | CI | I | RA | RA |
| Rapporteringsbehov och identifiering av avkastning | I | C | RA | C |
| Besök webbplatsen och maskinvarukrav | RA | I | C | C |
| Processdefinition för support | C | I | RA | I |
| Definiera arbets- och projektplanens omfattning | RA | RA | C | C |

I följande tabell sammanfattas **Dag ett: Projektimplementering (programdesign)**:

| **Fas** | **Integrator för ljud och video** | **AEM Implementor** | **Affärsstrategi** | **Innehållshantering** |
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

I följande tabell sammanfattas **dag ett: Projektimplementering (butiksberedskap)**:

| **Fas** | **Integrator för ljud och video** | **AEM Implementor** | **Affärsstrategi** | **Innehållshantering** |
|---|---|---|---|---|
| Maskinvarubeställning och lagring | RA | I | I | I |
| Butiksintroduktionsplan | I | I | C | RA |
| Testning av användargodkännande för mellanlagring | I | C | RA |   |
| Konfiguration av maskinvarugrupp | RA | I | C | I |
| Avtal om support efter start | RA | C | RA | C |

I följande tabell sammanfattas **Day One: Day One: Project Implementation (Hardware)**:

| **Fas** | **Integrator för ljud och video** | **AEM Implementor** | **Affärsstrategi** | **Innehållshantering** |
|---|---|---|---|---|
| Avtal om roller och ansvar | RA | RA | RA | RA |
| Detaljhandelsdesign omfattar kabeldragningar | - | - | - | - |
| Välj maskinvara | RAC | - | - | - |
| Enhetshantering för primär | RA | I | - | - |
| Enhetsbeställning och lagring &amp; konfigurering | RA | CI | I | - |
| Processdefinition för support | RA | I | RA | C |

>[!NOTE]
>
>Roller ändras under dag två (stöd efter start).

* **Författare**: Innehållshantering + strategi

* **Utvecklare**: Normalt är du medlem i AEM Screens implementeringsteam, eller överlämnar till ett internt utvecklingsteam

* **Tekniker**: Anskaffas antingen av Audio-Video Integrator eller ingår i samma företag.

I följande tabell sammanfattas **Dag två: RACI-diagram för stöd för poststart**:

| **Fas** | **Författare** | **Utvecklare** | **Tekniker** |
|---|---|---|---|
| *Dag två: Support efter start* |
| Avtal om roller och ansvar | RA | RA | RA |
| Stöd för nivå 1 | I | I | RA |
| Stöd för nivå 2 | I | C | RA |
| Stöd för nivå 3 | I | RA | C |
| Innehållsuppdatering | RA | I | I |
| Utvärdera UX-framgången och identifiera områden med förbättring | RA | C | I |
