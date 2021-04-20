---
title: Uppdatera gruppvis offline
seo-title: Uppdatera gruppvis offline
description: Följ den här sidan för att lära dig hur du kan uppdatera alla kanaler samtidigt.
seo-description: Följ den här sidan för att lära dig hur du kan uppdatera alla kanaler samtidigt.
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 1%

---


# Uppdatera satsvis offline {#bulk-offline-update}

I det här avsnittet beskrivs följande ämnen om Uppdatera gruppvis offline:

* **Översikt**
* **Använda Uppdatera gruppvis offline**

>[!CAUTION]
>
>Denna AEM Screens-funktionalitet är endast tillgänglig om du har installerat AEM 6.3 Feature Pack 3 eller AEM 6.4 Screens Feature Pack 1.
>
>Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobe Support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

## Översikt {#overview}

Uppdatera gruppvis offline gör att du kan uppdatera alla kanaler samtidigt. Då slipper du krånglet med att navigera till en viss kanal och uppdatera innehållet. I stället kan du uppdatera allt innehåll i kanaler för ett visst projekt på en gång.

Du kan även schemalägga den här aktiviteten under en tid med lägre nätverkstrafik.

>[!NOTE]
>
>Funktionen Uppdatera gruppvis offline är optimerad för att endast uppdatera de kanaler som har ändrats.

## Använda uppdatering {#using-bulk-offline-update} för flera offlinor

Du kan manuellt använda bulkuppdatering offline från användargränssnittet (UI) eller schemalägga bulkuppdateringen från OSGi-tjänster.

### Använda AEM Screens användargränssnitt {#using-aem-screens-user-interface}

Följ stegen nedan om du vill använda en bulkuppdatering för ett AEM Screens-projekt:

1. Gå till ditt AEM Screens-projekt.
1. Markera projektet och klicka på **Uppdatera offlineinnehåll** i åtgärdsfältet om du vill uppdatera kanalinnehållet manuellt.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Konfiguration av Adobe Experience Manager Web Console {#adobe-experience-manager-web-console-configuration}

Följ stegen nedan om du vill använda en bulkuppdatering för ett AEM Screens-projekt:

1. Konfiguration av Adobe Experience Manager Web Console.
1. Sök efter bulkbaserade uppdateringstjänster.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Lägg till följande egenskaper:

   **Projektsökväg** Ange sökvägen till ditt AEM Screens-projekt. Sökvägen är vanligtvis `/content/screens/<Name of your project>`.

   *Till exempel*, `/content/screens/we-retail`. Du hittar den här sökvägen i URL:en genom att välja ett projekt under AEM Screens (klicka inte på ikonen).

   >[!NOTE]
   >
   >Ange projektsökvägen i förhållande till kanalen.

   **Schemalägg** frekvensAnge en tidpunkt, till exempel klockan 17:00 eller 17:00, då den här tjänsten ska uppdatera offlineinnehåll.

1. Klicka på **Spara** om du vill spara inställningarna så uppdateras innehållet vid den angivna tidpunkten.

