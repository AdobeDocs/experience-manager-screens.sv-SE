---
title: Målinställd aktivering för butikslager
seo-title: Målinställd aktivering för butikslager
description: Denna Use Case visar butikslagret för tre olika färgade tröjor. Beroende på hur många tröjor som finns i lager och som spelats in på Google Sheets, visas bilden (röd, grön eller blå tröja) med det högsta antalet på skärmen.
seo-description: Denna Use Case visar butikslagret för tre olika färgade tröjor. Beroende på hur många tröjor som finns i lager och som spelats in på Google Sheets, visas bilden (röd, grön eller blå tröja) med det högsta antalet på skärmen.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Redigeringsskärmar
role: Administratör, utvecklare
level: Mellanliggande
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---


# Målinställd aktivering för butikslager {#retail-inventory-targeted-activation}

I följande exempel visas tre olika bilder baserat på värdena i Google Sheet.

## Beskrivning {#description}

Denna Use Case visar butikslagret för tre olika färgade tröjor. Beroende på hur många tröjor som finns i lager och som spelats in på Google Sheets, visas bilden (röd, grön eller blå tröja) med det högsta antalet på skärmen.

I det här fallet visas den röda, gröna eller blå tröjan på skärmen baserat på det högsta antalet svettare som är tillgängliga.

## Förhandsvillkor {#preconditions}

Innan du börjar implementera aktiveringen av målinriktningen för detaljhandelslager måste du lära dig hur du konfigurerar ***datalager***, ***målgruppssegmentering*** och ***Aktivera målanpassning för kanaler*** i ett AEM Screens-projekt.

Mer information finns i [Konfigurera ContextHub i AEM Screens](configuring-context-hub.md).

## Grundläggande flöde {#basic-flow}

Följ stegen nedan för att implementera användningsexemplet för butikslageraktivering:

1. **Fylla i Google Sheets**

   1. Navigera till ContextHubDemo Google Sheet.
   1. Lägg till tre kolumner (röd, grön och blå) med motsvarande värden för tre olika tröjor.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Konfigurera publikerna enligt kraven**

   1. Navigera till segmenten i målgruppen (se ***Steg 2: Konfigurerar målgruppssegmentering*** på **[Konfigurera ContextHub på AEM Screens-sidan](configuring-context-hub.md)** för mer information).

   1. Lägg till tre nya segment **For_Red**, **For_Green** och **For_Blue**.

   1. Välj **For_Red** och klicka på **Redigera** i åtgärdsfältet.

   1. Dra och släpp **jämförelsen: Egenskap - Egenskap** till redigeraren och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **googlesheets/value/1/2** i listrutan i **Förnamn på egenskap**

   1. Välj **Operator** som **större än** i listrutan

   1. Välj **datatyp** som **tal**

   1. Välj **googlesheets/value/1/1** i listrutan i **Andra egenskapsnamn**.

   1. Dra och släpp **en annan jämförelse: Egenskap - Egenskap** till redigeraren och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **GoogleSheets/value/1/2** i listrutan i **First Property name**.

   1. Välj **Operator** som **större än** i listrutan

   1. Välj **Datatyp** som **tal**

   1. Välj **googlesheets/value/1/0** i listrutan i **Andra egenskapsnamn**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Redigera och lägg till egenskapsregler för jämförelse i segmentet **For_Blue** enligt bilden nedan:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Du kan på liknande sätt redigera och lägga till egenskapsregler för jämförelse i** For_Green **segment enligt bilden nedan:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >För segment **For_Green** och **For_Green** kan data inte matchas i redigeraren eftersom endast den första jämförelsen är giltig från och med nu enligt värdena i Google Sheet.

1. Navigera till och markera din **DataDrivenRetail**-kanal (en sekvenskanal) och klicka på **Redigera** i åtgärdsfältet.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Du bör ha konfigurerat din **ContextHub** **Configurations** med hjälp av fliken **Egenskaper** —> **Personalisering**.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Du måste välja både **Varumärke** och **Område** för att aktiviteterna ska visas korrekt när du startar Målprocessen.

1. **Lägga till en standardbild**

   1. Lägg till en standardbild i kanalen och klicka på **Mål**.
   1. Välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Starta målgruppsanpassning**.

   1. Klicka på **Starta målanpassning**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Innan du börjar målinrikta måste du lägga till segmenten (**For_Green**, **For_Red** och **For_Blue**) genom att klicka på **+ Lägg till upplevelseanpassning** från sidospåret enligt bilden nedan.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Lägg till bilderna i alla tre olika scenarier enligt nedan.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Kontrollera förhandsvisningen**

   1. Klicka på **Förhandsgranska.** Öppna även Google Sheet och uppdatera värdet.
   1. Ändra värdet för alla tre olika kolumner så kommer du att märka att visningsbilden uppdateras enligt det högsta värdet i lagret.

   ![retail_result](assets/retail_result.gif)

