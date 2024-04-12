---
title: Supportövervakning
description: Läs mer om Support Monitoring for AEM Screens Best Practices Guide.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Supportövervakning {#support-monitoring}

I det här avsnittet beskrivs de effektivaste strategierna för hantering av enhets- och innehållsavvikelser i digitala signeringsprojekt.

Supportövervakning innefattar:

* **Enhetsövervakning**
* **Innehållsövervakning**

## Innehållsövervakning {#content-monitoring}

Med innehållsövervakning kan du felsöka problem med innehåll som inte visas korrekt på skärmen:

1. Om ett tomt skärmproblem påträffas:

   * Kontrollera *förhandsgranska* så att du kan se om kanalen visar en svart skärm.
   * Registrera en *lokal kromspelare* (som tillägg) på din bärbara dator till den skärmen och se om det visar en svart skärm.
   * Högerklicka, inspektera och kontrollera *tillämpliga loggar*.

   Om detta inte sker på den lokala spelaren utan bara på enheten:

   * Kontrollera *medietyp* (används) som kan ha problem på den enheten och även kontrollera om innehållet har hämtats lokalt (rensat kanalcache för administratörsgränssnitt).
   * Inkludera alla *enhetsloggar* i biljetten för snabb felsökning.
   * *Samla in loggar* från AEM.

## Enhetsövervakning {#device-monitoring}

Enhetsövervakning för övervakning av den fysiska enheten om ett problem med tomma skärmar uppstår:

1. Om ett tomt skärmproblem påträffas:

   * Kontrollera om *visa* är påslagen.
   * Kontrollera om *dator* är påslagen och skickar en signal.
   * Högerklicka, inspektera och kontrollera *tillämpliga loggar*.
