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

| **Projekt / system** | MortgageFlow – NordFinance |
| --- | --- |
| **Release / version** | Release 1.0 (testplan version 2.1) |
| **Testperiod** | Projektvecka 1–11. Go/No-Go och produktionssättning vecka 12 |
| **Dokumentägare** | Grupp 2 |
| **Datum** | 2026-10-26 |
| **Status** | \<Utkast / Slutlig\> |

*Använd mallen för att sammanfatta genomfört testarbete, resultat, avvikelser och kvarstående risker. Ersätt text inom \<hakparenteser\> och anpassa omfattningen efter projektets behov.*

## 1. Sammanfattning

*Ge en kort ledningssammanfattning av testperioden. Beskriv vad som testats, övergripande resultat, viktigaste avvikelserna och den samlade bedömningen.*

\<Sammanfattning\>

## 2. Scope

*Beskriv vad som ingick i testarbetet och eventuella avgränsningar. Koppla gärna till kritiska affärsflöden, testnivåer och testtyper.*

| **Område / flöde** | **Testnivå / testtyp** | **Prioritet** | **Kommentar** |
| --- | --- | --- | --- |
| Kreditbedömning och affärsregler | Systemtest, E2E, regression | P1 (R1) | Beslutstabeller och gränsvärden för skuldkvot och belåningsgrad. |
| Dubbelgodkännande för lån över 5 MSEK | Systemtest, E2E | P1 (R2) | Gränsvärden kring 5 000 000 SEK. |
| Behörighet och ärendesynlighet | Systemtest, säkerhetstest | P1 (R3, R4) | Alla roller, via UI och API. |
| Integration mot kreditupplysningstjänst | SIT, E2E | P1 (R5) | Inklusive timeout och felsvar. |
| Inloggning, MFA, kontolåsning, utloggning | Systemtest | P1 (R6) | Gränsvärden för inloggningsförsök och inaktivitet. |
| Ärendestatus och ärendelogg | Systemtest | P1 (R7) | Tillåtna och otillåtna övergångar. |
| Rolländring med verifiering och loggning (nytt krav) | Systemtest, säkerhetstest | P1 (R11) | Tillkom i version 2.0. |
| Dokumenthantering | Systemtest, SIT | P2 (R8) | Filtyper, 10 MB, versionshantering. |
| E-postbekräftelse | SIT, E2E | P2 (R10) |  Rätt mottagare och innehåll, samt hantering när e-posttjänsten inte svarar. Inga e-postrelaterade defekter är redovisade. |
| Prestanda (2 s svarstid, 500 användare) | Prestandatest | P2 (R9) | Endast 350 samtidiga användare har verifieras. |
| Webbläsare Chrome, Edge, Firefox | Kompatibilitetstest | P2 | Edge och Firefox som stickprov enligt version 2.0. |
| Rapporter och statistik | Systemtest | P3 | Prioriterades ned enligt version 2.0. |
| Verksamhetens arbetsflöden | UAT i ACC | P1 | Genomfört av handläggare och senior handläggare. |

## 3. Genomförda tester

*Sammanställ vilka tester och testaktiviteter som genomfördes. Redovisa relevant coverage och vad som eventuellt inte genomfördes.*

| **Testområde** | **Planerat** | **Genomfört** | **Status / kommentar** |
| --- | --- | --- | --- |
| Totalt testpaket (SIT, systemtest, E2E) | 300 | 290 (97 %) | 264 Passed, 10 Failed, 6 Blocked, 10 Not Run. 10 tester saknar registrerad status. |
| Testpaket efter första testveckan | 160 | 128 (80 %) | 20 % efter plan, status RÖD. Ikapp genom prioritering av P1. |
| Omtest av DEF-101 (Critical) | N/A | 15 | 15 av 15 Passed. Felet uppstod bara ibland (3 av 10 försök) och kördes därför många gånger. |
| Omtest av DEF-112 och DEF-124 | N/A | Genomfört | Passed, med E2E respektive regression. |
| Regression | 120 | 108 (90 %) | Ej körda: vissa webbläsarkombinationer, ovanliga dokumentformat, lågprioriterade rapporter. |
| E2E-flöden (E2E-1 till E2E-5) | 5 flöden | Genomfört | Passed. Stort lån (E2E-3) verifierat efter rättning av DEF-112. |
| UAT | Enligt plan | Genomfört | Godkänt med accepterade kända avvikelser. |
| Prestandatest | 500 användare | 350 användare | Svarstidskravet uppfyllt för 350. 500 kunde inte testas på grund av miljöbegränsning. |
| Säkerhets- och behörighetstest | Enligt plan | Genomfört | Inga kända Critical-säkerhetsdefekter kvar. |

