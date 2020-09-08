---
title: Hantera enheter
seo-title: Hantera enheter
description: Den här sidan beskriver enhetstilldelning.
seo-description: Följ den här sidan om du vill veta mer om enhetstilldelning. Med enhetskonsolen kan du komma åt enhetshanteraren och tilldela enheten till en skärm.
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
translation-type: tm+mt
source-git-commit: 6d86710a5d0a4fd1cf6c0dc46961d231b0128f95
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 2%

---


# Hantera enheter {#managing-devices}

Den här sidan beskriver enhetstilldelning.

Med enhetskonsolen kan du komma åt enhetshanteraren och tilldela enheten till en skärm.

>[!CAUTION]
>
>Innan du tilldelar din enhet måste du registrera den. Mer information finns i [Enhetsregistrering](device-registration.md).

## Enhetstilldelning {#device-assignment}

Följ stegen nedan för att tilldela en enhet till en skärm:

1. Navigera till mappen Enheter i ditt projekt, till exempel

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Välj mappen **Enheter** och tryck/klicka på **Enhetshanteraren** i åtgärdsfältet. De tilldelade och ej tilldelade enheterna visas.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Välj en ej tilldelad enhet i listan och tryck/klicka på **Tilldela enhet** i åtgärdsfältet.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Välj den skärm som du vill tilldela enheten till i listan och tryck/klicka på **Tilldela**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Tryck/klicka på **Slutför** för att slutföra tilldelningsprocessen.


   På kontrollpanelen visas den tilldelade enheten på panelen **Enheter** .

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Klicka på (**...**) i det övre högra hörnet av **enhetspanelen** för att antingen lägga till enhetskonfiguration eller uppdatera enheterna.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Varje gång den första enheten läggs till i ett nytt skärmsprojekt skapas en användargrupp.
>Om projektnodnamnet till exempel är *vi-butik*&#x200B;är användargruppnamnet *screens-we-retail-devices*.
>Den här gruppen läggs till som medlem i gruppen **Medarbetare** , vilket visas i bilden nedan:

![chlimage_1-39](assets/chlimage_1-39.png)

### Nästa steg {#the-next-steps}

När du känner till hur du tilldelar kanal till en skärm kan du läsa följande resurser:

* [Övervaka och felsöka](monitoring-screens.md)

