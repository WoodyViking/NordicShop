# Testplanering och Projektleverans (12 Veckor)

## Uppgift 1 – Identifiera aktiviteter

Följande testaktiviteter har identifierats och strukturerats för det 12 veckor långa projektet:

- **Testplanering & Strategi:** Framtagning och godkännande av övergripande teststrategi.
- **Kravanalys:** Granskning av kravdokumentation inför testdesign.
- **Testdesign:** Skapande av testfall, scenarier och acceptanskriterier.
- **Testdataförberedelse:** Identifiering, maskering och skapande av nödvändig testdata.
- **Mijöetablering & Röktest:** Säkra upp att SIT- och acceptansmiljöer är redo.
- **SIT (Systemintegrationstest):** Verifiering av flöden mellan integrerade system.
- **Systemtest:** Funktionell och icke-funktionell testning av det isolerade systemet.
- **Defect Triage & Retest:** Dagliga möten för att prioritera defekter samt omtestning av fixar.
- **Acceptanstest (UAT):** Verifiering tillsammans med verksamheten mot affärskrav.
- **Regressionstest:** Säkerställa att befintlig funktionalitet inte påverkats negativt.
- **Go/No-Go-underlag:** Sammanställning av slutrapport och kvalitetsmetriker för ledningsbeslut.
- **Release & Driftsättning:** Produktionssättning och efterföljande verifiering (Sanity test).

## Uppgift 2 – Skapa beroenden

| **Aktivitet**                | **Beroende av**                                                     |
|------------------------------|---------------------------------------------------------------------|
| Testdesign                   | Kravanalys (Krav måste vara frysta/förstådda)                       |
| Testdataförberedelse         | Testdesign (Testfall styr vilken data som behövs)                   |
| SIT (Systemintegrationstest) | Miljöetablering & Röktest samt utvecklingens enhetstest             |
| Systemtest                   | SIT (Integrationsblockerare måste vara lösta)                       |
| Acceptanstest (UAT)          | Systemtest (Systemet ska vara stabilt och signerat av IT)           |
| Regressionstest              | Defect Triage & Retest (Större delen av kodbasen måste vara stabil) |

## Uppgift 3 – Skapa RACI – Responsible, Accountable, Consultable, Informed.

| **Aktivitet**                | **Testledare** | **Testare** | **Utveckling** | **Product Owner** | **Verksamhet** |
|------------------------------|----------------|-------------|----------------|-------------------|----------------|
| Teststrategi / testplanering | A / R          | C           | C              | I                 | I              |
| Testdesign                   | A              | R           | I              | I                 | C              |
| Testdata                     | A              | R           | C              | I                 | I              |
| SIT                          | A              | R           | C              | I                 | I              |
| Systemtest                   | A              | R           | C              | I                 | I              |
| Acceptanstest                | A              | C           | I              | R                 | R              |
| Defect triage                | A / R          | R           | R              | C                 | C              |
| Regression                   | A              | R           | I              | I                 | I              |
| Teststatus                   | A / R          | C           | I              | I                 | I              |
| Go/No-Go-underlag            | A / R          | C           | I              | C                 | C              |

## Uppgift 4 & 6 – Tidsplan och Milstolpar

| **Aktivitet**      | **V1** | **V2** | **V3** | **V4** | **V5**   | **V6**   | **V7**   | **V8**   | **V9**   | **V10**  | **V11**  | **V12**  |
|--------------------|--------|--------|--------|--------|----------|----------|----------|----------|----------|----------|----------|----------|
| Analys             | **FA** | **FA** |        |        |          |          |          |          |          |          |          |          |
| Testdesign         |        | **BJ** | **BJ** |        |          |          |          |          |          |          |          |          |
| Testdata           |        |        | **FA** | **FA** |          |          |          |          |          |          |          |          |
| SIT                |        |        |        | **BJ** | **BJ**   | **BJ**   |          |          |          |          |          |          |
| Systemtest         |        |        |        |        |          | **FA**   | **FA**   | **FA**   |          |          |          |          |
| Retest             |        |        |        |        | **FABJ** | **FABJ** | **FABJ** | **FABJ** | **FABJ** |          |          |          |
| Acceptanstest      |        |        |        |        |          |          |          |          | **FA**   | **FA**   |          |          |
| Regression         |        |        |        |        |          |          |          | **BJ**   | **BJ**   | **BJ**   |          |          |
| Release readiness  |        |        |        |        |          |          |          |          |          | **FABJ** | **FABJ** |          |
| Go/No-Go           |        |        |        |        |          |          |          |          |          |          | **FABJ** |          |
| Release            |        |        |        |        |          |          |          |          |          |          |          | **FABJ** |
| Milstolpar (M1-M6) |        | **M1** |        | **M2** |          | **M3**   |          |          | **M4**   |          | **M5**   | **M6**   |

Beskrivning av Milstolpar:

