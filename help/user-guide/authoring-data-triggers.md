---
title: Skapa med Data Triggers
seo-title: Skapa med Data Triggers
description: Följ den här sidan för att lära dig hur du skapar med datautlösare.
feature: Redigeringsskärmar
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Skapa med Data Triggers {#authoring-with-data-triggers}

I det här avsnittet beskrivs hur du aktiverar målinriktning i dina kanaler.

>[!IMPORTANT]
>
>Den lägsta versionen som stöder datautlösare i en AEM Screens-kanal är AEM 6.5.3 Feature Pack 3.

## Förutsättningar {#prereqs}

Innan du följer stegen nedan för att aktivera mål i kanaler måste du lära dig de [nyckeltermer i Konfigurera i AEM Screens](configuring-context-hub.md) som krävs för att förstå ContextHub och Target i AEM Screens.

>[!IMPORTANT]
>
>Vi rekommenderar att du förstår och konfigurerar ContextHub-konfigurationer innan du aktiverar målinriktning i en AEM Screens-kanal.

Följ länkarna nedan för mer information:

1. **[Konfigurera datalager](configuring-context-hub.md)**
1. **[Konfigurera målgruppssegmentering](configuring-context-hub.md)**

När du har slutfört de föregående stegen är du redo att aktivera målinriktning i dina kanaler.

## Redigering med Data Triggers - översikt {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Aktivera mål i en AEM Screens-kanal {#enabling-targeting}

Följ stegen nedan för att aktivera målinriktning i dina kanaler.

1. Navigera till en av AEM Screens-kanalerna. Följande steg visar hur du aktiverar mål genom att använda **DataDrivenRetail** *(sekvenskanal)* som skapats i en AEM Screens-kanal.

1. Markera kanalen **DataDrivenRetail** och klicka på **Egenskaper** i åtgärdsfältet.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Välj fliken **Personalisering** för att konfigurera ContextHub-konfigurationer och välj ContextHub- och Segments-sökvägen.

   1. Välj **ContextHub-sökvägen** som **libs** > **inställningar** > **molninställningar** > **standard** > **ContextHub Configurations** och klicka på &lt;a 12/>Välj **.**

   1. Välj **Segmentsökväg** som **conf** > **We.Retail** > **inställningar** > **wcm** > **segment** och klicka på **Markera&lt;a1 3/>.**

   1. Klicka på **Spara och stäng**.
   >[!NOTE]
   >
   >Använd ContextHub och Segments-sökvägen, där du först sparade dina kontextnavkonfigurationer och segment.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navigera och välj **DataDrivenRetail** från **DataDrivenAssets** > **Kanaler** och klicka på **Redigera** i åtgärdsfältet. Dra och släpp resurserna i kanalredigeraren.

   >[!NOTE]
   >
   >Om du har konfigurerat allt korrekt visas alternativet **Målinriktning** i listrutan från redigeraren, vilket visas i bilden nedan.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Klicka på **Mål**.

1. Välj **Varumärke** och **Aktivitet** i listrutan och klicka på **Starta målgruppsanpassning**.

### Läs mer: Exempel på användningsfall {#learn-more-example-use-cases}

När du har konfigurerat ContextHub för ditt AEM Screens-projekt kan du följa de olika användningsexemplen för att förstå hur datautlösande resurser spelar en viktig roll i olika branscher:

1. **[Målinställd aktivering för butikslager](retail-inventory-activation.md)**
1. **[Temperaturaktivering i resecentret](local-temperature-activation.md)**
1. **[Aktivering av hotellreservation](hospitality-reservation-activation.md)**
