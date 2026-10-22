
# DEL 5 – UNDERLAG TILL GO/NO-GO

Testperioden är nu avslutad.

Det är dags att förbereda Go/No-Go-mötet.

## Slutligt testresultat

Totalt: **300 planerade tester**

| Status | Antal |
|---|---|
| Executed | 290 |
| Passed | 264 |
| Failed | 10 |
| Blocked | 6 |
| Not Run | 10 |

## Regression

- **Planerad regression:** 120 tester
- **Genomförd:** 108 tester

De tester som inte genomfördes gäller främst:

- vissa browserkombinationer
- ovanliga dokumentformatkombinationer
- några lågprioriterade rapportscenarier

## Critical DEF-101

Problemet är:

> Rättat

- **Retest:** Passed 15 av 15
- **Relevant regression:** Passed

## DEF-112 – High

Dubbelgodkännande för lån över 5 miljoner har rättats.

- **Retest:** Passed
- **E2E:** Passed

## Kvarstående defekter

| Severity | Öppna |
|---|---|
| Critical | 0 |
| High | 3 |
| Medium | 8 |
| Low | 11 |

### High 1

Kreditupplysningstjänsten kan vid timeout visa otydlig status för handläggaren.

Ingen felaktig kreditbedömning genomförs, men handläggaren behöver uppdatera ärendet manuellt.

### High 2

Administratörens rolländringslogg saknar ibland information om tidigare roll.

Den nya rollen loggas korrekt.

### High 3

En ovanlig kombination av dokumentversioner kan göra att den äldsta dokumentversionen inte visas korrekt.

Originaldokumentet finns kvar.

## UAT

Verksamheten har genomfört UAT.

**Resultat:**

> Godkänd med accepterade kända avvikelser

## Prestanda

Test genomfördes med:

> 350 samtidiga användare

Kravet är:

> 500 samtidiga användare

350 användare klarade svarstidskravet.

På grund av miljöbegränsningar kunde 500 samtidiga användare inte verifieras.

Det finns alltså kvarstående prestandarisk.

## Säkerhet

Behörighetstester är genomförda.

Den tidigare defekten där handläggare kunde se ärenden från fel region är:

> Rättad och regressionstestad

Inga kända Critical-säkerhetsdefekter kvarstår.

## Technical Readiness

- produktionsbuild klar
- deploymentplan klar
- monitorering klar
- rollbackplan verifierad
- supportberedskap finns
- databasbackup verifierad

## Verksamheten

MortgageFlow måste lanseras före årsskiftet på grund av att det gamla bolånesystemets avtal upphör.

Att flytta releasen innebär:

- betydande kostnad
- behov av att förlänga det gamla avtalet
- påverkan på planerad migrering

---

## Uppgift – Del 5

Ta fram ett Go/No-Go-underlag på **max 3 sidor**.

### Bedöm

**Exit Criteria**
Vilka är uppfyllda? Vilka är inte fullt uppfyllda?

**Testresultat**
Vad betyder siffrorna?

**Kvarstående defekter**
Är någon av dem releaseblockerande?

**Regression**
Vilken risk innebär X %?

**Prestanda**
Hur påverkar avsaknaden av verifiering med 500 samtidiga användare beslutet?

**Business Acceptance**
Vad betyder verksamhetens godkännande?

**Technical Readiness**
Är tekniken redo?

**Remaining Risk**
Vilka är de viktigaste kvarstående riskerna?

### Rekommendation

Välj:

- 🟢 GO
- 🟡 CONDITIONAL GO
- 🔴 NO-GO

Motivera utifrån:

> Fakta → Konsekvens → Risk → Rekommendation

Inte endast:

> "Vi har 0 Critical därför GO."



Go/No-Go-underlag – MortgageFlow release 1.0
Projekt: MortgageFlow, release 1.0 · Datum: 2026-10-22 Underlag till: Go/No-Go-mötet 23/10 · Framtaget av: testledningen, Grupp 2 Grundar sig på: testplan TP-MF-2.1 §7.2 (slutkriterier), teststatusrapport vecka 1 (Del 4) och slutligt testresultat (Del 5)

