
# Testanalys och Underlag – Projekt NordicShop

Detta dokument utgör det första underlaget för testarbetet i utvecklingen av den nya e-handelsplattformen. Syftet är att etablera en gemensam bild av testobjekt, kritiska flöden, risker och integrationer inför lanseringsmålet om 4 månader.

---

## 1. Testobjekt & Verifieringsbehov

| Testobjekt | Vad behöver verifieras? | Prioritet |
| :--- | :--- | :--- |
| **NordicShop Webb / Mobilapp** (Funktionalitet) | Kritiska användarflöden: att registrering, sök, varukorg och betalning fungerar tekniskt från start till slut. | **Hög** |
| **NordicShop Webb / Mobilapp** (UI/UX & Design) | Kosmetiskt utseende, layout, färger, typsnitt samt att designen följer Figma-skisser och grafisk profil. | **Låg / Medel** |
| **Backend / Order Service** | Affärslogik, orderhantering, statusuppdateringar, api-anrop och e-post/sms-triggers. | **Hög** |
| **Lagersystem (Integration)** | Att det 15 år gamla systemet synkar lagersaldo korrekt vid köp och avbeställning. | **Hög** |
| **Payment Provider (Integration)** | Säker överföring av betalningsdata, hantering av godkänd/nekad betalning samt kontroll mot dubbeldebitering. | **Hög** |
| **Delivery Provider (Integration)** | Hämtning av korrekta leveransalternativ (hem/ombud) och priser. | **Medel** |
| **E-post / SMS Service (Integration)** | Utskick av order- och avbeställningsbekräftelser med korrekt information. | **Medel** |
| **Administrationsverktyg** | Behörigheter, produkthantering, prisändringar och skapande av rabattkoder. | **Medel** |

---

## 2. Kritiska Affärsflöden (End-to-End)

### Flöde 1: Det lyckade standardköpet (Happy Path)
* **Sekvens:** Kund → Sök/Filtrera produkt → Lägg i kundvagn → Applicera rabattkod → Välj leveransmetod → Genomför Swish/Kortbetalning → Order Service skapar order → Lagersystem uppdateras → E-post skickas.
* **Verksamhetsmål:** Göra det enklare att handla, stödja fler betalalternativ, automatisera lager.
* **System som ingår:** Webb/App, Backend, Payment Provider, Lagersystem, Delivery Provider, E-post/SMS Service.
* **Konsekvens vid fel:** Totalt stopp i försäljningen.
* **Kritikalitet:** **Hög**

### Flöde 2: Avbeställning innan leverans
* **Sekvens:** Kund/Kundservice → Hitta order → Avbryt order → Backend triggar Payment Provider (återbetalning) → Lagersystem (återställ saldo) → Bekräftelse skickas till kund.
* **Verksamhetsmål:** Minska manuellt arbete för kundservice, ge snabbare orderhantering.
* **System som ingår:** Webb/App, Backend, Payment Provider, Lagersystem, E-post/SMS Service.
* **Konsekvens vid fel:** Felaktiga leveranser skickas ut, missnöjda kunder, manuell hantering för kundservice.
* **Kritikalitet:** **Hög**

### Flöde 3: Köp av sista produkten i lager (Gränsfall)
* **Sekvens:** Kund A & B lägger sista varan i kundvagnen samtidigt → Lagersaldo blir 0 → Kund B nekas att lägga vara i varukorgen → Kund B befrågas om den vill få veta om proudukten är i lager igen → Produkten hamnar som "tomt i lagger" och stoppas från att läggas i varukorger.
* **Verksamhetsmål:** Automatisera lageruppdateringar, minska manuellt arbete (felköp).
* **System som ingår:** Webb/App, Backend, Lagersystem.
* **Konsekvens vid fel:** NordicShop säljer produkter som inte finns i lager, vilket leder till restorder och hög belastning på kundservice.
* **Kritikalitet:** **Hög**

### Flöde 4: Inloggning och kontolåsning
* **Sekvens:** Kund → Webb/Mobilapp → Backend → Kontroll av inloggningsuppgifter → Inloggning eller kontolåsning
* **Verksamhetsmål:** Kunden ska kunna logga in säkert samtidigt som kontot skyddas mot upprepade felaktiga inloggningsförsök.
* **System som ingår:** Webb/APP,backend,E-post/SMS Service,databas
* **Konsekvens vid fel:** Kunden kan inte komma åt sitt konto, angripare kan försöka gissa lösenord, konton kan låsas felaktigt, kundservice får fler supportärenden.
* **Kritikalitet:** **Hög**

---

## 3. Integrationer & Felhantering

