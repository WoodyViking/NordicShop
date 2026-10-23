# Go/No-Go-underlag – MortgageFlow release 1.0

**Underlag till:** Go/No-Go-mötet
**Bygger på:** Testplan TP-MF-2.1, avsnitt 7.2 (slutkriterier)
**Datum:** 2026-10-23
**Författare:** Grupp 2


---

## 1. Exit Criteria

| Slutkriterium (TP 7.2) | Status | Kommentar |
|---|---|---|
| P1-tester genomförda, ≥ 95 % godkända | 🟡 Delvis | 97 % av alla tester genomförda, 91 % godkända. Siffror per P1 behöver redovisas. |
| E2E-flöden utan öppna S1/S2 | 🟡 Uppfyllt* | DEF-112 rättad, E2E passed. *High 1 ligger nära E2E-5 men enligt plan så får E2E-5 strykas om tiden inte räcker. |
| Inga öppna S1/S2 i P1-områden | 🔴 Ej uppfyllt | 0 Critical, men 3 High öppna. |
| Rättade P1-defekter omtestade + regression | 🟡 Delvis | Retest OK. Regression 108 av 120 (90 %). |
| ≥ 80 % av P2 genomförda | 🟢 Troligen | Helheten ligger på 97 % genomförda. |
| UAT godkänt | 🟢 Uppfyllt | Godkänt med accepterade kända avvikelser. |
| Säkerhetstest, inga kritiska säkerhetsfel | 🟢 Uppfyllt | Regionfelet är rättat och regressionstestat. |
| Prestanda verifierad *eller* avvikelse accepterad | 🟡 Delvis | 350 av 500 användare. Kräver formellt accepterad avvikelse. |
| R11 rolländring verifierad (inkl. tidigare roll i logg) | 🔴 Ej uppfyllt | High 2: tidigare roll saknas ibland. |
| Kvarstående risker accepterade av PO och PL | ⏳ Återstår | Ska beslutas på mötet. |

- 🟢 3 uppfyllda (P2, UAT, säkerhetstest)
- 🟡 4 delvis uppfyllda (P1-tester, E2E, retest och regression, prestanda)
- 🔴 2 ej uppfyllda (inga öppna S1/S2 i P1-områden, R11)
- ⏳ 1 som beslutas på mötet (accepterade kvarstående risker)

---

## 2. Testresultat

| | Antal | Andel |
|---|---|---|
| Planerade | 300 | 100 % |
| Genomförda | 290 | 97 % |
| Godkända | 264 | 88%. 91 % av genomförda |
| Failed | 10 | 3 % |
| Blocked | 6 | 2 % |
| Not Run | 10 | 3 % |

**Vad siffrorna betyder:**
- Täckningen är hög, och 26 tester (failed, blocked och not run) har inget godkänt resultat.
- Failed-testerna motsvarar i stort sett de kvarstående defekterna. Inget av dem gäller ett Critical-fel.
- **Datagap:** 264 + 10 + 6 = 280, inte 290. Status saknas för 10 genomförda tester och behöver förklaras innan mötet.

---

## 3. Kvarstående defekter

| Severity | Öppna | Releaseblockerande? |
|---|---|---|
| Critical | 0 | – |
| High | 3 | Se nedan |
| Medium | 8 | Nej, om PO accepterar |
| Low | 11 | Nej |

| Defekt | Fakta | Konsekvens | Blockerande? |
|---|---|---|---|
| **High 1**: timeout mot kreditupplysning | Otydlig status, ingen felaktig bedömning | Manuellt arbete för handläggaren | **Nej**, med rutin och information till handläggarna |
| **High 2**: rolländringslogg | Tidigare roll saknas ibland, ny roll loggas | Spårbarheten brister, vilket bryter mot R11 och kan bli ett revisionsproblem | **Villkorat**: kräver rättning snarast efter release eller kompenserande kontroll |
| **High 3**: dokumentversioner | Äldsta versionen visas ibland fel, originalet finns kvar | Ingen dataförlust, ovanligt scenario | **Nej** |

---

## 4. Regression

- **Genomförd:** 108 av 120 (90 %). **Ej genomförd:** 12 tester (10 %).
- Det som saknas gäller vissa browserkombinationer, ovanliga kombinationer av dokumentformat och lågprioriterade rapporter.
- **Risk:** Låg till medel. Kärnflödena är regressionstestade. Missade fel kommer troligen att drabba ett fåtal användare i perifera scenarier. Dokumentformat hänger ihop med High 3, så det området bör följas upp.

---

## 5. Prestanda

