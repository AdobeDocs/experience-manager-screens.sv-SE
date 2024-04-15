---
title: Arbetsflödeskonfiguration för direktplacering
description: På den här sidan visas arbetsflödeskonfiguration för direktplacering.
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Arbetsflödeskonfiguration för direktplacering {#direct-placement-workflow}

Följ den här sidan så att du kan lära dig mer om hur du konfigurerar ett resursarbetsflöde som gör att du kan infoga en resurs programmatiskt i en fördefinierad AEM Screens-kanal.

Detta avsnitt behandlar följande ämnen:

* Ökning
* Konfigurera arbetsflöde för direktplacering

## Ökning {#overview}

Arbetsflödeskonfiguration för direktplacering mappar en AEM Screens-projektkanal till en viss mapp i resurser och gör det möjligt att placera resurser i den mappen. Adobe rekommenderar att du aktiverar en bulkuppdatering offline för att slutföra publikationen.

Som innehållsförfattare kan du också klicka manuellt **Uppdatera offlineinnehåll**.

>[!NOTE]
>
>Mer information om hur du använder bulkuppdatering offline finns i [Innehållsuppdatering som tjänst](/help/user-guide/content-update-as-a-service.md).

## Konfigurera arbetsflöde för direktplacering {#configuring-workflow}

>[!IMPORTANT]
>
>Installera `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. När du har installerat paketet kan du visa det och få åtkomst till det från AEM > Verktyg (ikon) > **Arbetsflöde** > **Arbetsflödesmodeller**.

Följ stegen nedan för att konfigurera arbetsflödet för direktplacering:

1. Navigera till AEM Screens från AEM och skapa ett skärmsprojekt med namnet **Resursarbetsflöde**.

1. Skapa en kanal med namnet som **Arbetsflöden - resurser** under **Kanaler** mapp.

