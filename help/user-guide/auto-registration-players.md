---
title: Automatisk registrering av spelare
seo-title: Auto Registration of Players
description: Följ den här sidan om du vill veta mer om automatisk registrering av spelare med AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Automatisk registrering av spelare {#auto-registration}

Om du registrerar tusentals spelare manuellt kan det bli mycket krångligt och ge tid och pengar. För att förenkla den här processen kan du med bulkregistreringsfunktionen ange en i förväg delad nyckel i AEM som kan etableras i en spelare antingen via en konfigurationsfil eller en MDM-lösning (Mobile Device Management).

## Implementera automatisk registrering av spelare {#bulk-registering-implementation}

Följ stegen nedan för att implementera automatisk registrering av spelare:

1. Logga in i AEM och välj AEM skärmar och klicka på **Egenskaper** i åtgärdsfältet.
1. Välj **Avancerat** -fliken för att visa **Enhetsregistrering** -avsnitt.

1. Ange en kod för automatisk registrering i **Registreringskod för massutskick** fält och en valfri standardvisning i **Standardvisningstilldelning** som tilldelas den spelare som registreras automatiskt.
   >[!NOTE]
   >Ange en valfri kod och välj en standardskärm om det behövs.

   ![bild](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Ge dina spelare rätt server-URL och registreringskod med hjälp av en MDM-fil eller JSON-konfigurationsfil.

   >[!NOTE]
   >Mer information finns på implementeringssidan för den specifika spelaren för operativsystemet. Du kan också använda administratörsgränssnittet för att ange registreringskoden.

1. Om `registrationKey` -attributet matchar det som konfigurerats i AEM, spelaren registreras automatiskt och om en standardskärm är konfigurerad hämtas och spelas innehållet upp.

   ![bild](/help/user-guide/assets/auto-registration/auto-register2.png)

## Bästa praxis för säkerhet {#security-best-practices}

Följ avsnittet nedan för att se några av de bästa sätten att skydda:

* Om du vill vara säker på att registreringskoden inte äventyras konfigurerar du koden i AEM precis innan du påbörjar gruppregistreringen. När du är klar rensar du det fältet och sparar i AEM.

* Du kan konfigurera sökvägen `/bin/screens/registration` att endast vara tillgänglig från kända IP-intervall om möjligt.

* Använd en MDM för att tilldela spelaren konfigurationen.

* Använd alltid `HTTPS` och inte `HTTP` för spelarkommunikation med AEM.

   >[!NOTE]
   >Standardvisningstilldelning fungerar för närvarande bara för massregistrering och inte för manuell registrering utan registreringskod.