| Från | Till | Information | Vad kan gå fel? |
| :--- | :--- | :--- | :--- |
| **Backend / Order Service** | **Lagersystem (15 år gammalt)** | Reservera/återställa artiklar, hämta lagerstatus. | Timeout p.g.a. gammal hårdvara; felaktigt saldo skickas; systemet kraschar vid hög belastning. |
| **Backend / Order Service** | **Payment Provider** | Transaktionsbelopp, betalningsmetod, order-ID. | Avbruten anslutning mitt i köp (kunden betalar men ingen order skapas); dubbeldebitering. |
| **Backend / Order Service** | **Delivery Provider** | Adress, paketvikt, fraktalternativ. | Externa API:et är nere vilket gör att kassan låser sig och kunden inte kan slutföra köpet. |
| **Backend / Order Service** | **E-post / SMS Service** | Kunduppgifter, orderdetaljer, mall-ID. | Köpet slutförs men inga bekräftelser skickas ut, vilket leder till att kunder försöker köpa igen. |

---

## 4. Stakeholders & Beroenden

* **Product Owner (PO)**
  * *Testledaren behöver:* Tydliga acceptanskriterier och prioritering av buggar.
  * *De behöver från testledaren:* Löpande teststatus, riskrapporter och beslutsunderlag inför Go/No-Go.
* **De 3 utvecklingsteamen**
  * *Testledaren behöver:* Stabila byggen i testmiljön, enhetstestning samt teknisk dokumentation om API:er.
  * *De behöver från testledaren:* Tydliga felrapporter (buggar) med reproduktionssteg och loggar.
* **Externa leverantörer (Betalning & Leverans)**
  * *Testledaren behöver:* Tillgång till deras testmiljöer, testdata (t.ex. testkortnummer) och support vid integrationstestning.
  * *De behöver från testledaren:* Information om planerade belastningstester eller större uppdateringar i integrationen.

---

## 5. Riskmatris

| Risk | Sannolikhet | Konsekvens | Risknivå | Möjlig teståtgärd |
| :--- | :--- | :--- | :--- | :--- |
| **1. Det 15 år gamla lagersystemet klarar inte integrationen eller prestandan**. | **Hög** | **Hög** | **Kritisk** | Tidiga integrationstester (API/meddelandeköer) och dedikerade prestandatester mot lagersystemet. |
| **2. Tre utvecklingsteam krockar i den gemensamma testmiljön**. | **Hög** | **Medel** | **Hög** | Sätt upp ett tydligt releaseschema för miljön, inför CI/CD och röktest (smoke tests) vid varje driftsättning. |
| **3. Betalningsleverantörens testmiljö är instabil eller nere**. | **Medel** | **Hög** | **Hög** | Bygg "mockar" (simulatorer) för betalningsflödet så att interna tester kan fortsätta oberoende av extern part. |
| **4. Kunder debiteras dubbelt vid nätverksavbrott (K5)**. | **Låg** | **Hög** | **Hög** | Negativa tester: Bryt nätverksanslutningen exakt under betalningsögonblicket och verifiera hanteringen. |
| **5. Rabattkoder kombineras felaktigt så att varor blir gratis (K4)**. | **Medel** | **Medel** | **Medel** | Etablera en testmatris baserad på ekvivalensklassindelning för alla typer av rabattkombinationer. |
| **6. Kontolåsningen (K1) låser inte kontot efter 3 felaktiga försök, vilket öppnar för brute-force-attacker (K1 / Säkerhetsrisk)**. | **Medel** | **Hög** | **Hög** | Automatisera ett säkerhetstest som gör 3+ felaktiga inloggningar och verifierar att kontot förblir låst i exakt 30 minuter. |
| **7. Kundservice kan av misstag ändra priser eller behörigheter p.g.a. felaktig rollstyrning (K10 / Säkerhetsrisk)**. | **Låg** | **Hög** | **Hög** | Skapa separata testkonton för Kundservice respektive Admin för att verifiera rättighetsspärrar och 403-svar. |
| **8. Gamla eller saknade data i kassan gör att priser/leveransalternativ inte kan hämtas (K7 / Integrationsrisk)**. | **Medel** | **Medel** | **Medel** | Funktionella integrationstester med fiktiva adresser och tunga/skrymmande testprodukter för att trigga externa API-fel. |

---

## 6. Kvarstående Frågor inför Teststrategin

1. **Testdata:** Hur ska vi säkra realistisk testdata i den gemensamma testmiljön, särskilt för produkter, priser och lagersaldon?
2. **Prestandakrav:** Vilka specifika mål finns för "snabbare orderhantering" och hur många samtidiga användare ska plattformen klara?
3. **Säkerhet:** Ska en extern säkerhetsgranskning (penetrationstest) genomföras av kassan och kunddatabasen?
4. **Lagersystemet:** Finns det något tillgängligt API-gränssnitt till det 15 år gamla lagersystemet, eller kommunicerar det via filöverföring/databastabeller?
5. **Browser/OS-scope:** Vilka specifika webbläsare, operativsystem och mobila enheter ska plattformen stödja och testas på?
6. **Testmiljö:** Vem ansvarar för den gemensamma testmiljön, och hur ska bokning, versionshantering, deployment och miljöproblem samordnas mellan teamen?
7. **Teamansvar:** Vilka delar av plattformen ansvarar de tre utvecklingsteamen för, och vem ansvarar för tvärgående E2E- och integrationstestning?
8. **Scope:** Vilka funktioner och system ingår i den första releasen, och vad är uttryckligen Out of scope?
