---
title: Adaptiva renderingar i AEM Screens
description: This page describes Architectures Overview and Configurations for Adaptive Renditions in AEM Screens.
index: false
source-git-commit: bbae7c8ba0f24b228221df8bc4c26cc5c4817ce0
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 1%

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

Följ stegen nedan för att lägga till en nod under Återgivningsmappning:

1. Navigera till den här sökvägen `/conf/screens/sling:configs/rendition-mapping` från **CRXDE Lite**.

1. Skapa en nod under **renderingsmappning**. Högerklicka på **renderingsmappning** och klicka på **Create** —> **Skapa nod** enligt bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Ange **namnet** för mappningsregeln t.ex. **rule1** och noden **Skriv** som **nt:undefined** i dialogrutan **Skapa nod**. Klicka på **OK**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Du måste lägga till uttrycksegenskapen med värdet som innehåller frågeuttrycket.

   >[!NOTE]
   >Mer information finns i [Använda Media Query Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries).

   Klicka på **rule1** som du skapade och ange **expression** i **Name** och **(orientation:landscape)** i **Value**, som visas nedan. Klicka på **Lägg till**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node3.png)



1. Lägg till egenskapen pattern med värdet som innehåller det namngivningsmönster som ska markeras, om uttrycket utvärderas som true.

   Om du vill lägga till mönsteregenskapen klickar du på **rule1** som du har skapat och anger **pattern** i **Name** och **landscape** i **Value** enligt nedan. Klicka på **Lägg till**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Klicka på **Spara alla** så ser du egenskaperna under noden som du skapade under **renderingsmappning**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## Nästa steg {#next-steps}

När du har konfigurerat och överfört återgivningarna som innehållsförfattare kan du nu använda adaptiva återgivningar och även migrera dina enheter för stora nätverk för att använda den här funktionen i dina AEM Screens-kanaler. Mer information finns i [Använda adaptiva renderingar](/help/user-guide/using-adaptive-renditions.md).
