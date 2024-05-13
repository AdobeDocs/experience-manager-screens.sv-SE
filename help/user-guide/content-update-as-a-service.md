---
title: Innehållsuppdatering som tjänst
description: Läs om innehållsuppdatering som en tjänst.
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Innehållsuppdatering som tjänst {#content-update-as-a-service}

I det här avsnittet beskrivs följande ämnen om uppdatering av innehåll som en tjänst:

* **Översikt**
* **Använda Uppdatera gruppvis offline**

<!--
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission you can download it from Package Share. -->

## Ökning {#overview}

Med Uppdatera gruppvis offline kan du uppdatera alla kanaler samtidigt. Då slipper du krånglet med att navigera till en viss kanal och uppdatera innehållet. I stället kan du uppdatera allt innehåll i kanaler för ett visst projekt på en gång.

Du kan även schemalägga den här aktiviteten under en tid med lägre nätverkstrafik.

>[!NOTE]
>
>Funktionen Uppdatera gruppvis offline är optimerad för att endast uppdatera de kanaler som har ändrats.

## Använda Uppdatera gruppvis offline {#using-bulk-offline-update}

Du kan manuellt använda massvis offlineuppdatering från användargränssnittet (UI) eller schemalägga gruppuppdatering från OSGi-tjänster.

### Använda AEM Screens användargränssnitt {#using-aem-screens-user-interface}

Följ stegen nedan om du vill använda en bulkuppdatering för ett AEM Screens-projekt:

1. Gå till ditt AEM Screens-projekt.
1. Klicka på projektet och klicka på **Uppdatera offlineinnehåll** från åtgärdsfältet för att uppdatera kanalinnehållet manuellt.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Konfiguration av Adobe Experience Manager Web Console {#adobe-experience-manager-web-console-configuration}

Följ stegen nedan om du vill använda en bulkuppdatering för ett AEM Screens-projekt:

1. Konfiguration av Adobe Experience Manager Web Console.
1. Sök efter offlineuppdateringstjänster för massutskick.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Lägg till följande egenskaper:

   **Projektsökväg** Ange sökvägen till ditt AEM Screens-projekt. Banan är vanligtvis `/content/screens/<Name of your project>`.

   *Till exempel*, `/content/screens/we-retail`. Du hittar den här sökvägen i URL:en genom att välja ett projekt under AEM Screens (klicka inte på ikonen).

   >[!NOTE]
   >
   >Ange projektsökvägen i förhållande till kanalen.

   **Schemaläggningsfrekvens** Ange t.ex. en tidpunkt, 05:00 eller 17:00, då den här tjänsten ska uppdatera offlineinnehåll.

1. Klicka **Spara** så att du kan spara inställningarna. Allt innehåll uppdateras vid den angivna tidpunkten.