- **Fakta:** Kravet är 500 samtidiga användare. Bara 350 kunde verifieras (inom svarstidskravet) på grund av miljöbegränsningar.
- **Konsekvens:** Vi vet inte hur systemet beter sig mellan 350 och 500 användare.
- **Risk:** Medel. Långsamma svar eller driftstörning vid hög last, till exempel vid månadsskifte eller under migreringen.
- **Påverkan på beslutet:** Detta är det viktigaste skälet till att rekommendationen är villkorad. Slutkriteriet tillåter en *accepterad* avvikelse, så PO och PL måste formellt acceptera risken.

---

## 6. Business Acceptance

- UAT är **godkänt med accepterade kända avvikelser**.
- Det betyder att verksamheten bedömer att systemet stödjer arbetet trots de kända felen. Det är ett starkt argument för GO.
- Godkännandet ersätter inte en teknisk verifiering av prestanda eller R11. Verksamheten bör uttryckligen bekräfta att den känner till High 1–3 och prestandagapet.

---

## 7. Technical Readiness

✅ Produktionsbuild ✅ Deploymentplan ✅ Monitorering ✅ Rollbackplan verifierad ✅ Supportberedskap ✅ Databasbackup verifierad

**Bedömning:** Tekniken är redo. Verifierad rollback och monitorering gör det möjligt att upptäcka och backa om prestandarisken slår in.

---

## 8. Remaining Risk

| # | Risk | Sannolikhet | Påverkan | Hantering |
|---|---|---|---|---|
| 1 | Prestanda över 350 användare inte verifierad | Medel | Hög | Övervaka lasten, stegvis utrullning, rollback redo |
| 2 | Bristande spårbarhet i rolländringslogg (High 2) | Medel | Hög (compliance) | Hotfix och manuell loggning av rolländringar tills vidare |
| 3 | Otydlig status vid timeout (High 1) | Medel | Medel | Handläggarrutin och supportinformation |
| 4 | Ej regressionstestade perifera scenarier (10 %) | Låg | Låg–Medel | Kör resterande regression efter release |
| 5 | 10 tester utan redovisad status | Okänd | Okänd | Utred före mötet |

---

# 9. Rekommendation

> 🟡 **CONDITIONAL GO**: releasen kan gå till produktion före årsskiftet om villkoren i avsnitt 10 är uppfyllda.

Det finns inga kritiska fel kvar, de allvarligaste defekterna (DEF-101, DEF-112 icg regionfelet DEF-124) är rättade och verifierade, verksamheten har godkänt UAT och tekniken är redo. Två saker gör att vi inte kan rekommendera ett rent GO:

1. **Prestanda med 500 användare är inte verifierad**, bara med 350. Konsekvensen är att vi inte vet hur systemet beter sig mellan 350 och 500 användare, med risk för långsamma svar vid hög belastning.
2. **High 2 strider mot slutkriteriet för rolländringar (R11)**, eftersom loggen ibland saknar tidigare roll. Ny roll loggas rätt, men spårbarheten brister, vilket kan bli ett revisionsproblem.

Ett NO-GO bedöms inte vara rimligt De kvarstående felen leder inte till felaktiga kreditbeslut eller exponerade persondata, rollback är verifierad och riskerna går att hantera med villkor. Att skjuta på releasen ger dessutom stora kostnader och påverkar migreringen.

---

# 10. Villkor för CONDITIONAL GO

1. **PO och projektledare accepterar formellt** prestandaavvikelsen och kvarstående High-defekter och dokumenterar vilka UAT-avvikelser som accepterats.
2. **High 2:** en kompenserande kontroll (manuell loggning av tidigare roll) införs från dag 1, och en hotfix planeras med datum, säkerhetsspecialisten godkänner avvikelsen och en hotfix planeras med datum. (Säkerhetsspecialist och utvecklingsteamen, före produktionssättning.)
3. **High 1:** handläggare och support informeras om rutinen vid timeout.
4. **Prestanda:** stegvis utrullning med 350 samtidiga användare första dagarna, sedan förstärkt övervakning med tydliga tröskelvärden för rollback. Lasttest med 500 användare görs så snart en miljö finns.
5. **Resterande 12 regressionstester** och de 10 tester som saknar status körs eller förklaras och P1-flödena bekräftas i Chrome, Edge och Firefox.

**Om villkor 1 eller 2 inte kan uppfyllas blir rekommendationen NO-GO.**
Den ändras också till NO-GO om något av de tester som saknar status eller de ej körda regressionstesterna visar ett P1-fel
