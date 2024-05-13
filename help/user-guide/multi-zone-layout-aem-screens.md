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
* Använda enskilda resurser i en eller flera zoner
* Använda sekvensinnehåll i en eller flera zoner

## Ökning {#overview}

***Layout med flera zoner*** I kan du skapa innehåll med flera zoner och använda olika resurser, till exempel videoklipp, bilder och text som kan kombineras på en enda skärm. Du kan lägga in bilder, videor och text så att allt hänger ihop och skapar en intuitiv digital upplevelse.

Enligt projektkraven behöver du ibland flera zoner i en kanal och kan redigera dem som en enda heltäckande enhet. Till exempel en produktsekvens med en relaterad feed för sociala medier som körs i tre separata zoner på en enda kanal.

>[!NOTE]
>I kanaler med flera zoner rekommenderas inte schemaläggning på tillgångsnivå på grund av potentiella konflikter och oavsiktligt beteende. Om schemaläggning på tillgångsnivå behövs skapar du en separat sekvenskanal och tillämpar schemaläggningslogik i den kanalen. Bädda sedan in sekvenskanalen i flerzonskanalen.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen måste du ha den konceptuella kunskapen om:

* [Skapa ett AEM Screens-projekt](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [Skapa en bildskärm](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [Tilldela en kanal till en skärm](/help/user-guide/channel-assignment.md)

## Skapa layout med flera zoner {#creating-multi-zone-layout}

När du skapar en kanal kan du använda olika mallar för att skapa zoner i kanalen. Du kan lägga till en bild, video eller en inbäddad kanal som gör att flera resurser kan visas i en sekvens.

**Skapa en kanal**

1. Klicka på länken Adobe Experience Manager (överst till vänster) och sedan **Skärmar**. Du kan också gå direkt till: `http://localhost:4502/screens.html/content/screens`.
1. Navigera till **Kanaler** mapp och klicka på **Skapa** i åtgärdsfältet.

1. Klicka **1x2 Delad skärmkanal** från **Skapa** guide.

1. Klicka **Nästa** och anger **title** as **MultiZone**.

1. Klicka **Skapa** för att slutföra kanalskapandet.

### Använda enskilda resurser i en eller flera zoner {#using-single-assets-in-one-or-more-zones}

Du kan använda enstaka resurser som en bild eller en video i alla enskilda zoner. Följ stegen nedan för implementering:

1. **Lägga till innehåll i kanalen**

   1. Navigera till **Zoner** > **Kanaler**> **MultiZone**.
   1. Klicka på **MultiZone** och klicka på **Redigera** i åtgärdsfältet.

1. **Lägga till bilder i kanalen**

   Om du vill spela upp en enstaka bild eller en video i två zoner drar och släpper du bara en bild till varje zon i kanalredigeraren enligt bilden nedan:

   ![bild](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Använda sekvensinnehåll i en eller flera zoner {#using-sequenced-content-in-one-or-more-zones}

Om du vill att zonerna ska visa en bildsekvens och en video i olika zoner följer du stegen nedan för mer information.

1. **Skapa en kanalmapp**

   1. Navigera till **Zoner** > **MultiZone** > **Kanaler** och klicka **Skapa** i åtgärdsfältet.
   1. Klicka **Mappen Kanaler** från **Skapa** guide och klicka **Nästa**.
   1. Ange titeln som **InbäddadeKanaler** och klicka **Skapa**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Lägga till ytterligare två kanaler i kanalmappen**

   1. Navigera till **Zoner** > **Kanaler** > **InbäddadeKanaler** och klicka **Skapa** i åtgärdsfältet.
   1. Klicka **Sekvenskanal** från **Skapa** guide för att skapa en kanal med namnet **`Zone1`**.
   1. Klicka **`Zone1`** och klicka **Redigera** i åtgärdsfältet.
   1. Dra och släpp några bilder i den här kanalen.
   1. Skapa en annan sekvenskanal med namnet som **`Zone2`** in **InbäddadeKanaler** mapp.
   1. Dra och släpp en video i den här kanalen.

   I följande bild visas kanalerna **`Zone1`** och **`Zone2`**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Bilderna som lagts till i redigeraren av **`Zone1`** sekvenskanal visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Videon har lagts till i redigeraren av **`Zone2`** sekvenskanal visas nedan:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Lägga till inbäddade sekvenser (komponent) i huvudkanalen (MultiZone)**

   1. Navigera till **Zoner** > **Kanaler** > **MultiZone**.
   1. Klicka **Redigera** i åtgärdsfältet.
   1. Dra och släpp **Inbäddad sekvens** till båda zonerna.
   1. Klicka på den inbäddade sekvensen i någon av zonerna.
   1. Klicka på **Konfigurera** (skiftnyckel) till en av de inbäddade sekvenserna i redigeraren.
   1. Klicka på kanalbanan som **Zoner** > **Kanaler** > **InbäddadeKanaler** > **`Zone1`**, vilket visas i figuren nedan.
   1. Lägg på samma sätt till **`Zone2`** till en annan inbäddad sekvenskomponent i redigeraren.

      ![bild](/help/user-guide/assets/multi-zone/multizone-3.png)

### Skapa en plats och en visning {#creating-location}

Skapa en plats och en skärm så att du kan visa innehållet i AEM Screens Player.

1. **Skapa en plats**

   1. Navigera till **Zoner** > **Platser** mapp.
   1. Klicka på **Platser** mapp och klicka på **Skapa** i åtgärdsfältet.
   1. Klicka **Plats** från **Skapa** guide och klicka **Nästa**.
   1. Ange **Titel** as **SanJose** och klicka **Skapa**.

1. **Skapa en bildskärm**

   1. Navigera till **Zoner** > **Platser** mapp.
   1. Klicka på **SanJose** plats och klicka **Skapa** i åtgärdsfältet.
   1. Klicka **Visa** från **Skapa** guide och klicka **Nästa**.
   1. Ange **Titel** as **Lobby** och klicka **Skapa**.

### Tilldela kanaler till visningen {#channel-channel}

Tilldela kanalerna till visningen för att visa innehållet. Följ stegen nedan för att tilldela kanalen till visningen.

1. **Tilldela kanal till skärmen**

   1. Navigera till **Zoner** > **Platser** > **SanJose**> **Lobby**.
   1. Klicka på **Lobby** visa och klicka **Tilldela kanal** i åtgärdsfältet.
   1. Ange sökvägen till **MultiZone** kanal in **Kanalsökväg**.
   1. Ange **Händelser som stöds** as **Inledande inläsning**, **Inaktiv skärm** och **Timer**.
   1. Klicka **Spara**.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Tilldela på liknande sätt de andra två inbäddade kanalerna (**`Zone1`** och **`Zone2`**) till den här skärmen.
   1. När du har tilldelat alla tre kanalerna till **Lobby** ska du kunna visa de tilldelade kanalerna från kontrollpanelen.

      ![bild](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      >När du har tilldelat huvudkanalen (i det här fallet **MultiZone**) till skärmen är det obligatoriskt att tilldela de andra två inbäddade kanalerna **`Zone1`** och **`Zone2`** även på samma skärm.

### Registrerar enheten {#registering-device}

När du har konfigurerat en plats och en skärm följer du stegen nedan för att registrera enheten och tilldela skärmen till enheten.

1. **Registrerar enheten**

   1. Navigera till **Zoner** > **Enheter** mapp.
   1. Klicka på **Enheter** mapp och klicka på **Enhetshanteraren** i åtgärdsfältet.
   1. Klicka **Enhetsregistrering** och klicka på den väntande enheten i listan.

      >[!NOTE]
      > Enhetens titel måste matcha enhetstoken (**Token** fält) som visas i **Enhetsregistrering** -fliken.

   1. Om titeln matchar enhetstoken klickar du på enheten och sedan på **Registrera enhet** i åtgärdsfältet.
   1. Om registreringskoden matchar koden i skärmspelaren **Enhetsregistrering** flik, klicka **Validera** i åtgärdsfältet.
      ![bild](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Ange **Titel** as **`Chrome-Device1`** och klicka **Registrera**.
   1. Klicka **Tilldela visning** och klicka på sökvägen till enhetskonfigurationen.

   >[!NOTE]
   >Om du försöker visa innehållet i skärmspelaren ska du klicka **Uppdatera offlineinnehåll** från kanalkontrollpanelen för var och en av de kanaler som är tilldelade visningen.

### Visa resultatet {#viewing-the-result}

När du implementerar layouter med flera zoner med de föregående stegen visas följande utdata.

Markera Skärmspelaren så att du kan visa utdata som visar innehållet i två olika zoner. I den vänstra och högra zonen (båda används en inbäddad sekvens som en komponent).

Den vänstra zonen är en sekvenskanal och den högra zonen innehåller en video.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
