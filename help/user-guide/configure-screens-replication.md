---
title: Konfigurera Screens Replication Agents
description: Läs om hur du konfigurerar Screens Replication Agents.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 3%

---

# Konfigurera Screens Replication Agents {#configuring-screens-replication-agent}

På följande sida beskrivs hur du konfigurerar Screens Replication Agents.

## Syfte {#objective}

Screens Replication Agent ansvarar för att hämta kommandodata som *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* och många fler sådana värden, från publicering till författare. Det är viktigt att konfigurera den här agenten så att författaren kan visa enhetsping.

>[!NOTE]
>Mer information om Screens replikeringsagenter finns i [Screens replikeringsagenter och kommandon](https://experienceleague.adobe.com/sv/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Fyll i båda avsnitten om du vill slutföra konfigurationen för Screens Replication Agent:

1. [Aktivera användare och uppdatera lösenordet](#enable-users)
1. [Uppdaterar inställningar för Screens Replication Agent](#replicate-agent)

## Aktivera användare och uppdatera lösenordet {#enable-users}

Följ stegen nedan för att aktivera användare och uppdatera lösenordet för `screens-receiver-user`:

>[!NOTE]
>Av säkerhetsskäl bör du undvika att använda administratörslösenordet för `screens-receiver-user`.

1. Navigera till din instans av AEM författare.

1. Klicka på Verktyg > **Dokumentskydd** > **Användare**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Sök efter **`screens-receiver-user`**.

1. Klicka på **`screens-receiver-user`** och klicka på **Aktivera** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Bekräfta genom att klicka på **OK**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication3.png)

   När du har aktiverat användaren visas **`screens-receiver-user`** som **Aktiverad** under fältet **Status**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Klicka på **`screens-receiver-user`** och klicka på **Egenskaper** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Klicka på **Ändra lösenord** under **Kontoinställningar** på fliken **Detaljer** enligt bilden nedan.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Ange ett nytt lösenord i dialogrutan **Ändra lösenord** och klicka på **Spara**.

   >[!NOTE]
   >Ange det befintliga administratörslösenordet i fältet **Lösenord**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Klicka på **Spara och stäng**.

1. Klicka på **`screens-receiver-user`** och klicka på **Aktivera** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Bekräfta genom att klicka på **OK**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Klicka på **`screens-receiver-user`** och klicka på **Inaktivera** i åtgärdsfältet.

   >[!IMPORTANT]
   > Om du inaktiverar **`screens-receiver-user`** inaktiveras bara den här användaren från redigeringsinstansen, och alla användare i publiceringsinstansen förblir aktiva. Klicka inte på **Inaktivera** i åtgärdsfältet, eftersom inaktiveringen tar bort användaren även från publiceringsinstanserna.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Bekräfta genom att klicka på **OK**.

## Uppdaterar inställningar för Screens Replication Agent {#replicate-agent}

Följ avsnittet nedan för att uppdatera inställningarna i AEM Screens Replication Agent:

>[!IMPORTANT]
>Utför följande steg på ALLA befintliga AEM Screens-replikeringsagenter.

1. Navigera till AEM.
1. Klicka på verktyg > **Distribution** > **Replikering**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Klicka på **Agenter på författaren**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Sök efter alla AEM Screens Replication Agents på författaren och klicka på länken, vilket visas i bilden nedan.

   >[!NOTE]
   >Sök efter alla AEM Screens-replikeringsagenter. Namnet på Screens-replikeringsagenten innehåller bokstaven **S** i titeln.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Klicka på **Redigera**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Kontrollera **Aktiverad** på fliken **Inställningar**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Navigera till fliken **Transport** i dialogrutan **Agentinställningar** och uppdatera **Användare** till **`screens-receiver-user`** och ange samma lösenord som du angav tidigare i steg 8 i [Aktivera användare och uppdatera lösenordet](#enable-users).

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Klicka på **OK**.

1. När du har slutfört de föregående stegen klickar du på **Testa anslutning** för att verifiera anslutningen.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Om anslutningsverifieringen lyckas har du konfigurerat Screens Replication Agent.
