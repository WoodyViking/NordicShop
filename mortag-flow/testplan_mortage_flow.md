# TESTPLAN

**NordFinance**  
Projekt MortgageFlow  
Testplan för MortgageFlow – nytt bolånesystem, release 1.0  
**Version 1.0**

## Dokumenthistorik

| **Version** | **Datum** | **Författare** | **Kommentar** |
| --- | --- | --- | --- |
| 0.1 | 2026-10-15 | Grupp 2 | Dag 1 av MortgageFlow testplanering. Utkast utifrån mallen. |
| 1.0 | 2026-10-16 | Grupp 2 | Första kompletta version (Del 2). Bygger på teststrategi version 1.0. |
|  |  |  |  |

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

**TP-MF-1.0** – Testplan för MortgageFlow, release 1.0 (första produktionssättning).
 
Identifieraren följer formen *TP (testplan) – MF (MortgageFlow) – versionsnummer*.

# 2  Inledning

*Beskriv sammanhanget för testplanen och vad dokumentet ska styra.*

\<Testplanen styr testarbetet inför första produktionssättningen av MortgageFlow, från testanalys i vecka 1 till Go/No-Go i vecka 12. Den kompletterar teststrategin (version 1.0) genom att ange vad som testas, hur, när, av vem och under vilka förutsättningar. Strategin beskriver hur MortgageFlow normalt testas. Denna plan beskriver det konkreta upplägget för release 1.0 och eventuella avsteg från strategin (se avsnitt 6).>

## 2.1  Kortfattad beskrivning

Uppgift(tas bort innan inlämning): *Sammanfatta vilken testinsats planen avser, vilken release/version som testas, målgrupp samt vem som ansvarar för dokumentet.*

Planen avser all testning av MortgageFlow release 1.0 på nivåerna SIT, systemtest, E2E, acceptanstest samt regression och omtest. Komponenttest utförs av utvecklingsteamen i DEV och ingår inte i planens genomförande, men dess resultat är en förutsättning för teststart (se 7.1).
 
Målgrupp: testteamet, Product Owner (PO), projektledare, de tre utvecklingsteamen, verksamhetsrepresentanter, säkerhetsspecialist, DevOps och representanten från kreditupplysningstjänsten.
 
Dokumentansvarig är testledaren. Planen skrivs av Grupp 2.

## 2.2  Bakgrund

Uppgift(tas bort innan inlämning): *Beskriv projektets eller förändringens bakgrund, verksamhetsbehovet och varför testningen genomförs.*

NordFinance lanserar det nya interna bolånesystemet MortgageFlow. Bolånehandläggare, senior handläggare och administratörer ska använda det för att ta emot bolåneansökningar, kontrollera kunduppgifter, genomföra kreditbedömningar, hantera dokument, godkänna eller avslå bolån och kommunicera beslut till kunden.
 
Systemet är verksamhetskritiskt. Fel kan leda till ekonomiska förluster, felaktiga kreditbedömningar, säkerhetsproblem, GDPR-incidenter och kundmissnöje. Projektet har 12 veckor kvar till produktionssättning, och testteamet har fått uppdraget att planera, leda, följa upp och avsluta testarbetet. Testningen genomförs för att ge projektet och verksamheten ett tillförlitligt underlag för beslutet om Go/No-Go.

## 2.3  Syfte och mål

Uppgift(tas bort innan inlämning): *Beskriv vad testerna ska verifiera och vilka konkreta mål som ska vara uppnådda efter avslutad testperiod.*

**Syfte:** Verifiera att MortgageFlow uppfyller de funktionella och icke-funktionella kraven och att systemet tillsammans med sina beroende system är säkert nog att produktionssättas, samt redovisa kvarstående risker på ett sätt som gör det möjligt att fatta ett välgrundat Go/No-Go-beslut.
 
**Mål vid avslutad testperiod:**
 
- Alla kritiska affärsflöden (E2E-1 till E2E-5, se avsnitt 4) är testade.
- Alla högriskområden (R1–R6 i teststrategin) är testade och inga kritiska eller blockerande fel är öppna.
- Alla integrationer mot kreditupplysningstjänst, kund-/personregister, e-posttjänst, MFA/autentisering och dokumentlagring är verifierade, inklusive felfall och timeout.
- Verksamheten har genomfört och dokumenterat acceptanstest i ACC.
- Regression och omtest är genomförda efter sista leveransen.
- Kvarstående risker är dokumenterade och har en rekommendation (Go, Conditional Go eller No-Go) till PO och projektledare.

## 2.4  Termer och förkortningar

Uppgift(tas bort innan inlämning): *Förklara projektspecifika termer, förkortningar, verktygsnamn och begrepp som behövs för att förstå testplanen.*

| **Term** | **Förklaring** |
| --- | --- |
| Ärende | En bolåneansökan i MortgageFlow med uppgifter, dokument, status och logg. |
| Skuldkvot | Kundens totala skulder i förhållande till årsinkomsten. Över 6 ger hög risk. |
| Belåningsgrad | Lånebelopp i förhållande till objektvärde. Över 85 % ger varning. |
| Riskklass | Systemets bedömning av ärendets risknivå utifrån affärsreglerna. |
| Dubbelgodkännande | Lån över 5 MSEK godkänns av handläggare och därefter av senior handläggare. |
| MFA | Multifaktorautentisering. |
| SIT | Systemintegrationstest. |
| E2E | End-to-end-test av ett helt affärsflöde. |
| UAT | Acceptanstest som genomförs av verksamheten i ACC. |
| DEV / SYS / ACC / PROD | Utvecklings-, system-, acceptanstest- och produktionsmiljö. |
| Stub / mock | Simulerat system som ersätter ett riktigt beroende system. |
| Smoke test | Kort test efter deployment som visar att miljön är redo för vidare test. |
| Omtest | Test som visar att en rättad defekt är löst. |
| Regressionstest | Test som visar att tidigare fungerande funktionalitet inte påverkats. |
| Severity / Priority | Hur allvarligt ett fel är / hur snabbt det ska åtgärdas. |
| Kritiskt fel (S1) | Felet stoppar ett affärsflöde, ger fel kreditbeslut, säkerhetsbrist eller dataexponering. Ingen workaround. |
| Allvarligt fel (S2) | Viktig funktion fungerar fel men workaround finns. |
| Mindre fel (S3 / S4) | Begränsad påverkan respektive kosmetiskt fel. |
| Blockerande fel | Fel som hindrar fortsatt testning av en funktion eller ett flöde. |
| P1 / P2 / P3 | Testprioritet. P1 = hög risk och körs alltid, P2 = medel, P3 = låg. |
| Entry / Exit criteria | Start- respektive slutkriterier. |
| Release Readiness | Genomgång vecka 11 av om releasen är redo för Go/No-Go. |
| Go/No-Go | Beslutstillfälle om produktionssättning. |
| Kvarstående risk | Risk som finns kvar efter genomförd testning. |
| PO | Product Owner. |
| GDPR | EU:s dataskyddsförordning. |

