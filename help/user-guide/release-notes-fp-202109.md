---
title: Versionsinformation för funktionspaket 20109
description: Läs om AEM Screens Feature Pack 202109 som släpptes den 23 september 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 20109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). AEM Screens har underhållsstöd för AEM 6.3 Screens Platform.

## Tillgänglighet {#availability}

AEM Screens AEM 6.5 Feature Pack 9.

Du kan ladda ned det senaste funktionspaketet för AEM Screens 6.5.9 från [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Navigera till **Adobe Experience Manager** flik och sök efter **Skärmar** för att få det senaste funktionspaketet med namnet **AEM 6.5 skärmar FP9**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202109 är 23 september 2021.

### Nyheter {#what-is-new}

* **Stöd för miniatyrbilder för videor**

  Miniatyrbildsstöd för videor i stöds nu i AEM Screens. En innehållsförfattare definierar en miniatyrbild för videoklipp så att bilden används som platshållare. De testar också innehållsuppspelning och målinriktning på rätt sätt, medan själva videon färdigställs av rätt team. Bilden kan också användas om videouppspelningen misslyckas.
Se [Stöd för miniatyrbilder för videor](/help/user-guide/thumbnail-support.md) för mer information.

* **Grundläggande uppspelningsövervakning**

  AEM Screens har nu stöd för grundläggande uppspelningsövervakning. Spelaren rapporterar nu olika uppspelningsmått för varje ping (standardvärdet är 30 sekunder). Baserat på mätvärden upptäcker programmet olika kantfall (fastnålade upplevelser, tom skärm, schemaläggningsproblem osv.). Med den här funktionen kan teamet fjärrövervaka om en spelare spelar upp innehåll på rätt sätt och förbättrar reaktiviteten till tomma skärmar eller trasiga upplevelser på fältet. Det minskar också risken att slutanvändaren får en trasig upplevelse.
Se [Grundläggande uppspelningsövervakning](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring) för mer information.

* **Uppdateringar av rapporten för innehållstilldelning**

  Tilldelningsrapporten för innehåll har nu optimerats och förbättrats med en förbättrad användarupplevelse. Den hämtningsbara rapporten innehåller förbättrade spelarrelaterade enheter som platser, skärmar och enheter på en kalkylbladsflik och information om innehållsleverantören, t.ex. kanaler och resurser på en annan flik.
Se [Tilldelningsrapport för innehåll](/help/user-guide/content-assignment-report.md) för mer information.

* **Adaptiva renderingar**

  Med adaptiva renderingar kan enheterna automatiskt välja den bästa renderingen för en enhet baserat på kunddefinierade regler.

  Som AEM Screens-utvecklare kan du nu konfigurera enhetsspecifika resursrenderingar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt. Se [Adaptiva renderingar: Arkitektur - översikt och konfigurationer](/help/user-guide/adaptive-renditions.md) för mer information.

  Som AEM Screens Content Author kan du också konfigurera dina resurser så att de använder adaptiva renderingar. Du kan också migrera dina enheter för stora nätverk för att använda den här funktionen i dina AEM Screens-kanaler. Se [Använda adaptiva renderingar i AEM Screens](/help/user-guide/using-adaptive-renditions.md) för mer information.

* **Stöd för V3 Manifester**

  Du kan nu konfigurera Dispatcher för manifestversion v3. Om du vill aktivera v3-manifestet måste du:

   * Rensa alla väntande offlineinnehållsjobb i både författaren och publicerad.

      * Navigera till CRXDE Lite i Författare och Publicera.

      * Klicka på Verktyg > Fråga.

      * Använd `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`.

      * Detta listar alla offlineinnehållsjobb som körs eller väntar i kön.

      * Vänta tills inga fler offlineinnehållsjobb har returnerats från frågan.

   * Inaktivera ContentSync i `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

   * Aktivera SmartSync i `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

   * Uppdatera Dispatcher.

   * Uppdatera anpassad komponent.


   * Se [Konfigurera Dispatcher för manifestversion v3](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) för mer information.
   * Om du använder anpassade komponenter som en del av v3-manifestationer, se [Mall för anpassade hanterare](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers).


### Felkorrigeringar {#bug-fixes}

**Spelarsida**

* Åtgärdade fel vid filcachning genom att ersätta resurser med återgivningar.

* Spelarna visar nu endast resursrenderingar om det finns renderingsmappning.

* Förbättrad ping för att autentisera igen om svaret inte är en giltig JSON.

* Numeriska kanalnamn/roller orsakade en tom skärm.

* Hämta optimerade renderingar via SmartSync.

* Mappningen omvandlades till en lista med återgivningsnycklar.

* Åtkomst till `cmd.exe` och `reg.exe` i Windows Player.

* En spelare måste rapportera sin senaste lyckade uppspelningshändelse.

* En spelare måste rapportera sin uppspelningsstatus.

* Spelaren återhämtar inte resurser när `ALL` Cachen är rensad.

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

* Videominiatyrbilder återges tomma med aktiverade adaptiva renderingar.

* Uppdatera automatiskt kanalmanifestet om den refererade sidan publiceras.

* Borttagna enheter blockerar nu inte skärmreplikeringskön.

* Manifestet innehöll inte riktat innehåll eller platsinbäddade sidor. Detta har nu åtgärdats.

* Ny kärnbildkomponent har nu lagts till i kanalmanifestet.

* Hämtning av optimerade återgivningar via SmartSync stöds nu.

* Spela upp optimerad återgivning för alla resurser.

* Stöd för flera typer av innehållsleverantörer har lagts till

* Strategin för uppspelning av inbäddad sekvens har brutits och detta har nu åtgärdats.

* Offlinemanifest med parametern request `wcmmode` för html-post, vilket gör den oåtkomlig.

* En tom dynamisk inbäddad sekvens orsakade ibland en tom skärm.

* Spelaren rapporterar nu sin uppspelningsstatus.

* Videon spelades upp i `Tiny mode` och inte spelas upp som helskärmsvideo på enheten och problemet har åtgärdats nu.

### Släppta AEM Screens-spelare

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens Player - nedladdningar

Om du vill hämta den senaste AEM Screens-spelaren och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/index.html)**.
