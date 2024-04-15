---
title: Använda kommandosynkronisering
description: Läs mer om hur du använder kommandosynkronisering i AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Synkronisera kommandon {#command-sync}

På följande sida beskrivs hur du använder kommandosynkronisering. Med kommandosynkronisering kan du synkronisera uppspelningen mellan olika spelare. Spelarna kan spela upp olika innehåll, men varje resurs måste ha samma längd.

>[!IMPORTANT]
>
>Den här funktionen stöder inte inbäddade sekvenser, dynamiska inbäddade sekvenser, programkanaler eller övergångar.

## Ökning {#overview}

Digitala signeringslösningar måste ha stöd för videoväggar och synkroniserad uppspelning för scenarier som nyårsräkning eller stor video som segmenterats upp för uppspelning på flera skärmar, och det är här som kommandosynkronisering spelas upp.

Om du vill använda kommandosynkronisering fungerar en spelare som en *primär* och skickar kommando och alla andra spelare agerar som *klienter* och spelas upp när de får kommandot.

The *primär* skickar ett kommando till alla registrerade klienter när uppspelningen av ett objekt ska börja. Nyttolasten för detta kan vara indexvärdet för det objekt som ska spelas upp och/eller den yttre HTML-koden för det element som ska spelas upp.

## Implementera kommandosynkronisering {#using-command-sync}

I följande avsnitt beskrivs hur du kan använda kommandosynkronisering i ett AEM Screens-projekt.

>[!NOTE]
>
>För synkroniserad uppspelning krävs att alla maskinvaruenheter har samma maskinvaruspecifikationer och helst samma operativsystem. Synkronisering mellan olika maskinvara och operativsystem rekommenderas inte.

### Konfigurera projektet {#setting-up}

Innan du använder funktionen Kommandosynkronisering måste du kontrollera att du har ett projekt och en kanal med innehåll som har konfigurerats för ditt projekt.

1. I följande exempel visas ett demoprojekt med namnet **CommandSyncDemo** och en sekvenskanal **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en kanal eller lägger till innehåll i en kanal finns i [Skapa och hantera kanaler](/help/user-guide/managing-channels.md)

   Kanalen innehåller följande innehåll, vilket visas i bilden nedan.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Skapa en plats **Lobby** och sedan en skärm med namnet **LobbyDisplay** i **Platser** enligt bilden nedan.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Tilldela kanalen, **ChannelLobby** till **LobbyDisplay**. Nu kan du visa den tilldelade kanalen för visning från kontrollpanelen.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Mer information om hur du tilldelar en kanal till en skärm finns i [Skapa och hantera skärmar](/help/user-guide/managing-displays.md).

1. Navigera till **Enheter** mapp.
1. Välj **Enhetshanteraren** i åtgärdsfältet.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Mer information om hur du registrerar en enhet finns i [Enhetsregistrering](/help/user-guide/device-registration.md)

1. I det här exemplet visas en fönsterenhet och en Windows-spelare som två separata enheter. Båda enheterna pekar på samma skärm.
   ![image1](assets/command-sync6.png)

### Uppdaterar kanalinställningar

1. Navigera till **ChannelLobby**.
1. Välj **Redigera** i åtgärdsfältet.
1. Markera hela kanalen enligt bilden nedan.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Välj skiftnyckelsikonen.
   ![image1](assets/command-sync/command-sync8-1.png)

1. I **Sida** anger du *synkad* nyckelord i **Strategi** fält.
   ![image1](assets/command-sync/command-sync9-1.png)


### Konfigurera en primär {#setting-up-primary}

1. Navigera till kontrollpanelen från **CommandSyncDemo** > **Platser**  > **Lobby** > **LobbyDisplay** och markera **Kontrollpanel** i åtgärdsfältet.
Lägg märke till de två enheterna (fönsterstandard och Windows Player) i **ENHETER** enligt följande:
   ![image1](assets/command-sync/command-sync10-1.png)

1. Från **ENHETER** väljer du den enhet som du vill ange som primär. I följande exempel visas hur du ställer in Chrome-enheten som primär. Välj **Ange som primär enhet**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Ange IP-adressen i **Ange som primär enhet** och markera **Spara**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Du kan konfigurera flera enheter som primära.

### Synkroniserar med primär {#sync-up-primary}

1. När du har angett Chrome-enheten som primär synkroniserar du den andra enheten (i det här fallet Windows-spelaren) så att den synkroniseras med den primära.
Välj den andra enheten (i det här fallet Windows Player) på menyn **ENHETER** panel och markera **Synkronisera med primär enhet**.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Välj enheten i listan och välj **Spara**.

   >[OBS!]
   > The **Synkronisera med primär enhet** visas en lista med primära enheter. Välj önskad.

1. När enheten (Windows-spelaren) synkroniseras till den primära (Chrome Player) kan du se enheten synkroniserad i **ENHETER** -panelen.

   ![image1](assets/command-sync/command-sync14-1.png)

### Synkronisering med den primära {#desync-up-primary}

När du har synkroniserat en eller flera enheter till en primär enhet kan du avsynkronisera tilldelningen från den enheten.

>[!NOTE]
>
>Om du avsynkroniserar en primär enhet bryts även länken till alla klientenheter som är kopplade till den primära enheten.

Följ stegen nedan för att ta bort synkroniseringen från den primära enheten:

1. Navigera till **ENHETER** och välj enhet.

1. Välj **Desynkrona enheter** så att du kan desynkronisera klienten från den primära enheten.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Välj **Bekräfta** om du vill avsynkronisera den valda enheten från den primära enheten.

   >[OBS!]
   > Om du väljer den primära enheten och använder alternativet för avsynkronisering, kommer alla enheter som är anslutna till den primära att avsynkroniseras i ett steg.
