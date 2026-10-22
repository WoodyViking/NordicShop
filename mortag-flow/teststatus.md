# Teststatusrapport – MortgageFlow (Del 4)

**Projekt:** MortgageFlow – NordFinance  
**Release:** 1.0  
**Period:** Efter första testveckan  
**Datum:** 2026-10-22  
**Författare:** Grupp 2  
**Version:** 1.0

> Rapporten följer Del 4:s punkter: Progress, Resultat, Defekter, Coverage, Risk Coverage, Overall Status och Rekommenderade åtgärder.

---

## 1. Progress

| Mått | Värde |
|---|---|
| Planerat (totalt testpaket) | 300 tester |
| Planerat efter vecka 1 | 160 tester |
| Genomfört | 128 tester |
| **Test Execution %** | **80 % (128/160)** |
| Andel av totalt testpaket | 43 % (128/300) |
| **Ligger vi enligt plan?** | **Nej – 32 tester (20 %) efter plan** |

**Kommentar:** Testningen ligger 32 tester (20 %) efter den planerade takten. 128 av 160 planerade tester är genomförda.

---

## 2. Resultat

| Status | Antal |
|---|---|
| Exekverade | 128 |
| Godkända (Passed) | 91 |
| Ej godkända (Failed) | 23 |
| Blockerade (Blocked) | 14 |
| Not Run | 172 |

**Pass rate:** 91/128 = **71 %**

*Kontroll: 91 + 23 + 14 = 128. 300 − 128 = 172 Not Run.*

---

## 3. Defekter

**Totalt rapporterade:** 31 defekter.  
**Öppna:** 26 (1 Critical, 6 High, 12 Medium, 7 Low). Resterande 5 är rättade och stängda.

### Viktigaste problem
- **DEF-101 (Critical):** Vid belåningsgrad över 85 % visas varning, men handläggaren kan ändå godkänna utan ytterligare kontroll. inträffade i 3 av 10 testförsök.
- **DEF-112 (High):** Lån över 5 MSEK kan i vissa situationer gå direkt från första handläggarens godkännande till Godkänd utan senior handläggares slutgodkännande. Fel kund kan få ett stort godkänt lån och det är en stor ekonomiskrisk för banken
- **DEF-118 (High):** Kreditupplysningstjänsten returnerar ibland timeout, men ärendet visas ändå som att kreditkontrollen är genomförd. Kreditbedömningen behöver inte vara genomförd för att den ska visas som genomförd, det blir onödig press på support. Sedan kan det även göras en felbedömning och det finns därför en ekonomisk risk för banken eftersom att en dålig kund kan få låna pengar.
- **DEF-121 (High):** Administratör kan tilldela en användare senior behörighet utan att tidigare roll loggas.För att bli senior handläggare måste man varit handläggare överhuvudtaget här gäller behörighet och därför GDPR
- **DEF-124 (High):** En handläggare kan se ett ärende som tillhör fel region. Eftersom att det är en behörighetsfråga kommer GDPR lagar att träda in och därför kan man stämma banken.
- **Miljöproblem:** Den externa kreditupplysningstjänsten har varit instabil under 1,5 arbetsdag. 14 testfall är fortfarande blockerade på grund av detta och relaterade testdata.
Allt som ska göras efter upplysningstjänsten kan inte testas vilket betyder att man inte kan testa kritiska affärsflöden.
- **2 High defekter:** Defekter som inte har någon dokumentation/information om vad de är för problem och vad dem påverkar. 

---

## 4. Coverage

| Testområde | Planerat hittills | Genomfört | Coverage | Kommentar |
|---|---|---|---|---|
| Login/MFA | 20 | 20 | 100 % | Få problem |
| Kundregistrering | 25 | 22 | 88 % | 3 Failed |
| Kreditkontroll | 30 | 18 | 60 % | Integration instabil |
| Riskregler | 20 | 17 | 85 % | Flera avvikelser |
| Ärendestatus | 15 | 14 | 93 % | 2 Failed |
| Stora lån / dubbelgodkännande | 15 | 9 | 60 % | Delvis blockerat |
| Dokument | 15 | 13 | 87 % | 3 Failed |
| Behörighet | 10 | 7 | 70 % | 2 High-defekter |
| E2E | 10 | 8 | 80 % | 1 kritiskt flöde Failed |
| **Totalt** | **160** | **128** | **80 %** | – |

**Väl testade områden:** Login/MFA (100 %), Ärendestatus (93 %), Kundregistrering (88 %), Dokument (87 %), Riskregler (85 %).

**Otillräckligt verifierade:** Kreditkontroll (60 %), Stora lån/dubbelgodkännande (60 %), Behörighet (70 %) och E2E (80 %, ett kritiskt flöde Failed).

---

## 5. Risk Coverage