## 2.5  Hänvisningar till andra dokument

Uppgift(tas bort innan inlämning): *Lista relevanta styrande eller stödjande dokument, till exempel kravspecifikation, projektplan, teststrategi, felhanteringsprocess och testspecifikationer.*

| **Dokument** | **Beskrivning / sökväg / länk** |
| --- | --- |
| Teststrategi för MortgageFlow, version 1.0 | Styrande strategi: testnivåer, testmiljö, testobjekt och riskbedömning R1–R10. teststrategi.md |
| Kravunderlag | Slutprojekt – Teststrategi och planering, Case: MortgageFlow (funktionella och icke-funktionella krav, systemkarta, tidplan). |
| Riskregister | Produkt- och projektrisker med bedömning och åtgärd. Produktrisker i teststrategin 1.1, projektrisker i avsnitt 15. |
| Behörighetsmatris | Vilka roller får se och göra vad. \<Länk, tas fram vecka 1–2> |
| Testspecifikation / testfall | Testfall per testobjekt, kopplade till krav och risk. \<Länk till testverktyg> |
| Testdatafil | Syntetiska testpersoner, kreditupplysningssvar och testfiler. \<Länk, tas fram vecka 3> |
| SQL-skript | Skript för att skapa och återställa testdata i SYS och ACC. \<Länk> |
| Felhanteringsprocess | Defekters livscykel, severity, priority och triage. \<Länk> |
| Testrapport | Slutrapport (Del 6). |

## 2.6  Öppna frågor

Uppgift(tas bort innan inlämning): *Lista frågor eller beslut som ännu inte är lösta och som kan påverka testplanen.*

Frågorna nedan är hämtade från teststrategin 1.4 och med frågor dyker upp vid tesstplaneringen.

| **Fråga** | **Ansvarig** | **Senast datum** | **Status** |
| --- | --- | --- | --- |
| Gäller gränserna exakt? Är skuldkvot 6,0 hög risk, belåningsgrad 85,0 % varning och exakt 5 000 000 SEK dubbelgodkännande? | Product Owner | Vecka 1 | Öppen |
| Hur räknas riskklass fram och hur många riskklasser finns? | Product Owner / verksamhet | Vecka 1 | Öppen |
| Vilka beslut får senior handläggare överstyra, och ska motivering krävas och loggas? | Product Owner | Vecka 1 | Öppen |
| Räknas fem felaktiga inloggningsförsök i följd, och nollställs räknaren efter lyckad inloggning? | Product Owner / säkerhetsspecialist | Vecka 1 | Öppen |
| Hur ska systemet bete sig när kreditupplysningstjänsten inte svarar? | Product Owner / arkitekt | Vecka 2 | Öppen |
| Finns testmiljö hos kreditupplysningstjänsten med styrbara testsvar, eller behövs en stub? | Representant kreditupplysningstjänsten | Vecka 2 | Öppen |
| Hur sätts status Utbetald – manuellt eller via integration? | Product Owner | Vecka 2 | Öppen |
| Får maskerad produktionsdata användas i ACC, eller endast syntetisk data? | Projektledare / dataskyddsansvarig | Vecka 2 | Öppen |
| Vad menas med ”normal belastning”, och kan prestandatest göras i SYS? | Product Owner / DevOps | Vecka 2 | Öppen |
| Vem genomför säkerhetstest och ingår penetrationstest? | Säkerhetsspecialist | Vecka 2 | Öppen |
| Vilka versioner av Chrome, Edge och Firefox ska stödjas? | Product Owner | Vecka 2 | Öppen |
| Vilket testverktyg används för krav-, test- och felhantering? | Projektledare / testledare | Vecka 1 | Öppen |
| Vem deltar i Go/No-Go och vem fattar beslutet? | Projektledare | Vecka 3 | Öppen |
| Vilka verksamhetsrepresentanter deltar i UAT och hur mycket tid har de? | Product Owner | Vecka 5 | Öppen |

# 3  Testobjekt

Uppgift(tas bort innan inlämning): *Beskriv vad som ska testas: system, delsystem, funktioner, integrationer, API:er, batchjobb, rapporter eller andra komponenter. Ange gärna version/build och ägare.*

| **Testobjekt** | **Beskrivning** | **Version / build** |
| --- | --- | --- |
| MortgageFlow – webbapplikation och backend/API | Webbgränssnitt (React/TypeScript), affärsregler, ärendehantering, kreditbedömning, beslut, dokument, notifieringar, rapporter, ärendelogg och administration. | Release 1.0. Build anges per deployment i testrapporten. |
| Autentisering och MFA | Inloggning med användarnamn, lösenord och MFA, kontolåsning efter fem försök, automatisk utloggning efter 10 minuter. | Release 1.0 / testkonfiguration. |
| Integration mot kreditupplysningstjänst | REST-integration för kreditvärdighet, betalningsanmärkningar, skuldsaldo och taxerad inkomst. | Enligt leverantörens testmiljö eller stub. |
| Integration mot kund-/personregister | Hämtning av kunduppgifter via personnummer. | Testinstans. |
| Integration mot e-posttjänst | Automatisk e-postbekräftelse till kund vid godkännande. | Testinstans. |
| Dokumenthantering och dokumentlagring | Uppladdning av PDF, JPG och PNG (max 10 MB), virusskanning, versionshantering och loggning. | Release 1.0 / testinstans. |
| Databas och loggning | Krypterad persondata och ärendelogg över vem som ändrat vad och när. | Testdatabas i SYS och ACC. |
 
