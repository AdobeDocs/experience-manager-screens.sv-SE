---
title: Temperaturaktivering i resecentret
description: Läs om hur det här användningsexemplet visar hur man använder lokal temperaturaktivering i resecentret baserat på värdena i Google Sheets.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# Temperaturaktivering i resecentret {#travel-center-temperature-activation}

I följande exempel visas användningen av lokal temperaturaktivering i resecentret baserat på de värden som anges i Google Sheets.

## Beskrivning {#description}

Om värdet i Google Sheets är mindre än 50 visas i det här fallet en bild med varma drycker. Om värdet är större än eller lika med 50 visas en bild med kalla drycker. Om det finns något annat värde eller inget värde alls visas en standardbild.

## Förhandsvillkor {#preconditions}

Innan du börjar implementera aktiveringen av lokal temperatur i resecentret bör du lära dig hur du konfigurerar ***datalagret***, ***målgruppssegmentering*** och ***Aktivera målanpassning för kanaler*** i ett AEM Screens-projekt.

Mer information finns i [Konfigurera ContextHub i AEM Screens](configuring-context-hub.md).

## Grundläggande flöde {#basic-flow}

Följ stegen nedan för att implementera användningsexemplet för aktivering av lokal temperatur i Travel Center:

1. **Fylla i Google-blad**

   1. Navigera till ContextHubDemo Google Sheet.
   1. Lägg till en kolumn med **`Heading1`** med motsvarande värde för temperatur.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Konfigurera segmenten i Publiker enligt kraven**

   1. Navigera till segmenten i målgruppen (mer information finns i ***Steg 2: Konfigurera målgruppssegmentering*** i **[Konfigurera ContextHub på AEM Screens](configuring-context-hub.md)** -sidan).

   1. Klicka på **Blad A1** och klicka på **Redigera**.

   1. Klicka på jämförelseegenskapen och klicka på konfigurationsikonen.
   1. Klicka på **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**

   1. Klicka på **Operator** som **större än eller lika med** i listrutan

   1. Ange **Value** som **50**

   1. På samma sätt markerar du **Sheets A1 2** och klickar på **Redigera**.

   1. Klicka på **jämförelseegenskapen - värde** och välj konfigurationsikonen.
   1. Klicka på **Googlesheets/value/1/0** i listrutan i **Egenskapsnamn**

   1. Klicka på **Operator** som **mindre än** i listrutan

   1. Ange **Value** som **50**

1. Navigera och markera kanalen () och klicka på **Redigera** i åtgärdsfältet. I följande exempel, **DataDrivenWeather**, används en sekventiell kanal för att visa funktionaliteten.

   >[!NOTE]
   >
   >Din kanal bör redan ha en standardbild och publikationerna bör vara förkonfigurerade enligt beskrivningen i [Konfigurera ContextHub i AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Din **ContextHub** **Configurations** som använder fliken **Egenskaper** > **Personalization** i kanalen bör redan vara konfigurerad.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Klicka på **Riktning** i redigeraren och klicka på **Varumärke** och **Aktivitet** i listrutan och klicka sedan på **Start Targeting**.

   ![new_activity3](assets/new_activity3.gif)

1. **Kontrollerar förhandsvisningen**

   1. Klicka på **Förhandsgranska.** Öppna även Google-bladet och uppdatera värdet.
   1. Ändra värdet till mindre än 50. Du kan se en bild på en kalldryck. Om värdet i Google Sheets är 50 eller högre bör du se en bild på en het drink.

   ![result3](assets/result3.gif)