Rekommendation: 🟡 CONDITIONAL GO
Releasen kan genomföras under förutsättning att villkoren i avsnitt 8 är uppfyllda före produktionssättning. Villkor 1 är avgörande: om det inte kan uppfyllas ska releasen skjutas fram, oavsett affärstryck.
Skälet till att det inte är ett rent GO är att testplanens egna slutkriterier inte är uppfyllda. Två av tio kriterier faller, och ett av dem gäller ett säkerhetskrav som bankens säkerhetsavdelning ställt (R11). Skälet till att det inte är NO-GO är att inga kritiska fel kvarstår, att den kritiska defekten är omtestad och regressionstestad, att verksamheten godkänt UAT och att den tekniska beredskapen är komplett. De kvarvarande bristerna har antingen en känd kompenserande åtgärd eller kan åtgärdas inom releasefönstret.

1. Exit criteria – var står vi?
#
Slutkriterium (testplan §7.2)
Status
Kommentar
1
Alla P1-tester genomförda, ≥ 95 % godkända
Kan inte verifieras
Resultatet redovisas inte per prioritet. 96,4 % av de tester som fått ett utfall är godkända, men P1-nivån går inte att bekräfta.
2
Alla E2E-flöden körda utan öppna S1/S2
Delvis
Inga S1 kvarstår och DEF-112 är E2E-verifierad, men tre S2 är öppna och det framgår inte vilka flöden de träffar.
3
Inga öppna S1/S2 i P1-områden
Ej uppfyllt
0 Critical men 3 High öppna. DEF-112 ligger i behörighetsområdet, som är P1 enligt R11.
4
Rättade P1-defekter omtestade, P1-regression körd på slutlig kandidat
Uppfyllt
DEF-101: retest 15/15 passed, relevant regression passed. DEF-112: retest passed, E2E passed.
5
≥ 80 % av P2-testfallen genomförda
Kan inte verifieras
Ingen uppdelning per prioritet redovisad. Körningsgraden totalt är 93–97 %, vilket talar för att kravet är uppfyllt.
6
UAT genomfört och godkänt
Uppfyllt
Godkänt med accepterade kända avvikelser.
7
Säkerhetstest utan kritiska säkerhetsfel
Uppfyllt, med anmärkning
Regiondefekten är rättad och regressionstestad. DEF-112 är dock ett loggkrav från säkerhetsavdelningen.
8
Prestanda verifierade, eller avvikelse dokumenterad och accepterad
Delvis
500 samtidiga användare är inte verifierat. Avvikelsen är dokumenterad men inte formellt accepterad.
9
R11 verifierat: verifiering krävs och loggen innehåller användare, tidpunkt, tidigare roll och ny roll
Ej uppfyllt
DEF-112: tidigare roll saknas ibland i loggposten. Kravet är därmed inte uppfyllt i sin helhet.
10
Kvarstående risker dokumenterade och accepterade av PO och projektledare
Pågår
Detta dokument är underlaget. Acceptansen är ett beslut på mötet, inte en teknisk bedömning.
Utfall: 4 uppfyllda, 2 delvis, 2 ej uppfyllda, 2 som inte går att verifiera med nuvarande rapportering.

2. Testresultat – vad betyder siffrorna?
Mått
Värde
Planerade tester
300
Genomförda (enligt sammanställningen)
290 (96,7 %)
Passed / Failed / Blocked / Not Run
264 / 10 / 6 / 10
Körningsgrad med faktiskt utfall
280 av 300 (93,3 %)
Godkännandegrad av tester med utfall
264 av 274 (96,4 %)
Fakta: summeringen redovisar 264 + 10 + 6 + 10 = 290 statusar, men 300 tester planerades. Tio tester saknar alltså helt status.
Konsekvens: godkännandegraden kan presenteras som 96,4 %, 91,0 % eller 88,0 % beroende på vilken nämnare som används. Den siffra som betyder något för beslutet är 93,3 % körningsgrad – andelen tester som faktiskt gett ett svar. 16 tester (5,3 %) gav inget utfall alls: 6 blockerade och 10 aldrig startade.
Risk: att beslutet fattas på 96,4 % utan att notera att var tjugonde test saknar utfall. De tio oredovisade testerna måste stämmas av före mötet.

