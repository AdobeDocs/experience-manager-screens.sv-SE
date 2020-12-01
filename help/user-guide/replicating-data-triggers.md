---
title: Replikera datautlösare till publiceringsservrar
seo-title: Replikera datautlösare till publiceringsservern
description: Replikera datautlösare till publiceringsservern.
seo-description: Replikera datautlösare till publiceringsservern.
translation-type: tm+mt
source-git-commit: 081db31efda17ac12cdc88f79ed2f4e1fbfc7edf
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 2%

---


# Replikerar datutlösare till publiceringsservrar {#replicating-data-triggers}

När du använder ContextHub och AEM Target Engine för att anpassa innehåll baserat på datautlösare i en författar-/publiceringskonfiguration, replikeras inte alla ContextHub- och personaliseringsrelaterade konfigurationer automatiskt med kanalerna när de publiceras.

Följ den här sidan för att lära dig de manualer som krävs för att publicera dessa konfigurationer separat.

Det handlar om manuell publicering:

1. Konfiguration av ContextHub Store- och UI-moduler
1. Målgrupper inom personalisering
1. Personaliseringsaktiviteter

## Steg för replikering av datutlösare till publiceringsservern {#replicating-data-triggers-publish}

Följ stegen nedan för att replikera datautlösarna till publiceringsservern.

### Steg 1: Replikerar ContextHub-konfigurationer {#replicating-contexthub-configurations}

1. Navigera till **Verktyg** > **Distribution** > **Distribution** > **Publiceringsagent** och klicka på publiceringsagenten för att konfigurera inställningarna.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Du kan också använda `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` för att navigera direkt till skärmen för att konfigurera och testa anslutningen.

1. Klicka på **Testa anslutning** i åtgärdsfältet för att validera kommunikationen mellan författaren och publiceringsinstansen, vilket visas i bilden nedan.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Om testet misslyckas måste du åtgärda replikeringsagentens konfiguration mellan författaren och publiceringsinstansen. Mer information finns i [Troubleshooting Test Connection](/help/user-guide/replicating-data-triggers.md#troubleshoot-test).

1. Välj **Lägg till** i skärmträdet **Distributionsagent** och välj konfigurationssökvägen för projektet, till exempel `/conf/screens/settings/cloudsettings/configuration`.

1. Klicka på **Skicka**.

### Replikerar målgrupperna {#replicating-audiences}

1. Navigera till din AEM > **Personalisering** > **Publiker** eller använd `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` för att navigera direkt.

1. Gå ned i projektmappen, till exempel `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Välj alla målgrupper och segment i användargränssnittet.

1. Klicka på **Hantera publikation** i åtgärdsfältet.

1. Klicka på **Nästa** och **Publicera**.

### Replikerar aktiviteterna {#replicating-activities}

1. Navigera till din AEM > **Personalisering** > **Aktiviteter** eller använd `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` för att navigera direkt.

1. Gå ned i projektmappen, d.v.s. `/content/campaigns/screens/…`.

1. Välj alla aktiviteter i användargränssnittet.

1. Klicka på **Hantera publikation** i åtgärdsfältet.

1. Klicka på **Nästa** och **Publicera**.

>[!IMPORTANT]
>
>ContextHub-konfigurationer och målgrupper replikeras under projektkonfigurationen, medan aktiviteter replikeras och krävs varje gång målinriktningen ändras inuti en kanal.

#### Resultat {#result}

Om replikeringen lyckas bör du visa följande struktur på publiceringsinstansen (eller liknande för ditt projekt):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Felsökning av testanslutning {#troubleshoot-test}

Om testanslutningen misslyckas när ContextHub-konfigurationerna replikeras, följ avsnittet nedan för att felsöka problemet:

1. Navigera till Verktyg > **Distribution** > **Distribution** > **Publiceringsagent**.

1. Klicka på **Redigera** i åtgärdsfältet och kontrollera att slutpunkts-URL:en i **fältet Importerarslutpunkter** även pekar på publiceringsserverns URL i Distribution Agent.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Om du inte använder standardadministratörsautentiseringsuppgifterna måste du konfigurera distributionsagenten med ett annat användarnamn och lösenord.

   Följ stegen nedan:

   1. Gå till Verktyg > **Åtgärder** > **Webbkonsol** `http://localhost:4502/system/console/configMgr`för att öppna **Adobe Experience Manager Web Console-skärmen**.
   1. Sök efter **Transportreferenser för Apache Sling Distribution - Användarreferenser baserade DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Skapa en konfiguration genom att fylla i **Namn**, **Användarnamn** och **lösenord**, till exempel *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Klicka på **Spara**
   1. Använd `Cmd +F` för att söka efter **Apache Sling Distribution Agent - Forward Agents Factory** för att öppna konfigurationerna och söka efter **Transporthemlig provider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Uppdatera `(name=default)` med `(name=slingTransportSecretProvider)`.
   1. Klicka på **Spara** och kör testanslutningen igen från skärmen **Distributionsagent** från AEM igen.
