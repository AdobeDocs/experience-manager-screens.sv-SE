---
title: Adaptiva renderingar i AEM Screens
description: This page describes Architectures Overview and Configurations for Adaptive Renditions in AEM Screens.
index: false
source-git-commit: 75f7cf722880bb0a1f35ac663308cf049cd4fd20
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 1%

---


# Adaptiva renderingar: Arkitektöversikt och konfigurationer {#adaptive-renditions}

## Introduktion {#introduction}

Med adaptiva renderingar kan enheterna automatiskt välja den bästa renderingen för en enhet baserat på kunddefinierade regler. Enheterna laddar automatiskt ned och spelar upp den lämpligaste återgivningen av en resurs baserat på dessa regler, vilket gör att kunderna bara kan fokusera på att utforma *main*-upplevelsen.

## Syfte {#objective}

Som AEM Screens-utvecklare kan du nu konfigurera enhetsspecifika resursrenderingar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt. Du måste konfigurera de adaptiva återgivningarna innan en innehållsförfattare kan använda den här funktionen i en AEM Screens-kanal.

Om du har distribuerat en mängd olika enheter kan du använda den här funktionen för att automatiskt hämta och spela upp den lämpligaste återgivningen av en resurs baserat på reglerna.

## Arkitektöversikt {#architectural-overview}

Anpassade återgivningar baseras på idén att ha flera resursåtergivningar namngivna efter en viss namnkonvention. Beslutet att spela upp en viss återgivning görs genom att utvärdera mediefrågeuttryck som bara kan matchas på enheter med förväntade funktioner. Möjligheten att ha ett associerat namngivningsmönster definierar en regel för återgivningsmappning. När alla tillgängliga uttryck har beräknats samlar skärmspelaren in de namngivningsmönster som motsvarar matchande regler. Mönstren används för att hitta rätt återgivningar under sekvensuppspelningen genom att leta efter mönstren i återgivningsnamnen.

![bild](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Konfigurera inställningar för användning av adaptiva renderingar {#setup-adaptive-renditions}

För att aktivera funktionen Adaptiva återgivningar bör mappningsreglerna finnas och CA-konfigurationen kan lösas för kanaler och skärmar:

1. Kontrollera om återgivningsmappningskonfigurationen finns i `JCR`. Alla de senaste funktionspaketen har den här nodstrukturen ifylld i förväg.

   >[!NOTE]
   >Alla de senaste funktionspaketen har den här nodstrukturen ifylld i förväg.

   ![bild](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. Kontrollera att återgivningsmappningskonfigurationen är associerad med projektet Skärmar.

   * Alla nya projekt som skapas med projektguiden för skärmar innehåller en referens som pekar på återgivningsmappningskonfigurationen.

      ![bild](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * I en äldre version av Skärmprojekt måste associationen definieras explicit genom att lägga till `sling:configRef`-egenskapspunkterna vid `/conf/screens` till projektinnehållsnoden.

      ![bild](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)

## Migreringsstrategi {#migration-strategy}

>[!IMPORTANT]
>För stora nätverk rekommenderar vi att migreringen görs gradvis för att minska riskerna eftersom funktionen kommer att medföra förändringar i manifest- och fillagringsformatet.

I följande diagram visas migreringsstrategin för stora nätverk:

![bild](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Om du vill aktivera funktionen lägger du till minst en mappningsregel och kontrollerar att konfigurationen för återgivningsmappning kan matchas i kontexten för skärmar och kanaler. Följ stegen nedan för att migrera:

1. Lägg till [Återgivningsmappningsregler](#adding-rendition-mapping-rules).
1. Skapa en mapp för nya kanaler och lägg till en referenspunkt vid återgivningsmappningskonfigurationen.
1. Skapa nya kanaler som ersätter de gamla och överför renderingar.
1. Tilldela om skärmar till de nya kanalerna.
1. Lägg till en referens till de migrerade skärmarna eller platserna som pekar på återgivningsmappningskonfigurationen.
1. Upprepa steg 3, 4 och 5 för alla återstående kanaler och skärmar.
1. När migreringen är klar tar du bort alla konfigurationsreferenser från kanaler, skärmar och platser och lägger till en enda i projektinnehållsnoden.

## Konfigurera Författare och Publicera {#setup-author-publish}

Tänk på följande rekommendationer i Författare och Publicera innan du använder Adaptiv återgivning:

* Återgivningsmappningen måste replikeras manuellt.

* Resursåtergivningar replikeras inte som standard. Alla relevanta resurser måste replikeras manuellt.

## Lägga till återgivningsmappningsregler {#add-rendition-mapping-rules}

1. Om du vill lägga till en mappningsregel måste du skapa en nod av typen `nt:unstructured` under noden för återgivningsmappning.

1. Lägg till uttrycksegenskapen med värdet som innehåller frågeuttrycket.

   >[!NOTE]
   >Mer information finns i [Använda Media Query Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries).

1. Lägg till egenskapen pattern med värdet som innehåller det namngivningsmönster som ska markeras, om uttrycket utvärderas som true.

   ![bild](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## Överför återgivningar {#upload-renditions}

1. Skapa en version av resursen som bättre passar signeringsvisningen, till exempel `portrait orientation`.

1. Välj namngivningsmönstret för återgivningen, till exempel`portrait`.

1. Byt namn på resursfilen så att den innehåller mönstret, till exempel `my_asset_portrait.png`.

1. Klicka på **Lägg till återgivning** för att överföra återgivningen, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-rendition.png)

## Nästa steg {#next-steps}

När du har överfört renderingarna kan du nu använda adaptiva renderingar i dina AEM Screens-kanaler. Mer information finns i Använda adaptiva återgivningar.
