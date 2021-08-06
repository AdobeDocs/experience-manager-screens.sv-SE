---
title: Aktivering på kanalnivå - uppspelning av enstaka händelse
seo-title: Aktivering på kanalnivå - uppspelning av enstaka händelse
description: Följ den här vägledningen när du vill veta mer om aktivering på kanalnivå med en enda händelseuppspelning.
topic-tags: authoring
feature: redigeringsskärmar, aktivering på kanalnivå
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: 72352b9ece8fde2d02b9fa0ccd25c6dfd7d602fd
workflow-type: tm+mt
source-wordcount: '1795'
ht-degree: 0%

---

# Aktivering på kanalnivå {#channel-level-activation-single-event-playback}

Den här sidan beskriver kanalnivåaktivering för resurserna som används i kanaler.

Följande ämnen behandlas i detta avsnitt:

* Översikt
* Aktiveringsfönster
* Använda kanalnivåaktivering som en enda händelseuppspelning
* Hantera återkommande för resurser i en kanal
   * DayParting
   * WeekParting
   * MånadDelning
   * Kombination av partner
* Använda kanalnivåaktivering som en enda händelseuppspelning

## Översikt {#overview}

***Kanalnivåaktivering*** gör att kanalerna kan växla efter ett visst angivet schema. Den enskilda händelsekanalen ersätter huvudkanalen efter ett angivet schema och spelas upp en viss tid tills huvudkanalen spelar upp innehållet igen.

I följande exempel får du en lösning genom att fokusera på följande nyckeltermer:

* en ***huvudsekvenskanal*** för den globala sekvensen
* en ***enkel händelsekanal*** som bara körs en gång i taget
* en ***ange schema och prioritet*** för den enda uppspelningshändelsen som inträffar inuti huvudsekvenskanalen

## Aktiveringsfönster {#using-channel-level-activation}

I följande avsnitt beskrivs hur du skapar en enda händelseuppspelning i en kanal för ett AEM Screens-projekt.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har följande krav klara att börja implementera aktivering på kanalnivå:

* Skapa ett AEM Screens-projekt, i det här exemplet **Kanalnivåaktivering**

* Skapa en kanal som **MainAdChannel** under mappen **Kanaler**

* Skapa en annan kanal som **TargetedSinglePlay** under **Kanaler** mapp

* Lägg till relevanta resurser i båda kanalerna

Följande bild visar **kanalnivåaktivering**-projektet med **MainAdChannel** och **TargetedSinglePlay**-kanaler i **kanalmappen**.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Mer information om hur du skapar ett projekt och hur du skapar en sekvenskanal finns i resurserna nedan:
>
>* [Skapa och hantera projekt](creating-a-screens-project.md)

* [Hantera en kanal](managing-channels.md)



### Implementering {#implementation}

Implementering av kanalnivåaktivering i ett AEM Screens-projekt innefattar tre viktiga uppgifter:

1. **Konfigurera Project-taxonomin inklusive kanaler, platser och bildskärmar**
1. **Tilldela kanaler att visa**
1. **Konfigurera ett schema och en prioritet**

Följ stegen nedan för att implementera funktionen:

1. **Skapa en plats**

   Navigera till mappen **Platser** i ditt AEM Screens-projekt och skapa en plats som **Region**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   Mer information om hur du skapar en plats finns i **[Skapa och hantera platser](managing-locations.md)**.

