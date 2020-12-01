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
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '2535'
ht-degree: 0%

---


# Använda dynamisk inbäddad sekvens {#using-dynamic-embedded-sequence}

Användning av dynamiska inbäddade sekvenser omfattar följande ämnen:

* **Översikt**
* **Använda dynamisk inbäddad upplevelse i AEM Screens**
* **Visa resultaten**
* **Begränsa användare och ändra åtkomstkontrollistor**

## Översikt {#overview}

***Dynamiska inbäddade*** sekvenser skapas för stora projekt som följer efter den överordnade underordnade hierarkin, där den underordnade refereras inuti en platsmapp och inte en kanalmapp. Det gör att användaren kan bädda in en sekvens i en kanal med ***kanalroll***. Det gör att användaren kan definiera platsspecifika platshållare för olika kontor med hjälp av en inbäddad sekvens inuti en huvudkanal.

När du tilldelar en kanal till en visning kan du antingen ange sökvägen till visningen eller rollen för den kanal som ska matchas mot en faktisk kanal i sitt sammanhang.

Om du vill använda dynamisk inbäddad sekvens tilldelar du en kanal med ***Kanalroll***. Kanalrollen definierar visningssammanhanget. Rollen är inriktad på olika åtgärder och är oberoende av den faktiska kanal som uppfyller rollen. I det här avsnittet beskrivs ett användningsfall som definierar kanaler efter roll och hur du kan utnyttja innehållet till en global kanal. Du kan också se rollen som en identifierare för tilldelningen eller ett alias för kanalen i sammanhanget för den.

### Fördelar med att använda dynamiska inbäddade sekvenser {#benefits-of-using-dynamic-embedded-sequences}

Den största fördelen med att placera en sekvenskanal inuti en plats i stället för i kanalmappen är att lokala eller regionala författare kan redigera innehåll som är relevant för dem samtidigt som de inte kan redigera kanaler högre upp i hierarkin.

Med en *kanal efter roll* kan du skapa en lokal version av en kanal för att dynamiskt matcha platsspecifikt innehåll och även skapa en global kanal som utnyttjar innehållet för de platsspecifika kanalerna.

>[!NOTE]
>
>**Inbäddade sekvenser jämfört med dynamiska inbäddade sekvenser**
>
>En dynamisk inbäddad sekvens liknar en inbäddad sekvens men gör det möjligt för användaren att följa en hierarki där ändringar/uppdateringar som görs i en kanal sprids till en annan i relation till den. Den följer hierarkin för överordnade och underordnade och innehåller även resurser som bilder eller videoklipp.
>
>***Med dynamiska inbäddade*** sekvenser kan du visa platsspecifikt innehåll medan  ***inbäddade*** sekvenser endast visar allmänna bildspel av innehållet. När du konfigurerar dynamiska inbäddade sekvenser måste du dessutom konfigurera kanalen med kanalroll och namn. Se stegen nedan för en praktisk implementering.
>
>Mer information om hur du implementerar inbäddade sekvenser finns i [Inbäddade sekvenser](embedded-sequences.md) i AEM Screens.

I följande exempel får du en lösning genom att fokusera på följande nyckeltermer:

* en ***huvudsekvenskanal*** för den globala sekvensen
* ***dynamiska inbäddade*** sekvenskomponenter för varje lokalt anpassningsbar del av sekvensen
* ***de enskilda sekvenskanalerna*** på respektive plats med en  ** roll som matchar den  **dynamiska inbäddade sekvenskomponentens  *roll*.**

>[!NOTE]
>
>Mer information om kanaltilldelning finns i **[Kanaltilldelning](channel-assignment.md)** under redigeringsavsnitt i AEM Screens-dokumentationen.

## Använda dynamisk inbäddad sekvens {#using-dynamic-embedded-sequence-2}

I följande avsnitt beskrivs hur du skapar en dynamisk inbäddad sekvens i en AEM Screens-kanal.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har följande krav klara att börja implementera dynamiska inbäddade sekvenser:

* Skapa ett AEM Screens-projekt (i det här exemplet **Demo**)

* Skapa en kanal som **Global** under **Kanaler** mapp

* Lägg till innehåll i din **Global**-kanal (*Kontrollera **Resources.zip**för relevanta resurser*)

Följande bild visar **Demo**-projektet med kanalen **Global** i mappen **Kanaler**.
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



Implementering av Dynamic Embedded Sequence i ett AEM Screens-projekt innefattar tre viktiga uppgifter:

1. **Konfigurera Project-taxonomin inklusive kanaler, platser och bildskärmar**
1. **Skapa ett schema**
1. **Tilldela schema till varje skärm**

Följ stegen nedan för att implementera funktionen:

