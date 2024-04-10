---
title: Använda adaptiva renderingar i AEM Screens
description: På den här sidan beskrivs hur du använder adaptiva renderingar i AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Använda adaptiva renderingar i AEM Screens {#adaptive-renditions}

## Introduktion {#introduction}

Med adaptiva renderingar kan enheterna automatiskt välja den bästa renderingen för en enhet baserat på kunddefinierade regler. Enheterna laddar automatiskt ned och spelar upp den lämpligaste återgivningen av en mediefil baserat på dessa regler, så att kunderna bara kan fokusera på att utforma *main* upplevelse.

## Syfte {#objective}

Som AEM Screens Content Author kan du nu konfigurera enhetsspecifika materialåtergivningar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt.
När en utvecklare lägger till egenskaperna och reglerna för renderingsmappning är du nu redo att tillämpa renderingsmappningen på resurser och sedan inkludera dem i en AEM Screens-kanal.

>[!IMPORTANT]
>Innan du börjar använda adaptiva renderingar i en AEM Screens-kanal bör du läsa mer om den här funktionens arkitektoniska översikt och konfiguration. Se [Adaptiva renderingar: Arkitektur - översikt och konfigurationer](/help/user-guide/adaptive-renditions.md) för mer information.

## Använda adaptiva renderingar i kanaler {#using-adaptive-renditions}

>[!NOTE]
>När du har lagt till [återgivningsmappningsegenskapen till skärpeprojektet](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) och [regler för renderingsmappning](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)som innehållsförfattare är du nu redo att använda återgivningarna på dina resurser.

### Använda återgivningar på resurser {#apply-renditions-assets}

Följ stegen nedan för att tillämpa renderingar på resurserna som du vill använda i kanalen för visningsskärmar:

1. Navigera till **Resurser** i din AEM.

1. Skapa en version av resursen som bättre passar signeringsvisningen, till exempel `seahorse.jpg`.

1. Välj namngivningsmönstret för återgivningen, till exempel`landscape`, som det som definierades i **mönster** egenskap i **CRXDE Lite**. Se [Lägga till återgivningsmappningsregler](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) för mer information.

1. Klicka på **Lägg till återgivning** för att överföra återgivningen enligt bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Markera resursens nya namn. Den återgivning som du lägger till måste innehålla mönstret (definierat i steg 3), till exempel `seahorse-landscape.png`.

1. När du har lagt till resursen markerar du resursen och klickar på **Hantera publikation** från åtgärdsfältet för att publicera resursen.

   ![bild](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Se [On Demand Content Update](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en) om du vill veta mer om hur du hanterar publikation och levererar innehållsuppdateringar från författare till publiceringsenhet.


## Migreringsstrategi {#migration-strategy}

>[!IMPORTANT]
>För stora nätverk rekommenderar vi att migreringen görs gradvis för att minska riskerna eftersom funktionen kommer att medföra förändringar i manifest- och fillagringsformatet. Lägga till `sling:configRef` till hela projektet med att uppdatera alla spelare till Feature Pack 6.5.9. Om du har uppdaterat några spelare måste du lägga till `sling:configRef` endast till de skärmar, platser eller kanalmappar där alla spelare har uppdaterats till Feature Pack 6.5.9.

I följande diagram visas migreringsstrategin för stora nätverk:

![bild](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Om du vill aktivera funktionen lägger du till minst en mappningsregel och kontrollerar att konfigurationen för återgivningsmappning kan matchas i kontexten för skärmar och kanaler. Följ stegen nedan för att migrera:

1. Lägg till [Regler för återgivningsmappning](/help/user-guide/adaptive-renditions.md).
1. Skapa en mapp för nya kanaler och lägg till en referenspunkt vid återgivningsmappningskonfigurationen.
1. Skapa nya kanaler som ersätter de gamla och överför renderingar.
1. Tilldela om skärmar till nya kanaler.
1. Lägg till en referens till de migrerade skärmarna eller platserna som pekar på återgivningsmappningskonfigurationen.
1. Upprepa steg 3, 4 och 5 för alla återstående kanaler och skärmar.

   >[!NOTE]
   >När migreringen är klar måste du se till att ta bort alla konfigurationsreferenser från kanaler, skärmar och platser och lägga till en enda i projektinnehållsnoden.
