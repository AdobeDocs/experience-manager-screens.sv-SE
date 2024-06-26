---
title: Använda upplevelsefragment
description: Läs om hur du använder Experience Fragments i AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 0%

---

# Använda upplevelsefragment {#using-experience-fragments}

Den här sidan innehåller följande avsnitt:

* **Översikt**
* **Använda Experience Fragments i AEM Screens**
* **Sprider ändringar på sidan**

## Ökning {#overview}

An ***Experience Fragment*** är en grupp med en eller flera komponenter, inklusive innehåll och layout, som kan refereras till på sidor. Experience Fragments kan innehålla alla komponenter. Den kan till exempel innehålla en eller flera komponenter som kan innehålla vad som helst i ett styckesystem som refereras till den fullständiga upplevelsen eller som begärs av en tredje slutpunkt.


## Använda Experience Fragments i AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>I följande exempel används **`We.Retail`** som ett demoprojekt varifrån Experience Fragment tillämpas från en **Webbplatser** till ett AEM Screens-projekt.

I följande arbetsflöde visas hur du använder Experience Fragments från `We.Retail` i Sites. Du kan välja en webbsida och använda det innehållet i din AEM Screens-kanal i något av dina projekt.

### Krav {#pre-requisites}

**Skapa ett demonstrationsprojekt med en kanal**

***Skapa ett projekt***

1. Skapa ett projekt genom att klicka på **Skapa skärmsprojekt**.
1. Ange titeln som **DemoProject**.
1. Klicka **Spara**.

A **DemoProject** läggs till i din AEM Screens.

***Skapa en kanal***

1. Navigera till **DemoProject** du har skapat och klickar på **Kanaler** mapp.

1. Klicka **Skapa** i åtgärdsfältet så att du kan öppna guiden.
1. Välj **Sekvenskanal** mall från guiden och klicka på **Nästa**.

1. Ange **Titel** as **TestChannel** och klicka **Skapa**.

