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
>The **Textövertäckning** Funktionen är bara tillgänglig om du har AEM 6.3 Feature Pack 5 eller AEM 6.4 Feature Pack 3.

## Ökning {#overview}

Textövertäckning är en funktion i AEM Screens. Du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild.

Mer information om hur du skapar en egen anpassad komponent finns i **Utöka en AEM Screens-komponent**.

I det här avsnittet visas bara hur du använder och använder förhandsgranskningskomponenten i ett AEM Screens-projekt. Det visas också hur du använder det som en textövertäckning i en av sekvenskanalerna.

## Använda textövertäckning {#using-text-overlay}

I följande avsnitt beskrivs hur du använder textövertäckning i ett AEM Screens-projekt.

**Förutsättningar**

Innan du implementerar den här funktionen bör du kontrollera att du har konfigurerat ett projekt som en förutsättning för att börja implementera textövertäckning. Exempel:

* Skapa ett AEM Screens-projekt (i det här exemplet **TextOverlayDemo**)

* Skapa en sekvenskanal med namnet **TextExempel** under **Kanaler** mapp

* Lägg till innehåll i **TextExempel** Kanal

Följande bild visar **TextOverlayDemo** projektet med **TextExempel** i **Kanaler** mapp.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Följ stegen nedan för att använda textövertäckning i en AEM Screens-kanal:

1. Navigera till **TextOverlayDemo** > **Kanaler** > **TextExempel** och klicka **Redigera** i åtgärdsfältet.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Klicka på bilden och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan Egenskaper.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Klicka på **Textövertäckning** i navigeringsfältet i dialogrutan, vilket visas i bilden nedan.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Förstå egenskaper för textövertäckning {#understanding-text-overlay-properties}

Med hjälp av egenskaperna för textövertäckning kan du lägga till text i någon av komponenterna i skärmprojektet. I följande avsnitt ges en översikt över de egenskaper som är tillgängliga i Textövertäckning:

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

Mer information om hur du konfigurerar och hanterar datadrivna resursändringar med hjälp av ett datalager finns i [ContextHub konfigureras i AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

När du har ställt in de konfigurationer som krävs för ditt projekt följer du stegen nedan för att använda värden från Google Sheets:

1. Navigera till **TextOverlayDemo** > **Kanaler** > **TextExempel** och klicka **Egenskaper** i åtgärdsfältet.

1. Klicka på **Personalisering** så att du kan konfigurera ContextHub-konfigurationer.

   1. Klicka på **ContextHub-sökväg** as **libs** > **inställningar** > **molninställningar** > **standard** > **ContextHub-konfigurationer** och klicka **Välj**.

   1. Klicka på **Segmentsökväg** as **conf** > **skärmar** > **inställningar** > **wcm** > **segment** och klicka **Välj**.

   1. Klicka **Spara och stäng**.

      >[!NOTE]
      >
      >Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Navigera till **TextOverlayDemo** > **Kanaler** > **TextExempel** och klicka **Redigera** i åtgärdsfältet.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Lägga till en bild- och textövertäckningskomponent i bilden enligt beskrivningen i [Använda textövertäckning](/help/user-guide/text-overlay.md#using-text-overlay) på den här sidan.

1. Klicka på **Konfigurera** (skiftnyckelsikon) för att öppna **Bild** -dialogrutan.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Navigera till **ContextHub** -fliken från **Bild** -dialogrutan. Klicka **Lägg till**.

   >[!NOTE]
   >Om du inte har konfigurerat din ContextHub-konfiguration inaktiveras det här alternativet för ditt projekt.

1. Retur **Värde** i **Platshållare** fält. Klicka på raden där du vill hämta värdet från Google-bladet i **ContextHub-variabel**. I det här fallet hämtas värdet från rad 2 och kolumn 1 från Google-bladen. Nu kan du **Standardvärde** as **20**, vilket visas i bilden nedan. När du är klar klickar du på bockmarkeringen.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Följande bild visar det värde som hämtas från Google Sheets:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Navigera tillbaka till **Textövertäckning** i dialogrutan Bild och lägga till texten *Aktuell temperatur {Value}*, vilket visas i figuren nedan.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Klicka **Förhandsgranska**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
