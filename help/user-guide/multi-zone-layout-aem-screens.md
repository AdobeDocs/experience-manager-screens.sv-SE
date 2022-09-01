---
title: Layout med flera zoner
seo-title: Multi-zone Layout
description: Med layout med flera zoner kan du skapa innehåll med flera zoner och använda olika resurser, som videoklipp, bilder och text som kan kombineras på en enda skärm. Följ den här sidan om du vill veta mer.
seo-description: Multi-zone Layout allows you to create multiple zone content and use a variety of assets such as videos, images and text that can be combined in a single screen. Follow this page to learn more.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 0%

---

# Layout med flera zoner {#multi-zone-layout}

På följande sida beskrivs användningen av layout med flera zoner och följande avsnitt beskrivs:

* Översikt
* Skapa layout med flera zoner
* Förutsättningar
* Använda enskilda resurser i en eller flera zoner
* Använda sekvensinnehåll i en eller flera zoner

## Översikt {#overview}

***Layout med flera zoner*** I kan du skapa innehåll med flera zoner och använda olika resurser som videoklipp, bilder och text som kan kombineras på en enda skärm. Du kan lägga in bilder, videor och text som gör att allt kan smälta samman och skapa en intuitiv digital upplevelse.

Enligt projektkraven behöver du ibland flera zoner i en kanal och kan redigera dem som en enda heltäckande enhet. Till exempel en produktsekvens med en relaterad feed för sociala medier som körs i tre separata zoner på en enda kanal.


### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har de konceptuella kunskaperna om:

* [Skapa ett AEM Screens-projekt](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Skapa en bildskärm](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Tilldela en kanal till en skärm](/help/user-guide/channel-assignment.md)

## Skapa layout med flera zoner {#creating-multi-zone-layout}

När du skapar en kanal kan du använda olika mallar för att skapa zoner i kanalen. Du kan lägga till en bild, video eller en inbäddad kanal som gör att flera resurser kan visas i en sekvens.

**Skapa en kanal**

1. Klicka på länken Adobe Experience Manager (överst till vänster) och sedan **Skärmar**. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.
1. Navigera till **Kanaler** mapp och klicka på **Skapa** i åtgärdsfältet.

1. Välj **1x2 Delad skärmkanal** från **Skapa** guide.

1. Klicka **Nästa** och anger **title** as **MultiZone**.

1. Klicka **Skapa** för att slutföra kanalskapandet.

### Använda enskilda resurser i en eller flera zoner {#using-single-assets-in-one-or-more-zones}

Du kan använda enstaka resurser som en bild eller en video i alla enskilda zoner. Följ stegen nedan för implementering:

1. **Lägga till innehåll i kanalen**

   1. Navigera till **Zoner** —> **Kanaler**—> **MultiZone**.
   1. Välj **MultiZone** kanal och klicka **Redigera** i åtgärdsfältet för att öppna redigeraren.