Ägare för testobjekten är de tre utvecklingsteamen. Ägare för respektive beroende system anges i avsnitt 12.


# 4  Omfattning

Uppgift(tas bort innan inlämning): *Beskriv vad som ingår i testningen. Koppla gärna till krav, affärsflöden, testnivåer, testtyper och prioriterade områden.*

Testningen omfattar alla funktionella och icke-funktionella krav i kravunderlaget och är riskbaserad enligt teststrategin. Högst prioritet (P1) har kreditbedömning och affärsregler, dubbelgodkännande av lån över 5 MSEK, behörighet, säkerhet och skydd av persondata, integrationen mot kreditupplysningstjänsten, inloggning samt loggning och spårbarhet. Riskerna R1–R10 är definierade i teststrategin 1.1.
 
De fem kritiska affärsflödena som körs som E2E-test:
 
- **E2E-1 Standardärende:** ny ansökan → granskning → kreditkontroll → låg risk → godkänd → e-postbekräftelse.
- **E2E-2 Komplettering:** instabil anställning och låg inkomst → komplettering krävs → dokument laddas upp → ny granskning → beslut.
- **E2E-3 Stort lån:** lån över 5 MSEK → handläggare godkänner → senior handläggare godkänner → godkänd.
- **E2E-4 Hög risk:** aktiv betalningsanmärkning → hög risk → senior handläggare → avslag med registrerad orsak.
- **E2E-5 Tjänsten svarar inte:** kreditupplysning uteblir → inget beslut på ofullständiga uppgifter.

| **Område / flöde** | **Testnivå / testtyp** | **Prioritet** | **Kommentar** |
| --- | --- | --- | --- |
| Kreditbedömning och affärsregler (skuldkvot, belåningsgrad, riskklass, aktiva betalningsanmärkningar, instabil anställning) | Systemtest: beslutstabeller, gränsvärdesanalys. E2E-1, E2E-2, E2E-4 | P1 (R1) | Gränsvärden under, på och över 6 och 85 %. Beror på öppna frågor om riskklass. |
| Dubbelgodkännande, lån över 5 MSEK | Systemtest: gränsvärden, behörighet. E2E-3 | P1 (R2) | Lån på 4 999 999, 5 000 000 och 5 000 001 SEK. Ordning handläggare → senior. |
| Behörighet per roll och ärendesynlighet | Systemtest via UI och API, behörighetstest | P1 (R3) | Alla tre roller. Direkta API-anrop utan UI. |
| Persondata, kryptering och GDPR | Säkerhetstest tillsammans med säkerhetsspecialist | P1 (R4) | Inga persondata i loggar eller felmeddelanden. |
| Integration kreditupplysningstjänst | SIT: korrekta svar, felaktiga svar, timeout, upprepade anrop. E2E-5 | P1 (R5) | Stub används om testmiljö saknas. Verkligt beteende verifieras före SIT-avslut. |
| Inloggning, MFA, kontolåsning, automatisk utloggning | Systemtest, säkerhetstest | P1 (R6) | Gränsvärden 4, 5 och 6 försök, 9:59 och 10:00 min inaktivitet. |
| Statusflöde och ärendelogg | Systemtest: tillståndsbaserad testning | P1 (R7) | Tillåtna och otillåtna övergångar. Loggning av vem och när. |
| Registrering och validering av ansökan | Systemtest: ekvivalensklasser, gränsvärden | P2 | Personnummer, obligatoriska fält, inkomst, lånebelopp ≤ objektvärde − kontantinsats. |
| Beslut (godkänn, avslå, begär komplettering) | Systemtest, E2E | P1 | Avslagsorsak obligatorisk. Beslut loggas. |
| Dokumenthantering | Systemtest, SIT | P2 (R8) | Filtyper, 10 MB-gräns, virusskanning med ofarlig standardtestfil, versionshantering. |
| E-postbekräftelse till kund | SIT, E2E | P2 (R10) | Rätt mottagare och innehåll. Hantering när e-posttjänsten inte svarar. |
| Integration kund-/personregister, MFA, dokumentlagring | SIT | P2 | Korrekta svar, felfall och timeout. |
| Administration (användare, roller, systeminställningar, upplåsning) | Systemtest, behörighetstest | P2 | Administratörens upplåsning av låst konto. |
| Rapporter och statistik (senior handläggare) | Systemtest | P3 | Behörighet och rimlighet i siffror. |
| Prestanda: 2 s svarstid, 500 samtidiga användare | Prestandatest | P2 (R9) | Förutsätter definition av normal belastning och lämplig miljö. |
| Webbläsarkompatibilitet: Chrome, Edge, Firefox | Systemtest (kompatibilitet) | P2 | P1-flöden körs i alla tre webbläsare, övriga stickprov. |
| Verksamhetens arbetssätt | Acceptanstest i ACC | P1 | Scenariobaserat av handläggare och senior handläggare. |
| Regression och omtest | Regressionstest, omtest | P1 körs alltid | Automatisering av inloggning, affärsregler och behörighet först. |

# 5  Avgränsning

Uppgift(tas bort innan inlämning): *Beskriv uttryckligen vad som inte ska testas i denna testinsats och varför. Ange vid behov vem som ansvarar för testningen utanför denna plan.*