1. **Skapa visning under plats**

   1. Navigera till **Kanalnivåaktivering** > **Platser** > **Region**.
   1. Välj **Region** och klicka på **+ Skapa** i åtgärdsfältet.
   1. Välj **Visa** i guiden och skapa en visning med namnet **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Tilldela kanaler att visa**

   För **MainAdChannel:**

   1. Navigera till **Aktivering på kanalnivå** > **Platser** > **Region** > **RegionDisplay** och klicka på **Tilldela kanal** i åtgärdsfältet.
   1. **Dialogrutan** Kanaltilldelning öppnas.
   1. Välj **Referenskanal**. efter bana.
   1. Välj **kanalsökvägen** som **Kanalnivåaktivering** —> ***Kanaler*** —> ***MainAdChannel***.
   1. **Kanalrollen** är ifylld som **huvudkanal**.
   1. Välj **Prioritet** som **1**.
   1. Välj **Händelser som stöds** som **Inledande inläsning** och **Inaktivitetsskärm**.
   1. Klicka på **Spara**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   Du kan också tilldela kanal från kontrollpanelen genom att gå till **Kanalnivåaktivering** —> **Platser** —> **Region** —> **RegionDisplay** och klicka på **Kontrollpanel** från åtgärdsfältet. Klicka på **+ Tilldela kanal** på panelen **TILLDELADE KANALER &amp; SCHEMAT**.

   Tilldela på liknande sätt kanalen **TargetedSinglePlay** för visning**:

   1. Navigera till **Aktivering på kanalnivå** —> **Platser** —> **Region** —> **RegionDisplay** och klicka på **Tilldela kanal** i åtgärdsfältet.
   1. **Dialogrutan** Kanaltilldelning öppnas.
   1. Välj **Referenskanal**. efter bana.
   1. Välj **kanalsökvägen** som **Kanalnivåaktivering*** —> ***Kanaler*** —> ***TargetedSinglePlay***.
   1. **Kanalrollen** fylls i som **målsingleplay**.
   1. Ange **Prioritet** som **2**.
   1. Välj **Händelser som stöds** som **Inledande inläsning**, **Inaktivitetsskärm** och **Timer**, *enligt bilden nedan.
   1. Välj datumet i **active from** as November 27, 2018 11:59 och i **active until** as November 28, 2018 kl. 12:05.
   1. Klicka på **Spara**.

   >[!CAUTION]
   Du måste ange prioriteten för kanalen **TargetedSinglePlay** som är högre än kanalen **MainAdSegment**.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Om du vill välja samma dag måste du markera nästa dag och manuellt redigera datumet till samma dag men för en senare tid. Detta hindrar användaren från att välja ett tidigare datum. Se exemplet nedan:

   ![new1](assets/new1.gif)

## Visa resultaten {#viewing-the-results}

När du har konfigurerat kanalerna och visningen är klar startar du AEM Screens-spelaren för att visa innehållet.

Spelaren visar innehållet i **MainAdChannel** och exakt vid 11:59 (enligt schemat), visar **TargetedSinglePlay**-kanalen innehållet till kl. 12.05 och sedan fortsätter uppspelningen av **MainAdChannel**.

