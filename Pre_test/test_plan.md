# TESTPLAN

**NordicShop**
Testplan för NordicShop – ny e-handelsplattform
**Version 0.2**

> **Hur du läser dokumentet:** Text märkt **[SAKNAS]** finns inte i gruppens övriga dokument och måste fyllas i av er. Text märkt **[FÖRSLAG]** är härledd från underlaget men inte uttryckligen beslutad. Källfil anges inom parentes där det är relevant.

## Dokumenthistorik

| **Version** | **Datum** | **Författare** | **Kommentar** |
| --- | --- | --- | --- |
| 0.1 | 2026-09-24 | Grupp 2 | Mall skapad |
| 0.2 | 2026-10-06 | Grupp 2 | Förifylld från test_analys, test_strategi, sit, workshop_7, reviderad_testomfattning, test_estimera och testplan_12_veckor |
| | | | |

# Innehåll

- [Unik identifiering](#unik-identifiering)
- [1 Inledning](#1--inledning)
  - [1.1 Kortfattad beskrivning](#11--kortfattad-beskrivning)
  - [1.2 Bakgrund](#12--bakgrund)
  - [1.3 Syfte och mål](#13--syfte-och-mål)
  - [1.4 Termer och förkortningar](#14--termer-och-förkortningar)
  - [1.5 Hänvisningar till andra dokument](#15--hänvisningar-till-andra-dokument)
- [2 Öppna frågor](#2--öppna-frågor)
- [3 Testobjekt](#3--testobjekt)
- [4 Omfattning](#4--omfattning)
- [5 Avgränsning](#5--avgränsning)
- [6 Tillvägagångssätt](#6--tillvägagångssätt)
- [7 Iterationer](#7--iterationer)
- [8 Start- och slutkriterier](#8--start--och-slutkriterier)
  - [8.1 Kriterier för att inleda testarbetet](#81--kriterier-för-att-inleda-testarbetet)
  - [8.2 Kriterier för att avsluta testarbetet](#82--kriterier-för-att-avsluta-testarbetet)
- [9 Avbrytande- och återupptagandekriterier](#9--avbrytande--och-återupptagandekriterier)
  - [9.1 Kriterier för att avbryta testerna](#91--kriterier-för-att-avbryta-testerna)
  - [9.2 Kriterier för att återuppta testarbetet](#92--kriterier-för-att-återuppta-testarbetet)
- [10 Testdokumentation](#10--testdokumentation)
- [11 Testaktiviteter](#11--testaktiviteter)
- [12 Testmiljö](#12--testmiljö)
  - [12.1 Hård- och mjukvara](#121--hård--och-mjukvara)
  - [12.2 Testverktyg](#122--testverktyg)
  - [12.3 Lokaler](#123--lokaler)
- [13 Ansvar](#13--ansvar)
- [14 Resurs- och utbildningsbehov](#14--resurs--och-utbildningsbehov)
- [15 Tidplan](#15--tidplan)
  - [15.1 Första testomgången](#151--första-testomgången)
  - [15.2 Påföljande testomgångar](#152--påföljande-testomgångar)
- [16 Risker och oförutsedda händelser](#16--risker-och-oförutsedda-händelser)
- [17 Godkännande av testplanen](#17--godkännande-av-testplanen)

# Unik identifiering

**TP-NS-001** v0.2 **[FÖRSLAG]** – byt ut om ni har en annan ID-konvention.

# 1  Inledning

Testplanen styr testarbetet inför produktionsreleasen av NordicShops nya e-handelsplattform. Den bygger på teststrategin för NordicShop (`test_strategi.md`) och beskriver vad som testas, hur, av vem och när, samt eventuella avsteg från strategin. Planen innehåller den **reviderade, riskbaserade testomfattningen** som tagits fram när testkapaciteten minskade (se kapitel 4 och 5).

## 1.1  Kortfattad beskrivning

NordicShop är ett e-handelsföretag som säljer kläder, elektronik och heminredning. Testplanen avser första produktionsreleasen av den nya plattformen, som består av webb- och mobilapp, Backend/Order Service samt integrationer mot ett 15 år gammalt internt lagersystem och tre externa leverantörer (betalning, leverans, e-post/SMS). Utvecklingen sker agilt av tre team i tvåveckorssprintar. Dokumentet ansvaras av testledaren (Grupp 2) och riktar sig till testteamet, utvecklingsteamen, Product Owner och projektledaren.

**Release/version som testas:** **[SAKNAS]**

## 1.2  Bakgrund

NordicShop ersätter sin befintliga e-handelslösning. Målen med den nya plattformen är att göra det enklare för kunder att handla, minska antalet avbrutna köp, ge snabbare orderhantering, automatisera lageruppdateringar, stödja fler betalningsalternativ och minska kundservicens manuella arbete. Produktionsrelease är planerad om cirka fyra månader från projektstart. De största testutmaningarna är ett gammalt lagersystem, en gemensam testmiljö som delas av tre team samt externa leverantörers testmiljöer.

## 1.3  Syfte och mål

Testningen ska verifiera att NordicShops affärskritiska flöden fungerar tillsammans med de integrerade systemen, och ge projektledaren och Product Owner ett underlag för Go/No-Go.

Mål efter avslutad testperiod:

- De tre kritiska E2E-flödena är verifierade: **(1)** köpflöde inklusive betalning, **(2)** avbeställning och återbetalning, **(3)** köp av sista produkten i lager. Inloggning och kontolåsning (flöde 4) verifieras som säkerhetskritiskt flöde.
- Avbruten betalning skapar ingen order och ingen dubbeldebitering sker. Lagersaldot uppdateras vid köp och återställs vid avbeställning.
- Behörigheter för kundservice och administratör är verifierade.
- Inga öppna kritiska fel finns, och kvarstående fel och risker är dokumenterade och godkända av Product Owner.
- Acceptanstestet är signerat av Product Owner och verksamhetsansvarig.

## 1.4  Termer och förkortningar

| **Term** | **Förklaring** |
| --- | --- |
| Felrapport | Ett registrerat ärende för ett identifierat fel. |
| Testverktyg | Verktyg som används för krav-, test- och felhantering. |
| E2E | Ett testflöde som verifierar en hel kedja av steg, från kundens handling till att alla inblandade system har reagerat korrekt. |
| API | Application Programming Interface. Gränssnitt som system använder för att kommunicera med varandra, t.ex. mellan Order Service och externa leverantörer. |
| Regression | Testning som säkerställer att ny eller ändrad kod inte har förstört tidigare fungerande funktionalitet. |
| Testmiljö | En miljö avsedd för test, separat från produktion, där system och integrationer kan verifieras utan att påverka riktiga kunder eller data. |
| Mock | En förenklad, konstgjord version av ett system (t.ex. en betalningsleverantör) som används i test när det riktiga systemet inte är tillgängligt eller lämpligt att testa mot. |
| SIT | Systemintegrationstest. Verifierar integrationerna mellan Webb/App, Backend/Order Service, Lagersystem, Payment Provider, Delivery Provider och E-post/SMS Service. |
| UAT / AT | User Acceptance Test / Acceptanstest. Verksamheten verifierar systemet mot affärskrav. |
| MUST / SHOULD / COULD | Prioriteringsnivåer för testomfattning: måste, bör respektive kan testas (reduceras eller flyttas). |
| Entry/Exit-kriterier | Kriterier för när en testnivå får starta respektive anses avslutad. |
| Go/No-Go | Beslut om produktionsrelease ska genomföras, baserat på testresultat och kvarstående risker. |
| PO | Product Owner. |
| Rollback | Återgång till föregående version i produktion om releasen misslyckas. |
| Workaround | Tillfällig lösning som gör att ett fel inte blockerar ett affärsflöde. |

## 1.5  Hänvisningar till andra dokument

| **Dokument** | **Beskrivning / sökväg / länk** |
| --- | --- |
| Testanalys | `test_analys.md` – testobjekt, kritiska flöden, integrationer, stakeholders, riskmatris |
| Teststrategi | `test_strategi.md` – testnivåer, testmiljö, testobjekt (OBS: filen innehåller olösta merge-konflikter) |
| Krav | `krav.md` (**filen är tom**, kraven K1–K10 refereras i `test_analys.md`) |
| Entry/Exit-kriterier | `workshop_7.md` (SIT, systemtest, acceptanstest) och `sit.md` |
| Reviderad testomfattning | `reviderad_testomfattning.md` – prioritering, regression, out of scope, kvarstående risk |
| Estimering | `test_estimera.md` – estimat, kapacitet, omprioritering |
| Tidsplan (12 veckor) | `testplan_12_veckor.md` – aktiviteter, beroenden, RACI, milstolpar, resursfördelning |
| Testfall | `test_fall.md` – **[SAKNAS: filen finns inte bland uppladdade filer]** |
| Fil med testdata | **[SAKNAS]** |
| SQL-skript | **[SAKNAS]** |
| Felhanteringsprocess | **[SAKNAS]** |

# 2  Öppna frågor

| **Fråga** | **Ansvarig** | **Senast datum** | **Status** |
| --- | --- | --- | --- |
| Hur säkerställer vi realistisk och konsekvent testdata (produkter, priser, lagersaldon) i den gemensamma testmiljön? | Testledare / Utvecklingsteam | [SAKNAS] | Öppen |
| Vilka konkreta prestandamål gäller för "snabbare orderhantering" (svarstider, antal samtidiga användare)? | Product Owner | [SAKNAS] | Öppen |
| Ska en extern säkerhetsgranskning/penetrationstest göras av kassan och kunddatabasen före release? | Product Owner / Säkerhetsansvarig | [SAKNAS] | Öppen |
| Har lagersystemet ett tillgängligt API, eller sker kommunikationen via filöverföring/databas? | Utvecklingsteam (lagersystem) | [SAKNAS] | Öppen |
| Vilka webbläsare, operativsystem och mobila enheter ska stödjas och testas? (Reducerad omfattning: "de som flest använder", men vilka?) | Product Owner | [SAKNAS] | Öppen |
| Hur hanteras versionshantering och släppschema i den delade testmiljön så att de tre teamen inte stör varandra? | Testledare / Utvecklingsteam | [SAKNAS] | Öppen |
| Vilken testdata och åtkomst kan vi få till betalningsleverantörens separata testmiljö? | Testledare / Extern leverantör (betalning) | [SAKNAS] | Öppen |
| Vilken tester har lämnat projektet, och när? Är det avgjort vilken reducerad plan (302 h) som gäller, och är den godkänd av projektledaren? | Testledare / Projektledare | [SAKNAS] | Öppen |
| Är testperioden 4 veckor (`test_estimera.md`) eller 12 veckor (`testplan_12_veckor.md`)? Hur hänger de ihop (effort vs. kalendertid)? | Testledare | [SAKNAS] | Öppen |
| Vem fattar Go/No-Go-beslutet? | Projektledare / Product Owner | [SAKNAS] | Öppen |
| Aktiveras rabattkoder vid lansering? (Rekommendation i estimeringen: nej.) | Product Owner | [SAKNAS] | Öppen |
| Vilket testverktyg och vilket defektverktyg används? | Testledare | [SAKNAS] | Öppen |

# 3  Testobjekt

| **Testobjekt** | **Beskrivning** | **Version / build** |
| --- | --- | --- |
| Webb / Mobilapp – kärnflöden | Registrering, inloggning, kontolåsning, sök, kundvagn, rabattkod, checkout, betalning, orderöversikt. UI/UX-utseende ingår inte. | [SAKNAS] |
| Backend / Order Service | Orderhantering, statusuppdateringar, API-anrop och triggers mot lager, betalning, leverans och e-post/SMS. | [SAKNAS] |
| Lagersystem (integration) | Det 15 år gamla lagersystemet: saldo vid köp och avbeställning, beteende vid timeout och hög belastning. Fokus på gränssnittet, inte lagersystemets kod. | [SAKNAS] |
| Payment Provider (integration) | Visa, Mastercard och Swish: godkänd/nekad betalning, avbruten betalning, dubbeldebitering, återbetalning. | [SAKNAS] |
| Delivery Provider (integration) | Leveransalternativ (hem/ombud) och priser. Testas i standardfallet. | [SAKNAS] |
| E-post / SMS Service (integration) | Order- och avbeställningsbekräftelser med korrekt innehåll. | [SAKNAS] |
| Administrationsverktyg | Behörigheter (kundservice/administratör), produkthantering, prisändringar, skapande av rabattkoder. | [SAKNAS] |

# 4  Omfattning

Testningen är **riskbaserad** och bygger på den reviderade omfattningen efter att testkapaciteten minskat från 4 till 3 testare (480 → 360 timmar). Den reviderade planen omfattar **302 timmar** och lämnar **58 timmar buffert** (`test_estimera.md`). De tre E2E-flödena (köp inklusive betalning, avbeställning/återbetalning, sista produkten i lager) samt inloggning och kontolåsning har högst prioritet.

| **Område / flöde** | **Testnivå / testtyp** | **Prioritet** | **Kommentar** |
| --- | --- | --- | --- |
| Kundvagn | SIT, systemtest, regression / funktionell | MUST (29 h) | Del av happy path för köp. |
| Checkout | SIT, systemtest, regression / funktionell | MUST (26 h) | Utan checkout ingen försäljning. |
| Kortbetalning | SIT, systemtest, regression / funktionell, säkerhet | MUST (28 h) | De flesta kunder betalar med kort. Fel kostar pengar direkt. |
| Swishbetalning | SIT, systemtest, regression / funktionell | MUST (18 h) | Extern integration med hög osäkerhet. |
| Orderskapande | SIT, systemtest, regression / funktionell | MUST (22 h) | Risk att kunden betalar men ingen order skapas. |
| Lageruppdatering | SIT, systemtest, regression / funktionell, prestanda | MUST (33 h) | Gammalt system, störst teknisk osäkerhet (risk R1). |
| Avbeställning | SIT, systemtest, regression / funktionell | MUST (29 h) | Flera steg i flera system måste lyckas. |
| Återbetalning | SIT, systemtest, regression / funktionell | MUST (29 h) | Gäller kundens pengar. |
| Lås konto efter tre felaktiga försök | Systemtest / säkerhet | MUST (9 h) | Skydd mot brute force (risk R4). |
| Behörigheter (kundservice/admin) | Systemtest, acceptanstest / säkerhet | MUST (29 h) | Kundservice ska inte kunna ändra priser eller behörigheter (risk R8). |
| Login | Systemtest, indirekt via E2E | SHOULD (8 h, från 12) | Testas även i alla E2E-flöden. |
| Återställ lösenord | Systemtest | SHOULD (9 h, från 18) | Huvudscenario och att länken slutar gälla. |
| Orderbekräftelse via e-post | SIT, systemtest | SHOULD (8 h, från 14) | Kan skickas manuellt i nödläge. |
| Registrera konto | Systemtest, indirekt via E2E | SHOULD (7 h) | Huvudscenario och viktigaste felfall. |
| Leveransalternativ | SIT, systemtest | SHOULD (7 h, från 11) | Hemleverans och ombud i standardfall. |
| Produktsökning | Utforskande test | COULD (3 h, från 11) | Kort utforskande session. |
| Produktfilter | Utforskande test | COULD (2 h, från 12) | Snabb kontroll av vanligaste filtren. |
| Produktinformation | Utforskande test | COULD (2 h, från 7) | Kontrolleras indirekt via köpflödet. |
| Rabattkod | Utforskande test | COULD (2 h, från 7) | En giltig och en ogiltig kod. Bör inte aktiveras vid lansering. |
| Orderhistorik | Utforskande test | COULD (2 h, från 9) | Kort kontroll av att ordrar visas. |
| **Summa** | | **302 h** | 252 h MUST + 39 h SHOULD + 11 h COULD |

**Regression:** MUST-områden regressionstestas fullt ut (helst automatiserat). SHOULD-områden får kort röktest. COULD-områden regressionstestas inte. Köpflöde, betalning, Order Service, avbeställning/återbetalning samt inloggning och behörigheter ingår i regressionen.

**Felomtest:** Alla rättade kritiska och allvarliga fel omtestas. Endast omtest av mindre kosmetiska fel kan samlas och skjutas upp.

# 5  Avgränsning

| **Avgränsning** | **Motivering** | **Ansvar utanför planen** |
| --- | --- | --- |
| UI/UX-utseende, layout, färger och typsnitt | Inte avgörande för systemets funktion. Låg prioritet i testanalysen. | [SAKNAS] |
| Äldre webbläsare och enheter | Testas endast på de som flest användare har (vilka är en öppen fråga). | [SAKNAS] |
| Fördjupad sök-testning | Inte kritisk för köpflödet, endast kort utforskande session. Kan göras efter release. | [SAKNAS] |
| Fördjupad tillgänglighetstestning | Tas bort pga minskad testtid. Risk att lagkrav inte uppfylls (se kapitel 16). | [SAKNAS] |
| Prestandatest (reducerat) | Begränsat till att systemet "snurrar" och inte påverkar säkerhet. Kampanjtrafik är inte fullt verifierad. | [SAKNAS] |
| Leverans: endast standardfall | Fel pris eller saknade ombudsalternativ kan förekomma. | [SAKNAS] |
| Acceptanstest (kortare) | Kundservice kan upptäcka problem i sitt arbetsflöde först efter release. | Product Owner / Verksamhet |
| Intern implementation hos externa system (betalning, leverans, e-post/SMS) | Testas inte, endast gränssnittet/integrationen. | Externa leverantörer |
| Lagersystemets egen kod | Fokus ligger på gränssnittet mot Order Service. | Lagersystemets förvaltare |
| Komponent-/enhetstest | Genomförs av utvecklingsteamen. SIT startar först när kriterierna i kapitel 8 är uppfyllda. | Utvecklingsteamen |

# 6  Tillvägagångssätt

Testningen är **riskbaserad**. Prioriteringen följer MUST/SHOULD/COULD i kapitel 4 och riskmatrisen i `test_analys.md`, där de största riskerna är det gamla lagersystemet (R1, risknivå 25), tre team i en gemensam testmiljö (R2, 20) och instabil betalningsmiljö (R3, 12).

- **Testnivåer:** Komponent-/enhetstest (utvecklingsteamen), SIT, systemtest och acceptanstest. Varje nivå har entry- och exit-kriterier (kapitel 8).
- **Testtyper som behålls:** Funktionell testning (happy path för E2E-flödena) och säkerhet (inloggning, kontolåsning, behörigheter).
- **Testtyper som reduceras:** Prestanda, kompatibilitet (webbläsare/enheter) och användbarhet.
- **Testdesign:** MUST-funktioner får fullständiga testfall. SHOULD-funktioner färre varianter (huvudscenario och viktigaste felfall). COULD-funktioner testas med checklistor och utforskande test.
- **Testdata:** En gemensam uppsättning används för flera funktioner. Testdata för lager (saldo 0 och 1) och betalning (testkort, Swish) behålls fullt ut.
- **Betalning:** Testas mot leverantörens testmiljö. Om den är otillgänglig används en mock (endast SIT, systemtest kräver riktig testmiljö).
- **Felhantering:** Dagliga defect triage-möten. Fel rapporteras med reproduktionssteg och loggar. Prioritet: Kritisk, Hög, Medel, Låg.
- **Omtest och regression:** Se kapitel 4 och 7.
- **Automation:** Regression för MUST-funktioner automatiseras helst. Utvecklarna kan ta över mer av regressionen och komponenttesterna (rekommenderat alternativ i `test_estimera.md`).
- **Rapportering:** Teststatus löpande till projektledaren. SIT-testrapport, systemtestrapport och underlag för Go/No-Go.

# 7  Iterationer

| **Fas** | **Syfte** | **Genomförande** |
| --- | --- | --- |
| SIT | Verifiera integrationerna mellan systemen (lager, betalning, leverans, e-post/SMS) och de tre E2E-flödena. | Planerad V4–V6. Retest löpande parallellt. |
| Systemtest | Verifiera hela systemet funktionellt och säkerhetsmässigt, inklusive behörigheter. | Planerad V6–V8. Retest löpande. |
| Regression | Säkerställa att fixar inte förstört befintlig funktionalitet. | Planerad V8–V10. MUST fullt ut, SHOULD röktest. |
| Acceptanstest (UAT) | Verksamheten verifierar mot affärskrav K1–K10. | Planerad V9–V10. Kod fryst efter V9, endast kritiska buggfixar. |
| Release readiness / Go/No-Go | Slutrapport och beslutsunderlag. | V10–V11. |
| Release och sanity test | Produktionssättning och verifiering. | V12. |

# 8  Start- och slutkriterier

Fullständiga kriterier finns i `workshop_7.md` och `sit.md`. Sammanfattning nedan. **MUST** måste uppfyllas, **SHOULD** kan avvika efter riskbedömning.

## 8.1  Kriterier för att inleda testarbetet

**SIT**
- (MUST) Komponenttest klart, minst 80 % av enhetstesterna passerar, inga öppna Kritiska fel.
- (MUST) API-specifikationer för alla integrationer finns och är godkända av ansvarigt team och motparten.
- (MUST) SIT-miljön är uppsatt och röktest är godkänt (alla tjänster svarar, lagersystemet anslutet).
- (MUST) Åtkomst till Payment Providers testmiljö (testkort och Swish-test), annars fungerande mock.
- (MUST) Testdata finns: minst 20 produkter med olika saldon (minst en med saldo 1), testkunder och rabattkoder.
- (SHOULD) SIT-testfallen för de tre E2E-flödena är granskade av någon annan än författaren och godkända av testledaren.
- (SHOULD) Releaseschema för den delade testmiljön är dokumenterat och godkänt av alla tre team.

**Systemtest**
- (MUST) Inga öppna SIT-defekter som blockerar ett affärsflöde eller saknar workaround (undantag kräver testledarens skriftliga godkännande).
- (MUST) Systemtestmiljön är deployad med avsedd version och röktest är godkänt.
- (MUST) Testdata för huvudflödena är laddad och stickprovskontrollerad.
- (SHOULD) Teststrategi och systemtestets testplan är godkända av testledare och Product Owner.
- (SHOULD) Öppna SIT-defekter är listade i defektverktyget och delade med testarna.
- (SHOULD) Rutin för återställning av testdata finns, är provad och tar högst en arbetsdag.

**Acceptanstest**
- (MUST) Systemtestets obligatoriska exit-kriterier är uppfyllda och inga Kritiska fel är öppna.
- (MUST) Acceptanskriterier för K1–K10 är dokumenterade och godkända av Product Owner.
- (MUST) Acceptansscenarier för de tre E2E-flödena och kundservicens arbetsflöde är godkända av PO och läsbara för kundservice.
- (MUST) Verksamhetsrepresentanter bokade med namn för hela testveckan (minst två från kundservice och en administratör).
- (MUST) Produktionslik testdata (minst 20 produkter, testkunder med orderhistorik, ordrar i status betald/skickad/avbeställd, konton för kundservice och admin).
- (SHOULD) Deltagarna har fått introduktion (högst 1 timme) och listan över kända fel.

## 8.2  Kriterier för att avsluta testarbetet

**SIT**
- (MUST) 100 % av planerade testfall körda, minst 95 % passerade.
- (MUST) Inga öppna Kritiska eller Höga fel mot Payment Provider och Lagersystem.
- (MUST) Avbruten betalning skapar ingen order och ingen dubbeldebitering.
- (MUST) Lagersaldot uppdateras vid köp och återställs vid avbeställning i alla tre E2E-flöden.
- (MUST) Vid timeout från lagersystemet eller nedtid hos Delivery Provider får kunden felmeddelande inom 10 sekunder, ingen order skapas och ingen debitering görs.
- (SHOULD) Medel/Låga fel är dokumenterade med ansvarig och åtgärdsplan. SIT-testrapport godkänd av testledaren.

**Systemtest**
- (MUST) Alla testfall för kritiska affärsflöden (inloggning, kundvagn, checkout, order) är körda och 100 % passerade.
- (MUST) Behörighetstest klart för alla roller (kund, administratör, kundtjänst) och passerat.
- (MUST) Betalningsflöden (alla betalsätt, avbruten betalning, felflöden) testade mot leverantörens testmiljö och passerade.
- (SHOULD) Övriga öppna defekter har beslutad hantering godkänd av PO. Inga nya blockerande defekter de senaste 3 testdagarna. Testresultat och rapport uppdaterade och arkiverade.

**Acceptanstest**
- (MUST) 100 % av acceptansscenarierna för kritiska verksamhetsflöden körda (köp, avbeställning/återbetalning, sista produkten i lager, kundservice hanterar ärende, admin ändrar pris och skapar rabattkod).
- (MUST) Inga öppna Kritiska fel. Varje öppet Högt fel har en workaround godkänd av PO.
- (MUST) Kundservice har själva verifierat sitt arbetsflöde utan manuella extrasteg.
- (MUST) Varje kvarstående fel har dokumenterat beslut godkänt av PO. PO och verksamhetsansvarig har signerat acceptanstestet.
- (SHOULD) Övriga acceptansscenarier körda och minst 90 % passerade. Synpunkter på användbarhet dokumenterade med ansvarig och beslut.

**Gemensamt för hela testarbetet**
- Kvarstående risker är dokumenterade och accepterade av Product Owner (se kapitel 16).

# 9  Avbrytande- och återupptagandekriterier

> **[FÖRSLAG]** – dessa är härledda från riskerna i `test_analys.md` och entry-kriterierna. Underlaget innehåller inga uttryckligen beslutade avbrytandekriterier, så granska och justera.

## 9.1  Kriterier för att avbryta testerna

- Testmiljön är instabil eller otillgänglig, t.ex. när de tre teamens driftsättningar krockar (risk R2) eller röktestet misslyckas.
- Lagersystemet eller betalningsleverantörens testmiljö är nere och ingen mock finns (risk R1, R3).
- Öppna defekter blockerar ett affärsflöde och saknar workaround, så att fortsatt testning inte ger information.
- Nödvändiga testdata, testare eller verksamhetsrepresentanter saknas. Antal blockerande/kritiska fel som utlöser avbrott: **[SAKNAS: ange tröskel]**.

## 9.2  Kriterier för att återuppta testarbetet

- Blockerande problem är åtgärdade och verifierade, och röktest är godkänt i miljön.
- Miljön och externa beroenden är åter stabila (eller mock är på plats).
- Testledaren har fattat beslut om återstart och informerat projektledaren.

# 10  Testdokumentation

| **Dokument / artefakt** | **Beskrivning** | **Ansvarig** |
| --- | --- | --- |
| Teststrategi | Övergripande strategi (`test_strategi.md`). | Testledare |
| Testplan | Detta dokument. | Testledare |
| Testanalys och riskmatris | `test_analys.md`. | Testledare |
| Testfall / testdesign | Fullständiga för MUST, checklistor för COULD. Lagras i `test_fall.md` / testverktyg **[SAKNAS]**. | Testare |
| Testdata | Gemensam uppsättning samt återställningsrutin. | Testare |
| Defektlista / felrapporter | Registrerade fel i defektverktyget **[SAKNAS: verktyg]**. | Testare, Utveckling |
| SIT-testrapport | Resultat från SIT, godkänd av testledaren. | Testledare |
| Systemtestrapport | Resultat, testfallsstatus och defektlista, arkiverad senast sista testdagen. | Testledare |
| Acceptansscenarier och testmanus | Godkända av PO. | Product Owner / Verksamhet |
| Teststatusrapport | Löpande till projektledaren. | Testledare |
| Go/No-Go-underlag | Slutrapport, kvalitetsmetriker och kvarstående risker. | Testledare |

# 11  Testaktiviteter

| **ID** | **Aktivitet** | **Ägare** |
| --- | --- | --- |
| A1 | Testplanering och teststrategi | Testledare |
| A2 | Kravanalys (K1–K10) | Testledare / Testare |
| A3 | Testdesign (testfall, scenarier, acceptanskriterier) | Testare |
| A4 | Testdataförberedelse | Testare |
| A5 | Miljöetablering och röktest | Utveckling / Testare **[FÖRSLAG]** |
| A6 | SIT | Testare |
| A7 | Systemtest | Testare |
| A8 | Defect triage och retest | Testledare |
| A9 | Acceptanstest (UAT) | Product Owner / Verksamhet |
| A10 | Regressionstest | Testare |
| A11 | Teststatus och rapportering | Testledare |
| A12 | Go/No-Go-underlag | Testledare |
| A13 | Release och sanity test | Testledare / Utveckling **[FÖRSLAG]** |

# 12  Testmiljö

## 12.1  Hård- och mjukvara

| **Komponent** | **Version / konfiguration** | **Skillnad mot produktion** | **Ansvarig** |
| --- | --- | --- | --- |
| Gemensam testmiljö (webb/app, backend, interna flöden) – SIT och systemtest | [SAKNAS] | Delas av tre team, risk att förändringar krockar. Sannolikt lägre kapacitet än produktion. | [SAKNAS] (dedikerad miljöansvarig från utvecklingen föreslås) |
| Payment Providers testmiljö (Visa, Mastercard, Swish) | [SAKNAS] | Isolerad miljö hos extern part. Kräver separat åtkomst och testdata. Mock som fallback. | Extern leverantör / Testledare |
| Lagersystem (15 år gammalt) | [SAKNAS] | Testmiljön har inte samma datamängd och trafik som produktion. | Lagersystemets förvaltare |
| Delivery Provider / E-post-SMS (testmiljö eller mock) | [SAKNAS] | [SAKNAS] | [SAKNAS] |
| Acceptans-/stagingmiljö | [SAKNAS] | Ska efterlikna produktion, men med begränsad/anonymiserad data och utan skarpa betalningar. | [SAKNAS] |

## 12.2  Testverktyg

| **Verktyg** | **Användningsområde** | **Ansvarig** |
| --- | --- | --- |
| [SAKNAS] | Testfallshantering och rapportering | Testledare |
| [SAKNAS] | Defekthantering | Testledare |
| [SAKNAS] | Automatiserad regression (CI/CD och röktest vid varje driftsättning) | Utveckling / Testare |
| Mock/simulator för betalning | Intern testning oberoende av extern part | [SAKNAS] |

## 12.3  Lokaler

Ej applicerbart (inga särskilda lokaler, enheter eller fysisk utrustning har identifierats). **[SAKNAS: bekräfta]**

# 13  Ansvar

| **Roll** | **Ansvar / mandat** | **Namn / funktion** |
| --- | --- | --- |
| Testledare | Ansvarar för teststrategi, testplan, teststatus och Go/No-Go-underlag. Leder defect triage. Godkänner testfall och rapporter. Beslutar om undantag från entry-kriterier. | [SAKNAS: namn] (Grupp 2) |
| Testare | Utför testdesign, testdata, SIT, systemtest och regression. | Isabella, Johan, Fanny, Anders |
| Utveckling (3 team) | Komponenttest, felrättning, stabila byggen, API-dokumentation, miljö. Konsulteras i testdesign, SIT och systemtest. | [SAKNAS: teamnamn/kontakter] |
| Product Owner | Krav, acceptanskriterier, godkännande av kvarstående fel, ansvarig för acceptanstest tillsammans med verksamheten. | [SAKNAS: namn] |
| Verksamhet / Kundservice / Administratör | Genomför acceptanstest. | [SAKNAS: namn] (minst 2 från kundservice och 1 administratör) |
| Projektledare | Informeras om teststatus, risker och återstående arbete. Beslutar om tidsplanen. | [SAKNAS: namn] |
| Externa leverantörer | Testmiljöer, testdata och support för integrationstest. | [SAKNAS] |

**Beslut:** Teststart beslutas av testledaren utifrån entry-kriterierna. Avbrott beslutas av testledaren. Go/No-Go: testledaren tar fram underlaget, **beslutsfattare [SAKNAS]**.

**RACI (sammanfattning, från `testplan_12_veckor.md`):** Testledaren är *Accountable* för alla aktiviteter. Testare är *Responsible* för testdesign, testdata, SIT, systemtest och regression. Product Owner och verksamhet är *Responsible* för acceptanstest. Utveckling är Responsible tillsammans med testare för defect triage.

# 14  Resurs- och utbildningsbehov

| **Namn / resurs** | **Omfattning** | **Funktion** | **Organisation / team** |
| --- | --- | --- | --- |
| Isabella | 30 effektiva h/vecka | Testare: SIT, testdesign, regression, förbereder systemtestmiljö | Testteam |
| Johan | 30 effektiva h/vecka | Testare: SIT, testdesign, regression | Testteam |
| Fanny | 30 effektiva h/vecka | Testare: analys, testdata, systemtest, stödjer UAT | Testteam |
| Anders | 30 effektiva h/vecka | Testare: analys, testdata, systemtest, teknisk verifiering i UAT | Testteam |
| Testledare | [SAKNAS] | Planering, rapportering, defect triage | Testteam |
| Product Owner | Acceptanstest | Krav, godkännande | [SAKNAS] |
| Kundservice (minst 2) och administratör (1) | Hela UAT-veckan | Acceptanstest | Verksamhet |
| Miljöansvarig från utvecklingen | Under SIT och systemtest | Miljöstabilitet och röktest | Utveckling |

**Kapacitet:** Ursprungligen 4 testare × 30 h = 120 h/vecka. Efter att en testare lämnat projektet är kapaciteten 3 × 30 h = 90 h/vecka (25 % lägre). Se `test_estimera.md` för beräkning och reducerad plan. **[SAKNAS: vilken testare som försvunnit och hur fördelningen i `testplan_12_veckor.md` ska ändras.]**

**Utbildning/onboarding:** Deltagare i acceptanstest får en introduktion på högst en timme om testmanus och felrapportering. Eventuell ersättare behöver introduktion (full effekt efter ca en vecka). Gruppen har uppgett att de är oerfarna testare, vilket ingår i bufferten.

# 15  Tidplan

> **OBS:** Tidplanen nedan kommer från `testplan_12_veckor.md` och bygger på **fyra testare**. Omplaneringen efter att en testare försvann (Uppgift 9 i den filen) är inte gjord. Veckor är relativa (V1–V12). Kalenderdatum **[SAKNAS]**.

| **Aktivitet / milstolpe** | **Start** | **Slut** | **Ansvarig** | **Kommentar** |
| --- | --- | --- | --- | --- |
| Analys | V1 | V2 | Fanny, Anders | |
| Testdesign | V2 | V3 | Isabella, Johan | |
| Testdata | V3 | V4 | Fanny, Anders | |
| **M1** Teststrategi och testplan signerad, kravanalys klar | V2 | V2 | Testledare | |
| **M2** Testdesign klar, kritiska testdata laddad | V4 | V4 | Testledare | |
| SIT | V4 | V6 | Isabella, Johan | Beror på miljö, röktest och enhetstest. |
| Retest | V5 | V9 | Alla | Parallellt med SIT och systemtest. |
| **M3** SIT avslutad (inga blockerande/kritiska fel) | V6 | V6 | Testledare | |
| Systemtest | V6 | V8 | Fanny, Anders | |
| Regression | V8 | V10 | Isabella, Johan | |
| Acceptanstest | V9 | V10 | Anders, Fanny + verksamhet | |
| **M4** Systemtest och primär regression klar, kod fryst | V9 | V9 | Testledare | |
| Release readiness | V10 | V11 | Alla | |
| Go/No-Go | V11 | V11 | Testledare / Projektledare | |
| **M5** UAT signerad, Go/No-Go-underlag presenterat | V11 | V11 | Testledare | |
| Release | V12 | V12 | Alla | |
| **M6** Framgångsrik driftsättning | V12 | V12 | | |

## 15.1  Första testomgången

| **Fas** | **Varaktighet / datum** |
| --- | --- |
| SIT | V4–V6 (3 veckor) |
| Systemtest | V6–V8 (3 veckor) |
| Acceptanstest | V9–V10 (2 veckor) |

## 15.2  Påföljande testomgångar

Retest av rättade fel sker löpande under V5–V9. Regression körs V8–V10 och styrs av risk: MUST-områden fullt ut, SHOULD-områden som kort röktest, COULD-områden regressionstestas inte. Alla rättade kritiska och allvarliga fel omtestas. Efter kodfrysning (efter V9) tillåts endast kritiska buggfixar. Antalet omgångar styrs av felutfallet. Är fler fel än väntat funna i lagersystemet eller betalningen räcker bufferten (58 h) inte, och ett nytt beslut behövs.

# 16  Risker och oförutsedda händelser

| **Risk** | **Konsekvens / kommentar** | **Åtgärd** | **Ägare** | **Prioritet** |
| --- | --- | --- | --- | --- |
| R1: 15 år gamla lagersystemet klarar inte integrationen eller prestandan (risknivå 25) | Fel saldo, sålda varor som inte finns, restorder. Kvarstår vid hög belastning (kampanj). | Tidiga integrationstester (API/meddelandeköer) och prestandatester. Övervaka saldot efter release och ha rutin hos kundservice. | [SAKNAS] | Kritisk |
| R2: Tre utvecklingsteam krockar i den gemensamma testmiljön (20) | Falska fel, förlorad testtid. | Releaseschema för miljön, CI/CD, röktest vid varje driftsättning. | [SAKNAS] | Kritisk |
| R3: Betalningsleverantörens testmiljö instabil eller nere (12) | Betalningstester blockeras. Mock täcker inte callbacks, autentisering och återbetalning. | Mock för SIT. Test mot riktig testmiljö krävs i systemtest. | [SAKNAS] | Hög |
| R4: Kontolåsningen låser inte efter 3 försök (12) | Brute force-attacker möjliga. | Automatiserat säkerhetstest (3+ felförsök, 30 minuters låsning). | [SAKNAS] | Hög |
| R5: Avbeställning avbryter order men återbetalning genomförs inte (10) | Kunder får inte pengarna tillbaka. | Testa flödet i SIT och UAT (EX3/AT-EX3). | [SAKNAS] | Medel |
| R6: Rabattkoder kombineras felaktigt (9) | Ekonomisk förlust. Rabattkod testas endast utforskande. | Rabattkoder aktiveras inte vid lansering. Möjlighet att snabbt stänga av dem. | [SAKNAS] | Medel |
| R7: Dubbeldebitering vid nätverksavbrott (8) | Återbetalningar, kundservice. | Negativa tester: bryt nätverket under betalning. | [SAKNAS] | Medel |
| R8: Kundservice kan ändra priser/behörigheter (8) | Säkerhetsrisk. | Separata testkonton för kundservice och admin. Verifiera 403-svar. | [SAKNAS] | Medel |
| R9: Priser/leveransalternativ kan inte hämtas (8) | Kunden kan inte slutföra köp. | Integrationstest med fiktiva adresser och tunga produkter. | [SAKNAS] | Medel |
| R10: Kundservice har inte tid för acceptanstest (2) | UAT blir inte klart. | Boka resurser tidigt (V2). Färdiga och enkla testmanus. | [SAKNAS] | Låg |
| En testare har lämnat projektet, releasedatum ligger fast | Kapaciteten minskar 25 % (480 → 360 h). Ursprunglig plan saknar timmar. | Reducerad plan på 302 h, 58 h buffert. Alternativ: ersättare, utvecklare tar regression, eller flytta release ca 1 vecka. | Testledare | Hög |
| Reducerad testomfattning (kvarstående risker) | Fel i sök, filter, produktinformation, orderhistorik och rabattkoder kan nå produktion. Äldre webbläsare ger avbrutna köp. Reducerad regression kan missa följdfel. Tillgänglighetslagkrav kanske inte uppfylls. | Förstärkt övervakning efter release, beredskapsgrupp de första dagarna, möjlighet att stänga av rabattkoder, tydlig rollback-plan. | Testledare / Projektledare | Hög |
| Verksamhet/externa beroenden försenas | UAT och SIT blir försenade. | Se kritiska beroenden i `testplan_12_veckor.md`. | [SAKNAS] | Medel |

# 17  Godkännande av testplanen

| **Namn / roll** | **Beslut** | **Datum** | **Kommentar** |
| --- | --- | --- | --- |
| Testledare | [SAKNAS] | [SAKNAS] | |
| Product Owner | [SAKNAS] | [SAKNAS] | Ska godkänna enligt ST-EN4. |
| Projektledare | [SAKNAS] | [SAKNAS] | |
| Utvecklingsteamens representant | [SAKNAS] | [SAKNAS] | |
