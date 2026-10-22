# Slutprojekt – Teststrategi och planering

**Case:** MortgageFlow – nytt bolånesystem för NordFinance

Det här projektarbetet är kursens avslutande examination och ska testa studenternas förmåga att använda hela testledningsprocessen från strategi till avslut.

Projektet genomförs stegvis. Studenterna får alltså inte all information från början. Precis som i ett verkligt projekt förändras förutsättningarna under arbetets gång och de måste analysera konsekvenser, uppdatera sina planer och fatta nya beslut.

## Projektet består av åtta delar

| Del | Moment | Deadline |
|---|---|---|
| 1 | Teststrategi | 20/10 12:00 |
| 2 | Testplan | 20/10 12:00 |
| 3 | Förändring och omplanering | 21/10 16:00 |
| 4 | Teststatus efter första testveckan | 22/10 16:00 |
| 5 | Underlag och rekommendation inför Go/No-Go | 23/10 16:00 |
| 6 | Testrapport | 27/10 12:00 |
| 7 | Presentation | 29/10 9–16 |
| 8 | Individuell Lessons Learned | 1/11 – 22:00 |

## Examinationens arbetssätt

Projektet genomförs stegvis.

Efter varje del lämnas resultatet in innan nästa scenarioinformation delas ut.

Det är viktigt eftersom studenterna ska visa att de kan:

> planera → få ny information → analysera påverkan → uppdatera planen

De ska alltså inte i efterhand skriva om historiken som om förändringen alltid varit känd.

## Muntlig presentation

- **Datum:** 29 oktober
- **Tid:** 30 minuter per grupp

Alla i gruppen måste prata. Ordningen för vem som börjar kommer att lottas ut.

---

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
