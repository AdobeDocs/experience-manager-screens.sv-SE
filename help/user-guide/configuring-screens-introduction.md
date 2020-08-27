---
title: Konfigurera och distribuera AEM Screens
seo-title: Konfigurera och distribuera skärmar
description: AEM Screens-spelaren är tillgänglig för Android, Chrome OS, iOS och Windows. Den här sidan beskriver konfiguration och distribution av AEM Screens och sammanfattar även riktlinjerna för maskinvaruval för spelarenhet.
seo-description: AEM Screens-spelaren är tillgänglig för Android, Chrome OS, iOS och Windows. Den här sidan beskriver konfiguration och distribution av AEM Screens och sammanfattar även riktlinjerna för maskinvaruval för spelarenhet.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: acc0278631a4be2c90de7cc43d3b40a358ffa93e
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---


# Konfigurera och distribuera AEM Screens {#configuring-and-deploying-aem-screens}

På den här sidan visas hur du installerar och konfigurerar skärmspelarna på dina enheter.

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**Viktigt**:
>
>AEM Screens Player använder inte CSRF-token (Cross-Site Request Forgery). Om du vill konfigurera och AEM servern som ska vara klar att användas för AEM Screens hoppar du över referensfiltret genom att tillåta tomma referenter.

## Hälsokontrollsramverk {#health-check-framework}

I hälsokontrollsramverket kan användaren kontrollera om två nödvändiga konfigurationer har ställts in innan ett AEM Screens-projekt körs.

Det gör att användaren kan verifiera följande två konfigurationskontroller för att köra ett AEM Screens-projekt, d.v.s. kontrollera statusen för följande två filter:

1. **Tillåt tom referens**
2. **https**

Följ stegen nedan för att kontrollera om dessa två viktiga konfigurationer är aktiverade för AEM Screens:

1. Gå till [Adobe Experience Manager Web Console Sling Health Check](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![resurser](assets/health-check1.png)


2. Klicka på **Kör markerade hälsokontroller** för att köra valideringen för två egenskaper som anges ovan.

   Om båda filtren är aktiverade visar hälsotjänsten **för** skärmkonfiguration **resultatet** som **OK** med båda konfigurationerna aktiverade.

   ![resurser](assets/health-check2.png)

   Om det ena eller båda filtren är inaktiverade visas en varning för användaren, vilket visas i bilden nedan.

   Följande varningsmeddelande visar om båda filtren är inaktiverade:
   ![resurser](assets/health-check3.png)

>[!NOTE]
>
>* Information om hur du aktiverar **referensfiltret** för Apache Sling finns i [Tillåt tomma referensförfrågningar](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Information om hur du aktiverar **HTTP** -tjänsten finns i [Apache Felix Jetty Based HTTP Service](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Förutsättningar {#prerequisites}

Följande huvudpunkter nedan hjälper dig att konfigurera och AEM servern som ska användas för AEM Screens.

#### Tillåt tomma referentförfrågningar {#allow-empty-referrer-requests}

1. Gå till **Adobe Experience Manager Web Console Configuration** via AEM:> hammer icon —> **Operations** —> **Web Console**.

   ![bild](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web Console Configuration** öppnas. Sök efter försäljningsreferent.

   Om du vill söka efter egenskapen för Sing-refereraren trycker du på **Command+F** för **Mac** och **Ctrl+F** för **Windows**.

1. Markera alternativet **Tillåt tomt** , så som visas i bilden nedan.

   ![bild](assets/config/empty-ref2.png)

1. Klicka på **Spara** för att aktivera Apache Sling Referer-filtret Tillåt tomt.


#### Apache Felix Jetty Based HTTP Service {#allow-apache-felix-service}

1. Gå till **Adobe Experience Manager Web Console Configuration** via AEM:> hammer icon —> **Operations** —> **Web Console**.

   ![bild](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web Console Configuration** öppnas. Sök efter Apache Felix Jetty Based HTTP Service.

   Om du vill söka efter den här egenskapen trycker du på **Command+F** för **Mac** och **Ctrl+F** för **Windows**.

1. Markera alternativet **AKTIVERA HTTP** enligt bilden nedan.

   ![bild](assets/config/config-1.png)

1. Klicka på **Spara** för att aktivera *http* -tjänsten.

#### Aktivera Touch UI för AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens kräver ett TOUCH-gränssnitt och fungerar inte med CLASSIC-gränssnittet i Adobe Experience Manager (AEM).

1. Navigera till *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Kontrollera att standardläget **för** redigeringsgränssnittet är inställt på **TOUCH**, vilket visas i figuren nedan

Du kan också göra samma inställning med *&lt;yourAuthorInstance>*->*tools (hammer icon)* -> **Operations** -> **Web Console** och söka efter **WCM-redigeringens användargränssnittstjänst**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Du kan alltid aktivera klassiskt gränssnitt för specifika användare med hjälp av användarinställningarna.

#### AEM i NOSAMPLECONTENT, körningsläge {#aem-in-nosamplecontent-runmode}

När du kör AEM i produktion används körningsläget **NOSAMPLECONTENT** . Ta *bort rubriken X-Frame-Options=SAMEORIGIN* (i det extra svarshuvudet) från

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Detta krävs för att AEM Screens Player ska kunna spela upp onlinekanaler.

#### Lösenordsbegränsningar {#password-restrictions}

Med de senaste ändringarna av ***DeviceServiceImpl*** behöver du inte ta bort lösenordsbegränsningarna.

Du kan konfigurera ***DeviceServiceImpl*** från länken nedan för att aktivera lösenordsbegränsning när du skapar lösenordet för skärmenhetsanvändare:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Följ stegen nedan för att konfigurera ***DeviceServiceImpl***:

1. Gå till **Adobe Experience Manager Web Console Configuration** via AEM:> hammer icon —> **Operations** —> **Web Console**.

1. **Adobe Experience Manager Web Console Configuration **öppnas. Sök efter enhetstjänst. Om du vill söka efter egenskapen trycker du på **Command+F** för **Mac** och **Ctrl+F** för **Windows**.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher-konfiguration {#dispatcher-configuration}

Mer information om hur du konfigurerar dispatcher för ett AEM Screens-projekt finns i [Konfigurera Dispatcher för ett AEM Screens-projekt](dispatcher-configurations-aem-screens.md).

#### Java-kodning {#java-encoding}

Ställ in Unicode för ***Java-kodning*** . Dfile. *encoding=Cp1252* fungerar till exempel inte.

>[!NOTE]
>
>**Rekommendation:**
>
>Du bör använda HTTPS för AEM Screens Server i produktionen.








