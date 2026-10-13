# Workshop – Skriv en testrapport för NordicShop

> Rapporten följer de tio delarna i uppgiften. Den utdelade testrapportmallen finns inte bland uppladdade filer, så om mallen har andra rubriker eller ordning behöver innehållet flyttas dit.

# Testrapport – NordicShop Release 4.0

| | |
|---|---|
| **Projekt** | NordicShop |
| **Release** | 4.0 |
| **Författare** | Testledare (Grupp 2) |
| **Status** | Slutlig testrapport |

---

## 1. Sammanfattning

NordicShop Release 4.0 är färdigtestad: 240 av 250 planerade tester är genomförda (96 %), och 225 av dem har Passed (93,8 %). Alla P1-tester är genomförda och alla tre kritiska E2E-flöden har Passed efter rättningar. Båda Critical-defekterna (betalning utan order och dubbel debitering) är rättade och retestade, så inga Critical-defekter är öppna. Fyra High-defekter kvarstår, och den viktigaste gäller ett ovanligt refundscenario med en manuell workaround som verksamheten har accepterat. Regressionen är 95 % genomförd med riskbaserad prioritering, och UAT är godkänd. Testningen påverkades av en dags nedtid i Payment Providers SYS, tre sjukdagar och saknad testdata för refund, vilket blockerade 8 tester. Därför är vissa refundscenarier inte fullt verifierade, och något fullständigt belastningstest ingick inte. Tekniskt är releasen redo, med verifierad rollback, aktiv monitorering och supportberedskap. Vi rekommenderar **🟡 CONDITIONAL GO**, med villkor som rör refund, betalning och övervakning.

---

## 2. Scope

**Ingick i testningen**

- Login
- Kundvagn
- Checkout
- Betalning
- Order
- Lager
- Leverans
- Refund
- Behörigheter
- Kritiska E2E-flöden
- Regression
- UAT

**Ingick inte**

- **Fullständigt belastningstest.** Prestanda vid hög trafik är därför inte verifierad.
- Områden utanför listan ovan (till exempel kundprofil, sök och UI) nämns inte i underlaget. **[KONTROLLERA: fyll i om något annat uttryckligen var avgränsat.]**

---

## 3. Genomförda tester

| | Antal | Andel av 250 |
|---|---|---|
| Planerade | 250 | 100 % |
| **Genomförda (Executed)** | **240** | **96 %** |
| Ej genomförda (Not Run) | 10 | 4 % |

**Vad som genomfördes**
- Alla P1-tester.
- Alla tre kritiska E2E-flöden (Passed efter rättningar).
- 95 % av planerad regression, med riskbaserad prioritering.
- UAT (godkänd).

**Vad som återstod**
- 10 tester ej körda. Underlaget anger inte vilka, men avvikelserna visar att lågprioriterade tester omplanerades när en testare var sjuk. **[KONTROLLERA: lista vilka tester det är.]**
- 8 tester blockerades (saknad testdata för vissa refundscenarier).
- 5 % av regressionen (ej körd).

---

## 4. Resultat

| Status | Antal | Andel av genomförda (240) | Andel av planerade (250) |
|---|---|---|---|
| Passed | 225 | 93,8 % | 90 % |
| Failed | 7 | 2,9 % | 2,8 % |
| Blocked | 8 | 3,3 % | 3,2 % |
| Not Run | 10 | – | 4 % |

(Passed + Failed + Blocked = 240. Blockerade tester ingår alltså i "genomförda", vilket gör att genomförandegraden ser högre ut än antalet tester som gett ett resultat. Räknas bara Passed och Failed har 232 tester (92,8 % av planerade) gett ett faktiskt resultat.)

**Vad siffrorna betyder**
- **96 % genomförda och 93,8 % Passed** är en hög nivå, och alla P1-tester och kritiska E2E-flöden är gröna.
- **Failed (7)** ska vara kopplade till de kvarstående defekterna, annars saknas ett defekt-ID. **[KONTROLLERA]**
- **Blocked (8)** är det som oroar mest av de siffrorna, eftersom de ligger i refund, ett område som rör kundens pengar. Där finns alltså fler fel dolda.
- **Regression 95 %** uppfyller normalt kravet på minst 95 %, men det är precis på gränsen och bygger på riskbaserad prioritering.
- **Siffrorna är inte hela bilden.** De säger inget om belastning, och de 8 blockerade testerna och 10 ej körda testerna är inte verifierade.

---

## 5. Defekter

| Severity | Totalt | Kvarstående | Rättade/stängda |
|---|---|---|---|
| Critical | 2 | **0** | 2 |
| High | 9 | **4** | 5 |
| Medium | 17 | 6 | 11 |
| Low | 12 | 7 | 5 |
| **Totalt** | **40** | **17** | **23** |

