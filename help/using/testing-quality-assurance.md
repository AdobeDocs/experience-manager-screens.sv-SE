---
title: Testning och kvalitetssäkring
description: Läs mer om testning och kvalitetssäkring av AEM Screens i Best Practices Guide.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Testning och kvalitetssäkring {#testing-quality}

>[!NOTE]
>En typisk intressent för den här aktiviteten är en Audio-Video Integrator.

När ni närmar er driftsättningen av det digitala signeringsnätverket skapar ni en Test- och QA-plan som behandlar alla element i nätverket, inklusive alla maskinvarukomponenter, alla programvarukomponenter och alla nätverkskomponenter.
Under fasen ska hela testsystem byggas och testas fullt ut.

En checklista bör skapas som identifierar alla tidigare definierade KPI:er och mäter slutprodukterna mot dem.

>[!NOTE]
>
>Den här fasen bör även användas som ett verktyg för att skapa en installations- och användarhandbok. Båda kan senare levereras med utrustningen och behållas på plats för framtida referens.

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

AEM Screens har en Device Control Center-modul som möjliggör hantering av slutpunkter för Screens Player-program.

Det avser alla *Player*-maskinvaruenheter som har Screens Player-programmet installerat och som är registrerade för en instans av AEM.
Med den här modulen kan du:

1. Felloggar för bildspelsprogram
1. Hantera fjärrskärmbilder
1. Hantera innehållsnedladdningar
1. Hantera problem med programomstart

Mer information om ***Device Control Center*** finns i [Troubleshooting Device Control Center](https://experienceleague.adobe.com/sv/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) i **AEM Screens User Guide**.

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

Vilken plattform du väljer beror på flera faktorer, bland annat ***måloperativsystemet***, ***projektkraven*** och ***antalet slutpunkter***.

Några exempel är följande:

* Google Chrome Device Management
* TeamViewer
* AirWatch
* `42Gears`
* Tillverkningsspecifik programvara för ljud- och videointegrering