Fördelningen per testområde vid testavslut fins inte i underlaget, utan bara totalsiffrorna. Uppdelningen per område finns i statusrapporten efter första veckan.

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
| Critical | 1 | 0 | DEF-101 rättad och verifierad 15 av 15. |
| High | 6 | 3 | Se tabellen nedan. |
| Medium | 12 | 8 | Ingen bedöms som releaseblockerande. Accepteras av PO. |
| Low | 7 | 11 | Ökningen visar att nya mindre fel hittades sent i testperioden. |

Efter första veckan var 31 defekter rapporterade. Totalt antal rapporterade defekter vid testavslut har inte redovisats.

**Rättade allvarliga defekter:**

- **DEF-101 (Critical):** Ansökan med belåningsgrad över 85 % kunde godkännas utan ytterligare kontroll. Rättad, omtest 15 av 15 Passed, regression Passed.
- **DEF-112 (High):** Lån över 5 MSEK kunde godkännas utan senior handläggare. Rättad, omtest och E2E Passed.
- **DEF-124 (High):** Handläggare kunde se ärenden från fel region. Rättad och regressionstestad.

**Kvarstående High-defekter:**

| **Defekt** | **Påverkan** | **Hantering** |
| --- | --- | --- |
| High 1: otydlig status vid timeout mot kreditupplysningen | Ingen felaktig kreditbedömning, men handläggaren måste uppdatera ärendet manuellt. Allvaret har minskat jämfört med DEF-118 i vecka 1. | Särskild bevakning av kreditupplysningstjänsten, rutin för handläggare och support. |
| High 2: rolländringslogg saknar ibland tidigare roll | Ny roll loggas rätt, men spårbarheten brister. Säkerhetskravet R11 är inte helt uppfyllt (motsvarar DEF-121). | Uppföljning av High-defekter. Kompenserande kontroll rekommenderas, se avsnitt 10. |
| High 3: äldsta dokumentversionen visas ibland fel | Ovanlig kombination, originaldokumentet finns kvar. Ingen dataförlust. | Uppföljning. Hänger ihop med ej körd regression för dokumentformat. |


## 6. Avvikelser från plan

*Beskriv betydande avvikelser från testplanen, exempelvis ändrat scope, försenad miljö, saknad testdata, resursförändringar eller reducerad regression.*

| **Avvikelse** | **Påverkan på testningen** | **Åtgärd / hantering** |
| --- | --- | --- |
| Testare B lämnade projektet (Del 3) | En fjärdedel mindre testkapacitet. Funktionellt systemtest och E2E saknade ägare. | Ansvar omfördelat till Testare A, C och D. P2-målet sänkt till 80 %, webbläsartest som stickprov. Testplan version 2.0. |
| SYS fem arbetsdagar försenad | SIT och systemtest sköts fram. Systemtestet kortades från fyra till tre veckor. | Väntetiden användes till testfall, testdata och automation. |
| Nytt krav på rolländringar (R11) | Nytt P1-område utan extra tid. | Nya testfall och ny risk. High 2 visar att kravet inte är helt uppfyllt. |
| Fast releasedatum | Förseningarna kunde inte lösas genom att flytta release. | Komprimerad tidplan och riskbaserad prioritering. |
| Instabil kreditupplysningstjänst (1,5 arbetsdag) | 14 tester blockerade i vecka 1. | Eskalerat till leverantör och projektledare. Blockeringarna kunde till största delen hävas. |
| 20 % efter plan efter vecka 1 | Risk att P1-områden inte hann verifieras. | P1-områden prioriterades, daglig defect triage. 97 % kördes till slut. |
| Prestandatest endast med 350 användare | Kravet på 500 användare är inte verifierat. | Accepterad avvikelse. Separat prestandaverifiering efter release. |
| Reducerad regression (90 %) | Perifera scenarier är inte regressionstestade. | Ej körda tester körs efter release. |
| 10 tester utan registrerad status | Resultatet är inte fullständigt spårbart. | Ska utredas och redovisas. |



