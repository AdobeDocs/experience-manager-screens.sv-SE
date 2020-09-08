---
title: Kickstart Guide
seo-title: Kickstart Guide
description: Följ den här sidan för att skapa ett AEM Screens-demonstrationsprojekt. Det hjälper dig att skapa en digital signeringsupplevelse från installation och konfiguration av ett nytt projekt för att visa ditt innehåll i AEM Screens Player.
translation-type: tm+mt
source-git-commit: f2fef18cc73825b3f062a79c560097e8fd00ac9f
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 1%

---


# Kickstart Guide {#kickstart-guide}

I det här avsnittet kommer vi igång med AEM Screens och visar hur du konfigurerar och kör ett AEM Screens-projekt. Här får du hjälp med att skapa en grundläggande digital signeringsupplevelse och lägga till innehåll som resurser och/eller videor i varje kanal och publicera innehållet ytterligare i en AEM Screens-spelare.

>[!NOTE]
>Kontrollera att du har installerat det senaste funktionspaketet innan du börjar arbeta med projektinformationen. Du kan ladda ned det senaste funktionspaketet för AEM Screens 6.5.5 från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID.

## Skapa en upplevelse av en digital skylt på 5 minuter {#creating-a-digital-signage-experience-in-minutes}

Följ stegen nedan för att skapa ett exempelprojekt för AEM Screens och publicera innehåll ytterligare till Screens Player.

>[!NOTE]
>I följande självstudie visas hur du spelar upp innehållet i din kanal i Chrome OS-spelaren.

>[!IMPORTANT]
>**Konfigurationsinställningar för OSGi**
>Du måste aktivera den tomma referenten för att enheten ska kunna skicka data till servern. Om t.ex. den tomma refereraregenskapen är inaktiverad, kan enheten inte publicera en skärmdump. Vissa av dessa funktioner är för närvarande bara tillgängliga om Apache Sling Referrer-filtret Tillåt tomt är aktiverat i OSGi-konfigurationen. Kontrollpanelen kan visa en varning om att skyddsinställningarna kan förhindra vissa av dessa funktioner från att fungera.
>Följ stegen nedan för att aktivera filtret ***Apache Sling Referrer Tillåt tomt***:


## Tillåt tomma referentförfrågningar {#allow-empty-referrer-requests}

