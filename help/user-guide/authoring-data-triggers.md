---
title: Skapa med Data Triggers
description: Läs mer om hur du skapar med datautlösare i en AEM Screens-kanal.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Skapa med Data Triggers {#authoring-with-data-triggers}

I det här avsnittet beskrivs hur du aktiverar målinriktning i dina kanaler.

>[!IMPORTANT]
>
>Den lägsta versionen som stöder datautlösare i en AEM Screens-kanal är AEM 6.5.3 Feature Pack 3.

## Förutsättningar {#prereqs}

Innan du följer stegen nedan för att aktivera målinriktning i kanaler bör du läsa om [Viktiga termer i Konfigurera i AEM Screens](configuring-context-hub.md) krävs för att förstå ContextHub och Target i AEM Screens.

>[!IMPORTANT]
>
>Vi rekommenderar att du förstår och konfigurerar ContextHub-konfigurationer innan du aktiverar anpassning i en AEM Screens-kanal.

Följ länkarna nedan för mer information:

1. **[Konfigurera datalagret](configuring-context-hub.md)**
1. **[Konfigurera målgruppssegmentering](configuring-context-hub.md)**

När du har slutfört de föregående stegen är du redo att aktivera målinriktning i dina kanaler.

## Redigering med Data Triggers - översikt {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Aktivera mål i en AEM Screens-kanal {#enabling-targeting}

Följ stegen nedan för att aktivera målinriktning i dina kanaler.

1. Navigera till någon av AEM Screens-kanalerna. I följande steg visas hur du aktiverar målinriktning genom att använda **DataDrivenRetail** *(sekvenskanal)* som har skapats i en AEM Screens-kanal.

1. Klicka på kanalen **DataDrivenRetail** och klicka **Egenskaper** i åtgärdsfältet.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Klicka på **Personalisering** så att du kan konfigurera ContextHub-konfigurationer och klicka på ContextHub- och Segments-sökvägen.

   1. Klicka på **ContextHub-sökväg** as **libs** > **inställningar** > **molninställningar** > **standard** > **ContextHub-konfigurationer** och klicka **Klicka**.

   1. Klicka på **Segmentsökväg** as **conf** > **`We.Retail`** > **inställningar** > **wcm** > **segment** och klicka **Klicka**.

   1. Klicka **Spara och stäng**.

   >[!NOTE]
   >
   >Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navigera och klicka på **DataDrivenRetail** från **DataDrivenAssets** > **Kanaler** och klicka **Redigera** i åtgärdsfältet. Dra och släpp resurserna i kanalredigeraren.

   >[!NOTE]
   >
   >Om du har konfigurerat allt korrekt visas **Målinriktning** i listrutan i redigeraren, vilket visas i bilden nedan.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Klicka **Målinriktning**.

1. Klicka **Varumärke** och **Aktivitet** i listrutan och klicka på **Börja målinrikta**.

### Läs mer: Exempel på användningsfall {#learn-more-example-use-cases}

När du har konfigurerat ContextHub för ditt AEM Screens-projekt kan du följa de olika användningsexemplen för att förstå hur datautlösande resurser spelar en viktig roll i olika branscher:

1. **[Målinställd aktivering för butikslager](retail-inventory-activation.md)**
1. **[Temperaturaktivering i resecentret](local-temperature-activation.md)**
1. **[Aktivering av hotellreservation](hospitality-reservation-activation.md)**
