---
title: Använda Experience Fragments
seo-title: Använda Experience Fragments
description: 'Följ den här sidan om du vill veta mer om hur du använder Experience Fragments i AEM Screens. '
seo-description: 'Följ den här sidan om du vill veta mer om hur du använder Experience Fragments i AEM Screens. '
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Använda Experience Fragments {#using-experience-fragments}

Den här sidan innehåller följande avsnitt:

* **Översikt**
* **Använda upplevelsefragment i AEM-skärmar**
* **Sprider ändringar från mallsidan**

## Översikt {#overview}

Ett ***Experience Fragment*** är en grupp med en eller flera komponenter, inklusive innehåll och layout, som kan refereras till på sidor. Experience fragments kan innehålla alla komponenter, till exempel en eller flera komponenter som kan innehålla vad som helst i ett styckesystem, som refereras till den fullständiga upplevelsen eller begärs av en tredje slutpunkt.


## Använda upplevelsefragment i AEM-skärmar {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>
>I följande exempel används **We.Retail** som ett demoprojekt där Experience Fragment används från en **Sites** -sida till ett AEM Screens-projekt.

I följande arbetsflöde demonstreras användningen av upplevelsefragment från We.Retail i Sites. Du kan välja en webbsida och använda det innehållet i din AEM Screens-kanal i ett av dina projekt.

### Krav {#pre-requisites}

**Skapa ett demoprojekt med en kanal**

***Skapa ett projekt***

1. Klicka på Skärmar och välj **Skapa** —> **Skapa projekt **för att skapa ett nytt projekt.

1. Välj **Skärmar **i guiden **Skapa skärmsprojekt **.

1. Ange titeln som **DemoProject**.
1. Klicka på **Skapa**.

Ett **DemoProject** läggs till på dina AEM-skärmar.  ***Skapa en kanal***

1. Navigera till det **demoprojekt** du har skapat och markera mappen **Kanaler** .

1. Klicka på **Skapa** i åtgärdsfältet (se bilden nedan). En guide öppnas.
1. Välj mallen **Sekvenskanal** i guiden och klicka på **Nästa**.

1. Ange **titeln** som **TestChannel** och klicka på **Skapa**.

En **TestChannel** läggs till i ditt **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)



### Skapa ett upplevelsefragment {#creating-an-experience-fragment}

Följ stegen nedan för att utnyttja innehållet från **We.Retail** till din **TestChannel** i **DemoProject**.

1. **Navigera till en Sites-sida i We.Retail**

   1. Gå till Sites och välj **We.Retail **->** United States **->**English **och välj **Equipment** page för att använda detta som ett upplevelsefragment för din skärmkanal.

   1. Klicka på **Redigera** i åtgärdsfältet för att öppna sidan som du vill använda som ett upplevelsefragment för skärmkanalen.
   ![screen_shot_2018-06-06at105309am](assets/screen_shot_2018-06-06at105309am.png)

1. **Återanvända innehållet**

   1. Markera det fragment som du vill inkludera i kanalen.
   1. Klicka på den sista ikonen till höger för att öppna dialogrutan **Konvertera till upplevelsefragment** .
   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Skapa Experience fragment**

   1. Välj **åtgärden** som **Skapa ett nytt Experience Fragment**.

   1. Markera den **överordnade sökvägen**.
   1. Select the **Template**. Välj mallen **Experience Fragment - Screens Variation **här.

   1. Ange **Fragment Title **as **ScreensFragment**.

   1. Klicka på bockmarkeringen för att slutföra skapandet av ett nytt upplevelsefragment.
   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

