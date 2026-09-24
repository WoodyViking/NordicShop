
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

### Testobjekt baserad då KravListan

| **Testobjekt** | **Vad verifieras** | **Prioritet** | **Relaterat** |
|---|---|---|---|
| Inloggning | Kunden ska kunna skapa konto och logga in med e-post och lösenord | HÖG | K1 |
| Kontolåsning | Efter 3 felaktiga inloggningsförsök ska kontot låsas i 30 minuter | HÖG | K1 |
| Butiksnavigering | Kunden ska kunna söka produkter, filtrera, se pris, lagerstatus och produktinformation | HÖG | K2 |
| Kundvagn | Kunden ska kunna lägga produkter i kundvagnen, ändra antal och ta bort produkter | HÖG | K3 |
| Rabattkod | Kunden ska kunna använda rabattkod. Rabattkoden ska kontrolleras mot giltighetsdatum och minsta ordervärde | HÖG | K4 |
| Rabattkod – användning | En rabattkod ska endast kunna användas en gång per kund | HÖG | K4 |
| Betalning | Kunden ska kunna betala med Visa, Mastercard eller Swish. Order ska endast skapas om betalningen godkänns och kunden får inte debiteras två gånger | HÖG | K5 |
| Lager | När en order genomförs ska lagersaldot ändras automatiskt. En produkt som inte längre finns i lager ska inte kunna köpas | HÖG | K6 |
| Leverans | Kunden ska kunna välja hemleverans eller ombud. Leveransalternativ och pris ska hämtas från den externa leveranstjänsten | HÖG | K7 |
| Orderbekräftelse | Efter genomfört köp ska kunden få orderbekräftelse via e-post med ordernummer, betalningsinformation och leveransinformation | MEDEL | K8 |
| Avbeställning | Kunden ska kunna avbeställa en order innan den skickats | HÖG | K9 |
| Återbetalning | Vid avbeställning ska betalningen återbetalas | HÖG | K9 |
| Lageråterställning | Vid avbeställning ska lagersaldot återställas | HÖG | K9 |
| Avbeställningsbekräftelse | Kunden ska få en bekräftelse när ordern har avbeställts | MEDEL | K9 |
| Kundservice – behörighet | Kundservice ska kunna se kundens order och betalningsstatus | HÖG | K10 |
| Administratör – behörighet | Endast administratörer ska kunna ändra produktpriser och användarbehörigheter | HÖG | K10 |
| Behörighetsbegränsning | Kundservice ska inte kunna ändra produktpriser eller användarbehörigheter | HÖG | K10 |
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
| **Backend / Order Service** | **Delivery Provider** | Adress, paketvikt, fraktalternativ. | Externa API:et är nere vilket gör att kassan låser sig och kunden inte kan slutföra köpet.Jag skulle argumentera för att detta inte håller till Deliviry Provider och istället Payment provider |
| **Backend / Order Service** | **E-post / SMS Service** | Kunduppgifter, orderdetaljer, mall-ID. | Köpet slutförs men inga bekräftelser skickas ut, vilket leder till att kunder försöker köpa igen. |
| **Backend / Order Service** | **Delivery Provider** | Adress, Paketvikt, Fraktalternativ. | Integrationen mellan ordersystem och delivery provider kraschar(kund har betalat och slufört orderd) men finns ingen information om att kund ska få paket hos Postnord |
---

## 4. Stakeholders & Beroenden

### Product Owner (PO)

**Vad behöver testledaren från dem?**
- Tydliga krav.
- Information om vad kunden faktiskt vill ha.
- Tydliga acceptanskriterier utifrån kraven.
- Prioritering av vilka funktioner och krav som är viktigast.

**Vad behöver de från testledaren?**
- Löpande teststatus, riskrapporter och beslutsunderlag inför Go/No-Go.
- Testledaren kommer att behöva veta vad kunden faktiskt vill ha, denna information kommer från PO.
- Testledaren kommer att få tydliga krav och kan skapa acceptanskriterier utifrån dessa.

**Varför är denna stakeholder viktig för testarbetet?**
- Product Owner representerar verksamhetens behov och hjälper testledaren att förstå vilka krav och funktioner som är viktigast att verifiera.


---

### De 3 utvecklingsteamen

**Vad behöver testledaren från dem?**
- Stabila byggen i testmiljön, enhetstestning samt teknisk dokumentation om API:er.
- Information om tekniska förändringar som påverkar testerna.
- Information om kända tekniska problem eller begränsningar.

**Vad behöver de från testledaren?**
- Tydliga felrapporter (buggar) med reproduktionssteg och loggar.
- Testledaren behöver kommunicera vilka områden som är prioriterade att testa och vilka risker som har identifierats.
- Information om testresultat och vilka fel som behöver åtgärdas.

**Varför är denna stakeholder viktig för testarbetet?**
- Utvecklingsteamen utvecklar och förändrar systemet. Testledaren behöver därför samarbeta med utvecklingsteamen för att förstå förändringar, rapportera fel och säkerställa att nya versioner kan testas.


---

### Externa leverantörer (Betalning & Leverans)

**Vad behöver testledaren från dem?**
- Tillgång till deras testmiljöer, testdata (t.ex. testkortnummer) och support vid integrationstestning.
- Information om förändringar i deras tjänster eller API:er.
- Teknisk information om integrationerna.

**Vad behöver de från testledaren?**
- Information om planerade belastningstester eller större uppdateringar i integrationen.
- Information om identifierade integrationsfel.
- Information om när tester kommer att genomföras.

**Varför är denna stakeholder viktig för testarbetet?**
- Betalnings- och leveranstjänsterna hanteras av externa leverantörer. NordicShop är därför beroende av att integrationerna mellan systemen fungerar.


---

### Test Teamet

**Vad behöver testledaren från dem?**
- Dokumentation på utförda tester.
- Information om identifierade fel och problem.
- Testresultat och information om projektets framgång.
- Med denna information kan testledaren framföra planering och handlingsplaner för framtida sprintar.

**Vad behöver de från testledaren?**
- Tydliga testuppgifter och prioriteringar.
- Information om vilka områden som är viktigast att testa.
- Planering inför kommande sprintar.
- Återkoppling på testresultat och identifierade risker.

**Varför är denna stakeholder viktig för testarbetet?**
- Testteamet genomför testerna och ger testledaren information om testresultat, fel och återstående testarbete. Informationen används för att planera och följa upp testarbetet.


---

### Kundservice

**Vad behöver testledaren från dem?**
- Information från kunder om det är något som inte fungerar i "Live"-miljön, dvs. buggar att fixa.
- Information om återkommande problem som kunder upplever.
- Information om funktioner som orsakar problem för kunderna.

**Vad behöver de från testledaren?**
- Information om kända buggar och problem.
- Information om förändringar som påverkar kundservice.
- Information om vilka problem som är identifierade och hur de hanteras.

**Varför är denna stakeholder viktig för testarbetet?**
- Kundservice har kontakt med kunderna och kan därför ge testledaren information om verkliga problem som upptäcks i produktion. Informationen kan användas för att identifiera områden som behöver testas.


---

### Projektledare

**Vad behöver testledaren från dem?**
- Information om projektets tidplan.
- Information om kommande releaser och deadlines.
- Information om eventuella förändringar som påverkar testarbetet.

**Vad behöver de från testledaren?**
- Teststatus.
- Information om identifierade risker och kritiska fel.
- Information om återstående testarbete inför release.

**Varför är denna stakeholder viktig för testarbetet?**
- Projektledaren behöver ha information om testläget för att kunna följa projektets tidsplan och planera inför den kommande releasen.
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

