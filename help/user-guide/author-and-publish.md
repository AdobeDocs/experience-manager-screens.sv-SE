---
title: Konfigurera författare och publicera på AEM-skärmar
seo-title: Konfigurera författare och publicera på AEM-skärmar
description: AEM Screens-arkitekturen liknar en traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM-författarinstans och sedan vidarebefordras till flera publiceringsinstanser. Följ den här sidan för att lära dig hur du konfigurerar författare och publicerar för AEM-skärmar.
seo-description: AEM Screens-arkitekturen liknar en traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM-författarinstans och sedan vidarebefordras till flera publiceringsinstanser. Följ den här sidan för att lära dig hur du konfigurerar författare och publicerar för AEM-skärmar.
uuid: 0a6e87e7-0018-42ef-b484-9a3da61c636a
contentOwner: jsyal
content-type: reference
topic-tags: authoring
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: f2397d11-a18b-4779-b77b-5f99b797f40c
docset: aem65
translation-type: tm+mt
source-git-commit: 161eef6e7e45393f345240b9c36a104a18106f12

---


# Konfigurera författare och publicera på AEM-skärmar {#configuring-author-and-publish-in-aem-screens}

På den här sidan beskrivs följande ämnen:

* **Konfigurera författare- och publiceringsinstanser**
* **Konfigurera publiceringstopologi**
* **Hantera publikation: Leverera innehållsuppdateringar från författare till enhet**

## Förutsättningar {#prerequisites}

Innan du börjar med författare och publiceringsservrar bör du ha kunskap om:

* **AEM Topology**
* **Skapa och hantera AEM-skärmsprojekt**
* **Enhetsregistreringsprocess**

>[!NOTE]
>
>Den här AEM-skärmfunktionen är bara tillgänglig om du har installerat AEM 6.4 Screens Feature Pack 2. Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobes support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

## Konfigurera författare- och publiceringsinstanser {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Om du vill veta mer om författaren och publiceringen av en arkitekturöversikt och hur innehållet skapas på en AEM-författarinstans och sedan vidarebefordras till flera publiceringsinstanser, se Översikt över [](author-publish-architecture-overview.md)författare och publiceringsarkitektur.

I följande avsnitt beskrivs hur du konfigurerar replikeringsagenter för författare och publiceringstopologi.

Du kan skapa ett enkelt exempel där du är värd för en författare och två publiceringsinstanser:

* Författare —> localhost:4502
* Publish 1 (pub1) —> localhost:4503
* Publish 2 (pub2) —> localhost:4504

## Konfigurera replikeringsagenter på författare {#setting-replication-agents}

Om du vill skapa replikeringsagenter måste du lära dig hur du skapar en standardredigeringsagent.

Det finns tre replikeringsagenter som behövs för skärmar:

1. **Standardreplikeringsagent ***(anges som***standardreplikeringsagent**)
1. **Raster Replication Agent**
1. **Agenten för omvänd replikering**

### Steg 1: Skapar en standardsreplikeringsagent {#step-creating-a-default-replication-agent}

Följ stegen nedan om du vill skapa en standardsvar för replikering:

1. Navigera till din AEM-instans —> hammer-ikon —> **Åtgärder** —> **Konfiguration**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Välj **Replikering** i det vänstra navigeringsträdet.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Välj **agenter på författaren** i mappen **Replication** och klicka på **New** för att skapa en ny standardslikeringsagent.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Ange **titel** och **namn** för att skapa replikeringsagenten och klicka på **Skapa**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Högerklicka på replikeringsagenten och klicka på **Öppna** för att redigera inställningarna.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Klicka på **Redigera** för att öppna dialogrutan **Agentinställningar** och ange informationen.

   >[!NOTE]
   >
   >Användaren måste kontrollera **aktiverad** för att kunna aktivera replikeringsagenten. Du måste markera det här alternativet för standardagenter, skärmar och agenter för omvänd replikering.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Navigera till fliken **Transport** och ange **URI**, **Användare** och **Lösenord**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Du kan också kopiera och byta namn på en befintlig standardreplikeringsagent.


