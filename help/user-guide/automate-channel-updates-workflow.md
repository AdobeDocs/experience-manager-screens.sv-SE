---
title: Använd arbetsflödet för att automatisera resursuppdateringar för en AEM Screens-kanal
seo-title: Använd arbetsflödet för att automatisera resursuppdateringar för en AEM Screens-kanal
description: Lär dig hur du skapar ett arbetsflöde som automatiskt bearbetar resurser som överförts till Adobe Experience Manager och dynamiskt tilldelar dem till en skärmkanal. I det här exemplet aktiveras ett arbetsflöde som använder en dynamisk vattenstämpel och tilldelar bilden till en skärmkanal när en bild läggs till i en viss mapp. Lektioner från det här exemplet kan användas i en mängd olika automatiseringsscenarier.
seo-description: Lär dig hur du skapar ett arbetsflöde som automatiskt bearbetar resurser som överförts till Adobe Experience Manager och dynamiskt tilldelar dem till en skärmkanal. I det här exemplet aktiveras ett arbetsflöde som använder en dynamisk vattenstämpel och tilldelar bilden till en skärmkanal när en bild läggs till i en viss mapp. Lektioner från det här exemplet kan användas i en mängd olika automatiseringsscenarier.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Utveckla skärmar
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 1667fd10f415214a5301e9740d205eb33cc34f89
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Använd arbetsflöde för att automatisera resursuppdateringar för en AEM Screens-kanal {#automate-channel-updates-workflow}

Lär dig hur du skapar ett arbetsflöde som automatiskt bearbetar resurser som överförts till Adobe Experience Manager och dynamiskt tilldelar dem till en skärmkanal. I det här exemplet aktiveras ett arbetsflöde som använder en dynamisk vattenstämpel och tilldelar bilden till en skärmkanal när en bild läggs till i en viss mapp. Lektioner från det här exemplet kan användas i en mängd olika automatiseringsscenarier.

## Förutsättningar {#prerequisites}

För att slutföra den här självstudiekursen behöver du följande:

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html)
1. [AEM Service Pack 8 eller senare](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html)
1. [AEM 6.5-skärmar FP7 eller senare](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## Snabbinställning {#quick-setup}

I videon nedan visas hur du installerar ett exempelkodpaket som innehåller ett nytt arbetsflöde för Adobe Experience Manager. Med den här funktionen kan användare uppdatera egenskaperna för en mapp i AEM Assets så att de pekar på en skärmkanal. När en bild läggs till i den mappen läggs den till i den angivna skärmkanalen.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Hämta det kompilerade kodpaketet: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Installera ovanstående paket med AEM Package Manager.

## Arbetsflödesmodell {#workflow-model}

Ett anpassat mappmetadataschema skapades för att fånga målkanalen för skärmar som bilder ska läggas till. Två arbetsflödesmodeller används för att automatisera materialbearbetningen. Arbetsflödet **DAM Update Asset** har ändrats för att anropa ett anpassat arbetsflöde, **Bearbetning av skärmdemonstrationsresurser**, som undersöker resursens innehållande mapp för att avgöra målkanalen för skärmar. Arbetsflödet **Bearbetning av demoresurser på skärmar** ansvarar också för att vattenstämpeln används på bilden.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Anpassade steg för arbetsflödesprocessen {#workflow-process-step}

Inspect två anpassade arbetsflödessteg som används som en del av arbetsflödet **Bearbetning av skärmdemonstrationsresurser**.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` är en anpassad arbetsflödesprocess som utför en kontroll av arbetsflödets nyttolast för att avgöra om nyttolasten är en resurs och om mappen som innehåller är konfigurerad att peka på en skärmkanal. Om kraven är uppfyllda består processteget av två egenskaper, `screen-channel` och `asset-path`, till arbetsflödets metadata.

`AddAssetToChannel.java` är ett anpassat arbetsflödessteg som kontrollerar arbetsflödets metadata och uppdaterar skärmkanalen så att den refererar till bilden.

1. Hämta källkoden: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Zippa upp och visa koden med din favoritutvecklingsmiljö.
