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
feature: Redigeringsskärmar
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1199'
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

***Med*** layouter med flera zoner kan du skapa innehåll med flera zoner och använda olika resurser som videoklipp, bilder och text som kan kombineras på en enda skärm. Du kan lägga in bilder, videor och text som gör att allt kan smälta samman och skapa en intuitiv digital upplevelse.

Enligt projektkraven behöver du ibland flera zoner i en kanal och kan redigera dem som en enda heltäckande enhet. Till exempel en produktsekvens med en relaterad feed för sociala medier som körs i tre separata zoner på en enda kanal.


### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har de konceptuella kunskaperna om:

* [Skapa ett AEM Screens-projekt](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Skapa en bildskärm](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Tilldela en kanal till en skärm](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## Skapa layout med flera zoner {#creating-multi-zone-layout}

När du skapar en kanal kan du använda olika mallar för att skapa zoner i kanalen. Du kan lägga till en bild, video eller en inbäddad kanal som gör att flera resurser kan visas i en sekvens.

**Skapa en kanal**

1. Markera länken Adobe Experience Manager (överst till vänster) och **Skärmar**. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.
1. Navigera till mappen **Kanaler** och klicka på **Skapa** i åtgärdsfältet.

1. Välj **1x2 Delad skärmkanal** i guiden **Skapa**.

1. Klicka på **Nästa** och ange **titeln** som **MultiZone**.

1. Klicka på **Skapa** för att slutföra skapandet av kanalen.

### Använda enskilda resurser i en eller flera zoner {#using-single-assets-in-one-or-more-zones}

Du kan använda enstaka resurser som en bild eller en video i alla enskilda zoner. Följ stegen nedan för implementering:

1. **Lägga till innehåll i kanalen**

   1. Navigera till **Zones** —> **Kanaler**—> **MultiZone**.
   1. Markera kanalen **MultiZone** och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.

1. **Lägga till bilder i kanalen**

   Om du vill spela upp en enstaka bild eller en video i två zoner drar och släpper du bara en bild till varje zon i kanalredigeraren enligt bilden nedan:

   ![bild](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Använda sekvensinnehåll i en eller flera zoner {#using-sequenced-content-in-one-or-more-zones}

Om du vill att zonerna ska visa bildsekvenser och en video i olika zoner följer du stegen nedan för mer information.

1. **Skapa en kanalmapp**

   1. Navigera till **Zones** —> **MultiZone** —> **Kanaler** och klicka på **Skapa** från åtgärdsfältet.
   1. Välj **Kanalmapp** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange titeln som **EmbeddedChannels** och klicka på **Create**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Lägga till ytterligare två kanaler i kanalmappen**

   1. Navigera till **Zones** —> **Kanaler** —> **Inbäddade kanaler** och klicka på **Skapa** från åtgärdsfältet.
   1. Välj **Sekvenskanal** i guiden **Skapa** om du vill skapa en kanal med namnet **Zone1**.
   1. Välj **Zone1** och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.
   1. Dra och släpp några bilder i den här kanalen.
   1. Skapa på samma sätt en annan sekvenskanal med namnet **Zone2** i mappen **EmbeddedChannels**.
   1. Dra och släpp en video i den här kanalen.

   I följande bild visas kanalerna **Zone1** och **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Bilderna som läggs till i redigeraren för sekvenskanalen **Zone1** visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Videon som lagts till i redigeraren för sekvenskanalen **Zone2** visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Lägga till inbäddade sekvenser (komponent) i huvudkanalen (MultiZone)**

   1. Navigera till **Zones** —> **Kanaler** —> **MultiZone**.
   1. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.
   1. Dra och släpp **den inbäddade sekvensen**-komponenten till båda zonerna.
   1. Markera den inbäddade sekvensen i någon av zonerna.
   1. Klicka på ikonen **Konfigurera** (skiftnyckel) till en av de inbäddade sekvenserna i redigeraren.
   1. Välj kanalsökvägen som **Zones** —> **Kanaler** —> **EmbeddedChannels** —> **Zone1**, vilket visas i bilden nedan.
   1. Lägg på liknande sätt till **Zone2** i en annan inbäddad sekvenskomponent i redigeraren.

      ![bild](/help/user-guide/assets/multi-zone/multizone-3.png)

### Skapa en plats och en visning {#creating-location}

Du måste skapa en plats och en visning för att kunna visa innehållet i skärmspelaren. Följ stegen nedan för att skapa en plats och en visning.

1. **Skapa en plats**

   1. Navigera till mappen **Zones** —> **Platser**.
   1. Välj mappen **Platser** och klicka på **Skapa** i åtgärdsfältet.
   1. Välj **Plats** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange **titeln** som **SanJose** och klicka på **Skapa**.

1. **Skapa en bildskärm**

   1. Navigera till mappen **Zones** —> **Platser**.
   1. Välj platsen **SanJose** och klicka på **Skapa** i åtgärdsfältet.
   1. Välj **Visa** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange **titeln** som **Lobby** och klicka på **Skapa**.

### Tilldela kanaler till visningen {#channel-channel}

Du måste tilldela kanalerna till visningen för att kunna visa innehållet. Följ stegen nedan för att tilldela kanalen till visningen.

1. **Tilldela kanal till skärmen**

   1. Navigera till **Zones** —> **Platser** —> **SanJose**—> **Lobby**.
   1. Välj **Lobby**-visningen och klicka på **Tilldela kanal** i åtgärdsfältet.
   1. Ange sökvägen till flerzonskanalen **MultiZone** i **kanalsökvägen**.
   1. Ange **händelser som stöds** som **Inledande inläsning**, **Inaktivitetsskärm** och **Timer**.
   1. Klicka på **Spara**.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. På samma sätt måste du tilldela de andra två inbäddade kanalerna (**Zone1** och **Zone2**) till den här visningen.
   1. När du har tilldelat alla tre kanalerna till **Lobby**-visningen bör du kunna visa de tilldelade kanalerna från kontrollpanelen.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > När du har tilldelat huvudkanalen (i det här fallet **MultiZone**) till visningen är det obligatoriskt att tilldela de andra två inbäddade kanalerna **Zone1** och **Zone2** till samma skärm.

### Registrerar enheten {#registering-device}

När du har konfigurerat en plats och en skärm följer du stegen nedan för att registrera enheten och tilldela skärmen till enheten.

1. **Registrerar enheten**

   1. Navigera till mappen **Zones** —> **Enheter**.
   1. Välj mappen **Enheter** och klicka på **Enhetshanteraren** i åtgärdsfältet.
   1. Klicka på **Enhetsregistrering** och välj den väntande enheten i listan.

      >[!NOTE]
      > Titeln på enheten måste matcha enhetstoken (**Token**-fält) som visas på fliken **Enhetsregistrering**.
   1. Om titeln matchar enhetstoken väljer du enheten och klickar på **Registrera enhet** i åtgärdsfältet.
   1. Om registreringskoden matchar koden i skärmspelaren **Device Registration** klickar du på **Validera** i åtgärdsfältet.
      ![bild](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Ange **titeln** som **Chrome-Device1** och klicka på **Registrera**.
   1. Välj **Tilldela visning** och välj sökvägen till enhetskonfigurationen.

   >[!NOTE]
   >Om du försöker visa innehållet i skärmspelaren ska du klicka på **Uppdatera offlineinnehåll** i kanalkontrollpanelen för var och en av kanalerna som är tilldelade visningen.

### Visa resultatet {#viewing-the-result}

När du har implementerat layouter med flera zoner i de föregående stegen visas följande utdata.

Markera Skärmspelaren för att visa utdata som visar innehållet i två olika zoner. Vänster- och högerzonerna (båda använder inbäddad sekvens som en komponent).

Den vänstra zonen är en sekvenskanal och den högra zonen innehåller en video.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
