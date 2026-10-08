# Workshop 11 – Defect Triage Meeting

**Projekt:** NordicShop
**Läge:** Release om 3 dagar. Systemtest och regression pågår i SYS. Utvecklingsteamet kan inte rätta alla defekter före release.

**Skalor (enligt föreläsningen V3):**

| Severity | Betydelse | | Priority | Betydelse |
|---|---|---|---|---|
| Critical | Mycket allvarlig påverkan (felaktig betalning, säkerhet, kritiskt flöde fungerar inte) | | P1 | Lös omedelbart |
| High | Stor påverkan, viktig funktion fungerar inte | | P2 | Lös snarast |
| Medium | Begränsad påverkan, funktionen fungerar delvis eller workaround finns | | P3 | Kan lösas senare |
| Low | Liten påverkan, t.ex. mindre visuellt fel | | P4 | Låg prioritet / backlog |

**Severity** = hur allvarligt är felet? **Priority** = hur snabbt måste vi göra något åt det?

---

## Rollfördelning

| Roll | Fokus | Gruppmedlem |
|---|---|---|
| Testledare (leder mötet) | Testpåverkan, blockers, regression, risk, release readiness | |
| Utvecklare | Teknisk komplexitet, root cause, risk med rättningen, uppskattad tid | |
| Product Owner | Produkt, funktionalitet, användarvärde, prioritering | |
| Verksamhet | Kundpåverkan, affärsprocess, ekonomisk påverkan | |
| Projektledare | Tidplan, resurser, release, beroenden | |

---

## Uppgift 1 – Analysera defekterna

| ID | Defekt | Severity | Priority | Blocker? | Fix före release? | Motivering |
|---|---|---|---|---|---|---|
| **DEF-01** | Kunden debiteras två gånger vid snabbt dubbelklick på Betala | **Critical** | **P1** | Nej | **Ja** | Bryter mot krav K5 (ingen dubbeldebitering). Direkt ekonomisk skada för kunden, återbetalningar och förlorat förtroende. Händer lätt i verkligheten (stressade kunder, långsamt nät). |
| **DEF-02** | Logotypen något felplacerad i mobilvy | Low | P4 | Nej | Nej | Rent kosmetiskt. Påverkar inte köp. Läggs i backlog. |
| **DEF-03** | Betalning lyckas men order skapas ibland inte | **Critical** | **P1** | Ja, för köpflödet (intermittent) | **Ja** | Bryter mot K5. Kunden betalar men får ingen vara. Kräver manuell utredning och återbetalning. Flöden som bygger på en order (bekräftelse, avbeställning, återbetalning) kan inte testas stabilt. |
| **DEF-04** | Fel felmeddelande när rabattkod har gått ut | Low | P3 | Nej | Nej | Koden avvisas korrekt (K4 uppfylls), bara texten är fel. Kunden kan fortfarande handla. |
| **DEF-05** | Kundservice ser funktion för att ändra produktpris utan behörighet | **High** (Critical om priset faktiskt kan ändras) | **P1** | Nej | **Ja** | Säkerhets- och behörighetsfel, bryter mot K10. Måste först verifieras om ändringen går igenom i backend eller bara syns i gränssnittet. Fel pris i produktion ger ekonomisk skada. |
| **DEF-06** | Sökning tar 8 sekunder när många användare är aktiva | High | P2 | Nej | Nej | Påverkar konvertering vid lansering då trafiken är hög. Men prestandaproblem är svåra att rätta säkert på 3 dagar. Hanteras med skalning av infrastruktur och övervakning, rättas efter release. |
| **DEF-07** | Orderbekräftelse via e-post skickas inte för vissa köp | High | P2 | Nej | **Ja** | Bryter mot K8. Kunden blir osäker på om köpet gått igenom, vilket ger samtal till kundservice och risk för dubbelköp. Ordernumret visas dock på bekräftelsesidan. |
| **DEF-08** | Kan inte återställa lösenord om e-postadressen innehåller + | Medium | P3 | Bara enskilt test | Nej | Gäller en liten grupp användare. Workaround: kundservice hjälper till att återställa lösenordet. |
| **DEF-09** | Produkt kan i sällsynta fall köpas trots lagersaldo 0 | High | P2 | Nej | Ja (om kapacitet finns) | Bryter mot K3/K6. Översäljning ger avbeställning, återbetalning och missnöjd kund. Sällsynt, och det finns en manuell workaround (se Förändring). |
| **DEF-10** | "Leveransadress" felstavat på checkout-sidan | Low | P2 | Nej | Nej, rättas i första patchen | Låg severity men syns för alla kunder i checkout och påverkar intrycket inför lansering (exempel på *Low severity, hög priority*). Tar ingen av de fem platserna men är en enkel textändring. |
| **DEF-11** | Återbetalning genomförs men orderstatus ligger kvar som "Betald" | High | P2 | Nej | Nej | Kunden har fått sina pengar, men kundservice ser fel status. Risk för dubbel återbetalning. Workaround: kundservice kontrollerar betalningsstatus hos Payment Provider innan återbetalning. |
| **DEF-12** | SYS kraschar när fyra testare kör regression parallellt | High | **P1** | **Ja, hela regressionen** | Ja – men av DevOps/miljö, inte utvecklingsteamet | Stoppar regressionen 3 dagar före release. Troligen ett miljö- eller kapacitetsproblem, inte en produktdefekt. Workaround: max tre testare parallellt. |
| **DEF-13** | Administratör måste ibland logga in två gånger efter ny deployment | Low | P3 | Nej | Nej | Bara internt, bara efter deployment. Workaround: logga in igen. |
| **DEF-14** | Kan inte välja hemleverans till vissa giltiga postnummer | Medium | P2 | Delvis (vissa testfall) | Nej | Påverkar K7 för en del kunder, men workaround finns: välj leverans till ombud. Kan bero på data från Delivery Provider. |
| **DEF-15** | Samma problem som DEF-07, från annat testfall | – | – | – | Följer DEF-07 | **Duplicate of DEF-07** (se Uppgift 2). |

