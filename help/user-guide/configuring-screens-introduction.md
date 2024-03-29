---
title: Konfigurera och distribuera AEM Screens
seo-title: Configuring and Deploying Screens
description: AEM Screens Player finns för Android, Chrome OS, iOS och Windows. Den här sidan beskriver konfiguration och distribution av AEM Screens och sammanfattar även riktlinjerna för maskinvaruval för spelarenhet.
seo-description: The AEM Screens player is available for Android, Chrome OS, iOS, and Windows. This page describes the configuration and deployment of AEM Screens and also summarizes the h/w selection guidelines for player device.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 0%

---

# Konfigurera och distribuera AEM Screens {#configuring-and-deploying-aem-screens}

På den här sidan visas hur du installerar och konfigurerar skärmspelarna på dina enheter.

## Serverkonfiguration {#server-configuration}

>[!NOTE]
>
>**Viktigt**:
>
>AEM Screens Player använder inte CSRF-token (Cross-Site Request Forgery). Om du vill konfigurera och AEM servern som ska vara klar att användas för AEM Screens hoppar du över referensfiltret genom att tillåta tomma referenter.

## Hälsokontrollsramverk {#health-check-framework}

I hälsokontrollsramverket kan användaren kontrollera om två nödvändiga konfigurationer har ställts in innan ett AEM Screens-projekt körs.

Det gör det möjligt för användaren att verifiera följande två konfigurationskontroller för att köra ett AEM Screens-projekt, det vill säga för att kontrollera statusen för följande två filter:

1. **Tillåt tom referens**
2. **https**

Följ stegen nedan för att kontrollera om dessa två viktiga konfigurationer är aktiverade för AEM Screens:

1. Navigera till [Hälsokontroll för Adobe Experience Manager Web Console Sling](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![resurser](assets/health-check1.png)


2. Klicka på **Utför valda hälsokontroller** för att köra valideringen för två egenskaper som anges ovan.

   Om båda filtren är aktiverade visas **Hälsotjänst för skärmkonfiguration** visar **Resultat** as **OK** med båda konfigurationerna aktiverade.

   ![resurser](assets/health-check2.png)

   Om det ena eller båda filtren är inaktiverade visas en varning för användaren, vilket visas i bilden nedan.

   Följande varningsmeddelande visar om båda filtren är inaktiverade:
   ![resurser](assets/health-check3.png)

>[!NOTE]
>
>* Aktivera **Apache Sling Referer-filter**, se [Tillåt tomma referentförfrågningar](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Aktivera **HTTP** tjänst, se [Apache Felix Jetty Based HTTP Service](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Förutsättningar {#prerequisites}

Följande huvudpunkter nedan hjälper dig att konfigurera och AEM servern som ska användas för AEM Screens.

#### Tillåt tomma referentförfrågningar {#allow-empty-referrer-requests}

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console** via AEM instance —> hammer icon —> **Operationer** —> **Webbkonsol**.

   ![bild](assets/config/empty-ref1.png)

1. **Konfiguration av Adobe Experience Manager Web Console** öppnas. Sök efter försäljningsreferent.

   Om du vill söka efter egenskapen för Sing-refereraren trycker du på **Kommando+F** for **Mac** och **Ctrl+F** for **Windows**.

1. Kontrollera **Tillåt tomt** som i bilden nedan.

   ![bild](assets/config/empty-ref2.png)

1. Klicka **Spara** om du vill aktivera referensfiltret för Apache Sling Tillåt tomt.


#### Apache Felix Jetty Based HTTP Service {#allow-apache-felix-service}

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console** via AEM instance —> hammer icon —> **Operationer** —> **Webbkonsol**.

   ![bild](assets/config/empty-ref1.png)

1. **Konfiguration av Adobe Experience Manager Web Console** öppnas. Sök efter Apache Felix Jetty Based HTTP Service.

   Om du vill söka efter den här egenskapen trycker du på **Kommando+F** for **Mac** och **Ctrl+F** for **Windows**.

1. Kontrollera **AKTIVERA HTTP** som i bilden nedan.

   ![bild](assets/config/config-1.png)

1. Klicka **Spara** för att aktivera *http* service.

#### Aktivera Touch UI för AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens kräver ett TOUCH-gränssnitt och fungerar inte med CLASSIC-gränssnittet i Adobe Experience Manager (AEM).

1. Navigera till *&lt;yourauthorinstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Se till att **Standardläge för användargränssnitt för redigering** är inställd på **TOUCH**, vilket visas i figuren nedan

Du kan också göra samma inställning med din AuthorInstance *->* verktyg (hammarikon) -> **Operationer** -> **Webbkonsol** och söka efter **Tjänsten WCM för användargränssnittsläge vid redigering**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Du kan alltid aktivera klassiskt gränssnitt för specifika användare med hjälp av användarinställningarna.

#### AEM i NOSAMPLECONTENT, körningsläge {#aem-in-nosamplecontent-runmode}

För AEM i produktion används **NOSAMPLECONTENT** runmode. Ta bort *X-frame-options=SAMEORIGIN* rubrik (i det extra svarshuvudet) från

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Detta krävs för att AEM Screens Player ska kunna spela upp onlinekanaler.

#### Lösenordsbegränsningar {#password-restrictions}

Med de senaste ändringarna i ***DeviceServiceImpl*** behöver du inte ta bort lösenordsbegränsningarna.

Du kan konfigurera ***DeviceServiceImpl*** via länken nedan om du vill aktivera lösenordsbegränsning när du skapar lösenordet för skärmenhetsanvändare:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Följ stegen nedan för att konfigurera ***DeviceServiceImpl***:

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console** via AEM instance —> hammer icon —> **Operationer** —> **Webbkonsol**.

1. **Konfiguration av Adobe Experience Manager Web Console** öppnas. Sök efter *devicesservice*. Om du vill söka efter egenskapen trycker du på **Kommando+F** för macOS och **Ctrl+F** för Microsoft Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher-konfiguration {#dispatcher-configuration}

Mer information om hur du konfigurerar dispatcher för ett AEM Screens-projekt finns i [Konfigurera Dispatcher för ett AEM Screens-projekt](dispatcher-configurations-aem-screens.md).

#### Java-kodning {#java-encoding}

Ange ***Java-kodning*** till Unicode. Till exempel: *Dfile.encoding=Cp1252* kommer inte att fungera.

>[!NOTE]
>**Rekommendation:**
>Du bör använda HTTPS för AEM Screens Server i produktionen.
