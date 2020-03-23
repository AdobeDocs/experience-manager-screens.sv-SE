---
title: Använda dynamisk inbäddad sekvens
seo-title: Använda dynamisk inbäddad sekvens
description: Följ den här sidan för att lära dig hur du implementerar dynamiska inbäddade sekvenser i ditt AEM Screens-projekt.
seo-description: Följ den här sidan för att lära dig hur du implementerar dynamiska inbäddade sekvenser i ditt AEM Screens-projekt.
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
translation-type: tm+mt
source-git-commit: 119d5bdf854674ae86682ed82fee390f63972c0a

---


# Använda dynamisk inbäddad sekvens {#using-dynamic-embedded-sequence}

Användning av dynamiska inbäddade sekvenser omfattar följande ämnen:

* **Översikt**
* **Använda dynamisk inbäddad upplevelse i AEM-skärmar**
* **Visa resultaten**
* **Begränsa användare och ändra åtkomstkontrollistor**

## Översikt {#overview}

***Dynamiska inbäddade sekvenser*** skapas för stora projekt som följer den överordnade underordnade hierarkin, där den underordnade refereras inuti en platsmapp och inte en kanalmapp. Det gör att användaren kan bädda in en sekvens inuti en kanal via ***kanalrollen***. Det gör att användaren kan definiera platsspecifika platshållare för olika kontor med hjälp av en inbäddad sekvens inuti en huvudkanal.

När du tilldelar en kanal till en visning kan du antingen ange sökvägen till visningen eller rollen för den kanal som ska matchas mot en faktisk kanal i sitt sammanhang.

Om du vill använda dynamisk inbäddad sekvens tilldelar du en kanal efter ***kanalroll***. Kanalrollen definierar visningssammanhanget. Rollen är inriktad på olika åtgärder och är oberoende av den faktiska kanal som uppfyller rollen. I det här avsnittet beskrivs ett användningsfall som definierar kanaler efter roll och hur du kan utnyttja innehållet till en global kanal. Du kan också se rollen som en identifierare för tilldelningen eller ett alias för kanalen i sammanhanget för den.

### Fördelar med att använda dynamiska inbäddade sekvenser {#benefits-of-using-dynamic-embedded-sequences}

Den största fördelen med att placera en sekvenskanal inuti en plats i stället för i kanalmappen är att lokala eller regionala författare kan redigera innehåll som är relevant för dem samtidigt som de inte kan redigera kanaler högre upp i hierarkin.

Med hjälp av en *kanal efter roll* kan du skapa en lokal version av en kanal, för att dynamiskt matcha platsspecifikt innehåll och även skapa en global kanal som utnyttjar innehållet för de platsspecifika kanalerna.

>[!NOTE]
>
>**Inbäddade sekvenser jämfört med dynamiska inbäddade sekvenser**
>
>En dynamisk inbäddad sekvens liknar en inbäddad sekvens men gör det möjligt för användaren att följa en hierarki där ändringar/uppdateringar som görs i en kanal sprids till en annan i relation till den. Den följer hierarkin för överordnade och underordnade och innehåller även resurser som bilder eller videoklipp.
>
>***Med dynamiska inbäddade sekvenser*** kan du visa platsspecifikt innehåll medan ***inbäddade sekvenser*** endast visar allmänna bildspel av innehållet. När du konfigurerar dynamiska inbäddade sekvenser måste du dessutom konfigurera kanalen med kanalroll och namn. Se stegen nedan för en praktisk implementering.
>
>Mer information om hur du implementerar inbäddade sekvenser finns i [Inbäddade sekvenser](embedded-sequences.md) i AEM-skärmar.

I följande exempel får du en lösning genom att fokusera på följande nyckeltermer:

* en ***huvudsekvenskanal*** för den globala sekvensen
* ***dynamiska inbäddade sekvenskomponenter*** för varje lokalt anpassningsbar del av sekvensen
* ***enskilda sekvenskanaler*** på respektive plats med en *roll* i visningen som matchar den **dynamiska inbäddade sekvenskomponentens *roll*.**

