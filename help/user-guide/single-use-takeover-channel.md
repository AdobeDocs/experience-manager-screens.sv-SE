---
title: Ta över kanal för engångsbruk
seo-title: Ta över kanal för engångsbruk
description: Följ det här användningsexemplet när du vill skapa en överföringskanal.
seo-description: Följ det här användningsexemplet när du vill skapa en överföringskanal.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# Ta över kanal för engångsbruk {#single-use-takeover-channel}

På följande sida visas ett exempel på hur du använder ett projekt för att skapa en Single TakeOver-kanal som bara spelas upp en gång för en viss tid.


## Använd fallbeskrivning {#use-case-description}

Det här Use Case-alternativet förklarar hur du skapar en kanal som *tar över* från den kanal som spelas upp normalt för en visning eller en grupp av skärmar. Övertagandet sker endast en gång och för en viss tid.
Det finns till exempel en Single TakeOver-kanal som spelas upp på fredag från 09:00 till 10:00. Under den här tiden ska ingen annan kanal spelas upp. Före och efter denna tidpunkt kommer kanalen för engångsbruk inte att spelas upp. I följande exempel visas hur man skapar en enda köpkanal som spelas upp så att innehållet kan spelas upp i 2 minuter före klockan 12.00 på 31 dec till kl. 12.01.

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

1. Skapa ett AEM Screens-projekt med namnet **SingleUseTakeOver** enligt nedan.

   ![resurs](assets/single-takeover1.png)

1. Skapa en **MainAdChannel** i mappen **Channels** .

   ![resurs](assets/single-takeover2.png)

1. Markera **MainAdChannel** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp resurser (bilder, videoklipp, inbäddade sekvenser) i kanalen.

   ![resurs](assets/single-takeover2.png)


   >[!NOTE]
   >I **MainAdChannel** i det här exemplet visas en sekvenskanal som spelar upp innehåll kontinuerligt.

   ![resurs](assets/single-takeover3.png)

1. Skapa en **TakeOver** -kanal som tar över innehållet i **MainAdChannel** och endast spelar upp en viss dag och tid.

1. Markera **övertaget** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp resurser i kanalen. I följande exempel visas en enzonsbild som lagts till i den här kanalen.

   ![resurs](assets/single-takeover4.png)

1. Konfigurera en plats och visning för kanalerna. Följande plats **Lobby** och display **MainLobbyDisplay** är till exempel inställd för det här projektet.

   ![resurs](assets/single-takeover5.png)

**Tilldela kanaler till en visning**

1. Välj **MainLobbyDisplay** i mappen **Locations** . Klicka på **Tilldela kanal** i åtgärdsfältet.

   ![resurs](assets/single-takeover6.png)

   >[!NOTE]
   >Mer information om hur du tilldelar en kanal till en visning finns i **[Kanaltilldelning](channel-assignment.md)**.

1. Fyll i fälten (**Kanalsökväg**, **Prioritet** och **Händelser** som stöds) i dialogrutan **Kanaltilldelning** och klicka på **Spara**. Du har nu tilldelat **MainAdChannel** till din skärm.

   ![resurs](assets/single-takeover7.png)

1. Välj **Ta över** i mappen **Platser** . Klicka på **Tilldela kanal** i åtgärdsfältet för att tilldela övertagningskanalen för engångsbruk.

1. Om du vill tilldela **TakeOver** -kanalen till din visning vid en schemalagd tidpunkt och fylla i följande fält från dialogrutan **Kanaltilldelning** och klicka på **Spara**:

   * **Kanalsökväg**: Markera banan för TakeOver-kanalen
   * **Prioritet**: Ange prioriteten för den här kanalen som är större än **MainAdChannel**. Prioriteten i det här exemplet är till exempel 8.
      >[!NOTE]
      >Prioriteten kan vara vilket värde som helst som är högre än prioritetsvärdet för den kanal som spelas upp normalt.
   * **Händelser** som stöds: Välj **Inaktivitetsskärm** och **Timer**.
   * **Schema**: Ange texten för schemat som du vill att den här kanalen ska visa. Texten här tillåter till exempel att innehållet spelas upp 2 minuter före 01:00 på 31 dec till kl. 12:01.
Texten i **Schedule** som nämns i det här exemplet är *den 31 december efter 23:58 och även den 1 januari före 00.01*.

      ![resurs](assets/single-takeover8.png)

      Navigera till visningen från **SingleUseTakeOver** —> **Locations** —> **Lobby** —> **MainLobbyDisplay** och klicka på **Dashboard** i åtgärdsfältet för att visa de tilldelade kanalerna med deras prioriteringar, vilket visas nedan.

      >[!NOTE]
      >Det är obligatoriskt att ange övertagskanalens högsta prioritet.

      ![resurs](assets/single-takeover9.png)

>[!NOTE]
>
>Det är bäst att ta bort kanalen för enskild användning när den spelas upp.