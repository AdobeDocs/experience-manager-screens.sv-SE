---
title: Perpetual TakeOver Channel
seo-title: Perpetual TakeOver Channel
description: Följ det här användningsexemplet för att skapa en permanent TakeOver-kanal.
seo-description: Följ det här användningsexemplet när du ställer in ett projekt som skapar en permanent TakeOver-kanal som spelas upp en viss tid och dag kontinuerligt.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---


# Perpetual TakeOver Channel {#perpetual-takeover-channel}

På följande sida visas ett exempel på hur du använder ett projekt för att skapa en permanent TakeOver-kanal som spelas upp en viss dag och tid kontinuerligt.

## Använd fallbeskrivning {#use-case-description}

Det här Use Case-alternativet förklarar hur du skapar en kanal som *tar över* från den kanal som spelas upp normalt för en visning eller en grupp av skärmar. Övertagandet kommer att ske för en viss dag och tid permanent.
Det finns till exempel en permanent TakeOver-kanal som spelas upp varje fredag från 09:00 till 10:00. Under den här tiden ska ingen annan kanal spelas upp. I följande exempel visas hur man skapar en permanent övertagningskanal som spelas upp så att innehållet kan spelas upp varje onsdag i 2 timmar från kl. 2:00 till kl. 17:00.

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

1. Skapa ett AEM Screens-projekt med namnet **PerpetualTakeOver** enligt nedan.

   ![resurs](assets/p_usecase1.png)

1. Skapa en **MainAdChannel** i mappen **Channels** .

   ![resurs](assets/p_usecase2.png)

1. Markera **MainAdChannel** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp resurser (bilder, videoklipp, inbäddade sekvenser) i kanalen.

   ![resurs](assets/p_usecase3.png)


   >[!NOTE]
   >I **MainAdChannel** i det här exemplet visas en sekvenskanal som spelar upp innehåll kontinuerligt.

1. Skapa en **TakeOver** -kanal som tar över innehållet i **MainAdChannel** och kan spelas upp varje onsdag från kl. 2:00 till kl. 17:00.

1. Markera **övertaget** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp resurser i kanalen. I följande exempel visas en enzonsbild som lagts till i den här kanalen.

   ![resurs](assets/p_usecase4.png)

1. Konfigurera en plats och visning för kanalerna. Följande plats **MainLobby** och display **MainLobbyDisplay** är till exempel inställd för det här projektet.

   ![resurs](assets/p_usecase5.png)

**Tilldela kanaler till en visning**

1. Välj **MainLobbyDisplay** i mappen **Locations** . Klicka på **Tilldela kanal** i åtgärdsfältet för att öppna dialogrutan **Kanaltilldelning** .

   >[!NOTE]
   >Mer information om hur du tilldelar en kanal till en visning finns i **[Kanaltilldelning](channel-assignment.md)**.

1. Fyll i fälten (**Kanalsökväg**, **Prioritet** och **Händelser** som stöds) i dialogrutan **Kanaltilldelning** och klicka på **Spara** **** för att tilldela¥MainAdChannel¥ till visningen.

   * **Kanalsökväg**: Markera sökvägen till **MainAdChannel** -kanalen
   * **Prioritet**: Ange den här kanalens prioritet som 1.
   * **Händelser** som stöds: Välj **Inledande laddning** och **Inaktiv skärm**.
   ![resurs](assets/p_usecase6.png)

1. Välj **Ta över** i mappen **Platser** . Klicka på **Tilldela kanal** i åtgärdsfältet för att tilldela övertagandekanalen.

1. Om du vill tilldela **TakeOver** -kanalen till din visning vid en schemalagd tidpunkt och fylla i följande fält från dialogrutan **Kanaltilldelning** och klicka på **Spara**:

   * **Kanalsökväg**: Markera banan för **TakeOver** -kanalen
   * **Prioritet**: Ange prioriteten för den här kanalen som är större än **MainAdChannel**. Prioriteten i det här exemplet är till exempel 8.
   * **Händelser** som stöds: Välj **Inaktivitetsskärm** och **Timer**.
   * **Schema**: Ange texten för schemat som du vill att den här kanalen ska visa. Texten i **Schedule** som omnämns i det här exemplet är *på onsdag efter 14:00 och före 16:00*.
      >[!NOTE]
      >Mer information om de uttryck du kan lägga till i **schemat** finns i avsnittet [Exempel på uttryck](#example-expressions) nedan.
   * **aktiv från**: Startdatum och -tid.
   * **aktiv till**: Slutdatum och sluttid.

      Texten i **Schema** och **aktiv från** och **aktiv till** datum och tid här gör att innehållet kan spelas upp varje onsdag från kl. 2:00 till kl. 23:00.


      ![resurs](assets/p_usecase7.png)

      Navigera till visningen från **TakeOver** —> **Locations** —> **MainLobby** —> **MainLobbyDisplay** och klicka på **Dashboard** i åtgärdsfältet för att visa de tilldelade kanalerna med deras prioriteringar, vilket visas nedan.

      >[!NOTE]
      >Det är obligatoriskt att ange övertagskanalens högsta prioritet.

      ![asset](assets/p_usecase8.png)Now, kommer **TakeOver** -kanalen att ta över **MainAdChannel** kl. 17.00 i två timmar till kl. 17.00 varje onsdag och spela upp innehållet från den 9 januari 2020 till den 31 januari 2020.

## Exempeluttryck {#example-expressions}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| före 08:00 | kanalen spelas upp innan klockan åtta varje dag |
| efter klockan 2:00 | kanalen spelas upp efter klockan 17:00 varje dag |
| efter 12:15 och före 12:45 | kanalen spelas upp efter klockan 12:15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | kanalen spelas upp före kl. 12.15 varje dag och även efter kl. 12.45 |
| den första dagen i januari efter kl. 2:00 också den andra dagen i januari, även den tredje dagen i januari före kl. 3:00 | kanalen börjar spelas upp efter kl. 17.00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 17.00 den 3 januari |
| den 1-2 januari efter kl. 2:00 också den 2-3 januari före kl. 3:00 | kanalen startar spelaren efter kl. 17:00 den 1 januari, fortsätter att spelas upp till kl. 17:00 den 2 januari och börjar igen kl. 2:00 och fortsätter att spelas upp till kl. 3:00 den 3 januari |

>[!NOTE]
>
>Du kan också använda _militär_ tidsnotation (d.v.s. 14:00) i stället för *AM/pm* -notation (d.v.s. 2:00).
