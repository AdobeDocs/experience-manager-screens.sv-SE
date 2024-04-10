---
title: Aktivering av hotellreservation
seo-title: Hospitality Reservation Activation
description: Följande exempel visar hur man använder aktivering av sjukhusbokning baserat på de värden som anges i Google Sheets.
seo-description: The following use case demonstrates the usage of hospital reservation activation based on the values populated in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Aktivering av hotellreservation {#hospitality-reservation-activation}

Följande exempel visar hur man använder aktivering av sjukhusbokning baserat på de värden som anges i Google Sheets.

## Beskrivning {#description}

I det här användningsfallet fylls Google Sheet i med en procentandel reservationer på två restauranger **Restaurant1** och **Restaurant2**. En formel tillämpas baserat på värdena för Restaurant1 och Restaurant2 och baserat på formeln tilldelas värdet 1 eller 2 till **AdTarget** Kolumn.

Om värdet för **Restaurant1** > **Restaurant2** sedan **AdTaget** är tilldelat värde **1** annars **AdTarget** är tilldelat värde **2**. Värde 1 genererar *Svag mat* option and Value 2 results in display of *Thailändska livsmedel* på bildskärmen.

## Förhandsvillkor {#preconditions}

Innan du börjar implementera aktiveringen av reservationen måste du lära dig hur du konfigurerar ***Datalager***, ***Målgruppssegmentering*** och ***Aktivera mål för kanaler*** i ett AEM Screens-projekt.

Se [ContextHub konfigureras i AEM Screens](configuring-context-hub.md) för detaljerad information.

## Grundläggande flöde {#basic-flow}

Följ stegen nedan för att implementera användningsexemplet för aktivering av gästreservation för ditt AEM Screens-projekt:

1. **Fylla i Google-bladen och lägga till formeln.**

   Använd till exempel formeln på den tredje kolumnen **AdTarget**, vilket visas i figuren nedan.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Konfigurera segmenten i publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (se ***Steg 2: Konfigurera målgruppssegmentering*** in **[ContextHub konfigureras i AEM Screens](configuring-context-hub.md)** sida för mer information).

   1. Välj **Blad A1 1** och klicka **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **googlesheets/value/1/2** från listrutan i **Egenskapsnamn**

   1. Välj **Operator** as **likhet** i listrutan

   1. Ange **Värde** as **1**

   1. På samma sätt väljer du **Blad A1 2** och klicka **Redigera**.

   1. Markera jämförelseegenskapen och klicka på konfigurationsikonen för att redigera egenskaperna.
   1. Välj **googlesheets/value/1/2** från listrutan i **Egenskapsnamn**

   1. Välj **Operator** as **2**

1. Navigera och markera kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel **DataDrivenRestaurant**, används en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   >
   >Din kanal bör redan ha en standardbild och publikerna bör vara förkonfigurerade enligt beskrivningen i [ContextHub konfigureras i AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Du borde ha konfigurerat **ContextHub** **Konfigurationer** använda kanalen **Egenskaper** > **Personalisering** -fliken.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Välj **Målinriktning** i redigeraren och väljer **Varumärke** och **Aktivitet** i listrutan och klicka på **Börja målinrikta**.
1. **Kontrollera förhandsvisningen**

   1. Klicka **Förhandsgranska.** Du kan även öppna dina Google-blad och uppdatera deras värde.
   1. Uppdatera värdet i **Restaurant1** och **Restaurant2** kolumner. If **Restaurant1** > **Restaurant2,** du bör kunna visa en bild av *Stopp* annan mat, *Thailändska* matbilden visas på skärmen.

   ![result5](assets/result5.gif)
