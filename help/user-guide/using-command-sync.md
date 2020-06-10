---
title: Använda kommandosynkronisering
seo-title: Använda kommandosynkronisering
description: Följ den här sidan om du vill veta mer om hur du använder kommandosynkronisering.
seo-description: Följ den här sidan om du vill veta mer om hur du använder kommandosynkronisering.
translation-type: tm+mt
source-git-commit: 59eb6f298aa646d14445ddd6082006742fb02d62
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 2%

---


# Synkronisera kommandon {#command-sync}

På följande sida beskrivs hur du använder kommandosynkronisering. Med kommandosynkronisering kan du synkronisera uppspelningen mellan olika spelare. Spelarna kan spela upp olika innehåll, men varje resurs måste ha samma längd.

>[!IMPORTANT]
>Den här funktionen stöder inte inbäddade sekvenser, dynamiska inbäddade sekvenser, programkanaler eller övergångar.

## Översikt {#overview}

Digitala signeringslösningar måste ha stöd för videoväggar och synkroniserad uppspelning för scenarier som nyårsräkning eller stor video som segmenterats upp för uppspelning på flera skärmar, och det är här som kommandosynkronisering spelas upp.

Om du vill använda kommandosynkronisering fungerar en spelare som *master* och skickar kommando, och alla andra spelare fungerar som *klienter* och spelar när de tar emot kommandot.

Huvudet ** skickar ett kommando till alla registrerade klienter när uppspelningen av ett objekt ska börja. Nyttolasten för detta kan vara indexvärdet för det objekt som ska spelas upp och/eller den yttre HTML-koden för det element som ska spelas upp.

## Implementera kommandosynkronisering {#using-command-sync}

I följande avsnitt beskrivs hur du kan använda kommandosynkronisering i ett AEM-skärmsprojekt.

>[!NOTE]
>För synkroniserad uppspelning krävs att alla maskinvaruenheter har samma maskinvaruspecifikationer och helst samma operativsystem. Synkronisering mellan olika maskinvara och operativsystem rekommenderas inte.

### Konfigurera projektet {#setting-up}

Innan du använder funktionen Kommandosynkronisering måste du kontrollera att du har ett projekt och en kanal med innehåll som har konfigurerats för ditt projekt.

1. I följande exempel visas ett demoprojekt med namnet **CommandSyncDemo** och en sekvenskanal i **ChannelLoby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en kanal eller lägger till innehåll i en kanal finns i [Skapa och hantera kanaler](/help/user-guide/managing-channels.md)

   Kanalen innehåller följande innehåll, vilket visas i bilden nedan.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Skapa en visning i mappen **Platser** , som bilden nedan visar.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Tilldela kanalen **ChannelLobby** till din **LobbyDisplay**.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Mer information om hur du tilldelar en kanal till en skärm finns i [Skapa och hantera skärmar](/help/user-guide/managing-displays.md).

1. Navigera till mappen **Enheter** och klicka på **Enhetshanteraren** i åtgärdsfältet för att registrera enheterna.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Mer information om hur du tilldelar en kanal till en skärm finns i [Skapa och hantera bildskärmar](/help/user-guide/managing-displays.md)

1. I det här exemplet visas en fönsterenhet och en Windows-spelare som två separata enheter. Båda enheterna pekar på samma skärm.
   ![image1](assets/command-sync6.png)

### Uppdaterar kanalinställningar

1. Navigera till **ChannelLoby** och klicka på **Redigera** i åtgärdsfältet för att uppdatera kanalinställningarna.

1. Markera hela kanalen enligt bilden nedan.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Klicka på växlingsikonen för att öppna dialogrutan **Sida** .
   ![image1](assets/command-sync/command-sync8-1.png)

1. Ange det *synkroniserade* nyckelordet i fältet **Strategi** .

   ![image1](assets/command-sync/command-sync9-1.png)


### Konfigurera en mallsida {#setting-up-master}

1. Navigera till kontrollpanelen från **CommandSyncDemo** —> **Platser** —> **Lobby** —> **LobbyDisplay** och klicka på **Kontrollpanelen** i åtgärdsfältet.
De två enheterna (fönsterstandard och fönsterspelare) visas på **enhetspanelen** enligt bilden nedan.
   ![image1](assets/command-sync/command-sync10-1.png)

1. Välj den enhet som du vill ange som mall på panelen **Enheter** . I följande exempel visas hur du ställer in Chrome-enheten som master. Klicka på **Ange som huvudenhet**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Ange IP-adressen i **Ange som huvudenhet** och klicka på **Spara**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
> Du kan konfigurera flera enheter som master.

### Synkronisera med Master {#sync-up-master}

1. När du har angett Chrome-enheten som huvudenhet kan du synkronisera den andra enheten (i det här fallet Windows-spelaren) så att den synkroniseras med huvudspelaren.
Välj den andra enheten (i det här fallet Windows-spelaren) på panelen **Enheter** och klicka på **Synkronisera till huvudenhet** enligt bilden nedan.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Markera enheten i listan och klicka på **Spara**.

   >[OBS!]
   > I dialogrutan **Synkronisera med huvudenhet** visas en lista med huvudenheter. Du kan välja en av dina inställningar.

1. När enheten (Windows-spelaren) har synkroniserats med huvudspelaren (Chrome-spelaren) visas enheten synkroniserad på panelen **Enheter** .

   ![image1](assets/command-sync/command-sync14-1.png)

### Synkronisering med mallsidan tas bort {#desync-up-master}

När du har synkroniserat en eller flera enheter till en huvudenhet kan du avsynkronisera uppdraget från den enheten.

>[!NOTE]
>Om du avsynkroniserar en huvudenhet bryts även länken till alla klientenheter som är kopplade till den huvudenheten.

Följ stegen nedan för att ta bort synkroniseringen från huvudenheten:

1. Navigera till **enhetspanelen** och markera enheten.

1. Klicka på **Desync device(s)** för att avsynkronisera klienten från huvudenheten.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Klicka på **Bekräfta** för att avsynkronisera den valda enheten från huvuddatorn.

   >[OBS!]
   > Om du väljer huvudenheten och använder alternativet för avsynkronisering kommer alla enheter som är anslutna till huvudenheten att avsynkroniseras i ett steg.
