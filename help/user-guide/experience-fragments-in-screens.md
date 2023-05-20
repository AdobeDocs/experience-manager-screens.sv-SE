---
title: Använda Experience Fragments
seo-title: Using Experience Fragments
description: Följ den här sidan om du vill veta mer om hur du använder Experience Fragments i AEM Screens.
seo-description: Follow this page to learn about using Experience Fragments in AEM Screens.
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 0%

---

# Använda Experience Fragments {#using-experience-fragments}

Den här sidan innehåller följande avsnitt:

* **Översikt**
* **Använda Experience Fragments i AEM Screens**
* **Sprider ändringar på sidan**

## Översikt {#overview}

An ***Experience Fragment*** är en grupp med en eller flera komponenter, inklusive innehåll och layout, som kan refereras till på sidor. Experience fragments kan innehålla alla komponenter, till exempel en eller flera komponenter som kan innehålla vad som helst i ett styckesystem, som refereras till den fullständiga upplevelsen eller begärs av en tredje slutpunkt.


## Använda Experience Fragments i AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>I följande exempel används **Vi.butik** som ett demoprojekt från vilket Experience Fragment utnyttjas från en **Webbplatser** till ett AEM Screens-projekt.

I följande arbetsflöde demonstreras användningen av upplevelsefragment från We.Retail i Sites. Du kan välja en webbsida och använda det innehållet i din AEM Screens-kanal i något av dina projekt.

### Krav {#pre-requisites}

**Skapa ett demonstrationsprojekt med en kanal**

***Skapa ett projekt***

1. Klicka **Skapa skärmsprojekt** för att skapa ett nytt projekt.
1. Ange titeln som **DemoProject**.
1. Klicka **Spara**.

A **DemoProject** läggs till i din AEM Screens.

***Skapa en kanal***

1. Navigera till **DemoProject** du skapade och väljer **Kanaler** mapp.

1. Klicka **Skapa** i åtgärdsfältet för att öppna guiden.
1. Välj **Sekvenskanal** mall från guiden och klicka på **Nästa**.

1. Ange **Titel** as **TestChannel** och klicka **Skapa**.

