---
title: Hantera enheter
description: Läs om enhetstilldelning och -hantering i AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 5%

---

# Hantera enheter {#managing-devices}

Den här sidan beskriver enhetstilldelning.

Med enhetskonsolen kan du komma åt enhetshanteraren och tilldela enheten till en skärm.

>[!CAUTION]
>
>Registrera enheten innan du tilldelar den. Se [Enhetsregistrering](device-registration.md).

## Enhetstilldelning {#device-assignment}

Följ stegen nedan för att tilldela en enhet till en skärm:

1. Navigera till mappen Enheter i ditt projekt, till exempel

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Välj **Enheter** mapp och tryck/klicka **Enhetshanteraren** i åtgärdsfältet. De tilldelade och ej tilldelade enheterna visas.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Välj en ej tilldelad enhet i listan och tryck/klicka på **Tilldela enhet** i åtgärdsfältet.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Välj den skärm som du vill tilldela enheten till i listan och tryck/klicka på knappen **Tilldela**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Tryck/klicka på **Slutför** för att slutföra tilldelningsprocessen.


   På kontrollpanelen visas den tilldelade enheten i **ENHETER** -panelen.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Klicka på (**...**) i det övre högra hörnet av **ENHETER** för att antingen lägga till enhetskonfiguration eller uppdatera enheterna.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Varje gång den första enheten läggs till i ett nytt skärmsprojekt skapas en användargrupp.
>Om till exempel projektnodens namn är *webbutik* och användargruppnamnet är *screens-we-retail-devices*.
>Den här gruppen läggs till som medlem i **Medarbetare** grupp, enligt bilden nedan:

![chlimage_1-39](assets/chlimage_1-39.png)

### Nästa steg {#the-next-steps}

När du har lärt dig att tilldela en kanal till en skärm kan du läsa det[Övervaka och felsöka](monitoring-screens.md).
