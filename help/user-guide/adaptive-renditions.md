---
title: Adaptiva renderingar i AEM Screens
description: This page describes Architectures Overview and Configurations for Adaptive Renditions in AEM Screens.
index: false
source-git-commit: 951fd38d5f69cdab1bf9b23f07b4e92075e87baf
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---


# Adaptiva renderingar: Arkitektöversikt och konfigurationer {#adaptive-renditions}

## Introduktion {#introduction}

Med adaptiva renderingar kan enheterna automatiskt välja den bästa renderingen för en enhet baserat på kunddefinierade regler. Enheterna laddar automatiskt ned och spelar upp den lämpligaste återgivningen av en resurs baserat på dessa regler, vilket gör att kunderna bara kan fokusera på att utforma *main*-upplevelsen.

## Syfte {#objective}

Som AEM Screens-utvecklare kan du nu konfigurera enhetsspecifika resursrenderingar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt. Du måste konfigurera de adaptiva återgivningarna innan en innehållsförfattare kan använda den här funktionen i en AEM Screens-kanal.

## Arkitektöversikt {#architectural-overview}

Anpassade återgivningar baseras på idén att ha flera resursåtergivningar namngivna efter en viss namnkonvention. Beslutet att spela upp en viss återgivning görs genom att utvärdera mediefrågeuttryck som bara kan matchas på enheter med förväntade funktioner.

Möjligheten att ha ett associerat namngivningsmönster definierar en regel för återgivningsmappning, till exempel stående eller liggande, vilket visas i bilden nedan. När alla tillgängliga uttryck har beräknats samlar skärmspelaren in de namngivningsmönster som motsvarar matchande regler. Mönstren används för att hitta rätt återgivningar under sekvensuppspelningen genom att leta efter mönstren i återgivningsnamnen.

![bild](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Lägga till en återgivningsmappningsegenskap i skärmsprojektet {#rendition-mapping-new}

Om du vill aktivera funktionen Adaptiv återgivning bör följande mappningsregler finnas och kontextmedveten konfiguration (CA) kan lösas för kanaler och skärmar.

>[!NOTE]
>Mer information om innehållsanpassade konfigurationer finns i [här](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Konfigurera installationen genom att följa stegen nedan:

1. Navigera till **CRXDE Lite**. Kontrollera om konfigurationen **rendering-mapping** finns i `/conf/screens/sling:configs/rendition-mapping`, vilket visas i bilden nedan.

   >![bild](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Om du installerade den senaste funktionspaketet 20109 visas **rendition-mapping**-nodstrukturen i `/conf/screens/sling:configs/rendition-mapping` i CRXDE Lite. Se [Versionsinformation för funktionspaket 20109](/help/user-guide/release-notes-fp-202109.md) för mer information om det senaste funktionspaketet.
   >Kontrollera att konfigurationen **rendering-mapping** är associerad för befintliga projekt. Mer information finns i [Lägga till återgivningsmappning i ett befintligt projekt](#rendition-mapping-existing)-avsnitt.

### Lägga till en återgivningsmappningsegenskap i ett befintligt projekt {#rendition-mapping-existing}

1. Navigera till **CRXDE Lite**.

1. Definiera explicit återgivningsmappningsassociationen genom att lägga till `sling:configRef`-egenskapspunkterna vid `/conf/screens` till projektinnehållsnoden, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Konfigurera Författare och Publicera {#setup-author-publish}

Tänk på följande rekommendationer i Författare och Publicera innan du använder Adaptiv återgivning:

* Återgivningsmappningen måste replikeras manuellt.

* Resursåtergivningar replikeras inte som standard. Alla relevanta resurser måste replikeras manuellt.

## Lägga till återgivningsmappningsregler {#add-rendition-mapping-rules}

1. Om du vill lägga till en mappningsregel måste du skapa en nod av typen `nt:unstructured` under noden **rendering-mapping**.

1. Lägg till uttrycksegenskapen med värdet som innehåller frågeuttrycket.

   >[!NOTE]
   >Mer information finns i [Använda Media Query Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries).

1. Lägg till egenskapen pattern med värdet som innehåller det namngivningsmönster som ska markeras, om uttrycket utvärderas som true.

   ![bild](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## Nästa steg {#next-steps}

När du har konfigurerat och överfört återgivningarna som innehållsförfattare kan du nu använda adaptiva återgivningar och även migrera dina enheter för stora nätverk för att använda den här funktionen i dina AEM Screens-kanaler. Mer information finns i [Använda adaptiva renderingar](/help/user-guide/using-adaptive-renditions.md).