### Sammanfattning

| Severity | Antal | Defekter |
|---|---|---|
| Critical | 2 | DEF-01, DEF-03 |
| High | 6 | DEF-05, DEF-06, DEF-07, DEF-09, DEF-11, DEF-12 |
| Medium | 2 | DEF-08, DEF-14 |
| Low | 4 | DEF-02, DEF-04, DEF-10, DEF-13 |
| Duplicate | 1 | DEF-15 |

---

## Uppgift 2 – Identifiera duplicates

### Duplicate

**DEF-15 → Duplicate of DEF-07.** Båda beskriver att orderbekräftelsen inte skickas via e-post. DEF-15 kommer bara från ett annat testfall.

Vad vi gör:

- DEF-15 markeras som *Duplicate of DEF-07* och stängs.
- Kopplingen behålls, så att testbevis, loggar och testfall från DEF-15 inte försvinner.
- Testfallet från DEF-15 läggs till i retesten av DEF-07. Två olika testfall som visar felet hjälper utvecklaren att hitta grundorsaken.

### Möjligen relaterade (inte duplicates förrän root cause är känd)

| Defekter | Varför de kan hänga ihop | Åtgärd |
|---|---|---|
| DEF-03 och DEF-07 | Om ingen order skapas skickas heller ingen bekräftelse. En del av DEF-07 kan vara ett symptom på DEF-03. | Utvecklaren kontrollerar om ordern finns i de fall där mejlet saknas. Om ja: separata fel. Om nej: samma root cause. |
| DEF-01 och DEF-03 | Båda handlar om hur Order Service hanterar svaret från Payment Provider (t.ex. saknad idempotens eller fel vid callback). | Root cause-analys av betalning → order. En gemensam rättning kan lösa båda. |
| DEF-12 och DEF-06 | Båda visar problem när belastningen ökar. | Undersök om det är miljöns kapacitet eller ett prestandaproblem i produkten. |