3. Kvarstående defekter – är någon releaseblockerande?
Severity
Öppna
Bedömning
Critical
0
–
High
3
En blockerande under rådande kravbild, två accepterbara
Medium
8
Accepterbara, planeras till 1.1
Low
11
Accepterbara
DEF-112 (High) – rolländringsloggen saknar ibland tidigare roll. Den nya rollen loggas korrekt, men den gamla saknas. Det här är inte en funktionell detalj: kravet kom från bankens säkerhetsavdelning och kräver att loggposten innehåller användare, tidpunkt, tidigare roll och ny roll. DEF-112 gör att slutkriterium 9 inte är uppfyllt. Vid en intern eller extern revision går det inte att styrka vilken behörighet en administratör hade före ändringen. Blockerande – men åtgärden är avgränsad (ett loggfält) och bör rymmas i releasefönstret.
High 1 – kreditupplysningstjänsten kan vid timeout visa otydlig status. Ingen felaktig kreditbedömning genomförs; handläggaren uppdaterar ärendet manuellt. Ej blockerande – men den manuella rutinen måste vara dokumenterad och känd av alla handläggare innan drift, och larm ska finnas på timeouts.
High 3 – ovanlig kombination av dokumentversioner kan göra att äldsta versionen inte visas korrekt. Originaldokumentet finns kvar. Ej blockerande – låg frekvens, ingen dataförlust, känt arbetsflöde. Åtgärdas i 1.1.

4. Regression – vad innebär 90 %?
120 planerade regressionstester, 108 genomförda (90 %). De tolv som inte kördes gäller vissa browserkombinationer, ovanliga kombinationer av dokumentformat och några lågprioriterade rapportscenarier.
Fakta → konsekvens: kravet i §7.2 är att regression av P1 är körd på den slutliga releasekandidaten, vilket den är. De tolv som saknas ligger utanför P1. Risken är ändå reell för browserkombinationerna: bankens handläggare kan sitta på olika webbläsare, och ett gränssnittsfel som bara syns i en kombination upptäcks först i produktion.
Rekommendation: kör de tre vanligaste browserkombinationerna mot releasekandidaten före produktionssättning. Resten accepteras som kvarstående risk med övervakning.

5. Prestanda – 350 av 500 samtidiga användare
Fakta: 350 samtidiga användare uppnådde svarstidskravet. 500 kunde inte verifieras på grund av miljöbegränsningar. Det finns alltså en kvarstående prestandarisk som inte är mätt.
Konsekvens: vi vet att systemet klarar 70 % av den dimensionerade belastningen med godkänd svarstid. Vi vet inte hur det beter sig vid 500, och vi vet inte var gränsen går mellan 350 och 500. Belastningstoppar uppstår typiskt vid månadsskifte och kampanjer, alltså i drift snarare än i test.
Risk: försämrad svarstid eller otillgänglighet vid toppbelastning under de första veckorna i drift. Konsekvensen är fördröjd handläggning, inte felaktiga beslut.
Rekommendation: releasen kan inte vila på att prestandan är verifierad. Den måste vila på en uttalad acceptans av avvikelsen kombinerat med tre åtgärder: gradvis uppskalning av användare i produktion, larm på svarstid och felkvot, samt ett verifierande lasttest i produktionsmiljö utanför kontorstid inom två veckor efter driftsättning. Rollbackplanen är verifierad, vilket gör risken hanterbar.

