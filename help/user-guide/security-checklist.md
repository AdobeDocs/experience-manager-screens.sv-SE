---
title: Säkerhetschecklista
description: Läs mer om AEM Screens säkerhetsområden med en checklista med frågor och överväganden.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: ba5327077e4a2d30cc7b77f02123da5a240c67ae
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# AEM Screens Security Checklist  {#security-checklist}

Sidan AEM Screens Security Checklist beskriver de viktigaste säkerhetsområdena med en checklista med frågor och överväganden.

## Checklistetabell {#checklist-table}

| **Säkerhetsområde** | **Checklista** | **Ja/Nej/NA** |
|---|---|---|
| **AEM och skärmar - programuppdateringar** | **a.** *Har det senaste Adobe Experience Manager (AEM) Service Pack tillämpats?* <br>**b.** *Har det senaste AEM Screens-funktionspaketet installerats?* <br>**c.** *Använder du den senaste tillgängliga AEM Screens Player-programvaran från [AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/)?* |
| **Fysisk säkerhet** | **a.** *Har du inaktiverat alla onödiga portar?* <br>**b.** *Har du säkrat kablar och maskinvara?* <br>**c.** *Använder du några behållare om tillämpligt?* |
| **Nätverkssäkerhet** | **a.** *Använder du ett isolerat undernät för dina signeringsenheter?* <br>**b.** *Tillåter det isolerade undernätet åtkomst till de slutpunkter som krävs, inklusive AEM, Adobe Analytics eller andra obligatoriska tjänster?* <br>**c.** *Har du säkrat ditt Wi-Fi med bästa praxis för företag?* <br>**d.** *Om synkroniserad uppspelning används, har du bara tillåtit TCP 24503 för WebSocket på de primära enheterna?* <br>**e.** *Har du låst upp intervallet med IP-adresser för spelarenheterna så att bara behöriga enheter kan komma åt registreringstjänsten på redigeringsinstansen?* |
| **Säkerhet för operativsystem** | **a.** *Har du uppgraderat till den senaste versionen av operativsystemet och använt alla nödvändiga säkerhetsuppdateringar?* <br>**b.** *Har du inaktiverat alla onödiga tjänster och tagit bort onödiga program?* <br>**c.** *Har ni registrerat enheten i enhetshantering för att tillämpa företagets principer?* <br>**d.** *Har du låst enheten till en enda programkioskdator (spelare)?* <br>**e.** *Har du några standardprocedurer (SOP) för installation av säkerhetsuppdateringar för operativsystemet?*<br>**f.***Har du följt de bästa säkerhetsrutinerna för det operativsystem som används, till exempel program mot skadlig kod och icke-administrativa användare?* |
| **Programsäkerhet** | **a.** *Har du inaktiverat användargränssnittet för administratörer, kanalväljare och aktivitetsgränssnittet för produktion?* <br>**b.** *Har du minimerat loggnivån för produktion?* <br>**c.** *Använder du https för att ansluta till AEM?* <br>**d.** *Använder du ett CA-signerat certifikat eller ett företags-PKI? (inte självsignerade certifikat)*<br>**e.***Använder du TLS och inte SSL v3?*<br>**f.** *Validerar du registreringstoken på enhet och AEM vid registrering?*<br> **g.** *Har du klassificerat de data som används och att det inte finns någon PII eller PHI på enheten?*<br> **h.** *Har du klassificerat de data som används och att det inte finns någon personligt identifierbar information (PII) eller skyddad hälsoinformation (PHI) på enheten?*<br> **i.** *Har du konfigurerat övervakning av e-postmeddelanden och har du någon SOP för att svara på övervakning av e-postmeddelanden och hantering av icke-pingande enheter?* |
| **Åtkomstkontroll** | **a.** *Har du en rollbaserad åtkomstkontroll (RBAC) som identifieras och hanteras internt?* <br>**b.** *Har ni följt principen om minst privilegium att ge författare, administratörer och spelare tillgång till bästa praxis från Adobe?* |

### Hämtar checklista för säkerhet {#download-checklist}

Om du vill hämta checklistan för AEM Screens-säkerhet klickar du på [här](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
