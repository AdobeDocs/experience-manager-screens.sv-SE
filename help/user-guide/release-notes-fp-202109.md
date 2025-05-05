---
title: Versionsinformation för funktionspaket 20109
description: Läs om AEM Screens Feature Pack 202109 som släpptes den 23 september 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 20109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). AEM Screens ger underhållsstöd för Screens AEM 6.3.

## Tillgänglighet {#availability}

AEM Screens AEM 6.5 Feature Pack 9.

Du kan hämta den senaste funktionspaketet för AEM Screens 6.5.9 från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Gå till fliken **Adobe Experience Manager** och sök efter **Screens** för att få den senaste funktionspaketet med namnet **AEM 6.5 Screens FP9**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202109 är 23 september 2021.

### Nyheter {#what-is-new}

* **Stöd för miniatyrbilder för videoklipp**

  Miniatyrbildsstöd för videor i stöds nu i AEM Screens. En innehållsförfattare definierar en miniatyrbild för videoklipp så att bilden används som platshållare. De testar också innehållsuppspelning och målgruppsanpassning, medan rätt team slutför själva videon. Bilden kan också användas om videouppspelningen misslyckas.
Mer information finns i [Stöd för miniatyrbilder för videoklipp](/help/user-guide/thumbnail-support.md).

* **Grundläggande uppspelningsövervakning**

  AEM Screens har nu stöd för grundläggande uppspelningsövervakning. Spelaren rapporterar nu olika uppspelningsmått för varje ping (standardvärdet är 30 sekunder). Baserat på mätvärden upptäcker programmet olika kantfall (fastnålade upplevelser, tom skärm, schemaläggningsproblem osv.). Med den här funktionen kan teamet fjärrövervaka om en spelare spelar upp innehåll på rätt sätt och förbättrar reaktiviteten till tomma skärmar eller trasiga upplevelser på fältet. Det minskar också risken att slutanvändaren får en trasig upplevelse.
Mer information finns i [Grundläggande uppspelningsövervakning](https://experienceleague.adobe.com/sv/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring).

* **Uppdateringar i rapporten för innehållstilldelning**

  Tilldelningsrapporten för innehåll har nu optimerats och förbättrats med en förbättrad användarupplevelse. Den hämtningsbara rapporten innehåller förbättrade spelarrelaterade entiteter. Sådana enheter kan vara platser, visningar och enheter på en kalkylbladsflik. Den innehåller även information om innehållsleverantören, till exempel kanaler och resurser på andra flikar.
Mer information finns i [Rapport om innehållstilldelning](/help/user-guide/content-assignment-report.md).

* **Adaptiva återgivningar**

  Med adaptiva renderingar kan enheten klicka på den bästa renderingen automatiskt för en enhet baserat på kunddefinierade regler.

  Som AEM Screens-utvecklare kan du nu konfigurera enhetsspecifika resursrenderingar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt. Mer information finns i [Adaptiva återgivningar: Arkitektöversikt och konfigurationer](/help/user-guide/adaptive-renditions.md).

  Som AEM Screens Content Author kan du också konfigurera dina resurser så att de använder adaptiva renderingar. Du kan också migrera dina enheter för stora nätverk för att använda den här funktionen i dina AEM Screens-kanaler. Mer information finns i [Använda adaptiva återgivningar i AEM Screens](/help/user-guide/using-adaptive-renditions.md).

* **Stöd för V3-manifestering**

  Nu kan du konfigurera Dispatcher för manifestversion v3. Så här aktiverar du v3-manifestet:

   * Rensa alla väntande offlineinnehållsjobb i både författaren och publicerad.

      * Navigera till CRXDE Lite i Författare och Publish.

      * Klicka på Verktyg > Fråga.

      * Använd `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']` i frågan.

      * Detta listar alla offlineinnehållsjobb som körs eller väntar i kön.

      * Vänta tills inga fler offlineinnehållsjobb har returnerats från frågan.

   * Inaktivera ContentSync i `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

   * Aktivera SmartSync i `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

   * Uppdatera Dispatcher.

   * Uppdatera den anpassade komponenten.


   * Mer information finns i [Konfigurera Dispatcher för manifestversion v3](https://experienceleague.adobe.com/sv/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3).
   * Om du använder anpassade komponenter som en del av v3-manifest läser du [Mall för anpassade hanterare](https://experienceleague.adobe.com/sv/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers).


### Felkorrigeringar {#bug-fixes}

**Spelarsida**

* Åtgärdade fel vid filcachning genom att ersätta resurser med återgivningar.

* Spelarna visar nu endast resursrenderingar om det finns renderingsmappning.

* Förbättrad ping för att autentisera igen om svaret inte är giltigt JSON.

* Numeriska kanalnamn/roller orsakade en tom skärm.

* Hämta optimerade renderingar med SmartSync.

* Mappningen omvandlades till en lista med återgivningsnycklar.

* Åtkomsten till `cmd.exe` och `reg.exe` i Windows Player har tagits bort.

* En spelare måste rapportera sin senaste lyckade uppspelningshändelse.

* En spelare måste rapportera sin uppspelningsstatus.

* Spelaren hämtar inte Assets igen när `ALL`-cachen rensas.

* Som spelaradministratör kan du nu välja ett spelarnamn.

* Att kanaltilldelning tas bort från visningen återspeglas inte i spelaren.

* Om spelaren läses in igen medan kanaluppdateringen hämtas, ignorerar spelaren uppdateringen.

* Den inbäddade sidkomponenten respekterar nu pekhändelser.

* Fjärretablering av Tizen-spelaren stöds nu.

**Serversida**

* Målvideon visas inte
* Ansiktsförhållanden vid sändning av visningsdata till efterföljande aktiviteter.

* Kanalförhandsgranskning fungerar inte för kanaler som innehåller videoklipp.

* Förhandsgranskningsläget är tomt för den delade skärmkanalen.

* Videominiatyrbilder återges tomma med aktiverade adaptiva återgivningar.

* Uppdatera automatiskt kanalmanifestet om den refererade sidan publiceras.

* Borttagna enheter blockerar nu inte Screens replikeringskö.

* Manifestet innehöll inte riktat innehåll eller platsinbäddade sidor. Detta fel har åtgärdats.

* En ny kärnbildskomponent läggs nu till i kanalmanifestet.

* Hämtning av optimerade återgivningar via SmartSync stöds nu.

* Spela upp optimerad återgivning för alla resurser.

* Stöd för flera typer av innehållsleverantörer har lagts till

* Uppspelningsstrategin för den inbäddade sekvensen har brutits och det här felet har nu åtgärdats.

* Offlinemanifest med begärandeparametern `wcmmode` för html-post, vilket gör det oåtkomligt.

* En tom dynamisk inbäddad sekvens orsakade ibland en tom skärm.

* Spelaren rapporterar nu sin uppspelningsstatus.

* Videon spelades upp i `Tiny mode` och spelades inte upp som helskärmsvideo på enheten. Problemet har åtgärdats nu.

### Släppta AEM Screens-spelare

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens Player - nedladdningar

Om du vill hämta den senaste versionen av AEM Screens Player och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player-hämtningar](https://download.macromedia.com/screens/index.html)**.
