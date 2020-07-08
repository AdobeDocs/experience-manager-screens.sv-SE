---
title: 'Arbetsflödeskonfiguration för direktplacering '
seo-title: Arbetsflödeskonfiguration för direktplacering
description: På den här sidan visas arbetsflödeskonfiguration för direktplacering.
seo-description: På den här sidan visas arbetsflödeskonfiguration för direktplacering.
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Arbetsflödeskonfiguration för direktplacering {#direct-placement-workflow}

Följ den här sidan om du vill veta mer om hur du konfigurerar ett arbetsflöde för resurser som gör att du kan infoga en resurs i en fördefinierad AEM Screens-kanal programmatiskt.

Detta avsnitt behandlar följande ämnen:

* Översikt
* Konfigurera arbetsflöde för direktplacering

## Översikt {#overview}

Arbetsflödeskonfiguration för direktplacering mappar en AEM Screens-projektkanal till en viss mapp i resurser och gör det möjligt att placera resurser i den mappen. Vi rekommenderar att du aktiverar en satsvis offlineuppdatering för att slutföra publiceringen.

Som innehållsförfattare kan du också klicka på **Uppdatera offlineinnehåll** manuellt.

>[!NOTE]
>
>Mer information om hur du använder bulkuppdatering offline finns i [Innehållsuppdatering som en tjänst](/help/user-guide/content-update-as-a-service.md).

## Konfigurera arbetsflöde för direktplacering {#configuring-workflow}

>[!IMPORTANT]
>
>Innan du startar konfigurationen måste du installera [demopaketet](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). När du har installerat paketet bör du kunna visa och komma åt det från din AEM-instans —> Verktyg (ikon) —> **Arbetsflöde** —> **Arbetsflödesmodeller**.

Följ stegen nedan för att konfigurera arbetsflödet för direktplacering:

1. Navigera till AEM Screens från din AEM-instans och skapa ett skärmsprojekt med namnet **Asset Workflow**.

1. Skapa en kanal som heter **Arbetsflöde - Resurser** i mappen **Kanaler** .

1. 
