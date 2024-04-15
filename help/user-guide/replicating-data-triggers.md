---
title: Replikera datautlösare till publiceringsservrar
description: Lär dig hur du replikerar datautlösare till publiceringsservern för AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Replikera datutlösare till publiceringsservrar {#replicating-data-triggers}

När du använder ContextHub och AEM Target Engine för att anpassa innehåll baserat på datautlösare i en författar-/publiceringskonfiguration, replikeras inte alla ContextHub- och personaliseringsrelaterade konfigurationer automatiskt med kanalerna när de publiceras.

På den här sidan får du hjälp att lära dig de manuella steg som krävs för att publicera dessa konfigurationer separat.

Det handlar om manuell publicering:

1. Konfiguration av ContextHub Store- och UI-moduler
1. Målgrupper inom personalisering
1. Personaliseringsaktiviteter

## Steg för replikering av datautlösare till Publish Server {#replicating-data-triggers-publish}

Följ stegen nedan för att replikera datautlösarna till publiceringsservern.

### Steg 1: Replikerar ContextHub-konfigurationer {#replicating-contexthub-configurations}

1. Navigera till **verktyg** > **Distribution** > **Distribution** > **Publish Agent** och väljer publiceringsagent så att du kan konfigurera inställningarna.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Du kan också använda `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` för att navigera direkt till skärmen för att konfigurera och testa anslutningen.

1. Välj **Testanslutning** från åtgärdsfältet så att du kan validera kommunikationen mellan författaren och publiceringsinstansen, vilket visas i följande exempel:

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Om testet misslyckas korrigerar du replikeringsagentens konfiguration mellan författaren och publiceringsinstansen. Se [Felsökning av testanslutning](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) för mer information.

1. Välj **Lägg till** från **Distributionsagent** skärmträd och välj konfigurationssökvägen för projektet, till exempel `/conf/screens/settings/cloudsettings/configuration`.

1. Välj **Skicka**.

### Replikera målgrupperna {#replicating-audiences}

1. Navigera till AEM > **Personalisering** > **Målgrupper** eller använda `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` navigera direkt.

1. Gå ned i projektmappen, till exempel `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Välj alla målgrupper och segment i användargränssnittet.

1. Välj **Hantera publikation** i åtgärdsfältet.

1. Välj **Nästa** och **Publicera**.

### Replikera aktiviteterna  {#replicating-activities}

1. Navigera till AEM > **Personalisering** > **Verksamhet** eller använda `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` navigera direkt.

1. Gå ned i projektmappen, det vill säga `/content/campaigns/screens/…`.

1. Välj alla aktiviteter i användargränssnittet.

1. Välj **Hantera publikation** i åtgärdsfältet.

1. Välj **Nästa** och **Publicera**.

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

1. Navigera till Verktyg > **Distribution** > **Distribution** > **Publish Agent**.

1. Välj **Redigera** från åtgärdsfältet och kontrollera att slutpunktens URL i **Importerarslutpunkter** fältet pekar också på publiceringsserverns URL i Distribution Agent.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Om du inte använder standardadministratörsautentiseringsuppgifterna måste du konfigurera distributionsagenten med ett annat användarnamn och lösenord.

   Följ stegen nedan:

   1. Navigera till Verktyg > **Operationer** > **Webbkonsol** `http://localhost:4502/system/console/configMgr`så att du kan öppna **Adobe Experience Manager Web Console**.
   1. Sök efter **Transportreferenser för Apache Sling Distribution - Användarreferenser baserade DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Skapa en konfiguration genom att fylla i **Namn**, **Användarnamn** och **lösenord**, till exempel *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Välj **Spara**
   1. Använd `Cmd +F` att söka efter **Apache Sling Distribution Agent - Forward Agents Factory** för att öppna konfigurationerna och söka efter **Transporthemlighetsprovider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Uppdatera `(name=default)` med `(name=slingTransportSecretProvider)`.
   1. Välj **Spara** och kör testanslutningen igen från **Distributionsagent** från AEM igen.
