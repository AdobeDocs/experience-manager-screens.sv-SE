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

Det här Use Case-uttrycket förklarar hur du skapar en kanal som *tar över* från den kanal som spelas upp normalt för en visning eller grupp av skärmar. Övertagandet kommer att ske för en viss dag och tid permanent.
Det finns till exempel en permanent TakeOver-kanal som spelas upp varje fredag från 09:00 till 10:00. Under den här tiden ska ingen annan kanal spelas upp. I följande exempel visas hur man skapar en permanent övertagningskanal som spelas upp så att innehållet kan spelas upp varje onsdag i 2 timmar från kl. 2:00 till kl. 17:00.

### Förhandsvillkor {#preconditions}

Innan du börjar med det här användningsexemplet måste du förstå hur du gör:

* **[Skapa och hantera kanaler](managing-channels.md)**
* **[Skapa och hantera platser](managing-locations.md)**
* **[Skapa och hantera scheman](managing-schedules.md)**
* **[Enhetsregistrering](device-registration.md)**

### Primära skådespelare {#primary-actors}

Innehållsförfattare

## Konfigurera projektet {#setting-up-the-project}

Följ stegen nedan för att konfigurera ett projekt:

**Konfigurera kanaler och visning**

1. Skapa ett AEM Screens-projekt med namnet **PerpetualTakeOver**, enligt nedan.

   ![resurs](assets/p_usecase1.png)

1. Skapa en **MainAdChannel** i mappen **Kanaler**.

   ![resurs](assets/p_usecase2.png)

1. Välj **MainAdChannel** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp resurser (bilder, videoklipp, inbäddade sekvenser) i kanalen.

   ![resurs](assets/p_usecase3.png)


   >[!NOTE]
   >**MainAdChannel** i det här exemplet visar en sekvenskanal som spelar upp innehåll kontinuerligt.

1. Skapa en **TakeOver**-kanal som tar över innehållet i **MainAdChannel** och spelas upp varje onsdag från kl. 2:00 till kl. 23:00.

1. Markera **TakeOver** och klicka på **Edit** i åtgärdsfältet. Dra och släpp resurser i kanalen. I följande exempel visas en enzonsbild som lagts till i den här kanalen.

   ![resurs](assets/p_usecase4.png)

1. Konfigurera en plats och visning för kanalerna. Följande plats **MainLobby** och display **MainLobbyDisplay** har till exempel konfigurerats för det här projektet.

   ![resurs](assets/p_usecase5.png)

**Tilldela kanaler till en visning**

1. Välj visningen **MainLobbyDisplay** i mappen **Platser**. Klicka på **Tilldela kanal** i åtgärdsfältet för att öppna dialogrutan **Kanaltilldelning**.

   >[!NOTE]
   >Mer information om hur du tilldelar en kanal till en visning finns i **[Kanaltilldelning](channel-assignment.md)**.

1. Fyll i fälten (**Kanalsökväg**, **Prioritet** och **Händelser som stöds**) i dialogrutan **Kanaltilldelning** och klicka på **Spara** för att tilldela **MainAdChannel&lt;a1 1/> till din bildskärm.**

   * **Kanalsökväg**: Markera sökvägen till  **** MainAdChannel
   * **Prioritet**: Ange den här kanalens prioritet som 1.
   * **Händelser** som stöds: Välj  **Inledande** inläsning och  **Inaktiv skärm**.

   ![resurs](assets/p_usecase6.png)

1. Markera visningen **TakeOver** i mappen **Platser**. Klicka på **Tilldela kanal** i åtgärdsfältet för att tilldela övertagandekanalen.

1. Så här tilldelar du kanalen **TakeOver** till visningen vid en schemalagd tidpunkt och fyller i följande fält från dialogrutan **Kanaltilldelning** och klickar på **Spara**:

   * **Kanalsökväg**: Markera banan till  **** TakeOverchannel
   * **Prioritet**: Ange prioriteten för den här kanalen som är större än  **MainAdChannel**. Prioriteten i det här exemplet är till exempel 8.
   * **Händelser** som stöds: Välj  **Inaktiv** skärm och  **Timer**.
   * **Schema**: Ange texten för schemat som du vill att den här kanalen ska visa. Texten i **Schedule** som omnämns i det här exemplet är *på onsdagen efter 14:00 och före 16:00*.

      >[!NOTE]
      >Mer information om de uttryck du kan lägga till i **Schedule** finns i avsnittet [Exempeluttryck](#example-expressions) nedan.
   * **aktiv från**: Startdatum och -tid.
   * **aktiv till**: Slutdatum och sluttid.

      Texten i **Schedule** och **aktiv från** och **aktiv till** datum och tid här gör att innehållet kan spelas upp varje onsdag från kl. 2:00 till kl. 17:00.


      ![resurs](assets/p_usecase7.png)

      Navigera till visningen från **TakeOver** —> **Platser** —> **MainLobby** —> **MainLobbyDisplay** och klicka på **Dashboard** i åtgärdsfältet för att visa de tilldelade kanalerna med deras prioriteringar, som visas nedan .

      >[!NOTE]
      >Det är obligatoriskt att ange övertagskanalens högsta prioritet.

      ![](assets/p_usecase8.png)
assetNow, kommer  **** TakeOverchannel att ta över  **** MainAdChannelat 2:00 i två timmar till 17:00 varje onsdag och spela upp innehållet från 9 januari 2020 till 31 januari 2020.

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
>Du kan också använda _militär tid_-notation (d.v.s. 14:00) i stället för *am/pm*-notation (d.v.s. 2:00).
