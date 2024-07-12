---
title: Ta över kanal för engångsbruk
description: Följ det här användningsexemplet när du vill skapa en engångskanal för övertagande.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Ta över kanal för engångsbruk {#single-use-takeover-channel}

På följande sida visas ett exempel på hur du använder ett projekt för att skapa en Single TakeOver-kanal som spelas upp en gång för en viss tid.

## Använd fallbeskrivning {#use-case-description}

Det här användningsexemplet förklarar hur du skapar en kanal som *tar över* från den vanliga uppspelningskanalen för en visning eller en grupp med skärmar. Övertagandet sker endast en gång och för en viss tid.

Det finns till exempel en Single TakeOver-kanal som spelas upp fredag 9:00 till 10:00. Under den här tiden ska ingen annan kanal spelas upp. Före och efter den här gången spelas kanalen för engångsbruk inte upp. I följande exempel visas hur en enda köpkanal skapas som gör att innehållet kan spelas upp i 2 minuter före 12:00 den 31 december till 12:01.

### Förhandsvillkor {#preconditions}

Innan du börjar med det här användningsexemplet måste du förstå hur du gör:

* **[Skapa och hantera kanaler](managing-channels.md)**
* **[Skapa och hantera platser](managing-locations.md)**
* **[Skapa och hantera scheman](managing-schedules.md)**
* **[Enhetsregistrering](device-registration.md)**

### Primära aktörer {#primary-actors}

Innehållsförfattare

## Konfigurera projektet {#setting-up-the-project}

Följ stegen nedan för att konfigurera ett projekt:

**Konfigurera kanalerna och visningen**

1. Skapa ett AEM Screens-projekt med namnet **SingleUseTakeOver**, enligt nedan.

   ![resurs](assets/single-takeover1.png)

1. Skapa en **MainAdChannel** i mappen **Channel**.

   ![resurs](assets/single-takeover2.png)

1. Klicka på **MainAdChannel** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp resurser (bilder, videoklipp, inbäddade sekvenser) i kanalen.

   ![resurs](assets/single-takeover2.png)


   >[!NOTE]
   >**MainAdChannel** i det här exemplet demonstrerar en sekvenskanal som spelar upp innehåll kontinuerligt.

   ![resurs](assets/single-takeover3.png)

1. Skapa en **TakeOver**-kanal som tar över innehållet i **MainAdChannel** och endast spelas upp för en viss dag och tid.

1. Klicka på **TakeOver** och klicka på **Edit** i åtgärdsfältet. Dra och släpp resurser i kanalen. I följande exempel visas en enzonsbild som lagts till i den här kanalen.

   ![resurs](assets/single-takeover4.png)

1. Konfigurera en plats och visning för kanalerna. Till exempel har följande **Lobby**-plats och **MainLobbyDisplay**-visning konfigurerats för det här projektet.

   ![resurs](assets/single-takeover5.png)

**Tilldela kanaler till en skärm**

1. Klicka på visningen **MainLobbyDisplay** i mappen **Locations** . Klicka på **Tilldela kanal** i åtgärdsfältet.

   ![resurs](assets/single-takeover6.png)

   >[!NOTE]
   >Mer information om hur du tilldelar en kanal till en visning finns i **[Kanaltilldelning](channel-assignment.md)**.

1. Fyll i fälten (**Kanalsökväg**, **Prioritet** och **Händelser som stöds**) i dialogrutan **Kanaltilldelning** och klicka på **Spara**. Du har nu tilldelat **MainAdChannel** till din visning.

   ![resurs](assets/single-takeover7.png)

1. Klicka på visningen **TakeOver** i mappen **Locations** . Klicka på **Tilldela kanal** i åtgärdsfältet så att du kan tilldela en överköpskanal för engångsbruk.

1. Tilldela kanalen **TakeOver** till din skärm vid en schemalagd tidpunkt och fyll i följande fält från dialogrutan **Kanaltilldelning** och klicka på **Spara**:

   * **Kanalsökväg**: Klicka på sökvägen till TakeOver-kanalen
   * **Prioritet**: Ange den här kanalens prioritet som är högre än **MainAdChannel**. Prioriteten i det här exemplet är till exempel 8.

     >[!NOTE]
     >Prioriteten kan vara vilket värde som helst som är högre än prioritetsvärdet för den normala uppspelningskanalen.
   * **Händelser som stöds**: Klicka på **aktivitetsskärmen** och **tidtagaren**.
   * **Schema**: Ange texten för schemat som du vill att den här kanalen ska köras på skärmen. Texten här tillåter till exempel att innehållet spelas upp 2 minuter före 12:00 den 31 december till 12:01.
Texten i **Schedule** som nämns i det här exemplet är *den 31 december efter 23:58 och även den 1 januari före 00.01*.

     ![resurs](assets/single-takeover8.png)

     Navigera till visningen från **SingleUseTakeOver** > **Locations** > **Lobby** > **MainLobbyDisplay**. Klicka på **Instrumentpanel** i åtgärdsfältet så att du kan visa de tilldelade kanalerna med deras prioriteringar, vilket visas nedan.

     >[!NOTE]
     >Det är obligatoriskt att ange övertagskanalens högsta prioritet.

     ![resurs](assets/single-takeover9.png)

>[!NOTE]
>
>Det är bäst att ta bort kanalen för enskild användning när den spelas upp.
