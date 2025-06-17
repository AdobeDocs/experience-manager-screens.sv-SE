---
title: Övergång från ContentSync till SmartSync
description: Läs mer om SmartSync-funktionen och hur du kan gå över från ContentSync till SmartSync.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Övergång från ContentSync till SmartSync {#transitioning-from-contentsync-to-smartsync}

I det här avsnittet ges en översikt över SmartSync-funktionen och hur den minimerar belastningen på servern/lagringen och nätverkstrafiken för att minska kostnaderna.

## Ökning {#overview}

SmartSync är den senaste mekanismen som används av AEM Screens. Den ersätter den nuvarande metoden som används för att cachelagra offlinekanaler och leverera dem till spelaren.

Det körs både på serversidan och på klientsidan.

**På serversidan**

* Kanalernas innehåll, inklusive resurser, cachelagras i *`/var/contentsync`*.
* Cachen visas för spelarna med hjälp av ett manifest som beskriver det tillgängliga innehållet för en skärm.

**På klientsidan**

* Spelaren uppdaterar sitt innehåll baserat på manifestet som genereras ovan.

### Fördelar med SmartSync {#benefits-of-using-smartsync}

SmartSync-funktionen har flera fördelar för ditt AEM Screens-projekt, som följande:

* Dramatiskt minskade krav på nätverkstrafik och lagring på serversidan.
* Spelaren hämtar resurser på ett intelligent sätt endast om resursen saknas eller har ändrats.
* Lagringsoptimering på serversidan och klientsidan.

>[!NOTE]
>
>Adobe rekommenderar att du använder SmartSync för AEM Screens-projekt.

## Migrera från ContentSync till SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Om du redan har installerat AEM 6.3 Feature Pack 5 och AEM 6.4 Feature Pack 3 kan du aktivera SmartSync för resurser för att förbättra användningen av diskutrymme. Om du vill aktivera SmartSync följer du avsnittet nedan för att gå över från ContentSync till SmartSync, vilket aktiverar SmartSync.
>
>SmartSync är tillgängligt för Screens Player med servrar som stöds i AEM 6.4.3 FP3.
>
>Gå till [AEM Screens Player Downloads](https://download.macromedia.com/screens/) om du vill hämta den senaste spelaren. I följande tabell beskrivs den lägsta spelarversion som krävs för varje plattform:

| **Plattform** | **Lägsta spelarversion som stöds** |
|---|---|
| Android™ | 3.3.72 |
| CHROME OS | 1.0.136 |
| Windows | 1.0.136 |

Följ stegen nedan för att gå över från ContentSync till SmartSync:

1. Migrering från ContentSync till SmartSync kräver att ContentSync-cachen rensas innan SmartSync aktiveras.

   Navigera till ContentSync-konsolen från din instans med länken ***https://localhost:4502/libs/cq/contentsync/content/console.html*** och klicka på **Rensa cache** enligt bilden nedan:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Alla innehållscache måste rensas innan SmartSync kan användas för första gången.

1. Navigera till **Adobe Experience Manager Web Console Configuration** med AEM-instans > hammikon > **Åtgärder** > **Webbkonsol**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web Console Configuration** öppnas. Sök efter *offlinekontaktentservice*.

   Om du vill söka efter egenskapen **Screens Offline Content Service** trycker du på **Command+F** för **Mac** och **Control+F** för **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Klicka på **Spara** om du vill aktivera egenskapen **Screens Offline Content Services** och använda SmartSync för AEM Screens.
1. När du har aktiverat SmartSync navigerar du till ditt projekt och klickar på **Uppdatera offlineinnehåll** *(från åtgärdsfältet),* enligt bilden nedan.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
