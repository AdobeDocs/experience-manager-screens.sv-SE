---
title: Perpetual TakeOver Channel
description: Lär dig skapa en permanent TakeOver-kanal.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Perpetual TakeOver Channel {#perpetual-takeover-channel}

På följande sida visas ett exempel på hur du använder ett projekt för att skapa en permanent TakeOver-kanal som spelas upp en viss dag och tid kontinuerligt.

## Använd fallbeskrivning {#use-case-description}

Det här användningsexemplet förklarar hur du skapar en kanal som *tar över* från den vanliga uppspelningskanalen för en visning eller en grupp med skärmar. Övertagandet sker för en viss dag och tid permanent.
Det finns till exempel en permanent TakeOver-kanal som spelas upp varje fredag från 9:00 till 10:00. Under den här tiden ska ingen annan kanal spelas upp. I följande exempel visas hur man skapar en permanent köpkanal som gör att innehållet kan spelas upp varje onsdag i två timmar mellan kl. 17.00 och 17.00.

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

1. Skapa ett AEM Screens-projekt med namnet **PerpetualTakeOver**, enligt nedan.

   ![resurs](assets/p_usecase1.png)

1. Skapa en **MainAdChannel** i mappen **Channel**.

   ![resurs](assets/p_usecase2.png)

1. Klicka på **MainAdChannel** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp resurser (bilder, videoklipp, inbäddade sekvenser) i kanalen.

   ![resurs](assets/p_usecase3.png)


   >[!NOTE]
   >**MainAdChannel** i det här exemplet demonstrerar en sekvenskanal som spelar upp innehåll kontinuerligt.

1. Skapa en **TakeOver**-kanal som tar över innehållet i **MainAdChannel** och spelar varje onsdag från kl. 2.00 till kl. 17.00.

1. Klicka på **TakeOver** och klicka på **Edit** i åtgärdsfältet. Dra och släpp resurser i kanalen. I följande exempel visas en enzonsbild som lagts till i den här kanalen.

   ![resurs](assets/p_usecase4.png)

1. Konfigurera en plats och visning för kanalerna. Följande plats, **MainLobby** och display **MainLobbyDisplay** , har konfigurerats för det här projektet.

   ![resurs](assets/p_usecase5.png)

**Tilldela kanaler till en skärm**

1. Klicka på visningen **MainLobbyDisplay** i mappen **Locations** . Klicka på **Tilldela kanal** i åtgärdsfältet så att du kan öppna dialogrutan **Kanaltilldelning**.

   >[!NOTE]
   >Mer information om hur du tilldelar en kanal till en visning finns i **[Kanaltilldelning](channel-assignment.md)**.

1. Fyll i fälten (**Kanalsökväg**, **Prioritet** och **Händelser som stöds**) i dialogrutan **Kanaltilldelning** och klicka på **Spara** för att tilldela **MainAdChannel** till visningen.

   * **Kanalsökväg**: Klicka på sökvägen till kanalen **MainAdChannel**
   * **Prioritet**: Ange kanalens prioritet som 1.
   * **Händelser som stöds**: Klicka på **Inledande inläsning** och **Inaktiv skärm**.

   ![resurs](assets/p_usecase6.png)

1. Klicka på visningen **TakeOver** i mappen **Locations** . Klicka på **Tilldela kanal** i åtgärdsfältet så att du kan tilldela övertagandekanalen.

1. Tilldela kanalen **TakeOver** till din skärm vid en schemalagd tidpunkt. Fyll sedan i följande fält från dialogrutan **Kanaltilldelning** och välj **Spara**:

   * **Kanalsökväg**: Klicka på sökvägen till kanalen **TakeOver**
   * **Prioritet**: Ange den här kanalens prioritet som är högre än **MainAdChannel**. Prioriteten i det här exemplet är till exempel 8.
   * **Händelser som stöds**: Klicka på **aktivitetsskärmen** och **tidtagaren**.
   * **Schema**: Ange texten för schemat som du vill att den här kanalen ska köras på skärmen. Texten i **Schedule** som nämns i det här exemplet är *på onsdag efter 14:00 och före 16:00*.

     >[!NOTE]
     >Mer information om de uttryck du kan lägga till i **Schema** finns i avsnittet [Exempeluttryck](#example-expressions) nedan.
   * **aktiv från**: Startdatum och starttid.
   * **aktiv till**: Slutdatum och sluttid.

     Texten i **Schedule** och **active from** and **active until** date and time here gör att innehållet kan spelas upp varje onsdag från kl. 02.00 till kl. 17.00.


     ![resurs](assets/p_usecase7.png)

     Navigera till visningen från **TakeOver** > **Locations** > **MainLobby** > **MainLobbyDisplay** och klicka sedan på **Dashboard** i åtgärdsfältet så att du kan visa de tilldelade kanalerna med deras prioritet, vilket visas nedan.

     >[!NOTE]
     >Det är obligatoriskt att ange övertagskanalens högsta prioritet.

     ![resurs](assets/p_usecase8.png)
Nu tar **TakeOver** -kanalen över **MainAdChannel** kl. 2:00 i två timmar till kl. 17:00 varje onsdag och spelar upp innehållet från 9 januari 2020 till 31 januari 2020.

## Exempeluttryck {#example-expressions}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar en kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| före 08.00 | kanalen spelas upp före 08.00 varje dag |
| efter kl. 2:00. | kanalen spelas upp efter kl. 2.00 varje dag |
| efter 12:15 och före 12:45 | kanalen spelas upp efter 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | Kanalen spelas upp före kl. 12.15 varje dag och sedan även efter kl. 12.45. |
| den första dagen i januari efter kl. 2.00, även den andra dagen i januari samt den tredje dagen i januari före kl. 3.00. | kanalen börjar spelas upp efter kl. 17.00 den 1 januari och fortsätter att spela för hela dagen den 2 januari till kl. 17.00 den 3 januari 2003 |
| 1-2 dagar i januari efter kl. 2:00 också 2-3 dagar i januari före kl. 3:00. | kanalen startar spelaren efter kl. 17.00 den 1 januari, fortsätter att spelas upp till kl. 17.00 den 2 januari 2002, börjar den igen kl. 17.00 och fortsätter att spelas upp till kl. 17.00 den 3 januari 2003 |

>[!NOTE]
>
>Du kan också använda _militär tid_-notation (14:00) i stället för *A.M./P.M.* (2:00 P.M.).