| **Avgränsning** | **Motivering** | **Ansvar utanför planen** |
| --- | --- | --- |
| Komponent-/enhettest | Utförs löpande av utvecklarna i DEV. Resultatet följs upp men utförs inte av testteamet. | Utvecklingsteamen |
| Beroende systems interna logik (hur kreditupplysningstjänsten räknar fram kreditvärdighet, e-posttjänstens leverans, kund-/personregistrets innehåll) | Ägs och testas av respektive leverantör. MortgageFlows hantering av svar, fel och uteblivna svar ingår. | Respektive systemägare |
| Penetrationstest och djupare säkerhetsgranskning | Kräver särskild kompetens. Ingår endast om säkerhetsspecialisten beslutar det (öppen fråga). | Säkerhetsspecialist |
| Infrastruktur, backup/återställning och övervakning (load balancer, Kubernetes, brandvägg, Prometheus/Grafana, ELK) | Ägs av DevOps. Testteamet verifierar bara att miljön är redo och att loggar syns. | DevOps |
| Webbläsare och versioner utöver Chrome, Edge och Firefox, samt mobila enheter | Inte krav. Systemet är ett internt handläggarsystem. | Ej applicerbart |
| Test med verkliga kunders persondata | GDPR-risk. Endast syntetisk data om inget annat beslutas (öppen fråga). | Projektledare / dataskyddsansvarig |
| Migrering av befintliga ärenden och data | Inte nämnt i kravunderlaget. Ingår inte om inte annat beslutas. | Projektledare |
| Utbildning av handläggare och driftsättningsrutiner | Ingår inte i testuppdraget. | Projektledare / verksamhet |
| Fullständig regression av P3-fall | Prioriteras bort vid tidsbrist och redovisas som kvarstående risk. | Testledare (redovisning) |

# 6  Tillvägagångssätt

Uppgift(tas bort innan inlämning): *Beskriv hur testningen ska genomföras, exempelvis riskbaserat, kravbaserat, utforskande eller iterativt. Beskriv prioritering, felhantering, omtest, regression, rapportering och eventuell automatisering.*

Testningen följer teststrategin (version 1.0) och är **riskbaserad, kravbaserad och iterativ**.
 
**Riskbaserat.** Riskerna R1–R10 styr vad som testas först och hur djupt. P1-områden designas och testas först och körs i alla omgångar. P2 körs i den mån tiden räcker och P3 kan utelämnas. Det som inte körs redovisas som kvarstående risk.
 
**Kravbaserat.** Varje krav i kravunderlaget kopplas till minst ett testfall. Kopplingen mellan krav, risk och testfall hålls i testverktyget så att testtäckningen kan följas upp.
 
**Testdesign.** Gränsvärdesanalys (skuldkvot, belåningsgrad, 5 MSEK, 10 MB, fem inloggningsförsök, 10 minuter), beslutstabeller (affärsregler, riskklass), tillståndsbaserad testning (ärendestatus), ekvivalensklasser (validering) samt utforskande testning med tidsbegränsade sessioner och testcharter, särskilt i systemtest och E2E.
 
**Testfall.** Skrivs i vecka 1–2 med granskning av PO och verksamhet. Testfall för P1 granskas först.
 
**Beroende system.** Stubbar används om en tjänst saknar testmiljö, men det riktiga beteendet verifieras innan SIT avslutas.
 
**Felhantering.** Fel registreras i testverktyget och följer New → Analysis → In Progress → Ready for Retest → Closed. Varje fel får severity (S1–S4) och priority. Testledaren leder defect triage tre gånger i veckan under SIT och systemtest, därefter dagligen under regression. Fel i beroende system rapporteras till systemets ägare.
 
**Omtest och regression.** Varje rättat fel omtestas av den som hittade det eller av Testare D. Efter varje leverans körs smoke test, därefter regression av P1. Stabila affärskritiska tester (inloggning, kreditregler, behörighet) automatiseras först av Testare D.
 
**Rapportering.** Testledaren följer Planned vs Executed, Passed, Failed, Blocked, Not Run, öppna defekter per severity och risktäckning. Statusrapport skickas till projektledare och PO varje vecka och dagligen under UAT och regression. Före Go/No-Go lämnar testledaren rekommendation: Go, Conditional Go eller No-Go.
 
**Avsteg från strategin.** Inga avsteg i version 1.0. Eventuella avsteg dokumenteras här och i dokumenthistoriken.

## 6.1  Iterationer

Uppgift(tas bort innan inlämning): *Beskriv testcykler/testomgångar och vad som sker i varje cykel, till exempel test, omtest och regression.*

| **Fas** | **Syfte** | **Genomförande** |
| --- | --- | --- |
| Testanalys och testdesign (v1–2) | Förstå krav, bryta ner risker, skriva och granska testfall, få svar på öppna frågor. | Alla testare. Testfall granskas av PO och verksamhet. Behörighetsmatris och testdatabehov tas fram. |
| Förberedelse (v3) | Testdata och miljö redo före teststart. | Testare C tar fram testdata. DevOps och utvecklingsteamen levererar och verifierar SYS. Smoke test av miljön. |
| SIT – omgång 1 (v4) | Verifiera integrationer och hitta fel tidigt. | Testare A med utvecklare. Alla integrationer, både korrekta svar och felfall. |
| SIT – omgång 2 och systemtest – omgång 1 (v5–6) | Retest av SIT-fel samt första funktionella systemtestet. | Testare A, B, D. P1 först. Smoke test efter varje deployment. |
| Systemtest – omgång 2 och E2E (v7–8) | Slutföra systemtest, köra E2E-flöden, behörighet, säkerhet och prestanda. | Testare B, C, D, A och säkerhetsspecialist. Omtest av rättade fel. |
| UAT (v8–9) | Verksamhetens acceptans i ACC. | Verksamhetsrepresentanter med stöd av Testare C. Dokumenterat godkännande. |
| Regression och omtest (v9–10) | Visa att rättningar fungerar och inget har gått sönder. | Testare D med övriga. P1-regression alltid, P2 om tid finns. Eventuell ny UAT-körning vid kritiska fel. |
| Release Readiness (v11) | Bedöma om releasen är redo. | Testledare sammanställer testrapport, kvarstående risker och rekommendation. |
| Go/No-Go och produktionssättning (v12) | Beslut och smoke test i PROD. | Beslut av PO och projektledare. Smoke test i PROD efter produktionssättning. |

# 7  Start- och slutkriterier

