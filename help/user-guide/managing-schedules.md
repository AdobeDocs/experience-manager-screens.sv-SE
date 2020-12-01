---
title: Skapa och hantera scheman
seo-title: Hantera scheman
description: Följ den här sidan för att lära dig mer om scheman, där du kan ordna kanaler i återanvändbara grupper så att du inte behöver upprepa deras uppdrag separat för varje skärm där du vill visa ditt innehåll.
seo-description: Följ den här sidan för att lära dig mer om scheman, där du kan ordna kanaler i återanvändbara grupper så att du inte behöver upprepa deras uppdrag separat för varje skärm där du vill visa ditt innehåll.
uuid: c05328a0-620a-4597-b7b3-f4433e78d4e9
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 75ed3c42-4be9-42ae-9d76-e0343af81516
translation-type: tm+mt
source-git-commit: 6d86710a5d0a4fd1cf6c0dc46961d231b0128f95
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---


# Skapa och hantera scheman {#creating-and-managing-schedules}

**Med scheman** i AEM Screens kan du ordna kanaler i återanvändbara grupper så att du inte behöver upprepa deras uppdrag separat för varje skärm som du vill visa ditt innehåll på.

När du kombinerar scheman med ***DayParting*** kan du ange ett globalt schema med flera kanaler som körs vid specifika tidpunkter på dagen och återanvända inställningarna för alla skärmar samtidigt.

>[!NOTE]
>
>Den här AEM Screens-funktionen är bara tillgänglig om du har installerat AEM 6.3 Sites Feature Pack 1. Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobe Support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

## Skapar ett schema {#creating-a-schedule}

Du kan skapa ett schema för ditt skärmsprojekt som hanterar alla aktiviteter för ditt användningsfall.

Följ stegen nedan för att skapa ett schema för din kanal:

1. Klicka på länken Adobe Experience Manager (längst upp till vänster) och sedan på Skärmar. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.
1. Navigera till Skärmprojekt och klicka på **Scheman**.
1. Klicka på **Skapa** i åtgärdsfältet.
1. Välj **Schemalägg** i guiden **Skapa** och klicka på **Nästa**.

1. Ange **Namn** och **Titel** och klicka på **Skapa**.

Du ser en mapp med scheman med namn och titel i ditt projekt.


## Visar instrumentpanelen {#viewing-dashboard}

När du har skapat en mapp för scheman i ditt projekt kan du visa informationen från kontrollpanelen för scheman.

Följ stegen nedan för att visa kontrollpanelen för scheman. I följande exempel visas instrumentpanelen för projektet We.Retail:

1. Navigera till mappen **Scheman** för skärmar (till exempel We.Retail)-projektet.

   ![chlimage_1](assets/chlimage_1.png)

1. Klicka på **Kontrollpanel** i åtgärdsfältet för att öppna schemats kontrollpanel.

   Du kan visa tre olika paneler, till exempel **SCHEMALÄGGNINGSINFORMATION**, **TILLDELADE KANALER** och **TILLDELADE VISNINGAR**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Panelen Schemalägg informationKlicka** på Egenskaper i det övre högra hörnet på SCHEMALÄGGNINGSINFORMATIONSPANELEN för att visa/ändra schemats egenskaper.

   **Tilldelad** kanalpanelKlicka på +Tilldela kanal i det övre högra hörnet på panelen Tilldelade kanaler för att öppna dialogrutan Kanaltilldelning.

   **Tilldelad** visningspanelVälj någon av skärmarna på den tilldelade visningspanelen för att öppna kontrollpanelen.

