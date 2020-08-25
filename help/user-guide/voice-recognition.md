---
title: Röstigenkänning i AEM Screens
description: Sidan beskriver röstigenkänningsfunktionen i AEM Screens.
translation-type: tm+mt
source-git-commit: 0300af2ef44756dddbb27f3da15c52bc877b93ea
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 1%

---


# Röstigenkänning i AEM Screens {#voice-recognition}

## Översikt {#overview}

Med funktionen Röstigenkänning kan du ändra innehåll i en AEM Screens-kanal som styrs av röstinteraktion.

En innehållsförfattare kan konfigurera en visning som röstaktiverad. Syftet med den här funktionen är att ge kunderna möjlighet att använda tal som sätt att interagera med sina bildskärmar. Exempel på liknande användningsområden är att hitta produktrekommendationer i butiker, beställa menyalternativ på materier och restauranger. Den här funktionen ökar tillgängligheten för användarna och kan förbättra kundupplevelsen avsevärt.


>[!NOTE]
>Spelarens maskinvara måste stödja röstindata, t.ex. en mikrofon.

>[!IMPORTANT]
> Funktionen Röstigenkänning är bara tillgänglig på Chrome- och Electron-spelare.

## Implementera röstigenkänning {#implementing}


Om du vill implementera röstigenkänning i ditt AEM Screens-projekt måste du aktivera röstigenkänningen för bildskärmen och associera varje kanal med en unik tagg för att utlösa en kanalövergång.

I följande avsnitt beskrivs hur du kan aktivera och använda funktionen Röstigenkänning i ett AEM Screens-projekt.

### Konfigurera projektet {#setting-up}

Innan du använder funktionen för röstigenkänning bör du kontrollera att du har ett projekt och en kanal med innehåll som har konfigurerats för ditt projekt.

1. I följande exempel visas ett demoprojekt med namnet **VoiceDemo** och tre sekvenskanaler **Main**, **ColdDrinks** och **HotDrinks**, vilket visas i bilden nedan.

   ![bild](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en kanal eller lägger till innehåll i en kanal finns i [Skapa och hantera kanaler](/help/user-guide/managing-channels.md)

1. Navigera till varje kanal och lägg till innehåll. Navigera till **VoiceDemo** —> **Kanaler** —> **Main** och markera kanalen. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren och lägga till innehåll (bilder/videor) efter behov. Lägg på samma sätt till innehåll i både **ColdDrinks** och **HotDrinks** -kanalen.

   Kanalerna innehåller nu resurser (bilder), vilket visas i figurerna nedan.

   **Huvud**:

   ![bild](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![bild](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![bild](assets/voice-recognition/vr-2.png)

### Konfigurera taggar för kanaler {#setting-tags}

När du har lagt till innehåll i kanalerna måste du navigera till var och en av kanalerna och lägga till lämpliga taggar som skulle utlösa röstigenkänningen.

Följ stegen nedan för att lägga till taggar i din kanal:

1. Navigera till varje kanal och lägg till innehåll. Navigera till **VoiceDemo** —> **Kanaler** —> **Main** och markera kanalen.

1. Klicka på **Egenskaper** i åtgärdsfältet.

   ![bild](assets/voice-recognition/vr-5.png)

1. Navigera till fliken **Grunderna** och markera en tagg som redan finns i fältet **Taggar** eller skapa en ny.

   Du kan antingen skapa en ny tagg genom att skriva in ett nytt namn för taggen, vilket visas i bilden nedan:

   ![bild](assets/voice-recognition/vr-6.png)

   Eller

   Du kan skapa taggar från AEM i förväg för ditt projekt och sedan välja dem också.

   Skapa taggar genom att följa stegen nedan:

   1. Navigera till AEM.
   1. Klicka på verktygen —> **Taggning**.
      ![bild](assets/voice-recognition/vr-7.png)

1. Klicka på **Spara och stäng** när du är klar.

Lägg på samma sätt till taggen **hot** i **HotDrinks** -kanalen och **kalla** till **ColdDrinks** -kanalen.

### Tilldela kanal till en skärm {#channel-assignment}

1. Skapa en visning i mappen **Platser** , som bilden nedan visar.

   >[!NOTE]
   >
   >Mer information om hur du tilldelar en kanal till en skärm finns i [Skapa och hantera skärmar](/help/user-guide/managing-displays.md).

1. Tilldela kanalerna **Main**, **ColdDrinks** och **HotDrinks** till **LobbyDisplay**.


1. Ange följande egenskaper för varje kanal.

   >[!NOTE]
   >
   >Mer information om hur du tilldelar en kanal till en skärm finns i [Skapa och hantera skärmar](/help/user-guide/managing-displays.md).

1. När du har tilldelat kanaler till en visning går du till **LobbyDisplay** och väljer visningen. Välj **Egenskaper** i åtgärdsfältet.

1. Navigera till fliken **Visning** och aktivera alternativet **Röstaktiverat** under **Innehåll**.

   >[!NOTE]
   >Det är obligatoriskt att aktivera funktionen för röstigenkänning från skärmen.

## Visa innehållet i Chrome Player {#viewing-content}

När de föregående stegen är klara kan du registrera din enhet och visa utdata.

Följ stegen nedan:

1. Navigera till mappen **Enheter** och klicka på **Enhetshanteraren** i åtgärdsfältet för att registrera enheterna.







