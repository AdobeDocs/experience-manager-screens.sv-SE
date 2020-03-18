---
title: Aktivering av hotellreservation
seo-title: Aktivering av hotellreservation
description: I följande exempel visas hur aktiveringen av sjukhusbokning har gjorts baserat på de värden som anges i Google Sheets.
seo-description: I följande exempel visas hur aktiveringen av sjukhusbokning har gjorts baserat på de värden som anges i Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Aktivering av hotellreservation {#hospitality-reservation-activation}

I följande exempel visas hur aktiveringen av sjukhusbokning har gjorts baserat på de värden som anges i Google Sheets.

## Beskrivning {#description}

I det här användningsfallet fylls Google Sheet i med en procentandel reservationer på två restauranger **Restaurant1** och **Restaurant2**. En formel tillämpas baserat på värdena för Restaurant1 och Restaurant2 och baserat på formeln, så tilldelas värdet 1 eller 2 till **AdTarget** -kolumnen.

Om värdet för **Restaurant1** > **Restaurant2** tilldelas **AdTaget** värdet **1** , i annat fall tilldelas **AdTarget** **** värdet¥2¥. Värdet 1 genererar *alternativet Svag mat* och värdet 2 ger resultatet att *thailändska matalternativ* visas på skärmen.

## Förhandsvillkor {#preconditions}

Innan du börjar implementera aktiveringen av bokningen måste du lära dig hur du konfigurerar ***datalagret***, ***målgruppssegmenteringen*** och ***Aktivera målanpassning för kanaler*** i ett AEM-skärmsprojekt.

Mer information finns i [Configuring ContextHub in AEM Screens](configuring-context-hub.md) .

## Grundläggande flöde {#basic-flow}

Följ stegen nedan för att implementera användningsexemplet för aktivering av gästreservation för ditt AEM Screens-projekt:

1. **Fylla i Google Sheets och lägga till formeln.**

   Du kan t.ex. använda formeln på den tredje kolumnen **AdTarget**, vilket visas i figuren nedan.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Konfigurera segmenten i publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (se ***steg 2: Ställa in målgruppssegmentering*** i **[Configuring ContextHub på sidan AEM-skärmar](configuring-context-hub.md)**för mer information).

   1. Markera **blad A1 1** och klicka på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/2** i listrutan i **Egenskapsnamn**

   1. Välj **Operator** as **equal** i listrutan

   1. Ange **värdet** som **1**

   1. På samma sätt markerar du **Blad A1 2** och klickar på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/2** i listrutan i **Egenskapsnamn**

   1. Välj **operatorn** som **2**

1. Navigera och markera kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel, **DataDrivenRestaurant**, används en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   >
   >Din kanal bör redan ha en standardbild och publikationerna bör vara förkonfigurerade enligt beskrivningen i [Konfigurera ContextHub i AEM-skärmar](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Du bör ha konfigurerat **ContextHub** **Configurations** med hjälp av fliken **Kanalegenskaper** —> **Personalisering** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Välj **Riktning** i redigeraren och välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Start Targeting**.
1. **Kontrollera förhandsvisningen**

   1. Klicka på **Förhandsgranska.** Öppna även dina Google Sheets och uppdatera värdet.
   1. Uppdatera värdet i kolumnerna **Restaurant1** och **Restaurant2** . Om **Restaurant1** > **Restaurant2,** bör du kunna visa en bild av *Steak* food, annars visas den thailändska ** matbilden på skärmen.
   ![result5](assets/result5.gif)

