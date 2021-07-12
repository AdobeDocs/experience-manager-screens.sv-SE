---
title: Konfigurera åtkomstkontrollistor
seo-title: Konfigurera åtkomstkontrollistor
description: Följ den här sidan om du vill lära dig att dela upp projekt med hjälp av åtkomstkontrollistor så att varje enskild person eller grupp hanterar sitt eget projekt.
seo-description: Följ den här sidan om du vill lära dig att dela upp projekt med hjälp av åtkomstkontrollistor så att varje enskild person eller grupp hanterar sitt eget projekt.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Administrera skärmar
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Konfigurera åtkomstkontrollistor {#setting-up-acls}

I följande avsnitt beskrivs hur du skiljer ut projekt med hjälp av åtkomstkontrollistor så att varje enskild person eller grupp hanterar sitt eget projekt.

Som AEM vill du se till att teammedlemmar i ett projekt inte stör andra projekt och att alla användare tilldelas specifika roller enligt projektkraven.

## Konfigurera behörigheter {#setting-up-permissions}

I följande steg sammanfattas proceduren för att konfigurera åtkomstkontrollistor för ett projekt:

1. Logga in på AEM och navigera till **Verktyg** > **Säkerhet**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Klicka på **Grupper** och ange ett ID (till exempel Acme).

   Du kan också använda den här länken, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Klicka sedan på **Spara**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Välj **Deltagare** i listan och dubbelklicka på den.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Lägg till **Acme** (projekt du skapade) i **Lägg till medlemmar i grupp**. Klicka på **Spara**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Om du vill att projektgruppsmedlemmar ska registrera spelare (vilket innebär att en användare skapas för varje spelare), söker du efter gruppanvändaradministratörerna och lägger till ACME-gruppen i användaradministratörerna

1. Lägg till alla användare som ska arbeta med **Acme**-projektet i **Acme**-gruppen.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Konfigurera behörigheter för gruppen **Acme** med denna `(http://localhost:4502/useradmin)`.

   Markera gruppen **Acme** och klicka på **behörigheten**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Behörigheter {#permissions}

I följande tabell sammanfattas sökvägen med behörigheter på projektnivå:

| **Bana** | **Behörighet** | **Beskrivning** |
|---|---|---|
| `/apps/<project>` | LÄS | Ger åtkomst till projektfiler (om tillämpligt) |
| `/content/dam/<project>` | ALLA | Ger åtkomst till att lagra projektresurser som bilder eller video i DAM |
| `/content/screens/<project>` | ALLA | Tar bort åtkomst till alla andra projekt under /content/screens |
| `/content/screens/svc` | LÄS | Ger åtkomst till registreringstjänsten |
| `/libs/screens` | LÄS | Ger åtkomst till DCC |
| `/var/contentsync/content/screens/` | ALLA | Tillåter att offlineinnehåll för projektet uppdateras |

>[!NOTE]
>
>I vissa fall kan du separera författarfunktioner (som att hantera resurser och skapa kanaler) från administratörsfunktioner (som att registrera spelare). I ett sådant scenario skapar du två grupper och lägger till gruppen författare till medverkande och administratörsgruppen till både medverkande och användare-administratörer.

### Skapa grupper {#creating-groups}

När du skapar ett nytt projekt bör du även skapa standardanvändargrupper med en grundläggande uppsättning behörigheter. Du bör utöka behörigheterna till de typiska roller vi har för AEM Screens.

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
   <td>Skärmadministratörer<br /> <em>screens-admins</em></td>
   <td>Åtkomst på administratörsnivå till AEM Screens-funktioner</td>
   <td>
    <ul>
     <li>Medverkande medlem</li>
     <li>Medlem av användaradministratörer</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Skärmanvändare<br /> <em>screens-users</em></td>
   <td>Skapa och uppdatera kanaler och tidsplaner och tilldela till platser i AEM Screens</td>
   <td>
    <ul>
     <li>Medverkande medlem</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Skärmoperatorer<br /> <em>screens-operatorer</em></td>
   <td>Skapa och uppdatera platsstruktur och registrera spelare i AEM Screens</td>
   <td>
    <ul>
     <li>Medverkande medlem</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Skärmspelare<br /> <em>skärmar-&lt;project&gt;-devices</em></td>
   <td>Grupperar alla spelare och alla spelare/enheter automatiskt.</td>
   <td><p> Medverkande medlem</p> </td>
  </tr>
 </tbody>
</table>