Uppgift(tas bort innan inlämning): *Definiera objektiva kriterier för när testningen får starta och när den kan betraktas som avslutad.*

## 7.1  Kriterier för att inleda testarbetet

**För SIT och systemtest (SYS):**
 
- SYS är installerat med rätt version, konfiguration och anslutna integrationer (eller stubbar), och smoke test är godkänt.
- Komponenttester är körda av utvecklingsteamen utan öppna kritiska fel.
- Testdata för minst P1-områdena finns i SYS och kan återställas med SQL-skript.
- Testare har konton, roller och MFA-enheter i SYS.
- Krav och acceptanskriterier är tillräckligt tydliga, och öppna frågor som rör P1-områden (gränsvärden, riskklass, inloggningsräkning) är besvarade eller har dokumenterat antagande.
- Minst 90 % av P1-testfallen och 70 % av övriga testfall är framtagna och granskade.
- Testverktyg och felhanteringsprocess är på plats.
**För UAT (ACC):**
 
- Systemtest av P1 är genomfört, och inga kritiska eller blockerande fel är öppna.
- ACC är installerat med releasekandidaten, anslutna integrationer och syntetisk (eller beslutad maskerad) data.
- Smoke test i ACC är godkänt.
- Verksamhetsrepresentanter är bokade och UAT-scenarier är godkända av PO.

## 7.2  Kriterier för att avsluta testarbetet

- Alla planerade P1-tester är genomförda, och minst 95 % av P1-testfallen är godkända. Resterande avvikelser är analyserade.
- Alla E2E-flöden (E2E-1 till E2E-5) är körda utan öppna S1/S2-fel.
- Inga öppna kritiska (S1) eller allvarliga (S2) fel i P1-områdena. Öppna S3/S4-fel är redovisade och accepterade av PO.
- Alla P1-defekter som rättats är omtestade, och regression av P1 är körd på den slutliga releasekandidaten.
- Minst 90 % av P2-testfallen är genomförda.
- UAT är genomfört och godkänt av verksamheten.
- Säkerhetstestet är genomfört med en säkerhetsspecialist och inga kritiska säkerhetsfel återstår.
- Prestandakraven (svarstid 2 s, 500 användare) är verifierade, eller avvikelsen är dokumenterad och accepterad.
- Kvarstående risker är dokumenterade i testrapporten och accepterade av PO och projektledare.


# 8  Avbrytande- och återupptagandekriterier

Uppgift(tas bort innan inlämning): *Definiera när testningen ska pausas eftersom fortsatt testning inte är meningsfull, samt vad som krävs för att återuppta den.*

## 8.1  Kriterier för att avbryta testerna

- SYS eller ACC är instabil eller otillgänglig.
- Smoke test misslyckas efter en deployment.
- Fler än 20 % av planerade testfallen i en testomgång är blockerade.
- Fler än fem öppna kritiska fel (S1) eller ett fel som blockerar ett helt affärsflöde, till exempel inloggning eller kreditkontroll.
- Nödvändiga nyckelpersoner (utvecklare, DevOps, säkerhetsspecialist, verksamhetsrepresentanter), testdata, kreditupplysningstjänst eller stub saknas.
- Leveransen bedöms inte vara testbar, eller felfrekvensen är så hög att test ger lite nytt värde.
- Verkliga persondata upptäcks i testmiljö (testet stoppas omedelbart och GDPR-ansvarig informeras).
Beslutet om avbrott fattas av testledaren i samråd med projektledaren.

## 8.2  Kriterier för att återuppta testarbetet

- Blockerande problem är åtgärdade och verifierade med ett godkänt smoke test.
- Miljö och beroenden är åter stabila, och testdata är återställda.
- Ny version eller rättning är levererad med release notes.
- Beslut om återstart är fattat av testledaren tillsammans med projektledaren.
- Omplanering är gjord och påverkan på tidplan och omfattning är dokumenterad.

# 9  Testdokumentation

Uppgift(tas bort innan inlämning): *Beskriv vilka testartefakter som ska tas fram, var de lagras och vem som ansvarar för dem.*

| **Dokument / artefakt** | **Beskrivning** | **Ansvarig** |
| --- | --- | --- |
| Teststrategi för MortgageFlow, version 1.0 | Övergripande strategi. | Testledare |
| Testplan (TP-MF-1.0) | Detta dokument. | Testledare |
| Testfall / testspecifikation | Testfall med krav- och riskkoppling, förutsättningar, steg och förväntat resultat. | Testare A–D, per område |
| Behörighetsmatris | Roll mot funktion och data. | Testare D |
| Testdata och SQL-skript | Syntetiska personer och skript för återställning. | Testare C |
| Spårbarhetsmatris | Krav → risk → testfall → resultat. | Testledare |
| Testlogg / exekveringsresultat | Resultat per testfall, miljö, build och datum. | Respektive testare |
| Felrapporter | Defekter med severity, priority, steg, miljö och bevis. | Respektive testare |
| Statusrapporter | veckovis (dagligen under UAT och regression). Planned vs Executed, Passed, Failed, Blocked, defekter per severity. | Testledare |
| UAT-scenarier och UAT-protokoll | Scenarier och dokumenterat verksamhetsgodkännande. | Testare C, verksamhetsrepresentanter |
| Release Readiness-underlag | Sammanställning inför Go/No-Go med kvarstående risker. | Testledare |
| Testrapport | Slutrapport med resultat, risker och rekommendation. | Testledare |

# 10  Testaktiviteter

Uppgift(tas bort innan inlämning): *Lista de viktigaste aktiviteterna från testanalys och planering till genomförande, felhantering, uppföljning och testrapport.*

