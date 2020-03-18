---
title: Innehållsuppdatering som tjänst
seo-title: Innehållsuppdatering som tjänst
description: Följ den här sidan om du vill veta mer om innehållsuppdatering som en tjänst.
seo-description: Följ den här sidan om du vill veta mer om innehållsuppdatering som en tjänst.
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
translation-type: tm+mt
source-git-commit: 323e2df2419cc65de7bfe88648ffd1dbd3a91aec

---


# Innehållsuppdatering som tjänst {#content-update-as-a-service}

I det här avsnittet beskrivs följande ämnen om uppdatering av innehåll som en tjänst:

* **Översikt**
* **Använda Uppdatera gruppvis offline**

>[!CAUTION]
>
>Den här AEM-skärmfunktionen är bara tillgänglig om du har installerat AEM 6.3 Feature Pack 3 eller AEM 6.4 Screens Feature Pack 1.
>
>Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobes support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

## Översikt {#overview}

Uppdatera gruppvis offline gör att du kan uppdatera alla kanaler samtidigt. Då slipper du krånglet med att navigera till en viss kanal och uppdatera innehållet. I stället kan du uppdatera allt innehåll i kanaler för ett visst projekt på en gång.

Du kan även schemalägga den här aktiviteten under en tid med lägre nätverkstrafik.

>[!NOTE]
>
>Funktionen Uppdatera gruppvis offline är optimerad för att endast uppdatera de kanaler som har ändrats.

## Använda Uppdatera gruppvis offline {#using-bulk-offline-update}

Du kan manuellt använda bulkuppdatering offline från användargränssnittet (UI) eller schemalägga bulkuppdateringen från OSGi-tjänster.

### Använda användargränssnittet för AEM-skärmar {#using-aem-screens-user-interface}

Följ stegen nedan om du vill använda en bulkuppdatering för ett AEM Screens-projekt:

1. Gå till ditt AEM Screens-projekt.
1. Markera projektet och klicka på **Uppdatera offlineinnehåll** i åtgärdsfältet för att manuellt uppdatera kanalinnehållet.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Konfiguration av Adobe Experience Manager Web Console {#adobe-experience-manager-web-console-configuration}

Följ stegen nedan om du vill använda en bulkuppdatering för ett AEM Screens-projekt:

1. Konfiguration av Adobe Experience Manager Web Console.
1. Sök efter bulkbaserade uppdateringstjänster.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Lägg till följande egenskaper:

   **Projektsökväg** Ange sökvägen till ditt AEM-skärmsprojekt. Banan är vanligtvis `/content/screens/<Name of your project>`aktiv.

   *Exempel*, `/content/screens/we-retail`. Du hittar den här sökvägen i URL:en genom att välja ett projekt under AEM-skärmar (klicka inte på ikonen).

   >[!NOTE]
   >
   >Ange projektsökvägen i förhållande till kanalen.

   **Schemafrekvens** Ange en tidpunkt, till exempel klockan 17:00 eller 17:00, då den här tjänsten ska uppdatera offlineinnehåll.

1. Klicka på **Spara** för att spara inställningarna så uppdateras innehållet vid den angivna tidpunkten.

