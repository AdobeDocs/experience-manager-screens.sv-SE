---
title: Konfigurera agenter för skärmreplikering
description: Följ den här sidan för att få information om hur du konfigurerar agenter för skärmreplikering.
role: Developer
level: Intermediate
source-git-commit: 46b466d5d05700def4b2c290fa164fbdabae268a
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---


# Konfigurerar agenter för skärmreplikering {#configuring-screens-replication-agent}

På följande sida beskrivs hur du konfigurerar Screens Replication Agents.

## Syfte {#objective}

Agenten för skärmreplikering ansvarar för att pinga data som *användare*, *lösenord*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* och många fler sådana värden, från publicera till författare. Det är viktigt att konfigurera detta så att författaren kan visa enhetsping.

>[!NOTE]
>Mer information om agenter för skärmreplikering finns i [Skärmreplikeringsagenter och kommandon](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Du måste slutföra båda sektionerna för att slutföra konfigurationen för skärmreplikeringsagenten:

1. [Aktivera användare och uppdatera lösenordet](#enable-users)
1. [Uppdaterar inställningar för skärmreplikeringsagenten](#replicate-agent)

## Aktivera användare och uppdatera lösenordet {#enable-users}

Följ stegen nedan för att aktivera användare och uppdatera lösenordet för skärmmottagare-användare:

>[!NOTE]
>Av säkerhetsskäl bör du undvika att använda administratörslösenordet för skärmmottagare-användare.

1. Navigera till din AEM Author-instans.

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
   >Du bör ange det befintliga administratörslösenordet i **Ditt lösenord** fält.

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

## Uppdaterar inställningar för skärmreplikeringsagenten {#replicate-agent}

Följ avsnittet nedan för att uppdatera inställningarna i agenten för skärmreplikering:

>[!IMPORTANT]
>Du måste utföra följande steg på ALLA befintliga skärmreplikeringsagenter.

1. Navigera till AEM.

1. Klicka på verktygen —> **Distribution** —> **Replikering**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Klicka på **Agenter på författare**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Sök efter alla skärmreplikeringsagenter på författaren och klicka på länken enligt bilden nedan.

   >[!NOTE]
   >Sök efter alla skärmreplikeringsagenter. Namnet på skärmreplikeringsagenten kommer att innehålla en bokstav **S** i titeln.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Klicka på **Redigera**.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Kontrollera **Aktiverad** från **Inställningar** -fliken.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Navigera till **Transport** från **Agentinställningar** och uppdatera **Användare** till **screens-receiver-user** och ange samma lösenord som du angav tidigare i steg 8 av [Aktivera användare och uppdatera lösenordet](#enable-users).

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Klicka på **OK**.

1. När du är klar med de föregående stegen kan du klicka på **Testanslutning** för att verifiera anslutningen.

   ![bild](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Om anslutningsverifieringen lyckas har du slutfört konfigurationen av skärmreplikeringsagenten.