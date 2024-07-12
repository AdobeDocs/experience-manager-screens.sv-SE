---
title: Supportövervakning
description: Läs mer om Support Monitoring for AEM Screens Best Practices Guide.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '218'
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

   * Kontrollera *förhandsgranskningen* så att du kan se om kanalen visar en svart skärm.
   * Registrera en *lokal Chrome-spelare* (som ett tillägg) på din bärbara dator på den skärmen och se om det visar en svart skärm.
   * Högerklicka och inspektera *tillämpliga loggar*.

   Om problemet inte inträffar på den lokala spelaren utan bara på enheten:

   * Kontrollera den *medietyp* (används) som kan ha problem på den enheten och kontrollera även om innehållet har hämtats lokalt (rensad kanal för administratörsgränssnitt).
   * Inkludera eventuella *enhetsloggar* i biljetten för snabb felsökning.
   * *Samla in loggar* från enheten från AEM.

## Enhetsövervakning {#device-monitoring}

Enhetsövervakning som är relaterad till övervakning av den fysiska enheten om ett problem med tomma skärmar uppstår:

1. Om ett tomt skärmproblem påträffas:

   * Kontrollera om *display* är påslagen.
   * Kontrollera om *datorn* är påslagen och skickar en signal.
   * Högerklicka, inspektera och kontrollera *tillämpliga loggar*.