6. Business acceptance – vad betyder verksamhetens godkännande?
UAT är godkänt med accepterade kända avvikelser. Det betyder att verksamheten har prövat systemet i sina egna processer och funnit det användbart, och att de har tagit ställning till de avvikelser som presenterades för dem.
Två gränser måste sägas högt: godkännandet omfattar bara de avvikelser som faktiskt redovisades i UAT – om DEF-112 inte ingick där, är den inte accepterad av verksamheten. Och UAT är ett underlag, inte ett releasebeslut: det säger att systemet fungerar i verksamheten, inte att de tekniska slutkriterierna är uppfyllda.

7. Technical readiness
Samtliga sex punkter är gröna: produktionsbuild klar, deploymentplan klar, monitorering klar, rollbackplan verifierad, supportberedskap finns och databasbackup verifierad. Tekniken är redo. Det som återstår är inte tekniska förberedelser utan de villkor som anges nedan.

8. Kvarstående risker och villkor för GO
#
Kvarstående risk
Sannolikhet
Konsekvens
Hantering
R-A
DEF-112: ofullständig rolländringslogg bryter mot säkerhetskravet (R11)
Hög – kvarstår i dag
Hög – revisionsanmärkning, krav från säkerhetsavdelningen
Villkor 1: rättas och omtestas före produktionssättning. Alternativt kompenserande kontroll: rolländringar hanteras via ärende till säkerhetsfunktionen till dess fixen är driftsatt, skriftligt godkänt av PO och säkerhetsavdelning
R-B
Prestanda över 350 användare overifierad
Medel
Medel – fördröjd handläggning vid topp
Villkor 2: skriftlig acceptans av PO och projektledare + gradvis uppskalning, larm och lasttest i produktion inom 2 veckor
R-C
12 regressionstester ej körda, varav browserkombinationer
Medel
Låg–medel – gränssnittsfel för vissa användare
Villkor 3: de tre vanligaste browserkombinationerna körs före driftsättning
R-D
10 tester utan redovisad status, ingen P1/P2-uppdelning
Hög – gäller rapporteringen
Medel – beslutsunderlaget är ofullständigt
Villkor 4: stäms av och kompletteras före mötet
R-E
High 1: timeout mot kreditupplysningen ger otydlig status
Låg
Låg – inga felaktiga kreditbeslut
Dokumenterad manuell rutin + larm. Accepteras
R-F
High 3: äldsta dokumentversion visas inte i ovanliga kombinationer
Låg
Låg – original finns kvar
Accepteras, åtgärdas i 1.1
R-G
Tidspress: gamla systemets avtal upphör vid årsskiftet
Hög
Hög för verksamheten om releasen glider
Hanteras genom att villkoren skrivs uttryckligen i stället för att sänkas tyst
Villkor för GO. (1) DEF-112 rättad och omtestad med E2E och relevant regression, eller kompenserande kontroll enligt R-A. (2) Prestandaavvikelsen skriftligt accepterad samt uppskalnings- och larmplan fastställd. (3) Browserkombinationerna enligt R-C körda. (4) Rapporteringen kompletterad enligt R-D.
Om villkor 1 inte kan uppfyllas bör rekommendationen ändras till 🔴 NO-GO för den scope som omfattar administrativa rolländringar. Det är ett krav från bankens säkerhetsavdelning, inte en avvikelse verksamheten kan välja bort.
Om villkor 2–4 inte uppfylls är det fortfarande ett GO, men med utökad övervakning och dokumenterade kvarstående risker i Del 6.

9. Samlad bedömning
Fyra slutkriterier är uppfyllda, två delvis, två faller och två går inte att verifiera. Noll kritiska fel, den kritiska defekten rättad och omtestad, godkänd UAT och full teknisk beredskap talar för release. Tre öppna High-fel – varav ett bryter mot ett uttalat säkerhetskrav – och en overifierad prestandadimension talar emot.
Releasen är genomförbar men inte färdigverifierad. Därför CONDITIONAL GO: beslutet fattas när villkoren är uppfyllda, och villkoren ska stå i beslutsprotokollet – inte bara sägas muntligt.
