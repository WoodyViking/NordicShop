# TESTRAPPORT

*Mall för sammanställning och avslut av testarbete*

| **Projekt / system** | \<Namn> |
| --- | --- |
| **Release / version** | \<Version> |
| **Testperiod** | \<Datum - datum> |
| **Dokumentägare** | \<Namn / roll> |
| **Datum** | \<Datum> |
| **Status** | \<Utkast / Slutlig> |

*Använd mallen för att sammanfatta genomfört testarbete, resultat, avvikelser och kvarstående risker. Ersätt text inom \<hakparenteser> och anpassa omfattningen efter projektets behov.*

# 1. Sammanfattning

*Ge en kort ledningssammanfattning av testperioden. Beskriv vad som testats, övergripande resultat, viktigaste avvikelserna och den samlade bedömningen.*

\<Sammanfattning>

Testningen omfattade 250 planerade tester inom områdena login, kundvagn, checkout, betalning, order, lager, leverans, refund, behörigheter, kritiska E2E-flöden, regression samt UAT. Av dessa genomfördes 240 tester, varav 225 passerade, 7 misslyckades och 8 blockerades. Samtliga P1-tester genomfördes och de tre kritiska E2E-flödena passerade efter rättningar. Två Critical-defekter identifierades – betalning utan order samt dubbel debitering – och båda är rättade, retestade och verifierade. Fyra High-defekter kvarstår, varav den viktigaste gäller ett ovanligt refundscenario med manuell workaround som verksamheten accepterat. Regression genomfördes till 95 % med riskbaserad prioritering. UAT är godkänd och verksamheten accepterar de dokumenterade kvarstående riskerna. Technical Readiness är uppfylld med produktionsbuild, deploymentplan, verifierad rollback, aktiv monitoring och supportberedskap. Sammantaget bedöms Release 4.0 ha god kvalitet med hanterbara kvarstående risker.

# 2. Scope

*Beskriv vad som ingick i testarbetet och eventuella avgränsningar. Koppla gärna till kritiska affärsflöden, testnivåer och testtyper.*

| **Område / flöde** | **Testnivå / testtyp** | **Prioritet** | **Kommentar** |
| --- | --- | --- | --- |
| Login | Funktionalitet/systemtest | Hög |  |
| Kundvagn | Funktionalitet/systemtest | Hög |  |
| Checkout | Funktionalitet/E2E |  |  |
| betalning | Funktionalitet/integration |  |  |
| order | Funktionalitet/systemtest |  |  |
| lager | Funktionalitet/systemtest |  |  |
| leverans | Funktionalitet/systemtest |  |  |
| refund | Funktionalitet/systemtest |  |  |
| behörigheter | Funktionalitet/säkerhet |  |  |
| kritiska E2E-flöden | E2E |  |  |
| regression | regresion |  |  |
| UAT | Acceptanstest |  |  |

# 3. Genomförda tester

*Sammanställ vilka tester och testaktiviteter som genomfördes. Redovisa relevant coverage och vad som eventuellt inte genomfördes.*

| **Testområde** | **Planerat** | **Genomfört** | **Status / kommentar** |
| --- | --- | --- | --- |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |

# 4. Resultat

*Sammanfatta testresultatet. Siffror ska kompletteras med en kort analys av vad resultatet innebär.*

| **Mätetal** | **Resultat** | **Kommentar** |
| --- | --- | --- |
| \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> |

# 5. Defekter

*Sammanfatta identifierade och kvarstående defekter. Fokusera på allvarlighetsgrad, påverkan och status - inte enbart antal.*

| **Severity** | **Totalt** | **Öppna** | **Kommentar / påverkan** |
| --- | --- | --- |--- |
| Critical | 2 | 0 |  |
| High | 9 | 4 |  |
| Medium | 17 | 6 |  |
| Low | 12 | 7 |  |

# 6. Avvikelser från plan

*Beskriv betydande avvikelser från testplanen, exempelvis ändrat scope, försenad miljö, saknad testdata, resursförändringar eller reducerad regression.*

| **Avvikelse** | **Påverkan på testningen** | **Åtgärd / hantering** |
|---|---|---|
| Payment Provider SYS var otillgänglig en dag | Betalningstester försenades. Mindre tid för betalning och retest, vilket är ett högriskområde |  |
| En testare var sjuk i tre dagar | Vissa lågprioriterade tester omplanerades. Troligen en del av de 10 ej körda testerna |  |
| Testdata saknades för vissa refundscenarier | 8 tester blockerades. Refund är inte fullt verifierad |  |
| Full regression kunde inte genomföras | 95 % genomfördes med riskbaserad prioritering. 5 % ej körd, vilket är en kvarstående risk |  |

# 7. Risker

*Beskriv viktiga risker som identifierades under testarbetet och hur de hanterades.*

| **Risk** | **Konsekvens** | **Åtgärd** | **Status** |
| --- | --- | --- | --- |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |

# 8. Kvarstående risk

*Beskriv de risker och osäkerheter som fortfarande finns efter avslutad testning. Ta med exempelvis otestade områden, öppna fel, begränsad coverage eller skillnader mellan test och produktion.*

| **Kvarstående risk** | **Konsekvens** | **Risknivå** | **Riskägare / accepterad av** |
| --- | --- | --- | --- |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |

# 9. Slutsats

*Sammanfatta vad testningen visar om lösningens kvalitet och testmålen. Beskriv om Exit Criteria uppnåddes och vilka begränsningar som finns.*

\<Slutsats>

# 10. Rekommendation

*Ge en tydlig rekommendation baserad på testresultat och kvarstående risk. Exempel: GO, CONDITIONAL GO, NO-GO eller rekommenderade åtgärder efter release.*

| **Rekommendation** | \<GO / CONDITIONAL GO / NO-GO / annan> |
| --- | --- |
| **Motivering** | \<Kort motivering utifrån risk> |
| **Villkor / åtgärder** | \<Eventuella villkor eller uppföljning> |
| **Ansvar / uppföljning** | \<Roll / datum> |

# 11. Godkännande / mottagare

*Dokumentera vid behov vilka roller som har tagit del av eller godkänt testrapporten.*

| **Roll** | **Namn** | **Datum** | **Kommentar** |
| --- | --- | --- | --- |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |
