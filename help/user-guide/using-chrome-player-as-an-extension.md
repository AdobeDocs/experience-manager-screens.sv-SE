---
title: Använda Chrome Player som tillägg
description: Lär dig hur du installerar färgspelaren som ett webbläsartillägg för AEM Screens.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: 4102c2b2291c92823a36f87f07d5b5ca87cfa48f
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Använda Chrome Player som tillägg {#using-chrome-player}

ChromeOS-spelaren kan installeras som Chrome Browser-plugin i utvecklarläge utan att den faktiska enheten för Chrome Player krävs.

>[!CAUTION]
>
> Vi rekommenderar att du använder Chrome Player som ett tillägg för felsökning för snabbdemonstrationer, felsökning och även för att felsöka kundproblem. Använd inte den här mekanismen för produktionsdistributioner som kräver helskärmsläge och central hantering.

Följ den här sidan om du vill ha information om hur du installerar färgspelaren som ett webbläsartillägg.

1. Klicka [här](https://download.macromedia.com/screens/) för att ladda ned den senaste Chrome Player.

1. Zippa upp och spara det på disken.

1. Öppna webbläsaren Chrome och klicka på menyn med tre punkter och välj **Fler verktyg** från **Tillägg** i det övre högra hörnet eller navigera direkt till `chrome://extensions`.

1. Aktivera **Utvecklare** från det övre högra hörnet.

1. Klicka **Läs in opackad** från det övre vänstra hörnet och ladda uppzippad Chrome Player.

1. Kontrollera AEM Screens Chrome Player-plugin om det finns i listan över tillägg.

1. Öppna en ny flik och klicka på Apps-ikonen i det övre vänstra hörnet eller navigera direkt till `chrome://apps`.

1. Klicka **AEM Screens Plugin** så att du kan starta Chrome Player.

   >[!NOTE]
   >
   > Som standard startas spelaren i helskärmsläge. Tryck **Esc** för att avsluta helskärmsläget.


## Avancerade felsökningstips {#advanced-debugging-tips}

1. När spelaren har hämtat innehåll lokalt kan du bläddra i lokalt hämtat innehåll genom att gå till `http://localhost:24502`.

   >[!NOTE]
   >
   > Om den ovannämnda URL:en inte fungerar betyder det att spelaren inte har tilldelats någon visning eller att innehållet inte har hämtats. På nätverksfliken för spelarkonfigurationens JSON kan du se om spelaren har fått rätt information och om det finns nätverksproblem vid hämtning.

1. Högerklicka och inspektera tre lager i Chrome Player.
   **Felsöka innehåll**: Högerklicka och inspektera innehållet för att felsöka det innehåll som körs (det ska finnas ett objekt med namnet&quot;Inspect&quot; på snabbmenyn)

   **Felsöka inbyggd programvara**: Ta fram administratörsgränssnittet och högerklicka och inspektera sedan för att felsöka den inbyggda programkoden (spelare). (Det bör finnas ett alternativ för att inspektera och inspektera bakgrundssidan och simulera omstart av webbläsaren.)

   **Felsöka bakgrundssida**: Ta fram administratörsgränssnittet och högerklicka och inspektera sedan bakgrundssidan (för bakgrundstjänster som http-server).

## Uppgradera Player-tillägget {#upgrading-player}

Följ stegen nedan för att uppgradera spelartillägget om en ny version av spelaren släpps upp. Du kan även följa instruktionerna nedan för att testa uppgraderingsscenarier:

1. Stäng alla aktiva fönsterkontroller och spelarinstanser
1. Byt namn på den gamla mappen med spelarfiler
1. Extrahera den nya zippen på samma plats som den gamla mappen
1. Starta Chrome och navigera till `chrome://extensions`
1. Markera spelarikonen och klicka på knappen Uppdatera eller Läs in igen
