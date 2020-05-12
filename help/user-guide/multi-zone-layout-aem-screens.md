---
title: Layout med flera zoner
seo-title: Layout med flera zoner
description: Med layout med flera zoner kan du skapa innehåll med flera zoner och använda olika resurser, till exempel videoklipp, bilder och text som kan kombineras på en enda skärm. Följ den här sidan om du vill veta mer.
seo-description: Med layout med flera zoner kan du skapa innehåll med flera zoner och använda olika resurser, till exempel videoklipp, bilder och text som kan kombineras på en enda skärm. Följ den här sidan om du vill veta mer.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: ae05d169dce9d02562159524f9bf43e88a29e43f
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 1%

---


# Layout med flera zoner {#multi-zone-layout}

På följande sida beskrivs användningen av layout med flera zoner och följande avsnitt beskrivs:

* Översikt
* Skapa layout med flera zoner
* Förutsättningar
* Använda enskilda resurser i en eller flera zoner
* Använda sekvensinnehåll i en eller flera zoner

## Översikt {#overview}

***Med layout*** med flera zoner kan du skapa innehåll med flera zoner och använda olika resurser som videor, bilder och text som kan kombineras på en enda skärm. Du kan lägga in bilder, videor och text som gör att allt kan smälta samman och skapa en intuitiv digital upplevelse.

Enligt projektkraven behöver du ibland flera zoner i en kanal och kan redigera dem som en enda heltäckande enhet. Till exempel en produktsekvens med en relaterad feed för sociala medier som körs i tre separata zoner på en enda kanal.

## Skapa layout med flera zoner {#creating-multi-zone-layout}

När du skapar en kanal kan du använda olika mallar för att skapa zoner i kanalen. Du kan lägga till en bild, video eller en inbäddad kanal som gör att flera resurser kan visas i en sekvens.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen måste du se till att du har ett projekt redo som en förutsättning för att kunna börja implementera flerzonslayout. Till exempel,

* Skapa ett AEM Screens-projekt med namnet **Zones**
* Skapa en visning under **Platser** med namnet **MultiZoneDisplay**.

Skapa en kanal med namnet **MultiZone** i **Zones** -projekt. Följ stegen nedan:

**Skapa kanalen**

1. Markera Adobe Experience Manager-länken (överst till vänster) och sedan **Skärmar**. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.
1. Navigera till mappen **Kanaler** och klicka på **Skapa** i åtgärdsfältet.

1. Välj **1x2 Delad skärmkanal** i guiden **Skapa** .

1. Klicka på **Nästa** och ange **titeln** som **MultiZone**.

1. Klicka på **Skapa** för att slutföra kanalskapandet.

### Använda enskilda resurser i en eller flera zoner {#using-single-assets-in-one-or-more-zones}

Du kan använda enstaka resurser som en bild eller en video i alla tre olika zoner. Följ stegen nedan för implementering:

1. **Lägga till innehåll i kanalen**

   1. Navigera till **Zones** —> **Channels**—>**MultiZone**.
   1. Markera **MultiZone** -kanalen och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.

