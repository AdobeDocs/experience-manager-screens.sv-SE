---
title: Använda dynamisk inbäddad sekvens
description: Lär dig implementera dynamiska inbäddade sekvenser i ditt AEM Screens-projekt.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3208d058-0812-44e1-83e3-b727b384876a
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '2426'
ht-degree: 0%

---

# Använda dynamisk inbäddad sekvens {#using-dynamic-embedded-sequence}

Användning av dynamiska inbäddade sekvenser omfattar följande ämnen:

* **Översikt**
* **Använda dynamisk inbäddad upplevelse i AEM Screens**
* **Visa resultaten**
* **Begränsa användare och ändra åtkomstkontrollistor**

## Ökning {#overview}

***Dynamiska inbäddade sekvenser*** skapas för stora projekt som följer den överordnade-underordnade hierarkin, där den underordnade refereras inuti en platsmapp och inte en kanalmapp. Det gör att användaren kan bädda in en sekvens inuti en kanal med ***Kanalroll***. Det gör att användaren kan definiera platsspecifika platshållare för olika kontor med hjälp av en inbäddad sekvens inuti en huvudkanal.

När du tilldelar en kanal till en visning kan du välja att antingen ange sökvägen för visningen eller rollen för den kanal som tolkas till en faktisk kanal i sitt sammanhang.

Om du vill använda dynamisk inbäddad sekvens tilldelar du en kanal via ***Kanalroll***. Kanalrollen definierar visningssammanhanget. Rollen är inriktad på olika åtgärder och är oberoende av den faktiska kanal som uppfyller rollen. I det här avsnittet beskrivs ett användningsfall som definierar kanaler efter roll och hur du kan tillämpa innehållet på en global kanal. Du kan också se rollen som en identifierare för tilldelningen eller ett alias för kanalen i sammanhanget för den.

### Fördelar med att använda dynamiska inbäddade sekvenser {#benefits-of-using-dynamic-embedded-sequences}

Den största fördelen med att placera en sekvenskanal på en plats i stället för i kanalmappen är att lokala eller regionala författare kan redigera innehåll som är relevant för dem. Allt detta, samtidigt som det inte går att redigera kanaler högre upp i hierarkin.

Referera till en *Kanal efter roll* Med kan du skapa en lokal version av en kanal för att dynamiskt matcha platsspecifikt innehåll och även skapa en global kanal som använder innehållet för de platsspecifika kanalerna.

>[!NOTE]
>
>**Inbäddade sekvenser jämfört med dynamiska inbäddade sekvenser**
>
>En dynamisk inbäddad sekvens liknar en inbäddad sekvens men gör det möjligt för användaren att följa en hierarki där ändringar/uppdateringar som görs i en kanal sprids till en annan i relation till den. Den följer hierarkin för överordnade och underordnade och innehåller även resurser som bilder eller videoklipp.
>
>***Dynamiska inbäddade sekvenser*** gör att du kan visa platsspecifikt innehåll medan ***Inbäddade sekvenser*** bara visa det allmänna bildspelet av innehållet. När du konfigurerar dynamiska inbäddade sekvenser konfigurerar du kanalen med kanalroll och namn. Se stegen nedan för en praktisk implementering.
>
>Mer information om hur du implementerar inbäddade sekvenser finns i [Inbäddade sekvenser](embedded-sequences.md) i AEM Screens.

I följande exempel får du en lösning genom att fokusera på följande nyckeltermer:

* a ***huvudsekvenskanal*** för den globala sekvensen.
* ***dynamisk inbäddad sekvens*** -komponenter för varje lokalt anpassningsbar del av sekvensen.
* ***enskilda sekvenskanaler*** på respektive plats med en *roll* i den visning som matchar **dynamisk inbäddad sekvenskomponent *roll***.

>[!NOTE]
>
>Mer information om kanaltilldelning finns i **[Kanaltilldelning](channel-assignment.md)** under Redigering i AEM Screens-dokumentationen.

## Använda dynamisk inbäddad sekvens {#using-dynamic-embedded-sequence-2}

