---
title: Enhetsregistrering
seo-title: Enhetsregistrering
description: På den här sidan beskrivs enhetsregistreringsprocessen i ett AEM Screens-projekt.
seo-description: På den här sidan beskrivs enhetsregistreringsprocessen i ett AEM Screens-projekt.
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
feature: Administrera skärmar, Device Registration
role: Administratör
level: Mellanliggande
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---


# Enhetsregistrering {#device-registration}

På följande sida beskrivs enhetsregistreringsprocessen i ett AEM Screens-projekt.

## Registrerar en enhet {#registering-a-device}

Enhetsregistreringsprocessen görs på två olika datorer:

* Den faktiska enhet som ska registreras, till exempel din skyltskärm
* Den AEM som används för att registrera din enhet

>[!NOTE]
>
>När du har laddat ned den senaste Windows Player-versionen (*.exe*) från [AEM 6.4 Player Downloads](https://download.macromedia.com/screens/) följer du stegen på spelaren för att slutföra ad hoc-installationen:
>
>1. Tryck länge på det övre vänstra hörnet för att öppna administrationspanelen.
>1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsadressen för den AEM instansen i **Server** och klicka på **Spara**.
>1. Klicka på länken **Registrering** i den vänstra åtgärdsmenyn och stegen nedan för att slutföra enhetsregistreringsprocessen.

>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Starta AEM Screens Player på enheten. Registreringsgränssnittet visas.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. I AEM navigerar du till mappen **Devices** i ditt projekt.

   >[!NOTE]
   >
   >Mer information om hur du skapar ett nytt projekt för skärmar på AEM kontrollpanel finns i [Skapa och hantera skärmsprojekt](creating-a-screens-project.md).

1. Tryck/klicka på knappen **Enhetshanteraren** i åtgärdsfältet.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Tryck/klicka på knappen **Enhetsregistrering** överst till höger.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Välj önskad enhet (samma som steg 1) och tryck/klicka på **Registrera enhet**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. AEM väntar på att enheten ska skicka sin registreringskod.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Kontrollera **registreringskoden** på enheten.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Om **registreringskoden** är densamma på båda datorerna trycker/klickar du på **Validera** i AEM, vilket visas i steg 6.
1. Ange önskat namn för enheten och klicka på **Registrera**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Tryck/klicka på **Slutför** för att slutföra registreringsprocessen.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >Med **Register New** kan du registrera en ny enhet.
   >
   >Med **Tilldela visning** kan du lägga till enheten direkt på en skärm.

   Om du klickar på **Slutför** måste du tilldela enheten till en skärm.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar och hanterar en visning för ditt skärmsprojekt finns i [Skapa och hantera skärmar](managing-displays.md).

### Tilldela enhet till en skärm {#assigning-device-to-a-display}

Om du inte har tilldelat enheten till en skärm följer du stegen nedan för att tilldela enheten till en skärm i ditt AEM Screens-projekt:

1. Markera enheten och klicka på **Tilldela enhet** i åtgärdsfältet.

   ![screen_shot_2018-11-26at11026am](assets/screen_shot_2018-11-26at111026am.png)

1. Välj sökvägen för visningen i **Sökväg till Display/Device Config**.

   ![screen_shot_2018-11-26at11252am](assets/screen_shot_2018-11-26at111252am.png)

1. Klicka på **Tilldela** när du markerar sökvägen.

   ![screen_shot_2018-11-26at11722am](assets/screen_shot_2018-11-26at111722am.png)

1. Klicka på **Slutför** när enheten har tilldelats, enligt bilden nedan.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Dessutom kan du visa kontrollpanelen när du klickar på **Slutför**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Söka efter en enhet från Enhetshanteraren {#search-device}

När du har registrerat enheter till spelaren kan du visa alla enheter från användargränssnittet i Enhetshanteraren.

1. Gå till användargränssnittet för Enhetshanteraren från ditt AEM Screens-projekt, till exempel **DemoScreens** —> **Enheter**.

1. Välj mappen **Enheter** och klicka på **Enhetshanteraren** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/device-manager/device-manager-1.png)

1. Listan över registrerade enheter visas.

1. Om du har en lång lista över registrerade enheter kan du nu söka med sökikonen i åtgärdsfältet

   ![bild](/help/user-guide/assets/device-manager/device-manager-2.png)

   Eller

   Klicka på `/` (snedstreck) för att aktivera sökfunktionen.

   ![bild](/help/user-guide/assets/device-manager/device-manager-3.png)


### Begränsningar för sökfunktioner {#limitations}

* Användaren kan söka efter alla ord som finns i *enhets-ID* eller *enhetsnamn*.

   >[!NOTE]
   >Vi rekommenderar att du skapar enhetsnamnen i flera ord, t.ex. *Boston Store Lobby* i stället för en enda *BostonStoreLobby*.

* Om du skapar enhetsnamn som *Boston Store Lobby* kan den söka efter valfritt ord *boston*, *store* eller *lobby* men om enhetsnamnet kallas *BostonStoreLobby* sökning &lt;a1 0/>boston *visar inte resultatet.*

* Jokertecken `*` stöds för sökning. Om du vill hitta alla enheter med namn som börjar med *boston* kan du använda *boston**.

* Om enhetsnamnet är *BostonStoreLobby* och du söker efter *boston* returneras inte resultatet om du använder *boston** i sökvillkoren.

## Begränsningar för enhetsregistrering {#limitations-on-device-registration}

Användarlösenordsbegränsningar för hela systemet kan orsaka fel i enhetsregistreringen. Enhetsregistreringen använder ett slumpmässigt genererat lösenord för att skapa enhetsanvändaren.

Om lösenordet begränsas av *AuthorizableActionProvider*-konfigurationen kan det hända att det inte går att skapa enhetsanvändaren.

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

### Ytterligare resurser {#additional-resources}

Mer information om AEM Screens Player finns i [AEM Screens Player](working-with-screens-player.md).