| **ID** | **Aktivitet** | **Ägare** |
| --- | --- | --- |
| A1 | Testanalys: analysera krav, risker och öppna frågor. Koppla krav till risk. | Testledare, Testare A–D |
| A2 | Testdesign: skriva och granska testfall (P1 först). Ta fram behörighetsmatrisen. | Testare A–D, PO, verksamhet |
| A3 | Ta fram testdata, SQL-skript och testfiler. | Testare C |
| A4 | Miljöförberedelse: deployment, konfiguration, konton, MFA och smoke test av SYS. | DevOps, utvecklingsteamen, Testare A |
| A5 | SIT: kreditupplysning, personregister, e-post, MFA och dokumentlagring (korrekta svar, felfall, timeout). | Testare A |
| A6 | Systemtest funktionellt: inloggning, ansökan, status, kreditregler, stora lån, dokument, beslut. | Testare B |
| A7 | Behörighets- och regressionsautomation: behörighet per roll via UI och API, automatisering av P1. | Testare D |
| A8 | Säkerhets- och prestandatest: kryptering, kontolåsning, utloggning, 2 s, 500 användare. | Säkerhetsspecialist, Testare A |
| A9 | E2E-test av flödena E2E-1 till E2E-5 inklusive kontroll av ärendelogg. | Testare B, Testare C |
| A10 | Felhantering: registrera, triagera och följa upp defekter. | Testledare, Testare A–D |
| A11 | Omtest av rättade fel och smoke test efter varje deployment. | Testare D, den som rapporterat felet |
| A12 | UAT-förberedelse och stöd under acceptanstest i ACC. | Testare C, verksamhet |
| A13 | Regressionstest av P1 (och P2 om tid finns) på releasekandidaten. | Testare D |
| A14 | Statusrapportering och uppföljning av tidplan, risker och miljöbehov. | Testledare |
| A15 | Release Readiness: sammanställa resultat, kvarstående risker och rekommendation. | Testledare |
| A16 | Testrapport. | Testledare |
| A17 | Stöd vid Go/No-Go och smoke test i PROD. | Testledare, Testare D |

# 11  Testmiljö

Uppgift(tas bort innan inlämning): *Beskriv testmiljön och viktiga skillnader mot produktion. Dokumentera integrationer, beroenden, testdata, åtkomst och ansvar.*

Miljökedjan är DEV → SYS → ACC → PROD enligt teststrategins avsnitt 3. En miljö är redo för test först när rätt version är installerad, konfigurationen är rätt, integrationerna är anslutna, testarna har åtkomst och rätt testdata finns. Testmiljön SYS delas av SIT, systemtest, API-test, E2E, regression och omtest. Deploymentar till SYS planeras därför gemensamt av testledare, DevOps och de tre utvecklingsteamen så att pågående test inte stör varandra.

## 11.1  Hård- och mjukvara

| **Komponent** | **Version / konfiguration** | **Skillnad mot produktion** | **Ansvarig** |
| --- | --- | --- | --- |
| SYS – MortgageFlow (webbapp React/TypeScript, backend/API) | Releasekandidat per deployment, build anges i testlogg. | Delas av alla tester och tre utvecklingsteam. Mindre kapacitet, vilket påverkar prestandatest. | DevOps / utvecklingsteamen |
| ACC – MortgageFlow | Releasekandidat via releaseprocessen. | Ska likna PROD så mycket som möjligt. Endast syntetiska data om inget annat beslutas. | DevOps |
| Kreditupplysningstjänst (REST) | Leverantörens testmiljö eller stub (öppen fråga). | Förutbestämda svar per testpersonnummer. Stub fångar inte alla verkliga felkoder och svarstider. | Representant kreditupplysningstjänst / Testare A |
| Kund-/personregister | Testinstans med testpersoner. | Endast testpersoner. | DevOps |
| E-posttjänst (SMTP) | Testinstans med uppfångad post. | Inga riktiga kunder nås. | DevOps |
| Autentisering och MFA (AD/LDAP, MFA) | Testkonfiguration, testkonton och testenheter per roll. | Testkonton i stället för riktiga användare. | DevOps / säkerhetsspecialist |
| Dokumentlagring och virusskanning | Testinstans. | Virusskanning verifieras med ofarlig standardtestfil. | DevOps |
| Databas (PostgreSQL) | Separat testdatabas, kryptering som i PROD. Återställs med SQL-skript. | Endast testdata. | DevOps |
| Klienter | Windows-/macOS-klient med Chrome, Edge och Firefox (versioner: öppen fråga). | Testklienter. | Testare B |


## 11.2  Testverktyg

| **Verktyg** | **Användningsområde** | **Ansvarig** |
| --- | --- | --- |
| Testverktyg för krav-, test- och felhantering (val ej beslutat, öppen fråga) | Testfall, exekvering, spårbarhet, felrapporter och rapportering. | Testledare |
| API-testverktyg (t.ex. Postman) | API- och integrationstest, behörighetstest direkt mot API. | Testare A |
| Automationsramverk (t.ex. Playwright, Cypress eller Selenium) | Automatiserad regression och smoke test. | Testare D |
| Prestandaverktyg (t.ex. JMeter eller k6) | Last- och svarstidstest med upp till 500 samtidiga användare. | Testare A |
| Webbläsarnas utvecklarverktyg | Felsökning och kontroll av sessioner och nätverkstrafik. | Testare B, D |
| ELK Stack (logg) | Kontroll av ärendelogg, kontroll att persondata inte loggas i klartext. | DevOps / Testare A |
| Databasverktyg (SQL-klient) | Verifiera sparade data, kryptering och återställning med SQL-skript. | Testare C |
| Uppfångad e-post i testinstans | Verifiera e-postbekräftelser. | Testare B |

## 11.3  Lokaler

Uppgift(tas bort innan inlämning): *Beskriv särskilda lokaler, enheter eller fysisk utrustning som krävs. Om ej relevant, ange Ej applicerbart.*

Ej applicerbart, men fysiska MFA-enheter finns beskrivna i 11.1. Testningen sker via webbläsare i ordinarie arbetsmiljö och kan genomföras på distans.

# 12  Ansvar

Uppgift(tas bort innan inlämning): *Tydliggör ansvar, mandat, eskaleringsvägar och vem som fattar beslut om exempelvis teststart, avbrott och Go/No-Go.*

