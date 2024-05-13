---
title: Analyser med AEM Screens
description: Läs om Adobe Analytics med Adobe Experience Manager Screens.
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Analyser med AEM Screens {#analytics-screens}

>[!NOTE]
>
>Typiska intressenter för denna verksamhet är marknadsföring/affärsstrategier.

AEM Screens kan lokalt hämta alla spårbara händelser som körs på alla spelarenheter. Dessa data lagras lokalt tills de kan överföras till molnet för bearbetning. Förutom alla händelsedata läggs även ett deviceID och tidsstämpel till. Den här funktionen gör att data från en spelare kan särskiljas från en annan spelare. Och data som körs vid olika tidpunkter på dygnet kan vid behov utvärderas separat.

Det finns två grundläggande skäl till att du kanske vill hämta in dessa data.

Den första innefattar **feedback-slingor och maskininlärning** medan den andra involverar **skapa diagram, kontrollpaneler och rapporter** som är avsedda som livsmedel.

I det här fallet behöver du inte bekymra dig om visuella rapporter eller kontrollpaneler, utan i stället vill du definiera regler som AEM kan köra på för innehållsändringar. Genom att använda och bearbeta alla data för skärmspelarhändelser från en viss tidsperiod kan du definiera en regel som utvärderar effekten av image1 jämfört med image2. Genom att kombinera säljdata med uppspelningsdata kan AEM fastställa att bild1 har större påverkan på försäljningen och automatiskt instruerar alla spelare att använda bild1.

Det andra användningsexemplet med analys är att bearbeta uppspelningshändelser och användningsdata som ska användas som livsmedel genom rapporter och kontrollpaneler.
Du kan använda dessa data för att skapa en värmekarta av en interaktiv upplevelse för att fastställa vilken färdplan som ska användas genom programmet. Du kan också välja att skapa en kontrollpanel som ger en grafisk tolkning av hur många gånger konsumenterna interagerar med programmet.
