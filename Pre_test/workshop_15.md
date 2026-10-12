# Workshop – Samma testresultat, tre olika statusrapporter

## Scenario – NordicShop Release 4.0

Det är torsdag eftermiddag under sista testveckan. Go/No-Go är planerat till fredag kl. 15.00.

## Rådata (sammanfattning)

**Test Execution**

| Metric | Resultat |
|---|---|
| Planerade tester | 250 |
| Executed | 220 |
| Passed | 190 |
| Failed | 18 |
| Blocked | 12 |
| Not Run | 30 |
| Test Execution | 88 % |
| Pass Rate | 86,4 % |

**Defekter:** 10 öppna: Critical 1, High 2, Medium 5, Low 2.

**Critical-defekt:** betalning kan genomföras utan att order skapas. Utveckling arbetar med fix. Ny build väntas fredag kl. 09.00.

**Coverage**
- Fullt verifierade: login, kundvagn, checkout, lager, leverans, kundprofil.
- Delvis verifierade: betalning, order, refund.
- Blocked: 7 betalnings-/ordertester och 5 refundtester.

**Risk coverage**
- Verifierade höga risker: dubbel debitering, felaktigt lagersaldo, felaktig behörighet, Swish timeout.
- Ännu inte fullständigt verifierade: betalning utan order, dubbel refund.

---

## Rapport 1 – Till testteamet

**Mottagare:** testare, utvecklare och testledare.

> Testfalls-ID och defekt-ID finns inte i rådatan. ID:na nedan är exempel och ersätts med de riktiga från testverktyget.

### Läget just nu (torsdag)

- 220 av 250 genomförda (88 %), 190 Passed, 18 Failed, 12 Blocked, 30 Not Run.
- 10 öppna defekter: **1 Critical** (betalning kan genomföras utan att order skapas, **DEF-301**), 2 High (**DEF-287**, **DEF-295**), 5 Medium, 2 Low.
- Ny build med fix för Critical-defekten väntas **fredag kl. 09.00**.

### Failed och Blocked

| Område | Antal | Läge | Åtgärd |
|---|---|---|---|
| Betalning/order | 7 Blocked (**TC-PAY-021 – TC-PAY-027**) | Blockerade. Orsaken ska bekräftas, troligen DEF-301 | Kör direkt efter att den nya builden är godkänd |
| Refund | 5 Blocked (**TC-REF-011 – TC-REF-015**) | Blockerade | Kör efter betalning/order, eftersom återbetalning bygger på fungerande betalning |
| Alla områden | 18 Failed (till exempel **TC-CHK-008**, **TC-ORD-017**) | Kopplade till de öppna defekterna, bland annat **DEF-287** och **DEF-295** | Retest efter respektive fix. Failed utan defekt-ID ska få ett ID idag |

### Verifiering som saknas

- **Betalning utan order:** ska verifieras med den nya builden (kort, Swish, avbruten betalning, timeout).
- **Dubbel refund:** inte verifierad, och ska testas efter att refund-testerna har körts.

### Vem gör vad

| Roll | Uppgift |
|---|---|
| Testledare | Samlar status, avgör ordningen och rapporterar till projektledningen |
| Utvecklare | Levererar build 09.00, bekräftar vilka defekter som är rättade och meddelar direkt om det blir sent |
| Testare 1 (betalning/order) | Smoke test och retest av Critical-defekten, därefter de 7 blockerade testerna |
| Testare 2 (refund) | Kör de 5 blockerade refundtesterna, därefter "dubbel refund" |
| Testare 3 (regression) | Regression på checkout, order och lager efter fixen |
| Alla | Uppdaterar testverktyget löpande |

### Fredag morgon

| Tid | Aktivitet |
|---|---|
| 08.30 | Kort avstämning med utveckling: tid för build, vilka defekter som ingår |
| 09.00 | Build deployas. **Smoke test:** rätt version, tjänsterna svarar, ett minimalt köp ger en order |
| 09.15 | **Retest av Critical-defekten:** betalning ger alltid en order (kort, Swish, avbruten betalning, timeout) |
| 10.00 | Kör de **7 blockerade betalnings-/ordertesterna** |
| 11.00 | Kör de **5 blockerade refundtesterna** och verifiera **dubbel refund** |
| 12.30 | Retest av **High-defekterna** om de är rättade, och regression på checkout, order och lager |
| 13.30 | Sammanställ resultat och uppdatera defektlistan |
| 14.00 | Status till projektledningen inför Go/No-Go |
| 15.00 | Go/No-Go |