>[!NOTE]
Läs mer om AEM Screen Player här:
[AEM Screens Player-hämtningar](https://download.macromedia.com/screens/)
[Arbeta med AEM Screens Player](working-with-screens-player.md)


## Hantera återkommande för resurser i en kanal {#handling-recurrence-in-assets}

Du kan schemalägga att resurser i en kanal återkommer med vissa intervall på varje dag, vecka eller månad, beroende på dina behov.

Anta att du bara vill visa innehållet i en kanal på fredag från 1:00 till 10:00. Du kan använda fliken **Aktivering** för att ange önskat intervall för resursen.

### Dag-parsning {#day-parting}

1. Markera kanalen och klicka på **Kontrollpanelen** i åtgärdsfältet för att öppna kanalkontrollpanelen.

1. När du har angett startdatum/tid och slutdatum/tid i dialogrutan **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschema.

   >[!NOTE]
   Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman efter behov.

1. Ange uttrycket i **Schedule** så visas resursen för det angivna intervallet för dag och tid.

#### Exempeluttryck för dagdelning {#example-one}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| före 08:00 | resursen i kanalen spelas upp innan klockan åtta varje dag |
| efter klockan 2:00 | resursen i kanalen spelas upp efter klockan 17:00 varje dag |
| efter 12:15 och före 12:45 | resursen i kanalen spelas upp efter kl. 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | resursen i kanalen spelas upp före kl. 12.15 varje dag och även efter kl. 12.45 |
| Mån,Nyans,Ved eller Mån-Ved | resursen spelas upp i kanalen från måndag till onsdag |
| den första dagen i januari efter kl. 2:00 också den andra dagen i januari, även den tredje dagen i januari före kl. 3:00 | resursen i kanalen börjar spelas upp efter kl. 2:00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 3:00 den 3 januari |
| den 1-2 januari efter kl. 2:00 också den 2-3 januari före kl. 3:00 | resursen i kanalen startar spelaren efter kl. 2:00 den 1 januari, fortsätter att spelas upp till kl. 17:00 den 2 januari och börjar igen kl. 2:00 och fortsätter att spelas upp till kl. 3:00 den 3 januari |

>[!NOTE]
Du kan också använda _militär tid_-notation (d.v.s. 14:00) i stället för *am/pm*-notation (d.v.s. 2:00).

### WeekParting {#week-parting}

1. Markera kanalen och klicka på **Kontrollpanelen** i åtgärdsfältet för att öppna kanalkontrollpanelen.

1. När du har angett startdatum/tid och slutdatum/tid i dialogrutan **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschema.

   >[!NOTE]
   Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman efter behov.

1. Ange uttrycket i **Schedule** så visas resursen för det angivna intervallet för dag och tid.

#### Exempeluttryck för WeekParting {#example-two}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| Mån,Nyans,Ved eller Mån-Ved | resursen spelas upp i kanalen från måndag till onsdag |
| före 08:00 | resursen i kanalen spelas upp innan klockan åtta varje dag |
| efter klockan 2:00 | resursen i kanalen spelas upp efter klockan 17:00 varje dag |
| efter 12:15 och före 12:45 | resursen i kanalen spelas upp efter kl. 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | kanalen spelas upp före kl. 12.15 varje dag och även efter kl. 12.45 |

>[!NOTE]
Du kan också använda _militär tid_-notation (d.v.s. 14:00) i stället för *am/pm*-notation (d.v.s. 2:00).


### MånadDelning {#month-parting}

1. Markera kanalen och klicka på **Kontrollpanelen** i åtgärdsfältet för att öppna kanalkontrollpanelen.

1. När du har angett startdatum/tid och slutdatum/tid i dialogrutan **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschema.

   >[!NOTE]
   Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman efter behov.

1. Ange uttrycket i **Schedule** så visas resursen för det angivna intervallet för dag och tid.

#### Exempeluttryck för MonthParting {#example-three}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| februari,maj,augusti,november | resursen spelas upp i kanalen i februari,maj,augusti,november |

>[!NOTE]
När du definierar veckodagar och månader kan du både använda kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari.

>[!NOTE]
Du kan också använda _militär tid_-notation (d.v.s. 14:00) i stället för *am/pm*-notation (d.v.s. 2:00).

### Kombination av partner {#combined-parting}

1. Markera kanalen och klicka på **Kontrollpanelen** i åtgärdsfältet för att öppna kanalkontrollpanelen.

1. När du har angett startdatum/tid och slutdatum/tid i dialogrutan **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschema.

   >[!NOTE]
   Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman efter behov.

1. Ange uttrycket i **Schedule** så visas resursen för det angivna intervallet för dag och tid.

#### Exempeluttryck för en kombination av partner {#example-four}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| efter 6:00 och före 18:00 i Mon, Wed of Jan-Mar | tillgången spelas upp i kanalen mellan kl. 6.00 och kl. 18.00 måndag och onsdag från januari till slutet av mars |
| den första dagen i januari efter kl. 2:00 också den andra dagen i januari, även den tredje dagen i januari före kl. 3:00 | resursen i kanalen börjar spelas upp efter kl. 2:00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 3:00 den 3 januari |
| den 1-2 januari efter kl. 2:00 också den 2-3 januari före kl. 3:00 | resursen i kanalen startar spelaren efter kl. 2:00 den 1 januari, fortsätter att spelas upp till kl. 17:00 den 2 januari och börjar igen kl. 2:00 och fortsätter att spelas upp till kl. 3:00 den 3 januari |

>[!NOTE]
När du definierar veckodagar och månader kan du både använda kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari.  Dessutom kan du använda _militär tid_-notation (d.v.s. 14:00) i stället för *am/pm*-notation (d.v.s. 2:00).
