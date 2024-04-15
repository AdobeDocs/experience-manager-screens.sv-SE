---
title: Skapa och hantera scheman
description: Lär dig mer om scheman där du kan ordna kanaler i återanvändbara grupper så att du inte behöver upprepa deras uppdrag separat för varje skärm där du vill visa ditt innehåll.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Skapa och hantera scheman {#creating-and-managing-schedules}

**Scheman** i AEM Screens kan du ordna kanalerna i återanvändbara grupper så att du inte behöver upprepa deras uppdrag separat för varje skärm där du vill visa ditt innehåll.

Scheman, när de kombineras med ***DayParting*** kan du ange ett globalt schema med flera kanaler som körs vid specifika tidpunkter på dygnet och återanvända det som är inställt för alla skärmar samtidigt.

>[!NOTE]
>
>Den här AEM Screens-funktionen är bara tillgänglig om du har installerat AEM 6.3 Sites Feature Pack 1. Kontakta Adobe Support och begär åtkomst till detta funktionspaket. När du har de behörigheter som krävs kan du hämta den från paketresursen.

## Skapa ett schema {#creating-a-schedule}

Du kan skapa ett schema för ditt skärmsprojekt som kan hantera alla aktiviteter för ditt användningsfall.

Följ stegen nedan för att skapa ett schema för din kanal:

1. Klicka på länken Adobe Experience Manager (längst upp till vänster) och sedan på Skärmar. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.
1. Navigera till Skärmprojekt och klicka **Scheman**.
1. Klicka **Skapa** i åtgärdsfältet.
1. Välj **Schema** från **Skapa** guide och klicka **Nästa**.

1. Ange **Namn** och **Titel** och klicka **Skapa**.

Du kan se en schemamapp med det angivna namnet och titeln i ditt projekt.


## Visa instrumentpanel {#viewing-dashboard}

När du har skapat en mapp för scheman i ditt projekt kan du visa informationen från kontrollpanelen för scheman.

Följ stegen nedan för att visa kontrollpanelen för schemat. I följande exempel visas kontrollpanelen för `We.Retail` projekt:

1. Navigera till **Scheman** mapp med skärmar (till exempel `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Välj **Kontrollpanel** i åtgärdsfältet.

   Du kan visa tre olika paneler som **SCHEMALÄGGSINFORMATION**, **TILLDELADE KANALER** och **TILLDELADE VISNINGAR**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Panelen Schemalägg information** Klicka på Egenskaper i det övre högra hörnet på SCHEMALÄGGNINGENS INFORMATIONspanel för att visa/ändra schemats egenskaper.

   **Panelen Tilldelade kanaler** Klicka på +Tilldela kanal i det övre högra hörnet på panelen Tilldelade kanaler för att öppna dialogrutan Kanaltilldelning.

   **Tilldelad visningspanel** Välj någon av visningslägena på panelen TILLDELADE VISNINGAR för att öppna kontrollpanelen.
