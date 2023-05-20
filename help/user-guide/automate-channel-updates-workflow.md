---
title: Använd arbetsflödet för att automatisera resursuppdateringar för en AEM Screens-kanal
seo-title: Use workflow to automate asset updates for an AEM Screens channel
description: Lär dig hur du skapar ett arbetsflöde som automatiskt bearbetar resurser som överförts till Adobe Experience Manager och dynamiskt tilldelar dem till en skärmkanal. I det här exemplet aktiveras ett arbetsflöde som använder en dynamisk vattenstämpel och tilldelar bilden till en skärmkanal när en bild läggs till i en viss mapp. Lektioner från det här exemplet kan användas i en mängd olika automatiseringsscenarier.
seo-description: Learn how to create a workflow to automatically process assets uploaded to Adobe Experience Manager and dynamically assign them to a Screens channel. In this example when an image is added to a specific folder, a workflow is triggered that applies a dynamic watermark and assigns the image to a Screens channel. Lessons learned from this example can be applied to a wide variety of automation scenarios.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# Använd arbetsflödet för att automatisera resursuppdateringar för en AEM Screens-kanal {#automate-channel-updates-workflow}

Lär dig hur du skapar ett arbetsflöde som automatiskt bearbetar resurser som överförts till Adobe Experience Manager och dynamiskt tilldelar dem till en skärmkanal. I det här exemplet aktiveras ett arbetsflöde som tillämpar en dynamisk textövertäckning (vattenstämpelprocess) och tilldelar bilden till en skärmkanal när en bild läggs till i en viss mapp. Lektioner från det här exemplet kan användas i en mängd olika automatiseringsscenarier.

## Förutsättningar {#prerequisites}

För att slutföra den här självstudiekursen behöver du följande:

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html)
1. [AEM Service Pack 8 eller senare](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html)
1. [AEM 6.5-skärmar FP7 eller senare](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## Snabbinställningar {#quick-setup}

I videon nedan visas hur du installerar ett exempelkodpaket som innehåller ett nytt arbetsflöde för Adobe Experience Manager. Med den här funktionen kan användare uppdatera egenskaperna för en mapp i AEM Assets så att de pekar på en skärmkanal. När en bild läggs till i den mappen läggs den till i den angivna skärmkanalen.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Hämta det kompilerade kodpaketet: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Installera ovanstående paket med AEM Package Manager.

## Arbetsflödesmodell {#workflow-model}

Ett anpassat mappmetadataschema skapades för att fånga målkanalen för skärmar som bilder ska läggas till. Två arbetsflödesmodeller används för att automatisera materialbearbetningen. The **DAM-uppdateringsresurs** arbetsflödet ändras för att anropa ett anpassat arbetsflöde, **Bearbetning av demoresurser** som kontrollerar resursens innehållsmapp för att avgöra målkanalen för skärmar. The **Bearbetning av demoresurser** arbetsflödet ansvarar också för att använda vattenstämpeln på bilden.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Anpassade steg i arbetsflödet {#workflow-process-step}

Inspect två anpassade arbetsflödessteg som används som en del av **Bearbetning av demoresurser** arbetsflöde.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` är en anpassad arbetsflödesprocess som utför en kontroll av arbetsflödets nyttolast för att avgöra om nyttolasten är en resurs och om mappen som innehåller är konfigurerad att peka på en skärmkanal. Om kraven är uppfyllda består processteget av två egenskaper, `screen-channel` och `asset-path`, till arbetsflödets metadata.

`AddAssetToChannel.java` är ett anpassat arbetsflödessteg som kontrollerar arbetsflödets metadata och uppdaterar skärmkanalen så att den refererar till bilden.

1. Hämta källkoden: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Zippa upp och visa koden med din favoritutvecklingsmiljö.
