---
title: Content Update using Screens Launch
description: Lär dig hur du skapar en framtida version av kanalerna, som kallas Launch, och ställer in ett live-datum för lanseringen för att göra innehållet tillgängligt på enheter eller spelare.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 0%

---

# Content Update using Screens Launch {#launches}

Innehållsförfattare kan skapa en framtida version av kanalerna och ytterligare ange livedatum för den här lanseringen. Den här möjligheten gör att innehållet kan vara live i enheter eller spelare på angivet live-datum.

Med hjälp av ***Skärmstart***, kan författarna förhandsgranska varje kanal i starten och bör kunna initiera en begäran om granskning. Godkännargruppen får meddelanden och kan godkänna eller avvisa begäran. När live-datumet nås spelas innehållet upp på enheterna.

Om författaren till exempel vill skapa framtida versioner av c1, c2 (kanaler) skapas en start och ett live-datum ställs in (till exempel 10 november 8:00 A.M.). Fler uppdateringar av innehållet skickas ut för granskning.

Efter godkännande och på live-datumet (10 november, 8:00) spelas innehållet upp på enheterna eller spelarna.

## Krav {#requirements}

Innan du börjar använda *Skärmstart* i ett AEM Screens-projekt, se till att du förstår begreppet respitperiod och dess relevans.

När du kör en upplevelse på det angivna live-datumet på spelaren ingår följande:

* Sälj om att starta (tar normalt några sekunder).

* Publicering av resurser för publicering av instanser (tar vanligtvis några minuter, beroende på kanalernas eller resursernas storlek som måste publiceras).

* Den tid det tar för uppdateringen av offlineinnehåll att slutföras (tar normalt några minuter).

* Den tid det tar för spelarna att hämta innehållet från publiceringsinstansen (tar vanligtvis minuter beroende på bandbredden och storleken på resurserna som ska hämtas).

* Skillnader mellan servern och spelaren när som helst.

### Förstå respitperiod {#understanding-grace-period}

För att spelaren ska kunna börja spela upp innehållet på angivet live-datum startar du föregående aktiviteter före live-datumet.

Om live-datumet är *24 november 2000* och *24 timmar* är respitperioden, så börjar ovanstående åtgärdssekvens vid (live date - respitperiod), det vill säga den 23 november, 9:00 A.M. servertid. Den här inställningen ger 24 timmar att slutföra alla de ovannämnda åtgärderna för att innehållet ska nå ut till spelarna. Spelarna är införstådda med att den här perioden är ett startmaterial. Det innebär att innehållet inte spelas upp omedelbart, men spelarna kan lagra innehållet som en framtida version och låta det börja spelas upp exakt på det angivna livedatumet i spelarens tidszon.

Servern är till exempel i PST och enheterna är i EST. Den maximala tidsskillnaden är tre timmar. Kampanjen förutsätter att den tar en minut och att publiceringen från författaren tar 10 minuter att publicera och spelaren kan hämta resurserna på normalt 10-15 minuter. Därefter respitperioden = tidsskillnaden (tre timmar):

* Plus tid att marknadsföra lanseringen (1 minut)
* Plus tid för att publicera startprogrammet (10 minuter)
* Plus tid att ladda ned på spelaren (10-15 minuter)
* Plus-buffert (30 minuter)

Därför bör du ange 3 timmar och 56 minuter (14160 sekunder).

Så när du schemalägger en livesändning börjar kampanjen tidigt med att ta hänsyn till den här förskjutningen. I ekvationen ovan tar de flesta objekten inte så lång tid. Du kan använda en bra gissning för den här förskjutningen när du känner till den maximala tidsskillnaden mellan servern och valfri spelare.

>[!NOTE]
>
>Körklar är fristen för att starta skärmar inställd på 24 timmar. Det innebär att när du anger ett live-datum för en start för resurserna under */content/screens*, börjar kampanjen med den här förskjutningen.

### Uppdaterar en respitperiod som inte är tillgänglig {#updating-out-of-the-box-grace-period}

I det här avsnittet beskrivs hur du kan uppdatera en kostnadsfri respitperiod till 10 minuter.

