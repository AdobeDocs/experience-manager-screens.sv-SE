---
title: Konfigurera agenter för skärmreplikering
description: Lär dig hur du konfigurerar agenter för skärmreplikering.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 3%

---

# Konfigurerar agenter för skärmreplikering {#configuring-screens-replication-agent}

På följande sida beskrivs hur du konfigurerar Screens Replication Agents.

## Syfte {#objective}

Agenten för skärmreplikering ansvarar för att hämta kommandodata som, *användare*, *lösenord*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* och många fler sådana värden, från publicera till författare. Det är viktigt att konfigurera detta så att författaren kan visa enhetsping.

>[!NOTE]
>Mer information om agenter för skärmreplikering finns i [Skärmreplikeringsagenter och kommandon](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Fyll i båda avsnitten om du vill slutföra konfigurationen för skärmreplikeringsagenten:

1. [Aktivera användare och uppdatera lösenordet](#enable-users)
1. [Uppdaterar inställningar för skärmreplikeringsagenten](#replicate-agent)

## Aktivera användare och uppdatera lösenordet {#enable-users}

Följ stegen nedan för att aktivera användare och uppdatera lösenordet för `screens-receiver-user`:

>[!NOTE]
>Av säkerhetsskäl bör du undvika att använda adminlösenordet för `screens-receiver-user`.

1. Navigera till AEM Author-instansen.

1. Välj verktyg > **Säkerhet** > **Användare**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Sök efter **`screens-receiver-user`**.

1. Välj **`screens-receiver-user`** och markera **Aktivera** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Välj **OK** för att bekräfta.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication3.png)

   När du har aktiverat användaren ser du **`screens-receiver-user`** as **Aktiverad** under **Status** fält.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Välj **`screens-receiver-user`** och markera **Egenskaper** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Välj **Ändra lösenord** under **Kontoinställningar** från **Information** enligt bilden nedan.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Ange ett nytt lösenord i dialogrutan **Ändra lösenord** och välj **Spara**.

   >[!NOTE]
   >Ange det befintliga administratörslösenordet i **Ditt lösenord** fält.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Välj **Spara och stäng**.

1. Välj **`screens-receiver-user`** och markera **Aktivera** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Välj **OK** för att bekräfta.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Välj **`screens-receiver-user`** och markera **Inaktivera** i åtgärdsfältet.

   >[!IMPORTANT]
   > Inaktiverar **`screens-receiver-user`** inaktiverar bara den här användaren från redigeringsinstansen och alla användare i publiceringsinstansen förblir aktiva. Markera inte **Inaktivera** från åtgärdsfältet, eftersom inaktivering tar bort användaren även från Publishing-instanserna.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Välj **OK** för att bekräfta.

## Uppdaterar inställningar för skärmreplikeringsagenten {#replicate-agent}

Följ avsnittet nedan för att uppdatera inställningarna i AEM Screens Replication Agent:

>[!IMPORTANT]
>Utför följande steg på ALLA befintliga AEM Screens-replikeringsagenter.

1. Navigera till AEM.
1. Välj verktyg > **Distribution** > **Replikering**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Välj **Agenter på författare**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Sök efter alla AEM Screens Replication-agenter på författaren och välj länken enligt bilden nedan.

   >[!NOTE]
   >Sök efter alla AEM Screens-replikeringsagenter. Namnet på skärmreplikeringsagenten innehåller bokstaven **S** i titeln.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Välj **Redigera**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Kontrollera **Aktiverad** från **Inställningar** -fliken.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Navigera till **Transport** -fliken från **Agentinställningar** och uppdatera **Användare** till **`screens-receiver-user`** och ange samma lösenord som du angav tidigare i steg 8 av [Aktivera användare och uppdatera lösenordet](#enable-users).

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Välj **OK**.

1. När du är klar med stegen ovan väljer du **Testanslutning** för att verifiera anslutningen.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Om anslutningsverifieringen lyckas har du slutfört konfigurationen av skärmreplikeringsagenten.