**De viktigaste felen**

1. **Critical: betalning kunde genomföras utan att order skapades.** Kunden kunde debiteras utan beställning. Status: rättad → retestad → Passed.
2. **Critical: dubbel debitering.** Kunden kunde debiteras två gånger. Status: rättad → retestad → regression Passed.
3. **High (4 kvarstår):** den viktigaste gäller ett ovanligt refundscenario. Manuell workaround finns och verksamheten har accepterat risken.

**Tolkning:** de allvarligaste felen (Critical) är åtgärdade och verifierade. De kvarstående felen är främst Medium och Low (13 av 17), och de fyra High-defekterna har workarounds. **[KONTROLLERA: bekräfta att alla fyra har dokumenterad workaround, underlaget nämner det bara för den viktigaste.]**

---

## 6. Avvikelser från plan

| # | Avvikelse | Konsekvens | Påverkan på resultatet |
|---|---|---|---|
| 1 | Payment Provider SYS var otillgänglig en dag | Betalningstester försenades | Mindre tid för betalning och retest, vilket är ett högriskområde |
| 2 | En testare var sjuk i tre dagar | Vissa lågprioriterade tester omplanerades | Troligen en del av de 10 ej körda testerna |
| 3 | Testdata saknades för vissa refundscenarier | 8 tester blockerades | Refund är inte fullt verifierad |
| 4 | Full regression kunde inte genomföras | 95 % genomfördes med riskbaserad prioritering | 5 % ej körd, vilket är en kvarstående risk |

---

## 7. Risker

Risker som identifierades under testarbetet:

| Risk | Hur den påverkade testningen |
|---|---|
| Payment Provider SYS otillgänglig | **Inträffade.** Betalningstester försenades en dag. |
| Resursbortfall (sjukdom) | **Inträffade.** Lågprioriterade tester omplanerades. |
| Saknad testdata för refund | **Inträffade.** 8 tester blockerades. |
| Tidsbrist för full regression | **Inträffade.** 95 % genomfördes med riskbaserad prioritering. |
| SYS skiljer sig från Payment Providers produktionsmiljö | **Kvarstår.** Fel kan visa sig först i produktion. |
| Belastningsproblem | **Kvarstår.** Inget fullständigt belastningstest. |

---

## 8. Kvarstående risk

| # | Risk | Orsak | Konsekvens | Risknivå | Åtgärd |
|---|---|---|---|---|---|
| 1 | **Refundscenarier inte fullt verifierade** (8 blockerade tester) | Saknad testdata | Fel eller utebliven återbetalning till kund, tillsammans med den kända High-defekten | **Hög** | Skaffa testdata och kör testerna om möjligt före release, manuell refundprocess och daglig avstämning, övervakning |
| 2 | **Fyra High-defekter är öppna** | Hann inte rättas | Fel i refund och andra funktioner. Hanteras med workarounds | **Medel** | Dokumenterade workarounds, supportinstruktion, rättning i nästa release |
| 3 | **Fullständigt belastningstest genomfördes inte** | Utanför scope | Långsamt eller nere vid hög trafik | **Medel** (Hög om hög trafik väntas) | Övervakning av belastning de första dagarna, möjlighet att skala upp, belastningstest efter release |
| 4 | **SYS skiljer sig från Payment Providers produktionsmiljö** | Testmiljön är inte identisk | Betalningsfel som bara syns i produktion | **Medel** | Smoke test med betalning direkt efter driftsättning, monitorering, rollback |
| 5 | **5 % av regressionen ej körd** | Tidsbrist, riskbaserat urval | Fel i ej testade oförändrade områden | **Låg** | Prioriterade områden är körda, körs efter release om tid finns |

---

## 9. Slutsats

Testningen visar att NordicShop Release 4.0 är stabil i de kritiska flödena. Alla P1-tester och alla tre kritiska E2E-flöden är godkända, båda Critical-defekterna är åtgärdade och verifierade, och UAT är godkänd. Tekniskt är releasen redo, med verifierad rollback, aktiv monitorering och supportberedskap.

Kvarstående risk är koncentrerad till **refund** (blockerade tester och en känd High-defekt) och till det som inte testats (belastning och 5 % av regressionen). Dessutom skiljer sig SYS något från Payment Providers produktionsmiljö, så betalningsfel kan visa sig först i produktion. De riskerna är kända, dokumenterade och accepterade av verksamheten, men refund är det område som bör följas noggrant.

Kvaliteten är alltså god nog för release **om riskerna hanteras**, men inte riskfri.

---

## 10. Rekommendation

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
