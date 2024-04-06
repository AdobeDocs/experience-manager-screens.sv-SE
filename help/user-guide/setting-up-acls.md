---
title: Konfigurera åtkomstkontrollistor
description: Lär dig hur du skiljer ut projekt med hjälp av åtkomstkontrollistor så att varje enskild person eller grupp hanterar sitt eget projekt.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Konfigurera åtkomstkontrollistor {#setting-up-acls}

I följande avsnitt beskrivs hur du skiljer ut projekt med hjälp av åtkomstkontrollistor så att varje enskild person eller grupp hanterar sitt eget projekt.

Som AEM vill du se till att teammedlemmar i ett projekt inte stör andra projekt och att alla användare tilldelas specifika roller enligt projektkraven.

## Konfigurera behörigheter {#setting-up-permissions}

I följande steg sammanfattas proceduren för att konfigurera åtkomstkontrollistor för ett projekt:

1. Logga in på AEM och navigera till **verktyg** > **Säkerhet**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Klicka **Grupper** och ange ett ID (till exempel Acme).

   Du kan även använda den här länken, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Nästa, välj **Spara**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Välj **Medarbetare** i listan och dubbelklicka på den.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Lägg till **Acme** (projekt som du har skapat) till **Lägg till medlemmar i grupp**. Klicka **Spara**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Om du vill att projektgruppsmedlemmar ska registrera spelare (vilket innebär att en användare skapas för varje spelare), söker du efter gruppanvändaradministratörerna och lägger till ACME-gruppen i användaradministratörerna

1. Lägg till alla användare som arbetar med **Acme** Projekt till **Acme** grupp.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Ange behörigheter för gruppen **Acme** använda `(http://localhost:4502/useradmin)`.

   Markera gruppen **Acme** och klicka på **behörigheter**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Behörigheter {#permissions}

I följande tabell sammanfattas sökvägen med behörigheter på projektnivå:

| **Bana** | **Behörighet** | **Beskrivning** |
|---|---|---|
| `/apps/<project>` | LÄS | Ger tillgång till projektfiler, om tillämpligt. |
| `/content/dam/<project>` | ALLA | Ger åtkomst till att lagra projektresurser som bilder eller video i DAM. |
| `/content/screens/<project>` | ALLA | Tar bort åtkomst till alla andra projekt under /content/screens. |
| `/content/screens/svc` | LÄS | Ger åtkomst till registreringstjänsten. |
| `/libs/screens` | LÄS | Ger åtkomst till DCC. |
| `/var/contentsync/content/screens/` | ALLA | Gör att du kan uppdatera offlineinnehåll för projektet. |

>[!NOTE]
>
>Ibland kan du separera författarfunktioner (som att hantera resurser och skapa kanaler) från administratörsfunktioner (som att registrera spelare). I ett sådant scenario skapar du två grupper och lägger till gruppen författare till medverkande och administratörsgruppen till både medverkande och användare-administratörer.

### Skapa grupper {#creating-groups}

När du skapar ett projekt bör du även skapa standardanvändargrupper med en grundläggande uppsättning behörigheter. Utöka behörigheterna till de vanliga rollerna som definieras i AEM Screens.

Du kan till exempel skapa följande projektspecifika grupper:

* Skärmar projektadministratörer
* Skärmar Projektledare (registrera spelare och hantera platser och enheter)
* Skärmar Projektanvändare (arbeta med kanaler, scheman och kanaltilldelningar)

I följande tabell sammanfattas grupperna med beskrivning och behörighet för ett AEM Screens-projekt:

<table>
 <tbody>
  <tr>
   <td><strong>Gruppnamn</strong></td>
   <td><strong>Beskrivning</strong></td>
   <td><strong>Behörigheter</strong></td>
  </tr>
  <tr>
   <td>Skärmadministratörer<br /> <em>skärmadministratörer</em></td>
   <td>Åtkomst på administratörsnivå till AEM Screens-funktioner</td>
   <td>
    <ul>
     <li>Medverkande</li>
     <li>Medlem av användaradministratörer</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Skärmanvändare<br /> <em>skärmanvändare</em></td>
   <td>Skapa och uppdatera kanaler och tidsplaner och tilldela till platser i AEM Screens</td>
   <td>
    <ul>
     <li>Medverkande</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Skärmoperatorer<br /> <em>skärmoperatorer</em></td>
   <td>Skapa och uppdatera platsstruktur och registrera spelare i AEM Screens</td>
   <td>
    <ul>
     <li>Medverkande</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Skärmspelare<br /> <em>skärmar-&lt;project&gt;-devices</em></td>
   <td>Grupperar alla spelare och alla spelare/enheter automatiskt.</td>
   <td><p> Medverkande</p> </td>
  </tr>
 </tbody>
</table>