1. Navigera till CRXDE Lite och sedan till `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. Högerklicka och kopiera filen.
1. Navigera till `/apps/system/config` och högerklicka och klistra in.
1. Dubbelklicka `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` så att du kan öppna filen i redigeraren i CRXDE Lite. Den måste visa respitperioden för sökvägen */content/screens/* as **86400**. Ändra värdet till **600**.

Innehållet i textfilen bör nu se ut ungefär så här:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Du ställer in respitperioden på 10 minuter i föregående exempel. När du anger ett live-datum för en start för resurserna under */content/screens*, börjar kampanjen med den här förskjutningen.

Om till exempel live-datumet är inställt på 24 november, 9:00 och respitperioden är 600 sekunder börjar kampanjjobbet 24 november klockan 8:50.

## Använda skärmstart {#using-launches}

I det här avsnittet visas hur du implementerar Screens Launch i ditt AEM Screens-projekt.

### Creating a Screens Launch {#creating-a-launch}

Följ stegen nedan för att implementera funktionen Screens Launch i ditt AEM Screens-projekt:

1. Skapa en sekvenskanal i ett AEM Screens-projekt, till exempel **StartarDemo** > **Kanaler** > **FutureLaunch**, vilket visas nedan.

   >[!CAUTION]
   >
   >Skapa en lansering från en befintlig kanal i ditt AEM Screens-projekt.

   ![Bild](/help/user-guide/assets/launches-images/launches-11.png)

1. Klicka på kanalen **FutureLaunch** och klicka **Skapa start** i åtgärdsfältet.

   ![Bild](/help/user-guide/assets/launches-images/launches-12.png)

1. The **Skapa start** öppnas. Du kan antingen klicka på kanalen som redan visas i guiden eller klicka på **+ Lägg till kanaler** om du vill lägga till kanalen som du vill skapa starten för.

1. Klicka **Nästa** från **Skapa start** guide. The **Inkludera undersidor** är markerat som standard.

   ![bild](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Du kan använda **+ Lägg till kanaler** alternativ för att lägga till en annan kanal som du vill skapa starten för.

   Använd **Lägg till kanaler** , navigera till den kanal som du vill starta programmet för och klicka på **Välj**.

   The **Välj** är inaktiverat om du försöker klicka på flera kanaler eller en mapp för att lägga till starten.

   ![bild](/help/user-guide/assets/launches-images/launches-14.png)

   När du klickat på kanalen/kanalerna klickar du på **Nästa**.


1. Ange **Starta titel** as **Sommarkampanjer** och du behöver inte ange **Startdatum**, vilket visas i figuren nedan. Klicka **Skapa**.

   >[!NOTE]
   >
   >*Aktivera eller kontrollera* alternativet **Ärv källsidans livedata** tillåter att kanalerna skapas som live-kopior vid lanseringen. Om några ändringar görs i den ursprungliga kanalen tillämpas dessa ändringar automatiskt på startkanaler.
   >
   >
   >*Inaktivera eller avmarkera* **Ärv källsidans livedata** tillåter att kanalerna kopieras utan någon aktiv relation i starten. Så om ändringar görs i den ursprungliga kanalen tillämpas inte dessa ändringar på startkanaler.

   ![Bild](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Du kan ställa in live-startdatum i det här steget eller ställa in det senare när du redigerar egenskaperna för startprogrammet när det redan har skapats.

   **Förstå starterbjudandeomfång**

   * **Befordra en fullständig start** - Alla kanaler för lanseringen befordras vid angivet live-datum.
   * **Befordra ändrade sidor** - Endast ändrade startresurser befordras. Använd det här alternativet när startgranskning inte krävs.
   * **Befordra godkända sidor** - Det här alternativet kräver att arbetsflödet för godkännande vid start körs på startkanalerna. Endast godkända sidor befordras vid angivet live-datum.

     >[!CAUTION]
     >
     >Lansering av live-datum respekterar spelarens/enhetens tidszon i stället för servrar.

1. Observera att du har startat programmet. Du kan antingen klicka **Öppna** för att visa sidorna i redigeraren eller klicka på **Klar** för att gå tillbaka till ditt projekt.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Markera **Klar** kan du gå tillbaka till **FutureLaunch** kanal.

   ![Bild](/help/user-guide/assets/launches-images/launches-16.png)


### Redigera Launch-egenskaperna för att ange Live-datum och -omfång {#editing-the-launch-properties-to-set-the-live-date-and-scope}

När lanseringen har skapats kan du uppdatera egenskaperna, till exempel live-datum, starttitel och kampanjomfång, med **Startegenskaper**.

* **Startdatum** - live-datumet, det vill säga det datum eller den tidpunkt då innehållet spelas upp i skärmspelaren enligt spelarens tidszon.
* **Produktionsklar** - Efter befordran kan kanalerna publiceras och körklar är aktiverad, så du behöver inte ändra den.
* **Omfång** - Bestäm vilka kanaler som ska höjas under lanseringskampanjen.

Följ stegen nedan för att redigera startegenskaperna:

1. Navigera till kanalen **FutureLaunch** *(väntande start)* och klicka på kanalen enligt bilden nedan.

   ![bild](/help/user-guide/assets/launches-images/launches-17.png)

1. Klicka **Kontrollpanel** i åtgärdsfältet visas **VÄNTANDE START** från kanalkontrollpanelen.

   ![bild](/help/user-guide/assets/launches-images/launches-18.png)

1. Klicka på startsidan och klicka på **Startegenskaper** från **VÄNTANDE START** -panelen.

   ![bild](/help/user-guide/assets/launches-images/launches-19.png)

### Redigera startfönstret för skärmar för att lägga till eller ta bort kanaler {#editing-the-screens-launch-to-add-or-remove-channels}

När du har skapat starten kan du lägga till eller ta bort kanaler i den befintliga starten med **Redigera start** alternativ.

Klicka på **Spara** för att gå tillbaka till **FutureLaunch** kanal.

### Marknadsför att starta skärmar manuellt{#promote-the-screens-launch-manually}

Du kan befordra starten manuellt med **`Promote Launch`** från **VÄNTANDE START** -panelen.

Du kan välja vilka resurser du vill befordra som en del av den här manuella befordringen i dialogrutan **Starta erbjudandeguiden**.

![bild](/help/user-guide/assets/launches-images/launches-e.png)

1. Du kan aktivera eller inaktivera alternativet att ta bort starten efter produktionen.
1. Du kan ange **Omfång** vid starten med följande alternativ:
   * **Befordra en fullständig start** - Alla kanaler för lanseringen befordras vid angivet live-datum.
   * **Befordra ändrade sidor** - Endast ändrade startresurser befordras. Använd det här alternativet när startgranskning inte krävs.
   * **Befordra godkända sidor** - Det här alternativet kräver att arbetsflödet för godkännande vid start körs på startkanalerna. Endast godkända sidor befordras vid angivet live-datum.
   * **Höj upp aktuell sida** - Det här alternativet kräver att arbetsflödet för godkännande vid start endast körs för den aktuella sidan.
1. Klicka **Nästa** i **Promote Launch** guide.
1. Klicka **Befordra** för att marknadsföra lanseringen.

### Ta bort skärmstart

Du kan ta bort programstarten med **Ta bort start** från **VÄNTANDE START** -panelen.

>[!CAUTION]
>
>Den här åtgärden tar även bort alla underordnade (kapslade starter).