A **TestChannel** läggs till i **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Skapa ett upplevelsefragment {#creating-an-experience-fragment}

Följ stegen nedan för att tillämpa innehållet från **`We.Retail`** till **TestChannel** in **DemoProject**.

1. **Navigera till en Sites-sida i We.Retail**

   1. Navigera till platser och klicka på **`We.Retail`** > **Amerikas förenta stater** > **Engelska** > **Utrustning** och klicka på den här sidan så att du kan använda den som en Experience Fragment för din skärmkanal.

   1. Klicka **Redigera** i åtgärdsfältet så att du kan öppna sidan som du vill använda som Experience Fragment för din skärmkanal.

1. **Återanvända innehåll**

   1. Klicka på det fragment som du vill inkludera i kanalen.
   1. Klicka på den sista ikonen till höger så att du kan öppna **Konvertera till Experience Fragment** -dialogrutan.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Skapa ett upplevelsefragment**

   1. Välj **Åtgärd** as **Skapa ett nytt Experience Fragment**.

   1. Klicka på **Överordnad sökväg**.
   1. Klicka på **Mall**. Välj **Experience Fragment - skärmvariationer** mall här (värde i fältet) `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Ange **Fragmenttitel** as **SkärmarFragment**.

   1. Klicka på bockmarkeringen för att slutföra skapandet av ett nytt Experience Fragment.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Om du vill välja ett enklare alternativ klickar du på bockmarkeringen till höger om fältet så att du kan öppna valdialogrutan.

1. **Skapa Live Copy of Experience Fragment**

   1. Navigera till AEM startsida.
   1. Klicka **Upplevelsefragment** och markera **SkärmarFragment** och klicka **Variation som live-copy**, vilket visas i figuren nedan:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Klicka på **SkärmarFragment** från **Skapa Live Copy** guide och klicka **Nästa**.

   d. Ange **Titel** och **Namn** as **Skärmar**.

   e. Klicka **Skapa** så att du kan skapa en Live-kopia.

   f. Klicka på **Klar** så att du kan gå tillbaka till **SkärmarFragment** sida.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >När du har skapat ett AEM Screens-fragment kan du redigera egenskaperna för fragmentet. Klicka på fragmentet och klicka på **Egenskaper** i åtgärdsfältet.

   **Redigera egenskaper för ett skärmsfragment**

   1. Navigera till **SkärmarFragment** (du skapade i föregående steg) och klicka på **Egenskaper** i åtgärdsfältet.

   1. Klicka på **Offlinekonfiguration** enligt bilden nedan.

   Du kan lägga till **Bibliotek på klientsidan** (Java™ och CSS) och **Statiska filer** till er Experience Fragment.

   I följande exempel visas hur bibliotek på klientsidan och teckensnitten läggs till som en del av statiska filer i Experience Fragment.  ![fragment](assets/fragment.gif)

1. **Använda Experience Fragment som en komponent i Skärmkanalen**

   1. Navigera till kanalen Skärmar där du vill använda **Skärmar** fragment.
   1. Klicka på **TestChannel** och klicka **Redigera** i åtgärdsfältet.

   1. Klicka på komponentikonen på sidofliken.
   1. Dra och släpp **Experience Fragment** till er kanal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Klicka på **Experience Fragment** och klicka på ikonen längst upp till vänster (skiftnyckel) så att du kan öppna **Experience Fragment** -dialogrutan.

   f. Klicka på **Skärmar** Live-kopia av fragmentet som du skapade i *Steg 3* in **Bana**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Klicka på **Skärmar** Live-kopia av fragmentet som du skapade i *Steg 3* i **Experience Fragment**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Ange millisekunder i **Varaktighet**.

   i. Klicka på **Offlinekonfiguration** från **Upplevelsefragment** så att du kan definiera bibliotek på klientsidan och statiska filer.

   >[!NOTE]
   >
   >Om du vill lägga till bibliotek på klientsidan eller statiska filer utöver vad du konfigurerade i steg 4 kan du lägga till från **Offlinekonfiguration** i **Experience Fragment** -dialogrutan.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Klicka på bockmarkeringen så att du kan slutföra processen.

### Validerar resultatet {#validating-the-result}

När du har slutfört de föregående stegen kan du validera din Experience Fragment i **ChannelOne** av:

1. Navigera till **TestChannel**.
1. Markera **Förhandsgranska** i åtgärdsfältet.

Visa innehållet från **Webbplatser** sida (live-copy av Experience Fragment) i din kanal, vilket visas i bilden nedan:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Sprider ändringar på sidan {#propagating-changes-from-the-master-page}

***Live Copy*** refererar till kopian (av källan), som underhålls av synkroniseringsåtgärder som definieras av rollout-konfigurationerna.

Eftersom den Experience Fragment du skapade är en Live-kopia från **Webbplatser** -sidor, och du ändrar det särskilda fragmentet från den primära sidan, kan du visa ändringarna i din kanal. Eller så kan du visa målet där du har använt Experience Fragment.

>[!NOTE]
>
>Mer information om Live Copy finns i Återanvända innehåll: Multisite Manager och Live Copy.

Följ stegen nedan för att sprida ändringar från den primära kanalen till målkanalen:

1. Klicka på Experience Fragment på menyn **Webbplatser** (primär) och klicka på pennikonen så att du kan redigera objekten i Experience Fragment.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Klicka på Experience Fragment och klicka på skiftnyckelsikonen så att du kan öppna dialogrutan för att redigera bilderna.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. The **Produktstödraster** öppnas.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. Du kan redigera alla bilder. Här ersätts t.ex. den första bilden i det här avsnittet.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Klicka på Experience Fragment och klicka på ikonen Rollout så att du kan sprida ändringarna till det fragment som används i din kanal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Klicka på Överrullning.

   Observera att ändringarna introduceras.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validerar ändringarna {#validating-the-changes}

Följ stegen nedan för att bekräfta ändringarna i din kanal:

1. Navigera till **Skärmar** > **Kanaler** > **TestChannel**.

1. Klicka **Förhandsgranska** i åtgärdsfältet.

Följande bild visar ändringarna i **TestChannel**:\
![screen_shot_2018-06-08at3351pm](assets/screen_shot_2018-06-08at33351pm.png)
