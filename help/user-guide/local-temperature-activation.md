---
title: Temperaturaktivering i resecentret
seo-title: Temperaturaktivering i resecentret
description: I följande exempel visas användningen av lokal temperaturaktivering i resecentret baserat på de värden som anges i Google Sheets.
seo-description: I följande exempel visas användningen av lokal temperaturaktivering i resecentret baserat på de värden som anges i Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Temperaturaktivering i resecentret {#travel-center-temperature-activation}

I följande exempel visas användningen av lokal temperaturaktivering i resecentret baserat på de värden som anges i Google Sheets.

## Beskrivning {#description}

Om ditt Google Sheets har ett värde under 50 visas en bild med varma drycker och om värdet är större än eller lika med 50 visas bilden med kalla drycker. Om något annat eller inget värde anges visas en standardbild.

## Förhandsvillkor {#preconditions}

Innan du börjar implementera aktiveringen av lokal temperatur i resecentret måste du lära dig hur du konfigurerar ***datalagret***, ***målgruppssegmentering*** och ***Aktivera målanpassning för kanaler*** i ett AEM-skärmsprojekt.

Mer information finns i [Configuring ContextHub in AEM Screens](configuring-context-hub.md) .

## Grundläggande flöde {#basic-flow}

Följ stegen nedan för att implementera användningsexemplet för aktivering av lokal temperatur i Travel Center:

1. **Fylla i Google Sheets**

   1. Navigera till ContextHubDemo Google Sheet.
   1. Lägg till en kolumn med **Rubrik1** med motsvarande värde för temperatur.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Konfigurera segmenten i publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (se ***steg 2: Ställa in målgruppssegmentering*** i **[Configuring ContextHub på sidan AEM-skärmar](configuring-context-hub.md)**för mer information).

   1. Markera **blad A1 1** och klicka på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**

   1. Välj **Operatorn** som **större än eller lika med **i listrutan

   1. Ange **värdet** som **50**

   1. På samma sätt väljer du* Sheets A1 2 **och klickar på **Redigera**.

   1. Markera **jämförelseegenskapen - värde** och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**

   1. Välj **Operator** som **less-than **i listrutan

   1. Ange **värdet** som **50**

1. Navigera och markera kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel används **DataDrivenWeather** som en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   >
   >Din kanal bör redan ha en standardbild och publikationerna bör vara förkonfigurerade enligt beskrivningen i [Konfigurera ContextHub i AEM-skärmar](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Du bör ha konfigurerat **ContextHub** **Configurations** med hjälp av fliken **Kanalegenskaper** —> **Personalisering** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Välj **Riktning** i redigeraren och välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Start Targeting**.

   ![new_activity3](assets/new_activity3.gif)

1. **Kontrollera förhandsvisningen**

   1. Klicka på **Förhandsgranska.** Öppna även Google Sheet och uppdatera värdet.
   1. Om du ändrar värdet till mindre än 50 bör du kunna se en bild av sommardrycker. Om värdet i Google Sheet är 50 eller högre än vad som ska kunna visa bilden med en het drink.
   ![result3](assets/result3.gif)

