---
title: Enhetsregistrering
seo-title: Enhetsregistrering
description: Den här sidan beskriver enhetsregistreringsprocessen i ett AEM Screens-projekt.
seo-description: Den här sidan beskriver enhetsregistreringsprocessen i ett AEM Screens-projekt.
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Enhetsregistrering {#device-registration}

Följande sida beskriver enhetsregistreringsprocessen i ett AEM Screens-projekt.

## Registrera en enhet {#registering-a-device}

Enhetsregistreringsprocessen görs på två olika datorer:

* Den faktiska enhet som ska registreras, till exempel din skyltskärm
* Den AEM-server som används för att registrera din enhet

>[!NOTE]
>
>När du har laddat ned den senaste versionen av Windows Player (*.exe*) från [AEM 6.4 Player Downloads](https://download.macromedia.com/screens/) följer du stegen på spelaren för att slutföra ad hoc-installationen:
>
>1. Tryck länge på det övre vänstra hörnet för att öppna administrationspanelen.
>1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn, ange platsadressen för AEM-instansen i **Server** och klicka på **Spara**.
>1. Klicka på länken **Registrering** i den vänstra åtgärdsmenyn och på stegen nedan för att slutföra enhetsregistreringsprocessen.
>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Starta AEM Screens Player på enheten. Registreringsgränssnittet visas.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. I AEM navigerar du till mappen **Devices** i ditt projekt.

   >[!NOTE]
   >
   >Mer information om hur du skapar ett nytt projekt för skärmar på AEM-kontrollpanelen finns i [Skapa och hantera skärmsprojekt](creating-a-screens-project.md).

1. Tryck/klicka på knappen **Enhetshanteraren** i åtgärdsfältet.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Tryck/klicka på knappen **Enhetsregistrering** längst upp till höger.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Välj önskad enhet (samma som steg 1) och tryck/klicka på **Registrera enhet**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. I AEM väntar du tills enheten skickar sin registreringskod.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Kontrollera **registreringskoden** på enheten.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Om **registreringskoden** är densamma på båda datorerna trycker/klickar du på knappen **Validera** i AEM, vilket visas i steg 6.
1. Ange önskat namn för enheten och klicka på **Registrera**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Tryck/klicka på **Slutför** för att slutföra registreringsprocessen.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >Med **Registrera nytt** kan du registrera en ny enhet.
   >
   >Med **Tilldela skärm** kan du lägga till enheten direkt på en skärm.

   Om du klickar på **Slutför** måste du tilldela enheten till en skärm.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar och hanterar en visning för ditt skärmsprojekt finns i [Skapa och hantera skärmar](managing-displays.md).

### Tilldela enhet till en skärm {#assigning-device-to-a-display}

Om du inte har tilldelat enheten till en skärm följer du stegen nedan för att tilldela enheten till en skärm i ditt AEM Screens-projekt:

1. Markera enheten och klicka på **Tilldela enhet** i åtgärdsfältet.

   ![screen_shot_2018-11-26at11026am](assets/screen_shot_2018-11-26at111026am.png)

1. Välj sökvägen för visningen i **Visnings-/enhetskonfigurationssökväg**.

   ![screen_shot_2018-11-26at11252am](assets/screen_shot_2018-11-26at111252am.png)

1. Klicka på **Tilldela** när du markerar banan.

   ![screen_shot_2018-11-26at11722am](assets/screen_shot_2018-11-26at111722am.png)

1. Klicka på **Slutför** när enheten har tilldelats korrekt enligt bilden nedan.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Dessutom kan du visa kontrollpanelen när du klickar på **Slutför**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Begränsningar för enhetsregistrering {#limitations-on-device-registration}

Användarlösenordsbegränsningar för hela systemet kan orsaka fel i enhetsregistreringen. Enhetsregistreringen använder ett slumpmässigt genererat lösenord för att skapa enhetsanvändaren.

Om lösenordet begränsas av *AuthorizableActionProvider* -konfigurationen kan det hända att det inte går att skapa enhetsanvändaren.

>[!NOTE]
>
>Det aktuella genererade slumpmässiga lösenordet består av 36 ASCII-tecken, mellan 33 och 122 (innehåller nästan alla specialtecken).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Additional Resources {#additional-resources}

Mer information om AEM Screens Player finns i [AEM Screens Player](working-with-screens-player.md).