1. **Lägga till bilder i kanalen**

   Om du vill spela upp en enstaka bild eller en video i två zoner drar och släpper du bara en bild till varje zon i kanalredigeraren enligt bilden nedan:

   ![bild](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Använda sekvensinnehåll i en eller flera zoner {#using-sequenced-content-in-one-or-more-zones}

Om du vill att zonerna ska visa bildsekvenser och en video i olika zoner följer du stegen nedan för mer information.

1. **Skapa en kanalmapp**

   1. Navigera till **Zoner** —> **MultiZone** —> **Kanaler** och klicka **Skapa** i åtgärdsfältet.
   1. Välj **Mappen Kanaler** från **Skapa** guide och klicka **Nästa**.
   1. Ange titeln som **InbäddadeKanaler** och klicka **Skapa**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Lägga till ytterligare två kanaler i kanalmappen**

   1. Navigera till **Zoner** —> **Kanaler** —> **InbäddadeKanaler** och klicka **Skapa** i åtgärdsfältet.
   1. Välj **Sekvenskanal** från **Skapa** guide för att skapa en kanal med namnet **Zon1**.
   1. Välj **Zon1** och klicka **Redigera** i åtgärdsfältet för att öppna redigeraren.
   1. Dra och släpp några bilder i den här kanalen.
   1. Skapa en annan sekvenskanal med namnet som **Zon2** in **InbäddadeKanaler** mapp.
   1. Dra och släpp en video i den här kanalen.

   I följande bild visas kanalerna **Zon1** och **Zon2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Bilderna som lagts till i redigeraren av **Zon1** sekvenskanal visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Videon har lagts till i redigeraren av **Zon2** sekvenskanal visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Lägga till inbäddade sekvenser (komponent) i huvudkanalen (MultiZone)**

   1. Navigera till **Zoner** —> **Kanaler** —> **MultiZone**.
   1. Klicka **Redigera** i åtgärdsfältet för att öppna redigeraren.
   1. Dra och släpp **Inbäddad sekvens** till båda zonerna.
   1. Markera den inbäddade sekvensen i någon av zonerna.
   1. Klicka på **Konfigurera** (skiftnyckel) till en av de inbäddade sekvenserna i redigeraren.
   1. Markera kanalbanan som **Zoner** —> **Kanaler** —> **InbäddadeKanaler** —> **Zon1**, vilket visas i figuren nedan.
   1. Lägg på samma sätt till **Zon2** till en annan inbäddad sekvenskomponent i redigeraren.

      ![bild](/help/user-guide/assets/multi-zone/multizone-3.png)

### Skapa en plats och en visning {#creating-location}

Skapa en plats och en visning för att visa innehållet i skärmspelaren.

1. **Skapa en plats**

   1. Navigera till **Zoner** —> **Platser** mapp.
   1. Välj **Platser** mapp och klicka på **Skapa** i åtgärdsfältet.
   1. Välj **Plats** från **Skapa** guide och klicka **Nästa**.
   1. Ange **Titel** as **SanJose** och klicka **Skapa**.

1. **Skapa en bildskärm**

   1. Navigera till **Zoner** —> **Platser** mapp.
   1. Välj **SanJose** plats och klicka på **Skapa** i åtgärdsfältet.
   1. Välj **Visa** från **Skapa** guide och klicka **Nästa**.
   1. Ange **Titel** as **Lobby** och klicka **Skapa**.

### Tilldela kanaler till visningen {#channel-channel}

Tilldela kanalerna till visningen för att visa innehållet. Följ stegen nedan för att tilldela kanalen till visningen.

1. **Tilldela kanal till skärmen**

   1. Navigera till **Zoner** —> **Platser** —> **SanJose**—> **Lobby**.
   1. Välj **Lobby** visa och klicka **Tilldela kanal** i åtgärdsfältet.
   1. Ange sökvägen till **MultiZone** kanal in **Kanalsökväg**.
   1. Ange **Händelser som stöds** as **Inledande inläsning**, **Inaktiv skärm** och **Timer**.
   1. Klicka **Spara**.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. På samma sätt måste du tilldela de andra två inbäddade kanalerna (**Zon1** och **Zon2**) till denna skärm.
   1. När du har tilldelat alla tre kanalerna **Lobby** ska du kunna visa de tilldelade kanalerna från kontrollpanelen.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > När du har tilldelat huvudkanalen (i det här fallet **MultiZone**) till skärmen är det obligatoriskt att tilldela de andra två inbäddade kanalerna **Zon1** och **Zon2** till samma skärm.

### Registrerar enheten {#registering-device}

När du har konfigurerat en plats och en skärm följer du stegen nedan för att registrera enheten och tilldela skärmen till enheten.

1. **Registrerar enheten**

   1. Navigera till **Zoner** —> **Enheter** mapp.
   1. Välj **Enheter** mapp och klicka på **Enhetshanteraren** i åtgärdsfältet.
   1. Klicka **Enhetsregistrering** och välj den väntande enheten i listan.

      >[!NOTE]
      > Enhetens titel måste matcha enhetstoken (**Token** fält) som visas i **Enhetsregistrering** -fliken.
   1. Om titeln matchar enhetstoken väljer du enheten och klickar på **Registrera enhet** i åtgärdsfältet.
   1. Om registreringskoden matchar koden i skärmspelaren **Enhetsregistrering** flik, klicka **Validera** i åtgärdsfältet.
      ![bild](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Ange **Titel** as **Chrome-Device1** och klicka **Registrera**.
   1. Välj **Tilldela visning** och välj sökvägen till enhetskonfigurationen.

   >[!NOTE]
   >Om du försöker visa innehållet i skärmspelaren ska du klicka **Uppdatera offlineinnehåll** från kanalkontrollpanelen för var och en av de kanaler som är tilldelade visningen.

### Visa resultatet {#viewing-the-result}

När du har implementerat layouter med flera zoner i de föregående stegen visas följande utdata.

Markera Skärmspelaren för att visa utdata som visar innehållet i två olika zoner. I den vänstra och högra zonen (båda används en inbäddad sekvens som en komponent).

Den vänstra zonen är en sekvenskanal och den högra zonen innehåller en video.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