**Princip:** Vi markerar bara som duplicate när vi vet att grundorsaken är densamma. Annars riskerar vi att stänga ett fel som egentligen är ett annat.

---

## Uppgift 3 – Identifiera blockers

| Vad blockeras? | Defekt | Förklaring | Workaround |
|---|---|---|---|
| **Hela testningen** | **DEF-12** | Regressionen kan inte köras i full takt. Med 3 dagar kvar till release är det det största hotet mot att vi blir klara. | Max tre testare kör regression samtidigt. Schemalägg körningarna. DevOps undersöker miljöns kapacitet. |
| **Ett kritiskt flöde** | **DEF-03** | Köpflödet betalning → order fungerar inte stabilt. Testfall som kräver en order (bekräftelse, avbeställning, återbetalning) kan ge falska fel. | Kontrollera att ordern finns innan testet fortsätter. Logga alla fall där order saknas. |
| **Ett kritiskt flöde (delvis)** | DEF-01 | Blockerar inte testningen, men köpflödet kan inte godkännas så länge felet finns. | Testare undviker dubbelklick i andra tester, så att felet inte stör dem. |
| **Endast enskilda tester** | DEF-08 | Bara testfall för lösenordsåterställning med + i e-postadressen. | Använd en annan testadress för övriga tester. |
| **Endast enskilda tester** | DEF-14 | Bara testfall för hemleverans till vissa postnummer. | Använd andra postnummer eller ombud. |
| **Endast enskilda tester** | DEF-13 | Admin-tester direkt efter deployment. | Logga in igen. |

### Är alla blockers produktdefekter?

**Nej.** DEF-12 är troligen ett **miljöproblem**: SYS klarar inte belastningen från fyra parallella körningar. Det ska ägas av DevOps/miljöansvarig och inte ta en av utvecklingsteamets platser.

Andra blockers som inte är produktdefekter kan vara:

- SYS eller en extern testmiljö (t.ex. Payment Provider TEST) är nere
- testdata saknas eller har förbrukats
- fel build är deployad
- behörighet eller åtkomst till testmiljön saknas

**Men:** Om analysen visar att produkten själv kraschar under belastning (koppling till DEF-06), är DEF-12 en produktdefekt och en allvarlig risk för lanseringen. Därför måste root cause tas fram innan vi stänger frågan.

---

## Uppgift 4 – Prioritera rättningarna (5 defekter)

**Vald ordning:** DEF-01, DEF-03, DEF-05, DEF-09, DEF-07 (+ DEF-15)

**Ej i listan:** DEF-12 rättas parallellt av DevOps (miljöproblem). DEF-10 rättas i första patchen efter release.

### 1. DEF-01 – Dubbeldebitering

| | |
|---|---|
| **Konsekvens** | Kunden betalar två gånger. Ekonomisk skada, reklamationer, manuella återbetalningar och skadat förtroende. Kan bli ett mediefall vid lansering. |
| **Varför nu?** | Bryter mot K5. Ett känt fel som rör kundernas pengar kan inte släppas. Rättningen är ofta avgränsad (spärra knappen efter första klick + idempotensnyckel mot Payment Provider). |
| **Om den inte rättas** | Varje lanseringsdag ger nya dubbeldebiteringar. Release bör då inte genomföras (No-Go). |
| **Retest** | Dubbelklick, flera snabba klick, uppdatera sidan under betalning, tillbaka-knappen. Både kort och Swish. Kontrollera i Payment Provider TEST att bara en transaktion finns. |
| **Regression** | Hela köpflödet: lyckad betalning, nekad betalning, timeout, betalning → order. |

### 2. DEF-03 – Betalning lyckas men ingen order

