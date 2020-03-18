---
title: Supportövervakning
seo-title: Supportövervakning för AEM-skärmar
description: Sidan beskriver Support Monitoring for AEM Screens Best Practices Guide
seo-description: Sidan beskriver Support Monitoring for AEM Screens Best Practices Guide
translation-type: tm+mt
source-git-commit: 3c91e0ec80b29bebcc066f45a1eef1fd74e00a13

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
   * Registrera en *lokal färgspelare* (som tillägg) på din bärbara dator för den skärmen och se om det visar en svart skärm.
   * Högerklicka och inspektera och kontrollera *tillämpliga loggar*.
   Om detta inte händer på den lokala spelaren utan bara på enheten:

   * Kontrollera *medietypen* (används) som kan ha problem på den enheten och kontrollera även om innehållet har hämtats lokalt (admin-gränssnittets rensa kanalcache).
   * Inkludera eventuella *enhetsloggar* i biljetten för snabb felsökning.
   * *Samla in loggar* från enheten från AEM.


## Enhetsövervakning {#device-monitoring}

Enhetsövervakning för övervakning av den fysiska enheten om ett problem med tomma skärmar uppstår:

1. Om ett tomt skärmproblem påträffas:

   * Kontrollera om *skärmen* är påslagen.
   * Kontrollera om *datorn* är påslagen och skickar en signal.
   * Högerklicka, inspektera och kontrollera *tillämpliga loggar*.

