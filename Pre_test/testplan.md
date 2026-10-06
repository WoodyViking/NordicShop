# MALL FÖR TESTPLAN

**\<Företagsnamn>**  
\<Projektnamn>  
Testplan för  NordicShop  
**Version 0.1**

## Dokumenthistorik

| **Version** | **Datum** | **Författare** | **Kommentar** |
| --- | --- | --- | --- |
| \<0.1> | \<2026-09-24> | \<Grupp 2> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |

*Använd mallen som ett styrande dokument för ett specifikt testuppdrag, en release eller en testperiod. Ersätt all text inom \<hakparenteser> och anpassa avsnitten efter projektets behov.*

# Innehåll

- [1 Unik identifiering](#1--unik-identifiering)
- [2 Inledning](#2--inledning)
  - [2.1 Kortfattad beskrivning](#21--kortfattad-beskrivning)
  - [2.2 Bakgrund](#22--bakgrund)
  - [2.3 Syfte och mål](#23--syfte-och-mål)
  - [2.4 Termer och förkortningar](#24--termer-och-förkortningar)
  - [2.5 Hänvisningar till andra dokument](#25--hänvisningar-till-andra-dokument)
  - [2.6 Öppna frågor](#26--öppna-frågor)
- [3 Testobjekt](#3--testobjekt)
- [4 Omfattning](#4--omfattning)
- [5 Avgränsning](#5--avgränsning)
- [6 Tillvägagångssätt](#6--tillvägagångssätt)
  - [6.1 Iterationer](#61--iterationer)
- [7 Start- och slutkriterier](#7--start--och-slutkriterier)
  - [7.1 Kriterier för att inleda testarbetet](#71--kriterier-för-att-inleda-testarbetet)
  - [7.2 Kriterier för att avsluta testarbetet](#72--kriterier-för-att-avsluta-testarbetet)
- [8 Avbrytande- och återupptagandekriterier](#8--avbrytande--och-återupptagandekriterier)
  - [8.1 Kriterier för att avbryta testerna](#81--kriterier-för-att-avbryta-testerna)
  - [8.2 Kriterier för att återuppta testarbetet](#82--kriterier-för-att-återuppta-testarbetet)
- [9 Testdokumentation](#9--testdokumentation)
- [10 Testaktiviteter](#10--testaktiviteter)
- [11 Testmiljö](#11--testmiljö)
  - [11.1 Hård- och mjukvara](#111--hård--och-mjukvara)
  - [11.2 Testverktyg](#112--testverktyg)
  - [11.3 Lokaler](#113--lokaler)
- [12 Ansvar](#12--ansvar)
- [13 Resurs- och utbildningsbehov](#13--resurs--och-utbildningsbehov)
- [14 Tidplan](#14--tidplan)
  - [14.1 Första testomgången](#141--första-testomgången)
  - [14.2 Påföljande testomgångar](#142--påföljande-testomgångar)
- [15 Risker och oförutsedda händelser](#15--risker-och-oförutsedda-händelser)
- [16 Godkännande av testplanen](#16--godkännande-av-testplanen)

# 1  Unik identifiering

*Ange ett unikt ID för testplanen, exempelvis projekt-/systemprefix + löpnummer eller versions-ID.*

\<Beskriv här>

**TP-NS-001**, version 0.3

ID-format: TP (testplan) – NS (NordicShop) – löpnummer. En ny testplan för en senare release får nästa löpnummer, till exempel TP-NS-002.


# 2  Inledning

*Beskriv sammanhanget för testplanen och vad dokumentet ska styra.*

\<Beskriv här>
Testplanen styr testarbetet inför den första produktionsreleasen av NordicShops nya e-handelsplattform. Den bygger på teststrategin (`test_strategi.md`) och testanalysen (`test_analys.md`) och beskriver vad som testas, hur, av vem och när. Planen innehåller också ett avsteg från strategin: testomfattningen har reducerats riskbaserat eftersom en av fyra testare har lämnat projektet medan releasedatumet ligger fast (se kapitel 4, 5 och 15).

## 2.1  Kortfattad beskrivning

*Sammanfatta vilken testinsats planen avser, vilken release/version som testas, målgrupp samt vem som ansvarar för dokumentet.*

\<Beskriv här>
| | |
| --- | --- |
| **Testinsats** | SIT, systemtest, regression och acceptanstest av den nya e-handelsplattformen, inklusive integrationer mot lagersystem, betalning, leverans och e-post/SMS. |
| **Release / version** | Release 1.0, första produktionsreleasen. Build-nummer anges vid varje driftsättning i testmiljön. |
| **Målgrupp** | Testteamet, de tre utvecklingsteamen, Product Owner, projektledaren, kundservice och administratörer som deltar i acceptanstest. |
| **Ansvarig för dokumentet** | Testledaren (Grupp 2). |

## 2.2  Bakgrund

*Beskriv projektets eller förändringens bakgrund, verksamhetsbehovet och varför testningen genomförs.*

\<Beskriv här>
NordicShop säljer kläder, elektronik och heminredning och ersätter sin befintliga e-handelslösning med en ny plattform. Den nya plattformen ska göra det enklare för kunder att handla, minska antalet avbrutna köp, ge snabbare orderhantering, automatisera lageruppdateringar, stödja fler betalningsalternativ och minska kundservicens manuella arbete.

Plattformen består av webbplats, mobilapp, backend och Order Service, som NordicShop äger. Den integreras med ett 15 år gammalt internt lagersystem med begränsad dokumentation, samt med tre externa leverantörer för betalning, leverans och e-post/SMS. Utvecklingen sker agilt av tre team i tvåveckorssprintar, och produktionsrelease är planerad om cirka fyra månader.

Testningen behövs eftersom de största riskerna ligger i integrationerna: lagersystemet, den gemensamma testmiljön och betalningsleverantörens testmiljö. Fel där leder direkt till förlorade pengar, felköp eller att kunder inte kan handla.

## 2.3  Syfte och mål

*Beskriv vad testerna ska verifiera och vilka konkreta mål som ska vara uppnådda efter avslutad testperiod.*
**Syfte:** Verifiera att NordicShops affärskritiska flöden fungerar tillsammans med alla integrerade system, och ge Product Owner och projektledaren ett underlag för Go/No-Go.

**Mål efter avslutad testperiod:**

- De tre kritiska E2E-flödena är verifierade: köp inklusive betalning, avbeställning och återbetalning, samt köp av sista produkten i lager. Inloggning och kontolåsning är verifierade som säkerhetsflöde.
- En avbruten betalning skapar ingen order, och ingen kund debiteras två gånger.
- Lagersaldot minskar vid köp och återställs vid avbeställning.
- Behörigheterna för kund, kundservice och administratör är verifierade.
- Det finns inga öppna kritiska fel. Varje kvarstående fel har ett beslut som Product Owner har godkänt.
- Acceptanstestet är signerat av Product Owner och verksamhetsansvarig.
- Kvarstående risker är dokumenterade och accepterade inför Go/No-Go.

\<Beskriv här>

## 2.4  Termer och förkortningar

*Förklara projektspecifika termer, förkortningar, verktygsnamn och begrepp som behövs för att förstå testplanen.*

| **Term** | **Förklaring** |
| --- | --- |
| Felrapport | Ett registrerat ärende för ett identifierat fel. |
| Testverktyg | Verktyg som används för krav-, test- och felhantering. |
| \<Term\> | \<Förklaring\> |
| E2E | Ett testflöde som verifierar en hel kedja av steg, från kundens handling till att alla inblandade system har reagerat korrekt. |
| API | Application Programming Interface. Gränssnitt som system använder för att kommunicera med varandra, t.ex. mellan order service och externa leverantörer. |
| Regression | Testning som säkerställer att ny eller ändrad kod inte har förstört tidigare fungerande funktionalitet. |
| Testmiljö | En miljö avsedd för test, separat från produktion, där system och integrationer kan verifieras utan att påverka riktiga kunder eller data. |
| Mock | En förenklad, konstgjord verision av ett system (t.ex. en betalningsleverantör) som används i test när det riktiga systemet inte är tillgängligt eller lämpligt eller att testa mot. |


## 2.5  Hänvisningar till andra dokument

*Lista relevanta styrande eller stödjande dokument, till exempel kravspecifikation, projektplan, teststrategi, felhanteringsprocess och testspecifikationer.*

| **Dokument** | **Beskrivning / sökväg / länk** |
| --- | --- |
| Teststrategi | `test_strategi.md` – testnivåer, testmiljöer och testobjekt. (Filen innehåller olösta merge-konflikter som måste rättas.) |
| Testanalys | `test_analys.md` v2.0 – testobjekt, kritiska flöden, integrationer, stakeholders, risker 1–13, öppna frågor. |
| Krav | `krav.md` – kraven K1–K10. (Filen är tom i dag. Kraven finns i case-beskrivningen och refereras i `test_analys.md`.) |
| Entry/Exit-kriterier | `workshop_7.md` (SIT, systemtest, acceptanstest) och `sit.md`. |
| Reviderad testomfattning | `reviderad_testomfattning.md` – prioritering, regression, out of scope, kvarstående risk. |
| Estimering | `test_estimera.md` – estimat, kapacitet, omprioritering (302 h). |
| Tidplan | `testplan_12_veckor.md` – aktiviteter, beroenden, RACI, milstolpar. |
| Testfall | `test_fall.md` – ska tas fram i testdesignen (V2–V3). |
| Testdata | `testdata.md` – beskrivning av testdatauppsättningen och återställningsrutinen. Tas fram V3–V4. |
| SQL-skript | Skript för att ladda och återställa testdata. Tas fram av utvecklingsteamen tillsammans med testarna. |
| Felhanteringsprocess | Beskrivs i kapitel 6 i denna plan tills en separat process finns. |

## 2.6  Öppna frågor| Testplan | \<Länk eller sökväg till testplan\> |
| Fil med testdata | \<Länk eller sökväg till testdata\> |
| SQL-skript | \<Länk eller sökväg till skript\> |
| Testfall | <test_fall.md> |
| Krav | krav.md |
| 1 | Har lagersystemet ett API, eller sker kommunikationen via fil eller databas? Uppdateras saldot direkt eller i batch? | Lagersystemets förvaltare | V1 | Öppen |
| 2 | Vilka testkort och Swish-testnummer får vi till Payment Providers testmiljö, och hur förhindras dubbeldebitering tekniskt? | Payment Provider / Utvecklingsteam | V2 | Öppen |
| 3 | Hur fördelas den delade testmiljön mellan de tre teamen? Vem är miljöansvarig? | Utvecklingsteamen / Projektledare | V2 | Öppen |
| 4 | Vilka konkreta prestandamål gäller (svarstider, antal samtidiga användare, kampanjtoppar)? | Product Owner | V3 | Öppen |
| 5 | Vilka webbläsare, operativsystem och mobila enheter ska testas? | Product Owner | V2 | Öppen |
| 6 | Ska ett penetrationstest av kassan och kunddatabasen göras före release? | Product Owner / Säkerhetsansvarig | V3 | Öppen |
| 7 | Ska rabattkoder aktiveras vid lansering? (Testledarens rekommendation: nej.) | Product Owner | V4 | Öppen |
| 8 | Vem fattar Go/No-Go-beslutet? | Projektledare | V2 | Öppen |
| 9 | Vilka kalenderdatum gäller för V1–V12 och för releasen? | Projektledare | V1 | Öppen |
| 10 | Vilken testare har lämnat projektet, och är den reducerade planen (302 h) godkänd av projektledaren? | Projektledare / Testledare | V1 | Öppen |
| 11 | Vilket testverktyg och vilket defektverktyg ska användas? | Testledare | V1 | Öppen |
| 12 | Har Delivery Provider och E-post/SMS-leverantören testmiljöer, eller används mock? | Externa leverantörer | V3 | Öppen |
| 13 | Ska köpet blockeras när Delivery Provider är nere, eller används ett standardalternativ? | Product Owner | V3 | Öppen |
| 14 | Vilka krav gäller för personuppgifter i testmiljön (GDPR) och för tillgänglighet? | Product Owner / Säkerhetsansvarig | V3 | Öppen |


## 2.6  Öppna frågor

*Lista frågor eller beslut som ännu inte är lösta och som kan påverka testplanen.*
Målen anges i relativa veckor eftersom kalenderdatum för projektstart inte är fastställda (se fråga 9).

| **#** | **Fråga** | **Ansvarig** | **Senast** | **Status** |
| --- | --- | --- | --- | --- |
| 1 | Har lagersystemet ett API, eller sker kommunikationen via fil eller databas? Uppdateras saldot direkt eller i batch? | Lagersystemets förvaltare | V1 | Öppen |
| 2 | Vilka testkort och Swish-testnummer får vi till Payment Providers testmiljö, och hur förhindras dubbeldebitering tekniskt? | Payment Provider / Utvecklingsteam | V2 | Öppen |
| 3 | Hur fördelas den delade testmiljön mellan de tre teamen? Vem är miljöansvarig? | Utvecklingsteamen / Projektledare | V2 | Öppen |
| 4 | Vilka konkreta prestandamål gäller (svarstider, antal samtidiga användare, kampanjtoppar)? | Product Owner | V3 | Öppen |
| 5 | Vilka webbläsare, operativsystem och mobila enheter ska testas? | Product Owner | V2 | Öppen |
| 6 | Ska ett penetrationstest av kassan och kunddatabasen göras före release? | Product Owner / Säkerhetsansvarig | V3 | Öppen |
| 7 | Ska rabattkoder aktiveras vid lansering? (Testledarens rekommendation: nej.) | Product Owner | V4 | Öppen |
| 8 | Vem fattar Go/No-Go-beslutet? | Projektledare | V2 | Öppen |
| 9 | Vilka kalenderdatum gäller för V1–V12 och för releasen? | Projektledare | V1 | Öppen |
| 10 | Vilken testare har lämnat projektet, och är den reducerade planen (302 h) godkänd av projektledaren? | Projektledare / Testledare | V1 | Öppen |
| 11 | Vilket testverktyg och vilket defektverktyg ska användas? | Testledare | V1 | Öppen |
| 12 | Har Delivery Provider och E-post/SMS-leverantören testmiljöer, eller används mock? | Externa leverantörer | V3 | Öppen |
| 13 | Ska köpet blockeras när Delivery Provider är nere, eller används ett standardalternativ? | Product Owner | V3 | Öppen |
| 14 | Vilka krav gäller för personuppgifter i testmiljön (GDPR) och för tillgänglighet? | Product Owner / Säkerhetsansvarig | V3 | Öppen |


# 3  Testobjekt

*Beskriv vad som ska testas: system, delsystem, funktioner, integrationer, API:er, batchjobb, rapporter eller andra komponenter. Ange gärna version/build och ägare.*

| **Testobjekt** | **Beskrivning** | **Version / build** |
| --- | --- | --- |
| Webb / Mobilapp – kärnflöden | Registrering, inloggning, kontolåsning, sök, kundvagn, rabattkod, kassa, betalning, orderöversikt och avbeställning. UI/UX-utseende ingår inte. Ägare: utvecklingsteamen. | Release 1.0, build enligt driftsättningslogg |
| Backend / Order Service | Orderhantering, orderstatus och anrop till lager, betalning, leverans och e-post/SMS. Ägare: utvecklingsteamen. | Release 1.0, build enligt driftsättningslogg |
| Kundservicens arbetsverktyg | Söka kund, se order och betalningsstatus, avbryta order, initiera återbetalning. | Release 1.0 |
| Administrationsverktyg och behörigheter | Produkter, priser, rabattkoder och användarbehörigheter. Rollerna kund, kundservice och administratör. | Release 1.0 |
| Integration: Lagersystem | Gränssnittet mot det 15 år gamla lagersystemet: saldo vid köp och avbeställning, timeout och belastning. Ägare: lagersystemets förvaltare. | Befintlig produktionsversion (öppen fråga #1) |
| Integration: Payment Provider | Visa, Mastercard och Swish: godkänd, nekad och avbruten betalning, dubbeldebitering, återbetalning. | Leverantörens testmiljö (version enligt leverantören) |
| Integration: Delivery Provider | Leveransalternativ (hem/ombud), pris och leveransbokning. | Leverantörens testmiljö eller mock (öppen fråga #12) |
| Integration: E-post / SMS Service | Order- och avbeställningsbekräftelser. | Leverantörens testmiljö eller mock (öppen fråga #12) |


# 4  Omfattning

*Beskriv vad som ingår i testningen. Koppla gärna till krav, affärsflöden, testnivåer, testtyper och prioriterade områden.*

\<Beskriv här>

| **Område / flöde** | **Testnivå / testtyp** | **Prioritet** | **Kommentar** |
| --- | --- | --- | --- |
| Kundvagn | SIT, systemtest, regression / funktionell | MUST (29 h) | Del av köpflödet (K3). |
| Checkout | SIT, systemtest, regression / funktionell | MUST (26 h) | Utan kassa ingen försäljning. |
| Kortbetalning | SIT, systemtest, regression / funktionell, säkerhet | MUST (28 h) | De flesta kunder betalar med kort. Fel kostar pengar direkt (K5, risk 3, 4). |
| Swishbetalning | SIT, systemtest, regression / funktionell | MUST (18 h) | Extern integration med hög osäkerhet (K5, risk 3). |
| Orderskapande | SIT, systemtest, regression / funktionell | MUST (22 h) | Order får bara skapas vid godkänd betalning (K5). |
| Lageruppdatering | SIT, systemtest, regression / funktionell, prestanda | MUST (33 h) | Det gamla lagersystemet, störst teknisk osäkerhet (K6, risk 1, 12). |
| Avbeställning | SIT, systemtest, regression / funktionell | MUST (29 h) | Fyra steg i tre system måste lyckas (K9). |
| Återbetalning | SIT, systemtest, regression / funktionell | MUST (29 h) | Gäller kundens pengar (K9, risk 9). |
| Kontolåsning | Systemtest / säkerhet | MUST (9 h) | Skydd mot brute force (K1, risk 6). |
| Behörigheter (kund, kundservice, admin) | Systemtest, acceptanstest / säkerhet | MUST (29 h) | Testas både i gränssnittet och direkt mot API:et (K10, risk 7). |
| Inloggning | Systemtest, indirekt via E2E | SHOULD (8 h) | Testas även i alla E2E-flöden. |
| Återställ lösenord | Systemtest | SHOULD (9 h) | Huvudscenario och att länken slutar gälla. |
| Orderbekräftelse | SIT, systemtest | SHOULD (8 h) | Kan skickas manuellt i nödläge (K8). |
| Registrera konto | Systemtest, indirekt via E2E | SHOULD (7 h) | Huvudscenario och viktigaste felfall (K1). |
| Leveransalternativ | SIT, systemtest | SHOULD (7 h) | Hemleverans och ombud i standardfall (K7, risk 8). |
| Produktsökning | Utforskande test | COULD (3 h) | Kort utforskande session (K2). |
| Produktfilter | Utforskande test | COULD (2 h) | Vanligaste filtren (K2). |
| Produktinformation | Utforskande test | COULD (2 h) | Kontrolleras indirekt via köpflödet (K2). |
| Rabattkod | Utforskande test | COULD (2 h) | En giltig och en ogiltig kod. Bör inte aktiveras vid lansering (K4, risk 5, öppen fråga #7). |
| Orderhistorik | Utforskande test | COULD (2 h) | Att kundens ordrar visas. |
| **Summa** | | **302 h** | MUST 252 h + SHOULD 39 h + COULD 11 h. Buffert 58 h. |
# 5  Avgränsning

*Beskriv uttryckligen vad som inte ska testas i denna testinsats och varför. Ange vid behov vem som ansvarar för testningen utanför denna plan.*

| **Avgränsning** | **Motivering** | **Ansvar utanför planen** |
| --- | --- | --- |
| UI/UX-utseende (layout, färger, typsnitt) | Påverkar inte systemets funktion. Låg prioritet i testanalysen. | Utvecklingsteamen och design granskar mot skisserna i sprintarna. |
| Äldre webbläsare och enheter | Endast de som flest kunder använder testas. Vilka det är avgörs i öppen fråga #5. | Product Owner beslutar listan. |
| Fördjupad test av sök och filter | Inte kritiskt för köpflödet. Endast kort utforskande test. | Testteamet efter release. |
| Fördjupad tillgänglighetstest | Tas bort på grund av minskad testtid. Risk att lagkrav inte uppfylls (öppen fråga #14). | Product Owner beslutar om extern granskning. |
| Fullständigt prestanda-/lasttest | Begränsas till att systemet klarar normal last. Kampanjtrafik verifieras inte fullt ut (risk 13). | Drift övervakar efter release. Utvecklingsteamen vid behov. |
| Leverans utöver standardfallen | Endast hemleverans och ombud i standardfall testas. | Utvecklingsteamen och Delivery Provider. |
| Externa leverantörers interna funktion | Vi testar bara vår sida av integrationen. | Payment Provider, Delivery Provider och E-post/SMS-leverantören. |
| Bank, kortnätverk och Swish | Nås via Payment Provider. | Payment Provider. |
| Lagersystemets egen kod | Fokus ligger på gränssnittet mot Order Service. | Lagersystemets förvaltare. |
| Komponent-/enhetstest | Görs av utvecklingsteamen. SIT startar först när entry-kriterierna är uppfyllda (kapitel 7). | Utvecklingsteamen. |

# 6  Tillvägagångssätt

*Beskriv hur testningen ska genomföras, exempelvis riskbaserat, kravbaserat, utforskande eller iterativt. Beskriv prioritering, felhantering, omtest, regression, rapportering och eventuell automatisering.*

**Riskbaserat.** Prioriteringen följer MUST/SHOULD/COULD i kapitel 4 och riskerna i `test_analys.md`. De största riskerna är det gamla lagersystemet (risk 1), den delade testmiljön (risk 2), betalningsleverantörens testmiljö (risk 3), kontolåsningen (risk 6) och den minskade testkapaciteten (risk 11).

**Testnivåer.** Komponent-/enhetstest görs av utvecklingsteamen. Testteamet genomför SIT och systemtest. Verksamheten genomför acceptanstest med stöd av testteamet. Varje nivå har entry- och exit-kriterier (kapitel 7).

**Testtyper.** Funktionell test och säkerhetstest behålls fullt ut. Prestanda, kompatibilitet och användbarhet reduceras (kapitel 5).

**Testdesign.**
- MUST: fullständiga testfall med positiva och negativa fall. Integrationerna testas alltid för nedtid, timeout, felaktig data och dubbla meddelanden.
- SHOULD: huvudscenario och de viktigaste felfallen.
- COULD: checklistor och utforskande test.
- Testtekniker: ekvivalensklasser och gränsvärden (rabattkod, kontolåsning, lagersaldo 0 och 1) samt tillståndsbaserade test för orderstatus.

**Testdata.** En gemensam uppsättning används för flera funktioner: minst 20 produkter med olika saldon (minst en med saldo 1), testkunder med orderhistorik, ordrar i status betald, skickad och avbeställd, samt konton för kundservice och administratör. Testkort och Swish-testnummer kommer från Payment Provider. Ingen riktig kunddata används (öppen fråga #14).

**Betalning.** I SIT används Payment Providers testmiljö, och en mock om den är otillgänglig. I systemtest krävs den riktiga testmiljön, eftersom en mock inte täcker återanrop, autentisering och återbetalning.

**Felhantering.** Fel registreras i defektverktyget med steg, förväntat och faktiskt resultat, build och loggar. Prioritet: Kritisk (blockerar ett affärsflöde, ingen workaround), Hög, Medel, Låg. Daglig defect triage leds av testledaren tillsammans med utvecklingsteamen.

**Omtest.** Alla rättade fel med prioritet Kritisk och Hög omtestas innan de stängs. Mindre kosmetiska fel kan samlas och omtestas tillsammans.

**Regression.** MUST-områden regressionstestas fullt ut, i första hand automatiserat. SHOULD-områden får ett kort röktest. COULD-områden regressionstestas inte.

**Automation (Förslag).** Utvecklingsteamen tar över mer av komponenttesterna och den automatiserade regressionen av MUST-flödena, så att testarna frigör tid. Röktest körs automatiskt vid varje driftsättning i den delade miljön.

**Rapportering.** Veckovis teststatus till projektledaren och Product Owner (körda, passerade och blockerade testfall, öppna fel per prioritet, risker). Testrapport efter SIT och systemtest. Slutrapport och Go/No-Go-underlag i V11.

## 6.1  Iterationer

*Beskriv testcykler/testomgångar och vad som sker i varje cykel, till exempel test, omtest och regression.*

| **Fas** | **Syfte** | **Genomförande** |
| --- | --- | --- |
| SIT | Verifiera integrationerna (lager, betalning, leverans, e-post/SMS) och de tre E2E-flödena. | V4–V6. Omtest löpande. |
| Systemtest | Verifiera hela systemet funktionellt och säkerhetsmässigt, inklusive behörigheter och betalning mot den riktiga testmiljön. | V6–V8. Omtest löpande. |
| Omtest | Verifiera rättade fel. | Löpande V5–V9, styrt av defect triage. |
| Regression | Säkerställa att rättningar inte förstört befintlig funktionalitet. | V8–V10. MUST fullt ut, SHOULD som röktest. |
| Acceptanstest | Verksamheten verifierar mot K1–K10 och sina egna arbetsflöden. | V9–V10. Koden fryses efter V9, därefter endast kritiska rättningar. |
| Release readiness och Go/No-Go | Slutrapport och beslutsunderlag. | V10–V11. |
| Release och sanity test | Produktionssättning och kontroll av de kritiska flödena i produktion. | V12. |

# 7  Start- och slutkriterier

*Definiera objektiva kriterier för när testningen får starta och när den kan betraktas som avslutad.*
Fullständiga kriterier med motiveringar finns i `workshop_7.md` och `sit.md`. **MUST** måste uppfyllas. **SHOULD** kan avvika efter riskbedömning.
## 7.1  Kriterier för att inleda testarbetet

- \<Testmiljö är installerad och tillräckligt stabil>
- \<Nödvändiga testdata finns tillgängliga>
- \<Krav/acceptanskriterier är tillräckligt tydliga>
- \<Överenskommen andel testfall är framtagna och granskade>
**SIT**
- (MUST) Komponenttest är klart, minst 80 % av enhetstesterna passerar och inga fel med prioritet Kritisk är öppna.
- (MUST) API-specifikationer finns för alla integrationer och är godkända av ansvarigt team och motparten.
- (MUST) SIT-miljön är uppsatt och röktestet godkänt: alla tjänster svarar och lagersystemet är anslutet.
- (MUST) Det finns åtkomst till Payment Providers testmiljö med testkort och Swish-test, annars en fungerande mock.
- (MUST) Testdata finns: minst 20 produkter med olika saldon (minst en med saldo 1), testkunder och rabattkoder.
- (SHOULD) SIT-testfallen för de tre E2E-flödena är granskade av någon annan än författaren och godkända av testledaren.
- (SHOULD) Releaseschemat för den delade testmiljön är dokumenterat och godkänt av alla tre team.

**Systemtest**
- (MUST) Inga öppna SIT-fel som blockerar ett affärsflöde eller saknar workaround. Undantag kräver testledarens skriftliga godkännande.
- (MUST) Systemtestmiljön är driftsatt med avsedd version och röktestet är godkänt.
- (MUST) Testdata för huvudflödena är laddad och stickprovskontrollerad.
- (SHOULD) Teststrategi och testplan är godkända av testledare och Product Owner.
- (SHOULD) Öppna SIT-fel är listade i defektverktyget och delade med testarna.
- (SHOULD) Rutinen för att återställa testdata finns, är provad och tar högst en arbetsdag.

**Acceptanstest**
- (MUST) Systemtestets MUST-kriterier är uppfyllda och inga fel med prioritet Kritisk är öppna.
- (MUST) Acceptanskriterier för K1–K10 är dokumenterade och godkända av Product Owner.
- (MUST) Acceptansscenarierna för E2E-flödena och kundservicens arbetsflöde är godkända av PO, och kundservice har bekräftat att de kan följa dem.
- (MUST) Verksamhetsrepresentanter är bokade med namn för hela testveckan: minst två från kundservice och en administratör.
- (MUST) Produktionslik testdata finns, inklusive ordrar i olika status och konton för alla roller.
- (SHOULD) Deltagarna har fått en introduktion (högst en timme) och listan över kända fel.
## 7.2  Kriterier för att avsluta testarbetet

- \<Planerade kritiska tester är genomförda>
- \<Inga öppna blockerande/kritiska fel över accepterad nivå>
- \<Överenskommen testtäckning och resultatnivå är uppnådd>
- \<Kvarstående risker är dokumenterade och accepterade>
**SIT**
- (MUST) 100 % av planerade testfall är körda och minst 95 % har passerat.
- (MUST) Inga öppna fel med prioritet Kritisk eller Hög mot Payment Provider och lagersystemet.
- (MUST) En avbruten betalning skapar ingen order och ingen dubbeldebitering sker.
- (MUST) Lagersaldot uppdateras vid köp och återställs vid avbeställning i alla tre E2E-flöden.
- (MUST) Vid timeout i lagersystemet eller nedtid hos Delivery Provider får kunden ett felmeddelande inom 10 sekunder, ingen order skapas och ingen debitering görs.
- (SHOULD) Fel med prioritet Medel och Låg har ansvarig och åtgärdsplan. SIT-testrapporten är godkänd av testledaren.

**Systemtest**
- (MUST) Alla testfall för de kritiska affärsflödena (inloggning, kundvagn, checkout, order) är körda och 100 % har passerat.
- (MUST) Behörighetstestet är genomfört för alla roller och alla testfall har passerat.
- (MUST) Betalningsflödena (alla betalsätt, avbruten betalning, felflöden) är testade mot leverantörens testmiljö och alla testfall har passerat.
- (SHOULD) Övriga öppna fel har beslutad hantering godkänd av PO. Inga nya blockerande fel under de senaste tre testdagarna. Testresultat och rapport är uppdaterade och arkiverade.

**Acceptanstest**
- (MUST) Alla acceptansscenarier för de kritiska verksamhetsflödena är körda.
- (MUST) Inga öppna fel med prioritet Kritisk. Varje öppet fel med prioritet Hög har en workaround godkänd av PO.
- (MUST) Kundservice har själva verifierat sitt arbetsflöde utan manuella extrasteg.
- (MUST) Varje kvarstående fel har ett dokumenterat beslut godkänt av PO.
- (MUST) Product Owner och verksamhetsansvarig har signerat acceptanstestet.
- (SHOULD) Övriga scenarier är körda och minst 90 % har passerat. Synpunkter på användbarhet har ansvarig och beslut.

**Hela testarbetet**
- Kvarstående risker (kapitel 15) är dokumenterade och accepterade av Product Owner inför Go/No-Go.

# 8  Avbrytande- och återupptagandekriterier

*Definiera när testningen ska pausas eftersom fortsatt testning inte är meningsfull, samt vad som krävs för att återuppta den.*

## 8.1  Kriterier för att avbryta testerna

- \<Testmiljön är instabil eller otillgänglig>
- \<För många blockerande/kritiska fel>
- \<Nödvändiga nyckelpersoner, testdata eller beroenden saknas>
- \<Leveransen bedöms inte vara testbar>

Testledaren pausar testningen på en nivå, eller i ett flöde, när något av följande gäller:

- Testmiljön är otillgänglig eller instabil, till exempel när röktestet efter en driftsättning misslyckas eller när teamens driftsättningar krockar (risk 2).
- Lagersystemet eller Payment Providers testmiljö är nere och ingen mock kan användas (risk 1, 3).
- **(Förslag)** Tre eller fler fel med prioritet Kritisk är öppna samtidigt, eller mer än 30 % av testfallen i ett E2E-flöde är blockerade.
- Den levererade builden saknar funktioner som testfallen kräver, så att leveransen inte är testbar.
- Testdata är förstörd och kan inte återställas samma dag.
- Nyckelpersoner saknas, till exempel verksamhetsrepresentanter under acceptanstestet (risk 10).
## 8.2  Kriterier för att återuppta testarbetet

- \<Blockerande problem är åtgärdade och verifierade>
- \<Miljö och beroenden är åter stabila>
- \<Beslut om återstart är fattat av ansvarig roll>

- Det blockerande problemet är åtgärdat och verifierat, och röktestet är godkänt.
- Miljön och de externa beroendena är stabila igen, eller en mock är på plats.
- Testdata är återställd.
- Testledaren har beslutat om återstart och informerat projektledaren. Tester som kördes på den felaktiga builden körs om.

# 9  Testdokumentation

*Beskriv vilka testartefakter som ska tas fram, var de lagras och vem som ansvarar för dem.*

| **Dokument / artefakt** | **Beskrivning** | **Ansvarig** |
| --- | --- | --- |
| Teststrategi | Övergripande strategi (`test_strategi.md`). | Testledare |
| Testplan | Detta dokument. | Testledare |
| Testanalys och risker | `test_analys.md`. Uppdateras när risker ändras. | Testledare |
| Testfall och checklistor | Fullständiga testfall för MUST, checklistor för COULD. Lagras i testverktyget. | Testare |
| Testdata och återställningsrutin | Beskrivning av datauppsättningen och SQL-skript. | Testare med stöd av utvecklingsteamen |
| Felrapporter | Registreras i defektverktyget. | Testare, utvecklingsteam |
| Veckovis teststatus | Testfall, fel per prioritet och risker. | Testledare |
| SIT-testrapport | Resultat från SIT, godkänd av testledaren. | Testledare |
| Systemtestrapport | Resultat, testfallsstatus och fellista, arkiverad senast sista testdagen. | Testledare |
| Acceptansscenarier och testmanus | Godkända av PO och läsbara för kundservice. | Product Owner, testare |
| Acceptanssignering | Skriftligt godkännande från PO och verksamhetsansvarig. | Product Owner |
| Go/No-Go-underlag och slutrapport | Testresultat, öppna fel och kvarstående risker. | Testledare |


# 10  Testaktiviteter

*Lista de viktigaste aktiviteterna från testanalys och planering till genomförande, felhantering, uppföljning och testrapport.*

| **ID** | **Aktivitet** | **Ägare** |
| --- | --- | --- |
| A1 | Testplanering och teststrategi | Testledare |
| A2 | Kravanalys (K1–K10) och acceptanskriterier | Testledare, testare, Product Owner |
| A3 | Testdesign: testfall, scenarier, checklistor | Testare |
| A4 | Testdataförberedelse | Testare, utvecklingsteam |
| A5 | Miljöetablering och röktest | Miljöansvarig (utveckling), testare |
| A6 | SIT | Testare |
| A7 | Systemtest | Testare |
| A8 | Defect triage och omtest | Testledare, utvecklingsteam, testare |
| A9 | Regressionstest | Testare, utvecklingsteam (automatiserad del) |
| A10 | Acceptanstest | Product Owner, kundservice, administratörer (stöd: testare) |
| A11 | Teststatus och rapportering | Testledare |
| A12 | Go/No-Go-underlag | Testledare |
| A13 | Release och sanity test i produktion | Utvecklingsteam, drift, testare |

# 11  Testmiljö

*Beskriv testmiljön och viktiga skillnader mot produktion. Dokumentera integrationer, beroenden, testdata, åtkomst och ansvar.*

## 11.1  Hård- och mjukvara

| **Komponent** | **Version / konfiguration** | **Skillnad mot produktion** | **Ansvarig** |
| --- | --- | --- | --- |
| Gemensam testmiljö: webb, app, backend, Order Service (SIT och systemtest) | Release 1.0, build enligt driftsättningslogg | Delas av tre team, så ändringar kan krocka. Lägre kapacitet än produktion. | Miljöansvarig från utvecklingen (öppen fråga #3) |
| Lagersystem (test) | Samma version som i produktion (öppen fråga #1) | Mindre datamängd och trafik än i produktion, så prestandaresultat gäller inte fullt ut. | Lagersystemets förvaltare |
| Payment Providers testmiljö (Visa, Mastercard, Swish) | Enligt leverantören | Extern och isolerad. Kräver separat åtkomst, testkort och Swish-testnummer. Inga riktiga dragningar. | Payment Provider, testledare |
| Delivery Provider och E-post/SMS (test eller mock) | Enligt leverantören, eller mock | En mock återger inte riktiga svarstider och fel. | Externa leverantörer, utvecklingsteam (mock) |
| Acceptans-/stagingmiljö | Samma build som är tänkt för release | Ska likna produktion, men med anonymiserad data och utan skarpa betalningar. | Miljöansvarig |
| Mobila enheter och webbläsare | Enligt öppen fråga #5 | Begränsat antal enheter jämfört med kundernas. | Testledare |


## 11.2  Testverktyg

| **Verktyg** | **Användningsområde** | **Ansvarig** |
| --- | --- | --- |
| Testhanteringsverktyg (Förslag: Jira med testplugin, eller liknande) | Testfall, testkörningar, spårbarhet mot K1–K10, rapportering. | Testledare |
| Defektverktyg (Förslag: samma verktyg som utvecklingsteamen använder) | Felrapporter och defect triage. | Testledare |
| CI/CD-pipeline med automatiserade tester | Röktest vid varje driftsättning och automatiserad regression av MUST-flödena. | Utvecklingsteam, testare |
| Mock/simulator för betalning, leverans och e-post/SMS | Test oberoende av externa parter, och simulering av timeout och nedtid. | Utvecklingsteam |
| API-testverktyg (Förslag: Postman eller liknande) | Test av integrationer, dubbla anrop och behörighet direkt mot API:et. | Testare || \<Fyll i> | \<Fyll i> | \<Fyll i> |

## 11.3  Lokaler

*Beskriv särskilda lokaler, enheter eller fysisk utrustning som krävs. Om ej relevant, ange Ej applicerbart.*

\<Beskriv här>
Ej applicerbart. Inga särskilda lokaler behövs. Under acceptanstestveckan bokas ett gemensamt rum eller en digital mötesyta, så att kundservice och administratörer kan få stöd av testarna under testet.

# 12  Ansvar

*Tydliggör ansvar, mandat, eskaleringsvägar och vem som fattar beslut om exempelvis teststart, avbrott och Go/No-Go.*

| **Roll** | **Ansvar / mandat** | **Namn / funktion** |
| --- | --- | --- |
| Testledare | Ansvarar för teststrategi, testplan, teststatus och Go/No-Go-underlag. Leder defect triage. Beslutar om teststart, avbrott, återstart och undantag från entry-kriterier. | Grupp 2 |
| Testare | Testdesign, testdata, SIT, systemtest, omtest och regression. Stöd i acceptanstest. | Testteamet (tre testare, se kapitel 13) |
| Utvecklingsteamen (3) | Komponenttest, felrättning, stabila byggen, API-dokumentation, mockar och automatiserad regression. | Respektive team |
| Miljöansvarig | Den delade testmiljöns stabilitet, driftsättningsschema och röktest. | Utses av utvecklingsteamen (öppen fråga #3) |
| Product Owner | Krav och acceptanskriterier. Godkänner kvarstående fel och acceptanstest. Prioriterar vid konflikt om omfattning. | Product Owner |
| Kundservice och administratörer | Genomför acceptanstest och verifierar sina arbetsflöden. | Minst två från kundservice och en administratör |
| Projektledare | Tidplan och resurser. Tar emot eskaleringar från testledaren. | Projektledare |
| Lagersystemets förvaltare | Kunskap om lagersystemet, testdata och stöd vid integrationsfel. | Förvaltaren av lagersystemet |
| Externa leverantörer | Testmiljöer, testdata och support. | Payment Provider, Delivery Provider, E-post/SMS-leverantören |

**Beslut och eskalering:**
- Teststart och avbrott: testledaren, utifrån kriterierna i kapitel 7 och 8.
- Eskalering: testare → testledare → projektledare. Frågor om prioritering och kvarstående fel går till Product Owner.
- Go/No-Go: testledaren tar fram underlaget. Vem som fattar beslutet är öppen fråga #8 (förslag: projektledare och Product Owner tillsammans).


*Ange resurser, omfattning/tillgänglighet, funktion och eventuella utbildnings- eller onboardingbehov.*
| **Namn / resurs** | **Omfattning** | **Funktion** | **Organisation / team** |
| --- | --- | --- | --- |
| Testledare | Hela testperioden | Planering, rapportering, defect triage, Go/No-Go-underlag | Testteamet |
| Testare 1 (SIT och regression) | 30 effektiva h/vecka | SIT, testdesign för integrationer, automatiserad regression | Testteamet |
| Testare 2 (SIT och systemtest) | 30 effektiva h/vecka | SIT, systemtest, säkerhets- och behörighetstest | Testteamet |
| Testare 3 (systemtest och acceptanstest) | 30 effektiva h/vecka | Analys, testdata, systemtest, stöd till verksamheten i acceptanstest | Testteamet |
| Miljöansvarig | Under SIT och systemtest (V4–V8) | Miljöstabilitet och röktest | Utvecklingsteamen |
| Product Owner | Löpande, samt hela acceptanstestet | Krav, prioritering, godkännanden | Verksamheten |
| Kundservice (minst 2) och administratör (1) | Hela acceptanstestveckan, bokade i V2 | Acceptanstest | Verksamheten |
| Lagersystemets förvaltare | Workshop i V1–V2, därefter vid behov | Kunskap om lagersystemet | Intern IT |

**Kapacitet:** Ursprungligen 4 testare × 30 h = 120 h/vecka. Efter att en testare lämnat projektet är kapaciteten 3 × 30 h = 90 h/vecka (25 % lägre). Rollerna ovan ersätter fördelningen i `testplan_12_veckor.md`, som byggde på fyra testare. Vilka personer som har vilken roll bestäms när öppen fråga #10 är besvarad.

**Utbildning och introduktion:**
- Workshop med lagersystemets förvaltare för testarna (V1–V2), eftersom dokumentationen är begränsad.
- Genomgång av Payment Providers testmiljö, testkort och Swish-test innan SIT.
- Introduktion för deltagarna i acceptanstestet (högst en timme) om testmanus och felrapportering.
- En eventuell ersättare behöver introduktion och ger full effekt först efter ungefär en vecka.


# 14  Tidplan

*Beskriv testperioden, viktiga milstolpar och planerade testomgångar. Anpassa efter projektets leveransmodell.*
Veckorna är relativa till testperiodens start (V1–V12). Kalenderdatum sätts när öppen fråga #9 är besvarad. Tidplanen bygger på `testplan_12_veckor.md` men är anpassad till tre testare. Uppskattningen på 302 timmar avser testarbetet för de 20 funktionerna. Resten av kapaciteten går till analys, miljö, omtest, rapportering och acceptansstöd.

| **Aktivitet / milstolpe** | **Start** | **Slut** | **Ansvarig** | **Kommentar** |
| --- | --- | --- | --- | --- |
| Analys och kravgenomgång | V1 | V2 | Testare 3, testledare | Workshop med lagersystemets förvaltare. |
| **M1** Teststrategi och testplan godkända, kravanalys klar | V2 | V2 | Testledare | Verksamheten bokas för acceptanstest. |
| Testdesign | V2 | V3 | Testare 1, 2 | MUST först. |
| Testdata | V3 | V4 | Testare 3 | Saldo 0 och 1, testkort, Swish-test. |
| **M2** Testdesign klar, kritisk testdata laddad | V4 | V4 | Testledare | |
| SIT | V4 | V6 | Testare 1, 2 | Kräver godkänd miljö, röktest och komponenttest. |
| Omtest | V5 | V9 | Alla testare | Styrs av defect triage. |
| **M3** SIT avslutad | V6 | V6 | Testledare | SIT:s exit-kriterier uppfyllda. |
| Systemtest | V6 | V8 | Testare 2, 3 | Betalning mot den riktiga testmiljön. |
| Regression | V8 | V10 | Testare 1, utvecklingsteam | MUST automatiserat i första hand. |
| **M4** Systemtest och primär regression klar, kodfrys | V9 | V9 | Testledare | Därefter bara kritiska rättningar. |
| Acceptanstest | V9 | V10 | PO, verksamheten, testare 3 | |
| Release readiness | V10 | V11 | Alla | |
| **M5** Acceptanstest signerat, Go/No-Go-underlag presenterat | V11 | V11 | Testledare, PO | |
| Go/No-Go | V11 | V11 | Beslutsfattare (öppen fråga #8) | |
| Release och sanity test | V12 | V12 | Utvecklingsteam, drift, testare | |
| **M6** Driftsättning genomförd | V12 | V12 | Projektledare | |


## 14.1  Första testomgången

| **Fas** | **Varaktighet / datum** |
| --- | --- |
| SIT | V4–V6 (3 veckor) |
| Systemtest | V6–V8 (3 veckor) |
| Regression | V8–V10 (3 veckor, delvis parallellt) |
| Acceptanstest | V9–V10 (2 veckor) || \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |

## 14.2  Påföljande testomgångar

*Beskriv hur efterföljande testomgångar planeras, vad som återanvänds och hur omfattningen styrs av felutfall och risk.*

\<Beskriv här>
Omtest av rättade fel sker löpande V5–V9. Varje ny build i testmiljön börjar med ett röktest. Därefter körs omtest av de fel som rättats, och sedan regression enligt risk: MUST-områden fullt ut, SHOULD-områden som röktest, COULD-områden inte alls. Testfall och testdata från första omgången återanvänds.

Antalet omgångar styrs av felutfallet. Bufferten på 58 timmar ska täcka fler fel än väntat. Om fler fel än väntat hittas i lagersystemet eller betalningen och bufferten inte räcker, eskalerar testledaren till projektledaren för ett nytt beslut. Alternativen är att ta in en ersättare, att utvecklarna tar mer av regressionen, eller att releasen flyttas ungefär en vecka.

# 15  Risker och oförutsedda händelser

*Dokumentera risker som kan påverka testningen eller leveransen. Ange konsekvens/kommentar, förebyggande eller korrigerande åtgärd, ägare och prioritet.*
Numreringen följer `test_analys.md` v2.0.

| **Risk** | **Konsekvens / kommentar** | **Åtgärd** | **Ägare** | **Prioritet** |
| --- | --- | --- | --- | --- |
| 1. Det 15 år gamla lagersystemet klarar inte integrationen eller prestandan. | Fel saldo, varor som inte finns säljs, restorder. Risken kvarstår delvis vid hög belastning. | Tidiga integrationstester, prestandatest, flöde 3 med samtidiga köp. Övervakning av saldot efter release och en färdig rutin hos kundservice. | Testledare, lagersystemets förvaltare | Hög |
| 2. Tre utvecklingsteam krockar i den gemensamma testmiljön. | Falska fel och förlorad testtid. | Releaseschema för miljön, CI/CD, röktest vid varje driftsättning. | Miljöansvarig | Hög |
| 3. Betalningsleverantörens testmiljö är instabil eller nere. | Betalningstester blockeras. En mock täcker inte återanrop, autentisering och återbetalning. | Mock i SIT. Systemtest kräver den riktiga testmiljön. Tidig kontakt med leverantören. | Testledare, Payment Provider | Hög |
| 4. Kunder debiteras dubbelt vid nätverksavbrott eller dubbelklick. | Återbetalningar, kundserviceärenden, förlorat förtroende. | Negativa tester: avbruten anslutning, dubbla anrop, dubbelklick. | Utvecklingsteam | Medel |
| 5. Rabattkoder valideras eller kombineras felaktigt. | Ekonomisk förlust. Rabattkoder testas bara utforskande. | Rabattkoder aktiveras inte vid lansering (öppen fråga #7). De ska kunna stängas av snabbt. | Product Owner | Medel |
| 6. Kontolåsningen fungerar inte (brute force). | Konton kan tas över. Kan inte rättas i efterhand. | Automatiserat säkerhetstest: 3+ felaktiga försök, låsning i 30 minuter, upplåsning. | Utvecklingsteam, testare | Hög |
| 7. Kundservice kan ändra priser eller behörigheter. | Säkerhetsrisk och felaktiga priser. | Separata testkonton per roll. Test i gränssnittet och direkt mot API:et (403-svar). | Utvecklingsteam, testare | Medel |
| 8. Leveransalternativ och priser kan inte hämtas. | Kunden kan inte slutföra köpet. | Integrationstest med nedtid, timeout och ovanliga adresser. Beslut om reservalternativ (öppen fråga #13). | Utvecklingsteam, Product Owner | Medel |
| 9. Ordern avbryts men återbetalningen genomförs inte. | Kunden får inte tillbaka sina pengar. | E2E-test av avbeställning med kontroll hos Payment Provider. Negativt test där återbetalningen misslyckas. | Utvecklingsteam, testare | Medel |
| 10. Kundservice har inte tid att delta i acceptanstestet. | Acceptanstestet blir inte klart eller signerat i tid. | Boka namngivna personer i V2, enkla testmanus, korta testpass. | Product Owner | Medel |
| 11. En testare har lämnat projektet och releasedatumet ligger fast. | Kapaciteten minskar 25 % (480 → 360 h). Den ursprungliga planen går inte att genomföra. | Reducerad plan på 302 h med 58 h buffert. Alternativ: ersättare, utvecklarna tar mer regression, eller releasen flyttas ungefär en vecka. | Testledare, projektledare | Hög |
| 12. Begränsad dokumentation av lagersystemet ger testfall som bygger på fel antaganden. | Fel upptäcks sent eller inte alls. | Workshop med förvaltaren, tidig utforskande test, gemensam granskning av testfallen. | Testledare | Hög |
| 13. Plattformen klarar inte toppbelastning, till exempel vid en kampanj. | Långsamma svar eller nedtid när försäljningen är som störst. | Lasttest av köpflödet när prestandamålen är kända (öppen fråga #4). Övervakning efter release. | Product Owner, drift | Hög |
| Kvarstående risk från den reducerade omfattningen | Fel i sök, filter, produktinformation, orderhistorik och rabattkoder kan nå produktion. Kunder med äldre webbläsare kan avbryta köp. Den reducerade regressionen kan missa följdfel. Tillgänglighetskraven uppfylls kanske inte. | Förstärkt övervakning efter release, beredskapsgrupp de första dagarna, möjlighet att stänga av rabattkoder, tydlig rollback-plan. | Testledare, projektledare | Hög |


# 16  Godkännande av testplanen

*Ange vilka roller/personer som ska godkänna testplanen och när godkännandet skedde.*

| **Namn / roll** | **Beslut** | **Datum** | **Kommentar** |
| --- | --- | --- | --- |
| Testledare (Grupp 2) | Ej beslutat | – | Ansvarig för planen. |
| Product Owner | Ej beslutat | – | Ska godkänna planen (systemtestets entry-kriterium ST-EN4) och besluta om rabattkoder (öppen fråga #7). |
| Projektledare | Ej beslutat | – | Ska godkänna den reducerade planen och tidplanen (öppen fråga #10). |
| Representant för utvecklingsteamen | Ej beslutat | – | Ska godkänna ansvar för komponenttest, mockar, miljö och automatiserad regression. |