| | |
|---|---|
| **Konsekvens** | Kunden har betalat men får ingen vara. Kundservice måste utreda och återbetala manuellt. |
| **Varför nu?** | Bryter mot K5. Det är ett kritiskt flöde och samtidigt en blocker för tester som kräver en order. |
| **Om den inte rättas** | Kunder betalar utan att få något, och vi kan inte lita på resultaten i order-, avbeställnings- och återbetalningstesterna. |
| **Retest** | Upprepade köp (felet är intermittent, så minst 20–30 köp), med kort och Swish. Även vid fördröjt svar från Payment Provider. |
| **Regression** | Betalning → order, orderbekräftelse (DEF-07), lageruppdatering, avbeställning och återbetalning. |

### 3. DEF-05 – Kundservice ser prisändring

| | |
|---|---|
| **Konsekvens** | Om kundservice kan ändra pris kan produkter säljas till fel pris. Även om det bara syns i gränssnittet är det ett säkerhetsfel och bryter mot K10. |
| **Varför nu?** | Säkerhets- och behörighetsfel ska inte gå i produktion. Rättningen är troligen liten (rollkonfiguration + kontroll i backend) och har låg risk. |
| **Om den inte rättas** | Risk för felaktiga priser, ekonomisk skada och brister vid revision. |
| **Retest** | Logga in som kundservice: funktionen syns inte och direkta API-anrop för prisändring nekas. Logga in som administratör: prisändring fungerar. |
| **Regression** | Behörighetstester för alla roller (kund, kundservice, administratör), K10. |

### 4. DEF-09 – Köp trots lagersaldo 0

| | |
|---|---|
| **Konsekvens** | Översäljning. Kunden får avbeställning och återbetalning i stället för sin vara. |
| **Varför nu?** | Bryter mot K3 och K6. Vid lansering är trafiken hög och kampanjvaror tar slut, vilket gör ett sällsynt fel vanligare. |
| **Om den inte rättas** | Fler översålda ordrar, mer arbete för kundservice och fler missnöjda kunder. |
| **Retest** | Två kunder köper samtidigt den sista produkten (saldo 1). Köp när saldot nyss blivit 0. |
| **Regression** | Lageruppdatering vid köp, återställning av lager vid avbeställning, visning av lagerstatus. Kontroll av integrationen mot lagersystemet. |

### 5. DEF-07 (+ DEF-15) – Orderbekräftelse skickas inte

| | |
|---|---|
| **Konsekvens** | Kunden vet inte om köpet gått igenom. Ger samtal till kundservice och risk för dubbelköp. |
| **Varför nu?** | Bryter mot K8. Berör många kunder direkt. Rättningen kan också visa om felet hänger ihop med DEF-03. |
| **Om den inte rättas** | Ökad belastning på kundservice under lanseringen. Sämre kundupplevelse. |
| **Retest** | Testfallen från både DEF-07 och DEF-15. Kort och Swish, olika leveranssätt, med och utan rabattkod. |
| **Regression** | Orderbekräftelse, ordernummer, betalnings- och leveransinformation i mejlet (K8). E-post vid avbeställning (K9). |

### Varför inte DEF-11 eller DEF-06?

- **DEF-11:** Kunden har fått sina pengar. Felet påverkar intern status och har en manuell workaround för kundservice.
- **DEF-06:** Prestandaproblem är svåra och riskfyllda att rätta på 3 dagar. Skalning och övervakning är en säkrare kortsiktig åtgärd.

### Plan för de 3 dagarna

| Dag | Aktivitet |
|---|---|
| Dag 1 | Utvecklingsteamet rättar de fem defekterna. DevOps löser DEF-12. Testarna kör regression med max tre parallellt. |
| Dag 2 | Ny build deployas + smoke test. Retest av de fem rättningarna. P1-regression av betalning, order, lager och behörighet. |
| Dag 3 | Omtest av eventuella nya fel. Testrapport. Go/No-Go-möte. |

---

# Förändring – bara 3 defekter kan rättas

**Release Manager:** Releasen kan inte flyttas. Utvecklingsteamet hinner bara rätta **tre** defekter i stället för fem.

## 1. Vilka tre prioriteras?

