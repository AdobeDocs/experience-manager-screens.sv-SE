---
title: Textövertäckning
description: Lär dig mer om textövertäckning i AEM Screens där du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# Textövertäckning {#text-overlay}

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Använda textövertäckning**
* **Förstå egenskaper för textövertäckning**
* **Använda ContextHub-värden i textövertäckning**

>[!CAUTION]
>
>Funktionen **Textövertäckning** är bara tillgänglig om du har installerat AEM 6.3 Feature Pack 5 eller AEM 6.4 Feature Pack 3.

## Ökning {#overview}

Textövertäckning är en funktion i AEM Screens. Du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild.

Mer information om hur du skapar en egen anpassad komponent finns i **Utöka en AEM Screens-komponent**.

I det här avsnittet visas bara hur du använder och använder förhandsgranskningskomponenten i ett AEM Screens-projekt. Det visas också hur du använder det som en textövertäckning i en av sekvenskanalerna.

## Använda textövertäckning {#using-text-overlay}

I följande avsnitt beskrivs hur du använder textövertäckning i ett AEM Screens-projekt.

**Förutsättningar**

Innan du implementerar den här funktionen bör du kontrollera att du har konfigurerat ett projekt som en förutsättning för att börja implementera textövertäckning. Exempel:

* Skapa ett AEM Screens-projekt (i det här exemplet **TextOverlayDemo**)

* Skapa en sekvenskanal med namnet **TextSample** i mappen **Channels**

* Lägg till innehåll i din **TextSample**-kanal

Följande bild visar **TextOverlayDemo** -projektet med **TextSample** -kanalen i mappen **Channels** .

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Följ stegen nedan för att använda textövertäckning i en AEM Screens-kanal:

1. Navigera till **TextOverlayDemo** > **Kanaler** > **TextSample** och klicka på **Redigera** i åtgärdsfältet.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Klicka på bilden och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan för egenskaper.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Klicka på alternativet **Textövertäckning** i navigeringsfältet i dialogrutan, vilket visas i bilden nedan.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Förstå egenskaper för textövertäckning {#understanding-text-overlay-properties}

Med hjälp av egenskaperna för textövertäckning kan du lägga till text i någon av komponenterna i ditt Screens-projekt. I följande avsnitt ges en översikt över de egenskaper som är tillgängliga i Textövertäckning:

![text](assets/text.gif)

Du kan lägga till en text i textrutan och lägga till typografisk betoning som fet, kursiv och understrykning.

**Färgvariant** Med det här alternativet kan texten antingen vara mörk (text i svart färg) eller Ljus (text i vit färg).

**Storlek och placering** Med det här alternativet kan användaren justera texten vågrätt eller lodrätt eller också använda finkorniga verktyg för textjustering.

>[!NOTE]
>
>När du använder finkorniga verktyg måste du se till att identifiera rätt position i pixlar med (px) som suffix, till exempel 200 px. Resultatet av det här uttrycket är 200 pixlar från startpunkten.

## Använda ContextHub-värden i textövertäckning {#using-text-overlay-context-hub}

I följande avsnitt beskrivs användningen av värden från ett datalager, till exempel Google sheets i textövertäckningskomponenten.

**Förutsättningar**

Konfigurera ContextHub för ditt AEM Screens-projekt.

Mer information om hur du konfigurerar och hanterar datadrivna resursändringar med ett datalager finns i [Konfigurera ContextHub i AEM Screens](https://experienceleague.adobe.com/sv/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

När du har ställt in de konfigurationer som krävs för ditt projekt följer du stegen nedan för att använda värden från Google Sheets:

1. Navigera till **TextOverlayDemo** > **Kanaler** > **TextSample** och klicka på **Egenskaper** i åtgärdsfältet.

1. Klicka på fliken **Personalization** så att du kan konfigurera ContextHub-konfigurationer.

   1. Klicka på **ContextHub Path** som **libs** > **settings** > **cloudssettings** > **default** > **ContextHub Configurations** och klicka på **Select**.

   1. Klicka på **Segmentbanan** som **conf** > **screens** > **settings** > **wcm** > **segments** och klicka på **Markera**.

   1. Klicka på **Spara och stäng**.

      >[!NOTE]
      >
      >Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

      ![bild1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Navigera till **TextOverlayDemo** > **Kanaler** > **TextSample** och klicka på **Redigera** i åtgärdsfältet.

   ![bild1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Lägg till en bild- och textöverläggskomponent i bilden enligt beskrivningen i avsnittet [Använda textövertäckning](/help/user-guide/text-overlay.md#using-text-overlay) på den här sidan.

1. Klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan **Bild** .

   ![bild1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Gå till fliken **ContextHub** i dialogrutan **Bild**. Klicka på **Lägg till**.

   >[!NOTE]
   >Om du inte har konfigurerat din ContextHub-konfiguration inaktiveras det här alternativet för ditt projekt.

1. Ange **Värde** i fältet **Platshållare**. Klicka på raden som du vill hämta värdet från ditt Google-blad i **ContextHub-variabeln**. I det här fallet hämtas värdet från rad 2 och kolumn 1 från Google-bladen. Ange nu **standardvärdet** som **20**, vilket visas i figuren nedan. När du är klar klickar du på bockmarkeringen.

   ![bild1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Följande bild visar det värde som hämtas från Google Sheets:

   ![bild1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Gå tillbaka till fliken **Textövertäckning** i dialogrutan Bild och lägg till texten *Aktuell temperatur {Value}* enligt bilden nedan.

   ![bild1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Klicka på **Förhandsgranska**.

   ![bild1](/help/user-guide/assets/text-overlay/text-overlay10.png)
