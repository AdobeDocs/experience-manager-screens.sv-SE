---
title: Skapa komponenter
description: Lär dig mer om hur AEM komponenter används för att lagra, formatera och återge innehåll som är tillgängligt på dina webbsidor.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Skapa komponenter {#creating-components}

AEM används för att lagra, formatera och återge innehåll som är tillgängligt på dina webbsidor.

>[!NOTE]
>
>Mer information om hur du skapar AEM finns i Utveckla AEM.

## Redigeringskanaler {#authoring-channels}

Kanalen är det centrala objektet för innehåll som levereras till en uppsättning skärmar. Därför öppnar en innehållsförfattare vanligtvis en kanal i redigeraren för att lägga till eller ändra innehåll. Eftersom kanalen är en ***`cq:Page`*** följer den samma traditionella UX-mönster för att lägga till och ändra komponenter i kanalen.

Men eftersom komponenter i en kanal vanligtvis återges i helskärmsläge, blir redigeringsmiljön lidande när du försöker redigera enskilda komponenter eller skapa nya order. Kanalen använder därför väljare för att återge olika vyer av komponenterna. I redigeringsmiljön används redigeringsväljaren för att aktivera den anpassade kanalåtergivningen.

Exempel: `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

Användaren behöver inte ta hand om att lägga till väljaren till URL-adressen när han/hon redigerar. En logik på klientsidan lyssnar på lagerväxlingshändelsen och lägger till väljaren om kanalen har den dedikerade resurstypen *skärmar/kärna/komponenter/kanal*.

## Återgivningskomponenter {#rendering-components}

För att möjliggöra rätt redigering måste komponenterna tillhandahålla följande två återgivningar:

| **Komponent** | **Återgivningar** |
|---|---|
| *my-component/my-component.html* | produktionsrendering |
| *my-component/edit.html* | redigera återgivning i en mindre vy |

De inbyggda komponenterna använder följande klientbibliotekskategorier:

| **Komponent** | **Klientbibliotek** |
|---|---|
| *cq.screens.components.edit* | CSS och JS som måste läsas in vid redigering |
| *cq.screens.components.production* | CSS och JS som måste läsas in när kanalen körs |
| *cq.screens.components* | delad CSS och JS |

>[!NOTE]
>
>Använd exempelkomponentmallen ***[AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)*** för att utveckla anpassade komponenter.
