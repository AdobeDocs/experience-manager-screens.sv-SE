---
title: Versionsinformation för funktionspaket 202109
description: Följ den här sidan för att få information om AEM Screens Feature Pack 202105 släppt den 23 september 2021.
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: 898eb8e7e9b7442aead9fb6fb89c2646aef65e05
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Vi rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). Skärmar har underhållsstöd för AEM 6.3 Screens-plattformen.

## Tillgänglighet {#availability}

AEM Screens har släppt AEM 6.5 Feature Pack 9.

Du kan hämta det senaste funktionspaketet för AEM Screens 6.5.9 från [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) med din Adobe ID. Gå till fliken **Adobe Experience Manager** och sök efter **skärmar** för att få den senaste funktionspaketet med namnet **AEM 6.5 skärmar FP9**.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 202109 är 23 september 2021.

### Nyheter {#what-is-new}

* **Stöd för miniatyrbilder för videoklipp**

   Miniatyrbildsstöd för videor i stöds nu i AEM Screens. Innehållsförfattare kan definiera en miniatyrbild för videoklipp så att bilden kan användas som platshållare och testa uppspelning och målgruppsanpassning av innehållet medan videon färdigställs av rätt team. Bilden kan också användas om videouppspelningen misslyckas.
Mer information finns i Stöd för miniatyrbilder för videoklipp.

* **Grundläggande uppspelningsövervakning**

   AEM Screens har nu stöd för grundläggande uppspelningsövervakning. Spelaren rapporterar nu olika uppspelningsmått för varje ping (standardvärdet är 30 sekunder). Baserat på mätvärden ger det möjlighet att upptäcka olika kantfall (fastnålade upplevelser, tom skärm, schemaläggningsproblem osv.). Med den här funktionen kan teamet fjärrövervaka om en spelare spelar upp innehåll, förbättrar reaktiviteten till tomma skärmar eller trasiga upplevelser i fältet och minskar risken för att slutanvändaren får en trasig upplevelse.
Mer information finns i Grundläggande uppspelningsövervakning.

* **Uppdateringar av rapporten för innehållstilldelning**

   Tilldelningsrapporten för innehåll har nu optimerats och förbättrats med förbättrad användarupplevelse. Den hämtningsbara rapporten innehåller förbättrade spelarrelaterade enheter som platser, skärmar och enheter på en kalkylbladsflik och information om innehållsleverantören, t.ex. kanaler och resurser på en annan flik.

* **Stöd för V3-manifestationer**

   Du kan nu konfigurera Dispatcher för manifestversion v3. Mer information finns i [Configuring Dispatcher for Manifest Version v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3).
Om du dessutom använder anpassade komponenter som en del av v3-manifestet läser du [Mall för anpassade hanterare](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).


### Felkorrigeringar {#bug-fixes}

**Spelarsida**

* Åtgärdade fel vid filcachning genom att ersätta resurser med återgivningar.

* Spelarna visar nu endast resursrenderingar om det finns renderingsmappning.

* Du kan nu konfigurera slackvarningar baserat på skräppostloggar.

* Förbättrad ping för att autentisera igen om svaret inte är giltigt i JSON.

* Numeriska kanalnamn/roller orsakade en tom skärm.

* Hämta optimerade renderingar via SmartSync.

* Mappningen omvandlades till en lista med återgivningsnycklar.

* Åtkomsten till `cmd.exe` och `reg.exe` i Windows-spelaren har tagits bort.

* En spelare måste rapportera sin senaste lyckade uppspelningshändelse.

* En spelare måste rapportera sin uppspelningsstatus.

* Player hämtar inte resurser igen när `ALL`-cachen har rensats.

* Som spelaradministratör kan du nu välja ett spelarnamn.

* Att kanaltilldelning tas bort från visningen återspeglas inte i spelaren.

* Om spelaren läses in igen medan kanaluppdateringen hämtas, ignorerar spelaren uppdateringen.

* Den inbäddade sidkomponenten respekterar nu pekhändelser.

* Fjärretablering av Tizen-spelaren stöds nu.

**Serversida**

* Målvideon visas inte
* Ansiktsvillkor vid sändning av visningsdata till efterföljande aktiviteter.

* Kanalförhandsgranskning fungerar inte för kanaler som innehåller videoklipp.

* Förhandsgranskningsläget är tomt för den delade skärmkanalen.

* Videominiatyrbilder återges tomma med aktiverade adaptiva renderingar.

* Uppdatera automatiskt kanalmanifestet om den refererade sidan publiceras.

* Borttagna enheter blockerar nu inte skärmreplikeringskön.

* Manifestet innehöll inte riktat innehåll eller platsinbäddade sidor. Detta har nu åtgärdats.

* Ny kärnbildkomponent läggs nu till i kanalmanifestet.

* Hämtning av optimerade återgivningar via SmartSync stöds nu.

* Spela upp optimerad återgivning för alla resurser.

* Stöd för flera typer av innehållsleverantörer har lagts till

* Strategin för uppspelning av inbäddad sekvens har brutits och detta har nu åtgärdats.

* Offlinemanifest med begärandeparametern `wcmmode` för HTML-posten, vilket gör den otillgänglig.

* En tom dynamisk inbäddad sekvens orsakade ibland en tom skärm.

* Spelaren rapporterar nu sin uppspelningsstatus.

* Videon spelades upp i `Tiny mode` och spelades inte upp som helskärmsvideo på enheten. Problemet har åtgärdats nu.

### Lanserade AEM Screens-spelare {#released-aem-screens-players}

Följande AEM Screens-spelare finns för AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### AEM Screens Player - nedladdningar  {#aem-screens-player-downloads}

Om du vill hämta den senaste AEM Screens-spelaren och läsa mer om felkorrigeringarna kan du läsa **[AEM Screens Player Downloads](https://download.macromedia.com/screens/index.html)**.
