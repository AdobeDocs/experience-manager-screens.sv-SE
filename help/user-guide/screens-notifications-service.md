---
title: AEM Screens Notifications Service
description: Läs mer om hur du kan övervaka enhetsaktiviteter för AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# AEM Screens Notifications Service{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens Notifications Service*** beskriver aktiviteten för bildskärmsenheter.

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Konfigurerar e-postinställningar**
* **E-postmeddelande**
* **Exempel på användningsfall**

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. -->

## Ökning {#overview}

Med ***AEM Screens Notifications Service*** kan administratörer få ett e-postmeddelande om en AEM Screens Player inte pingar under en konfigurerbar tid.

Tjänsten kan konfigureras i OSGi-webbkonsolen.

## Konfigurerar e-postinställningar {#configuring-email-settings}

Följ stegen nedan för att konfigurera inställningarna för e-postmeddelanden:

1. Öppna **Adobe Experience Manager Web Console Configuration**.
1. Öppna **E-postövervakningstjänsten för Screens-enheter**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Definiera följande fält så att du kan konfigurera inställningarna för e-postmeddelandet:

   **Enhetssökväg** Ange sökvägen till de Screens-projekt som du vill övervaka. Sökvägen är vanligtvis `/home/users/screens/<Name of your project>`.

   Om ditt projekt till exempel är **`We.Retail`** använder du projektsökvägen som ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Ange projektsökvägen där enhetsanvändarna finns.

   **Schemaläggningsfrekvens** - Ange en tid (t.ex. 5:00 P.M. eller 17:00) eller frekvens i timmar (t.ex. 1) som den här övervakaren ska skicka e-post med.

   **Ping Time out** - Det här fältet anger intervallet i minuter efter vilket en enhet inte kan nås.

   **SMTP-server** - Anger SMTP-servern som används för att skicka e-post.

   **SMTP-port** - Ange SMTP-porten.

   **Använd TLS** - TLS (Transport Layer Security) gör att du kan använda säker kommunikation med SMTP-servern.

   Adobe rekommenderar att du använder TLS för säker anslutning till företagets e-postservrar. Fråga e-postadministratören om lämpliga värden.

   **användarnamn** - Ange användarnamn för att skicka e-post.

   **password** - Ange lösenordet för att skicka e-post.

   **Mottagare** - Ange mottagarens e-postadress.

   >[!NOTE]
   >
   >Du kan bara ange en e-postadress. Om du vill skicka ett större e-postmeddelande skapar du en grupp eller distributionslista med de relevanta användarna.

1. Klicka på **Spara** för att konfigurera övervakningsaktiviteten via ett e-postmeddelande för din AEM Screens-enhet.

## E-postmeddelande {#email-notification}

När du har angett konfigurationen för dina e-postmeddelanden får du ett e-postmeddelande som innehåller länken till den faktiska enheten som rapporteras om inaktivitet.

Om du får åtkomst till den länken navigerar du direkt till enhetens kontrollpanel.

E-post skickas endast om:

* det finns minst en enhet som inte har pingats för den angivna pingtidsgränsen, och
* är fortfarande inte pingande när e-postmeddelandet genereras.

### Exempel på användningsfall {#example-use-cases}

I följande exempel beskrivs några referensscenarier för att konfigurera egenskaperna från Screens E-postövervakningstjänst för enheter.

**Scenario 1**

Du ställer in schemafrekvensen till 1:00 och pingtidsgränsen till 60. Om din AEM Screens-enhet inte växlar mellan kl. 12.00 till kl. 13.00 får du ett e-postmeddelande som bekräftar inaktivitet i enheten.

**Scenario 2**

Du ställer in schemafrekvensen till 1 och pingtidsgränsen till 60. Om din AEM Screens-enhet inte pingar samtidigt vid en viss tidpunkt på dagen får du ett e-postmeddelande som bekräftar att enheten är inaktiv.