- **M1 (Vecka 2):** Teststrategi och testplan signerad samt kravanalys klar.
- **M2 (Vecka 4):** Testdesign färdigställd och kritiska testdata genererad/laddad.
- **M3 (Vecka 6):** SIT avslutad (inga blockerande eller kritiska defekter kvar).
- **M4 (Vecka 9):** Systemtest och primär regression avslutad. Kod fryst inför UAT.
- **M5 (Vecka 11):** Acceptanstest (UAT) signerad och klar av verksamheten. Go/No-Go-underlag presenterat.
- **M6 (Vecka 12):** Framgångsrik driftsättning (Release) i produktionsmiljön.

## Uppgift 5 – Fördela testarna

Resursallokering baserad på projektets tre tillgängliga testare för att undvika konflikter:

| **Fas**                   | **Testare**                    | **Motivering**                                                                                                                                 |
|---------------------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| SIT                       | Isabella, Johan                | Kräver djup teknisk kompetens inom integrationer och API-testning. Isabella förbereder samtidigt systemtestmiljön.                             |
| Systemtest                | Fanny, Anders                  | Fokus på end-to-end-funktionalitet och UI. Fan påbörjar stöd och förberedelse inför UAT med verksamheten.                                      |
| Acceptanstest (UAT)       | Anders, Fanny                  | Fan leder och stöttar verksamheten (UAT). Anders hjälper till med teknisk verifiering och felrapportering. Isabella säkrar regressionspaketet. |
| Regression                | Isabella, Johan                | Alla resurser samlas för maximal täckning och snabb exekvering innan slutgiltig release readiness.                                             |
| Testdesign                | Isabella, Johan                |                                                                                                                                                |
| Testdata                  | Fanny, Anders                  |                                                                                                                                                |
| Analys                    | Fanny, Anders                  |                                                                                                                                                |
| Retest, Go/No-go, Release | Isabella, Johan, Fanny, Anders |                                                                                                                                                |

## Uppgift 7 – Kritiska beroenden

| **Kritiskt beroende**                 | **Vad händer om det blir försenat?**                                   | **Åtgärd**                                                                                                |
|---------------------------------------|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| Testdataförberedelse (Klar V4)        | Testexekvering i SIT (V4) blockeras eller fördröjs.                    | Förbered syntetisk data tidigt; eskalera till PO för att få produktionsliknande data maskerad snabbare.   |
| SIT-miljöns stabilitet (V4-V6)        | Integrationsproblem upptäcks inte i tid, vilket skjuter på systemtest. | Dagliga röktest, ha en dedikerad miljöansvarig från utvecklingsteamet tillgänglig.                        |
| Defekt fixar från utveckling (V5-V9)  | Retest och regressionstester hopar sig i slutet av projektet.          | Tydliga tjänstenivå avtal för defekter baserat på prioritet; daglig defect triage med utvecklingsledaren. |
| Verksamhetens tillgänglighet (V9-V10) | Acceptanstest (UAT) blir inte slutfört eller signerat i tid.           | Boka upp verksamhetsresurser långt i förväg (redan i V2); ge dem färdiga och enkla testmanuskript.        |
| Kodfrys (Code Freeze) inför V10       | Nya buggar introduceras under slutskedet av acceptans och regression.  | Strikta policyer i versionshanteringen; endast kritiska buggfixar tillåts efter vecka 9                   |

## Uppgift 8 – Kontrollera planen

- **Finns tid för defektfix?** Ja, integrerat i tidsplanen under exekveringsveckorna (V5–V9) via 'Retest'-aktiviteten.
- **Finns tid för retest?** Ja, löper parallellt med SIT och Systemtest så att fixar verifieras kontinuerligt.
- **Finns tid för regression?** Ja, ett dedikerat block ligger i V8–V10 för att säkra basfunktionaliteten före och under UAT.
- **Är acceptanstestet realistiskt?** Ja, det ligger på 2 fulla veckor (V9–V10) efter att systemet stabiliserats i systemtest.
- **Är samma testare bokad på flera fulla aktiviteter samtidigt?** Nej, resursfördelningen i Uppgift 5 visar hur testarna roterar och fördelas strategiskt för att undvika överallokering.
- **Finns tid mellan regression och release?** Ja, Vecka 11 fokuserar helt på Release Readiness och Go/No-Go-beslut efter att den huvudsakliga regressionen avslutats i V10.
- **Är externa beroenden inplanerade?** Ja, miljöer, testdataleveranser och verksamhetens deltagande har synkroniserats med rätt veckor i tidsplanen.

## Uppgift 9 – Planera om

Besvara:

1. Vilka aktiviteter påverkas?
2. Vilka beroenden påverkas?
3. Kan något göras parallellt under tiden?
4. Behöver resurser omfördelas?
5. Hur påverkas SIT?
6. Hur påverkas systemtest?
7. Hur påverkas regression?
8. Finns release-risk?
9. Vad behöver kommuniceras till projektledaren?

Uppdatera tidsplanen.
