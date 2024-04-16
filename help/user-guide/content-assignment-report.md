---
title: Tilldelningsrapport för innehåll
description: Lär dig hur du hämtar och använder Content Assignment Report när det gäller AEM Screens.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Tilldelningsrapport för innehåll {#content-assignment-report}

Med rapportfunktionen Innehållstilldelning kan en AEM Screens-administratör eller författare exportera en *Tilldelningsrapport för innehåll* i ett kalkylbladsformat.

## Använda rapporten för innehållstilldelning {#using-content-assignment-report}

Med rapporten Innehållstilldelning kan en AEM Screens-författare eller en administratör hämta rapporten som innehåller alla resurser, till exempel bilder, videor i alla kanaler som har skapats i ett AEM Screens-projekt. Dessutom innehåller det information om alla kanaler som är tilldelade till alla avsedda skärmar och hädanefter alla enheter som är tilldelade till deras avsedda skärmar.

I rapporten Innehållstilldelning kan du inte bara förhandsgranska alla kanaler, resurser, skärmar och enheter i det valda AEM Screens-projektet, utan även få en högnivåstruktur i ditt projekt.


### Krav {#pre-reqs}

Innan du laddar ned rapporten för innehållstilldelning bör du kontrollera att du har konfigurerat ett AEM Screens-projekt med kanaler, platser och enheter.
Mer information finns i följande resurser:

1. [Skapa och hantera projekt](/help/user-guide/creating-a-screens-project.md)
1. [Skapa och hantera kanaler](/help/user-guide/managing-channels.md)
1. [Skapa och hantera platser](/help/user-guide/managing-locations.md)
1. [Skapa och hantera skärmar](/help/user-guide/managing-displays.md)
1. [Skapa enheter](/help/user-guide/managing-devices.md)
1. [Tilldela kanaler](/help/user-guide/channel-assignment-latest-fp.md)


## Hämtar rapporten för innehållstilldelning {#downloading-content-assignment-report-fp}

När du har konfigurerat ditt AEM Screens-projekt och har tilldelat visningar för var och en av platserna enligt stegen ovan, hämtar du rapporten för innehållstilldelning.

>[!NOTE]
>Det går bara att komma åt funktionen för innehållstilldelningsrapport på projektnivå.

Följ instruktionerna nedan för att hämta rapporten för innehållstilldelning:

1. Navigera till ditt AEM Screens-projekt och klicka på projektet **DemoScreens**.

1. Klicka **Tilldelningsrapport för innehåll** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/content-assignment-report/can-download.png)

1. Det hämtade kalkylbladet består av två flikar, till exempel **Platser** och **Innehåll**. På fliken Plats visas fyra kolumner, till exempel **Platser**, **Visar**, **Kanaler** och **Enheter** som kan användas för att ytterligare undersöka dessa fyra enheter som hör till ditt AEM Screens-projekt.

   ![bild](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >De data som visas i kalkylbladet sorteras i bokstavsordning i ett lättläst format.

1. Markera någon av kanalerna på panelen **Kanaler** kolumnen öppnar **Innehåll** -fliken. I sin tur navigerar den direkt till den kanalen och ger dig information om resurser (bilder och videor) som är kopplade till den specifika kanalen.

   ![bild](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
