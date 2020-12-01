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
source-git-commit: 83ce95e5dc530c5792ec9a00dcb758a424202a7a
workflow-type: tm+mt
source-wordcount: '752'
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

## Hälsokontrollramverk {#health-check-framework}

I hälsokontrollsramverket kan användaren kontrollera om två nödvändiga konfigurationer har ställts in innan ett AEM Screens-projekt körs.

Det gör att användaren kan verifiera följande två konfigurationskontroller för att köra ett AEM Screens-projekt, d.v.s. kontrollera statusen för följande två filter:

1. **Tillåt tom referens**
2. **https**

Följ stegen nedan för att kontrollera om dessa två viktiga konfigurationer är aktiverade för AEM Screens:

1. Navigera till [Hälsokontroll för Adobe Experience Manager Web Console Sling](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![resurser](assets/health-check1.png)


2. Klicka på **Kör markerade hälsokontroller** för att köra valideringen för två egenskaper som listas ovan.

   Om båda filtren är aktiverade visar **Hälsotjänsten för skärmkonfiguration** **Resultat** som **OK** med båda konfigurationerna aktiverade.

   ![resurser](assets/health-check2.png)

   Om det ena eller båda filtren är inaktiverade visas en varning för användaren, vilket visas i bilden nedan.

   Följande varningsmeddelande visar om båda filtren är inaktiverade:
   ![resurser](assets/health-check3.png)

>[!NOTE]
>
>* Om du vill aktivera **Refererarfiltret för Apache Sling** går du till [Tillåt tomma referentförfrågningar](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Om du vill aktivera tjänsten **HTTP** läser du [Apache Felix Jetty Based HTTP Service](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Förutsättningar {#prerequisites}

Följande huvudpunkter nedan hjälper dig att konfigurera och AEM servern som ska användas för AEM Screens.

#### Tillåt tomma referentförfrågningar {#allow-empty-referrer-requests}

1. Navigera till **Adobe Experience Manager Web Console Configuration** via AEM:> hammer icon —> **Åtgärder** —> **Webbkonsol**.

   ![bild](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web Console-** konfigurationöppnas. Sök efter försäljningsreferent.

   Om du vill söka efter egenskapen för snedbrytningsreferenten trycker du på **Command+F** för **Mac** och **Ctrl+F** för **Windows**.

1. Markera alternativet **Tillåt tomt** enligt bilden nedan.

   ![bild](assets/config/empty-ref2.png)

1. Klicka på **Spara** för att aktivera Apache Sling Referer-filtret Tillåt tomt.


#### Apache Felix Jetty Based HTTP Service {#allow-apache-felix-service}

1. Navigera till **Adobe Experience Manager Web Console Configuration** via AEM:> hammer icon —> **Åtgärder** —> **Webbkonsol**.

   ![bild](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web Console-** konfigurationöppnas. Sök efter Apache Felix Jetty Based HTTP Service.

   Om du vill söka efter den här egenskapen trycker du på **Command+F** för **Mac** och **Ctrl+F** för **Windows**.

1. Markera alternativet **AKTIVERA HTTP** enligt bilden nedan.

   ![bild](assets/config/config-1.png)

1. Klicka på **Spara** för att aktivera tjänsten *http*.

#### Aktivera Touch UI för AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens kräver ett TOUCH-gränssnitt och fungerar inte med CLASSIC-gränssnittet i Adobe Experience Manager (AEM).

1. Navigera till *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Kontrollera att standardläget för redigering **är inställt på** TOUCH **, vilket visas i figuren nedan**

Du kan också utföra samma inställning med hjälp av verktygen för din författarinstans *->* (hammikon) -> **Åtgärder** -> **Webbkonsol** och söka efter **tjänsten för WCM-redigeringsläge**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Du kan alltid aktivera klassiskt gränssnitt för specifika användare med hjälp av användarinställningarna.

#### AEM i NOSAMPLECONTENT-körningsläge {#aem-in-nosamplecontent-runmode}

När du kör AEM i produktion används körningsläget **NOSAMPLECONTENT**. Ta bort rubriken *X-Frame-Options=SAMEORIGIN* (i det extra svarshuvudet) från

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Detta krävs för att AEM Screens Player ska kunna spela upp onlinekanaler.

#### Lösenordsbegränsningar {#password-restrictions}

Med de senaste ändringarna av ***DeviceServiceImpl*** behöver du inte ta bort lösenordsbegränsningarna.

Du kan konfigurera ***DeviceServiceImpl*** från länken nedan för att aktivera lösenordsbegränsning när du skapar lösenordet för skärmenhetsanvändarna:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Följ stegen nedan för att konfigurera ***DeviceServiceImpl***:

1. Navigera till **Adobe Experience Manager Web Console Configuration** via AEM:> hammer icon —> **Åtgärder** —> **Webbkonsol**.

1. **Adobe Experience Manager Web Console-** konfigurationöppnas. Sök efter *enhetstjänst*. Om du vill söka efter egenskapen trycker du på **Command+F** för macOS och **Ctrl+F** för Microsoft Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher-konfiguration {#dispatcher-configuration}

Mer information om hur du konfigurerar dispatcher för ett AEM Screens-projekt finns i [Konfigurera Dispatcher för ett AEM Screens-projekt](dispatcher-configurations-aem-screens.md).

#### Java-kodning {#java-encoding}

Ställ in Unicode för ***Java-kodning***. Exempelvis fungerar inte *Dfile.encoding=Cp1252*.

>[!NOTE]
>**Rekommendation:**
>Du bör använda HTTPS för AEM Screens Server i produktionen.








