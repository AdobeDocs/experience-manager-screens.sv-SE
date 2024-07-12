---
title: Adaptiva renderingar Arkitektur - översikt och konfigurationer
description: Läs mer om översikten och konfigurationerna för arkitekturen i CRXDE Lite för adaptiva renderingar i AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 1%

---

# Adaptiva renderingar: Arkitektur - översikt och konfigurationer {#adaptive-renditions}

## Introduktion {#introduction}

Med adaptiva renderingar kan enheter klicka på den bästa renderingen automatiskt för en enhet baserat på kunddefinierade regler. Enheterna hämtar automatiskt och spelar upp den lämpligaste återgivningen av en resurs baserat på dessa regler, vilket gör att kunderna kan fokusera på att utforma *huvudupplevelsen* endast.

## Syfte {#objective}

Som AEM Screens-utvecklare kan du nu konfigurera enhetsspecifika resursrenderingar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt. Konfigurera de adaptiva återgivningarna innan en innehållsförfattare kan använda den här funktionen i en AEM Screens-kanal.

## Arkitektöversikt {#architectural-overview}

Anpassade återgivningar baseras på idén att ha flera återgivningar av en resurs som namnges efter en viss namnkonvention. Beslutet att spela upp en viss återgivning görs genom att utvärdera mediefrågeuttryck som bara kan matchas på enheter med förväntade funktioner.

Möjligheten att ha ett associerat namngivningsmönster definierar en regel för återgivningsmappning, till exempel stående eller liggande, vilket visas i bilden nedan. När alla tillgängliga uttryck har beräknats samlar Screens-spelaren in de namngivningsmönster som motsvarar matchningsreglerna. Mönstren används för att hitta rätt återgivningar under sekvensuppspelningen genom att leta efter mönstren i återgivningsnamnen.

![bild](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Lägga till en återgivningsmappningsegenskap i Screens-projektet {#rendition-mapping-new}

Om du vill aktivera funktionen Adaptiv återgivning bör följande mappningsregler finnas och kontextmedveten konfiguration (CA) kan lösas för kanaler och skärmar.

>[!NOTE]
>Mer information om innehållsanpassade konfigurationer finns [här](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Konfigurera installationen genom att följa stegen nedan:

1. Gå till **CRXDE Lite**. Kontrollera om konfigurationen **rendition-mapping** finns i `/conf/screens/sling:configs/rendition-mapping`, vilket visas i bilden nedan.

   >![bild](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Om du har installerat den senaste funktionspaketet 20109 visas nodstrukturen **rendition-mapping** som är ifylld i `/conf/screens/sling:configs/rendition-mapping` i CRXDE Lite. Mer information om det senaste funktionspaketet finns i [Versionsinformation för 20109](/help/user-guide/release-notes-fp-202109.md).
   >Kontrollera att konfigurationen **rendering-mapping** är kopplad till Screens-projektet för befintliga projekt. Mer information finns i avsnittet [Lägga till återgivningsmappning i ett befintligt projekt](#rendition-mapping-existing).

### Lägga till en återgivningsmappningsegenskap i ett befintligt projekt {#rendition-mapping-existing}

1. Gå till **CRXDE Lite**.

1. Definiera explicit återgivningsmappningsassociationen genom att lägga till egenskapen `sling:configRef` som pekar på `/conf/screens` i projektinnehållsnoden, vilket visas i figuren nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Lägga till återgivningsmappningsregler {#add-rendition-mapping-rules}

Följ stegen nedan för att lägga till en nod under Återgivningsmappning:

1. Navigera till den här sökvägen `/conf/screens/sling:configs/rendition-mapping` från **CRXDE Lite**.
1. Skapa en nod under **renderingsmappning**. Högerklicka på **renderingsmappning** och klicka på **Skapa** > **Skapa nod** enligt bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Ange **Namn** för mappningsregeln som **regel1** och noden **Typ** som **`nt:unstructured`** i dialogrutan **Skapa nod**. Klicka på **OK**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Lägg till uttrycksegenskapen med värdet som innehåller frågeuttrycket.

   >[!NOTE]
   >Mer information finns i [Använda syntax för mediefrågor](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries).

   Klicka på **rule1** som du har skapat och ange **expression** i **Name** och **(orientation:landscape)** i **Value** enligt nedan. Klicka på **Lägg till**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Lägg till egenskapen pattern med värdet som innehåller namngivningsmönstret.

   >[!NOTE]
   >Värdet som definieras i egenskapen pattern matchas mot den nya resursåtergivningen och väljs om uttrycket utvärderas till true.

   Om du vill lägga till mönsteregenskapen klickar du på **rule1** som du har skapat och anger **pattern** i **Name** och **landscape** i **Value** enligt nedan. Klicka på **Lägg till**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Klicka på **Spara alla** och observera egenskaperna under noden som du skapade under **återgivningsmappning**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## Nästa steg {#next-steps}

När du har lagt till egenskaper och regler för återgivningsmappning som innehållsförfattare kan du konfigurera dina resurser. Du kan använda adaptiva renderingar och även migrera dina enheter för stora nätverk för att använda den här funktionen i dina AEM Screens-kanaler. Mer information finns i [Använda adaptiva återgivningar i AEM Screens](/help/user-guide/using-adaptive-renditions.md).
