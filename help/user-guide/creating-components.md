---
title: Skapa komponenter
seo-title: Skapa komponenter
description: AEM används för att lagra, formatera och återge innehåll som är tillgängligt på dina webbsidor. Följ den här sidan om du vill veta mer om redigeringskanaler och återgivningskomponenter.
seo-description: AEM används för att lagra, formatera och återge innehåll som är tillgängligt på dina webbsidor. Följ den här sidan om du vill veta mer om redigeringskanaler och återgivningskomponenter.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Utveckla skärmar
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Skapar komponenter {#creating-components}

AEM används för att lagra, formatera och återge innehåll som är tillgängligt på dina webbsidor.

>[!NOTE]
>
>Mer information om hur du skapar AEM finns i Utveckla AEM.

## Redigeringskanaler {#authoring-channels}

Kanalen är det centrala objektet för innehåll som levereras till en uppsättning skärmar. Därför öppnar en innehållsförfattare vanligtvis en kanal i redigeraren för att lägga till eller ändra innehåll. Eftersom kanalen är en ***cq:Page*** följer den samma traditionella UX-mönster för att lägga till och ändra komponenter i kanalen.

Men eftersom komponenter i en kanal vanligtvis återges i helskärmsläge blir redigeringsupplevelsen lidande när du försöker redigera enskilda komponenter eller skapa nya order. Kanalen använder därför väljare för att återge olika vyer av komponenterna. Redigeringsmiljön använder redigeringsväljaren för att aktivera den anpassade kanalåtergivningen.

Till exempel, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

Användaren behöver inte ta hand om att lägga till väljaren till URL-adressen när han/hon redigerar. En logik på klientsidan lyssnar på lagerväxlingshändelsen och lägger till väljaren om en kanal har den dedikerade resurstypen *skärmar/core/components/channel.*

## Återger komponenter {#rendering-components}

För att möjliggöra en korrekt redigering måste komponenterna tillhandahålla följande två återgivningar:

| **Komponent** | **Återgivningar** |
|---|---|
| *my-component/my-component.html* | produktionsrendering |
| *my-component/edit.html* | redigera återgivning i en mindre vy |

De inbyggda komponenterna utnyttjar följande klientbibliotekskategorier:

| **Komponent** | **Klientbibliotek** |
|---|---|
| *cq.screens.components.edit* | CSS och JS som måste läsas in vid redigering |
| *cq.screens.components.production* | CSS och JS som måste läsas in när kanalen körs |
| *cq.screens.components* | delad CSS och JS |

>[!NOTE]
>
>Om du vill utveckla anpassade komponenter använder du exempelkomponentmallen ***[AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.

