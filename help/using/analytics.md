---
title: Analyser med AEM Screens
seo-title: Analytics with AEM Screens
description: Sidan beskriver Analytics med AEM Screens
seo-description: The page describes the analytics with AEM Screens
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Analyser med AEM Screens {#analytics-screens}

>[!NOTE]
>
>Typiska intressenter för denna verksamhet är en marknadsförings-/affärsstrateg.

AEM Screens ger möjlighet att lokalt hämta alla spårbara händelser som körs på alla spelarenheter. Dessa data lagras lokalt tills de kan överföras till molnet för bearbetning. Förutom alla händelsedata läggs även ett deviceID och tidsstämpel till. Detta gör att data från en spelare kan särskiljas från en annan spelare och data som körs vid olika tidpunkter på dagen kan utvärderas separat om det behövs.

Det finns två grundläggande skäl till att vi kanske vill hämta in dessa data.

Den första innefattar **feedback-slingor och maskininlärning** medan den andra involverar **skapa diagram, kontrollpaneler och rapporter** som är avsedda att användas som livsmedel.

I det här fallet är vi inte intresserade av visuella rapporter eller kontrollpaneler, utan vill i stället definiera regler som AEM kan tillämpa för innehållsändringar. Genom att använda och bearbeta alla data för skärmspelarhändelser från en viss tidsperiod kan vi definiera en regel som utvärderar effekten av image1 jämfört med image2. Genom att kombinera säljdata med uppspelningsdata kan AEM fastställa att image1 har en mycket större inverkan på försäljningen och automatiskt instruerar alla spelare att använda image1.

Det andra användningsexemplet med analys är att bearbeta uppspelningshändelser och användningsdata som ska användas som livsmedel via rapporter och kontrollpaneler.
Vi kan använda dessa data för att skapa en värmekarta av en interaktiv upplevelse för att fastställa den önskade färdplanen genom vår applikation. Vi kan också välja att skapa en kontrollpanel som ger en grafisk tolkning av hur många gånger konsumenterna interagerar med vår applikation.
