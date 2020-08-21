---
title: Röstigenkänning i AEM Screens
description: Sidan beskriver röstigenkänningsfunktionen i AEM Screens.
translation-type: tm+mt
source-git-commit: c46cd26f5067468aadf80a822fffce1d5f0b5d9a
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# Röstigenkänning i AEM Screens {#voice-recognition}

## Översikt {#overview}

Med funktionen Röstigenkänning kan du ändra innehåll i en AEM Screens-kanal som styrs av röstinteraktion.

En innehållsförfattare kan konfigurera en visning som röstaktiverad. Detta gör att alla spelare som är registrerade mot visningen kan förstå tal. Du måste aktivera röstigenkänningen för bildskärmen och associera varje kanal med en unik tagg för att aktivera en kanalövergång.

>[!NOTE]
>Spelarens maskinvara måste stödja röstindata, t.ex. en mikrofon.

>[!IMPORTANT]
> Funktionen Röstigenkänning är bara tillgänglig på Chrome- och Electron-spelare.

## Implementera röstigenkänning {#implementing}

I följande avsnitt beskrivs hur du kan aktivera och använda funktionen Röstigenkänning i ett AEM Screens-projekt.

### Konfigurera projektet {#setting-up}

Innan du använder funktionen för röstigenkänning bör du kontrollera att du har ett projekt och en kanal med innehåll som har konfigurerats för ditt projekt.

1. I följande exempel visas ett demoprojekt med namnet **VoiceDemo** och tre sekvenskanaler **Main**, **ColdDrinks** och **HotDrinks**, vilket visas i bilden nedan.

   >[!NOTE]
   >
   >Mer information om hur du skapar en kanal eller lägger till innehåll i en kanal finns i [Skapa och hantera kanaler](/help/user-guide/managing-channels.md)

1. Navigera till varje kanal och lägg till innehåll. Navigera till **VoiceDemo** —> **Kanaler** —> **Main** och markera kanalen. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren och lägga till innehåll (bilder/videor) efter behov. Lägg på samma sätt till innehåll i både **ColdDrinks** och **HotDrinks** -kanalen.

   Kanalerna innehåller nu följande innehåll, vilket visas i figurerna nedan.

   **Huvud**:

   **ColdDrinks**:

   **HotDrinks**:

### Konfigurera taggar för kanaler {#setting-tags}

När du har lagt till innehåll i kanalerna måste du navigera till var och en av kanalerna och lägga till lämpliga taggar som skulle utlösa röstigenkänningen.

Följ stegen nedan för att lägga till taggar i din kanal:

1. Navigera till varje kanal och lägg till innehåll. Navigera till **VoiceDemo** —> **Kanaler** —> **Main** och markera kanalen.

1. Klicka på **Egenskaper** i åtgärdsfältet.

1. Navigera till fliken **Grunderna** och markera en tagg som redan finns i fältet **Taggar** eller skapa en ny.

1. Klicka på **Spara och stäng** när du är klar.


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