A **TestChannel** läggs till i **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Skapa ett upplevelsefragment {#creating-an-experience-fragment}

Följ stegen nedan för att återanvända innehållet från **Vi.butik** till **TestChannel** in **DemoProject**.

1. **Navigera till en Sites-sida i We.Retail**

   1. Navigera till Platser och välj **Vi.butik** -> **Amerikas förenta stater** -> **Engelska** -> **Utrustning** och väljer den här sidan om du vill använda den som ett upplevelsefragment för din skärmkanal.

   1. Klicka **Redigera** från åtgärdsfältet för att öppna sidan som du vill använda som ett upplevelsefragment för din skärmkanal.

1. **Återanvända innehållet**

   1. Markera det fragment som du vill inkludera i kanalen.
   1. Klicka på den sista ikonen till höger för att öppna **Konvertera till upplevelsefragment** -dialogrutan.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Skapa Experience fragment**

   1. Välj **Åtgärd** as **Skapa ett nytt Experience Fragment**.

   1. Välj **Överordnad sökväg**.
   1. Välj **Mall**. Välj **Experience Fragment - skärmvariationer** mall här (värde i fältet) `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Ange **Fragmenttitel** as **SkärmarFragment**.

   1. Klicka på bockmarkeringen för att slutföra skapandet av ett nytt upplevelsefragment.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Obs! Om du vill välja ett enklare alternativ klickar du på bockmarkeringen till höger om fälten för att öppna urvalsdialogrutan.

1. **Skapa Live Copy of Experience Fragment**

   1. Navigera till AEM startsida.
   1. Välj **Upplevelsefragment** och markera **SkärmarFragment** och klicka **Variation som live-copy**, vilket visas i figuren nedan:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Välj **SkärmarFragment** från **Skapa Live Copy** guide och klicka **Nästa**.

   d. Ange **Titel** och **Namn** as **Skärmar**.

   e. Klicka **Skapa** för att skapa Live Copy.

   f. Klicka **Klar** för att gå tillbaka till **SkärmarFragment** sida.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >När du har skapat fragmentet Skärmar kan du redigera egenskaperna för fragmentet. Markera fragmentet och klicka på **Egenskaper** i åtgärdsfältet.

   **Redigera egenskaper för ett skärmsfragment**

   1. Navigera till **SkärmarFragment** (du skapade i föregående steg) och klicka på **Egenskaper** i åtgärdsfältet.

   1. Välj **Offlinekonfiguration** enligt bilden nedan.

   Du kan lägga till **Bibliotek på klientsidan** (java och css) och **Statiska filer** till ert upplevelsefragment.

   I följande exempel visas hur bibliotek på klientsidan och teckensnitten läggs till som en del av statiska filer i ditt upplevelsefragment.  ![fragment](assets/fragment.gif)

1. **Använda Experience Fragment som en komponent i Skärmkanalen**

   1. Navigera till kanalen Skärmar där du vill använda **Skärmar** fragment.
   1. Välj **TestChannel** och klicka **Redigera** i åtgärdsfältet.

   1. Klicka på komponentikonen på sidofliken.
   1. Dra och släpp **Experience Fragment** till er kanal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Välj **Experience Fragment** och välj ikonen längst upp till vänster (skiftnyckel) för att öppna **Experience Fragment** -dialogrutan.

   f. Välj **Skärmar** live copy av fragmentet du skapade i *Steg 3* in **Bana**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Välj **Skärmar** live copy av fragmentet du skapade i *Steg 3* i **Experience Fragment**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Ange millisekunder i **Varaktighet**.

   i. Välj **Offlinekonfiguration** från **Upplevelsefragment** för att definiera bibliotek på klientsidan och statiska filer.

   >[!NOTE]
   >
   >Om du vill lägga till bibliotek på klientsidan eller statiska filer utöver vad du konfigurerade i steg 4 kan du lägga till från **Offlinekonfiguration** i **Experience Fragment** -dialogrutan.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Klicka på bockmarkeringen för att slutföra processen.

### Validerar resultatet {#validating-the-result}

När du är klar med de föregående stegen kan du validera ditt upplevelsefragment i **ChannelOne** av:

1. Navigera till **TestChannel**.
1. Markera **Förhandsgranska** i åtgärdsfältet.

Du kan visa innehållet från **Webbplatser** sida (live-copy av upplevelsefragmentet) i din kanal, vilket visas i bilden nedan:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Sprider ändringar på sidan {#propagating-changes-from-the-master-page}

***Live Copy*** refererar till kopian (av källan), som underhålls av synkroniseringsåtgärder som definieras av rollout-konfigurationerna.

Sedan Experience Fragment skapade vi en live-kopia från **Webbplatser** sidor, så om du gör ändringar i det aktuella avsnittet från den överordnad sidan, kommer du att se ändringarna i kanalen eller målet där du har använt Experience Fragment.

>[!NOTE]
>
>Mer information om Live Copy finns i Återanvända innehåll: Multi Site Manager och Live Copy.

Följ stegen nedan för att sprida ändringar från den överordnad kanalen till målkanalen:

1. Välj Experience Fragment på menyn **Webbplatser** (överordnad) och klicka på pennikonen för att redigera objekten i Experience Fragment.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Välj Experience Fragment och klicka på skiftnyckelsikonen för att öppna dialogrutan för att redigera bilderna.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. The **Produktstödraster** öppnas.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. Du kan redigera alla bilder. Här ersätts t.ex. den första bilden i det här avsnittet.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Välj Experience Fragment och klicka på ikonen Rollout för att sprida ändringarna till det fragment som används i din kanal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Klicka på Överrullning för att bekräfta ändringarna.

   Du ser att ändringarna har rullats ut.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validerar ändringarna {#validating-the-changes}

Följ stegen nedan för att bekräfta ändringarna i din kanal:

1. Navigera till **Skärmar** -> **Kanaler** -> **TestChannel**.

1. Klicka **Förhandsgranska** i åtgärdsfältet för att bekräfta ändringarna.

Följande bild visar ändringarna i **TestChannel**:\
![screen_shot_2018-06-08at3351pm](assets/screen_shot_2018-06-08at33351pm.png)
