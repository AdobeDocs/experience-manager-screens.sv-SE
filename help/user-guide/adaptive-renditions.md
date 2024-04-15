---
title: Adaptiva renderingar Arkitektur - översikt och konfigurationer
description: Läs mer om översikten och konfigurationerna för arkitekturen i CRXDE Lite för adaptiva renderingar i AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 1%

---

# Adaptiva renderingar: Arkitektur - översikt och konfigurationer {#adaptive-renditions}

## Introduktion {#introduction}

Med adaptiva renderingar kan enheterna automatiskt välja den bästa renderingen för en enhet baserat på kunddefinierade regler. Enheterna laddar automatiskt ned och spelar upp den lämpligaste återgivningen av en mediefil baserat på dessa regler, så att kunderna bara kan fokusera på att utforma *main* upplevelse.

## Syfte {#objective}

Som AEM Screens-utvecklare kan du nu konfigurera enhetsspecifika resursrenderingar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt. Konfigurera de adaptiva återgivningarna innan en innehållsförfattare kan använda den här funktionen i en AEM Screens-kanal.

## Arkitektöversikt {#architectural-overview}

Anpassade återgivningar baseras på idén att ha flera återgivningar av en resurs som namnges efter en viss namnkonvention. Beslutet att spela upp en viss återgivning görs genom att utvärdera mediefrågeuttryck som bara kan matchas på enheter med förväntade funktioner.

Möjligheten att ha ett associerat namngivningsmönster definierar en regel för återgivningsmappning, till exempel stående eller liggande, vilket visas i bilden nedan. När alla tillgängliga uttryck har beräknats samlar skärmspelaren in de namngivningsmönster som motsvarar matchande regler. Mönstren används för att hitta rätt återgivningar under sekvensuppspelningen genom att leta efter mönstren i återgivningsnamnen.

![bild](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Lägga till en återgivningsmappningsegenskap i skärmsprojektet {#rendition-mapping-new}

Om du vill aktivera funktionen Adaptiv återgivning bör följande mappningsregler finnas och kontextmedveten konfiguration (CA) kan lösas för kanaler och skärmar.

>[!NOTE]
>Mer information om innehållsmedvetna konfigurationer finns i [här](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Konfigurera installationen genom att följa stegen nedan:

1. Navigera till **CRXDE Lite**. Markera om **återgivningsmappning** konfigurationen finns i `/conf/screens/sling:configs/rendition-mapping`, vilket visas i figuren nedan.

   >![bild](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Om du har installerat den senaste funktionspaketet 2012 finns en **återgivningsmappning** nodstruktur förifylld i `/conf/screens/sling:configs/rendition-mapping` i CRXDE Lite. Se [Versionsinformation för funktionspaket 20109](/help/user-guide/release-notes-fp-202109.md) om du vill ha information om det senaste funktionspaketet.
   >För befintliga projekt måste du se till att projektet Skärmar har **återgivningsmappning** associerad konfiguration. Se [Lägga till återgivningsmappning i ett befintligt projekt](#rendition-mapping-existing) för mer information.

### Lägga till en återgivningsmappningsegenskap i ett befintligt projekt {#rendition-mapping-existing}

1. Navigera till **CRXDE Lite**.

1. Definiera explicit återgivningsmappningsassociationen genom att lägga till `sling:configRef` egenskap som pekar på `/conf/screens` till projektinnehållsnoden enligt bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Lägga till återgivningsmappningsregler {#add-rendition-mapping-rules}

Följ stegen nedan för att lägga till en nod under Återgivningsmappning:

1. Navigera till den här sökvägen `/conf/screens/sling:configs/rendition-mapping` från **CRXDE Lite**.
1. Skapa en nod under **återgivningsmappning**. Högerklicka **återgivningsmappning** och markera **Skapa** > **Skapa nod**, vilket visas i figuren nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Ange **Namn** för din mappningsregel som **rule1** och noden **Typ** as **`nt:unstructured`** in **Skapa nod** -dialogrutan. Välj **OK**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Lägg till uttrycksegenskapen med värdet som innehåller frågeuttrycket.

   >[!NOTE]
   >Se [Använda Media Query Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries) om du vill veta mer.

   Välj **rule1** som du har skapat och anger **uttryck** in **Namn** och **(orientering:liggande)** in **Värde**, vilket visas nedan. Välj **Lägg till**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Lägg till egenskapen pattern med värdet som innehåller namngivningsmönstret.

   >[!NOTE]
   >Värdet som definieras i egenskapen pattern matchas mot den nya resursåtergivningen och väljs om uttrycket utvärderas till true.

   Om du vill lägga till mönsteregenskapen väljer du **rule1** som du har skapat och anger **mönster** in **Namn** och **liggande** in **Värde**, vilket visas nedan. Välj **Lägg till**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Välj **Spara alla** och observera egenskaperna under noden som du skapade under **återgivningsmappning**.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## Nästa steg {#next-steps}

När du har lagt till egenskaper och regler för återgivningsmappning som innehållsförfattare kan du konfigurera dina resurser. Det gör du genom att använda adaptiva renderingar och även migrera dina enheter för stora nätverk för att använda den här funktionen i dina AEM Screens-kanaler. Se [Använda adaptiva renderingar i AEM Screens](/help/user-guide/using-adaptive-renditions.md) för mer information.
