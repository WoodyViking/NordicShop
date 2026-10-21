# TESTRAPPORT


| --- | --- |
| **Projekt / system** | NordFinance - MortgageFlow |
| **Release / version** | 1.0 |
| **Testperiod** | Vecka 1 |
| **Dokumentägare** | Grupp 2 |
| **Datum** | 2026-10-21 |
| **Status** | Pågående / Slutlig |

# Innehåll

- [1. Sammanfattning](#1-sammanfattning)
- [2. Scope](#2-scope)
- [3. Genomförda tester](#3-genomförda-tester)
- [4. Resultat](#4-resultat)
- [5. Defekter](#5-defekter)
- [6. Avvikelser från plan](#6-avvikelser-från-plan)
- [7. Risker](#7-risker)
- [8. Kvarstående risk](#8-kvarstående-risk)
- [9. Slutsats](#9-slutsats)
- [10. Rekommendation](#10-rekommendation)
- [11. Godkännande / mottagare](#11-godkännande--mottagare)

# 1. Sammanfattning

Status: 🔴 RÖD
128/300 43% test genomfört
Planen var 160 53%
Testtakten är alltså 80 % av de planerade 160 test, utan att räkna de 14 blockeade så blir det 71%. 
Ett Critical-fel (DEF-101) och sex High-fel är öppna varav 2 är inte verifierade.
Alla fyra beskrivna High-fel ligger i högriskområden: kreditbeslut, dubbelgodkännande, behörighet och rolländring. 
Den instabila kreditupplysningstjänsten (1,5 arbetsdag) blockerar 14 tester.

# 2. Scope

| **Område / flöde** | **Testnivå / testtyp** | **Prioritet** | **Kommentar** |
| --- | --- | --- | --- |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |

# 3. Genomförda tester

| **Testområde** | **Planerat** | **Genomfört** | **Status / kommentar** |
| --- | --- | --- | --- |
| Login/MFA | 20 | 20 | 100% Få problem |
| Kundregistrering | 25 | 22 | 88% 3 Failed |
| Kreditkontroll | 30 | 18 | 60% Integration instabil |
| Riskregler | 20 | 17 | 85% Flera avvikelser |
| Ärendestatus | 15 | 14 | 93% 2 Failed |
| Stora lån / dubbelgodkännande | 15 | 9 | 60% Delvis Blocked |
| Dokument | 15 | 13 | 86% 3 Failed |
| Behörighet | 10 | 7 | 70% 2 High-defekter |
| E2E | 10 | 8 | 80% 1 kritiskt flöde Failed |
| **Totalt genomförda tester** | **160** | **128** | 80 % av planerad takt. Inkluderar 14 blockerade. |
| **Total godkända tester** | – | **91** | 71 % av genomförda och 30 % av hela paketet (300). |

# 4. Resultat

| **Mätetal** | **Resultat** | **Kommentar** |
| --- | --- | --- |
| Alla tester | 300 | Fullständig testpaket |
| Planerade Tester | 160 | Första veckan |
| Executed | 128 | Genomförda tester |
| Passed | 91 | Lyckade tester |
| Failed | 23 | Misslyckade tester |
| Blocked | 14 | Blockerade tester |
| Not Run | 172 | Icke körda tester |


# 5. Defekter

*Sammanfatta identifierade och kvarstående defekter. Fokusera på allvarlighetsgrad, påverkan och status - inte enbart antal.*

| **Severity** | **Totalt** | **Öppna** | **Kommentar / påverkan** |
| --- | --- | --- | --- |
| Critical | 1 | **DEF-101:** belåningsgrad över 85 % ger varning, men handläggaren kan godkänna utan kontroll från senior handläggare, (3 av 10 testförsök). Risk för felaktiga kreditbeslut. |
| High | 6 | **DEF-112:** lån över 5 MSEK kan gå till Godkänd utan senior handläggares godkännande. **DEF-118:** timeout från kreditupplysningen visas som genomförd kreditkontroll. **DEF-121:** rolländring loggar inte tidigare roll, vilket bryter mot det nya kravet. **DEF-124:** handläggare ser ärende från fel region. Två High defekter är inte beskrivna. |
| Medium | 12 | Ingen specificerad påverkan. Hanteras i triage. |
| Low | 7 | Ingen specificerad påverkan. Hanteras i triage. |EF-118:** timeout från kreditupplysningen visas som genomförd kreditkontroll. **DEF-121:** rolländring loggar inte tidigare roll, vilket bryter mot det nya kravet. **DEF-124:** handläggare ser ärende från fel region. Två High-fel är inte närmare beskrivna. |
| Medium | 12 | Ingen specificerad påverkan. Hanteras i triage |
| Low | 7 | Ingen specificerad påverkan. Hanteras i triage |

# 6. Avvikelser från plan

| **Avvikelse** | **Påverkan på testningen** | **Åtgärd / hantering** |
| --- | --- | --- |
| **Testtakten ligger under plan.** 128 av 160 planerade tester är genomförda (80 %). Utan de 14 blockerade är det 114 (71 %). | 32 tester ligger efter, och 27 av dem är P1. P1-områdena ligger på 78 % av plan och P2-områdena på 88 %. Risk att systemtestet inte hinner klart. | P1 prioriteras. P2-områden (kundregistrering, dokument) körs bara som omtest tills P1 är i takt med planen. |
| **Kreditupplysningstjänsten är instabil.** Instabil under 1,5 arbetsdag, och relaterade testdata. | 14 tester är blockerade. Kreditkontroll ligger på 18 av 30 och stora lån på 9 av 15. | Eskalera till DevOps och representanten från kreditupplysningen. Använd stub enligt planen. |
| **Fler och allvarligare fel än väntat i P1-områdena.** 31 rapporterade och 26 öppna, varav 1 Critical och 6 High. | Planens slutkriterium (7.2) kräver inga öppna S1/S2 i P1-områden. Tid går åt till triage, omtest och regression. | Daglig defect triage i stället för tre gånger i veckan. DEF-101 och DEF-112 rättas och omtestas först. |

# 7. Risker

| **Risk** | **Konsekvens** | **Åtgärd** | **Status** |
| --- | --- | --- | --- |
| **R1, DEF-101 (Critical):** ansökan med belåningsgrad över 85 % kan godkännas utan ytterligare kontroll (3 av 10 försök). | Felaktiga kreditbeslut och ekonomisk förlust. Intermittent, vilket gör felet svårt att avgränsa. | Prioriterad rättning. Dokumentera förutsättningarna och upprepa minst 10 försök vid omtest. | Öppen |
| **R2, DEF-112 (High):** lån över 5 MSEK kan gå till Godkänd utan senior handläggares godkännande. | Den interna kontrollen för stora lån kringgås. | Rätta först, och testa sedan gränsvärdena 4 999 999, 5 000 000 och 5 000 001 SEK. | Öppen |
| **R5, DEF-118 (High):** timeout från kreditupplysningen visas som genomförd kreditkontroll. | Ärenden kan se ut att ha fått kreditkontroll fast den inte gjorts. 14 tester är blockerade. | Rätta DEF-118, avblockera med stub och verifiera mot den riktiga tjänsten. | Öppen |
| **R3, R4, DEF-124 (High):** handläggare kan se ärende från fel region. | Otillåten åtkomst till persondata och risk för GDPR-incident. | Säkerhetsspecialisten bedömer påverkan. Rättning, och Testare D slutför behörighetstesterna. | Öppen |
| **R11, DEF-121 (High):** rolländring loggar inte tidigare roll. | Det nya säkerhetskravet uppfylls inte och spårbarheten saknas. | Rättning, och testa därefter att loggposten innehåller användare, tidpunkt, tidigare och ny roll. | Öppen |
| **Tidsrisk:** eftersläpning, fast releasedatum och ingen buffert. | P1-tester hinner inte klart före acceptanstest och Go/No-Go. | Prioritera P1, daglig triage och daglig status till PO och projektledare. | Ökad |

# 8. Kvarstående risk

| **Kvarstående risk** | **Konsekvens** | **Risknivå** | **Riskägare / accepterad av** |
| --- | --- | --- | --- |
| **Kvarstående risk** | **Konsekvens** | **Risknivå** | **Riskägare / accepterad av** |
| --- | --- | --- | --- |
| Kreditbeslut och affärsregler ej verifierade (R1). DEF-101 öppen och kreditkontroll 18 av 30. | Felaktiga kreditbeslut och ekonomisk förlust. | Hög | Product Owner / ej accepterad |
| Dubbelgodkännande ej verifierat (R2). DEF-112 öppen, 9 av 15 testade. | Lån över 5 MSEK kan godkännas utan kontroll. | Hög | Product Owner / ej accepterad |
| Behörighet och persondata ej verifierade (R3, R4). DEF-124 öppen, 7 av 10 testade. | Otillåten åtkomst och GDPR-incident. | Hög | Product Owner och säkerhetsspecialist / ej accepterad |
| Integrationen mot kreditupplysningen ej verifierad (R5). Instabil och DEF-118 öppen. | Kreditkontroll kan utebli utan att det syns. | Hög | Product Owner / ej accepterad |
| Rolländring ej verifierad (R11). DEF-121 öppen. | Nytt säkerhetskrav ej uppfyllt. | Hög | Product Owner och säkerhetsspecialist / ej accepterad |
| Prestanda (R9), e-post (R10) och säkerhetstest har inga resultat ännu. | Okänd prestanda under last och okänd kvalitet på e-postbekräftelser. | Medel | Product Owner / ej accepterad |
| 172 tester ej körda (57 % av paketet) och 23 failed som ska omtestas. | Okända fel kan finnas kvar. | Medel | Testledare / ej accepterad |

# 9. Slutsats

Testningen visar att Login/MFA, ärendestatus, kundregistrering och dokumenthantering fungerar. Kreditbeslut och dubbelgodkännande har däremot allvarliga brister, och behörighet, persondata och det nya kravet på rolländring har hittade fel. Alla P1-tester är inte genomförda, eftersom 27 P1-tester ligger efter. Öppna S1/S2-fel i P1-områden är inte uppfyllt (1 Critical och 6 High är öppna). Två High defekter är inte beskrivna.
Status är 🔴

# 10. Rekommendation

*Ge en tydlig rekommendation baserad på testresultat och kvarstående risk. Exempel: GO, CONDITIONAL GO, NO-GO eller rekommenderade åtgärder efter release.*

| | |
| --- | --- |
| **Rekommendation** | \<GO / CONDITIONAL GO / NO-GO / annan> |
| **Motivering** | \<Kort motivering utifrån risk> |
| **Villkor / åtgärder** | \<Eventuella villkor eller uppföljning> |
| **Ansvar / uppföljning** | \<Roll / datum> |

# 11. Godkännande / mottagare

*Dokumentera vid behov vilka roller som har tagit del av eller godkänt testrapporten.*

| **Roll** | **Namn** | **Datum** | **Kommentar** |
| --- | --- | --- | --- |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |
