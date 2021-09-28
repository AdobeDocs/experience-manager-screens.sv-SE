---
title: Använda adaptiva renderingar i AEM Screens
description: På den här sidan beskrivs hur du använder adaptiva renderingar i AEM Screens.
source-git-commit: 99102513b100f1f3b086eff9dcd21e5afb4f493c
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Använda adaptiva renderingar i AEM Screens {#adaptive-renditions}

## Introduktion {#introduction}

Med adaptiva renderingar kan enheterna automatiskt välja den bästa renderingen för en enhet baserat på kunddefinierade regler. Enheterna laddar automatiskt ned och spelar upp den lämpligaste återgivningen av en resurs baserat på dessa regler, vilket gör att kunderna bara kan fokusera på att utforma *main*-upplevelsen.

## Syfte {#objective}

Som AEM Screens Content Author kan du nu konfigurera enhetsspecifika materialåtergivningar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt.
När en utvecklare lägger till egenskaperna och reglerna för renderingsmappning är du nu redo att tillämpa renderingsmappningen på resurser och sedan inkludera dem i en AEM Screens-kanal.

>[!IMPORTANT]
>Innan du börjar använda adaptiva renderingar i en AEM Screens-kanal bör du läsa mer om den här funktionens arkitektoniska översikt och konfiguration. Se [Adaptiva renderingar: Arkitektöversikt och konfigurationer](/help/user-guide/adaptive-renditions.md) för mer information.

## Använda adaptiva renderingar i kanaler {#using-adaptive-renditions}

>[!NOTE]
>När du har lagt till egenskapen [renderingsmappning i skärmsprojektet](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) och [renderingsmappningsregler](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) är du nu klar att använda renderingarna i dina resurser som innehållsförfattare.

### Använda återgivningar på resurser {#apply-renditions-assets}

Följ stegen nedan för att tillämpa renderingar på resurserna som du vill använda i kanalen för visningsskärmar:

1. Navigera till mappen **Resurser** i din AEM.

1. Skapa en version av resursen som bättre passar signeringsvisningen, till exempel `seahorse.jpg`.

1. Välj namngivningsmönstret, till exempel`landscape`, som liknar det som definierats i **pattern**-egenskapen i **CRXDE Lite**. Mer information finns i [Lägga till regler för återgivningsmappning](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules).

1. Byt namn på resursfilen så att den innehåller mönstret (definierat i steg 3), till exempel `seahorse_landscape.png`.

1. Klicka på **Lägg till återgivning** för att överföra återgivningen, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-rendition.png)


## Migreringsstrategi {#migration-strategy}

>[!IMPORTANT]
>För stora nätverk rekommenderar vi att migreringen görs gradvis för att minska riskerna eftersom funktionen kommer att medföra förändringar i manifest- och fillagringsformatet. Om du lägger till `sling:configRef` i hela projektet måste alla spelare uppdateras till Feature Pack 6.5.9. Om du har uppdaterat några av spelarna behöver du bara lägga till `sling:configRef` till de skärmar, platser eller kanalmappar där alla spelare har uppdaterats till Feature Pack 6.5.9.

I följande diagram visas migreringsstrategin för stora nätverk:

![bild](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Om du vill aktivera funktionen lägger du till minst en mappningsregel och kontrollerar att konfigurationen för återgivningsmappning kan matchas i kontexten för skärmar och kanaler. Följ stegen nedan för att migrera:

1. Lägg till [Återgivningsmappningsregler](/help/user-guide/adaptive-renditions.md).
1. Skapa en mapp för nya kanaler och lägg till en referenspunkt vid återgivningsmappningskonfigurationen.
1. Skapa nya kanaler som ersätter de gamla och överför renderingar.
1. Tilldela om skärmar till de nya kanalerna.
1. Lägg till en referens till de migrerade skärmarna eller platserna som pekar på återgivningsmappningskonfigurationen.
1. Upprepa steg 3, 4 och 5 för alla återstående kanaler och skärmar.

   >[!NOTE]
   >När migreringen är klar måste du se till att ta bort alla konfigurationsreferenser från kanaler, skärmar och platser och lägga till en enda i projektinnehållsnoden.

