---
title: Temperaturaktivering i resecentret
seo-title: Travel Center Temperature Activation
description: I följande exempel visas användningen av lokal temperaturaktivering i resecentret baserat på de värden som anges i Google Sheets.
seo-description: The following use case demonstrates the usage of travel center local temperature activation based on the values populated in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Temperaturaktivering i resecentret {#travel-center-temperature-activation}

I följande exempel visas användningen av lokal temperaturaktivering i resecentret baserat på de värden som anges i Google Sheets.

## Beskrivning {#description}

Om värdet är mindre än 50 visas en bild med varma drycker och om värdet är större än eller lika med 50 visas bilden med kalla drycker. Om något annat eller inget värde anges visas en standardbild.

## Förhandsvillkor {#preconditions}

Innan du börjar implementera aktiveringen av lokal temperatur i resecentralen måste du lära dig hur du konfigurerar ***Datalager***, ***Målgruppssegmentering*** och ***Aktivera mål för kanaler*** i ett AEM Screens-projekt.

Se [ContextHub konfigureras i AEM Screens](configuring-context-hub.md) för detaljerad information.

## Grundläggande flöde {#basic-flow}

Följ stegen nedan för att implementera användningsexemplet för aktivering av lokal temperatur i Travel Center:

1. **Fylla i Google-ark**

   1. Navigera till ContextHubDemo Google Sheet.
   1. Lägga till en kolumn med **Rubrik1** med motsvarande värde för temperaturen.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Konfigurera segmenten i publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (se ***Steg 2: Konfigurera målgruppssegmentering*** in **[ContextHub konfigureras i AEM Screens](configuring-context-hub.md)** sida för mer information).

   1. Välj **Blad A1 1** och klicka **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **googlesheets/value/1/0** från listrutan i **Egenskapsnamn**

   1. Välj **Operator** as **större än eller lika med** i listrutan

   1. Ange **Värde** as **50**

   1. På samma sätt väljer du **Blad A1 2** och klicka **Redigera**.

   1. Välj **Jämförelseegenskap - värde** och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **googlesheets/value/1/0** från listrutan i **Egenskapsnamn**

   1. Välj **Operator** as **mindre än** i listrutan

   1. Ange **Värde** as **50**

1. Navigera och markera kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel **DataDrivenVäder**, används en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   >
   >Din kanal bör redan ha en standardbild och publikerna bör vara förkonfigurerade enligt beskrivningen i [ContextHub konfigureras i AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Du borde ha konfigurerat **ContextHub** **Konfigurationer** använda kanalen **Egenskaper** > **Personalisering** -fliken.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Välj **Målinriktning** i redigeraren och väljer **Varumärke** och **Aktivitet** i listrutan och klicka på **Börja målinrikta**.

   ![new_activity3](assets/new_activity3.gif)

1. **Kontrollera förhandsvisningen**

   1. Klicka **Förhandsgranska.** Du kan även öppna Google Sheet och uppdatera värdet.
   1. Om du ändrar värdet till mindre än 50 bör du kunna se en bild av sommardrycker. Om värdet i Google Sheet är 50 eller högre än vad som ska kunna visas på en bild av en het drink.

   ![result3](assets/result3.gif)
