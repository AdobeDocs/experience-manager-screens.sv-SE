---
title: Använda övergångar
seo-title: Använda övergångar
description: Följ den här sidan om du vill lära dig hur du använder övergångar i skärmsprojekt.
seo-description: Följ den här sidan om du vill lära dig hur du använder övergångar i skärmsprojekt.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# Använda övergångar {#applying-transitions}

I det här avsnittet beskrivs hur du kan använda komponenten **Övergång** mellan olika resurser (bilder och videoklipp) och inbäddade sekvenser i en kanal.


>[!CAUTION]
>
>Mer information om egenskaperna för **övergångskomponenten** finns i [Övergångar](adding-components-to-a-channel.md#transition).

## Lägga till övergångskomponent i resurser i en kanal {#adding-transition}

Följ stegen nedan för att lägga till en övergångskomponent i ditt AEM Screens-projekt:

>[!NOTE]
>
>**Förutsättningar**
>
> Skapa ett AEM Screens-projekt **TestProject** med en kanal **TestTransition**. Dessutom kan du ställa in en plats och en visning för att visa utdata.

1. Navigera till **Kanaltestövergång** och klicka på **Redigera** i åtgärdsfältet.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >Kanalen **TestTransition** innehåller redan få resurser (bilder och videor). Kanalen **TestTransition** innehåller till exempel tre bilder och två videoklipp, vilket visas nedan:

   ![image2](assets/transitions2.png)


1. Dra och släpp **övergångskomponenten** i redigeraren.
   >[!CAUTION]
   >
   >Innan du lägger till övergången till dina resurser i din kanal måste du se till att du inte lägger till en övergång före den första resursen i den sekventiella kanalen. Det första objektet i kanalen måste vara en resurs och inte en övergång.

   ![image3](assets/transitions3.png)

   > [!NOTE]
   >
   >Som standard anges egenskaperna för övergångskomponenten, till exempel **Typ** , till **Tona** och **Varaktighet** till *1 600 ms*.  Dessutom är det inte tillrådligt att ange en tidslängd för övergången som är längre än den tillgång den används på.

1. Om du dessutom lägger till en **inbäddad sekvenskomponent** (som innehåller en sekvenskanal) i den här kanalredigeraren kan du lägga till en övergångskomponent i slutet så att innehållet spelas upp i rätt ordning, vilket visas i bilden nedan:

   ![image3](assets/transitions5.png)

