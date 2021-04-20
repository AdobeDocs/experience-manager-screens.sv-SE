---
title: AEM Screens Notifications Service
seo-title: AEM Screens Notifications Service
description: Följ den här sidan om du vill veta mer om hur du kan övervaka enhetsaktivitet.
seo-description: Följ den här sidan om du vill veta mer om hur du kan övervaka enhetsaktivitet.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# AEM Screens Notifications Service{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens Notifications Service*** beskriver funktionen där du kan övervaka enhetsaktivitet.

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

***Med AEM Screens Notifications Service*** kan administratörer få ett e-postmeddelande om en AEM inte pingar under en konfigurerbar tidsperiod.

Den här tjänsten kan konfigureras i OSGi-webbkonsolen.

## Konfigurerar e-postinställningar {#configuring-email-settings}

Följ stegen nedan för att konfigurera inställningarna för e-postmeddelanden:

1. Öppna **Adobe Experience Manager Web Console Configuration**.
1. Öppna **E-postövervakningstjänsten för skärmar**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Definiera följande fält för att konfigurera inställningarna för e-postmeddelandet:

   **Enheter** PathAnge sökvägen till skärmsprojekt som du vill övervaka. Sökvägen är vanligtvis `/home/users/screens/<Name of your project>`.

   Om ditt projekt till exempel är **We.Retail** använder du projektsökvägen som ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Ange projektsökvägen där enhetsanvändarna finns.

   **Schemalägg** frekvensAnge en tid (t.ex. klockan 17:00 eller 17:00) eller frekvens i timmar (t.ex. 1) som den här övervakaren ska skicka e-post med.

   **Ping-** timeoutDetta anger intervallet i minuter efter vilket en enhet inte kan nås.

   **SMTP-** server Anger SMTP-servern som används för att skicka e-post.

   **SMTP-** portAnge SMTP-porten.

   **Med TLS (** TLSTransport Layer Security) kan du använda säker kommunikation med SMTP-servern.

   TLS rekommenderas för säker anslutning till företagets e-postservrar. Kontrollera med e-postadministratören om du har rätt värden.

   **** användarnamnAnge användarnamn för att skicka e-post.

   **** lösenordAnge lösenordet för att skicka e-post.

   **Mottagare** Ange mottagarens e-postadress.

   >[!NOTE]
   >
   >Du kan bara ange en e-postadress. Skapa en grupp eller distributionslista med de relevanta användarna för att kunna skicka ett större e-postmeddelande.

1. Klicka på **Spara** för att konfigurera övervakningsaktiviteten via ett e-postmeddelande för din AEM Screens-enhet.

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
