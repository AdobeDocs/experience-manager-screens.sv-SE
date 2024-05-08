---
title: Testning och kvalitetssäkring
description: Läs mer om testning och kvalitetssäkring av AEM Screens i Best Practices Guide.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Testning och kvalitetssäkring {#testing-quality}

>[!NOTE]
>En typisk intressent för den här aktiviteten är en ljud-/videointegratör.

När ni närmar er driftsättningen av det digitala signeringsnätverket skapar ni en Test- och QA-plan som behandlar alla element i nätverket, inklusive alla maskinvarukomponenter, alla programvarukomponenter och alla nätverkskomponenter.
Under fasen ska hela testsystem byggas och testas fullt ut.

En checklista bör skapas som identifierar alla tidigare definierade KPI:er och mäter slutprodukterna mot dem.

>[!NOTE]
>
>Denna fas bör också användas som ett verktyg för att skapa en installations- och användarhandbok som senare kan levereras med utrustningen och behållas på plats för framtida referens.

Följande faktorer bör beaktas:

## 1. Mekaniska överväganden {#mechanical-considerations}

Följande mekaniska överväganden rekommenderas:

* skärmmontering
* montering av spelare
* ventilation
* kringutrustning
* kabelhantering
* enhetsnätverk

## 2. Överväganden gällande programvara {#software-considerations}

Följande programvaruöverväganden rekommenderas:

* enhetsregistrering
* mediepublicering
* uppspelning
* databasberoenden (tidigare definierade)


## 3. Överväganden gällande enhetshantering {#device-management-considerations}

AEM Screens innehåller en Device Control Center-modul som gör att du kan hantera slutpunkter för skärmsspelarprogram.

Detta avser alla *player* maskinvaruenhet som har programmet Skärmspelaren installerat och som är registrerad för en instans av AEM.
Med den här modulen kan du:

1. Felloggar för bildspelsprogram
1. Hantera fjärrskärmbilder
1. Hantera innehållsnedladdningar
1. Hantera problem med programomstart

Mer detaljerad information om ***Device Control Center***, se [Felsökning av Device Control Center](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) in **AEM Screens Användarhandbok**.

>[!CAUTION]
>
>Använd inte Device Control Center för att:
>
>* Installera nya versioner av spelarprogrammet
>* Övervaka resurser på systemnivå
>* Felsöka systemnivåfel
>* Tillåt åtgärder på fjärrskrivbord


>[!NOTE]
>
> Adobe rekommenderar att dedikerade enhetshanteringsplattformar från tredje part används för alla distributioner.

Vilken plattform du väljer beror på flera faktorer, bland annat ***måloperativsystem***, ***projektkrav*** och ***antal slutpunkter***.

Några exempel är följande:

* Google Chrome Device Management
* TeamViewer
* AirWatch
* `42Gears`
* Egendefinierat mellanvara för ljud-/videointegrering