1. Gå till **Adobe Experience Manager Web Console Configuration** via AEM:> hammer icon —> **Operations** —> **Web Console**.

   ![bild](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web Console Configuration** öppnas. Sök efter försäljningsreferent.

   Om du vill söka efter egenskapen för Sing-refereraren trycker du på **Command+F** för **Mac** och **Ctrl+F** för **Windows**.

1. Markera alternativet **Tillåt tomt** , så som visas i bilden nedan.

   ![bild](assets/config/empty-ref2.png)

1. Klicka på **Spara** för att aktivera Apache Sling Referer-filtret Tillåt tomt.


## Självstudiekurs {#tutorial}

### Skapa ett nytt AEM Screens-projekt {#creating-project}

Det första steget är att skapa ett nytt AEM Screens-projekt.

1. Navigera till din Adobe Experience Manager-instans (AEM) och klicka på **Skärmar**. Du kan också navigera direkt från `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Klicka på **Skapa skärmsprojekt** för att skapa ett nytt skärmsprojekt. Ange titeln som **demoskärmar** och klicka på **Spara**.

   ![bild](assets/kickstart/demo-1.png)

   >[!NOTE]
   >När du har skapat projektet återgår du till startsidan för Skärmprojekt. Nu kan du välja ditt projekt. I ett projekt finns det fem olika mappar med namnen **Program**, **Kanaler**, **Enheter**, **Platser** och **Scheman**.


### Skapa en ny kanal {#creating-channel}

När projektet är på plats måste du skapa en ny kanal där du hanterar innehållet.

Följ stegen nedan för att skapa en ny kanal för ditt projekt:

1. När du har skapat ett projekt väljer du **DemoScreens** -projektet och väljer mappen **** Kanaler enligt bilden nedan. Klicka på **+ Skapa** i åtgärdsfältet.

   ![bild](assets/kickstart/demo-2.png)

1. Välj **Sekvenskanal** i guiden och klicka på **Nästa**.
   ![bild](assets/kickstart/demo-3.png)

1. Ange **titeln** som *TestChannel* och klicka på **Skapa**.

   ![bild](assets/kickstart/demo-4.png)

TestChannel ** skapas och läggs till i kanalmappen, vilket visas i bilden nedan.

![bild](assets/kickstart/demo-5.png)

### Lägga till innehåll i en kanal {#adding-content}

När du väl har skapat kanalen måste du lägga till innehåll i kanalen som skärmspelaren ska visa.

Följ stegen nedan för att lägga till innehåll i kanalen (*TestChannel*) i ditt projekt:

1. Navigera till *Test_Project* som du skapade och markera mappen **Kanaler** .

1. Klicka på **Redigera** i åtgärdsfältet (se bilden nedan). Redigeraren för *TestChannel* öppnas.

1. Klicka på ikonen som växlar sidopanelen till vänster i åtgärdsfältet för att öppna resurserna och komponenterna.

1. Dra och släpp de komponenter du vill lägga till i kanalen.

   ![chlimage_1-8](assets/chlimage_1-8.png)

I det här exemplet visar redigeraren en bild som lagts till i kanalen.

![chlimage_1-9](assets/chlimage_1-9.png)

### Skapa en ny plats {#creating-location}

När du väl har skapat din kanal måste du skapa en plats.

***Platserna*** är olika för olika digitala signeringsupplevelser och innehåller de konfigurationer som visas beroende på var de olika skärmarna finns.

Följ stegen nedan för att skapa en ny plats för ditt projekt:

1. Navigera till *Test_Project* som du skapade och markera mappen **Platser** .

1. Klicka på **Skapa** bredvid plusikonen i åtgärdsfältet (se bilden nedan). En guide öppnas.
1. Välj **Plats** i guiden och klicka på **Nästa**.

1. Ange **namn** och **titel** för platsen (ange titeln som *TestLocation*) och klicka på **Skapa**.

   ![chlimage_1-10](assets/chlimage_1-10.png)

TestLocation ** skapas och läggs till i mappen **Locations** .

![chlimage_1-11](assets/chlimage_1-11.png)

### Skapa en ny visning för TestLocation {#creating-display}

När du har skapat en plats måste du skapa en ny skärm för platsen.

***Skärmar*** representerar den digitala upplevelse som körs på en eller flera skärmar.

1. Navigera till den plats där du vill skapa visningen (*Test_* Project —> **Locations** —> *TestLocation)* som visas i bilden ovan och välj *TestLocation*.

1. Klicka på **Skapa** i åtgärdsfältet.
1. Välj **Visning** i guiden **Skapa** och klicka på **Nästa**.

1. Ange **namn** och **titel** för visningsplatsen (ange titeln som *TestDisplay*).

1. Välj information om layouten på fliken **Visa** .

   1. Välj **Upplösning** som **Full HD**.

   1. Välj **Antal enheter vågrätt** som 1.

   1. Välj **Antal enheter lodrätt** som 1.

   1. Klicka på **Skapa**.

En ny skärm (*TestDisplay*) läggs till på platsen *TestLocation)*, vilket visas i bilden nedan.

![chlimage_1-12](assets/chlimage_1-12.png)

### Tilldela en kanal {#assigning-channel}

1. Navigera till visningen från *Test_Project* —> **Locations** —> *TestLocation* —> *TestDisplay*.

1. Välj *TestDisplay* och tryck/klicka på **Tilldela kanal **i åtgärdsfältet, *eller*,

1. Klicka på **Kontrollpanelen** och välj **+Tilldela kanal** längst upp till höger på panelen **TILLDELADE KANALER &amp; SCHEMALER** , som visas i bilden nedan. **Dialogrutan Kanaltilldelning** öppnas.

1. Välj **referenskanal** efter **sökväg**

1. Ange **kanalrollen** som *LiveStream*.

1. Markera **kanalsökvägen** (*Test_Project* —> *Kanaler* —> *TestChannel* ) i **kanalen**.

1. Välj **Prioritet** för den här kanalen som *1*.

1. Välj **Händelser** som stöds som **Inledande inläsning** och **Inaktiv skärm**.

1. Ange **Schedule** och välj de datum som är **aktiva från** och **aktiva till**.

1. Click **Save**.

Kanalen skapas och läggs till på panelen.

![chlimage_1-15](assets/chlimage_1-15.png)

### Registrera en enhet {#registering-device}

Du måste registrera din enhet med AEM kontrollpanel.

>[!NOTE]
>Du kan öppna skärmspelaren med den AEM Screens-app du hämtade eller med webbläsaren.



### Visa innehåll i AEM Screens Player {#viewing-the-content-in-screens-player}

När du har lagt till ovanstående konfigurationer bör spelaren automatiskt visa standardkanalen för visningen på din enhet.

![chlimage_1-23](assets/chlimage_1-23.png)

Mer information om AEM Screens Player finns i [AEM Screens Player](working-with-screens-player.md) .
