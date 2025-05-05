---
title: Layout med flera zoner
description: Lär dig hur du skapar innehåll med flera zoner och använder olika resurser som videoklipp, bilder och text som kombineras på en enda skärm i AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Layout med flera zoner {#multi-zone-layout}

På följande sida beskrivs användningen av layout med flera zoner och följande avsnitt beskrivs:

* Ökning
* Skapa layout med flera zoner
* Förutsättningar
* Använda en Assets i en eller flera zoner
* Använda sekvensinnehåll i en eller flera zoner

## Ökning {#overview}

Med ***Layout med flera zoner*** kan du skapa innehåll med flera zoner och använda olika resurser, till exempel videoklipp, bilder och text som kan kombineras på en enda skärm. Du kan lägga in bilder, videor och text så att allt hänger ihop och skapar en intuitiv digital upplevelse.

Enligt projektkraven behöver du ibland flera zoner i en kanal och kan redigera dem som en enda heltäckande enhet. Till exempel en produktsekvens med en relaterad feed för sociala medier som körs i tre separata zoner på en enda kanal.

>[!NOTE]
>I kanaler med flera zoner rekommenderas inte schemaläggning på tillgångsnivå på grund av potentiella konflikter och oavsiktligt beteende. Om schemaläggning på tillgångsnivå behövs skapar du en separat sekvenskanal och tillämpar schemaläggningslogik i den kanalen. Bädda sedan in sekvenskanalen i flerzonskanalen.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen måste du ha den konceptuella kunskapen om:

* [Skapa ett AEM Screens-projekt](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [Skapar en visning](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [Tilldela en kanal till en skärm](/help/user-guide/channel-assignment.md)

## Skapa layout med flera zoner {#creating-multi-zone-layout}

När du skapar en kanal kan du använda olika mallar för att skapa zoner i kanalen. Du kan lägga till en bild, video eller en inbäddad kanal som gör att flera resurser kan visas i en sekvens.

**Skapar en kanal**

1. Klicka på länken Adobe Experience Manager (överst till vänster) och sedan **Screens**. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.
1. Navigera till mappen **Kanaler** och klicka på **Skapa** i åtgärdsfältet.

1. Klicka på **1x2 Delad skärmkanal** i guiden **Skapa**.

1. Klicka på **Nästa** och ange **title** som **MultiZone**.

1. Klicka på **Skapa** för att slutföra kanalskapandet.

### Använda en Assets i en eller flera zoner {#using-single-assets-in-one-or-more-zones}

Du kan använda enstaka resurser som en bild eller en video i alla enskilda zoner. Följ stegen nedan för implementering:

1. **Lägger till innehåll i kanalen**

   1. Navigera till **Zones** > **Kanaler**> **MultiZone**.
   1. Klicka på **MultiZone**-kanalen och klicka på **Redigera** i åtgärdsfältet.

1. **Lägger till bilder i kanalen**

   Om du vill spela upp en enstaka bild eller en video i två zoner drar och släpper du bara en bild till varje zon i kanalredigeraren enligt bilden nedan:

   ![bild](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Använda sekvensinnehåll i en eller flera zoner {#using-sequenced-content-in-one-or-more-zones}

Om du vill att zonerna ska visa en bildsekvens och en video i olika zoner följer du stegen nedan för mer information.

1. **Skapar en kanalmapp**

   1. Navigera till **Zones** > **MultiZone** > **Channel** och klicka på **Create** i åtgärdsfältet.
   1. Klicka på **Kanalmapp** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange titeln som **EmbeddedChannels** och klicka på **Create**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Lägger till ytterligare två kanaler i kanalmappen**

   1. Navigera till **Zones** > **Channels** > **EmbeddedChannels** och klicka på **Create** i åtgärdsfältet.
   1. Klicka på **Sekvenskanal** i guiden **Skapa** för att skapa en kanal med namnet **`Zone1`**.
   1. Klicka på **`Zone1`** och klicka på **Redigera** i åtgärdsfältet.
   1. Dra och släpp några bilder i den här kanalen.
   1. Skapa på samma sätt en annan sekvenskanal med namnet **`Zone2`** i mappen **EmbeddedChannels** .
   1. Dra och släpp en video i den här kanalen.

   I följande bild visas kanalerna **`Zone1`** och **`Zone2`**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Bilderna som läggs till i redigeraren för **`Zone1`**-sekvenskanalen visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Videon som lagts till i redigeraren för sekvenskanalen **`Zone2`** visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Lägger till inbäddade sekvenser (komponent) i huvudkanalen (MultiZone)**

   1. Navigera till **Zones** > **Kanaler** > **MultiZone**.
   1. Klicka på **Redigera** i åtgärdsfältet.
   1. Dra och släpp komponenten **Inbäddad sekvens** till båda zonerna.
   1. Klicka på den inbäddade sekvensen i någon av zonerna.
   1. Klicka på ikonen **Konfigurera** (skiftnyckel) för att göra en av de inbäddade sekvenserna i redigeraren.
   1. Klicka på kanalsökvägen som **Zones** > **Channels** > **EmbeddedChannels** > **`Zone1`**, vilket visas i bilden nedan.
   1. Lägg på samma sätt till **`Zone2`** i en annan inbäddad sekvenskomponent i redigeraren.

      ![bild](/help/user-guide/assets/multi-zone/multizone-3.png)

### Skapa en plats och en visning {#creating-location}

Skapa en plats och en skärm så att du kan visa innehållet i AEM Screens Player.

1. **Skapar en plats**

   1. Navigera till mappen **Zones** > **Locations**.
   1. Klicka på mappen **Platser** och klicka på **Skapa** i åtgärdsfältet.
   1. Klicka på **Plats** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange **Title** som **SanJose** och klicka på **Create**.

1. **Skapar en visning**

   1. Navigera till mappen **Zones** > **Locations**.
   1. Klicka på platsen **SanJose** och klicka på **Skapa** i åtgärdsfältet.
   1. Klicka på **Visa** i guiden **Skapa** och klicka på **Nästa**.
   1. Ange **Title** som **Lobby** och klicka på **Create**.

### Tilldela kanaler till visningen {#channel-channel}

Tilldela kanalerna till visningen för att visa innehållet. Följ stegen nedan för att tilldela kanalen till visningen.

1. **Tilldela kanal till skärmen**

   1. Navigera till **Zones** > **Locations** > **SanJose**> **Lobby**.
   1. Klicka på visningen av **lobbyn** och klicka på **Tilldela kanal** i åtgärdsfältet.
   1. Ange sökvägen till **MultiZone**-kanalen i **Kanalsökväg**.
   1. Ange **händelser som stöds** som **Inledande inläsning**, **Inaktivitetsskärm** och **Timer**.
   1. Klicka på **Spara**.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Tilldela på liknande sätt de andra två inbäddade kanalerna (**`Zone1`** och **`Zone2`**) till den här visningen.
   1. När du har tilldelat alla tre kanalerna till **Lobby**-visningen bör du kunna visa de tilldelade kanalerna från kontrollpanelen.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      >När du har tilldelat huvudkanalen (i det här fallet **MultiZone**) till visningen är det obligatoriskt att tilldela de andra två inbäddade kanalerna **`Zone1`** och **`Zone2`** även till samma skärm.

### Registrerar enheten {#registering-device}

När du har konfigurerat en plats och en skärm följer du stegen nedan för att registrera enheten och tilldela skärmen till enheten.

1. **Registrerar enheten**

   1. Navigera till mappen **Zones** > **Devices**.
   1. Klicka på mappen **Enheter** och klicka på **Enhetshanteraren** i åtgärdsfältet.
   1. Klicka på **Enhetsregistrering** och klicka på den väntande enheten i listan.

      >[!NOTE]
      > Titeln på enheten måste matcha enhetstoken (**Token**-fältet) som visas på fliken **Enhetsregistrering**.

   1. Om titeln matchar enhetstoken klickar du på enheten och sedan på **Registrera enhet** i åtgärdsfältet.
   1. Om registreringskoden matchar koden på fliken **Device Registration** i Screens Player klickar du på **Validate** i åtgärdsfältet.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Ange **Titel** som **`Chrome-Device1`** och klicka på **Registrera**.
   1. Klicka på **Tilldela skärm** och klicka på sökvägen till enhetskonfigurationen.

   >[!NOTE]
   >Om du försöker visa innehållet i Screens-spelaren ska du klicka på **Uppdatera offlineinnehåll** på kanalkontrollpanelen för var och en av de kanaler som är tilldelade till visningen.

### Visa resultatet {#viewing-the-result}

När du implementerar layouter med flera zoner med de föregående stegen visas följande utdata.

Kontrollera Screens-spelaren så att du kan visa utdata som visar innehållet i två olika zoner. I den vänstra och högra zonen (båda används en inbäddad sekvens som en komponent).

Den vänstra zonen är en sekvenskanal och den högra zonen innehåller en video.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
