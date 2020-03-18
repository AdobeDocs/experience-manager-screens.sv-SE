---
title: Textövertäckning
seo-title: Textövertäckning
description: Textövertäckning är en funktion i AEM-skärmar som gör att du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild. Följ den här sidan om du vill veta mer.
seo-description: Textövertäckning är en funktion i AEM-skärmar som gör att du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild. Följ den här sidan om du vill veta mer.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Textövertäckning {#text-overlay}

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Använda textövertäckning**
* **Förutsättningar**
* **Förstå egenskaper för textövertäckning**

>[!CAUTION]
>
>Funktionen **Textövertäckning** är bara tillgänglig om du har installerat AEM 6.3 Feature Pack 5 eller AEM 6.4 Feature Pack 3.

## Översikt {#overview}

Textövertäckning är en funktion i AEM-skärmar som gör att du kan skapa en övertygande upplevelse i en sekvenskanal genom att ange en rubrik eller en beskrivning som läggs ovanpå en bild.

Mer information om hur du skapar en egen anpassad komponent finns i **Utöka en AEM Screens-komponent**.

I det här avsnittet visas bara hur du använder och drar nytta av filmminiatyrkomponenten i ett AEM Screens-projekt och använder den som textövertäckning i en av sekvenskanalerna.

## Använda textövertäckning {#using-text-overlay}

I följande avsnitt beskrivs hur du använder textövertäckning i ett AEM Screens-projekt.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har konfigurerat ett projekt som en förutsättning för att börja implementera textövertäckning. Exempel:

* Skapa ett AEM Screens-projekt (i det här exemplet **TextOverlayDemo**)

* Skapa en kanal som **TextSample** under mappen **Channels**

* Lägg till innehåll i din **TextSample** Channel

Följande bild visar **TextOverlayDemo** -projektet med **TextSample** -kanalen i **mappen** Channels.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. Gå till **TextOverlayDemo** —> **Channels** —> **TextSample** och klicka på **Edit** i åtgärdsfältet för att öppna redigeraren.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Markera bilden och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan Egenskaper.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Välj alternativet **Textövertäckning** i navigeringsfältet i dialogrutan, så som visas i bilden nedan.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Förstå egenskaper för textövertäckning {#understanding-text-overlay-properties}

Med egenskaperna för textövertäckning kan du lägga till text i valfri komponent i skärmsprojektet. I följande avsnitt ges en översikt över de egenskaper som är tillgängliga i Textövertäckning:

![text](assets/text.gif)

Du kan lägga till en text i textrutan och lägga till typografisk betoning som fet, kursiv stil, understrykning och så vidare.

**Färgvariant** Med det här alternativet kan texten antingen vara mörk (text i svart färg) eller Ljus (text i vit färg).

**Storlek och placering** Med det här alternativet kan användaren justera texten vågrätt eller lodrätt eller dessutom använda finkorniga verktyg för textjustering.

>[!NOTE]
>
>Om du vill använda finkorniga verktyg på rätt sätt måste du se till att identifiera rätt position i pixlar med (px) som suffix, till exempel 200px. Resultatet av det här uttrycket blir 200 pixlar från startpunkten.

