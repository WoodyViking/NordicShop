DEL 6 – TESTRAPPORT
Projektet har fattat beslut:
🟡 CONDITIONAL GO
Release genomförs med:
- förstärkt produktionsmonitorering
- särskild bevakning av kreditupplysningstjänsten
- supportberedskap första veckan
- planerad uppföljning av kvarstående High-defekter
- separat prestandaverifiering efter release

Uppgift
Skriv en avslutande testrapport utifrån mallen som används i kursen.

# TESTRAPPORT

Mall för sammanställning och avslut av testarbete

| **Projekt / system** | \<Namn\> |
| --- | --- |
| **Release / version** | \<Version\> |
| **Testperiod** | \<Datum - datum\> |
| **Dokumentägare** | \<Namn / roll\> |
| **Datum** | \<Datum\> |
| **Status** | \<Utkast / Slutlig\> |

*Använd mallen för att sammanfatta genomfört testarbete, resultat, avvikelser och kvarstående risker. Ersätt text inom \<hakparenteser\> och anpassa omfattningen efter projektets behov.*

## 1. Sammanfattning

*Ge en kort ledningssammanfattning av testperioden. Beskriv vad som testats, övergripande resultat, viktigaste avvikelserna och den samlade bedömningen.*

\<Sammanfattning\>

## 2. Scope

*Beskriv vad som ingick i testarbetet och eventuella avgränsningar. Koppla gärna till kritiska affärsflöden, testnivåer och testtyper.*

| **Område / flöde** | **Testnivå / testtyp** | **Prioritet** | **Kommentar** |
| --- | --- | --- | --- |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |

## 3. Genomförda tester

*Sammanställ vilka tester och testaktiviteter som genomfördes. Redovisa relevant coverage och vad som eventuellt inte genomfördes.*

| **Testområde** | **Planerat** | **Genomfört** | **Status / kommentar** |
| --- | --- | --- | --- |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |

## 4. Resultat

*Sammanfatta testresultatet. Siffror ska kompletteras med en kort analys av vad resultatet innebär.*

| **Mätetal** | **Resultat** | **Kommentar** |
| --- | --- | --- |
| Test Execution | 290 av 300 (97 %) | Hög täckning. |
| Pass rate | 264 av 290 (91 %), 88 % av alla planerade | Lägre än målet 95 % för P1, men siffror per prioritet saknas. |
| Failed / Blocked / Not Run | 10 / 6 / 10 | Hänger ihop med kvarstående defekter. Inget gäller Critical-fel. |
| Tester utan godkänt resultat | 36 (12 %) | 10 Failed, 6 Blocked, 10 Not Run och 10 utan registrerad status. |
| Datagap | 10 tester | 264 + 10 + 6 = 280, inte 290 som rapporterats som executed. |
| Regression | 90 % | Kärnflödena regressionstestade. |
| Prestanda | 70 % av kravet verifierat | 350 av 500 samtidiga användare. |

**Analys:** Resultatet visar att kärnflödena fungerar: kreditbedömning, dubbelgodkännande, behörighet och E2E har gått igenom efter rättningar. Den höga körningsgraden döljer dock att 36 tester (12 %) saknar godkänt resultat. För 10 av dem har status inte kunnat redovisas, vilket är en brist i uppföljningen. Pass rate på 91 % ligger under målet 95 % för P1-tester, men eftersom resultat per prioritet saknas kan vi inte avgöra om P1-målet uppnåddes.
## 5. Defekter

*Sammanfatta identifierade och kvarstående defekter. Fokusera på allvarlighetsgrad, påverkan och status - inte enbart antal.*

| **Severity** | **Totalt** | **Öppna** | **Kommentar / påverkan** |
| --- | --- | --- | --- |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |

## 6. Avvikelser från plan

*Beskriv betydande avvikelser från testplanen, exempelvis ändrat scope, försenad miljö, saknad testdata, resursförändringar eller reducerad regression.*

| **Avvikelse** | **Påverkan på testningen** | **Åtgärd / hantering** |
| --- | --- | --- |
| \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> |

## 7. Risker

*Beskriv viktiga risker som identifierades under testarbetet och hur de hanterades.*

| **Risk** | **Konsekvens** | **Åtgärd** | **Status** |
| --- | --- | --- | --- |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |

## 8. Kvarstående risk

*Beskriv de risker och osäkerheter som fortfarande finns efter avslutad testning. Ta med exempelvis otestade områden, öppna fel, begränsad coverage eller skillnader mellan test och produktion.*

| **Kvarstående risk** | **Konsekvens** | **Risknivå** | **Riskägare / accepterad av** |
| --- | --- | --- | --- |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |

## 9. Slutsats

*Sammanfatta vad testningen visar om lösningens kvalitet och testmålen. Beskriv om Exit Criteria uppnåddes och vilka begränsningar som finns.*

\<Slutsats\>

## 10. Rekommendation

*Ge en tydlig rekommendation baserad på testresultat och kvarstående risk. Exempel: GO, CONDITIONAL GO, NO-GO eller rekommenderade åtgärder efter release.*

| **Rekommendation** | \<GO / CONDITIONAL GO / NO-GO / annan\> |
| --- | --- |
| **Motivering** | \<Kort motivering utifrån risk\> |
| **Villkor / åtgärder** | \<Eventuella villkor eller uppföljning\> |
| **Ansvar / uppföljning** | \<Roll / datum\> |

## 11. Godkännande / mottagare

*Dokumentera vid behov vilka roller som har tagit del av eller godkänt testrapporten.*

| **Roll** | **Namn** | **Datum** | **Kommentar** |
| --- | --- | --- | --- |
| \<...\> | \<...\> | \<...\> | \<...\> |
| \<...\> | \<...\> | \<...\> | \<...\> |

Testrapport - \<Projekt / system\>
