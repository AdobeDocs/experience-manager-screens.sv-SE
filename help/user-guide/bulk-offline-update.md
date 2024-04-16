---
title: Uppdatera gruppvis offline
description: Lär dig hur du kan uppdatera alla kanaler samtidigt.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Uppdatera gruppvis offline {#bulk-offline-update}

I det här avsnittet beskrivs följande ämnen om Uppdatera gruppvis offline:

* **Översikt**
* **Använda Uppdatera gruppvis offline**

<!-- OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permissions you can download it from Package Share. -->

## Ökning {#overview}

Uppdatera gruppvis offline gör att du kan uppdatera alla kanaler samtidigt. Då slipper du krånglet med att navigera till en viss kanal och uppdatera innehållet. I stället kan du uppdatera allt innehåll i kanaler för ett visst projekt på en gång.

Du kan även schemalägga den här aktiviteten under en tid med lägre nätverkstrafik.

>[!NOTE]
>
>Funktionen Uppdatera gruppvis offline är optimerad för att endast uppdatera de kanaler som har ändrats.

## Använda Uppdatera gruppvis offline {#using-bulk-offline-update}

Du kan manuellt använda bulkuppdatering offline från användargränssnittet (UI) eller schemalägga bulkuppdateringen från OSGi-tjänster.

### Använda AEM Screens användargränssnitt {#using-aem-screens-user-interface}

Följ stegen nedan om du vill använda en bulkuppdatering för ett AEM Screens-projekt:

1. Gå till ditt AEM Screens-projekt.
1. Klicka på projektet och sedan på **Uppdatera offlineinnehåll** i åtgärdsfältet så att du kan uppdatera kanalinnehållet manuellt.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Konfiguration av Adobe Experience Manager Web Console {#adobe-experience-manager-web-console-configuration}

Följ stegen nedan om du vill använda en bulkuppdatering för ett AEM Screens-projekt:

1. Konfiguration av Adobe Experience Manager Web Console.
1. Sök efter bulkbaserade uppdateringstjänster.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Lägg till följande egenskaper:

   **Projektsökväg** Ange sökvägen till ditt AEM Screens-projekt. Banan är vanligtvis `/content/screens/<Name of your project>`.

   *Till exempel*, `/content/screens/we-retail`. Du hittar den här sökvägen i URL:en genom att välja ett projekt under AEM Screens (klicka inte på ikonen).

   >[!NOTE]
   >
   >Ange projektsökvägen i förhållande till kanalen.

   **Schemaläggningsfrekvens** Ange t.ex. en tidpunkt, 05:00 eller 17:00, då den här tjänsten ska uppdatera offlineinnehåll.

1. Klicka **Spara** för att spara inställningarna. Innehållet uppdateras vid den angivna tidpunkten.
