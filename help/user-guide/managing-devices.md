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
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 5%

---

# Hantera enheter {#managing-devices}

Den här sidan beskriver enhetstilldelningen.

Med enhetskonsolen kan du komma åt enhetshanteraren och tilldela enheten till en skärm.

>[!CAUTION]
>
>Registrera enheten innan du tilldelar den. Se [Enhetsregistrering](device-registration.md).

## Enhetstilldelning {#device-assignment}

Följ stegen nedan för att tilldela en enhet till en skärm:

1. Navigera till mappen Enheter i ditt projekt, till exempel

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Klicka på mappen **Enheter** och klicka på **Enhetshanteraren** i åtgärdsfältet. De tilldelade och ej tilldelade enheterna visas.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Klicka på en ej tilldelad enhet i listan och klicka sedan på **Tilldela enhet** i åtgärdsfältet.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Klicka på den skärm som du vill tilldela enheten till i listan och klicka på **Tilldela**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Klicka på **Slutför** för att slutföra tilldelningsprocessen.


   På kontrollpanelen visas den tilldelade enheten på panelen **ENHETER**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Klicka på (**..**) i det övre högra hörnet av panelen **DEVICES** för att antingen lägga till enhetskonfiguration eller uppdatera enheterna.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Varje gång den första enheten läggs till i ett nytt Screens-projekt skapas en användargrupp.
>>Om till exempel projektnodens namn är *we-retail* är användargruppens namn *screens-we-retail-devices*.
>>Den här gruppen läggs till som medlem i gruppen **Medarbetare** enligt bilden nedan:

![chlimage_1-39](assets/chlimage_1-39.png)

### Nästa steg {#the-next-steps}

När du känner till hur du tilldelar kanal till en skärm kan du läsa [Övervaka och felsöka](monitoring-screens.md).