## 7. Risker

*Beskriv viktiga risker som identifierades under testarbetet och hur de hanterades.*

| **Risk** | **Konsekvens** | **Åtgärd** | **Status** |
| --- | --- | --- | --- |
| R1 Felaktig kreditbedömning (DEF-101) | Lån beviljas trots för hög belåningsgrad. | Rättning, omtest 15 gånger, regression av riskregler. | Hanterad |
| R2 Dubbelgodkännande kringgås (DEF-112) | Stora lån utan senior handläggare. | Rättning, omtest, E2E. | Hanterad |
| R3/R4 Behörighet och persondata (DEF-124) | Ärenden och persondata synliga för fel region (GDPR). | Rättning, regression, behörighetstest. | Hanterad |
| R5 Instabil kreditupplysning (DEF-118 / High 1) | Blockerade tester. Beslut på ofullständiga uppgifter. | Eskalering. Felet minskat till otydlig status. | Delvis hanterad |
| R11 Rolländringslogg (DEF-121 / High 2) | Bristande spårbarhet vid revision. | Rättning påbörjad, uppföljning efter release. | Kvarstår |
| R9 Prestanda | Långsamma svar eller driftstörning vid hög last. | Test med 350 användare, verifiering efter release. | Kvarstår |
| Projektrisk: minskad kapacitet och försenad SYS | Testning hinns inte med. | Omplanering i version 2.0, prioritering av P1. | Hanterad |


## 8. Kvarstående risk

*Beskriv de risker och osäkerheter som fortfarande finns efter avslutad testning. Ta med exempelvis otestade områden, öppna fel, begränsad coverage eller skillnader mellan test och produktion.*

| **Kvarstående risk** | **Konsekvens** | **Risknivå** | **Riskägare / accepterad av** |
| --- | --- | --- | --- |
| Prestanda mellan 350 och 500 samtidiga användare är inte verifierad | Långsamma svar eller driftstörning vid hög last, till exempel vid månadsskifte eller migrering. | Medel–hög | PO och projektledare (accepterad i Go/No-Go) |
| High 2: tidigare roll saknas ibland i rolländringsloggen | Säkerhetskravet R11 är inte helt uppfyllt. Revisionsrisk. | Medel–hög | Säkerhetsavdelningen och PO – bör accepteras formellt |
| High 1: otydlig status vid timeout | Manuellt merarbete, risk för förvirring hos handläggare. | Medel | PO |
| High 3: dokumentversioner | Fel version kan visas i ovanliga fall. | Låg | PO |
| Ej körd regression (10 %) | Fel i perifera scenarier kan upptäckas först i produktion. | Låg–medel | Testledare, accepterad av PO |
| 10 tester utan registrerad status | Okänt om de visar fel. | Okänd | Testledare |
| 8 Medium- och 11 Low-defekter | Mindre störningar i arbetet. | Låg | PO (accepterade i UAT) |
| Begränsad tid för rollback | Det gamla systemets avtal upphör vid årsskiftet, så möjligheten att backa krymper med tiden. | Medel | Projektledare |


## 9. Slutsats

*Sammanfatta vad testningen visar om lösningens kvalitet och testmålen. Beskriv om Exit Criteria uppnåddes och vilka begränsningar som finns.*
264 Passed, 10 Failed, 6 Blocked, 10 Not Run. 10 tester saknar registrerad status.
Med en större testcoverage har vi kunnat verifiera alla risker och ta bort kritiska och ett flertal high defekter. 
För den kritiska defekten från vecka 1, har det genomförts restest på alla plenerade tester och allt godkändes. 
DEF-101 är därför inte längre existerande. 

Det finns kvar några high defekter och prestanda testet har inte utförts enligt krav, men dessa anses inte vara kritiska och utför inget problem på något affärsflöde. De defekter som finns nu anses inte vara
krav och det går att lösa problemen manuelt.

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

Testrapport - \<Projekt / system\>
