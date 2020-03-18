---
title: Analyser med AEM-skärmar
seo-title: Analyser med AEM-skärmar
description: Sidan beskriver analys med AEM-skärmar
seo-description: Sidan beskriver analysen med AEM Screens
translation-type: tm+mt
source-git-commit: f01b69b860a3862e2b46f11b2d9b95dede742d9c

---


# Analyser med AEM-skärmar {#analytics-screens}

>[!NOTE]
>
>Typiska intressenter för denna verksamhet är en marknadsförings-/affärsstrateg.

AEM Screens ger möjlighet att lokalt hämta alla spårbara händelser som varje spelarenhet utför. Dessa data lagras lokalt tills de kan överföras till molnet för bearbetning. Förutom alla händelsedata läggs även ett deviceID och tidsstämpel till. Detta gör att data från en spelare kan särskiljas från en annan spelare och data som körs vid olika tidpunkter på dagen kan utvärderas separat om det behövs.

Det finns två grundläggande skäl till att vi kanske vill hämta in dessa data.

Det första handlar om **feedbackslingor och maskininlärning** medan det andra handlar om att **skapa diagram, instrumentpaneler och rapporter** som är avsedda att användas som livsmedel.

I det här fallet är vi inte intresserade av visuella rapporter eller kontrollpaneler, utan vill i stället definiera regler som AEM kan köra på för innehållsändringar. Genom att använda och bearbeta alla data för skärmspelarhändelser från en viss tidsperiod kan vi definiera en regel som utvärderar effekten av image1 jämfört med image2. Genom att kombinera säljdata med uppspelningsdata kan AEM fastställa att image1 har en mycket större effekt på försäljningen och automatiskt instruerar alla spelare att använda image1.

Det andra användningsexemplet med analys är att bearbeta uppspelningshändelser och användningsdata som ska användas som livsmedel via rapporter och kontrollpaneler.
Vi kan använda dessa data för att skapa en heatmap av en interaktiv upplevelse för att fastställa vilken färdplan vi föredrar genom vår applikation. Vi kan också välja att skapa en kontrollpanel som ger en grafisk tolkning av hur många gånger konsumenterna interagerar med vår applikation.

