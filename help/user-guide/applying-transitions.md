---
title: Använda övergångar
description: Lär dig använda övergångar i dina AEM Screens-projekt.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: 97084aee861e152abcc5f117a2a4759dced038cc
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Använda övergångar {#applying-transitions}

I det här avsnittet beskrivs hur du kan använda **Övergång** mellan olika resurser (bilder och videor) och inbäddade sekvenser i en kanal.

>[!CAUTION]
>
>Mer information om egenskaperna för **Övergång** -komponent, se [Övergångar](adding-components-to-a-channel.md#transition).

## Lägga till övergångskomponent i resurser i en kanal {#adding-transition}

Följ stegen nedan för att lägga till en övergångskomponent i ditt AEM Screens-projekt:

>[!NOTE]
>
>**Förutsättningar**
>
>Skapa ett AEM Screens-projekt **TestProject** med en kanal **TestTransition**. Du kan även ställa in en plats och en visning för att visa utdata.

1. Navigera till kanalen **TestTransition** och klicka **Redigera** i åtgärdsfältet.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >The **TestTransition** kanalen innehåller redan få resurser (bilder och videor). Till exempel **TestTransition** Kanalen innehåller tre bilder och två videoklipp, vilket visas nedan:

   ![image2](assets/transitions2.png)


1. Dra och släpp **Övergång** till redigeraren.

   >[!CAUTION]
   >
   >Innan du lägger till övergången till dina resurser i din kanal måste du se till att du inte lägger till en övergång före den första resursen i den sekventiella kanalen. Det första objektet i kanalen måste vara en resurs och inte en övergång.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >Som standard är övergångskomponentens egenskaper, som **Typ** är inställd på **Tona** och **Varaktighet** är inställd på *1 600 millisekunder*. Det är inte heller tillrådligt att ange en tidslängd för övergången som är längre än den tillgång den används på.

1. Om du lägger till en **Inbäddad sekvens** -komponenten (som inkluderar en sekvenskanal) i den här kanalredigeraren kan du lägga till en övergångskomponent i slutet. Detta garanterar att innehållet spelas upp i rätt ordning, vilket visas i följande bild:

   ![image3](assets/transitions5.png)
