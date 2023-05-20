---
title: AEM Screens Notifications Service
seo-title: AEM Screens Notifications Service
description: Följ den här sidan om du vill veta mer om hur du kan övervaka enhetsaktivitet.
seo-description: Follow this page to learn more about how you can monitor device activity.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# AEM Screens Notifications Service{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens Notifications Service***, beskriver funktionen där du kan övervaka enhetsaktivitet.

Detta avsnitt behandlar följande ämnen:

* **Översikt**
* **Konfigurerar e-postinställningar**
* **E-postmeddelande**
* **Exempel på användningsfall**

>[!CAUTION]
>
>Denna AEM Screens-funktionalitet är endast tillgänglig om du har installerat AEM 6.3.2 Feature Pack 3 eller AEM 6.4.1 Screens Feature Pack 1.
>
>Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobe Support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

## Översikt {#overview}

***AEM Screens Notifications Service***, gör att administratörer kan ta emot ett e-postmeddelande om en AEM inte pingar under en konfigurerbar tidsperiod.

Den här tjänsten kan konfigureras i OSGi-webbkonsolen.

## Konfigurerar e-postinställningar {#configuring-email-settings}

Följ stegen nedan för att konfigurera inställningarna för e-postmeddelanden:

1. Öppna **Konfiguration av Adobe Experience Manager Web Console**.
1. Öppna **E-postövervakningstjänst för skärmar**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Definiera följande fält för att konfigurera inställningarna för e-postmeddelandet:

   **Sökväg till enheter** Ange sökvägen till de skärmprojekt som du vill övervaka. Banan är vanligtvis `/home/users/screens/<Name of your project>`.

   Om ditt projekt till exempel är **Vi.butik** använder du projektsökvägen som ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Ange projektsökvägen där enhetsanvändarna finns.

   **Schemaläggningsfrekvens** Ange en tid (t.ex. 17:00 eller 17:00) eller frekvens i timmar (t.ex. 1) som den här övervakaren ska skicka e-post med.

   **Ping-timeout** Detta anger intervallet i minuter efter vilket en enhet inte kan nås.

   **SMTP-server** Anger den SMTP-server som används för att skicka e-post.

   **SMTP-port** Ange SMTP-porten.

   **Använd TLS** TLS (Transport Layer Security) gör att du kan använda säker kommunikation med SMTP-servern.

   TLS rekommenderas för säker anslutning till företagets e-postservrar. Kontrollera med e-postadministratören om du har rätt värden.

   **användarnamn** Ange användarnamn för att skicka e-post.

   **lösenord** Ange lösenordet för att skicka e-post.

   **Mottagare** Ange mottagarens e-postadress.

   >[!NOTE]
   >
   >Du kan bara ange en e-postadress. Skapa en grupp eller distributionslista med de relevanta användarna för att kunna skicka ett större e-postmeddelande.

1. Klicka **Spara** för att konfigurera övervakningsaktiviteten via ett e-postmeddelande för din AEM Screens-enhet.

## E-postmeddelande {#email-notification}

När du har angett konfigurationen för dina e-postmeddelanden får du ett e-postmeddelande som innehåller länken till den faktiska enheten som rapporteras om inaktivitet.

Om du får åtkomst till den länken kommer du direkt till kontrollpanelen för enheten.

E-postmeddelanden skickas endast om det finns minst en enhet som inte har pingats för den angivna pingtidsgränsen och som fortfarande inte pingas när e-postmeddelandet genereras.

### Exempel på användningsfall {#example-use-cases}

I följande exempel beskrivs ett fåtal referensscenarier för att konfigurera egenskaperna från E-postövervakningstjänsten för skärmar.

**Scenario 1**:

Om du ställer in schemafrekvensen till 1:00 och pingtidsgränsen till 60 får du ett e-postmeddelande som bekräftar inaktivitet på enheten om skärmarna inte växlar mellan 12:00 och 13:00.

**Scenario 2**:

Om du ställer in schemafrekvensen till 1 och ping-tidsgränsen till 60, kommer du att få ett e-postmeddelande som bekräftar enhetens inaktivitet om skärmenheten inte växlar mellan en gång vid en viss tidpunkt på dagen.