>[!NOTE]
>
>Mer information om kanaltilldelning finns i **[Kanaltilldelning](channel-assignment.md)**under Redigering i dokumentationen för AEM-skärmar.

## Använda dynamisk inbäddad sekvens {#using-dynamic-embedded-sequence-2}

I följande avsnitt beskrivs hur du skapar en dynamisk inbäddad sekvens i en AEM-skärmkanal.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har följande krav klara att börja implementera dynamiska inbäddade sekvenser:

* Skapa ett AEM Screens-projekt (i det här exemplet **Demo**)

* Skapa en kanal som **global** under mappen **Kanaler**

* Lägg till innehåll i din **globala** kanal (*se **Resources.zip**för relevanta resurser*)

I följande bild visas **demonstrationsprojektet** med den **globala** kanalen i mappen **Kanaler** .
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Resurser {#resources}

Du kan hämta följande resurser (bilder och lägga till dem i resurser) och sedan använda dem som kanalinnehåll för demonstrationssyfte.

[Hämta fil](assets/resources.zip)

>[!NOTE]
>
>Mer information om hur du skapar ett projekt och hur du skapar en sekvenskanal finns i resurserna nedan:
>
>* **[Skapa och hantera projekt](creating-a-screens-project.md)**
>* **[Hantera en kanal](managing-channels.md)**
>



Implementering av dynamisk inbäddad sekvens i ett AEM-skärmsprojekt innefattar tre viktiga uppgifter:

1. **Konfigurera Project-taxonomin inklusive kanaler, platser och bildskärmar**
1. **Skapa ett schema**
1. **Tilldela schema till varje skärm**

Följ stegen nedan för att implementera funktionen:

>[!CAUTION]
>
>När du implementerar dynamiska inbäddade sekvenser bör du vara försiktig med fälten **Namn** och **Titel** när du skapar kanaler under varje plats. Följ instruktionerna i nomenklaturen noga.

1. **Skapa en mapp med två platser.**

   Navigera till mappen **Platser** i ditt AEM Screens-projekt och skapa två platsmappar som **Region A** och **Region B**.

   >[!NOTE]
   >
   >När du skapar en **platsmapp för region A** måste du ange **Titel** som **region A** och lämna fältet **Namn** tomt så att automatiskt **region-a** -namn hämtas.
   >
   >Liknande är fallet när du skapar en **platsmappregion B**, vilket visas nedan:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en plats finns i **[Skapa och hantera platser](managing-locations.md)**.

1. **Skapa två platser och en kanal under varje platsmapp.**

   1. Navigera till **Demo** —> **Platser** —> **Region A**.
   1. Markera **område A** och klicka på **+ Skapa** i åtgärdsfältet.
   1. Välj **Plats** i guiden med **Titel** som **Store 1**. Skapa en annan plats från guiden som heter **Store 2** med **Title** as **Store 2**. Du kan lämna fältet **Namn** tomt när du skapar **Store 1** och **Store 2**.
   1. Upprepa steg b och välj **Sekvenskanal** i guiden. Ange **Title** som **Region A** och **Name** som **region **för den här kanalen.
   >[!CAUTION]
   >
   >Kontrollera att du anger **Title** som **Region A** och **Name** som **region när du skapar kanalområde A** ****.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Du kan också skapa två platser under **Region B** med namnen **Store 3** och **Store 4**. Skapa också en **sekvenskanal** med **titeln** som **region B** och **namnet** som **region**.

   >[!CAUTION]
   >
   >Se till att du kan använda samma namn för de kanaler som skapas i **region A** och **region B** som **region**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Skapa Visning och Kanal under varje plats.**

   1. Navigera till **Demo** —> **Platser** —> **Region A** —> **Store 1**.
   1. Välj **Store 1** och klicka på **+ Create** i åtgärdsfältet.
   1. Välj **Visa** i guiden och skapa **Store1Display.**
   1. Upprepa steg b och välj sedan **Sekvenskanal** i guiden. Ange **Title** som **Store1Channel** och **Name** as **store**.
   >[!CAUTION]
   >
   >När du skapar en sekvenskanal är det viktigt att kanalens **namn** är som du vill, men **namnet** ska vara detsamma i alla lokala kanaler.
   >
   >I det här exemplet har kanalerna under **Region A** och **Region B** samma **namn** som **region** och kanaler under **Store 1************** **** ****,¥Store 2,¥Store 3¥ och¥Store 4¥ samma¥Name¥ somstore¥¥.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   På samma sätt kan du skapa en skärm som **Store2Display** och en channel **Store2Channel** under **Store 2** (med namnet **store**).

   >[!NOTE]
   >
   >Se till att du kan använda samma namn för de kanaler som skapas i **Store 1** och **Store 2** som **store**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Följ stegen ovan för att skapa en kanal och visa den i **Store 3** och **Store 4** under **Region B**. Se även till att du använder samma **namn** som **butik** när du skapar kanal **Store3Channel** respektive **Store4Channel** .

   Följande bild visar visningen och kanalen i **Store 3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   Bilden nedan visar visningen och kanalen i **Store 4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Lägg till innehåll i kanalerna på deras respektive platser.**

   Navigera till **Demo** -> **Platser** -> **Region A** -> **Region A** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp de resurser du vill lägga till i kanalen.

   >[!NOTE]
   >
   >Du kan använda ***Resources.zip*** -filen i avsnittet **Resources** ovan om du vill använda bilderna som resurser för kanalinnehållet.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   På samma sätt går du till **Demo** -> **Platser** -> **Region B** -> **Region B** och klickar på **Redigera** i åtgärdsfältet för att dra och släppa resurserna i din kanal, som visas nedan:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Följ de föregående stegen och resurserna för att lägga till innehåll i följande kanaler:

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **Skapa ett schema**

   Navigera till och välj mappen **Scheman** i ditt AEM Screens-projekt och klicka på **Skapa** i åtgärdsfältet för att skapa ett nytt schema.

   Följande bild visar **AdSchedule** som skapats i **Demo** -projektet.

   ![screen_shot_2018-09-13at3307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Tilldela kanaler till ett schema**

   1. Navigera till **Demo** —> **Scheman** —> **AdSchedule** och klicka på **Dashboard** i åtgärdsfältet.
   1. Klicka på **+ Tilldela kanal** på panelen **TILLDELADE KANALER** för att öppna dialogrutan **Kanaltilldelning** .
   1. Välj **referenskanal**.. efter bana.
   1. Välj **kanalsökvägen** som **demo** —> ***Kanaler*** —> ***Global***.
   1. Ange **kanalrollen** som **GlobalAdSegment**.
   1. Välj **Händelser** som stöds som **Inledande inläsning**, **Inaktivitetsskärm** och **Användarinteraktion**.
   1. Click **Save**.
   **Tilldela kanal efter roll för region:**

   1. Klicka på **+ Tilldela kanal** på panelen **TILLDELADE KANALER** för att öppna dialogrutan **Kanaltilldelning** .
   1. Välj **referenskanal**.. efter namn.
   1. Ange **kanalnamnet** som **region***.
   1. Ange **kanalrollen** som **RegionAdSegment**.
   1. Click **Save**.
   **Tilldela kanal efter roll för butik:

   1. Klicka på **+ Tilldela kanal** på panelen **TILLDELADE KANALER** för att öppna dialogrutan **Kanaltilldelning** .
   1. Välj **referenskanal**.. efter namn.
   1. Ange **kanalnamnet** som **butik**.
   1. Ange **kanalrollen** som **StoreAdSegment**.
   1. Click **Save**.
   I följande bild visas de tilldelade kanalerna per sökväg och roll.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Konfigurerar dynamisk inbäddad sekvens till den globala kanalen.**

   Navigera till den **globala** kanalen som du ursprungligen skapade i **Demo** -projektet.

   Klicka på **Redigera** i funktionsmakrot för att öppna redigeraren.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Dra och släpp två **dynamiska inbäddade sekvenskomponenter** i kanalredigeraren.

   Öppna egenskaperna från en av komponenterna och ange **kanaltilldelningsrollen** som **RegionAdSegment**.

   På samma sätt markerar du den andra komponenten och öppnar egenskaper för att ange **kanaltilldelningsrollen** som **StoreAdSegment**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **Tilldela schema till varje skärm**

   1. Navigera till varje skärm, till exempel **Demo** —> **Platser** —> **Region A** —>**Store 1** —>**Store1Display**.
   1. Klicka på **Kontrollpanel** i åtgärden för att öppna kontrollpanelen.
   1. Klicka **..** på panelen **TILLDELADE KANALER OCH SCHEMALÄGG** och ytterligare klicka på **+Tilldela schema**.
   1. Välj sökvägen till schemat (här, till exempel **Demo** —> **Scheman** —>**AdSchedule**).
   1. Click **Save**.

## Visa resultaten {#viewing-the-results}

När du har konfigurerat kanalerna och visningen är klar startar du AEM Screens Player för att visa innehållet.

>[!NOTE]
>
>Läs mer om AEM Screen Player här:
>
>* [Ladda ned AEM Screens Player](https://download.macromedia.com/screens/)
>* [Arbeta med AEM Screens Player](working-with-screens-player.md)



Följande utdata bekräftar ditt kanalinnehåll i AEM Screens Player, beroende på visningssökvägen.

**Scenario 1**:

Om du tilldelar visningssökvägen som **Demo** —> **Platser** —> **Region A** —>** Store 1** —> **Store1Display**, visas följande innehåll i din AEM-skärmspelare.

![channeldisplay1](assets/channeldisplay1.gif)

**Scenario 1**:

Om du tilldelar visningssökvägen som **Demo** —> **Platser** —> **Region B** —> **Store 3** —> **Store3Display** visas följande innehåll i din AEM-skärmsspelare.

![channeldisplay2](assets/channeldisplay2.gif)

## Begränsa användare och ändra åtkomstkontrollistor {#restricting-users-and-modifying-the-acls}

Du kan skapa globala, regionala eller lokala författare för att redigera innehåll som är relevant för dem samtidigt som du inte kan redigera kanaler högre upp i hierarkin.

Du måste ändra åtkomstkontrollistorna för att begränsa användarnas åtkomst till innehållet baserat på deras plats.

### Exempel på användningsfall {#example-use-case}

I följande exempel kan du skapa tre användare för demonstrationsprojektet ovan.

Följande behörigheter tilldelas varje grupp:

**Grupper**:

* **Global-Author**: Består av användare som har tillgång till alla platser och kanaler i **demoprojektet** och har alla läs-, skriv- och redigeringsbehörigheter.

* **Region-Author**: Består av användare som har läs-, skriv- och redigeringsbehörigheter i **region A** och **region B**.

* **Store-Author**: Består av användare som har läs-, skriv- och redigeringsbehörighet endast i **Store 1**, **Store 2**, **Store 3** och **Store 4**.

#### Steg för att skapa användargrupper, användare och konfigurera åtkomstkontrollistor {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Mer information om hur du skiljer ut projekt med hjälp av åtkomstkontrollistor så att varje enskild person eller grupp hanterar sitt eget projekt finns i **Konfigurera åtkomstkontrollistor**.

Följ stegen nedan för att skapa grupper, användare och ändra åtkomstkontrollistor enligt behörigheterna:

1. **Skapa grupper**

   1. Gå till **Adobe Experience Manager**.
   1. Klicka på **Verktyg** —> **Säkerhet** —> **Grupper**.
   1. Klicka på **Skapa grupp** och ange **Global-Author** i **ID**.
   1. Klicka på **Spara och stäng**.
   Du kan också skapa två andra grupper, till exempel **Region-Author** och **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Skapa användare och lägga till användare i grupper**

   1. Gå till **Adobe Experience Manager**.
   1. Klicka på **Verktyg** —> **Säkerhet** —> **Användare**.
   1. Klicka på **Skapa användare** och ange **Global-User** i **ID**.
   1. Ange **lösenordet** och bekräfta lösenordet för den här användaren.
   1. Klicka på fliken **Grupper** och ange gruppnamnet i **Välj grupp**, till exempel ange **Global-Author** för att lägga till **Global-User** i den specifika gruppen.
   1. Klicka på **Spara och stäng**.
   Du kan också skapa två andra användare, till exempel **Region-Användare** och **Store-User** , och lägga till dem i **Region-Författare** respektive **Store-Författare** .

   >[!NOTE]
   >
   >Det är en god vana att lägga till användare i en grupp och sedan tilldela behörigheter till varje enskild användargrupp.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Lägg till alla grupper till deltagare**

   1. Gå till **Adobe Experience Manager**.
   1. Klicka på **Verktyg** —> **Säkerhet** —> **Grupper**.
   1. Välj **Medarbetare** i listan och välj fliken **Medlemmar** .
   1. Markera **gruppen** som **Global-Author**, **** Region-Author och **Store-Author** till medverkande.
   1. Klicka på **Spara och stäng**.

1. **Åtkomst till behörigheter för varje grupp**

   1. Navigera till *användaradministratören* och använd det här gränssnittet för att ändra behörigheter för olika grupper.
   1. Sök efter **Global-Author** och klicka på fliken **Behörigheter** , så som visas i bilden nedan.
   1. På samma sätt kan du komma åt behörigheterna för **Region-Author** och **Store-Author**.
   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Ändra behörigheter för varje grupp**

   **För global författare:**

   1. Navigate to the **Permissions** tab
   1. Navigera till ***/content/screens/demo*** och kontrollera alla behörigheter
   1. Navigera till ***/content/screens/demo/locations*** och kontrollera alla behörigheter
   1. Navigera till ***/content/screens/demo/locations***/***region-a*** och kontrollera alla behörigheter. Kontrollera på samma sätt behörigheterna för **region-b**.
   Se bilden nedan för att förstå stegen:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   Bilden nedan visar att **Global-User** nu har åtkomst till **Global Channel** och både **Region A** och **Region B** med alla fyra butikerna: **Store 1**************,¥Store 2¥,¥Store 3¥ ochStore 4¥.

   ![globalt](assets/global.gif)

   **För Region-Author:**

   1. Navigate to the **Permissions** tab.
   1. Navigera till ***/content/screens/demo*** och kontrollera endast **läsbehörighet** .
   1. Navigera till ***/content/screens/demo/locations*** och kontrollera endast **läsbehörighet** .
   1. Navigera till ***/content/screens/demo/channel ***och avmarkera behörigheterna för den **globala**kanalen.***
   1. Navigera till ***/content/screens/demo/locations***/***region-a*** och kontrollera alla behörigheter. Kontrollera på samma sätt behörigheterna för **region-b**.
   Se bilden nedan för att förstå stegen:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   Bilden nedan visar att Region-User nu har åtkomst till både **Region A** och **Region B** med alla fyra butikerna: **Store 1**, **Store 2**, **Store 3****** **** och¥Store 4, men inte till Global¥ Channel.

   ![region](assets/region.gif)

   **För Store-Author:**

   1. Navigate to the **Permissions** tab.
   1. Navigera till ***/content/screens/demo*** och kontrollera endast **läsbehörighet** .
   1. Navigera till ***/content/screens/demo/locations*** och kontrollera endast **läsbehörighet** .
   1. Navigera till ***/content/screens/demo/channel*** och avmarkera behörigheterna för den **globala** kanalen.
   1. Navigera till ***/content/screens/demo/locations/region-a*** och kontrollera endast **läsbehörigheterna** . På samma sätt bör du bara kontrollera **läsbehörighet** för **region-b**.
   1. Navigera till ***/content/screens/demo/locations***/***region-a /store-1*** och kontrollera alla behörigheter. Kontrollera på samma sätt behörigheterna för **store-2,** store-3 och **store-4**.
   Se bilden nedan för att förstå stegen:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   Bilden nedan visar att **Store-User** nu endast har åtkomst till de fyra butikerna: **Store 1**, **Store 2**, **Store 3** och **Store 4** ******** ****, men inte har behörighet att komma åt¥Global eller regionen (¥Region Aoch¥Region B¥).

   ![store](assets/store.gif)

>[!NOTE]
>
>Mer information om hur du konfigurerar behörigheter finns i [Konfigurera åtkomstkontrollistor](setting-up-acls.md).