### Prioritering
1. Critical-defekten och de blockerade testerna för betalning/order.
2. Refund (blockerade tester och dubbel refund).
3. Retest av High-defekterna.
4. Regression kring det som ändrats.
5. De 30 ej körda testerna, i den ordning kritiska flöden kommer först. De som inte hinns dokumenteras som kvarstående risk.

**Vad teamet behöver veta:** i morgon fram till 15.00 handlar allt om att få betalning → order och refund verifierade. Meddela direkt om builden är försenad eller om retest fallerar.

---

## Rapport 2 – Till projektledningen

**Mottagare:** projektledare, Product Owner och Release Manager.

**Status: 🔴 RÖD tills den kritiska defekten är rättad och verifierad.**

**Progress mot plan**
88 % av planerade tester är genomförda (220 av 250) och 86,4 % av dem har passerat. 30 tester är inte körda och 12 är blockerade. Sex områden är fullt verifierade (login, kundvagn, checkout, lager, leverans, kundprofil), medan betalning, order och refund är delvis verifierade.

**Viktiga avvikelser**
- **Critical-defekt:** betalning kan genomföras utan att order skapas. Kunden kan debiteras utan beställning.
- **2 High-defekter** är öppna.
- **12 blockerade tester ligger i kritiska flöden:** 7 betalning/order och 5 refund.
- **Ej verifierade höga risker:** betalning utan order och dubbel refund.

**Påverkan på tidplanen**
Ny build väntas fredag kl. 09.00. Det lämnar ungefär sex timmar till Go/No-Go kl. 15.00 för smoke test, retest av Critical, de 12 blockerade testerna, verifiering av dubbel refund och regression. Tidplanen är därmed mycket tight. Blir builden försenad hinns inte allt.

**Release-risk**
**Hög** i nuläget. Releasen går inte att rekommendera förrän betalning → order och refund är verifierade.

**Planerade åtgärder**
Retest av Critical direkt efter builden, därefter blockerade tester och dubbel refund, och regression på de berörda flödena. Testledaren rapporterar läget kl. 12.00 och 14.00.

**Före Go/No-Go måste följande vara klart**

| # | Krav |
|---|---|
| 1 | Ny build levererad och godkänd i smoke test |
| 2 | Critical-defekten verifierad som rättad (betalning ger alltid en order) |
| 3 | 12 blockerade tester körda och utan kritiska fel |
| 4 | Dubbel refund verifierad |
| 5 | 2 High-defekter rättade eller godkända med workaround |
| 6 | De ej körda testerna dokumenterade som kvarstående risk |

**Beslut vi behöver från er**
- Bekräftelse från utveckling att builden kommer kl. 09.00.
- Vad vi gör om builden blir sen eller Critical-defekten inte är rättad: **vi rekommenderar att releasen då skjuts upp**. Vi föreslår en tidsgräns: om builden inte är levererad och godkänd i smoke test senast kl. 11.00 skjuts releasen upp, eftersom det annars inte finns tid att verifiera betalning och refund före kl. 15.00.

---

## Rapport 3 – Till styrgrupp/verksamhet (max 5 meningar)

Testningen är i huvudsak klar, men det finns en allvarlig kvarstående risk: betalning kan i dag gå igenom utan att kunden får en order, vilket kan ge debiterade kunder utan beställning, förlorat förtroende och ekonomiska förluster. En rättning levereras i morgon bitti och måste verifieras tillsammans med återbetalningsflödet, som ännu inte är fullständigt testat. I nuläget är releasen inte redo, men den kan bli det om verifieringen lyckas före beslutsmötet kl. 15.00. Om kontrollerna inte hinner slutföras eller något kritiskt fel kvarstår är risken för kunder och ekonomi större än värdet av att släppa på planerad dag. Vi rekommenderar därför att beslutet fattas i morgon på det färska testresultatet, och att releasen skjuts upp om betalning och återbetalning inte är verifierade.

---

## Jämförelse av de tre rapporterna

| | Testteamet | Projektledningen | Styrgrupp/verksamhet |
|---|---|---|---|
| **Fokus** | Vad ska göras, av vem och när | Läge, risk och vad som krävs före Go/No-Go | Beslut och affärskonsekvens |
| **Detaljnivå** | Testfalls-ID, defekt-ID, tider | Siffror och flöden, utan testfall | Inga siffror, inga ID |
| **Språk** | Tekniskt | Projektspråk | Affärsspråk |
| **Slutsats** | Hur vi arbetar fredag morgon | Vad som måste vara klart och vilket beslut som behövs | Rekommendation: skjut upp om risken kvarstår |
