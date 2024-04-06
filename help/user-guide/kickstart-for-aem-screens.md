---
title: Kickstart Guide
seo-title: Kickstart Guide
description: Följ den här sidan för att skapa ett AEM Screens-demonstrationsprojekt. Det hjälper dig att skapa en digital signeringsupplevelse från installation och konfiguration av ett nytt projekt för att visa ditt innehåll i AEM Screens Player.
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 1%

---

# Kickstart Guide {#kickstart-guide}

I början av AEM Screens demonstreras hur du konfigurerar och kör ett AEM Screens-projekt. Här får du hjälp med att skapa en grundläggande digital signeringsupplevelse och lägga till innehåll som resurser och/eller videor i varje kanal och publicera innehållet ytterligare i en AEM Screens-spelare.

>[!NOTE]
>Kontrollera att du har installerat det senaste funktionspaketet för AEM Screens innan du börjar arbeta med projektinformationen. Du kan hämta det senaste funktionspaketet från [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID.

## Förutsättningar {#prerequisites}

Följ stegen nedan för att skapa ett exempelprojekt för AEM Screens och publicera innehåll ytterligare till Screens Player.

>[!NOTE]
>I följande självstudie visas hur du spelar upp innehållet i din kanal i Chrome OS-spelaren.

>[!IMPORTANT]
>**Konfigurationsinställningar för OSGi**
>Du måste aktivera den tomma referenten för att enheten ska kunna skicka data till servern. Om t.ex. den tomma refereraregenskapen är inaktiverad, kan enheten inte publicera en skärmdump. Vissa av dessa funktioner är för närvarande bara tillgängliga om Apache Sling Referrer-filtret Tillåt tomt är aktiverat i OSGi-konfigurationen. Kontrollpanelen kan visa en varning om att skyddsinställningarna kan förhindra vissa av dessa funktioner från att fungera.
>Följ stegen nedan för att aktivera ***Apache Sling Referer-filtret Tillåt tomt***:


## Tillåt tomma referentförfrågningar {#allow-empty-referrer-requests}

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console** via AEM > hammarikon > **Operationer** > **Webbkonsol**.

   ![bild](assets/config/empty-ref1.png)

1. **Konfiguration av Adobe Experience Manager Web Console** öppnas. Sök efter försäljningsreferent.

   Om du vill söka efter egenskapen för Sing-refereraren trycker du på **Kommando+F** for **Mac** och **Ctrl+F** for **Windows**.

1. Kontrollera **Tillåt tomt** som i bilden nedan.

   ![bild](assets/config/empty-ref2.png)

1. Klicka **Spara** om du vill aktivera referensfiltret för Apache Sling Tillåt tomt.

## Skapa en upplevelse av en digital skylt på 5 minuter {#creating-a-digital-signage-experience-in-minutes}

### Skapa ett AEM Screens-projekt {#creating-project}

Det första steget är att skapa ett AEM Screens-projekt.

1. Navigera till din Adobe Experience Manager-instans (AEM) och klicka på **Skärmar**. Du kan även navigera direkt från `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Klicka **Skapa skärmsprojekt** för att skapa ett nytt skärmsprojekt. Ange titeln som **DemoScreens** och klicka **Spara**.

   ![bild](assets/kickstart/demo-1.png)

   >[!NOTE]
   >När du har skapat projektet återgår du till startsidan för Skärmprojekt. Nu kan du välja ditt projekt. I ett projekt finns det fem olika mappar **Program**, **Kanaler**, **Enheter**, **Platser** och **Scheman**.

### Skapa en kanal {#creating-channel}

När du har skapat ditt AEM Screens-projekt måste du skapa en ny kanal där du hanterar innehållet.

Följ stegen nedan för att skapa en ny kanal för ditt projekt:

1. När du har skapat ett projekt väljer du **DemoScreens** projektet och välj **Kanaler** enligt bilden nedan. Klicka **+ Skapa** i åtgärdsfältet.

   ![bild](assets/kickstart/demo-2.png)

1. Välj **Sekvenskanal** från guiden och klicka på **Nästa**.
   ![bild](assets/kickstart/demo-3.png)

1. Ange **Titel** as **TestChannel** och klicka **Skapa**.

   ![bild](assets/kickstart/demo-4.png)

   The **TestChannel** läggs nu till i din kanalmapp enligt bilden nedan.

   ![bild](assets/kickstart/demo-5.png)

### Lägga till innehåll i en kanal {#adding-content}

När ni väl har er kanal på plats måste ni lägga till innehåll i kanalen som AEM Screens Player visar.

Följ stegen nedan för att lägga till innehåll i kanalen (**TestChannel**) i ditt projekt:

1. Navigera till **DemoProject** du har skapat och väljer **TestChannel** från **Kanaler** mapp.

1. Klicka **Redigera** i åtgärdsfältet (se figuren nedan). Redigeraren för **TestChannel** öppnas.

   ![bild](assets/kickstart/demo-6.png)

1. Klicka på ikonen som växlar sidopanelen till vänster i åtgärdsfältet för att öppna resurserna och komponenterna.

1. Dra och släpp de komponenter du vill lägga till i kanalen.

   ![bild](assets/kickstart/demo-7.png)

### Skapa en plats {#creating-location}

När du väl har skapat kanalen måste du skapa en plats.

>[!NOTE]
>***Platser*** dela upp dina olika digitala signeringsupplevelser och innehåller de konfigurationer som visas beroende på var de olika skärmarna finns.

Följ stegen nedan för att skapa en ny plats för ditt projekt:

1. Navigera till **DemoProject** du har skapat och väljer **Platser** mapp.

1. Klicka **+ Skapa** i åtgärdsfältet.

1. Välj **Plats** från guiden och klicka på **Nästa**.

1. Ange **Namn** för din plats (ange titeln som **TestLocation**) och klicka på **Skapa**.

The **TestLocation** skapas och läggs till i **Platser** mapp.


### Skapa en visning för plats {#creating-display}

När du har skapat en plats måste du skapa en ny skärm för platsen.

>[!NOTE]
>***Visa*** representerar den digitala upplevelse som körs på en eller flera skärmar.

1. Navigera till **TestLocation** och markera den.

1. Klicka **Skapa** i åtgärdsfältet.

   ![bild](assets/kickstart/demo-disp1.png)

1. Välj **Visa** från **Skapa** guide och klicka **Nästa**.

   ![bild](assets/kickstart/demo-disp2.png)

1. Ange **Titel** as **LobbyDisplay** och klicka **Skapa**.

   ![bild](assets/kickstart/demo-disp3.png)

   En ny skärm med namnet **TestDisplay** läggs nu till på din plats **TestLocation**, vilket visas i figuren nedan.

   ![bild](assets/kickstart/demo-disp4.png)

### Tilldela en kanal {#assigning-channel}

När projektkonfigurationen är klar måste du tilldela kanalen till en skärm för att kunna visa innehållet.

1. Navigera till önskad visning från **DemoScreens** > **Platser** > **TestLocation** > **LobbyDisplay**.

1. Tryck/klicka **Tilldela kanal** i åtgärdsfältet.

   ![bild](assets/kickstart/demo-assign1.png)

   Eller

   Tryck/klicka **Kontrollpanel** i åtgärdsfältet och klicka på **+Tilldela kanal** från **TILLDELADE KANALER OCH SCHEMAN** -panelen.

   ![bild](assets/kickstart/demo-assign2.png)

1. The **Kanaltilldelning** öppnas.

1. Från **Inställningar** väljer du kanal **efter bana**  och **Händelser som stöds** as **Inledande inläsning** och **Inaktiv skärm**.

   >[!NOTE]
   >
   >The **Kanalroll**, **Prioritet** och **Avbrottsmetoder** fylls alla i som standard. Se [Kanalegenskaper](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) om du vill veta mer om kanaltilldelningsegenskaper.

   ![bild](assets/kickstart/demo-assign3.png)

   Dessutom kan du välja **Aktiveringsfönster** och **Återkommande schema**.

   >[!NOTE]
   >The *Återkommande schema* gör att du kan ange ett återkommande schema för din kanal. Du ställer in flera upprepningsscheman för en kanal.
   >Se [Återkommande schema](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) för mer information.

1. Klicka **Spara** när du har konfigurerat dina inställningar.

### Registrera en enhet och tilldela en enhet till en skärm {#registering-device}

Du måste registrera din enhet med AEM kontrollpanel.

>[!IMPORTANT]
>Chrome OS-spelaren kan installeras som Chrome Browser-plugin i utvecklarläge utan att den faktiska enheten för Chrome Player krävs. För installation, följ stegen nedan:
>
>1. Klicka [här](https://download.macromedia.com/screens/) för att ladda ned den senaste Chrome Player.
>1. Zippa upp och spara det på disken.
>1. Öppna Chrome-webbläsaren och välj **Tillägg** från menyn eller direkt navigera till ***chrome://extensions***.
>1. Aktivera **Utvecklarläge** från det övre högra hörnet.
>1. Klicka på **Läs in opackad** från det övre vänstra hörnet och läsa in den uppzippade Chrome Player.
>1. Kontrollera **AEM Screens Chrome Player** plugin-program, om det finns i listan över tillägg.
>1. Öppna en ny flik och klicka på **Appar** ikonen i det övre vänstra hörnet eller direkt navigera till ***chrome://apps***.
>1. Klicka på **AEM Screens** Plugin-program för att starta Chrome Player. Som standard startas spelaren i helskärmsläge. Tryck **esc** för att avsluta helskärmsläget.

När du har aktiverat Chrome OS-spelaren följer du stegen nedan för att registrera en Chrome-enhet.

1. Navigera till **Enheter** projektmapp från AEM.

1. Tryck/klicka på **Enhetshanteraren** i åtgärdsfältet.

   ![bild](assets/kickstart/demo-register1.png)

1. Tryck/klicka på **Enhetsregistrering** uppifrån till höger.

1. Välj önskad enhet och tryck/klicka **Registrera enhet**.

   ![bild](assets/kickstart/demo-register2.png)

1. Vänta tills enheten skickar sin registreringskod och kontrollera samtidigt **Registreringskod** från din Chrome-enhet.
   ![bild](assets/kickstart/demo-register3.png)

1. Om **Registreringskod** är samma på båda datorerna, tryck/klicka **Validera** AEM.

1. Ange önskat namn som **ChromeDevice forDemo** för enheten och klicka på **Registrera**.

   ![bild](assets/kickstart/demo-register4.png)

1. Klicka **Tilldela visning** från **Enhetsregistrering lyckades** -dialogrutan.

   ![bild](assets/kickstart/demo-register5.png)

1. Markera sökvägen till din visning som **DemoScreens** > **Platser** > **TestLocation** > **LobbyDisplay** och klicka **Tilldela**.

   ![bild](assets/kickstart/demo-device6.png)

1. När enheten har tilldelats ser du följande bekräftelse.

   ![bild](assets/kickstart/demo-register8.png)

1. Tryck/klicka **Slutför** för att slutföra registreringsprocessen. Du bör kunna visa din registrerade enhet från kontrollpanelen.

   ![bild](assets/kickstart/demo-register9.png)

### Visa innehållet i Chrome Player {#viewing-content-output}

Alla resurser i din kanal spelas nu upp i din Chrome OS-spelare.

Grattis till att du nu spelar upp innehåll i en AEM Screens-kanal!

![bild](assets/kickstart/demo-video-screens.gif)
