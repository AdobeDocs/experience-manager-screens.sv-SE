---
title: Skapa och hantera scheman
description: Läs mer om scheman där du kan ordna kanaler i återanvändbara grupper så att du inte behöver upprepa deras tilldelning individuellt.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# Skapa och hantera scheman {#creating-and-managing-schedules}

Med **Scheman** i AEM Screens kan du ordna kanaler i återanvändbara grupper. Om du gör det behöver du inte upprepa deras uppdrag separat för varje skärm där du vill visa innehållet.

När du kombinerar scheman med ***DayParting*** kan du ange ett globalt schema med flera kanaler som körs vid specifika tidpunkter på dagen och återanvända det som är inställt för alla skärmar samtidigt.

>[!NOTE]
>
>Den här AEM Screens-funktionen är bara tillgänglig om du har installerat AEM 6.3 Sites Feature Pack 1. Kontakta Adobe Support och begär åtkomst till detta funktionspaket. När du har de behörigheter som krävs kan du hämta den från paketresursen.

## Skapa ett schema {#creating-a-schedule}

Du kan skapa ett schema för ditt Screens-projekt som kan hantera alla aktiviteter för ditt användningsfall.

Följ stegen nedan för att skapa ett schema för din kanal:

1. Klicka på länken Adobe Experience Manager (överst till vänster) och sedan på Screens. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.
1. Navigera till Screens-projekt och klicka på **Scheman**.
1. Klicka på **Skapa** i åtgärdsfältet.
1. Klicka på **Schemalägg** i guiden **Skapa** och klicka på **Nästa**.

1. Ange **Namn** och **Titel** och klicka på **Skapa**.

Du kan se en schemamapp med det angivna namnet och titeln i ditt projekt.


## Visa instrumentpanel {#viewing-dashboard}

När du har skapat en schemamapp i ditt projekt kan du visa informationen från kontrollpanelen för scheman.

Följ stegen nedan för att visa kontrollpanelen för schemat. I följande exempel visas kontrollpanelen för projektet `We.Retail`:

1. Navigera till mappen **Scheman** i Screens-projektet (till exempel `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Klicka på **Instrumentpanel** i åtgärdsfältet.

   Du kan visa tre olika paneler, till exempel **SCHEMALÄGGNINGSINFORMATION**, **TILLDELADE KANALER** och **TILLDELADE VISNINGAR**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Panelen Schemalägg information** Klicka på Egenskaper i det övre högra hörnet på SCHEMALÄGGNINGSINFORMATIONSPanelen för att visa/ändra schemats egenskaper.

   **Panelen Tilldelade kanaler** Klicka på +Tilldela kanal i det övre högra hörnet på panelen Tilldelade kanaler för att öppna dialogrutan Kanaltilldelning.

   **Tilldelad visningspanel** Klicka på någon av skärmarna på den tilldelade visningspanelen för att öppna kontrollpanelen.
