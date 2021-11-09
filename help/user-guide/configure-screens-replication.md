---
title: Konfigurera agenten för skärmreplikering
description: Följ den här sidan för att få information om hur du konfigurerar Screens Replication Agent.
role: Developer
level: Intermediate
source-git-commit: 75250cf11254499dbb30b3a5b04b1849753ea266
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 6%

---


# Konfigurerar agenten för skärmreplikering {#configuring-screens-replication-agent}

I det här avsnittet beskrivs hur du konfigurerar Screens-replikeringsagenten.

## Aktivera användare och uppdatera lösenordet {#enable-users}

Följ stegen nedan:

1. Navigera till AEM.

1. Klicka på verktygen —> **Säkerhet** —> **Användare**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Sök efter **screens-receiver-user**.

1. Välj **screens-receiver-user** och klicka på **Aktivera** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Klicka på **OK** för att bekräfta.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication3.png)

   När du har aktiverat användaren visas **screens-receiver-user** as **Aktiverad** under **Status** fält.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Välj **screens-receiver-user** och klicka på **Egenskaper** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Klicka på **Ändra lösenord** under **Kontoinställningar** från **Detaljer** enligt bilden nedan.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Ange ett nytt lösenord i dialogrutan **Ändra lösenord** och klicka på **Spara**.

   >[!NOTE]
   >Du bör ange **admin** in **Ditt lösenord** fält.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Klicka på **Spara och stäng**.

1. Välj **screens-receiver-user** och klicka på **Aktivera** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Klicka på **OK** för att bekräfta.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Välj **screens-receiver-user** och klicka på **Inaktivera** i åtgärdsfältet.

   >[!IMPORTANT]
   > Inaktiverar **screens-receiver-user** inaktiverar bara den här användaren från författarinstansen och alla användare i publiceringsinstansen förblir aktiva. Klicka inte på **Inaktivera** i åtgärdsfältet, eftersom inaktivering tar bort användaren även från publiceringsinstanserna.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Klicka på **OK** för att bekräfta.

## Replikeringsagenten för skärmar uppdateras {#replicate-agent}

Följ avsnittet nedan för att uppdatera inställningarna i agenten för skärmreplikering:

1. Navigera till AEM.

1. Klicka på verktygen —> **Distribution** —> **Replikering**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Klicka på **Agenter på författare**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Klicka på länken enligt bilden nedan.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Klicka på **Redigera**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Kontrollera **Aktiverad** från **Inställningar** -fliken.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Navigera till **Transport** från **Agentinställningar** och ange samma lösenord som du angav tidigare i steg 8 av [Aktivera användare och uppdatera lösenordet](#enable-users). Klicka på **OK**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1f.png)

1. När du är klar med de föregående stegen kan du klicka på **Testanslutning** för att verifiera anslutningen.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Om anslutningsverifieringen lyckas har du slutfört konfigurationen av skärmreplikeringsagenten.