| **Roll** | **Ansvar / mandat** | **Namn / funktion** |
| --- | --- | --- |
| Projektledare | Övergripande ansvar för projektet och tidplanen. Beslutar tillsammans med PO om Go/No-Go. Hanterar eskalering. | Projektledare |
| Product Owner (PO) | Besvarar kravfrågor, godkänner testfall och accepterar kvarstående risker. Fattar Go/No-Go tillsammans med projektledare. | Product Owner |
| Testledare | Ansvarar för testplan, strategi, planering, uppföljning, rapportering och defect triage. Beslutar om teststart, avbrott och återupptagande tillsammans med projektledare. Ger rekommendation vid Go/No-Go. | Testledare |
| Testare A | API, integration, tekniska tester. SIT och prestandatest. | Testare A |
| Testare B | Funktionellt systemtest och E2E. Kompatibilitet i webbläsare. | Testare B |
| Testare C | Bankverksamhet, UAT och testdata. Stöd till verksamheten. | Testare C |
| Testare D | Regression, automation och behörighet. Omtest och smoke test. | Testare D |
| Utvecklingsteam 1–3 | Komponenttest, rättning av fel, deployment till SYS/ACC enligt plan, support vid SIT. | Utvecklingsteamen |
| Verksamhetsrepresentanter | Genomför UAT, godkänner scenarier och ger verksamhetens acceptans. | Bolånehandläggare / senior handläggare |
| Säkerhetsspecialist | Säkerhetstest, bedömning av säkerhets- och GDPR-risker. | Säkerhetsspecialist |
| DevOps | Miljöer, deployment, konfiguration, åtkomst, loggar och återställning. | DevOps |
| Representant kreditupplysningstjänst | Testmiljö eller testsvar, felsökning av integrationen. | Extern representant |

**En möjlig Eskaleringsväg:** Testare → Testledare → Projektledare / PO. Blockerare i miljö eskaleras direkt till DevOps och därefter till projektledare om de inte åtgärdats inom en arbetsdag.

# 13  Resurs- och utbildningsbehov

Uppgift(tas bort innan inlämning): *Ange resurser, omfattning/tillgänglighet, funktion och eventuella utbildnings- eller onboardingbehov.*

| **Namn / resurs** | **Omfattning** | **Funktion** | **Organisation / team** |
| --- | --- | --- | --- |
| Testledare | 100 %, vecka 1–12 | Planering, ledning, rapportering | Testteamet |
| Testare A | 100 %, vecka 1–10, därefter stöd | API, integration, prestanda | Testteamet |
| Testare B | 100 %, vecka 1–10, därefter stöd | Funktionellt systemtest, E2E | Testteamet |
| Testare C | 100 %, vecka 1–10, därefter stöd | Testdata, UAT, bankverksamhet | Testteamet |
| Testare D | 100 %, vecka 1–12 | Regression, automation, behörighet | Testteamet |
| Utvecklare | Daglig tillgänglighet för felrättning, SIT-stöd och deployment | Rättning, support | Utvecklingsteam 1–3 |
| Verksamhetsrepresentanter | Heltid under UAT (v8–9), samt granskning av testfall i v2 | UAT, granskning | NordFinance verksamhet |
| Säkerhetsspecialist | Cirka 5 dagar i systemtest (v5–8) | Säkerhetstest | Projektet |
| DevOps | Daglig tillgänglighet vid deployment, miljöproblem och SQL-återställning | Miljöer | Projektet |
| Representant kreditupplysningstjänst | Tillgänglig under SIT (v4–5) | Testsvar, felsökning | Extern leverantör |
 
**Utbildnings- och onboardingbehov:**
 
- Testare B och D behöver kunskap om bolånes affärsregler från Testare C och verksamheten (workshop i vecka 1).
- Alla testare behöver introduktion i testverktyget, felhanteringsprocessen och severity-/priority-skalan.
- Verksamhetsrepresentanter behöver kort introduktion i ACC, testscenarier och hur fel rapporteras innan UAT.
- Testare D behöver tillgång till och eventuell utbildning i valt automationsramverk.

# 14  Tidplan

Uppgift(tas bort innan inlämning): *Beskriv testperioden, viktiga milstolpar och planerade testomgångar. Anpassa efter projektets leveransmodell.*

Tidplanen anges i projektveckor (vecka 1–12 räknat från projektets start).

| **Aktivitet / milstolpe** | **Start** | **Slut** | **Ansvarig** | **Kommentar** |
| --- | --- | --- | --- | --- |
| Testanalys och testdesign | Vecka 1 | Vecka 2 | Testledare / Testare A–D | Besvara öppna frågor, skriva och granska testfall. |
| Testdata och miljöförberedelser | Vecka 3 | Vecka 3 | Testare C / DevOps | Startkriterier för SIT ska vara uppfyllda i slutet av veckan. |
| SIT | Vecka 4 | Vecka 5 | Testare A | Alla integrationer inklusive felfall. |
| Systemtest (inkl. behörighet, säkerhet, prestanda) | Vecka 5 | Vecka 8 | Testare B, D, A, säkerhetsspecialist | Börjar parallellt med slutet av SIT. |
| E2E-test | Vecka 7 | Vecka 8 | Testare B, C | Efter avslutat SIT. |
| UAT | Vecka 8 | Vecka 9 | Testare C / verksamhet | I ACC. |
| Regression och retest | Vecka 9 | Vecka 10 | Testare D | Efter sista leveransen av rättningar. |
| Release Readiness | Vecka 11 | Vecka 11 | Testledare | Testrapport och kvarstående risker. |
| Go/No-Go och produktionssättning | Vecka 12 | Vecka 12 | PO / projektledare | Smoke test i PROD. |
 
**Tidplan per vecka**

