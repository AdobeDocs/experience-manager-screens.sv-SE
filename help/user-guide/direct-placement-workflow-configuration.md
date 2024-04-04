---
title: Arbetsflödeskonfiguration för direktplacering
seo-title: Direct Placement Workflow Configuration
description: På den här sidan visas arbetsflödeskonfiguration för direktplacering.
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Arbetsflödeskonfiguration för direktplacering {#direct-placement-workflow}

Följ den här sidan om du vill veta mer om hur du konfigurerar ett resursarbetsflöde som gör att du kan infoga en resurs i en fördefinierad AEM Screens-kanal via programmering.

Detta avsnitt behandlar följande ämnen:

* Ökning
* Konfigurera arbetsflöde för direktplacering

## Ökning {#overview}

Arbetsflödeskonfiguration för direktplacering mappar en AEM Screens-projektkanal till en viss mapp i resurser och gör det möjligt att placera resurser i den mappen. Vi rekommenderar att du aktiverar en satsvis offlineuppdatering för att slutföra publiceringen.

Som innehållsförfattare kan du också klicka manuellt **Uppdatera offlineinnehåll**.

>[!NOTE]
>
>Mer information om hur du använder bulkuppdatering offline finns i [Innehållsuppdatering som tjänst](/help/user-guide/content-update-as-a-service.md).

## Konfigurera arbetsflöde för direktplacering {#configuring-workflow}

>[!IMPORTANT]
>
>Innan du startar konfigurationen måste du installera [Demonspaket](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). När du har installerat paketet kan du visa det och få åtkomst till det från AEM > Verktyg (ikon) > **Arbetsflöde** > **Arbetsflödesmodeller**.

Följ stegen nedan för att konfigurera arbetsflödet för direktplacering:

1. Navigera till AEM Screens från din AEM och skapa ett skärmsprojekt med namnet **Resursarbetsflöde**.

1. Skapa en kanal med namnet som **Arbetsflöden - resurser** under **Kanaler** mapp.

