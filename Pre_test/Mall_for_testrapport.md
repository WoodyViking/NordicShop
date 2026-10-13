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
| Login | | |  |
| Kundvagn | | |  |
| Checkout |  |  |  |
| betalning |  |  |  |
| order |  |  |  |
| lager | |  |  |
| leverans | |  |  |
| refund |  |  |  |
| behörigheter |  |  |  |
| kritiska E2E-flöden | |  |  |
| regression | |  |  |
| UAT |  |  |  |

# 4. Resultat

*Sammanfatta testresultatet. Siffror ska kompletteras med en kort analys av vad resultatet innebär.*

| **Mätetal** | **Resultat** | **Kommentar** |
| --- | --- | --- |
| Planerade tester |	250 |	Fullständig testplan |
| Executed |	240 |	96 % av planerade tester genomfördes |
| Passed	| 225 |	93,75 % av executed tester passerade |
| Failed |	7 |	2,9 % av executed tester misslyckades |
| Blocked |	8 |	3,3 % av executed tester blockerades |
| Not Run |	10 |	4 % av planerade tester kördes inte |
| P1-tester |	100 % |	Samtliga genomförda |
| Kritiska E2E-flöden |	3/3 |	Efter genomförda rättningar |
| Regression |	95 % |	Riskbaserad prioritering |
| UAT |	Godkänd |	Verksamheten accepterar kvarstående risker |

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
| Payment Provider SYS var otillgänglig en dag | Betalningstester försenades. Mindre tid för betalning och retest, vilket är ett högriskområde | Tester omplanerades och genomfördes senare |
| En testare var sjuk i tre dagar | Vissa lågprioriterade tester omplanerades. Troligen en del av de 10 ej körda testerna | Resurser omfördelades, lågprioriterade tester sköts upp |
| Testdata saknades för vissa refundscenarier | 8 tester blockerades. Refund är inte fullt verifierad | Manuell workaround dokumenterades, verksamheten accepterade |
| Full regression kunde inte genomföras | 95 % genomfördes med riskbaserad prioritering. 5 % ej körd, vilket är en kvarstående risk | Riskbaserad prioritering tillämpades |

# 7. Risker

*Beskriv viktiga risker som identifierades under testarbetet och hur de hanterades.*

| **Risk** | **Konsekvens** | **Åtgärd** | **Status** |
| --- | --- | --- | --- |
| Payment Provider SYS otillgänglig | **Inträffade.** Betalningstester försenades en dag. |  |  |
| Resursbortfall (sjukdom) | **Inträffade.** Lågprioriterade tester omplanerades. |  |  |
| Saknad testdata för refund | **Inträffade.** 8 tester blockerades. | Manuell workaround |  |
| Tidsbrist för full regression | **Inträffade.** 95 % genomfördes med riskbaserad prioritering. | Riskbaserad prioritering |  |
| SYS skiljer sig från Payment Providers produktionsmiljö | **Kvarstår.** Fel kan visa sig först i produktion. |  |  |
| Belastningsproblem | **Kvarstår.** Inget fullständigt belastningstest. |  |  |

# 8. Kvarstående risk

*Beskriv de risker och osäkerheter som fortfarande finns efter avslutad testning. Ta med exempelvis otestade områden, öppna fel, begränsad coverage eller skillnader mellan test och produktion.*

| **Kvarstående risk** | **Konsekvens** | **Risknivå** | **Riskägare / accepterad av** |
| --- | --- | --- | --- |
| **Refundscenarier inte fullt verifierade** (8 blockerade tester) | Saknad testdata. Fel eller utebliven återbetalning till kund, tillsammans med den kända High-defekten | **Hög** |  |
| **Fyra High-defekter är öppna** | Hann inte rättas. Fel i refund och andra funktioner. Hanteras med workarounds | **Medel** | |
| **Fullständigt belastningstest genomfördes inte** | Utanför scope. Långsamt eller nere vid hög trafik | **Medel** (Hög om hög trafik väntas) | |
| **SYS skiljer sig från Payment Providers produktionsmiljö** | Testmiljön är inte identisk. Betalningsfel som bara syns i produktion | **Medel** | |
| **5 % av regressionen ej körd** | Tidsbrist, riskbaserat urval. Fel i ej testade oförändrade områden | **Låg** | |




# 9. Slutsats

*Sammanfatta vad testningen visar om lösningens kvalitet och testmålen. Beskriv om Exit Criteria uppnåddes och vilka begränsningar som finns.*

