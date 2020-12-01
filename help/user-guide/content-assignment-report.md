---
title: Tilldelningsrapport för innehåll
description: Den här sidan beskriver hur du hämtar och använder Content Assignment Report.
translation-type: tm+mt
source-git-commit: b9091708221f92b11e859f0da8a7080b31b0af77
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# Tilldelningsrapport för innehåll {#content-assignment-report}

Med rapportfunktionen Innehållstilldelning kan en AEM Screens-administratör eller författare exportera en *innehållsuppdragsrapport* som kan vara i kalkylbladsformat.

## Använda rapporten för innehållstilldelning {#using-content-assignment-report}

Med rapporten Innehållstilldelning kan en AEM Screens-författare eller en administratör hämta rapporten som innehåller alla resurser, till exempel bilder, videor i alla kanaler som har skapats i ett AEM Screens-projekt. Dessutom innehåller det information om alla kanaler som är tilldelade till alla avsedda skärmar och hädanefter alla enheter som är tilldelade till deras avsedda skärmar.

### Använda rapportfunktionen Innehållstilldelning{#downloading-content-assignment-report-fp}

#### Konfigurera projektet {#setting-up-project}

Följ stegen nedan för att hämta rapporten för innehållstilldelning från ett AEM Screens-projekt:

1. Skapa en AEM Screens med namnet **DemoScreens**.

1. Skapa två sekvenskanaler i **DemoScreens** som **ChannelOne** och **ChannelTwo**.

1. Välj **ChannelOne** och klicka på **Redigera** i åtgärdsfältet. Lägg till få resurser (bilder/videor) i den här kanalen. Lägg på samma sätt till resurser i **ChannelTwo**.

1. Navigera till mappen Locations från **DemoScreens** —> **Locations** och skapa tre olika platser med namnen **SanJose**, **Dublin** och **San Francisco**.

1. Navigera till var och en av platserna och skapa en display för varje plats, t.ex. **SanJoseMain** under **SanJose** , **DublinMain** under **Dublin** och **SanFranciscoMain** **** under¥SanFrancisco¥.

1. Tilldela en enhet till varje skärm.

#### Hämta rapporten för innehållstilldelning {#downloading-content-assignment-report}

När du har konfigurerat ditt AEM Screens-projekt och har tilldelat displayer till var och en av platserna enligt stegen ovan.

>[!NOTE]
>Det går bara att komma åt funktionen för innehållstilldelningsrapport på projektnivå.

Följ instruktionerna nedan för att hämta rapporten för innehållstilldelning:

1. Gå till ditt AEM Screens-projekt och välj projektet **DemoScreens**.

1. Klicka på Rapport om innehållstilldelning i åtgärdsfältet. Ett Excel-blad ska laddas ned till din dator.

   >[!NOTE]
   >Det hämtade Excel-arket består av fyra kolumner, till exempel **Kanaler**, **Resurser**, **Bildskärmar** och **Enheter** , som kan användas för att undersöka alla dessa fyra enheter ytterligare.




