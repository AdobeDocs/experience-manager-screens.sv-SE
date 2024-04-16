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
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Övergång från ContentSync till SmartSync {#transitioning-from-contentsync-to-smartsync}

I det här avsnittet ges en översikt över SmartSync-funktionen och hur den minimerar belastningen på servern/lagringen och nätverkstrafiken för att minska kostnaderna.

## Ökning {#overview}

SmartSync är den senaste mekanismen som används av AEM Screens. Den ersätter den nuvarande metoden som används för att cachelagra offlinekanaler och leverera dem till spelaren.

Det körs både på serversidan och på klientsidan.

**På serversidan**:

* Kanalernas innehåll, inklusive resurser, cachas i *`/var/contentsync`*.
* Cachen visas för spelarna via ett manifest som beskriver det tillgängliga innehållet för en skärm.

**På klientsidan**:

* Spelaren uppdaterar innehållet baserat på manifestet som genereras ovan.

### Fördelar med SmartSync {#benefits-of-using-smartsync}

SmartSync-funktionen har flera fördelar för ditt AEM Screens-projekt, som följande:

* Dramatiskt minskade krav på nätverkstrafik och lagring på serversidan.
* Player hämtar resurser på ett intelligent sätt endast om resursen saknas eller har ändrats.
* Lagringsoptimering på serversidan och klientsidan.

>[!NOTE]
>
>Adobe rekommenderar starkt att du använder SmartSync för AEM Screens-projekt.

## Migrera från ContentSync till SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Om du redan har installerat AEM 6.3 Feature Pack 5 och AEM 6.4 Feature Pack 3 kan du aktivera SmartSync för resurser för att förbättra användningen av diskutrymme. Om du vill aktivera SmartSync följer du avsnittet nedan för att gå över från ContentSync till SmartSync, vilket aktiverar SmartSync.
>
>SmartSync är tillgängligt för skärmspelaren med servrar som stöds AEM 6.4.3 FP3.
>
>Se [AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/) för att ladda ned den senaste spelaren. I följande tabell beskrivs den lägsta spelarversion som krävs för varje plattform:

| **Plattform** | **Lägsta spelarversion som stöds** |
|---|---|
| Android™ | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

Följ stegen nedan för att gå över från ContentSync till SmartSync:

1. Migrering från ContentSync till SmartSync kräver att ContentSync-cachen rensas innan SmartSync aktiveras.

   Navigera till ContentSync-konsolen från din instans via länken ***https://localhost:4502/libs/cq/contentsync/content/console.html*** och klicka **Rensa cache**, vilket visas i figuren nedan:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Alla innehållscache måste rensas innan SmartSync kan användas för första gången.

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console** via AEM > hammarikon > **Operationer** > **Webbkonsol**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Konfiguration av Adobe Experience Manager Web Console** öppnas. Sök efter *offlinecontentservice*.

   Om du vill söka i **Skärmar som är offline Innehållstjänst** egenskap, tryck **Kommando+F** for **Mac** och **Ctrl+F** for **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Klicka **Spara** för att aktivera **Skärmar offline Innehållstjänster** och använder därför SmartSync för AEM Screens.
1. När du har aktiverat SmartSync går du till ditt projekt och klickar på **Uppdatera offlineinnehåll** *(från åtgärdsfältet),* som visas i figuren nedan.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
