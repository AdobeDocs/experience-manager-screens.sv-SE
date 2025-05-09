---
cloud: Experience Cloud
product: experience manager
audience: end-user
user-guide-title: Hjälp med Adobe Experience Manager Screens
breadcrumb-title: Användarhandbok om AEM Screens
user-guide-description: Lär dig använda en lösning för digital signering som gör att du kan publicera dynamiska och interaktiva digitala upplevelser och interaktioner.
feature-set: Experience Manager Screens
feature: Content
role: User
source-git-commit: d8392b015c65e6bba35ba4c923d4f663e1121e0c
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 5%

---


# AEM Screens Användarhandbok {#user-guide}

+ [Introduktion till Screens](aem-screens-introduction.md)
+ Översikt och Kickstart-guide {#overview}
   + [Kickstart Guide](kickstart-for-aem-screens.md)
   + [Screens Best Practices Guide](https://experienceleague.adobe.com/sv/docs/experience-manager-screens/using/about-guide)
   + [Nyckeltermer](screens-glossary.md)
   + [Screens terminologi och begrepp](screens-concepts-feature-video-understand.md)
+ Grundläggande om nätverk för digital signering {#digital-signage-network}
   + [Del 1: Projektroller och ansvarsområden](project-roles-responsibilities.md)
   + [Del 2: Att tänka på som projekt omfång](project-considerations.md)
   + [Del 3: Testning, POC, piloter &amp; Rollouts](testing-pocs-pilots-rollouts.md)
   + [Del 4: Projektledning och driftsättning](project-management-and-deployment.md)
   + [Del 5: Supportöverväganden](support-considerations.md)
+ Konfiguration och administration {#administering}
   + [Konfigurera Screens Server](configuring-screens-introduction.md)
   + [Konfigurera Dispatcher Configurations](dispatcher-configurations-aem-screens.md)
   + [Installera Screens Player](installing-screens-player.md)
   + [Ansluta Screens Player](working-with-screens-player.md)
   + [Enhetsregistrering](device-registration.md)
   + [Konfigurera åtkomstkontrollistor](setting-up-acls.md)
   + [AEM Screens Security Checklist](security-checklist.md)
   + [Övergång från ContentSync till SmartSync](smartsync.md)
   + [Ny projektimporterare från fil](project-importer.md)
   + [Replikera datutlösare till publiceringsservrar](replicating-data-triggers.md)
   + [Konfigurera replikeringsagenter på Screens](configure-screens-replication.md)
   + Klientspecifika överväganden {#installing-client}
      + [Chrome OS Player](implementing-chrome-os-player.md)
      + [Använda Chrome Player som tillägg för felsökning](using-chrome-player-as-an-extension.md)
      + [Android](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Tizen Player](tizen-player.md)
      + [Cloud Player](implementing-cloud-player.md)
      + [Automatisk registrering av spelare](auto-registration-players.md)
      + [Använda fjärrkontrollen](implementing-remote-control.md)
   + Författarpublicering {#author-publish}
      + [Author-Publish Architectional Overview](author-publish-architecture-overview.md)
      + [Konfigurera författare och publicera](author-and-publish.md)
   + Analysintegrering med AEM Screens {#analytics-integration}
      + [Adobe Analytics Integration](adobe-analytics-integration-aem-screens.md)
      + [Konfigurera Adobe Analytics med AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Exempel på redigerings- och användningsexempel {#authoring}
   + Konfigurera ett Screens-projekt {#setting-up-projects}
      + [Skapa och hantera projekt](creating-a-screens-project.md)
      + [Skapa och hantera kanaler](managing-channels.md)
      + [Skapa och hantera skärmar](managing-displays.md)
      + [Skapa och hantera platser](managing-locations.md)
      + [Skapa och hantera scheman](managing-schedules.md)
      + [Hantera enheter](managing-devices.md)
      + Tilldelar kanaler {#assigning-channels}
         + [Kanaltilldelning](channel-assignment-latest-fp.md)
         + [Kanaltilldelning: Äldre AEM Screens-funktionspaket](channel-assignment.md)
   + Använda kärnproduktfunktioner {#product-features}
      + [Textövertäckning](text-overlay.md)
      + [Uppdatera gruppvis offline](bulk-offline-update.md)
      + [AEM Screens Notifications Service](screens-notifications-service.md)
      + [Använda upplevelsefragment](experience-fragments-in-screens.md)
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
      + [Använda taggar](tagging.md)
      + [Röstigenkänning](voice-recognition.md)
      + [Tilldelningsrapport för innehåll](content-assignment-report.md)
      + [Stöd för miniatyrbilder för videor](thumbnail-support.md)
      + [Använda adaptiva renderingar i AEM Screens](using-adaptive-renditions.md)
   + Hantera innehållsuppdateringar {#content-updates}
      + [On Demand Content Update](on-demand-content.md)
      + [Uppdatering av innehållet som en tjänst](content-update-as-a-service.md)
      + [Innehållsuppdatering med Screens Launch](launches.md)
   + Använd exempel på exempel {#use-case-examples}
      + [Nödkanaler](emergency-channel.md)
      + [Temperaturaktivering i resecentret](local-temperature-activation.md)
      + [Aktivering av hotellreservation](hospitality-reservation-activation.md)
      + [Målinställd aktivering för butikslager](retail-inventory-activation.md)
      + [Använda övergångar](applying-transitions.md)
      + [Övergångar mellan flera zoner och en zon](multizone-to-singlezone.md)
      + [Ta över kanal för engångsbruk](single-use-takeover-channel.md)
      + [Löpande användning av TakeOver Channel](perpetual-takeover-channel.md)
+ Resurser för utvecklare och API {#developing}
   + [REST API:er](rest-api.md)
   + [Utveckla en anpassad komponent för AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Offlinekanaler](offline-channels.md)
   + [Utöka en AEM Screens-komponent](extending-component-tutorial-develop.md)
   + [Skapa komponenter](creating-components.md)
   + [Bädda in ett REACT-program med AEM SPA Editor och integrera med AEM Screens Analytics](embedding-react-app.md)
   + [ContextHub konfigureras i AEM Screens](configuring-context-hub.md)
   + [Skapa anpassade mallar för MultiZone-layouter](creating-custom-templates-multizone-layouts.md)
   + [Använda anpassad profilering och formatering för textövertäckningar](custom-branding-text-overlays.md)
   + [Adaptiva renderingar: Arkitektur - översikt och konfigurationer](/help/user-guide/adaptive-renditions.md)
+ Felsökning och vanliga frågor {#troubleshooting}
   + [Vanliga frågor om AEM Screens](aem-screens-faqs.md)
   + [Felsökning av Device Control Center](monitoring-screens.md)
   + [Videouppspelningskonfiguration](troubleshoot-videos.md)
+ Versionsinformation {#release-notes}
   + [Versionsinformation för funktionspaket 20250327](release-notes-fp-20250327.md)
   + [Versionsinformation för funktionspaket 20250224](release-notes-fp-20250224.md)
   + [Versionsinformation för funktionspaket 20240715](release-notes-fp-20240715.md)
   + [Versionsinformation för funktionspaket 202401](release-notes-fp-20250215.md)
   + [Versionsinformation för funktionspaket 202401](release-notes-fp-202401.md)
   + [Versionsinformation för funktionspaket 20240116](release-notes-fp-20240116.md)
   + [Versionsinformation för funktionspaket 20240215](release-notes-fp-20240215.md)
   + [Versionsinformation för funktionspaket 202204](release-notes-fp-202204.md)
   + [Versionsinformation för funktionspaket 202203](release-notes-fp-202203.md)
   + [Versionsinformation för funktionspaket 2012](release-notes-fp-202112.md)
   + [Versionsinformation för funktionspaket 20109](release-notes-fp-202109.md)
   + [Versionsinformation för funktionspaket 202105](release-notes-fp-202105.md)
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