| # | Defekt | Varför |
|---|---|---|
| 1 | **DEF-01 – Dubbeldebitering** | Critical. Rör kundernas pengar och bryter mot K5. Ingen rimlig workaround. |
| 2 | **DEF-03 – Betalning utan order** | Critical. Kunden betalar utan att få varan. Blockerar också testningen av orderflödet. |
| 3 | **DEF-05 – Behörighet prisändring** | Säkerhetsfel (K10). Liten och säker rättning, så den ger mycket riskminskning för lite utvecklingstid. |

**Princip:** Vi rättar det som rör **pengar och säkerhet** och som saknar en bra workaround. Det som har en workaround lämnas öppet.

**Alternativ:** Om DEF-05 kan lösas med enbart konfiguration (administratören tar bort behörigheten från kundservicerollen) behöver den inte någon av utvecklingsteamets platser. Då tar **DEF-09** den tredje platsen.

## 2. Vilka defekter lämnas öppna?

| Lämnas öppen | Severity | Plan |
|---|---|---|
| DEF-07 (+ DEF-15) | High | Rättas i första patchen efter release |
| DEF-09 | High | Rättas i första patchen efter release |
| DEF-11 | High | Rättas i första patchen efter release |
| DEF-06 | High | Rättas efter release, efter prestandatest och root cause-analys |
| DEF-14 | Medium | Rättas i patch, utreds tillsammans med Delivery Provider |
| DEF-08 | Medium | Backlog / patch |
| DEF-10 | Low | Första patchen (enkel textändring) |
| DEF-04, DEF-13 | Low | Backlog |
| DEF-02 | Low | Backlog |
| DEF-12 | – | Inte en produktdefekt. Hanteras av DevOps, påverkar inte produktion. |

## 3. Finns workaround?

| Defekt | Workaround | Ansvarig |
|---|---|---|
| DEF-07 | Ordernumret visas på bekräftelsesidan. Kundservice kan skicka bekräftelsen manuellt. Daglig kontroll av ordrar utan skickat mejl. | Kundservice / Verksamhet |
| DEF-09 | Visa produkter som slut redan när lagersaldot är 1 (säkerhetsmarginal), särskilt för kampanjvaror. Daglig kontroll av ordrar med saldo under 0, som avbeställs och återbetalas direkt. | Verksamhet / Administratör |
| DEF-11 | Kundservice kontrollerar alltid betalningsstatus hos Payment Provider innan en återbetalning görs. Status rättas manuellt. | Kundservice |
| DEF-06 | Skala upp servrar inför lanseringen. Övervaka svarstider. | DevOps |
| DEF-14 | Kunden väljer leverans till ombud. Informationstext i checkout. | PO / Kundservice |
| DEF-08 | Kundservice hjälper till att återställa lösenordet. | Kundservice |
| DEF-13 | Administratören loggar in igen. | Administratör |
| DEF-02, DEF-04, DEF-10 | Ingen behövs (kosmetiskt / text). | – |

**Viktigt:** En workaround är bara en workaround om någon känner till den och är beredd att använda den. Kundservice måste få instruktionerna **före** release.

## 4. Vilka residual risks skapas?

| Residual risk | Sannolikhet | Konsekvens | Risknivå | Hantering |
|---|---|---|---|---|
| Översäljning av produkter (DEF-09) | L | M | **M** | Säkerhetsmarginal i lagret, daglig kontroll, rättning i första patchen |
| Kunder får ingen orderbekräftelse (DEF-07) | M | M | **M** | Ordernummer på skärmen, kundservice skickar manuellt, övervakning |
| Dubbel återbetalning p.g.a. fel status (DEF-11) | L | H | **M** | Kontroll mot Payment Provider före varje återbetalning |
| Långsam sökning vid hög trafik (DEF-06) | H | M | **H** | Skalning, övervakning, beredskap vid lanseringen |
| Sämre förtroende p.g.a. synliga småfel (DEF-02, DEF-10) | M | L | **L** | Rättas i första patchen |
| Rättningarna av DEF-01/03/05 orsakar nya fel | M | H | **H** | Fokuserad retest och P1-regression av betalning, order och behörighet |
| Regressionen blir inte helt klar p.g.a. DEF-12 och tidsbrist | M | H | **H** | Prioritera P1-regression, dokumentera vad som inte har testats |

