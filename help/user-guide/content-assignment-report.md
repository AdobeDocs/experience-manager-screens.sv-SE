---
title: Tilldelningsrapport för innehåll
description: Den här sidan beskriver hur du hämtar och använder Content Assignment Report.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: 9e750b874253a5d1786e5ef78fc41d96e72b702d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Tilldelningsrapport för innehåll {#content-assignment-report}

Med rapportfunktionen Innehållstilldelning kan en AEM Screens-administratör eller författare exportera en *Tilldelningsrapport för innehåll* i kalkylbladsformat.

## Använda rapporten för innehållstilldelning {#using-content-assignment-report}

Med rapporten Innehållstilldelning kan en AEM Screens-författare eller en administratör hämta rapporten som innehåller alla resurser, till exempel bilder, videor i alla kanaler som har skapats i ett AEM Screens-projekt. Dessutom innehåller det information om alla kanaler som är tilldelade till alla avsedda skärmar och hädanefter alla enheter som är tilldelade till deras avsedda skärmar.

Tilldelningsrapporten för innehåll tillåter inte bara en förhandsgranskning av alla kanaler, resurser, skärmar och enheter i det valda AEM Screens-projektet, utan även en högnivåstruktur i ditt projekt.


### Krav {#pre-reqs}

Innan du hämtar rapporten för innehållstilldelning bör du kontrollera att du har konfigurerat ett AEM Screens-projekt med kanaler, platser och enheter.
Mer information finns på följande resurser:

1. [Skapa och hantera projekt](/help/user-guide/creating-a-screens-project.md)
1. [Skapa och hantera kanaler](/help/user-guide/managing-channels.md)
1. [Skapa och hantera platser](/help/user-guide/managing-locations.md)
1. [Skapa och hantera skärmar](/help/user-guide/managing-displays.md)
1. [Skapa enheter](/help/user-guide/managing-devices.md)
1. [Tilldela kanaler](/help/user-guide/channel-assignment-latest-fp.md)


## Hämta rapporten för innehållstilldelning {#downloading-content-assignment-report-fp}

När du har konfigurerat ditt AEM Screens-projekt och har tilldelat displayannonser till var och en av platserna enligt stegen ovan kan du ladda ned rapporten för innehållstilldelning.

>[!NOTE]
>Det går bara att komma åt funktionen för innehållstilldelningsrapport på projektnivå.

Följ instruktionerna nedan för att hämta rapporten för innehållstilldelning:

1. Navigera till ditt AEM Screens-projekt och markera projektet **DemoScreens**.

1. Klicka på **Tilldelningsrapport för innehåll** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/content-assignment-report/can-download.png)

1. Det hämtade kalkylbladet består av två flikar, till exempel **Platser** och **Innehåll**. På fliken Plats visas fyra kolumner, till exempel **Platser**, **Visar**, **Kanaler** och **Enheter** som kan användas för att ytterligare undersöka dessa fyra enheter som hör till ditt AEM Screens-projekt.

   ![bild](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >De data som visas i kalkylbladet sorteras i bokstavsordning i ett format som är enkelt att läsa.

1. Du kan klicka på någon av kanalerna i **Kanaler** kolumnen som ska öppnas **Innehåll** som direkt navigerar dig till den kanalen och även ger dig information om resurser (bilder och videor) som är kopplade till den kanalen, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
