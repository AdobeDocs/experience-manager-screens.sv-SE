---
title: Replikera datautlösare till publiceringsservrar
description: Lär dig hur du replikerar datautlösare till publiceringsservern för AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Replikera datutlösare till publiceringsservrar {#replicating-data-triggers}

När du använder ContextHub och AEM Target Engine för att anpassa innehåll baserat på datautlösare i en författar-/publiceringskonfiguration, replikeras inte alla ContextHub- och Personalization-relaterade konfigurationer automatiskt med kanalerna när de publiceras.

På den här sidan får du hjälp att lära dig de manuella steg som krävs för att publicera dessa konfigurationer separat.

Det handlar om att manuellt publicera följande:

1. Konfiguration av ContextHub Store- och UI-moduler
1. Personalization målgrupper
1. Personalization-verksamhet

## Steg för replikering av datautlösare till Publish Server {#replicating-data-triggers-publish}

Följ stegen nedan för att replikera datautlösarna till publiceringsservern.

### Steg 1: Replikerar ContextHub-konfigurationer {#replicating-contexthub-configurations}

1. Navigera till **Verktyg** > **Distribution** > **Distribution** > **Publish Agent** och klicka på publiceringsagenten så att du kan konfigurera inställningarna.

   ![bild1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Du kan också använda `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` för att navigera direkt till skärmen för att konfigurera och testa anslutningen.

1. Klicka på **Testa anslutning** i åtgärdsfältet så att du kan validera kommunikationen mellan författaren och publiceringsinstansen enligt följande:

   ![bild1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Om testet misslyckas korrigerar du replikeringsagentens konfiguration mellan författaren och publiceringsinstansen. Mer information finns i [Felsökning av testanslutning](/help/user-guide/replicating-data-triggers.md#troubleshoot-test).

1. Klicka på **Lägg till** i skärmträdet **Distributionsagent** och klicka på konfigurationssökvägen för ditt projekt, till exempel `/conf/screens/settings/cloudsettings/configuration`.

1. Klicka på **Skicka**.

### Replikera målgrupperna {#replicating-audiences}

1. Navigera till din AEM-instans > **Personalization** > **Publiker** eller använd `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` för att navigera direkt.

1. Gå ned i projektmappen, till exempel `/conf/screens/`.

   ![bild1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Klicka på alla målgrupper och segment i användargränssnittet.

1. Klicka på **Hantera publikation** i åtgärdsfältet.

1. Klicka på **Nästa** och **Publicera**.

### Replikera aktiviteterna {#replicating-activities}

1. Navigera till din AEM-instans > **Personalization** > **Aktiviteter** eller använd `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` för att navigera direkt.

1. Gå ned i projektmappen, det vill säga `/content/campaigns/screens/…`.

1. Klicka på alla aktiviteter i användargränssnittet.

1. Klicka på **Hantera publikation** i åtgärdsfältet.

1. Klicka på **Nästa** och **Publicera**.

>[!IMPORTANT]
>
>Replikering av ContextHub-konfigurationer och målgrupper sker under projektkonfigurationen samtidigt som aktiviteter replikeras och krävs varje gång målinriktningen ändras inuti en kanal.

#### Resultat {#result}

Om replikeringen lyckas bör du visa följande struktur på publiceringsinstansen (eller liknande för ditt projekt):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Felsökning av testanslutning {#troubleshoot-test}

Om testanslutningen misslyckas när ContextHub-konfigurationerna replikeras, följ avsnittet nedan för att felsöka problemet:

1. Navigera till **Verktyg** > **Distribution** > **Distribution** > **Publiceringsagent**.

1. Klicka på **Redigera** i åtgärdsfältet och kontrollera att slutpunkts-URL:en i fältet **Importerarslutpunkter** också pekar på publiceringsserverns URL i distributionsagenten.
   ![bild1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Om du inte använder standardadministratörsautentiseringsuppgifterna måste du konfigurera distributionsagenten med ett annat användarnamn och lösenord.

   Följ stegen nedan:

   1. Navigera till Verktyg > **Åtgärder** > **Webbkonsol** `http://localhost:4502/system/console/configMgr`så att du kan öppna **Adobe Experience Manager Web Console**.
   1. Sök efter **`Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider`**

      ![bild1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Skapa en konfiguration genom att fylla i **Namn**, **Användarnamn** och **lösenord**, till exempel *slingTransportSecretProvider*.

      ![bild1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Klicka på **Spara**
   1. Använd `Cmd +F` för att söka efter **Apache Sling Distribution Agent - Forward Agents Factory** för att öppna konfigurationerna och söka efter **Transporthemlighetsprovider**.

      ![bild1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Uppdatera `(name=default)` med `(name=slingTransportSecretProvider)`.
   1. Klicka på **Spara** och kör testanslutningen igen från skärmen **Distributionsagent** från din AEM-instans igen.