#### Skapar standardreplikeringsagenter {#creating-standard-replication-agents}

1. Skapa en standardobjektreplikeringsagent för pub1 (standardagenten som är färdig bör redan vara konfigurerad) (till exempel *https://&lt;värdnamn>:4503/bin/receive?sling:authRequestLogin=1*)
1. Skapa en standardslikeringsagent för pub2. Du kan kopiera rep agent för pub1 och uppdatera transporten som ska användas för pub2 genom att ändra porten i transportkonfigurationen. (till exempel *https://&lt;värdnamn>:4504/bin/receive?sling:authRequestLogin=1*)

#### Skapar agenter för skärmreplikering {#creating-screens-replication-agents}

1. Skapa AEM Screens-replikeringsagent för pub1. Det finns en som heter Screens Replication Agent som pekar på port 4503. Detta måste aktiveras.
1. Skapa AEM Screens-replikeringsagent för pub2. Kopiera skärmreplikeringsagenten för pub1 och ändra porten till punkt 4504 för pub2.

#### Skapar agenter för omvänd rasterreplikering {#creating-screens-reverse-replication-agents}

1. Skapa en standardinverterad replikeringsagent för pub1.
1. Skapa en standardinverterad replikeringsagent för pub2. Du kan kopiera omvänd rep-agent för pub1 och uppdatera transporten som ska användas för pub2 genom att ändra porten i transportkonfigurationen.

## Konfigurera publiceringstopologi {#setting-up-publish-topology}

### Steg 1: Konfigurera Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

Konfigurera Apache Sling Oak-Based Discovery för alla publiceringsinstanser i topologin

För varje publiceringsinstans:

1. Navigera till `https://<host>:<port>/system/console/configMgr`
1. Välj **Konfiguration av Apache Sling Oak-Based Discovery Service** .
1. Uppdatera topologianslutnings-URL: lägga till URL:er för alla partakta publiceringsinstanser som är:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. Whitelist för topologikoppling: anpassa sig till IP-adresser eller undernät som omfattar partakta publiceringsinstanser
1. Aktivera **automatiska stopp av lokala loopar**

Konfigurationen ska vara identisk för varje publiceringsinstans och den automatiska stopploopen förhindrar en oändlig slinga.

#### Steg 2: Verifiera publiceringstopologi {#step-verify-publish-topology}

Navigera till någon av publiceringsinstanserna `https://:/system/console/topology`. Du bör se alla publiceringsinstanser som representeras i topologin under **Utgående topologianslutningar**.

#### Steg 3: Konfigurera ActiveMQ-objektkluster {#step-setup-activemq-artemis-cluster}

I det här steget kan du skapa krypterat lösenord för ActiveMQ Artemis-klustret.
Klusteranvändaren och lösenordet för alla publiceringsinstanser i topologin måste vara identiska. Lösenordet för ActiveMQ Artemis-konfigurationen måste krypteras. Eftersom varje instans har en egen krypteringsnyckel måste du använda krypteringsstöd för att skapa en krypterad lösenordssträng. Krypterat lösenord används sedan i OSGi-konfigurationen för ActiveMQ.

På varje publiceringsinstans:

1. I OSGi Console går du till **MAIN** —> **Crypto Support** (*https://&lt;värd>:&lt;port>/system/console/crypto*).
1. Skriv in det önskade lösenordet för oformaterad text (samma för alla förekomster) i **oformaterad text**
1. Klicka på **Skydda**.
1. Kopiera värdet **Skyddad text** till anteckningsrutan eller textredigeraren. Det här värdet används i OSGi-konfigurationen för ActiveMQ.

Eftersom varje publiceringsinstans som standard har unika krypteringsnycklar måste du utföra det här steget på varje pub-instans och spara den unika nyckeln för nästa konfiguration.

>[!NOTE]
>Lösenordet ska börja och sluta med klammerparenteser.
>Exempel:{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a6 10e}

#### Steg 4: Aktivera ActiveMQ Artemis-kluster {#step-activate-activemq-artemis-cluster}

På varje publiceringsinstans:

1. Navigera till OSGi Config-hanteraren *https://&lt;host>:&lt;port>/system/console/configMgr*
1. Välj **konfiguration för ActiveMQ Artemis JMS Provider** för Apache
1. Uppdatera följande:

* ***Klusterlösenord***: (använd krypterat värde från föregående steg per instans)
* ***Avsnitt***: {name: &#39;commands&#39;, adress: &#39;com.adobe.cq.screens.commands&#39;, maxConsumers: 50}

#### Verifiera ActiveMQ-objektkluster {#verify-activemq-artemis-cluster}

Följ stegen nedan för varje publiceringsinstans:

1. Navigera till OSGi Console -> Meny > ActiveMQ Artemis `[https://localhost:4505/system/console/mq`.
1. Verifiera och kontrollera om du vill visa portar för andra instanser under Klusterinformation > Topologi > noder=2, members=2.
1. Skicka ett testmeddelande (högst upp på skärmen under Information om mäklare)
1. Ange följande ändringar i fält:

   1. **Mål**: /com.adobe.cq.screens/devTestTopic
   1. **Text**: Hello World
   1. Visa felet.log för varje instans för att se att meddelandet skickades och togs emot i hela klustret

>[!NOTE]
>
>Navigering till OSGI-konsolen kan ta några sekunder efter att konfigurationen sparats i föregående steg. Du kan också kontrollera error.log för mer information.

Följande bild visas till exempel när ActiveMQ Artemis Server har konfigurerats.

Om du inte ser följande konfiguration från */system/console/mq* går du till */system/console/mq* och klickar på **Starta** om du vill starta om mäklaren.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Ta bort krav på referensrubrik {#remove-referrer-header-requirement}

Följ stegen för varje publiceringsinstans:

1. Navigera till **OSGi-konsolen** > **Configuration Manager**
1. Välj **filtret Apache Sling Referrer**
1. Uppdatera konfiguration och **markera Tillåt tomt**

### Konfigurera författare och publiceringsinstans {#configuring-author-and-publish-instance}

När du har konfigurerat publiceringstologin måste du konfigurera författaren och publiceringsinstanserna för att visa de praktiska resultaten av implementeringen:

>[!NOTE]
>
>**Förutsättningar**
>
>För att komma igång med det här exemplet skapar du ett nytt AEM Screens-projekt följt av att skapa en plats, en skärm och en kanal i projektet. Lägg till innehåll i kanalen och tilldela kanalen till en skärm.

#### Steg 1: Starta en AEM Screens Player (enhet) {#step-starting-an-aem-screens-player-device}

1. Starta ett separat webbläsarfönster.
1. Gå till Skärmspelaren med *webbläsaren*,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` d.v.s. eller starta appen AEM Screens. När du öppnar enheten visas enhetens status som ej registrerad.

>[!NOTE]
>
>Du kan öppna en AEM Screens-spelare med appen AEM Screens som du har laddat ned eller med webbläsaren.

#### Steg 2: Registrera en enhet på författaren {#step-registering-a-device-on-author}

1. Gå till `https://localhost:4502/screens.html/content/screens/we-retail` eller välj projektet och navigera till Enheter > Enhetshanteraren.
1. Välj **Registrera enhet**.
1. Klicka på **Enhetsregistrering** för att visa enheten.
1. Välj den enhet som du vill registrera och klicka på **Registrera enhet**.
1. Verifiera registreringskoden och klicka på **Validera**.
1. Ange en rubrik för enheten och klicka på **Registrera**.

#### Steg 3: Tilldela enheten till visning {#step-assigning-the-device-to-display}

1. Klicka på **Tilldela visning** i dialogrutan i föregående steg.
1. Välj visningssökvägen för kanalen i mappen **Platser** .
1. Klicka på **Tilldela**.
1. Klicka på **Slutför** för att slutföra processen, och nu tilldelas enheten.

Kontrollera spelaren så ser du innehållet som du har lagt till i kanalen.

#### Steg 4: Publicera enhetskonfiguration för publiceringsinstanser {#step-publishing-device-configuration-to-publish-instances}

**Verifiera enheten**

Innan du utför stegen nedan kontrollerar du att enhets-ID är verifierat. Om du vill verifiera söker du efter enhets-ID i CRXDELite, med sökvägen as */home/users/screens/we-retail/devices*.

Så här replikerar du enhetsanvändaren:

1. Gå till sidan för användaradministration (t.ex.: `https://localhost:4502/useradmin`
1. Sök efter **gruppen screens-devices-master**
1. Högerklicka på gruppen och klicka på **Aktivera**

>[!CAUTION]
>
>Aktivera inte författare-publish-screens-service eftersom det är en systemanvändare som används av författarjobbet.

Du kan även aktivera enheten från enhetshanteringskonsolen. Följ stegen nedan:

1. Gå till ditt skärmsprojekt —> **Enheter**.
1. Klicka på **Enhetshanteraren** i åtgärdsfältet.
1. Markera enheten och klicka på **Aktivera** i åtgärdsfältet enligt bilden nedan.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>När du har aktiverat enheten kan du också redigera eller uppdatera server-URL:en genom att klicka på **Redigera server-URL** i åtgärdsfältet, som visas i bilden nedan, så sprids ändringarna till AEM Screens Player.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Publiceringskontrolllista {#publishing-check-list}

Följande punkter sammanfattar publiceringskontrolllistan:

* *Skärmar som enhetsanvändare* - Detta lagras som en AEM-användare och kan aktiveras via **Verktyg** > **Säkerhet** > **Användare**. Användaren får prefixet&quot;screens&quot; med en lång serialiserad sträng.

* *Projekt* - projektet AEM Screens.
* *Plats* - Den plats där enheten är ansluten.
* *Kanaler* - en eller flera kanaler som visas på platsen
* *Schema* - Om du använder ett schema måste du se till att det publiceras
* *Plats, Scheman och Kanalmapp* - om motsvarande resurser finns i en mapp.

Följ stegen nedan för att verifiera författarens/publiceringens beteende:

1. Uppdatera kanalinnehåll i författarinstans
1. Utför **Hantera publikation** för att publicera nya ändringar i alla publiceringsinstanser
1. Tryck på **Aktivera** för att aktivera enheten från **Enhetshanteraren**
1. **Redigera URL** från författarinstansens URL till någon av publiceringsinstansernas URL
1. Verifiera att det uppdaterade kanalinnehållet visas i AEM Screens Player
1. Upprepa dessa steg med en annan publiceringsinstans


#### Steg 5: Peka på enheten för att publicera instansen på Admin-panelen {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Visa administratörsgränssnittet från Skärmspelaren, tryck länge på det övre vänstra hörnet för att öppna Admin-menyn, på din touchaktiverade AEM Screens Player eller med en mus.
1. Klicka på alternativet **Konfiguration** på sidopanelen.
1. Ändra författarinstansen till publiceringsinstansen i **Server**.

Se ändringarna i din AEM Screens Player.

Du kan även uppdatera/redigera server-URL:en från enhetshanteringskonsolen genom att följa följande steg:

1. Navigera till ditt AEM Screens-projekt och välj mappen **Devices** .
1. Klicka på **Enhetshanteraren** i åtgärdsfältet.
1. Markera enheten och klicka på **Redigera server-URL** i åtgärdsfältet, som visas i bilden nedan, så sprids ändringarna till AEM Screens Player.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

Med funktionen **Hantera publikation** kan du leverera innehållsuppdateringar från författare till publicering till enhet. Du kan publicera/avpublicera innehåll för hela AEM Screens-projektet eller bara för en av dina kanaler, platser, enheter, program eller scheman. Mer information om den här funktionen finns i [Innehållsuppdatering](on-demand-content.md)på begäran.