## 5. Behöver testomfattningen förändras?

**Ja.** Med mindre tid och färre rättningar flyttar vi testningen dit risken är störst.

**Mer test:**

- Retest av DEF-01, DEF-03 och DEF-05.
- **P1-regression** (måste köras): betalning, betalning → order, lager, avbeställning/återbetalning, behörighet.
- Verifiera att varje workaround faktiskt fungerar (t.ex. att kundservice kan skicka bekräftelse manuellt).
- Kort belastningstest av sökning, om miljön klarar det, för att förstå hur stor DEF-06-risken är.

**Mindre test:**

- **P3-regression** (kan utelämnas): visuella kontroller, admin-funktioner med låg risk, texter.
- Tester av områden med kända öppna fel (DEF-08, DEF-14) körs inte om, eftersom vi redan vet att de fallerar.

**Praktiskt:**

- Max tre testare kör regression samtidigt (DEF-12).
- Allt som inte har testats dokumenteras och redovisas på Go/No-Go-mötet.

## 6. Vad behöver kommuniceras inför Go/No-Go?

Det räcker inte att säga "vi har 11 öppna defekter". Testledaren redovisar:

| Område | Innehåll |
|---|---|
| **Öppna defekter per severity** | Critical: 0 (om DEF-01 och DEF-03 är rättade och retestade). High: 4 (DEF-06, DEF-07, DEF-09, DEF-11). Medium: 2. Low: 4. |
| **Rättade och verifierade** | DEF-01, DEF-03, DEF-05: retest godkänd, P1-regression godkänd (eller vad som återstår). |
| **Kritiska flöden** | Köp, betalning → order och behörighet är verifierade. Orderbekräftelse och lager fungerar med workaround. |
| **Vad har inte testats** | T.ex. full regression av lågprioriterade områden, belastning på sökning. |
| **Residual risks** | Tabellen i punkt 4, med ägare. |
| **Workarounds** | Vilka som gäller, vem som ansvarar och att kundservice har fått instruktioner. |
| **Plan efter release** | Första patchen med DEF-07, DEF-09, DEF-11 och DEF-10. Ansvarig och datum. |
| **Övervakning** | Larm vid dubbeldebitering, ordrar utan mejl, lagersaldo under 0 och långsam sökning. Beredskap första dagarna. |

### Testledarens rekommendation

**Villkorad Go:**

- **Go** om DEF-01 och DEF-03 är rättade, retestade och P1-regressionen av köpflödet är godkänd, och om verksamheten accepterar residual risks och workarounds.
- **No-Go** om DEF-01 eller DEF-03 inte kan verifieras. En release med känd risk för dubbeldebitering eller betalning utan order rekommenderas inte.

**Vem beslutar?** Testledaren ger underlaget och en rekommendation. Beslutet om Go/No-Go och om att acceptera residual risks tas av **Product Owner, verksamheten och projektledaren / Release Manager** tillsammans.

---

## Till presentationen – varför är detta viktigt?

- **Alla defekter är inte lika viktiga.** En dubbeldebitering väger tyngre än tio felstavade ord. Därför räknar vi inte bara defekter utan bedömer risk.
- **Severity och priority är inte samma sak.** DEF-10 är ett litet fel men syns för alla kunder. DEF-06 är allvarligt men för riskfyllt att rätta på 3 dagar.
- **Workarounds gör det möjligt att släppa med kända fel**, men bara om verksamheten känner till dem och är beredd att använda dem.
- **Testledarens roll** är inte att fatta beslutet om release, utan att ge ett tydligt underlag: vad är testat, vad är kvar, vilka risker finns och vad rekommenderar vi.:
