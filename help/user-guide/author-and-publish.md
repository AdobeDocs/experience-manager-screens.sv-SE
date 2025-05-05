---
title: Konfigurera författare och Publish-instanser i AEM Screens
description: Lär dig hur du konfigurerar en Author-instans och en Publish-instans för AEM Screens.
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '1940'
ht-degree: 0%

---


# Konfigurera författare och Publish-instanser i AEM Screens {#configuring-author-and-publish-in-aem-screens}

På den här sidan beskrivs följande ämnen:

* **Konfigurerar författare och Publish-instanser**
* **Konfigurerar Publish Topology**
* **Hantera publikation: Levererar innehållsuppdateringar från författare till Publish till enhet**

## Förutsättningar {#prerequisites}

Innan du börjar använda författare och Publish-servrar bör du ha kännedom om:

* **AEM topologi**
* **Skapa och hantera AEM Screens-projekt**
* **Device Registration Process**

>[!NOTE]
>
>Den här AEM Screens-funktionen är bara tillgänglig om du har AEM 6.4 Screens Feature Pack 2 installerat. Kontakta Adobe Support och begär åtkomst till detta funktionspaket. När du har behörighet kan du hämta den från paketresursen.

>[!IMPORTANT]
>
>Om du vill använda mer än en Publish-instans med Dispatcher uppdaterar du Dispatcher. Se [Aktivera anteckningssessioner](dispatcher-configurations-aem-screens.md#enable-sticky-session).

## Konfigurera författare och Publish-instanser {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Mer information om översikten över författaren och Publish-arkitekturen och hur innehållet skapas i en AEM författarinstans och sedan replikeras vidare till flera Publish-instanser finns i [Författaröversikt och Publish-översiktsöversikt](author-publish-architecture-overview.md).

I följande avsnitt beskrivs hur du konfigurerar replikeringsagenter i topologin för författare och Publish.

Du kan skapa ett enkelt exempel där du har en författare och två Publish-instanser:

* Författare > localhost:4502
* Publish 1 (pub1) > localhost:4503
* Publish 2 (pub2) > localhost:4504

## Konfigurera replikeringsagenter på författare {#setting-replication-agents}

Lär dig hur du skapar en standardoperationsagent för replikering när du vill skapa replikeringsagenter.

Det finns tre replikeringsagenter som behövs för Screens:

1. **Standardreplikeringsagent &#x200B;***(anges som&#x200B;*** standardreplikeringsagent**)
1. **Screens Replication Agent**
1. **Agenten för omvänd replikering**

### Steg 1: Skapa en standardreplikeringsagent {#step-creating-a-default-replication-agent}

Följ stegen nedan om du vill skapa en standardsvar för replikering:

1. Navigera till din AEM > hammikon > **Åtgärder** > **Konfiguration**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Klicka på **Replikering** i det vänstra navigeringsträdet.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Klicka på **Agenter på författare** i mappen **Replikering** och klicka på **Nytt** för att skapa en ny standardreplikeringsagent.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Ange **Titel** och **Namn** så att du kan skapa replikeringsagenten och klicka sedan på **Skapa**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Högerklicka på replikeringsagenten och klicka på **Öppna** för att redigera inställningarna.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Klicka på **Redigera**.

1. Ange informationen i dialogrutan **Agentinställningar**.

   >[!NOTE]
   >
   >Användaren måste kontrollera **Aktiverad** för att aktivera replikeringsagenten. Markera det här alternativet för standardagenter, Screens-agenter och omvända replikeringsagenter.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Navigera till fliken **Transport** och ange **URI**, **Användare** och **Lösenord**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Du kan också kopiera och byta namn på en befintlig standardreplikeringsagent.


#### Skapar standardreplikeringsagenter {#creating-standard-replication-agents}

1. Skapa en standardreplikeringsagent för pub1 (en standardagent som inte är installerad bör redan vara konfigurerad). Exempel: *`https://<hostname>:4503/bin/receive?sling:authRequestLogin=1`*
1. Skapa en standardreplikeringsagent för pub2. Du kan kopiera som replikeringsagent för pub1 och uppdatera transporten som ska användas för pub2 genom att ändra porten i transportkonfigurationen. Exempel: *`https://<hostname>:4504/bin/receive?sling:authRequestLogin=1`*.

#### Skapar Screens Replication Agents {#creating-screens-replication-agents}

1. Skapa en AEM Screens-replikeringsagent för pub1. Det finns en färdig Screens-replikeringsagent som pekar på port 4503. Aktivera det.
1. Skapa en AEM Screens-replikeringsagent för pub2. Kopiera Screens replikeringsagent för pub1 och ändra porten till 4504 för pub2.

   >[!NOTE]
   >Mer information om hur du konfigurerar Screens replikeringsagenter finns i [Konfigurera Screens Replication Agent](https://experienceleague.adobe.com/sv/docs/experience-manager-screens/user-guide/administering/configure-screens-replication).

#### Skapar omvända replikeringsagenter för Screens {#creating-screens-reverse-replication-agents}

1. Skapa en omvänd replikeringsagent för pub1.
1. Skapa en omvänd replikeringsagent för pub2. Du kan kopiera den omvända replikeringsagenten för pub1 och uppdatera transporten som ska användas för pub2 genom att ändra porten i transportkonfigurationen.

## Konfigurera Publish Topology {#setting-up-publish-topology}

### Steg 1: Konfigurera Apache Sling Oak-baserad identifiering {#step-configure-apache-sling-oak-based-discovery}

Konfigurera Apache Sling Oak-baserad Discovery för alla Publish-instanser i topologin

För varje Publish-instans:

1. Navigera till `https://<host>:<port>/system/console/configMgr`
1. Klicka på **Konfiguration av Apache Sling Oak-baserad Discovery Service**.
1. Uppdatera topologianslutnings-URL:er: lägg till URL:er för alla parsande Publish-instanser som är:
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **Topologianslutning `Whitelist` Lista**: Anpassa till IP-adresser eller undernät som omfattar alla Publish-instanser. Kontrollera att du `whitelist` IP-/värdnamnet för alla Publish-instanser utan portnumret.

1. Aktivera **Stoppa lokala loopar automatiskt**

Konfigurationen ska vara identisk för varje Publish-instans och Local-loopen som automatiskt stoppar förhindrar en oändlig slinga.

#### Steg 2: Verifiera Publish Topology {#step-verify-publish-topology}

Navigera till `https://:/system/console/topology` för alla Publish-instanser. Du bör se varje Publish-instans representeras i topologin under **Utgående topologianslutningar**.

#### Steg 3: Konfigurera ActiveMQ-objektkluster {#step-setup-activemq-artemis-cluster}

I det här steget kan du skapa ett krypterat lösenord för ActiveMQ Artemis-klustret.
Klusteranvändaren och lösenordet för alla Publish-instanser i topologin måste vara identiska. Lösenordet för ActiveMQ Artemis-konfigurationen måste vara krypterat. Eftersom varje instans har en egen krypteringsnyckel måste du använda krypteringsstöd för att skapa en krypterad lösenordssträng. Sedan kan det krypterade lösenordet användas i OSGi-konfigurationen för ActiveMQ.

På varje Publish-instans:

1. I OSGi-konsolen går du till **MAIN** > **Crypto Support** (`https://<host>:<port>/system/console/crypto`).
1. Skriv det lösenord för oformaterad text (samma för alla förekomster) i **Oformaterad text**
1. Klicka på **Protect**.
1. Kopiera värdet **Skyddad text** till ett anteckningsblock eller en textredigerare. Det här värdet kan användas i OSGi-konfigurationen för ActiveMQ.

Eftersom varje Publish-instans som standard har unika krypteringsnycklar utför du det här steget på varje pub-instans och sparar den unika nyckeln för nästa konfiguration.

>[!NOTE]
>
>Lösenordet ska börja och sluta med klammerparenteser. Till exempel:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Steg 4: Aktivera ActiveMQ-artemis-kluster {#step-activate-activemq-artemis-cluster}

På varje publiceringsinstans:

1. Navigera till OSGi Config-hanteraren `https://<host>:<port>/system/console/configMgr`
1. Klicka på **Konfiguration för Apache ActiveMQ Artemis JMS Provider**
1. Uppdatera följande:

   * ***Klusterlösenord***: använd krypterat värde från föregående steg per instans
   * ***Ämnen***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verifiera ActiveMQ-objektkluster {#verify-activemq-artemis-cluster}

Följ stegen nedan för varje Publish-instans:

1. Navigera till OSGi Console > Main > ActiveMQ Artemis `https://localhost:4505/system/console/mq`.
1. Verifiera och kontrollera om du vill visa portar för andra instanser under Klusterinformation > Topologi > noder=2, members=2.
1. Skicka ett testmeddelande (högst upp på skärmen under Information om mäklare)
1. Ange följande ändringar i fält:

   1. **Mål**: /com.adobe.cq.screens/devTestTopic
   1. **Text**: Hello World
   1. Visa `error.log` för varje instans så att du kan se att meddelandet skickades och togs emot i klustret.

>[!NOTE]
>
>Det kan ta några sekunder att navigera till OSGi Console efter att konfigurationen har sparats i föregående steg. Du kan också kontrollera error.log för mer information.

Följande bild visas till exempel när ActiveMQ Artemis Server har konfigurerats.

Om du inte ser följande konfiguration från */system/console/mq* går du till */system/console/mq* och klickar på **Starta om** för att starta om mäklaren.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Ta bort krav på referensrubrik {#remove-referrer-header-requirement}

Följ stegen i varje Publish-instans:

1. Navigera till **OSGi-konsolen** > **Configuration Manager**
1. Klicka på **Refererarfilter för Apache Sling**
1. Uppdatera konfigurationen och **markera Tillåt tomt**

### Konfigurera författare och Publish-instans {#configuring-author-and-publish-instance}

När du har konfigurerat publiceringstopologin ska du konfigurera författaren och Publish-instanserna så att de praktiska resultaten av implementeringen visas:

>[!NOTE]
>
>**Förutsättningar**
>
>För att komma igång med det här exemplet skapar du ett AEM Screens-projekt följt av att du skapar en plats, visning och kanal i ditt projekt. Lägg till innehåll i kanalen och tilldela kanalen till en skärm.

#### Steg 1: Starta en AEM Screens Player (enhet)

1. Starta ett separat webbläsarfönster.
1. Gå till Screens Player med *webbläsaren*, det vill säga `https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html`, eller starta AEM Screens-appen. När du öppnar enheten bör du observera att enhetens status är oregistrerad.

>[!NOTE]
>
>Du kan öppna en AEM Screens Player med den AEM Screens-app du har laddat ned eller med webbläsaren.

#### Steg 2: Registrera en enhet på författaren {#step-registering-a-device-on-author}

1. Gå till `https://localhost:4502/screens.html/content/screens/we-retail` eller klicka på projektet och gå till Enheter > Enhetshanteraren.
1. Klicka på **Registrera enhet**.
1. Klicka på **Enhetsregistrering**.
1. Klicka på den enhet som du vill registrera och klicka sedan på **Registrera enhet**.
1. Verifiera registreringskoden och klicka sedan på **Validera**.
1. Ange en rubrik för enheten och klicka sedan på **Registrera**.

#### Steg 3: Tilldela enheten till visning {#step-assigning-the-device-to-display}

1. Klicka på **Tilldela visning** i dialogrutan från föregående steg.
1. Klicka på kanalens visningssökväg i mappen **Platser**.
1. Klicka på **Tilldela**.
1. Klicka på **Slutför** för att slutföra processen, och nu tilldelas enheten.

Kontrollera spelaren och lägg märke till innehållet som du har lagt till i kanalen.

#### Steg 4: Publicera enhetskonfiguration till Publish-instanser {#step-publishing-device-configuration-to-publish-instances}

**Verifierar enheten**

Så här replikerar du enhetsanvändaren:

1. Gå till sidan för användaradministration. Exempel: `https://localhost:4502/useradmin`.
1. Sök efter gruppen **`screens-devices-master`**.
1. Högerklicka på gruppen och klicka på **Aktivera**.

>[!CAUTION]
>
>Aktivera inte författaren-publish-screens-service eftersom det är en systemanvändare som används av författarjobbet.

Du kan även aktivera enheten från enhetshanteringskonsolen. Följ stegen nedan:

1. Gå till ditt Screens-projekt > **Enheter**.
1. Klicka på **Enhetshanteraren** i åtgärdsfältet.
1. Klicka på enheten och klicka på **Aktivera** i åtgärdsfältet enligt bilden nedan.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>När du har aktiverat enheten kan du även redigera eller uppdatera serverns URL. Klicka på **Redigera server-URL** i åtgärdsfältet, så som visas i bilden nedan. Ändringarna sprids till AEM Screens Player.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Publiceringskontrolllista {#publishing-check-list}

Följande punkter sammanfattar publiceringskontrolllistan:

* *Screens Device User* - Den här informationen lagras som en AEM användare och kan aktiveras från **Tools** > **Security** > **Users**. Användaren har prefixet&quot;screens&quot; med en lång serialiserad sträng.

* *Projekt* - AEM Screens-projektet.
* *Plats* - Plats som enheten är ansluten till.
* *Kanaler* - en eller flera kanaler som visas på platsen.
* *Schema* - Om du använder ett schema måste du se till att schemat publiceras.
* *Plats, Scheman och Kanalmapp* - Om motsvarande resurser finns i en mapp.

Följ stegen nedan för att verifiera hur redigering och publicering fungerar:

1. Uppdatera visst kanalinnehåll på Author-instansen.
1. Utför **Hantera publikation** om du vill publicera nya ändringar i alla Publish-instanser.
1. Tryck på **Aktivera** för att aktivera enheten från **Enhetshanteraren**.
1. Välj **Redigera URL** från författarinstansens URL till en av publiceringsinstansens URL.
1. Kontrollera att det uppdaterade kanalinnehållet visas i AEM Screens Player.
1. Upprepa dessa steg med en annan Publish-instans.


#### Steg 5: Peka enheten mot Publish-instansen på administratörspanelen {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Visa administratörsgränssnittet från Screens Player, tryck länge på det övre vänstra hörnet så att du kan öppna Admin-menyn, AEM Screens Player med pekfunktion eller med en mus.
1. Klicka på alternativet **Konfiguration** på sidopanelen.
1. Ändra författarinstansen till Publish-instansen i **Server**.

Se ändringarna i AEM Screens Player.

Du kan även uppdatera/redigera server-URL:en från enhetshanteringskonsolen genom att följa följande steg:

1. Navigera till ditt AEM Screens-projekt och klicka på mappen **Enheter** .
1. Klicka på **Enhetshanteraren** i åtgärdsfältet.
1. Klicka på enheten och klicka sedan på **Redigera server-URL** i åtgärdsfältet, så som visas i bilden nedan. Ändringarna sprids till AEM Screens Player.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

Med funktionen **Hantera publikation** kan du leverera innehållsuppdateringar från författare till Publish till enhet. Du kan publicera/avpublicera innehåll för hela AEM Screens-projektet eller bara för en av dina kanaler, platser, enheter, program eller scheman. Mer information om den här funktionen finns i [Uppdatera innehåll på begäran](on-demand-content.md).

## Felsökning - tips {#troubleshoot-tips}

Följ avsnittet nedan för att få svar på vanliga frågor om författaren/Publish-konfigurationen.

### Hur lägger jag till en omdirigering från https till http efter den första registreringen och tilldelningen? {#add-redirect}

**Lösning**
Ange Aktivera `Proxy/Load Balancer Connection in the Jetty configuration` till `true`.

### Hur uppdaterar jag offlineinnehåll och problem med hämtning av spelare med resurser utanför `/content/dam/projects/<project>`? {#update-offline-content}

**Lösning**
Om du vill vara mer restriktiv ger du läsbehörighet för användare som har massvis-offline-uppdatering-screens-service och `screens-devices-master` grupp för alla `/content/dam` eller de specifika resurser som du vill använda.

### Hur löser man fel i Screens Replication Agent? {#replication-agent}

**Lösning**
Kontrollera att du inte har markerat Använd för omvänd replikering i agentkonfigurationen. Screens replikeringsagent kan inte användas som en omvänd replikeringsagent och omfattningen av den här funktionen är att vidarebefordra enhetskommandon från författare till Publish.