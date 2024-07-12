---
title: Använda övergångar
description: Lär dig använda övergångar i dina AEM Screens-projekt.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Använda övergångar {#applying-transitions}

I det här avsnittet beskrivs hur du kan använda komponenten **Transition** mellan olika resurser (bilder och videoklipp) och inbäddade sekvenser i en kanal.

>[!CAUTION]
>
>Mer information om egenskaperna för komponenten **Transition** finns i [Övergångar](adding-components-to-a-channel.md#transition).

## Lägga till övergångskomponent i Assets i en kanal {#adding-transition}

Följ stegen nedan för att lägga till en övergångskomponent i ditt AEM Screens-projekt:

>[!NOTE]
>
>**Förutsättningar**
>
>Skapa ett AEM Screens-projekt **TestProject** med en kanal **TestTransition**. Du kan även ställa in en plats och en visning för att visa utdata.

1. Navigera till kanalen **TestTransition** och klicka på **Redigera** i åtgärdsfältet.

   ![bild1](assets/transitions1.png)

   >[!NOTE]
   >
   >Kanalen **TestTransition** innehåller redan några resurser (bilder och videor). Kanalen **TestTransition** innehåller till exempel tre bilder och två videoklipp, vilket visas nedan:

   ![bild2](assets/transitions2.png)


1. Dra och släpp komponenten **Transition** till redigeraren.

   >[!CAUTION]
   >
   >Innan du lägger till övergången till dina resurser i din kanal måste du se till att du inte lägger till övergången före den första resursen i den sekventiella kanalen. Det första objektet i kanalen måste vara en resurs och inte en övergång.

   ![bild3](assets/transitions3.png)

   >[!NOTE]
   >
   >Som standard är egenskaperna för övergångskomponenten, till exempel **Type**, inställda på **Tona** och **Varaktighet** inställda på *1600 millisekunder*. Det är inte heller tillrådligt att ange en tidslängd för övergången som är längre än den tillgång den används på.

1. Om du dessutom lägger till en **inbäddad sekvenskomponent** (som innehåller en sekvenskanal) i den här kanalredigeraren kan du lägga till en övergångskomponent i slutet. Om du gör det ser du till att innehållet spelas upp i rätt ordning enligt följande bild:

   ![bild3](assets/transitions5.png)
