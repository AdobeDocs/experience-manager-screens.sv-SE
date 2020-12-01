---
title: Tilldelningsrapport för innehåll
description: Den här sidan beskriver hur du hämtar och använder Content Assignment Report.
translation-type: tm+mt
source-git-commit: b93baeeb26e48b906ee1ddfc034112f8b73615af
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 1%

---


# Tilldelningsrapport för innehåll {#content-assignment-report}

Med rapportfunktionen Innehållstilldelning kan en AEM Screens-administratör eller författare exportera en *innehållsuppdragsrapport* i ett kalkylbladsformat.

## Använda rapporten för innehållstilldelning {#using-content-assignment-report}

Med rapporten Innehållstilldelning kan en AEM Screens-författare eller en administratör hämta rapporten som innehåller alla resurser, till exempel bilder, videor i alla kanaler som har skapats i ett AEM Screens-projekt. Dessutom innehåller det information om alla kanaler som är tilldelade till alla avsedda skärmar och hädanefter alla enheter som är tilldelade till deras avsedda skärmar.

Tilldelningsrapporten för innehåll tillåter inte bara en förhandsgranskning av alla kanaler, resurser, skärmar och enheter i det valda AEM Screens-projektet, utan även en högnivåstruktur i ditt projekt.

### Använda rapporten för innehållstilldelning {#downloading-content-assignment-report-fp}

#### Konfigurera projektet {#setting-up-project}

Följ stegen nedan för att hämta rapporten för innehållstilldelning från ett AEM Screens-projekt:

1. Skapa en AEM Screens med namnet **DemoScreens**.

   ![bild](/help/user-guide/assets/content-assignment-report/car-1.png)

1. Skapa två sekvenskanaler i **DemoScreens** som **ChannelOne** och **ChannelTwo**.

   ![bild](/help/user-guide/assets/content-assignment-report/car-2.png)

1. Välj **ChannelOne** och klicka på **Redigera** i åtgärdsfältet. Lägg till få resurser (bilder/videor) i den här kanalen. Lägg på samma sätt till resurser i **ChannelTwo**.

1. Navigera till mappen Locations från **DemoScreens** —> **Locations** och skapa tre olika platser med namnen **SanJose**, **Dublin** och **San Francisco**.

   ![bild](/help/user-guide/assets/content-assignment-report/car-3.png)

1. Navigera till var och en av platserna och skapa en display för varje plats, t.ex. **SanJoseMain** under **SanJose** , **DublinMain** under **Dublin** och **SanFranciscoMain** **** under¥SanFrancisco¥.

1. Tilldela en enhet till varje skärm.

   >[!NOTE]
   >Mer information om hur du tilldelar en kanal till en skärm finns i [Kanaltilldelning](/help/user-guide/channel-assignment.md).

#### Hämta rapporten för innehållstilldelning {#downloading-content-assignment-report}

När du har konfigurerat ditt AEM Screens-projekt och har tilldelat displayannonser till var och en av platserna enligt stegen ovan kan du ladda ned rapporten för innehållstilldelning.

>[!NOTE]
>Det går bara att komma åt funktionen för innehållstilldelningsrapport på projektnivå.

Följ instruktionerna nedan för att hämta rapporten för innehållstilldelning:

1. Gå till ditt AEM Screens-projekt och välj projektet **DemoScreens**.

1. Klicka på **Tilldelningsrapport** för innehåll i åtgärdsfältet. Ett Excel-blad ska laddas ned till din dator.

   ![bild](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >Det hämtade kalkylbladet består av fyra kolumner, till exempel **Kanaler**, **Resurser**, **Bildskärmar** och **Enheter** , som kan användas för att ytterligare undersöka dessa fyra enheter som hör till ditt AEM Screens-projekt.