1. **Skapa Live Copy of Experience Fragment**

   1. Gå till AEM-startsidan.
   1. Välj **Experience Fragments** och markera **ScreensFragment** och klicka på **Variation som live-copy**, vilket visas i bilden nedan:
   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Välj** ScreensFragment **från** guiden Skapa Live-kopia** och klicka på **Nästa**.

   d. Ange **Rubrik** och **Namn** som **skärmar**.

   e. Klicka på **Skapa** för att skapa Live-kopian.

   f. Klicka på **Klar** för att gå tillbaka till sidan **Skärmfragment** .

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >När du har skapat fragmentet Skärmar kan du redigera egenskaperna för fragmentet. Markera fragmentet och klicka på **Egenskaper** i åtgärdsfältet.

   **Redigera egenskaper för ett skärmsfragment**

   1. Navigera till **ScreensFragment** (du skapade i föregående steg) och klicka på **Egenskaper** i åtgärdsfältet.

   1. Välj fliken **Offlinekonfiguration** , så som visas i bilden nedan.
   Du kan lägga till bibliotek **på** klientsidan (java och css) och **statiska filer** till ditt upplevelsefragment.

   I följande exempel visas hur bibliotek på klientsidan och teckensnitten läggs till som en del av statiska filer i ditt upplevelsefragment.  ![fragment](assets/fragment.gif)

1. **Använda Experience Fragment som en komponent i Skärmkanalen**

   1. Navigera till kanalen Skärmar där du vill använda fragmentet **Skärmar** .
   1. Markera **TestChannel** och klicka på **Redigera** i åtgärdsfältet.

   1. Klicka på komponentikonen på sidofliken.
   1. Dra och släpp **Experience Fragment** i kanalen.
   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Markera **Experience Fragment** -komponenten och markera den övre vänstra (skiftnyckel) ikonen för att öppna dialogrutan **Experience Fragment** .

   f. Markera **skärmens** aktiva kopia av fragmentet som du skapade i *steg 3* i fältet **Sökväg **.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Markera **skärmens** aktiva kopia av fragmentet som du skapade i *steg 3* i fältet **Experience Fragment **.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Ange sekunder i fältet** Varaktighet**.

   i. Välj **Offline Config** i dialogrutan **Experience Fragments** för att definiera bibliotek på klientsidan och statiska filer.

   >[!NOTE]
   >
   >Om du vill lägga till bibliotek på klientsidan eller statiska filer utöver vad du konfigurerade i steg 4, kan du lägga till från fliken **Offlinekonfiguration** i dialogrutan **Experience Fragment** .

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Klicka på bockmarkeringen för att slutföra processen.

### Validerar resultatet {#validating-the-result}

När du har slutfört de föregående stegen kan du validera ditt upplevelsefragment i **ChannelOne** genom att:

1. Navigera till **TestChannel**.
1. Välj **Förhandsgranska** i åtgärdsfältet.

Du kan visa innehållet från **webbplatssidan** (live-copy av upplevelsefragmentet) i din kanal, vilket visas i bilden nedan:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Sprider ändringar från mallsidan {#propagating-changes-from-the-master-page}

***Live-kopia*** refererar till kopian (av källan), som underhålls av synkroniseringsåtgärder enligt definitionen i utrullningskonfigurationerna.

Sedan Experience Fragment har vi skapat en live-kopia från **Sites** -sidorna, så om du gör ändringar i det aktuella fragmentet från mallsidan kan du visa ändringarna i kanalen eller målet där du har använt Experience Fragment.

>[!NOTE]
>
>Mer information om Live Copy finns i Återanvända innehåll: Multi Site Manager och Live Copy.

Följ stegen nedan för att sprida ändringar från huvudkanalen till målkanalen:

1. Välj Experience Fragment på **webbplatssidan** (mallsida) och klicka på pennikonen för att redigera objekten i Experience Fragment.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Välj Experience Fragment och klicka på skiftnyckelsikonen för att öppna dialogrutan för att redigera bilderna.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. Dialogrutan **Produktstödraster** öppnas.

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

1. Navigera till **Skärmar** -> **Kanaler** -> **Testkanal**.

1. Klicka på **Förhandsgranska** i åtgärdsfältet för att bekräfta ändringarna.

Följande bild visar förändringarna i din **TestChannel**:\
![screen_shot_2018-06-08at3351pm](assets/screen_shot_2018-06-08at33351pm.png)
