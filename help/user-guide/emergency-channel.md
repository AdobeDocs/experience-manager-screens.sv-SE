---
title: Nödkanal
description: Lär dig hur du skapar och hanterar en nödkanal som innehållsförfattaren kan växla från en sekvenskanal om det finns ett förhandsvillkor.
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Nödkanal {#emergency-channel}

## Använd fallbeskrivning {#use-case-description}

I det här avsnittet beskrivs ett exempel på ett användningsfall. Det betonar att man ska skapa och hantera en nödkanal som innehållsförfattaren kan växla från en sekvenskanal, om det finns ett förhandsvillkor.

### Förhandsvillkor {#preconditions}

Innan du börjar med det här användningsexemplet måste du förstå hur du gör:

* **[Skapa och hantera kanaler](managing-channels.md)**
* **[Skapa och hantera platser](managing-locations.md)**
* **[Skapa och hantera scheman](managing-schedules.md)**
* **[Enhetsregistrering](device-registration.md)**

### Primära aktörer {#primary-actors}

Innehållsförfattare

## Grundläggande flöde: Konfigurera projektet {#basic-flow-setting-up-the-project}

Följ stegen nedan för att konfigurera en nödkanal:

1. Skapa ett AEM Screens-projekt med namnet **EmergencyChannel**, vilket visas nedan.

   >[!NOTE]
   >Mer information om hur du skapar och hanterar projekt i AEM Screens finns i Skapa ett projekt.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Skapa en sekvenskanal**

   1. Klicka på **Kanaler** mapp och klicka på **Skapa**.

   1. Klicka **Sekvenskanal** från guiden och skapa kanalen som **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Lägga till innehåll i sekvenskanalen**

   1. Klicka på kanalen (**MainAdChannel**).
   1. Klicka **Redigera** i åtgärdsfältet.
   1. Dra och släpp några resurser i kanalen.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Skapa en nödkanal**

   1. Klicka på **Kanaler** mapp.
   1. Klicka **Skapa**.
   1. Klicka **Sekvenskanal** från guiden och skapa kanalen som **EmergencyChannel**.

   >[!NOTE]
   >
   >Normalt läggs din nödkanal till i ditt befintliga produktionsprojekt.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Lägga till innehåll i en nödkanal**

   1. Klicka på kanalen (**Nödkanal)**.
   1. Klicka **Redigera** i åtgärdsfältet.
   1. Dra och släpp den resurs du vill köra i en nödsituation till kanalen.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Skapa en plats**

   1. Navigera till **Platser** mapp.
   1. Klicka **Skapa** i åtgärdsfältet och skapa en plats med namnet **Butik** från guiden.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Skapar bildskärmar på din plats**

   Navigera till din plats (**Butik**) och klicka på **Skapa** i åtgärdsfältet. Skapa två efter guiden **Visar** titled som **StoreFront** och **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Skapa ett schema**

   1. Navigera till **Scheman** mapp.
   1. Klicka **Skapa** i åtgärdsfältet.
   1. Skapa ett schema som heter som efter guiden **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Tilldela båda skärmarna till ditt schema och ange prioriteter

   1. Klicka på schemat **(StoreSchedule)** och klicka **Kontrollpanel** i åtgärdsfältet.

   1. Klicka **+ Tilldela kanal** från **TILLDELADE KANALER** -panelen.

   1. Från **Kanaltilldelning** dialogruta:

      1. Klicka på banan till **MainAdChannel**
      1. Ange **Prioritet** as 2
      1. Ange händelser som stöds som **Inledande inläsning** och **Inaktiv skärm**.
      1. Klicka **Spara**

      Följ samma steg igen för att tilldela **EmergencyChannel** och ange **Prioritet**.

   >[!NOTE]
   >
   >Prioritet används för att ordna tilldelningarna om flera matchar uppspelningsvillkoren. Den som har det högsta värdet har alltid företräde framför de lägre värdena.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Klicka **+ Tilldela kanal** från **TILLDELADE KANALER** -panelen.

1. Från **Kanaltilldelning** dialogruta:

   1. Klicka på banan till **EmergencyChannel**
   1. Ange **Prioritet** som 1

   1. Ange händelser som stöds som **Inledande inläsning**, **Inaktiv skärm** och **Användarinteraktion**

   1. Klicka **Spara**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Du kan visa de tilldelade kanalerna från **StoreSchedule** kontrollpanel.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Tilldela schema till varje skärm**

   1. Navigera till varje visning, till exempel **EmergencyChannel** > **Platser** > **Butik** >**StoreFront**.

   1. Klicka **Kontrollpanel** i åtgärdsfältet.
   1. Klicka **...** från **TILLDELADE KANALER OCH SCHEMAN** panel och ytterligare klicka **+Tilldela schema**.

   1. Klicka på sökvägen till schemat (till exempel här, **EmergencyChannel** > **Scheman** >**StoreSchedule**).

   1. Klicka **Spara**.

   Du kan visa det tilldelade schemat för visningen från **StoreSchedule** kontrollpanel.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Enhetsregistrering**

   Slutför registreringsprocessen. När du har registrerat dig kan du visa följande utdata i din AEM Screens Player.

   ![new30](assets/new30.gif)

## Växla till nödkanal {#switching-to-emergency-channel}

Utför följande steg om det uppstår en kris:

1. Navigera till **EmergencyChannel** > **Scheman** > **StoreSchedule** och klicka **Kontrollpanel** i åtgärdsfältet.

   ![screen_shot_2019-02-25at10112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Klicka på **EmergencyChannel** från **StoreSchedule** kontrollpanel och klicka på **Redigera uppdrag**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Uppdatera **Prioritet** i **EmergencyChannel** till **3** från **Kanaltilldelning** och klicka **Spara**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. När kanalens prioritet uppdateras visas den **EmergencyChannel** innehåll.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Slutsats {#conclusion}

The **EmergencyChannel** fortsätter att visa innehållet tills innehållsförfattaren återställer prioritetsvärdet till 1.

När innehållsförfattaren får instruktionerna om att nödläget har åtgärdats bör de uppdatera prioriteten för **MainAdChannel**. Om du gör det återupptas den normala uppspelningen.
