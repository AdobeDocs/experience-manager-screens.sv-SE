---
title: Konfiguration och felsökning av videouppspelning
description: Lär dig hur du felsöker och felsöker videouppspelning i din kanal för AEM Screens.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 1%

---

# Konfiguration och felsökning av videouppspelning {#video-playback-configuration-and-troubleshooting}

När du överför en video till DAM och lägger till den i din kanal kan det uppstå problem där videon inte kan spelas upp i AEM Screens Player.

I följande avsnitt beskrivs hur du felsöker och felsöker videouppspelning i din kanal.

## DAM-återgivningar {#dam-renditions}

När du har överfört videon till kanalen bör AEM börja skapa vissa återgivningar för den. Du kan visa dina videofilmer under Assets.

Så här visar du videon:

1. Navigera till videon, till exempel `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Klicka på videon och expandera den övre vänstra menyn och klicka på **Återgivningar**.

Det ska finnas olika renderingar (MP4 eller M4V).

Om det inte finns någon återgivning kontrollerar du att du har FFMPEG installerat på det operativsystem där AEM körs.

>[!CAUTION]
>
>Om det inte finns någon återgivning kontrollerar du att du har FFMPEG installerat på det operativsystem där AEM körs.
>
>Klicka [här](https://www.ffmpeg.org/download.html) för att installera FFMPEG.

## Video Assets {#video-assets}

Om du inte ser något källattribut under video kan det bero på att videon inte har transkodats. Om videon omkodas korrekt visas den på kontrollpanelen, vilket visas i följande exempel:

Kontrollera att FFMPEG är installerat och videoprofilerna.

![chlimage_1-2](assets/chlimage_1-2.png)

### Kontrollerar videoprofil {#checking-video-profile}

1. Navigera till **videoprofilen**, det vill säga `http://localhost:4502/etc/dam/video.html`, och klicka på **Överför testvideo**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Överför en testvideo och klicka på **OK** så att du kan börja omkodningen.

   Om den omkodade videon misslyckas expanderar du FFMPEG-utdata för att förstå eventuella fel i konsolutdata i FFMPEG.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Om videoomkodningen lyckas kan även den omkodade filen hämtas.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Se till att du hinner koda om videon tillräckligt mycket innan du lägger till den i någon kanal (den nya taggen ska visas i stället för att bearbetas).

### Kontrollera profil med en videokomponent {#checking-profile-with-a-video-component}

Kontrollera listan med profiler från siddesignen om videokomponenten inte är korrekt konfigurerad.

1. Navigera till kanalen och klicka på **designläget**.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Klicka på videon och öppna dialogrutan **Redigera**. Öppna fliken **Profiler**.

   >[!NOTE]
   >Klicka på olika profiler (åtminstone ska profilen&quot;Hög kvalitet H.264&quot; finnas).

### Kontrollera videon i webbspelaren {#checking-the-video-in-the-web-player}

Använd **webbspelaren** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` för att validera uppspelningen i webbläsare (Chrome och Safari). Chrome används på Android™-enheter medan Safari är OS X- och iOS-webbläsare.

Om videon inte kan köras på Safari körs den inte heller i OS X- och iOS-spelare. Det här problemet är troligen ett kodningsproblem och videon måste kodas om.

Så här använder du ett DAM-arbetsflöde för att skapa FullHD-renderingar:

1. Navigera till *arbetsflödesmodelladministratören* som är `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Klicka på modellen **Screens Update Asset**.
1. Klicka på **Starta arbetsflöde** i åtgärdsfältet.
1. I dialogrutan **Kör arbetsflöde** klickar du på videoresursen i **nyttolasten**.
1. Klicka på **Kör**.

>[!NOTE]
>
>Ge lite tid åt att skapa återgivningarna, men efter några sekunder/minuter (beroende på videostorleken) kan du läsa in webbspelaren på Safari igen.

#### Felsökning av flaggan för automatisk uppspelningsprincip {#troubleshooting-autoplay-policy-flag}

Om AEM Screens Player hämtar videon men inte visar den felsöker du flaggan för automatisk uppspelningsprincip.

Följ stegen nedan för att felsöka Google problem med automatisk uppspelningspolicy:

1. Navigera till ***chrome://flags/#autoplay-policy***
1. Ändra **principen för automatisk uppspelning** från **Standard** till **ingen användargest krävs**

1. Starta om webbläsaren och uppdatera spelaren

>[!NOTE]
>
>Läs mer om de bästa sätten att skapa bra användarupplevelser med de nya automatiska spelreglerna i Chrome. Se *Principändringar automatiskt* på `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Synkronisera video mellan flera spelare {#syncing-video-across-multiple-players}

Om du vill spela upp videofilmer synkront på flera enheter bör du använda den absoluta strategin för den sekvens videon är en del av.

#### Krav {#requirements}

* identiska 2+ spelare
* idealisk maskinvara
* identisk nätverkstopologi (spelare är anslutna till en NTP-server som justerar sina interna systemklockor)

#### Ställa in den absoluta strategin {#setting-up-the-absolute-strategy}

Den absoluta strategin:

* Beräknar en fästpunktstid (midnatt den aktuella dagen).
* Beräknar sekvensens varaktighet (summan av längden för alla dess objekt).
* När som helst beräknas vilket objekt som ska spelas upp och nästa objekt genom att sekvensen _remain_time = (current_time - anchor_time) % sequence_duration löses.

Följ stegen nedan för att konfigurera en absolut strategi:

1. Navigera till kanalförfattaren och klicka på sekvenskomponenten så som visas i bilden nedan.
1. Öppna konfigurationsdialogrutan.
1. Redigera **strategin** och lägg till absolut.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >Spelarnas operativsystem måste ha samma klocka.

**Justera klockor i OS X** Följ stegen nedan för att justera klockorna i OS X:

1. Öppna inställningarna för **Datum och tid** i varje OS X-ruta
1. Kontrollera **Ange datum och tid automatiskt**
1. Klistra in värde 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com i listrutan eller kör *sudo ntpdate -u -v 0.pool.ntp.org*
1. Starta 2+ spelare

Det kan ta en stund innan spelarna startar en ny, justerad sekvens.
