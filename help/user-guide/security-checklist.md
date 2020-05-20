---
title: Säkerhetschecklista
seo-title: Säkerhetschecklista
description: Sidan beskriver checklistan för säkerhet
seo-description: Sidan beskriver checklistan för säkerhet
translation-type: tm+mt
source-git-commit: aade9071cebddf147dfad51d7319fb6f0e1c22bf
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# AEM Screens Security Checklist  {#security-checklist}

Sidan AEM Screens Security Checklist beskriver de viktigaste säkerhetsområdena med en checklista med frågor och överväganden.

## Checklistetabell {#checklist-table}

| **Säkerhetsområde** | **Checklista** | **Ja/Nej/NA** |
|---|---|---|
| **Uppdateringar av AEM och skärmar** | ***a.*** *Har det senaste AEM-Service Pack (Adobe Experience Manager) tillämpats?* <br>***b.****Har det senaste AEM Screens-funktionspaketet installerats?*<br>***c.*** *Använder du den senaste tillgängliga versionen av AEM Screens Player från[AEM Screens Player Downloads](https://download.macromedia.com/screens/)?* |
| **Fysisk säkerhet** | ***a.*** *Har du inaktiverat alla onödiga portar?* <br>***b.****Har du säkrat kablar och maskinvara?*<br>***c.*** *Använder du några behållare om tillämpligt?* |
| **Nätverkssäkerhet** | ***a.*** *Använder du ett isolerat undernät för dina signeringsenheter?* <br>***b.****Tillåter det isolerade undernätet åtkomst till de slutpunkter som krävs, inklusive AEM, Adobe Analytics eller andra obligatoriska tjänster?*<br>***c.*** *Har du säkrat ditt Wi-Fi med bästa praxis för företag?* <br>***d.****Om synkroniserad uppspelning används, har du bara tillåtit TCP 24503 för WebSocket på huvudenheterna?*<br>***e.*** *Har du vitlistat IP-intervallen för spelarenheterna så att bara behöriga enheter kan komma åt registreringstjänsten på författaren?* |
| **Säkerhet för operativsystem** | ***a.*** *Har du uppgraderat till den senaste versionen av operativsystemet och använt alla nödvändiga säkerhetsuppdateringar?* <br>***b.****Har du inaktiverat alla onödiga tjänster och tagit bort onödiga program?*<br>***c.*** *Har ni registrerat enheten i enhetshantering för att tillämpa företagets principer?* <br>***d.****Har du låst enheten till en enda programkioskdator (spelare)?*<br>***e.*** *Har du några standardprocedurer (SOP) för installation av säkerhetsuppdateringar för operativsystemet?*<br>***f.****Har du följt de bästa säkerhetsrutinerna för det operativsystem som används, till exempel program mot skadlig kod och icke-administrativa användare?* |
| **Programsäkerhet** | ***a.*** *Har du inaktiverat användargränssnittet för administratörer, kanalväljare och aktivitetsgränssnitt för produktion?* <br>***b.****Har du minimerat loggnivån för produktion?*<br>***c.*** *Använder du https för att ansluta till AEM?* <br>***d.****Använder du ett CA-signerat certifikat eller ett företags-PKI? (inte självsignerade certifikat)*<br>***e.**** Använder du TLS och inte SSL v3?*<br>*** f.****Validerar du registreringstoken på enheten och AEM vid registrering?*<br> ***g.*** *Har du klassificerat de data som används och att det inte finns någon PII eller PHI på enheten?*<br> ***h.*** *Har du klassificerat de data som används och att det inte finns någon personligt identifierbar information (PII) eller skyddad hälsoinformation (PHI) på enheten?*<br> ***i.*** *Har du konfigurerat övervakning av e-postmeddelanden och har du någon SOP för att svara på övervakning av e-postmeddelanden och hantering av icke-pingande enheter?* |
| **Åtkomstkontroll** | ***a.*** *Har du en RBAC (Role Based Access Control) identifierad och hanterad internt?* <br>***b.****Har ni följt principen om minst privilegium att ge författare, administratörer och spelare tillgång till Adobes bästa praxis?* |

### Hämtar checklista för säkerhet {#download-checklist}

Klicka [här](/help/user-guide/assets/Screens-Security-Checklist.pdf)om du vill hämta säkerhetschecklistan för AEM-skärmar.



