---
title: Testning och kvalitetssäkring
seo-title: Testning och kvalitetssäkring för AEM Screens
description: På sidan beskrivs Testing and Quality Assurance for AEM Screens Best Practices Guide
seo-description: På sidan beskrivs Testing and Quality Assurance for AEM Screens Best Practices Guide
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# Testning och kvalitetssäkring {#testing-quality}

>[!NOTE]
>En typisk intressent för den här aktiviteten är en A/V-integratör.

När vi kommer närmare den faktiska driftsättningen av det digitala signeringsnätet bör vi skapa en Test- och QA-plan som behandlar alla element i nätverket, inklusive alla maskinvarukomponenter, alla programvarukomponenter och alla nätverkskomponenter.
Under fasen ska hela testsystem byggas och testas fullt ut.

En checklista ska skapas som identifierar alla tidigare definierade KPI:er och mäter slutprodukten mot dem.

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

AEM Screens har en Device Control Center-modul som gör att du kan hantera slutpunkter för skärmsspelarprogram.

Detta avser alla *spelarmaskinvaruenheter* som har programmet Skärmspelaren installerad och som är registrerade för en instans av AEM.
Med den här modulen kan du:

1. Felloggar för bildspelsprogram
1. Hantera fjärrskärmbilder
1. Hantera innehållsnedladdningar
1. Hantera problem med programomstart

Mer information om ***Device Control Center*** finns i [Troubleshooting Device Control Center](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) i **AEM Screens User Guide**.

>[!CAUTION]
>
> Använd inte Device Control Center för att:
> 1. Installera nya versioner av spelarprogrammet
> 1. Övervaka resurser på systemnivå
> 1. Felsöka systemnivåfel
> 1. Tillåt åtgärder på fjärrskrivbord



>[!NOTE]
>
> Adobe rekommenderar att dedikerade enhetshanteringsplattformar från tredje part används för alla distributioner.

Vilken plattform du väljer beror på ett antal faktorer, bland annat ***måloperativsystemet***, ***projektkraven*** och ***antalet slutpunkter***.

Det finns få exempel:

* Google Chrome-enhetshantering
* TeamViewer
* AirWatch
* 42Gears
* Äkta AV-integratör för mellanvara
