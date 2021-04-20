---
title: Textövertäckning
seo-title: Textövertäckning
description: Textövertäckning är en funktion i AEM Screens som gör att du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild. Följ den här sidan om du vill veta mer.
seo-description: Textövertäckning är en funktion i AEM Screens som gör att du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild. Följ den här sidan om du vill veta mer.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 1%

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

## Översikt {#overview}

Textövertäckning är en funktion i AEM Screens som gör att du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild.

Mer information om hur du skapar en egen anpassad komponent finns i **Utöka en AEM Screens-komponent**.

I det här avsnittet visas bara hur du använder och drar nytta av filmminiatyrkomponenten i ett AEM Screens-projekt och använder den som textövertäckning i en av sekvenskanalerna.

## Använda textövertäckning {#using-text-overlay}

I följande avsnitt beskrivs hur du använder textövertäckning i ett AEM Screens-projekt.

**Förutsättningar**

Innan du börjar implementera den här funktionen bör du kontrollera att du har konfigurerat ett projekt som en förutsättning för att börja implementera textövertäckning. Till exempel,

* Skapa ett AEM Screens-projekt (i det här exemplet **TextOverlayDemo**)

* Skapa en sekvenskanal med namnet **TextSample** under **Kanaler** mapp

* Lägg till innehåll i din **TextSample**-kanal

Följande bild visar **TextOverlayDemo**-projektet med **TextSample**-kanalen i **kanalmappen**.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Följ stegen nedan för att använda textövertäckning i en AEM Screens-kanal:

1. Navigera till **TextOverlayDemo** —> **Kanaler** —> **TextSample** och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Markera bilden och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan för egenskaper.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Välj alternativet **Textövertäckning** i navigeringsfältet i dialogrutan, vilket visas i bilden nedan.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Förstå egenskaper för textövertäckning {#understanding-text-overlay-properties}

Med egenskaperna för textövertäckning kan du lägga till text i valfri komponent i skärmsprojektet. I följande avsnitt ges en översikt över de egenskaper som är tillgängliga i Textövertäckning:

![text](assets/text.gif)

Du kan lägga till en text i textrutan och lägga till typografisk betoning som fet, kursiv stil, understrykning och så vidare.

**Färgvariant** Med det här alternativet kan texten antingen vara mörk (text i svart färg) eller Ljus (text i vit färg).

**Storlek och** placeringMed det här alternativet kan användaren justera texten vågrätt eller lodrätt eller dessutom använda finkorniga verktyg för textjustering.

>[!NOTE]
>
>Om du vill använda finkorniga verktyg på rätt sätt måste du se till att identifiera rätt position i pixlar med (px) som suffix, till exempel 200px. Resultatet av det här uttrycket blir 200 pixlar från startpunkten.

## Använda ContextHub-värden i textövertäckning {#using-text-overlay-context-hub}

I följande avsnitt beskrivs användningen av värden från ett datalager, till exempel Google sheets i textövertäckningskomponenten.

**Förutsättningar**

Du måste konfigurera ContextHub-konfigurationer för ditt AEM Screens-projekt.

Mer information om hur du konfigurerar och hanterar datadrivna resursändringar med ett datalager finns i [Konfigurera ContextHub i AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

När du har ställt in de konfigurationer som krävs för ditt projekt följer du stegen nedan för att använda värden från Google Sheets:

1. Navigera till **TextOverlayDemo** —> **Kanaler** —> **TextSample** och klicka på **Egenskaper** i åtgärdsfältet.

1. Välj fliken **Personalisering** för att konfigurera ContextHub-konfigurationer.

   1. Välj **ContextHub-sökvägen** som **libs** > **inställningar** > **molninställningar** > **standard** > **ContextHub Configurations** och klicka på &lt;a 12/>Välj **.**

   1. Välj **Segmentsökväg** som **conf** > **skärmar** > **inställningar** > **wcm** > **segment** och klicka på **Markera&lt;a1 3/>.**

   1. Klicka på **Spara och stäng**.

      >[!NOTE]
      >
      >Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Navigera till **TextOverlayDemo** —> **Kanaler** —> **TextSample** och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Lägg till en bild- och textövertäckningskomponent i bilden enligt beskrivningen i [Använda textövertäckning](/help/user-guide/text-overlay.md#using-text-overlay) på den här sidan.

1. Klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan **Bild**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Gå till fliken **ContextHub** i dialogrutan **Bild**. Klicka på **Lägg till**.

   >[!NOTE]
   >Om du inte har konfigurerat dina ContextHub-konfigurationer inaktiveras det här alternativet för ditt projekt.

1. Ange **Värde** i fältet **Platshållare** och markera raden som du vill hämta värdet från Google Sheet i **ContextHub-variabel** (i det här fallet hämtas värdet från rad 2 och kolumn 1 från Google Sheets) och ange **Standardvärde** som **20**, vilket visas i figuren nedan. När du är klar klickar du på bockmarkeringen.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Följande bild visar det värde som hämtas från Google Sheets:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Gå tillbaka till fliken **Textövertäckning** i dialogrutan Bild och lägg till texten *Aktuell temperatur {Value}*, som bilden nedan visar.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Klicka på **Förhandsgranska** för att visa önskat utvärde.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)















