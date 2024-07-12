---
title: Konfigurera och distribuera AEM Screens
description: AEM Screens Player finns för Android&trade;, Chrome OS, iOS och Windows. Lär dig mer om konfiguration och driftsättning av AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# Konfigurera och distribuera AEM Screens {#configuring-and-deploying-aem-screens}

På den här sidan visas hur du installerar och konfigurerar Screens-spelare på dina enheter.

## Serverkonfiguration {#server-configuration}

>[!IMPORTANT]
>
>AEM Screens Player använder inte CSRF-token (Cross-Site Request Forgery). Om du vill konfigurera AEM som ska användas för AEM Screens hoppar du över referensfiltret genom att tillåta tomma referenter.

## Hälsokontrollramverk {#health-check-framework}

Med Health Check Framework kan användaren kontrollera om två nödvändiga konfigurationer har konfigurerats innan ett AEM Screens-projekt körs.

Det gör att användaren kan verifiera följande två konfigurationskontroller för att köra ett AEM Screens-projekt, d.v.s. kontrollera statusen för följande två filter:

1. **Tillåt tom referent**
2. **https**

Följ stegen nedan för att kontrollera om dessa två viktiga konfigurationer är aktiverade för AEM Screens:

1. Navigera till [Hälsokontroll för Adobe Experience Manager Web Console-delning](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![resurser](assets/health-check1.png)


2. Klicka på **Kör de markerade hälsokontrollerna** så att du kan köra valideringen för två egenskaper som listas ovan.

   Om båda filtren är aktiverade visar **Screens Configuration Health Service** **Result** som **OK** med båda konfigurationerna aktiverade.

   ![resurser](assets/health-check2.png)

   Om det ena eller båda filtren är inaktiverade visas en varning för användaren, vilket visas i bilden nedan.

   Följande varningsmeddelande visar om båda filtren är inaktiverade:
   ![resurser](assets/health-check3.png)

>[!NOTE]
>
>* Information om hur du aktiverar **Refererarfiltret för Apache Sling** finns i [Tillåt tomma referentförfrågningar](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Information om hur du aktiverar tjänsten **HTTP** finns i [Apache Felix Jetty Based HTTP Service](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).

### Förutsättningar {#prerequisites}

Följande huvudpunkter nedan hjälper dig att konfigurera och AEM servern som ska användas för AEM Screens.

#### Tillåt tomma referentförfrågningar {#allow-empty-referrer-requests}

1. Navigera till **Adobe Experience Manager Web Console Configuration** genom AEM > hammikon > **Åtgärder** > **Webbkonsol**.

   ![bild](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web Console Configuration** öppnas. Sök efter försäljningsreferent.

   Om du vill söka efter egenskapen för snedbrytningsreferenten trycker du på **Kommando+F** för **Mac** och **Ctrl+F** för **Windows**.

1. Markera alternativet **Tillåt tomt** enligt bilden nedan.

   ![bild](assets/config/empty-ref2.png)

1. Klicka på **Spara** för att aktivera Apache Sling Referer-filtret Tillåt tomt.


#### Apache Felix Jetty Based HTTP Service {#allow-apache-felix-service}

1. Navigera till **Adobe Experience Manager Web Console Configuration** genom AEM > hammikon > **Åtgärder** > **Webbkonsol**.

   ![bild](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web Console Configuration** öppnas. Sök efter Apache Felix Jetty Based HTTP Service.

   Om du vill söka efter den här egenskapen trycker du på **Kommando+F** för **Mac** och **Ctrl+F** för **Windows**.

1. Markera alternativet **AKTIVERA HTTP**, vilket visas i bilden nedan.

   ![bild](assets/config/config-1.png)

1. Klicka på **Spara** för att aktivera tjänsten *http*.

#### Aktivera Touch UI för AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens kräver ett TOUCH-användargränssnitt och fungerar inte med det klassiska användargränssnittet i Adobe Experience Manager (AEM).

1. Navigera till `*<yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*`
1. Kontrollera att standardläget för **redigeringsgränssnittet** är inställt på **TOUCH**, vilket visas i figuren nedan

Du kan också göra samma inställning med hjälp av verktygen *>* (hammikonen) > **Åtgärder** > **Webbkonsol** och söka efter **tjänsten för användargränssnittsläge för WCM-redigering**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Du kan alltid aktivera klassiskt gränssnitt för specifika användare med hjälp av användarinställningarna.

#### AEM i NOSAMPLECONTENT-körningsläge {#aem-in-nosamplecontent-runmode}

När du kör AEM i produktion används körningsläget **NOSAMPLECONTENT** . Ta bort rubriken *X-Frame-Options=SAMEORIGIN* (i det extra svarshuvudet) från

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Den här borttagningen krävs för att AEM Screens Player ska kunna spela upp onlinekanaler.

#### Lösenordsbegränsningar {#password-restrictions}

Med de senaste ändringarna av ***DeviceServiceImpl*** behöver du inte ta bort lösenordsbegränsningarna.

Du kan konfigurera ***DeviceServiceImpl*** från länken nedan för att aktivera lösenordsbegränsning när du skapar lösenordet för skärmenhetsanvändarna:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Följ stegen nedan för att konfigurera ***DeviceServiceImpl***:

1. Navigera till **Adobe Experience Manager Web Console Configuration** via din AEM > hammikon > **Åtgärder** > **Webbkonsol**.

1. **Adobe Experience Manager Web Console Configuration** öppnas. Sök efter `*deviceservice*`. Om du vill söka efter egenskapen trycker du på **Kommando+F** för macOS och **Ctrl+F** för Microsoft® Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

Mer information om hur du konfigurerar Dispatcher för ett AEM Screens-projekt finns i [Konfigurera Dispatcher för ett AEM Screens-projekt](dispatcher-configurations-aem-screens.md).

#### Java™-kodning {#java-encoding}

Ställ in Unicode för ***Java™-kodningen***. `*Dfile.encoding=Cp1252*` fungerar till exempel inte.

>[!NOTE]
>
>Använd HTTPS för AEM Screens Server i produktion.
