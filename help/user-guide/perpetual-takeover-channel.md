---
title: Perpetual TakeOver Channel
description: Följ det här användningsexemplet för att skapa en permanent TakeOver-kanal.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Perpetual TakeOver Channel {#perpetual-takeover-channel}

På följande sida visas ett exempel på hur du använder ett projekt för att skapa en permanent TakeOver-kanal som spelas upp en viss dag och tid kontinuerligt.

## Använd fallbeskrivning {#use-case-description}

I det här Use Case-exemplet beskrivs hur du skapar en kanal som *tar över* från den normala uppspelningskanalen för en visning eller grupp av skärmar. Övertagandet sker för en viss dag och tid permanent.
Det finns till exempel en permanent TakeOver-kanal som spelas upp varje fredag från 9:00 till 10:00. Under den här tiden ska ingen annan kanal spelas upp. I följande exempel visas hur man skapar en permanent köpkanal som spelas upp så att innehållet kan spelas upp varje onsdag i två timmar mellan kl. 2:00 och kl. 17:00.

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

**Konfigurera kanaler och visning**

1. Skapa ett AEM Screens-projekt med namnet **PerpetualTakeOver**, vilket visas nedan.

   ![resurs](assets/p_usecase1.png)

1. Skapa en **MainAdChannel** i **Kanaler** mapp.

   ![resurs](assets/p_usecase2.png)

1. Välj **MainAdChannel** och klicka **Redigera** i åtgärdsfältet. Dra och släpp resurser (bilder, videoklipp, inbäddade sekvenser) i kanalen.

   ![resurs](assets/p_usecase3.png)


   >[!NOTE]
   >The **MainAdChannel** i det här exemplet demonstrerar en sekvenskanal som spelar upp innehåll kontinuerligt.

1. Skapa en **TakeOver** kanal som tar över innehållet i **MainAdChannel** och spelar varje onsdag från kl. 02.00 till kl. 17.00.

1. Välj **TakeOver** och klicka **Redigera** i åtgärdsfältet. Dra och släpp resurser i kanalen. I följande exempel visas en enzonsbild som lagts till i den här kanalen.

   ![resurs](assets/p_usecase4.png)

1. Konfigurera en plats och visning för kanalerna. Till exempel följande plats **MainLobby** och visa **MainLobbyDisplay** har konfigurerats för det här projektet.

   ![resurs](assets/p_usecase5.png)

**Tilldela kanaler till en visning**

1. Välj visning **MainLobbyDisplay** från **Platser** mapp. Klicka **Tilldela kanal** i åtgärdsfältet så att du kan öppna **Kanaltilldelning** -dialogrutan.

   >[!NOTE]
   >Mer information om hur du tilldelar en kanal till en skärm finns i **[Kanaltilldelning](channel-assignment.md)**.

1. Fyll i fälten (**Kanalsökväg**, **Prioritet** och **Händelser som stöds**) från **Kanaltilldelning** och klicka **Spara** för att tilldela **MainAdChannel** på skärmen.

   * **Kanalsökväg**: Markera sökvägen till **MainAdChannel** kanal
   * **Prioritet**: Ange den här kanalens prioritet som 1.
   * **Händelser som stöds**: Välj **Inledande inläsning** och **Inaktiv skärm**.

   ![resurs](assets/p_usecase6.png)

1. Välj visning **TakeOver** från **Platser** mapp. Klicka **Tilldela kanal** från åtgärdsfältet så att du kan tilldela övertagandekanalen.

1. Tilldela **TakeOver** kanalen till din skärm vid en schemalagd tidpunkt och fyller i följande fält från **Kanaltilldelning** och klicka **Spara**:

   * **Kanalsökväg**: Markera sökvägen till **TakeOver** kanal
   * **Prioritet**: Ange den här kanalens prioritet som är högre än **MainAdChannel**. Prioriteten i det här exemplet är till exempel 8.
   * **Händelser som stöds**: Välj **Inaktiv skärm** och **Timer**.
   * **Schema**: Ange texten för schemat som du vill att den här kanalen ska köra visningen. Texten i **Schema** som nämns i det här exemplet *på onsdagen efter kl. 14.00 och före kl. 16.00*.

     >[!NOTE]
     >Om du vill veta mer om de uttryck du kan lägga till i **Schema**, se [Exempeluttryck](#example-expressions) nedan.
   * **aktiv från**: Startdatum och -tid.
   * **aktiv tills**: Slutdatum och sluttid.

     Till exempel texten i **Schema** och **aktiv från** och **aktiv tills** datum och tid här gör att innehållet kan spelas upp varje onsdag från kl. 02.00 till kl. 17.00.


     ![resurs](assets/p_usecase7.png)

     Navigera till visningen från **TakeOver** > **Platser** > **MainLobby** > **MainLobbyDisplay** och klicka **Kontrollpanel** i åtgärdsfältet så att du kan visa de tilldelade kanalerna med deras prioriteringar, vilket visas nedan.

     >[!NOTE]
     >Det är obligatoriskt att ange övertagskanalens högsta prioritet.

     ![resurs](assets/p_usecase8.png)
Nu **TakeOver** kanalen tar över **MainAdChannel** kl. 02.00 i två timmar till kl. 17.00 varje onsdag och spelar upp innehållet mellan den 9 januari och den 31 januari 2020.

## Exempeluttryck {#example-expressions}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| före 08.00 | kanalen spelas upp före 08.00 varje dag |
| efter kl. 2:00. | kanalen spelas upp efter kl. 2.00 varje dag |
| efter 12:15 och före 12:45 | kanalen spelas upp efter 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | Kanalen spelas upp före kl. 12.15 varje dag och sedan även efter kl. 12.45. |
| den första dagen i januari efter kl. 2.00, även den andra dagen i januari, den tredje dagen i januari före kl. 17.00. | kanalen börjar spelas upp efter kl. 17.00 den 1 januari och fortsätter hela dagen den 2 januari ända till kl. 17.00 den 3 januari |
| 1-2 dagar i januari efter kl. 2:00 också 2-3 dagar i januari före kl. 3:00 . | kanalen börjar spelas upp efter kl. 17.00 den 1 januari, fortsätter att spelas upp till kl. 17.00 den 2 januari, börjar den igen kl. 2:00 och fortsätter att spela fram till kl. 17.00 den 3 januari |

>[!NOTE]
>
>Du kan också använda _militär tid_ notation (14:00) i stället för *A.M./P.M.* (2:00).
