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
feature: Redigeringsskärmar
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# Aktivering av hotellreservation {#hospitality-reservation-activation}

I följande exempel visas hur aktiveringen av sjukhusbokning har gjorts baserat på de värden som anges i Google Sheets.

## Beskrivning {#description}

I det här användningsfallet fylls Google Sheet i med en procentandel reservationer på två restauranger **Restaurant1** och **Restaurant2**. En formel tillämpas baserat på värdena för Restaurant1 och Restaurant2 och baserat på formeln, tilldelas värdet 1 eller 2 till kolumnen **AdTarget**.

Om värdet för **Restaurant1** > **Restaurant2**, tilldelas **AdTarget** värdet **1** annars **AdTarget** **2**. Värdet 1 genererar *Svag mat* och Värde 2 ger *Thai food*-alternativ på bildskärmen.

## Förhandsvillkor {#preconditions}

Innan du börjar implementera reservationsaktiveringen måste du lära dig att konfigurera ***datalagret***, ***målgruppssegmentering*** och ***Aktivera målgruppsanpassning för kanaler*** i ett AEM Screens-projekt.

Mer information finns i [Konfigurera ContextHub i AEM Screens](configuring-context-hub.md).

## Grundläggande flöde {#basic-flow}

Följ stegen nedan för att implementera användningsexemplet för aktivering av gästreservation för ditt AEM Screens-projekt:

1. **Fylla i Google Sheets och lägga till formeln.**

   Du kan till exempel använda formeln på den tredje kolumnen **AdTarget**, vilket visas i figuren nedan.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Konfigurera segmenten i publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (se ***Steg 2: Konfigurerar målgruppssegmentering*** på **[Konfigurera ContextHub på AEM Screens-sidan](configuring-context-hub.md)** för mer information).

   1. Välj **Blad A1 1** och klicka på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/2** i listrutan i **Egenskapsnamn**

   1. Välj **Operator** som **lika med** i listrutan

   1. Ange **värdet** som **1**

   1. På samma sätt väljer du **Blad A1 2** och klickar på **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **Googlesheets/value/1/2** i listrutan i **Egenskapsnamn**

   1. Välj **Operator** som **2**

1. Navigera och markera kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel, **DataDrivenRestaurant**, används en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   >
   >Din kanal bör redan ha en standardbild och publikationerna bör vara förkonfigurerade enligt beskrivningen i [Konfigurera ContextHub i AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Du bör ha konfigurerat din **ContextHub** **Configurations** med hjälp av fliken **Egenskaper** —> **Personalisering**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Välj **Mål** i redigeraren och välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Starta målgruppsanpassning**.
1. **Kontrollera förhandsvisningen**

   1. Klicka på **Förhandsgranska.** Öppna även dina Google Sheets och uppdatera värdet.
   1. Uppdatera värdet i kolumnerna **Restaurant1** och **Restaurant2**. Om **Restaurant1** > **Restaurant2,** bör du kunna visa en bild av *Steak* mat otherwise, *Thai* food image displays on your screen.
   ![result5](assets/result5.gif)
