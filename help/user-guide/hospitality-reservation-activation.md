---
title: Aktivering av hotellreservation
description: Se hur det här användningsexemplet visar hur man använder aktivering av gästreservation baserat på de värden som anges i Google Sheets.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Aktivering av hotellreservation {#hospitality-reservation-activation}

Följande exempel visar hur man använder aktivering av sjukhusbokning baserat på de värden som anges i Google Sheets.

## Beskrivning {#description}

I det här fallet fylls Google Sheet i med en procentandel reservationer på två restauranger **`Restaurant1`** och **`Restaurant2`**. En formel tillämpas baserat på värdena `Restaurant1` och `Restaurant2` och, baserat på formeln, värdet 1 eller 2 tilldelas till kolumnen **AdTarget**.

Om värdet är **`Restaurant1`** > **`Restaurant2`** tilldelas **AdTaget** värdet **1**, annars tilldelas **AdTarget** värdet **2**. Värdet 1 genererar ett *Steak food* -alternativ och värdet två ger en visning av *thailändska food* -alternativet på bildskärmen.

## Förhandsvillkor {#preconditions}

Läs om hur du konfigurerar ***datalagret***, ***Målgruppssegmentering*** och ***Aktivera mål för kanaler*** i ett AEM Screens-projekt innan du börjar implementera reservationsaktiveringen.

Mer information finns i [Konfigurera ContextHub i AEM Screens](configuring-context-hub.md).

## Grundläggande flöde {#basic-flow}

Följ instruktionerna nedan för att implementera aktivering av gästreservation för ditt AEM Screens-projekt:

1. **Fyller i Google-bladen och lägger till formeln**.

   Använd till exempel formeln på den tredje kolumnen **AdTarget**, som visas i figuren nedan.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Konfigurera segmenten i Publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (mer information finns i ***Steg 2: Konfigurera målgruppssegmentering*** i **[Konfigurera ContextHub på AEM Screens](configuring-context-hub.md)** -sidan).
   1. Klicka på **Blad A1** och klicka på **Redigera**.
   1. Klicka på jämförelseegenskapen och klicka på ikonen **Konfiguration** .
   1. Klicka på **Googlesheets/value/1/2** i listrutan i **Egenskapsnamn**.
   1. Klicka på **Operator** som **equal** i listrutan.
   1. Ange **Value** som **1**.
   1. Klicka på **Blad A1** och sedan på **Redigera**.
   1. Klicka på jämförelseegenskapen och klicka på ikonen **Konfiguration** .
   1. Klicka på **Googlesheets/value/1/2** i listrutan i **Egenskapsnamn**.
   1. Klicka på **Operator** som **2**.

1. Navigera och klicka på kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel, **DataDrivenRestaurant**, används en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   >
   >Din kanal bör redan ha en standardbild och publikationerna bör vara förkonfigurerade enligt beskrivningen i [Konfigurera ContextHub i AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Din **ContextHub** **Configurations** som använder fliken **Egenskaper** > **Personalization** bör redan ha konfigurerats.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Klicka på **Riktning** i redigeraren och klicka på **Varumärke** och **Aktivitet** i listrutan och klicka sedan på **Start Targeting**.
1. **Kontrollerar förhandsvisningen**

   1. Klicka på **Förhandsgranska.** Öppna även dina Google-blad och uppdatera värdet.
   1. Uppdatera värdet i kolumnerna **`Restaurant1`** och **`Restaurant2`**. Om **`Restaurant1`** > **`Restaurant2`,** ska du kunna visa en bild av maten *Steak* , annars visas matbilden *Thai* på skärmen.

   ![result5](assets/result5.gif)
