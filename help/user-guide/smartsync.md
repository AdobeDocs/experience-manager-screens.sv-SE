---
title: Övergång från ContentSync till SmartSync
seo-title: Övergång från ContentSync till SmartSync
description: Följ den här sidan om du vill veta mer om funktionen SmartSync och hur du kan gå över från ContentSync till SmartSync.
seo-description: Följ den här sidan om du vill veta mer om funktionen SmartSync och hur du kan gå över från ContentSync till SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: 7832176cfb1e4647a49852ce382862978dddbfe2
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Övergång från ContentSync till SmartSync {#transitioning-from-contentsync-to-smartsync}

I det här avsnittet ges en översikt över SmartSync-funktionen och hur den minimerar belastningen på servern/lagringen och nätverkstrafiken för att minska kostnaderna.

## Översikt {#overview}

SmartSync är den senaste funktionen som används av AEM-skärmar. Den ersätter den nuvarande metoden som används för att cachelagra offlinekanaler och leverera dem till spelaren.

Det körs både på serversidan och på klientsidan.

**På serversidan**:

* Kanalernas innehåll, inklusive resurser, cachelagras i */var/contentsync*.
* Cachen visas för spelarna via ett manifest som beskriver det tillgängliga innehållet för en skärm.

**På klientsidan**:

* Spelaren uppdaterar innehållet baserat på manifestet som genereras ovan.

### Fördelar med SmartSync {#benefits-of-using-smartsync}

SmartSync-funktionen ger ett antal fördelar för ditt AEM Screens-projekt. Den tillåter

* Dramatisk minskning av nätverkstrafiken och lagringskraven på serversidan
* Spelaren hämtar resurser på ett intelligent sätt endast om resursen saknas eller har ändrats
* Lagringsoptimering på serversidan och klientsidan

>[!NOTE]
>
>Adobe rekommenderar starkt att du använder SmartSync för AEM-skärmsprojekt.

## Migrera från ContentSync till SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Om du redan har installerat AEM 6.3 Feature Pack 5 och AEM 6.4 Feature Pack 3 kan du aktivera SmartSync för resurser för att förbättra användningen av diskutrymme. Om du vill aktivera SmartSync följer du avsnittet nedan för att gå över från ContentSync till SmartSync, vilket aktiverar SmartSync.
>
>SmartSync är tillgängligt för Screens Player med servrar som stöds, AEM 6.4.3 FP3.
>
>Hämta den senaste spelaren genom att läsa [AEM Screens Player Downloads](https://download.macromedia.com/screens/) . I följande tabell beskrivs den lägsta spelarversion som krävs för varje plattform:

| **Plattform** | **Lägsta spelarversion som stöds** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

Följ stegen nedan för att gå över från ContentSync till SmartSync:

1. Migrering från ContentSync till SmartSync kräver att ContentSync-cachen rensas innan SmartSync aktiveras.

   Navigera till ContentSync-konsolen från din instans med länken ***https://localhost:4502/libs/cq/contentsync/content/console.html*** och klicka på **Rensa cache**, vilket visas i bilden nedan:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Alla innehållscache måste rensas innan SmartSync kan användas för första gången.

1. Gå till **Adobe Experience Manager Web Console Configuration** via AEM instance —> hammer icon —> **Operations** —> **Web Console**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web Console Configuration** öppnas. Sök efter *offlinekontaktentservice*.

   Om du vill söka efter egenskapen **Skärmar som är offline i innehållstjänsten** trycker du på **Kommando+F** för **Mac** och **Ctrl+F** för **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Klicka på **Spara** om du vill aktivera egenskapen **Skärmar som är offline för innehållstjänster** och använda SmartSync för AEM-skärmar.
1. När du har aktiverat SmartSync måste du navigera till projektet och klicka på **Uppdatera offlineinnehåll** *(från åtgärdsfältet),* enligt bilden nedan.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)