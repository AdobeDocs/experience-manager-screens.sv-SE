---
title: Supportövervakning
seo-title: Supportövervakning för AEM Screens
description: På sidan beskrivs Support Monitoring for AEM Screens Best Practices Guide
seo-description: På sidan beskrivs Support Monitoring for AEM Screens Best Practices Guide
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Supportövervakning {#support-monitoring}

I det här avsnittet beskrivs de effektivaste strategierna för hantering av enhets- och innehållsavvikelser i digitala signeringsprojekt.

Supportövervakning innefattar:

* **Enhetsövervakning**
* **Innehållsövervakning**

## Innehållsövervakning {#content-monitoring}

Med innehållsövervakning kan du felsöka problem som rör innehåll som inte visas korrekt på skärmen:

1. Om ett tomt skärmproblem påträffas:

   * Kontrollera *förhandsgranskning* för att se om kanalen visar en svart skärm
   * Registrera en *lokal kromspelare* (som tillägg) på din bärbara dator till den skärmen och se om det visar en svart skärm.
   * Högerklicka och inspektera och kontrollera *tillämpliga loggar*.

   Om detta inte händer på den lokala spelaren utan bara på enheten:

   * Kontrollera *medietyp* (används) som kan ha problem på den enheten och kontrollera även om innehållet har hämtats lokalt (admin-gränssnittets rensa kanalcache).
   * Ta med alla *enhetsloggar* i biljetten för snabb felsökning.
   * *Samla in* loggar från enheten från AEM.


## Enhetsövervakning {#device-monitoring}

Enhetsövervakning för övervakning av den fysiska enheten om ett problem med tomma skärmar uppstår:

1. Om ett tomt skärmproblem påträffas:

   * Kontrollera om *skärmen* är påslagen.
   * Kontrollera om *datorn* är påslagen och skickar en signal.
   * Högerklicka, inspektera och kontrollera *tillämpliga loggar*.