I följande avsnitt beskrivs hur du skapar en dynamisk inbäddad sekvens i en AEM Screens-kanal.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen måste du se till att du har följande krav på dig att börja implementera dynamiska inbäddade sekvenser:

* Skapa ett AEM Screens-projekt (i det här exemplet **Demo**).
* Skapa en kanal som **Global** under **Kanaler** mapp.
* Lägg till innehåll i **Global** Kanal (*Kontrollera **Resources.zip**för relevanta tillgångar*).

Följande bild visar **Demo** projekt med **Global** kanal in **Kanaler** mapp.
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Resurser {#resources}

Du kan hämta följande resurser (bilder och lägga till dem i resurser) och sedan använda dem som kanalinnehåll för demonstrationssyfte.

[Hämta fil](assets/resources.zip)

>[!NOTE]
>
>Mer information om hur du skapar ett projekt och hur du skapar en sekvenskanal finns i följande resurser:
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
>När du implementerar dynamiska inbäddade sekvenser ska du vara försiktig med **Namn** och **Titel** fält när kanaler skapas under varje plats. Följ instruktionerna på nomenklaturen noga.

1. **Skapa en mapp med två platser.**

   Navigera till **Platser** i ditt AEM Screens-projekt och skapa två platsmappar som **Region A** och **Region B**.

   >[!NOTE]
   >
   >När du skapar **Region A** platsmapp, kontrollera att du anger **Titel** as **Region A** och du kan lämna **Namn** fältet är tomt, så automatiskt **region-a** namnet har hämtats.
   >
   >Liknande är fallet när du skapar en platsmapp **Region B**, enligt nedan:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Mer information om hur du skapar en plats finns i **[Skapa och hantera platser](managing-locations.md)**.

1. **Skapa två platser och en kanal under varje platsmapp.**

   1. Navigera till **Demo** > **Platser** > **Region A**.
   1. Välj **Region A** och klicka **+ Skapa** i åtgärdsfältet.
   1. Välj **Plats** från guiden med **Titel** as **Butik 1**. På samma sätt kan du skapa en annan plats från guiden med namnet som **Butik 2** med **Titel** as **Butik 2**. Du kan lämna **Namn** fältet är tomt när du skapar **Butik 1** och **Butik 2**.
   1. Upprepa steg b och välj nu **Sekvenskanal** från guiden. Ange **Titel** as **Region A** och **Namn** as **region** för den här kanalen.

   >[!CAUTION]
   >
   >Se till att du gör det när du skapar kanal **Region A**, anger **Titel** as **Region A** och **Namn** as **region**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Skapa på samma sätt två platser under **Region B** titled som **Butik 3** och **Butik 4**. Skapa också en **Sekvenskanal** med **Titel** as **Region B** och **Namn** as **region**.

   >[!CAUTION]
   >
   >Se till att du kan använda samma namn för de kanaler som skapas i **Region A** och **Region B** as **region**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Skapa Visning och Kanal under varje plats.**

   1. Navigera till **Demo** > **Platser** > **Region A** > **Butik 1**.
   1. Välj **Butik 1** och klicka **+ Skapa** i åtgärdsfältet.
   1. Välj **Visa** från guiden och skapa **`Store1Display`**.
   1. Upprepa steg b och välj den här gången **Sekvenskanal** från guiden. Ange **Titel** as **`Store1Channel`** och **Namn** as **store**.

   >[!CAUTION]
   >
   >Det är viktigt när du skapar en sekvenskanal, **Titel** av kanalen kan vara vad du behöver, men **Namn** ska vara samma i alla lokala kanaler.
   >I det här exemplet är kanalerna under **Region A** och **Region B** dela **Namn** as **region** och kanaler under **`Store 1`**, **`Store 2`**, **`Store 3`** och **`Store 4`** dela **Namn** as **store**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   På samma sätt kan du skapa en visning som **`Store2Display`** och en kanal **`Store2Channel`** under **`Store `2** (med namn som **store**).

   >[!NOTE]
   >Se till att du kan använda samma namn för de kanaler som skapas i **`Store 1`** och **`Store 2`** as **store**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Följ stegen ovan så att du kan skapa en kanal och visa i **`Store 3`** och **`Store 4`** under **Region B**. Se till att du använder samma **Namn** as **store** när kanal skapades **`Store3Channel`** och **`Store4Channel`** respektive.

   I följande bild visas visningen och kanalen i **`Store 3`**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   I följande bild visas visningen och kanalen i **`Store 4`**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Lägg till innehåll i kanalerna på deras respektive platser.**

   Navigera till **Demo** > **Platser** > **Region A** > **Region A** och klicka **Redigera** i åtgärdsfältet. Dra och släpp de resurser du vill lägga till i kanalen.

   >[!NOTE]
   >Du kan använda ***Resources.zip*** från **Resurs** ovan om du vill använda bilderna som resurser för ditt kanalinnehåll.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Navigera på samma sätt till **Demo** > **Platser** > **Region B** > **Region B** och klicka **Redigera** från åtgärdsfältet för att dra och släppa resurserna i din kanal, vilket visas nedan:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Följ de föregående stegen och resurserna så att du kan lägga till innehåll i följande kanaler:

   * **`Store1Channel`**
   * **`Store2Channel`**
   * **`Store3Channel`**
   * **`Store4Channel`**

1. **Skapa ett schema**

   Navigera och markera **Scheman** i ditt AEM Screens-projekt. Klicka sedan på **Skapa** i åtgärdsfältet.

   Följande bild visar **AdSchedule** som **Demo** projekt.

   ![screen_shot_2018-09-13at3307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Tilldela kanaler till ett schema**

   1. Navigera till **Demo** > **Scheman** > **AdSchedule** och klicka **Kontrollpanel** i åtgärdsfältet.
   1. Klicka **+ Tilldela kanal** från **TILLDELADE KANALER** så att du kan öppna **Kanaltilldelning** -dialogrutan.
   1. Välj **Referenskanal** efter bana.
   1. Välj **Kanalsökväg** as **Demo** > ***Kanaler*** > ***Global***.
   1. Ange **Kanalroll** as **GlobalAdSegment**.
   1. Välj **Händelser som stöds** as **Inledande inläsning**, **Inaktiv skärm** och **Användarinteraktion**.
   1. Klicka **Spara**.

   **Tilldela kanal efter roll för region:**

   1. Klicka **+ Tilldela kanal** från **TILLDELADE KANALER** -panelen.
   1. Välj i dialogrutan Kanaltilldelning **Referenskanal** efter namn.
   1. Ange **Kanalnamn** as **region***.
   1. Ange **Kanalroll** as **RegionAdSegment**.
   1. Klicka **Spara**.

   **Tilldela kanal efter roll för butik:**

   1. Klicka **+ Tilldela kanal** från **TILLDELADE KANALER** -panelen.
   1. Välj i dialogrutan Kanaltilldelning **Referenskanal** efter namn.
   1. Ange **Kanalnamn** as **store**.
   1. Ange **Kanalroll** as **StoreAdSegment**.
   1. Klicka **Spara**.

   I följande bild visas de tilldelade kanalerna per sökväg och roll.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Konfigurerar dynamisk inbäddad sekvens till den globala kanalen.**

   Navigera till **Global** Kanal som du ursprungligen skapade i **Demo** projekt.

   Klicka **Redigera** i åtgärdsfältet.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Dra och släpp två i redigeraren **Dynamisk inbyggd sekvens** i kanalredigeraren.

   Öppna egenskaperna från en av komponenterna och ange **Kanaltilldelningsroll** as **RegionAdSegment**.

   På samma sätt markerar du de andra komponenterna och öppnar egenskaper för att ange **Kanaltilldelningsroll** as **StoreAdSegment**.

   ![channelDisplay4](assets/channeldisplay4.gif)

1. **Tilldela schema till varje skärm**

   1. Navigera till varje visning, till exempel **Demo** > **Platser** > **Region A** >**Butik 1** >**`Store1Display`**.
   1. Klicka **Kontrollpanel** i åtgärdsfältet.
   1. Klicka på **...** från **TILLDELADE KANALER OCH SCHEMAN** och klicka sedan på **+Tilldela schema**.
   1. Välj sökvägen till schemat (till exempel här, **Demo** > **Scheman** > **AdSchedule**).
   1. Klicka **Spara**.

## Visa resultaten {#viewing-the-results}

När du har konfigurerat kanalerna och visningen är klar startar du AEM Screens-spelaren för att visa innehållet.

>[!NOTE]
>
>Mer information om AEM Screens Player finns i följande resurser:
>
>* [Ladda ned AEM Screens Player](https://download.macromedia.com/screens/)
>* [Arbeta med AEM Screens Player](working-with-screens-player.md)


Följande utdata bekräftar ditt kanalinnehåll i AEM Screens Player, beroende på visningssökvägen.

**Scenario 1**:

Om du tilldelar visningssökvägen som **Demo** > **Platser** > **Region A** > **Butik 1** > **`Store1Display`** visas följande innehåll på din AEM Screens-spelare.

![channelDisplay1](assets/channeldisplay1.gif)

**Scenario 1**:

Om du tilldelar visningssökvägen som **Demo** > **Platser** > **Region B** > **Butik 3** > **`Store3Display`** visas följande innehåll på din AEM Screens-spelare.

![channelDisplay2](assets/channeldisplay2.gif)

## Begränsa användare och ändra åtkomstkontrollistor {#restricting-users-and-modifying-the-acls}

Du kan skapa globala, regionala eller lokala författare för att redigera innehåll som är relevant för dem samtidigt som du inte kan redigera kanaler högre upp i hierarkin.

Redigera åtkomstkontrollistorna så att du kan begränsa användarens åtkomst till innehållet baserat på deras plats.

### Exempel på användningsfall {#example-use-case}

I följande exempel kan du skapa tre användare för demonstrationsprojektet ovan.

Följande behörigheter tilldelas varje grupp:

**Grupper**:

* **Global-Author**: Består av användare som har tillgång till alla platser och kanaler i **Demo** och har alla läs-, skriv- och redigeringsbehörigheter.

* **Region-Author**: Består av användare som har läs-, skriv- och redigeringsbehörighet till **Region A** och **Region B**.

* **Store-Author**: Består endast av användare som har läs-, skriv- och redigeringsbehörighet till **Butik 1**, **Butik 2**, **Butik 3** och **Butik 4**.

#### Steg för att skapa användargrupper, användare och konfigurera åtkomstkontrollistor {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Om du vill veta mer om hur du skiljer ut projekt med hjälp av åtkomstkontrollistor så att varje enskild person eller grupp hanterar sitt eget projekt går du till **Konfigurera åtkomstkontrollistor**.

Följ stegen nedan för att skapa grupper, användare och ändra åtkomstkontrollistor enligt behörigheterna:

1. **Skapa grupper**

   1. Navigera till **Adobe Experience Manager**.
   1. Klicka **verktyg** > **Säkerhet** > **Grupper**.
   1. Klicka **Skapa grupp** och ange **Global-Author** in **ID**.
   1. Klicka **Spara och stäng**.

   Skapa på samma sätt två andra grupper, som **Region-Author** och **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Skapa användare och lägga till användare i grupper**

   1. Navigera till **Adobe Experience Manager**.
   1. Klicka **verktyg** > **Säkerhet** > **Användare**.
   1. Klicka **Skapa användare** och ange **Global-användare** in **ID**.
   1. Retur **Lösenord** och bekräfta lösenordet för användaren.
   1. Klicka på **Grupper** och ange gruppnamnet i **Välj grupp**, t.ex. enter **Global-Author** att lägga till **Global-användare** till den specifika gruppen.
   1. Klicka **Spara och stäng**.

   På samma sätt kan du skapa två andra användare, som **Region-användare** och **Butiksanvändare** och lägga till dem i **Region-Author** och **Store-Author** respektive.

   >[!NOTE]
   >Det är en god vana att lägga till användare i en grupp och sedan tilldela behörigheter till varje enskild användargrupp.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Lägg till alla grupper till deltagare**

   1. Navigera till **Adobe Experience Manager**.
   1. Klicka **verktyg** > **Säkerhet** > **Grupper**.
   1. Välj **Medarbetare** i listan och välj **Medlemmar** -fliken.
   1. Välj **Grupp** som **Global-Author**, **Region-Author,** och **Store-Author** till medverkande.
   1. Klicka **Spara och stäng**.

1. **Åtkomst till behörigheter för varje grupp**

   1. Navigera till *Användaradministratör* och använd det här användargränssnittet för att ändra behörigheter för olika grupper.
   1. Sök efter **Global-Author** och klicka **Behörigheter** enligt bilden nedan.
   1. På samma sätt kan du komma åt behörigheterna för **Region-Author** och **Store-Author**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Ändra behörigheter för varje grupp**

   **För global författare:**

   1. Navigera till **Behörigheter** tab
   1. Navigera till ***/content/screens/demo*** och kontrollera alla behörigheter
   1. Navigera till ***/content/screens/demo/locations*** och kontrollera alla behörigheter
   1. Navigera till ***/content/screens/demo/locations/region-a*** och kontrollera alla behörigheter. På samma sätt kontrollerar du behörigheterna för **`region-b`**.

   Se följande bild för att förstå stegen:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   Följande visar att **Global-användare** har åtkomst till **Global Channel** och både **Region A** och **Region B** med alla fyra butikerna, **Butik 1**, **Butik 2**, **Butik 3** och **Butik 4**.

   ![global](assets/global.gif)

   **För Region-Author:**

   1. Navigera till **Behörigheter** -fliken.
   1. Navigera till ***/content/screens/demo*** och bara kontrollera **Läs** behörigheter.
   1. Navigera till ***/content/screens/demo/locations*** och bara kontrollera **Läs** behörigheter.
   1. Navigera till ***/content/screens/demo/channel*** och avmarkera behörigheterna för **Global** kanal.
   1. Navigera till ***/content/screens/demo/locations***/***region-a*** och kontrollera alla behörigheter. På samma sätt kontrollerar du behörigheterna för **`region-b`**.

   Se följande bild så att du kan förstå stegen:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   Följande visar att Region-User har åtkomst till båda **Region A** och **Region B**, med alla fyra butikerna, nämligen **Butik 1**, **Butik 2**, **Butik 3** och **Butik 4**, men har inte åtkomst till **Global** Kanal.

   ![region](assets/region.gif)

   **För Store-Author:**

   1. Navigera till **Behörigheter** -fliken.
   1. Navigera till ***/content/screens/demo*** och bara kontrollera **Läs** behörigheter.
   1. Navigera till ***/content/screens/demo/locations*** och bara kontrollera **Läs** behörigheter.
   1. Navigera till ***/content/screens/demo/channel*** och avmarkera behörigheterna för **Global** kanal.
   1. Navigera till ***/content/screens/demo/locations/region-a*** och bara kontrollera **Läs** behörigheter. På samma sätt bör du bara kontrollera **Läs** behörigheter för **`region-b`**.
   1. Navigera till ***/content/screens/demo/locations***/***region-a /store-1*** och kontrollera alla behörigheter. På samma sätt kontrollerar du behörigheterna för **store-2, store-3,** och **store-4**.

   Se följande bild så att du kan förstå stegen:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   Följande visar att **Butiksanvändare** har endast åtkomst till **Butik 1**, **Butik 2**, **Butik 3** och **Butik 4**, men har inte behörighet att komma åt **Global** eller region (**Region A** och **Region B**) kanaler.

   ![store](assets/store.gif)

>[!NOTE]
>
>Mer information om hur du konfigurerar behörigheter finns i [Konfigurera åtkomstkontrollistor](setting-up-acls.md).
