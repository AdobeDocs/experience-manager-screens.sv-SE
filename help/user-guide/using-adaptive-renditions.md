---
title: Använda adaptiva renderingar i AEM Screens
description: Lär dig hur du använder adaptiva renderingar i AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: f1ddcf5e5ee9691e436e139ce0084f2c39f9c9dd
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Använda adaptiva renderingar i AEM Screens {#adaptive-renditions}

## Introduktion {#introduction}

>[!CAUTION]
>Den här funktionen stöds endast på AEM lokalt (AEM 6.x). Det stöds inte på AEM as a Cloud Service.

Med adaptiva renderingar kan enheterna klicka på den bästa renderingen automatiskt för en enhet baserat på kunddefinierade regler. Enheterna laddar automatiskt ned och spelar upp den lämpligaste återgivningen av en resurs baserat på dessa regler. Den låter kunderna fokusera på att utforma *main*-upplevelsen.

## Syfte {#objective}

Som AEM Screens Content Author kan du nu konfigurera enhetsspecifika materialåtergivningar så att de hämtas och spelas upp automatiskt utan att du behöver skapa alla innehållsvarianter manuellt.
När en utvecklare har lagt till egenskaper och regler för återgivningsmappning kan du tillämpa återgivningsmappningen på resurser och sedan inkludera dem i en AEM Screens-kanal.

>[!IMPORTANT]
>Innan du börjar använda adaptiva renderingar i en AEM Screens-kanal rekommenderar Adobe att du lär dig mer om den här funktionens arkitektoniska översikt och konfiguration. Se [Adaptiva renderingar: Arkitekturöversikt och konfigurationer](/help/user-guide/adaptive-renditions.md).

## Använda adaptiva renderingar i kanaler {#using-adaptive-renditions}

>[!NOTE]
>När du har lagt till egenskapen [återgivningsmappning i Screens Project](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) och [återgivningsmappningsreglerna](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) kan du som innehållsförfattare använda återgivningarna på dina resurser.

### Använda återgivningar i Assets {#apply-renditions-assets}

Så här använder du återgivningar på resurser som du vill använda i Screens-kanalen Tour.

1. Navigera till mappen **Assets** i din AEM-instans.
1. Skapa en version av resursen som bättre passar signeringsvisningen, till exempel `seahorse.jpg`.
1. Välj namngivningsmönstret för återgivningen, till exempel `landscape`, som liknar det som definierats i egenskapen **pattern** i **CRXDE Lite**. Mer information finns i [Lägga till återgivningsmappningsregler](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules).
1. Klicka på **Lägg till återgivning** för att överföra återgivningen, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Klicka på resursens nya namn. Den återgivning som du lägger till måste innehålla mönstret (definierat i steg 3), till exempel `seahorse-landscape.png`.
1. När du har lagt till resursen klickar du på resursen och sedan på **Hantera publikation** i åtgärdsfältet för att publicera resursen.

   ![bild](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Mer information om hur du hanterar publikation och levererar innehållsuppdateringar från författare till publiceringsenhet finns i [Uppdatera on demand](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content) .

## Migreringsstrategi {#migration-strategy}

>[!IMPORTANT]
>För stora nätverk rekommenderar Adobe att migreringen sker successivt för att minska riskerna. Orsaken är att funktionen kan medföra förändringar i manifest- och fillagringsformatet. Om du lägger till `sling:configRef` i hela projektet måste alla spelare uppdateras till Feature Pack 6.5.9. Om du har uppdaterat några av spelarna lägger du bara till `sling:configRef` i de skärmar, platser eller kanalmappar där alla spelare har uppdaterats till Feature Pack 6.5.9.

I följande diagram visas migreringsstrategin för stora nätverk:

![bild](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Om du vill aktivera funktionen lägger du till minst en mappningsregel och ser till att konfigurationen för återgivningsmappning kan matchas i kontexten för skärmar och kanaler. Följ stegen nedan för att migrera:

1. Lägg till [återgivningsmappningsregler](/help/user-guide/adaptive-renditions.md).
1. Skapa en mapp för nya kanaler och lägg till en referenspunkt vid återgivningsmappningskonfigurationen.
1. Skapa kanaler som ersätter de gamla och överför renderingar.
1. Tilldela om skärmar till nya kanaler.
1. Lägg till en referens till de migrerade skärmar eller platser som pekar på återgivningsmappningskonfigurationen.
1. Upprepa steg 3, 4 och 5 för alla återstående kanaler och skärmar.

   >[!NOTE]
   >När migreringen är klar måste du se till att ta bort alla konfigurationsreferenser från kanaler, skärmar och platser och lägga till en enda i projektinnehållsnoden.
