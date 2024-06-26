---
title: Använda kommandosynkronisering
description: Läs mer om hur du använder kommandosynkronisering i AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# Synkronisera kommandon {#command-sync}

På följande sida beskrivs hur du använder kommandosynkronisering. Med kommandosynkronisering kan du synkronisera uppspelningen mellan olika spelare. Spelarna kan spela upp olika innehåll, men varje resurs måste ha samma längd.

>[!IMPORTANT]
>
>Den här funktionen stöder inte inbäddade sekvenser, dynamiska inbäddade sekvenser, programkanaler eller övergångar.

## Ökning {#overview}

Digitala signeringslösningar måste ha stöd för videoväggar och synkroniserad uppspelning. Det här scenariot är sant om du försöker stödja scenarier som nyårslicenser eller stora videor som segmenterats för att spelas upp på flera skärmar. Det är då kommandosynkronisering spelas upp.

Om du vill använda kommandosynkronisering fungerar en spelare som en *primär* och skickar kommandot och alla andra spelare agerar som *klienter* och spelas upp när de får kommandot.

The *primär* skickar ett kommando till alla registrerade klienter när uppspelningen av ett objekt ska börja. Nyttolasten för den här åtgärden kan vara indexvärdet för det objekt som ska spelas upp, den yttre HTML-koden för det element som ska spelas upp eller båda.

## Implementera kommandosynkronisering {#using-command-sync}

I följande avsnitt beskrivs hur du kan använda kommandosynkronisering i ett AEM Screens-projekt.

>[!NOTE]
>
>För synkroniserad uppspelning krävs att alla maskinvaruenheter har samma maskinvaruspecifikationer och helst samma operativsystem. Synkronisering mellan olika maskinvara och operativsystem rekommenderas inte.

### Konfigurera projektet {#setting-up}

Innan du använder funktionen Kommandosynkronisering kontrollerar du att du har ett projekt och en kanal med innehåll som har konfigurerats för ditt projekt.

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
1. Klicka **Enhetshanteraren** i åtgärdsfältet.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Mer information om hur du registrerar en enhet finns i [Enhetsregistrering](/help/user-guide/device-registration.md)

1. I det här exemplet visas en Chrome-enhet och en Windows Player som två separata enheter. Båda enheterna pekar på samma skärm.
   ![image1](assets/command-sync6.png)

### Uppdaterar kanalinställningar

1. Navigera till **ChannelLobby**.
1. Klicka **Redigera** i åtgärdsfältet.
1. Klicka på hela kanalen enligt bilden nedan.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Klicka på skiftnyckelsikonen.
   ![image1](assets/command-sync/command-sync8-1.png)

1. I **Sida** anger du *synkad* nyckelord i **Strategi** fält.
   ![image1](assets/command-sync/command-sync9-1.png)


### Konfigurera en primär {#setting-up-primary}

1. Navigera till kontrollpanelen från **CommandSyncDemo** > **Platser**  > **Lobby** > **LobbyDisplay**. Klicka sedan på **Kontrollpanel** i åtgärdsfältet.
Lägg märke till de två enheterna (Chrome och Windows Player) i **ENHETER** enligt följande:
   ![image1](assets/command-sync/command-sync10-1.png)

1. Från **ENHETER** klickar du på den enhet som du vill ange som primär. I följande exempel visas hur du konfigurerar Chrome-enheten som primär enhet. Klicka **Ange som primär enhet**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Ange IP-adressen i **Ange som primär enhet** och klicka **Spara**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Du kan konfigurera flera enheter som primära enheter.

### Synkroniserar med primär {#sync-up-primary}

1. När du har angett Chrome-enheten som primär synkroniserar du den andra enheten (i det här fallet Windows Player) så att den synkroniseras med den primära.
Klicka på den andra enheten (i det här fallet Windows Player) på **ENHETER** panel och klicka **Synkronisera med primär enhet**.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Klicka på enheten i listan och klicka på **Spara**.

   >[OBS!]
   > The **Synkronisera med primär enhet** visas en lista med primära enheter. Välj önskad.

1. När enheten (Windows Player) synkroniseras till den primära (Chrome Player) kan du se enheten synkroniserad i **ENHETER** -panelen.

   ![image1](assets/command-sync/command-sync14-1.png)

### Synkronisering med den primära {#desync-up-primary}

När du har synkroniserat en eller flera enheter till en primär enhet kan du avsynkronisera tilldelningen från den enheten.

>[!NOTE]
>
>Om du avsynkroniserar en primär enhet bryts även länken till alla klientenheter som är kopplade till den primära enheten.

Följ stegen nedan för att ta bort synkroniseringen från den primära enheten:

1. Navigera till **ENHETER** och klicka på enheten.

1. Klicka **Desynkrona enheter** så att du kan desynkronisera klienten från den primära enheten.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Klicka **Bekräfta** om du vill avsynkronisera den valda enheten från den primära enheten.

   >[OBS!]
   > Om du klickar på den primära enheten och använder alternativet för avsynkronisering kommer alla enheter som är anslutna till den primära att avsynkroniseras i ett steg.
