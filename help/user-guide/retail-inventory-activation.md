---
title: Målinställd aktivering för butikslager
seo-title: Retail Inventory Targeted Activation
description: Denna Use Case visar butikslagret för tre olika färgade tröjor. Beroende på hur många tröjor som finns i lager och som är inspelade i Google Sheets, visas bilden (röd, grön eller blå tröja) med det högsta antalet på skärmen.
seo-description: This Use Case showcases the retail inventory stock for three different colored sweatshirts. Depending on the number of sweatshirts available in stock that is recorded in Google Sheets, the image (red, green, or blue sweatshirt) with highest number is displayed on the screen.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Målinställd aktivering för butikslager {#retail-inventory-targeted-activation}

I följande exempel visas tre olika bilder baserat på värdena i Google-bladet.

## Beskrivning {#description}

Denna Use Case visar butikslagret för tre olika färgade tröjor. Beroende på hur många tröjor som finns i lager och som är inspelade i Google Sheets, visas bilden (röd, grön eller blå tröja) med det högsta antalet på skärmen.

I det här fallet visas den röda, gröna eller blå tröjan på skärmen baserat på det högsta antalet svettare som är tillgängliga.

## Förhandsvillkor {#preconditions}

Innan du börjar implementera aktiveringen av lagermålinriktning måste du lära dig hur du konfigurerar ***Datalager***, ***Målgruppssegmentering*** och ***Aktivera mål för kanaler*** i ett AEM Screens-projekt.

Se [ContextHub konfigureras i AEM Screens](configuring-context-hub.md) för detaljerad information.

## Grundläggande flöde {#basic-flow}

Följ stegen nedan för att implementera användningsexemplet för butikslageraktivering:

1. **Fylla i Google-ark**

   1. Navigera till ContextHubDemo Google Sheet.
   1. Lägg till tre kolumner (röd, grön och blå) med motsvarande värden för tre olika tröjor.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Konfigurera publikerna enligt kraven**

   1. Navigera till segmenten i målgruppen (se ***Steg 2: Konfigurera målgruppssegmentering*** in **[ContextHub konfigureras i AEM Screens](configuring-context-hub.md)** sida för mer information).

   1. Lägg till tre nya segment **For_Red**, **For_Green** och **För_blå**.

   1. Välj **For_Red** och klicka **Redigera** i åtgärdsfältet.

   1. Dra och släpp **Comparison : Property - Property** till redigeraren och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **googlesheets/value/1/2** från listrutan i **Första egenskapsnamnet**

   1. Välj **Operator** as **större än** i listrutan

   1. Markera **Datatyp** as **tal**

   1. Välj **googlesheets/value/1/1** från listrutan i **Andra egenskapsnamnet**.

   1. Dra och släpp **en annan jämförelse: property - property** till redigeraren och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **googlesheets/value/1/2** från listrutan i **Första egenskapsnamnet**.

   1. Välj **Operator** as **större än** i listrutan

   1. Välj **Datatyp** as **tal**

   1. Välj **googlesheets/value/1/0** från listrutan i **Andra egenskapsnamnet**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   På samma sätt kan du redigera och lägga till egenskapsregler för jämförelse i **För_blå** segmentet enligt figuren nedan:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Du kan på liknande sätt redigera och lägga till egenskapsregler för jämförelse i** For_Green **segment enligt bilden nedan:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Du kommer att märka det för segment **For_Green** och **For_Green** går det inte att matcha data i redigeraren eftersom endast den första jämförelsen är giltig från och med nu enligt värdena i Google Sheet.

1. Navigera och markera **DataDrivenRetail** kanal (en sekvenskanal) och klicka på **Redigera** i åtgärdsfältet.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Du borde ha konfigurerat **ContextHub** **Konfigurationer** använda kanalen **Egenskaper** > **Personalisering** -fliken.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >Du måste markera båda **Varumärke** och **Område** för att aktiviteterna ska visas korrekt när du startar målprocessen.

1. **Lägga till en standardbild**

   1. Lägg till en standardbild i kanalen och klicka på **Målinriktning**.
   1. Välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Börja målinrikta**.

   1. Klicka **Börja målinrikta**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Innan du börjar målinrikta måste du lägga till segmenten (**For_Green**, **For_Red** och **För_blå**) genom att klicka på **+ Lägg till Experience Targeting** från sidospåret enligt figuren nedan.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Lägg till bilderna i alla tre olika scenarier enligt nedan.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Kontrollera förhandsvisningen**

   1. Klicka **Förhandsgranska.** Du kan även öppna Google Sheet och uppdatera värdet.
   1. Ändra värdet för alla tre olika kolumner så kommer du att märka att visningsbilden uppdateras enligt det högsta värdet i lagret.

   ![retail_result](assets/retail_result.gif)