| **Vecka** | **1** | **2** | **3** | **4** | **5** | **6** | **7** | **8** | **9** | **10** | **11** | **12** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Testanalys och testdesign | TL+ A-D | TL+ A-D | | | | | | | | | | |
| Testdata och miljöförberedelser | | | TC+ DevOps | | | | | | | | | |
| SIT | | | | TA | TA | | | | | | | |
| Systemtest (inkl. behörighet, säkerhet, prestanda) | | | | | TBDA+ SÄKspec | TBDA+ SÄKspec | TBDA+ SÄKspec | TBDA+ SÄKspec | | | | |
| E2E-test | | | | | | | TBC | TBC | | | | |
| UAT | | | | | | | | TC/ verksamhet | TC/ verksamhet | | | |
| Regression och retest | | | | | | | | | TD | TD | | |
| Release Readiness | | | | | | | | | | | TL | |
| Go/No-Go och produktionssättning | | | | | | | | | | | | PO +PL |

*Förkortningar: TL = testledare, A-D = testare A–D, TA/TC/TD = testare A/C/D, TBDA = testare B, D och A, TBC = testare B och C, SÄKspec = säkerhetsspecialist, PO = Product Owner, PL = projektledare.*

## 14.1  Första testomgången

| **Fas** | **Varaktighet / datum** |
| --- | --- |
| Förberedelse: miljö, testdata, smoke test | Vecka 3 |
| SIT omgång 1: alla integrationer | Vecka 4 (5 arbetsdagar) |
| Systemtest omgång 1: P1-funktioner (inloggning, kreditregler, stora lån, behörighet) | Start vecka 5, cirka 1,5 vecka |
| Defect triage och rättning | Löpande, 3 gånger per vecka |
| Statusrapport efter omgång 1 | Slutet av vecka 5 |

## 14.2  Påföljande testomgångar

Uppgift(tas bort innan inlämning): *Beskriv hur efterföljande testomgångar planeras, vad som återanvänds och hur omfattningen styrs av felutfall och risk.*

Påföljande omgångar genomförs vid varje ny leverans från utvecklingsteamen. Varje omgång inleds med smoke test och omtest av rättade fel, därefter körs regression av P1 och nya eller ändrade funktioner. Omfattningen styrs av felutfall och risk: områden med många eller allvarliga fel får utökad testning (fler testfall, utforskande sessioner), medan stabila områden endast körs som regression. Testfall, testdata och automatiserade tester från första omgången återanvänds. P2 körs när P1 är klart, och P3 körs bara om tid finns. Vid ändrade krav eller förseningar uppdaterar testledaren planen och dokumenterar ändringen i dokumenthistoriken.

# 15  Risker och oförutsedda händelser

Uppgift(tas bort innan inlämning): *Dokumentera risker som kan påverka testningen eller leveransen. Ange konsekvens/kommentar, förebyggande eller korrigerande åtgärd, ägare och prioritet.*

| **Risk** | **Konsekvens / kommentar** | **Åtgärd** | **Ägare** | **Prioritet** |
| --- | --- | --- | --- | --- |
| P1: Kreditupplysningstjänsten saknar testmiljö eller är instabil | SIT och E2E kan inte köras med verkliga svar. Risk för fel som upptäcks först i produktion. | Använd stub, verifiera mot verklig tjänst före SIT-avslut. Ta upp med leverantörsrepresentanten vecka 2. | Testare A / PO | Hög |
| P2: Öppna frågor om affärsregler (gränsvärden, riskklass) besvaras för sent | Testfall och förväntade resultat kan bli fel, omarbete. | Frågor besvaras senast vecka 1–2. Annars dokumenterade antaganden som PO godkänner. | PO | Hög |
| P3: SYS delas av många och är instabil eller blockerad av deployments | Förseningar, blockerade testfall. | Gemensam deploymentplan, smoke test efter varje deployment, dagliga avstämningar med DevOps. | DevOps / testledare | Hög |
| P4: Sen leverans eller många fel i leveranserna | Kort tid för testning, mer regression, risk för No-Go. | Tidig SIT, daglig triage, riskbaserad prioritering, tidiga varningar till projektledare. | Testledare / projektledare | Hög |
| P5: Testdata saknas eller är inkonsekvent mellan beroende system | E2E-flöden fungerar inte, testning blockeras. | Testare C tar fram testdata vecka 3 med samma testperson i alla system. SQL-skript för återställning. | Testare C | Hög |
| P6: Verksamhetsrepresentanter har inte tid för UAT | UAT försenas eller blir ofullständigt. | Boka tidigt, definiera scenarier vecka 6, eskalera till PO. | PO | Medel |
| P7: Prestandatest kan inte göras representativt i SYS | Prestandakrav kan inte verifieras fullt ut. | Definiera normal belastning, överväg testkörning i ACC eller särskild miljö, redovisa som kvarstående risk. | DevOps / Testare A | Medel |
| P8: Nyckelperson är sjuk eller otillgänglig | Förseningar. Specialistkunskap saknas. | Backup-ansvar mellan testare, dokumenterade testfall, korsutbildning. | Testledare | Medel |
| P9: Verkliga persondata används av misstag i testmiljö | GDPR-incident. | Endast syntetisk data, kontroll av SQL-skript, stopp enligt 8.1. | Projektledare / testledare | Hög |
| P10: Ändrade krav eller ny scope under testperioden | Testfall och plan blir inaktuella. | Ändringshantering via PO, konsekvensanalys, uppdaterad plan med ny version. | Testledare / PO | Medel |
| P11: Automation hinner inte bli klar | Regression blir manuell och långsam. | Automatisera endast P1 först (inloggning, kreditregler, behörighet). | Testare D | Medel |

# 16  Godkännande av testplanen

Uppgift(tas bort innan inlämning): *Ange vilka roller/personer som ska godkänna testplanen och när godkännandet skedde.*

| **Namn / roll** | **Beslut** | **Datum** | **Kommentar** |
| --- | --- | --- | --- |
| Testledare | Ej godkänd (väntar) |  | Författare av planen. |
| Product Owner | Ej godkänd (väntar) |  | Godkänner omfattning, prioritering och slutkriterier. |
| Projektledare | Ej godkänd (väntar) |  | Godkänner tidplan och resurser. |
| Verksamhetsrepresentant | Ej godkänd (väntar) |  | Godkänner UAT-upplägg. |
| Säkerhetsspecialist | Ej godkänd (väntar) |  | Godkänner säkerhetstestets omfattning. |




