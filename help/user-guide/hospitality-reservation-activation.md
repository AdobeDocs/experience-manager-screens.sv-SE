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
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Aktivering av hotellreservation {#hospitality-reservation-activation}

Följande exempel visar hur man använder aktivering av sjukhusbokning baserat på de värden som anges i Google Sheets.

## Beskrivning {#description}

I det här fallet fylls Google Sheet i med en procentandel reservationer på två restauranger **`Restaurant1`** och **`Restaurant2`**. En formel används baserat på värden för `Restaurant1` och `Restaurant2` och baserat på formeln tilldelas värdet 1 eller 2 till **AdTarget** Kolumn.

Om värdet för **`Restaurant1`** > **`Restaurant2`** sedan **AdTaget** är tilldelat värde **1** annars **AdTarget** är tilldelat värde **2**. Värde 1 genererar *Svag mat* option och Value two results in display of *Thailändska livsmedel* på bildskärmen.

## Förhandsvillkor {#preconditions}

Läs om hur du konfigurerar innan du börjar implementera reservationsaktiveringen ***Datalager***, ***Målgruppssegmentering*** och ***Aktivera mål för kanaler*** i ett AEM Screens-projekt.

Se [ContextHub konfigureras i AEM Screens](configuring-context-hub.md) för detaljerad information.

## Grundläggande flöde {#basic-flow}

Följ instruktionerna nedan för att implementera aktivering av gästreservation för ditt AEM Screens-projekt:

1. **Fylla i Google-bladen och lägga till formeln**.

   Använd till exempel formeln på den tredje kolumnen **AdTarget**, vilket visas i figuren nedan.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Konfigurera segmenten i publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (se ***Steg 2: Konfigurera målgruppssegmentering*** in **[ContextHub konfigureras i AEM Screens](configuring-context-hub.md)** sida för mer information).
   1. Klicka på **Blad A1 1** och klicka **Redigera**.
   1. Klicka på jämförelseegenskapen och klicka på **Konfiguration** -ikon.
   1. Klicka **googlesheets/value/1/2** från listrutan i **Egenskapsnamn**.
   1. Klicka på **Operator** as **likhet** i listrutan.
   1. Ange **Värde** as **1**.
   1. På samma sätt klickar du på **Blad A1 2** och klicka **Redigera**.
   1. Klicka på jämförelseegenskapen och klicka på **Konfiguration** -ikon.
   1. Klicka **googlesheets/value/1/2** från listrutan i **Egenskapsnamn**.
   1. Klicka på **Operator** as **2**.

1. Navigera och klicka på kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel **DataDrivenRestaurant**, används en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   >
   >Din kanal bör redan ha en standardbild och publikerna bör vara förkonfigurerade enligt beskrivningen i [ContextHub konfigureras i AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Du borde ha konfigurerat **ContextHub** **Konfigurationer** använda kanalen **Egenskaper** > **Personalisering** -fliken.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Klicka **Målinriktning** från redigeraren och klicka på **Varumärke** och **Aktivitet** i listrutan och klicka på **Börja målinrikta**.
1. **Kontrollera förhandsvisningen**

   1. Klicka **Förhandsgranska.** Du kan även öppna dina Google-blad och uppdatera deras värde.
   1. Uppdatera värdet i **`Restaurant1`** och **`Restaurant2`** kolumner. If **`Restaurant1`** > **`Restaurant2`,** du bör kunna visa en bild av *Stopp* annan mat, *Thailändska* matbilden visas på skärmen.

   ![result5](assets/result5.gif)
