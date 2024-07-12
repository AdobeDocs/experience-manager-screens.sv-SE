---
title: Automatisk registrering av spelare
description: Följ den här sidan så att du kan lära dig mer om automatisk registrering av spelare med AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Automatisk registrering av spelare {#auto-registration}

Om du registrerar tusentals spelare manuellt blir det krångligt och kostar mer och mer. För att förenkla den här processen kan du med bulkregistreringsfunktionen ange en i förväg delad nyckel i AEM som kan etableras i en spelare antingen via en konfigurationsfil eller en MDM-lösning (Mobile Device Management).

## Implementera automatisk registrering av spelare {#bulk-registering-implementation}

Följ stegen nedan för att implementera automatisk registrering av spelare:

1. Logga in på AEM och klicka på ditt AEM Screens-projekt och klicka på **Egenskaper** i åtgärdsfältet.
1. Klicka på fliken **Avancerat** så att du kan visa avsnittet **Enhetsregistrering**.

1. Ange en kod för automatisk registrering i fältet **Kod för massregistrering**. Därefter visas en valfri standardskärm i **standardvisningstilldelningen** som tilldelas den spelare som registreras automatiskt.

   >[!NOTE]
   >Ange en valfri kod och klicka på en standardskärm om det behövs.

   ![bild](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Ge dina spelare rätt server-URL och registreringskod med hjälp av en MDM-fil eller JSON-konfigurationsfil.

   >[!NOTE]
   >Mer information finns på implementeringssidan för den specifika spelaren för ditt operativsystem. Du kan också använda administratörsgränssnittet för att ange registreringskoden.

1. Om attributet `registrationKey` matchar det som är konfigurerat i AEM registrerar sig spelaren automatiskt och om en standardskärm är konfigurerad hämtas och spelas innehållet upp.

   ![bild](/help/user-guide/assets/auto-registration/auto-register2.png)

## Bästa praxis för säkerhet {#security-best-practices}

Följ avsnittet nedan för att se några av de bästa sätten att skydda:

* Se till att registreringskoden inte äventyras - Konfigurera koden i AEM precis innan du påbörjar gruppregistreringen och när du är klar rensar du det fältet och sparar i AEM.

* Du kan konfigurera sökvägen `/bin/screens/registration` så att den bara är tillgänglig från kända IP-intervall, om det är möjligt.

* Använd en MDM för att tilldela spelaren konfigurationen.

* Använd alltid `HTTPS` och inte `HTTP` för spelarkommunikation med AEM.

  >[!NOTE]
  >Standardvisningstilldelning fungerar för närvarande bara för massregistrering. Det fungerar inte för manuell registrering när en registreringskod inte är tillgänglig.
