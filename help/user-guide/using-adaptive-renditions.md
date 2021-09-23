---
title: Använda adaptiva renderingar i AEM Screens
description: På den här sidan beskrivs hur du använder adaptiva renderingar i AEM Screens.
index: false
source-git-commit: 687b850860cc0576b9e3ee607cac2f9e5685d33e
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Använda adaptiva renderingar i AEM Screens {#adaptive-renditions}

## Introduktion {#introduction}

Med adaptiva renderingar kan enheterna automatiskt välja den bästa renderingen för en enhet baserat på kunddefinierade regler. Enheterna laddar automatiskt ned och spelar upp den lämpligaste återgivningen av en resurs baserat på dessa regler, vilket gör att kunderna bara kan fokusera på att utforma *main*-upplevelsen.

## Syfte {#objective}

Som AEM Screens Content Author kan du nu konfigurera enhetsspecifika materialåtergivningar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt.
När en utvecklare lägger till egenskaperna och reglerna för renderingsmappning är du nu redo att tillämpa renderingsmappningen på resurser och sedan inkludera dem i en AEM Screens-kanal.

>[!IMPORTANT]
>Innan du börjar använda adaptiva renderingar i en AEM Screens-kanal bör du läsa mer om den här funktionens arkitektoniska översikt och konfiguration. Se Adaptiva renderingar: Arkitektöversikt och konfigurationer för mer information.

## Migreringsstrategi {#migration-strategy}

>[!IMPORTANT]
>För stora nätverk rekommenderar vi att migreringen görs gradvis för att minska riskerna eftersom funktionen kommer att medföra förändringar i manifest- och fillagringsformatet.

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

## Överföra renderingar och använda adaptiva renderingar i en AEM Screens-kanal {#upload-renditions}

1. Skapa en version av resursen som bättre passar signeringsvisningen, till exempel `portrait orientation`.

1. Välj namngivningsmönstret för återgivningen, till exempel`portrait`.

1. Byt namn på resursfilen så att den innehåller mönstret, till exempel `my_asset_portrait.png`.

1. Klicka på **Lägg till återgivning** för att överföra återgivningen, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/add-rendition.png)