1. **Lägga till bilder i kanalen**

   Om du vill spela upp en enstaka bild eller en video i två zoner drar och släpper du bara en bild till varje zon i kanalredigeraren enligt bilden nedan:

   MultiZone-img3

   ![image](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Använda sekvensinnehåll i en eller flera zoner {#using-sequenced-content-in-one-or-more-zones}

Om du vill att zonerna ska visa sekvenser av bilder eller innehåll och en statisk bild i två olika zoner följer du stegen nedan för mer information.

1. **Skapa en kanalmapp**

   1. Navigera till **Zones** —> **MultiZone** —> **Channels** och klicka på **Create** i åtgärdsfältet.
   1. Välj **Kanalmapp** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange titeln som **EmbeddedChannels** och klicka på **Create**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Lägga till ytterligare två kanaler i kanalmappen**

   1. Navigera till **Zones** —> **Channels** —> **EmbeddedChannels** och klicka på **Create** i åtgärdsfältet.
   1. Välj **Sekvenskanal** i guiden **Skapa** för att skapa en kanal med namnet **Zon1**.
   1. Välj **Zon1** och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.
   1. Dra och släpp några bilder i den här kanalen.
   Skapa på samma sätt en annan sekvenskanal med namnet **Zone2** i mappen **EmbeddedChannels** .

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Bilderna som läggs till i redigeraren för **Zone1** -sekvenskanalen visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Den video som lagts till i redigeraren för **Zone2** -sekvenskanalen visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Lägga till inbäddade sekvenser (komponent) i huvudkanalen (MultiZone)**

   1. Navigera till **Zones** —> **Channels** —> **MultiZone**.
   1. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.
   1. Dra och släpp den **inbäddade sekvenskomponenten** till två av zonerna.

1. **Lägg till innehåll i alla tre zoner**

   1. Navigera till **Zones** —> **Channels** —> **MultiZone**.
   1. Markera den inbäddade sekvensen i någon av zonerna.
   1. Klicka på ikonen **Konfigurera** (skiftnyckel) för en av de inbäddade sekvenserna i redigeraren.
   1. Välj kanalsökvägen som **Zones** —> **Channels** —> **EmbeddedChannels** —> **Zone1**, vilket visas i bilden nedan.
   Lägg på samma sätt till **Zone2** i en annan inbäddad sekvenskomponent i redigeraren.

   ![image](/help/user-guide/assets/multi-zone/multizone-3.png)

### Skapa plats och visning {#creating-location}

Du måste skapa en plats och en visning för att kunna visa innehållet i skärmspelaren. Följ stegen nedan för att skapa en plats och en visning.

1. **Skapa en plats**

   1. Navigera till mappen **Zones** —> **Locations** .
   1. Markera mappen **Platser** och klicka på **Skapa** i åtgärdsfältet.
   1. Välj **Plats** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange **Title** som **SanJose** och klicka på **Create**.

1. **Skapa en bildskärm**

   1. Navigera till mappen **Zones** —> **Locations** .
   1. Välj **platsen SanJose** och klicka på **Skapa** i åtgärdsfältet.
   1. Välj **Visning** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange **Titel** som **ikon** och klicka på **Skapa**.

### Tilldela kanal till skärmen {#channel-channel}

Du måste tilldela kanalerna till visningen för att kunna visa innehållet. Följ stegen nedan för att tilldela kanalen till visningen.

1. **Tilldela kanal till skärmen**

   1. Navigera till **Zones** —> **Locations** —> **SanJose**—> **Lobby**.
   1. Välj **Lobby** -visningen och klicka på **Tilldela kanal** i åtgärdsfältet.
   1. Ange sökvägen till **MultiZone** -kanalen i **kanalsökvägen**.
   1. Ange **händelser** som stöds som **Inledande inläsning**, **Inaktiv skärm** och **Timer**.
   1. Click **Save**.

      ![image](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. På samma sätt måste du tilldela de två andra inbäddade kanalerna (**Zone1** och **Zone2**) till den här visningen med hjälp av steg 2.
   1. När du har tilldelat alla tre kanalerna till **Lobby** -visningen bör du kunna visa de tilldelade kanalerna från kontrollpanelen.

      ![image](/help/user-guide/assets/multi-zone/multizone-img8.png)
   >[!Iviktig]
   > När du har tilldelat huvudkanalen (i det här fallet **MultiZone**) till visningen är det obligatoriskt att tilldela de två andra inbäddade kanalerna **Zone1** och **Zone2** till samma skärm.

### Registrerar enheten {#registering-device}

När du har konfigurerat en plats och en skärm följer du stegen nedan för att registrera enheten och tilldela skärmen till enheten.

1. **Registrerar enheten**

   1. Navigera till mappen **Zones** —> **Devices** .
   1. Välj mappen **Enheter** och klicka på **Enhetshanteraren** i åtgärdsfältet.
   1. Klicka på **Enhetsregistrering** och välj den väntande enheten i listan.
      >[!NOTE]
      > Enhetens titel måste matcha enhetstoken (**tokenfältet** ) som visas på fliken **Device Registration** .
   1. Om titeln matchar enhetstoken väljer du enheten och klickar på **Registrera enhet** i åtgärdsfältet.
   1. Om registreringskoden matchar koden på registreringsfliken för skärmspelaren klickar du på **Validera** i åtgärdsfältet.
      ![image](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Ange **titeln** som **Chrome-Device1** och klicka på **Register**.
   1. Välj **Tilldela visning** och välj sökvägen till enhetskonfigurationen.

#### Visa resultatet {#viewing-the-result}

När du har implementerat layouter med flera zoner med de föregående stegen visas följande utdata, vilket visas i bilden nedan.

Markera Skärmspelaren för att visa utdata som visar innehållet i två olika zoner. Vänster- och högerzonerna (båda använder inbäddad sekvens som en komponent).

>[!NOTE]
>Om du försöker visa innehållet i skärmspelaren ska du klicka på **Uppdatera offlineinnehåll** på kanalkontrollpanelen.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


