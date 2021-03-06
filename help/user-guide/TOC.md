---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Hjälp om Adobe Experience Manager Screens
breadcrumb-title: AEM Screens Guide
user-guide-description: Lär dig använda en lösning för digital signering som gör att du kan publicera dynamiska och interaktiva digitala upplevelser och interaktioner.
translation-type: tm+mt
source-git-commit: dae7744bd8efb99a16807f0651cbcaff5514b73b
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 1%

---


# AEM Screens användarhandbok {#user-guide}

+ [Introduktion till skärmar](aem-screens-introduction.md)
+ Översikt och snabbstartsguide {#overview}
   + [Kickstart Guide](kickstart-for-aem-screens.md)
   + [Guide till bästa praxis för skärmar](https://docs.adobe.com/content/help/en/experience-manager-screens/using/about-guide.html)
   + [Nyckeltermer](screens-glossary.md)
+ Grundläggande om nätverk för digitala signaturer {#digital-signage-network}
   + [Del 1: Projektroller och ansvarsområden](project-roles-responsibilities.md)
   + [Del 2: Att tänka på när projekt är omfång](project-considerations.md)
   + [Del 3: Testning, POC, piloter &amp; Rollouts](testing-pocs-pilots-rollouts.md)
   + [Del 4: Projektledning och driftsättning](project-management-and-deployment.md)
   + [Del 5: Supportöverväganden](support-considerations.md)
+ Konfiguration och administration {#administering}
   + [Konfigurationer för skärmar](configuring-screens-introduction.md)
   + [Konfigurera Dispatcher-konfigurationer](dispatcher-configurations-aem-screens.md)
   + [Installera skärmuppspelaren](installing-screens-player.md)
   + [Ansluta skärmuppspelaren](working-with-screens-player.md)
   + [Enhetsregistrering](device-registration.md)
   + [Konfigurera åtkomstkontrollistor](setting-up-acls.md)
   + [AEM Screens Security Checklist](security-checklist.md)
   + [Övergång från ContentSync till SmartSync](smartsync.md)
   + [Ny projektimporterare från fil](project-importer.md)
   + [Replikera datutlösare till publiceringsservrar](replicating-data-triggers.md)
   + Klientspecifika överväganden {#installing-client}
      + [Chrome OS Player](implementing-chrome-os-player.md)
      + [Använda Chrome Player som ett tillägg för felsökning](using-chrome-player-as-an-extension.md)
      + [Android Player](implementing-android-player.md)
      + [Massetablering av Android Player med Enterprise Mobility Management](using-emm-bulkprovision-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Tizen Player](tizen-player.md)
      + [Automatisk registrering av spelare](auto-registration-players.md)
   + Författarpublicera {#author-publish}
      + [Författare/Publicera arkitektur - översikt](author-publish-architecture-overview.md)
      + [Konfigurera författare och publicera](author-and-publish.md)
   + Analysintegrering med AEM Screens {#analytics-integration}
      + [Adobe Analytics Integration](adobe-analytics-integration-aem-screens.md)
      + [Konfigurera Adobe Analytics med AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Exempel på redigerings- och användningsfall {#authoring}
   + Konfigurera ett skärmprojekt {#setting-up-projects}
      + [Skapa och hantera projekt](creating-a-screens-project.md)
      + [Skapa och hantera kanaler](managing-channels.md)
      + [Skapa och hantera skärmar](managing-displays.md)
      + [Skapa och hantera platser](managing-locations.md)
      + [Skapa och hantera scheman](managing-schedules.md)
      + [Hantera enheter](managing-devices.md)
      + Tilldela kanaler {#assigning-channels}
         + [Kanaltilldelning](channel-assignment-latest-fp.md)
         + [Kanaltilldelning: Äldre AEM Screens-funktionspaket](channel-assignment.md)
   + Använda kärnfunktioner {#product-features}
      + [Textövertäckning](text-overlay.md)
      + [Uppdatera gruppvis offline](bulk-offline-update.md)
      + [AEM Screens Notifications Service](screens-notifications-service.md)
      + [Använda Experience Fragments](experience-fragments-in-screens.md)
      + [Aktivering på tillgångsnivå](asset-level-scheduling.md)
      + [Aktivering på kanalnivå](channel-level-activation.md)
      + [Skapa och hantera en Live-kopia](managing-livecopy.md)
      + [Skapa ett arbetsflöde för videoutfyllnad](creating-a-video-padding-workflow.md)
      + [Lägga till komponenter i en kanal](adding-components-to-a-channel.md)
      + [Inbäddade sekvenser](embedded-sequences.md)
      + [Layout med flera zoner](multi-zone-layout-aem-screens.md)
      + [Videoåtergivningar](generating-renditions.md)
      + [Dynamisk inbäddad sekvens](dynamic-embedded-sequences.md)
      + [Varaktighet för massbildsuppspelning på kanalnivå](channel-level-image-playback.md)
      + [Synkronisera kommandon](using-command-sync.md)
      + [Skapa med Data Triggers](authoring-data-triggers.md)
      + [Röstigenkänning](voice-recognition.md)
      + [Tilldelningsrapport för innehåll](content-assignment-report.md)
   + Hantera innehållsuppdateringar {#content-updates}
      + [On Demand Content Update](on-demand-content.md)
      + [Uppdatering av innehållet som en tjänst](content-update-as-a-service.md)
      + [Content Update using Screens Launch](launches.md)
   + Exempel på användningsfall {#use-case-examples}
      + [Nödkanaler](emergency-channel.md)
      + [Temperaturaktivering i resecentret](local-temperature-activation.md)
      + [Aktivering av hotellreservation](hospitality-reservation-activation.md)
      + [Målinställd aktivering för butikslager](retail-inventory-activation.md)
      + [Använda övergångar](applying-transitions.md)
      + [Övergångar mellan flera zoner och en zon](multizone-to-singlezone.md)
      + [Ta över kanal för engångsbruk](single-use-takeover-channel.md)
      + [Permanent användning, TakeOver Channel](perpetual-takeover-channel.md)
+ Resurser för utvecklare och API {#developing}
   + [REST API:er](rest-api.md)
   + [Utveckla en anpassad komponent för AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Offlinekanaler](offline-channels.md)
   + [Utöka en AEM Screens-komponent](extending-component-tutorial-develop.md)
   + [Skapa komponenter](creating-components.md)
   + [Bädda in ett REACT-program med AEM och integrera med AEM Screens Analytics](embedding-react-app.md)
   + [ContextHub konfigureras i AEM Screens](configuring-context-hub.md)
   + [Skapa anpassade mallar för MultiZone-layouter](creating-custom-templates-multizone-layouts.md)
   + [Använda anpassad profilering och formatering för textövertäckningar](custom-branding-text-overlays.md)
+ Felsökning och vanliga frågor och svar {#troubleshooting}
   + [Vanliga frågor om AEM Screens](aem-screens-faqs.md)
   + [Felsökning av Device Control Center](monitoring-screens.md)
   + [Videouppspelningskonfiguration](troubleshoot-videos.md)
+ Versionsinformation {#release-notes}
   + [Versionsinformation för funktionspaket 2013](release-notes-fp-202103.md)
   + [Versionsinformation för funktionspaket 2011](release-notes-fp-202011.md)
   + [Versionsinformation för funktionspaket 2008](release-notes-fp-202008.md)
   + [Versionsinformation för funktionspaket 2004](release-notes-fp-202004.md)
   + [Versionsinformation för funktionspaket 2001](release-notes-fp-202001.md)
   + [Versionsinformation för funktionspaket 201909](release-notes-fp-201909.md)
   + [Versionsinformation för funktionspaket 201907](release-notes-fp-201907.md)
   + [Versionsinformation för funktionspaket 201905](screens-release-notes-fp-201905.md)
   + [Versionsinformation för funktionspaket 201812](release-notes-fp-201812.md)
   + [Versionsinformation för funktionspaket 201809](screens-release-notes.md)