>[!CAUTION]
>
>När du implementerar dynamiska inbäddade sekvenser ska du vara försiktig med fälten **Namn** och **Rubrik** när du skapar kanaler under varje plats. Följ instruktionerna i nomenklaturen noga.

1. **Skapa en mapp med två platser.**

   Navigera till mappen **Platser** i ditt AEM Screens-projekt och skapa två platsmappar som **Region A** och **Region B**.

   >[!NOTE]
   >
   >När du skapar platsmappen **Region A** ska du ange **Title** som **Region A** och du kan lämna fältet **Name** tomt, så automatiskt **region-a**-namnet hämtas.
   >
   >Liknande är fallet när du skapar platsmappen **region B**, vilket visas nedan:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Mer information om hur du skapar en plats finns i **[Skapa och hantera platser](managing-locations.md)**.

1. **Skapa två platser och en kanal under varje platsmapp.**

   1. Navigera till **Demo** —> **Platser** —> **Region A**.
   1. Välj **Region A** och klicka på **+ Skapa** i åtgärdsfältet.
   1. Välj **Plats** i guiden med **Titel** som **Lagra 1**. På samma sätt skapar du en annan plats från guiden med namnet **Store 2** med **Title** som **Store 2**. Du kan lämna fältet **Namn** tomt när du skapar **Store 1** och **Store 2**.
   1. Upprepa steg b och välj nu **Sekvenskanal** i guiden. Ange **titeln** som **Region A** och **Namn** som **region** för den här kanalen.

   >[!CAUTION]
   >
   >Se till att du, när du skapar kanalen **Region A**, anger **Title** som **Region A** och **Name** som **region**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Skapa på samma sätt två platser under **Region B** som heter **Store 3** och **Store 4**. Skapa också en **sekvenskanal** med **Titel** som **Region B** och **Namn** som **region**.

   >[!CAUTION]
   >
   >Se till att du kan använda samma namn för de kanaler som skapas i **region A** och **region B** som **region**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Skapa Visning och Kanal under varje plats.**

   1. Navigera till **Demo** —> **Platser** —> **Region A** —> **Store 1**.
   1. Välj **Lagra 1** och klicka på **+ Skapa** i åtgärdsfältet.
   1. Välj **Visa** i guiden och skapa **Store1Display.**
   1. Upprepa steg b och välj den här gången **Sekvenskanal** i guiden. Ange **titeln** som **Store1Channel** och **namnet** som **store**.

   >[!CAUTION]
   >
   >När du skapar en sekvenskanal är det viktigt att kanalens **titel** är som du vill, men **namnet** ska vara detsamma i alla lokala kanaler.
   >I det här exemplet delar kanalerna under **region A** och **region B** samma **namn** som **region** och kanaler under **Store 1**, **Store 2**, **Store 3** och **Store 4** delar samma **Namn** som **store**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Skapa på samma sätt en visning som **Store2Display** och en kanal **Store2Channel** under **Store 2** (med namnet **store**).

   >[!NOTE]
   >Se till att du kan använda samma namn för de kanaler som skapas i **Store 1** och **Store 2** som **store**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Följ stegen ovan för att skapa en kanal och visa den i **Store 3** och **Store 4** under **Region B**. Kontrollera att du använder samma **Namn** som **store** när du skapar kanal **Store3Channel** respektive **Store4Channel**.

   I följande bild visas visning och kanal i **Store 3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   I följande bild visas visning och kanal i **Store 4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Lägg till innehåll i kanalerna på deras respektive platser.**

   Navigera till **Demo** -> **Platser** -> **Region A** -> **Region A** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp de resurser du vill lägga till i kanalen.

   >[!NOTE]
   >Du kan använda filen ***Resources.zip*** i avsnittet **Resources** ovan om du vill använda bilderna som resurser för kanalinnehållet.

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

   Följande bild visar det **AdSchedule** som skapats i **Demo**-projektet.

   ![screen_shot_2018-09-13at3307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Tilldela kanaler till ett schema**

   1. Navigera till **Demo** —> **Scheman** —> **AdSchedule** och klicka på **Kontrollpanelen** i åtgärdsfältet.
   1. Klicka på **+ Tilldela kanal** från **TILLDELADE KANALER** för att öppna dialogrutan **Kanaltilldelning**.
   1. Välj **Referenskanal**. efter bana.
   1. Välj **kanalsökvägen** som **Demo** —> ***Kanaler*** —> ***Global***.
   1. Ange **kanalrollen** som **GlobalAdSegment**.
   1. Välj **Händelser som stöds** som **Inledande inläsning**, **Inaktivitetsskärm** och **Användarinteraktion**.
   1. Klicka på **Spara**.

   **Tilldela kanal efter roll för region:**

   1. Klicka på **+ Tilldela kanal** från **TILLDELADE KANALER** för att öppna dialogrutan **Kanaltilldelning**.
   1. Välj **Referenskanal**. efter namn.
   1. Ange **kanalnamnet** som **region***.
   1. Ange **kanalrollen** som **RegionAdSegment**.
   1. Klicka på **Spara**.

   **Tilldela kanal efter roll för butik:**

   1. Klicka på **+ Tilldela kanal** från **TILLDELADE KANALER** för att öppna dialogrutan **Kanaltilldelning**.
   1. Välj **Referenskanal**. efter namn.
   1. Ange **kanalnamnet** som **store**.
   1. Ange **kanalrollen** som **StoreAdSegment**.
   1. Klicka på **Spara**.

   I följande bild visas de tilldelade kanalerna per sökväg och roll.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Konfigurerar dynamisk inbäddad sekvens till den globala kanalen.**

   Navigera till **Global** Channel, som du ursprungligen skapade i **Demo**-projektet.

   Klicka på **Redigera** i åtgärden för att öppna redigeraren.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Dra och släpp två **dynamiska inbäddade sekvenser**-komponenter i kanalredigeraren.

   Öppna egenskaperna från en av komponenterna och ange **rollen Kanaltilldelning** som **RegionAdSegment**.

   Markera på samma sätt den andra komponenten och öppna egenskaper för att ange **rollen Kanaltilldelning** som **StoreAdSegment**.

   ![channelDisplay4](assets/channeldisplay4.gif)

1. **Tilldela schema till varje skärm**

   1. Navigera till varje skärm, till exempel **Demo** —> **Platser** —> **Region A** —>**Store 1** —>**Store1Display**.
   1. Klicka på **Kontrollpanel** i åtgärden för att öppna kontrollpanelen.
   1. Klicka på **..** från panelen **TILLDELADE KANALER OCH SCHEMALÄGG** och klicka på **+Tilldela schema**.
   1. Välj sökvägen till schemat (här, till exempel **Demo** —> **Scheman** —>**AdSchedule**).
   1. Klicka på **Spara**.

## Visa resultaten {#viewing-the-results}

När du har konfigurerat kanalerna och visningen är klar startar du AEM Screens-spelaren för att visa innehållet.

>[!NOTE]
>
>Läs mer om AEM Screen Player här:
>
>* [AEM Screens Player nedladdningar](https://download.macromedia.com/screens/)
>* [Arbeta med AEM Screens Player](working-with-screens-player.md)



Följande utdata bekräftar ditt kanalinnehåll i AEM Screens Player, beroende på visningssökvägen.

**Scenario 1**:

Om du tilldelar visningssökvägen som **Demo** —> **Platser** —> **Region A** —> **Store 1** —> **Store1Display** visas följande innehåll i din AEM Screens-spelare.

![channelDisplay1](assets/channeldisplay1.gif)

**Scenario 1**:

Om du tilldelar visningssökvägen som **Demo** —> **Platser** —> **Region B** —> **Store 3** —> **Store3Display** visas följande innehåll i din AEM Screens-spelare.

![channelDisplay2](assets/channeldisplay2.gif)

## Begränsa användare och ändra åtkomstkontrollistor {#restricting-users-and-modifying-the-acls}

Du kan skapa globala, regionala eller lokala författare för att redigera innehåll som är relevant för dem samtidigt som du inte kan redigera kanaler högre upp i hierarkin.

Du måste ändra åtkomstkontrollistorna för att begränsa användarnas åtkomst till innehållet baserat på deras plats.

### Exempel på användningsfall {#example-use-case}

I följande exempel kan du skapa tre användare för demonstrationsprojektet ovan.

Följande behörigheter tilldelas varje grupp:

**Grupper**:

* **Global-Author**: Består av användare som har tillgång till alla platser och kanaler i  **** demoprojektet och som har alla läs-, skriv- och redigeringsbehörigheter.

* **Region-Author**: Består av användare som har läs-, skriv- och redigeringsbehörighet för  **region** och  **region B**.

* **Store-Author**: Består av användare som har läs-, skriv- och redigeringsbehörighet endast i  **Store 1**,  **Store 2**,  **Store 3** och  **Store 4**.

#### Steg för att skapa användargrupper, användare och konfigurera åtkomstkontrollistor {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Mer information om hur du skiljer ut projekt med hjälp av åtkomstkontrollistor så att varje enskild person eller grupp hanterar sitt eget projekt finns i **Konfigurera åtkomstkontrollistor**.

Följ stegen nedan för att skapa grupper, användare och ändra åtkomstkontrollistor enligt behörigheterna:

1. **Skapa grupper**

   1. Navigera till **Adobe Experience Manager**.
   1. Klicka på **Verktyg** —> **Säkerhet** —> **Grupper**.
   1. Klicka på **Skapa grupp** och ange **Global-Author** i **ID**.
   1. Klicka på **Spara och stäng**.

   Du kan även skapa två andra grupper, till exempel **Region-Author** och **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Skapa användare och lägga till användare i grupper**

   1. Navigera till **Adobe Experience Manager**.
   1. Klicka på **Verktyg** —> **Säkerhet** —> **Användare**.
   1. Klicka på **Skapa användare** och ange **Global-User** i **ID**.
   1. Ange **Lösenord** och bekräfta lösenordet för den här användaren.
   1. Klicka på fliken **Grupper** och ange gruppnamnet i **Välj grupp**, till exempel ange **Global-Author** för att lägga till **Global-User** till den specifika gruppen.
   1. Klicka på **Spara och stäng**.

   Du kan även skapa två andra användare, till exempel **Region-User** och **Store-User**, och lägga till dem i **Region-Author** respektive **Store-Author**.

   >[!NOTE]
   >Det är en god vana att lägga till användare i en grupp och sedan tilldela behörigheter till varje enskild användargrupp.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Lägg till alla grupper till deltagare**

   1. Navigera till **Adobe Experience Manager**.
   1. Klicka på **Verktyg** —> **Säkerhet** —> **Grupper**.
   1. Välj **Deltagare** i listan och välj fliken **Medlemmar**.
   1. Välj **gruppen**, t.ex. **Global-Author**, **Region-Author,** och **Store-Author** till medverkande.
   1. Klicka på **Spara och stäng**.

1. **Åtkomst till behörigheter för varje grupp**

   1. Navigera till *användaradmin* och använd det här gränssnittet för att ändra behörigheter för olika grupper.
   1. Sök efter **Global-Author** och klicka på fliken **Behörigheter** enligt bilden nedan.
   1. På samma sätt kan du komma åt behörigheterna för **Region-Author** och **Store-Author**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Ändra behörigheter för varje grupp**

   **För global författare:**

   1. Navigera till fliken **Behörigheter**
   1. Navigera till ***/content/screens/demo*** och kontrollera alla behörigheter
   1. Navigera till ***/content/screens/demo/locations*** och kontrollera alla behörigheter
   1. Navigera till ***/content/screens/demo/locations/region-a*** och kontrollera alla behörigheter. Kontrollera på samma sätt behörigheterna för **region-b**.

   Se bilden nedan för att förstå stegen:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   Följande bild visar att nu **Global-User** har åtkomst till **Global Channel** och både **region A** och **region B** med alla fyra butikerna: **Store 1**, **Store 2**, **Store 3** och **Store 4**.

   ![globalt](assets/global.gif)

   **För Region-Author:**

   1. Gå till fliken **Behörigheter**.
   1. Navigera till ***/content/screens/demo*** och kontrollera endast behörigheterna **Läs**.
   1. Navigera till ***/content/screens/demo/locations*** och kontrollera endast behörigheterna **Läs**.
   1. Navigera till ***/content/screens/demo/channel*** och avmarkera behörigheterna för **Global**-kanal.
   1. Navigera till ***/content/screens/demo/locations***/***region-a*** och kontrollera alla behörigheter. Kontrollera på samma sätt behörigheterna för **region-b**.

   Se bilden nedan för att förstå stegen:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   Bilden nedan visar att regionanvändaren nu har åtkomst till både **region A** och **region B** med alla fyra butikerna: **Store 1**, **Store 2**, **Store 3** och **Store 4&lt;a1 1/> men har inte åtkomst till kanalen** Global **.**

   ![region](assets/region.gif)

   **För Store-Author:**

   1. Gå till fliken **Behörigheter**.
   1. Navigera till ***/content/screens/demo*** och kontrollera endast behörigheterna **Läs**.
   1. Navigera till ***/content/screens/demo/locations*** och kontrollera endast behörigheterna **Läs**.
   1. Navigera till ***/content/screens/demo/channel*** och avmarkera behörigheterna för **Global**-kanal.
   1. Navigera till ***/content/screens/demo/locations/region-a*** och kontrollera endast behörigheterna **Läs**. Kontrollera på samma sätt bara behörigheterna **Läs** för **region-b**.
   1. Navigera till ***/content/screens/demo/locations***/***region-a /store-1*** och kontrollera alla behörigheter. Kontrollera på samma sätt behörigheterna för **store-2, store-3,** och **store-4**.

   Se bilden nedan för att förstå stegen:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   Följande bild visar att **Store-User** nu endast har åtkomst till de fyra butikerna: **Store 1**, **Store 2**, **Store 3** och **Store 4**, men inte har behörighet att komma åt **Global&lt;a 11/> eller regionens (** region A **och** region B **) kanaler.**

   ![store](assets/store.gif)

>[!NOTE]
>
>Mer information om hur du konfigurerar behörigheter finns i [Konfigurera åtkomstkontrollistor](setting-up-acls.md).