\<Slutsats>
Testningen visar att NordicShop Release 4.0 är stabil i de kritiska flödena. Alla P1-tester och alla tre kritiska E2E-flöden är godkända, båda Critical-defekterna är åtgärdade och verifierade, och UAT är godkänd. Tekniskt är releasen redo, med verifierad rollback, aktiv monitorering och supportberedskap.

Kvarstående risk är koncentrerad till refund (blockerade tester och en känd High-defekt) och till det som inte testats (belastning och 5 % av regressionen). Dessutom skiljer sig SYS något från Payment Providers produktionsmiljö, så betalningsfel kan visa sig först i produktion. De riskerna är kända, dokumenterade och accepterade av verksamheten, men refund är det område som bör följas noggrant.

Kvaliteten är alltså god nog för release om riskerna hanteras, men inte riskfri.

# 10. Rekommendation

*Ge en tydlig rekommendation baserad på testresultat och kvarstående risk. Exempel: GO, CONDITIONAL GO, NO-GO eller rekommenderade åtgärder efter release.*

| **Rekommendation** | \<GO / CONDITIONAL GO / NO-GO / annan> |
| --- | --- |
| **Motivering** | Testningen visar god kvalitet med hög pass rate och samtliga kritiska flöden verifierade. Fyra High-defekter kvarstår dock, varav en påverkar refundscenarier. Verksamheten har accepterat riskerna och manuell workaround finns. Fullständig regression och belastningstest saknas. |
| **Villkor / åtgärder** | 1. **Refund:** de 8 blockerade refundtesterna körs före release när testdata finns. Om det inte hinns ska den manuella refundprocessen och daglig avstämning vara på plats.
2. **Monitorering:** larm för betalning utan order, misslyckade återbetalningar och hög belastning är aktiva, med namngiven ägare de första dagarna.
3. **Support:** kundservice är instruerad om workarounds för de fyra High-defekterna och om den manuella refundprocessen.
4. **Smoke test i produktion:** körs direkt efter driftsättning, inklusive en betalning, eftersom SYS skiljer sig från Payment Providers produktionsmiljö.
5. **Rollback:** den verifierade planen är redo, med ett tydligt utlösningskriterium och en ansvarig beslutsfattare.
6. **Efter release:** belastningstest och resterande 5 % av regressionen körs, och de fyra High-defekterna rättas i nästa release. |
| **Ansvar / uppföljning** | Testledare / datum> |

# 🟡 CONDITIONAL GO

**Motivering**

| Steg | Bedömning |
|---|---|
| **Resultat** | 96 % genomfört, 93,8 % Passed, alla P1-tester och kritiska E2E-flöden Passed, regression 95 %. |
| **Defekter** | 0 Critical, 4 High med workarounds, och Critical-felen i betalning och debitering är rättade och retestade. |
| **Kvarstående risk** | Refund är inte fullt verifierad (Hög), samt belastning, SYS-skillnader och High-defekter (Medel). Alla är dokumenterade och accepterade av verksamheten. |
| **Varför inte GO** | Refund är ett område som rör kundens pengar och är inte fullt verifierat, och belastning är inte testad. En ren GO vore för säkert. |
| **Varför inte NO-GO** | Inga Critical är öppna, de kritiska flödena fungerar, UAT är godkänd, tekniken är redo och riskerna har workarounds och är accepterade. Att stoppa skulle kosta mer än den kvarstående risken motiverar. |

**Villkor**

1. **Refund:** de 8 blockerade refundtesterna körs före release när testdata finns. Om det inte hinns ska den manuella refundprocessen och daglig avstämning vara på plats.
2. **Monitorering:** larm för betalning utan order, misslyckade återbetalningar och hög belastning är aktiva, med namngiven ägare de första dagarna.
3. **Support:** kundservice är instruerad om workarounds för de fyra High-defekterna och om den manuella refundprocessen.
4. **Smoke test i produktion:** körs direkt efter driftsättning, inklusive en betalning, eftersom SYS skiljer sig från Payment Providers produktionsmiljö.
5. **Rollback:** den verifierade planen är redo, med ett tydligt utlösningskriterium och en ansvarig beslutsfattare.
6. **Efter release:** belastningstest och resterande 5 % av regressionen körs, och de fyra High-defekterna rättas i nästa release.




# 11. Godkännande / mottagare

*Dokumentera vid behov vilka roller som har tagit del av eller godkänt testrapporten.*

| **Roll** | **Namn** | **Datum** | **Kommentar** |
| --- | --- | --- | --- |
| \<...> | \<...> | \<...> | \<...> |
| \<...> | \<...> | \<...> | \<...> |