| Risk | Färg | Varför | Påverkan | Åtgärd |
|---|---|---|---|---|
| R1 Kreditbedömning | 🔴 Röd | DEF-101 (Critical) öppen; låg coverage (Kreditkontroll 60 %, Riskregler 85 %) | Felaktiga kreditbeslut → ekonomisk förlust | Åtgärda DEF-101, beslutstabeller + gränsvärden, retest |
| R2 Lån > 5 MSEK | 🔴 Röd | DEF-112 (High) öppen; 60 % coverage + delvis block | Lån godkänns utan senior slutgodkännande | Fixa DEF-112, gränsvärden, behörighetstest, E2E |
| R3 Behörighet | 🔴 Röd | DEF-121 + DEF-124 (2 High); 70 % coverage | Obehörig åtkomst till ärenden/persondata | Retest + behörighetsmatris i UI och API |
| R4 GDPR/persondata | 🟡 Gul | DEF-124 indirekt (fel region = persondata exponeras); inget säkerhetstest redovisat | GDPR-incident, rättslig risk | Säkerhetstest med säkerhetsspecialist; verifiera kryptering + loggning |
| R5 Kreditupplysning | 🔴 Röd | DEF-118 (High) + 14 blockerade + 60 % coverage | Kreditkontroll visas som genomförd utan svar → fel beslut | Eskalera miljöproblemet; SIT negativa fall/timeout; fixa DEF-118 |
| R6 Inloggning/MFA | 🟢 Grön | 100 % coverage, få problem, inga öppna höga defekter | Låg | Behåll i regression |
| R7 Loggning/status | 🟡 Gul | DEF-121 visar att loggning inte är komplett; 93 % coverage | Spårbarhet brister → svårt att utreda beslut | Fixa DEF-121, verifiera ärendelogg (vem/när) |
| R8 Skadliga/stora filer | 🟡 Gul | Dokument 87 %, 3 Failed; otydligt verifierat | Skadlig fil kan laddas upp | Verifiera virusskanning + 10 MB-gräns + filtyper |
| R9 Prestanda (500 anv.) | 🔴 Röd | Inget prestandatest genomfört – risken är otestad | Instabilitet/svarstid vid belastning | Genomför prestandatest (P2) |
| R10 E-postbekräftelse | 🟡 Gul | E2E 80 %, inga namngivna defekter – delvis verifierad | Kund får ingen/fel bekräftelse | SIT + E2E med rätt mottagare/innehåll |

**Verifierade risker:** R6 (inloggning/MFA).

**Osäkra risker:** R1, R2, R3, R5 (röda) samt R4, R7, R8, R10 (gula). R9 är helt otestad.

---

## 6. Overall Status

### 🔴 RÖD

**Varför:** Testningen ligger 20 % efter plan (32 tester), en Critical-defekt (DEF-101) är öppen i kreditbedömningen och kreditupplysningens integration har varit instabil (14 blockerade tester). Fyra högrisker (R1, R2, R3, R5) är ännu inte verifierade och prestandarisken (R9) är helt otestad. 2 höga defekter är upptäckta som saknar information.

**Påverkan:** Kritiska affärsflöden – kreditbedömning, stora lån och kreditkontroll – kan inte verifieras som säkra. Det innebär hög release-risk: systemet kan fatta felaktiga kreditbeslut eller visa en kreditkontroll som genomförd utan svar. Release bör inte genomföras i nuvarande läge.

**Åtgärd:** Eskalera miljöproblemet till leverantör och DevOps, åtgärda DEF-101/112/118/121/124, kör SIT/API-test på kreditintegrationen och följ upp med retest + regression. Om inte den kritiska defekten och miljöproblemet är lösta inom veckan ska Go/No-Go omprövas. Begär mer information om de 2 höga defekterna som inte hade information.

## 7. Rekommenderade åtgärder

**Prioritering (1 = högst):**

| Prioritet | Åtgärd |
|---|---|
| 1 | Miljöproblemet – eskalera till leverantör/DevOps och återställ stabil kreditupplysningstjänst |
| 1 | DEF-101 (Critical) – åtgärda och retesta |
| 2 | DEF-118 (High) – timeout ska inte visas som genomförd kreditkontroll |
| 2 | DEF-112 (High) – säkerställ senior slutgodkännande för lån > 5 MSEK |
| 2 | DEF-121 (High) – logga tidigare roll vid behörighetsändring |
| 2 | DEF-124 (High) – begränsa ärenden per region |
| 2 | Information - 2 Höga defekter behöver få information om vad de påverkar |
| 3 | SIT/API-test på kreditintegrationen (Testare A) |
| 3 | Retest av åtgärdade defekter |
| 3 | Påbörja regression av kritiska flöden |
| 4 | Prestandatest (R9) – planera in, risken är i dag otestad |
| 5 | Övriga Medium/Low-defekter – väntar tills Critical/High är avklarade |

**Nästa vecka:** Börja med miljöproblemet, därefter SIT/API-testning av kreditintegrationen, retest av DEF-101/112/118/121/124 och påbörja regression. Lägre prioriterade defekter hanteras först när alla Critical- och High-defekter är avklarade.

