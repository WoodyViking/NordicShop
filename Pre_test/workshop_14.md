# Workshop – Från rå testdata till teststatus

## Scenario

Vi är testledare för NordicShop Release 4.0. Det är torsdag under sista testveckan och Go/No-Go är planerat till fredag eftermiddag.

Projektledaren frågar: *"Hur ser kvaliteten ut och är vi redo för release?"*

## Rådata (sammanfattning)

**Test Execution:** 250 planerade, 220 genomförda

| Status | Antal |
|---|---|
| Passed | 190 |
| Failed | 18 |
| Blocked | 12 |
| Not Run | 30 |

**Testområden**

| Område | Planerade | Genomförda |
|---|---|---|
| Login | 20 | 20 |
| Kundvagn | 25 | 25 |
| Checkout | 40 | 38 |
| Betalning | 45 | 42 |
| Order | 35 | 33 |
| Lager | 25 | 23 |
| Refund | 25 | 14 |
| Leverans | 15 | 15 |
| Kundprofil | 10 | 10 |
| Regression övrigt | 10 | 0 |
| **Totalt** | **250** | **220** |

**Defekter:** 64 rapporterade. Closed 48, Ready for Retest 6, Open 10

| Severity | Antal |
|---|---|
| Critical | 0 |
| High | 3 |
| Medium | 5 |
| Low | 2 |

**Defect trend**

| Dag | Nya | Stängda |
|---|---|---|
| Mån | 12 | 5 |
| Tis | 9 | 7 |
| Ons | 5 | 10 |
| Tors | 3 | 8 |

**Reopen:** av de 48 stängda har 7 öppnats igen.

**Risk coverage:**

| Risk | Status |
|---|---|
| Dubbel debitering | Verifierad – Passed |
| Betalning utan order | Verifierad – Passed efter fix |
| Felaktigt lagersaldo | Verifierad – Passed |
| Refund misslyckas | Delvis verifierad |
| Felaktig behörighet | Verifierad – Passed |
| Swish timeout | Verifierad – Passed |
| Dubbel refund | Ej verifierad |

**Leakage föregående release:** 72 defekter före produktion, 8 relevanta defekter efter release.

---

## Uppgift 1 – Beräkna KPI:erna

| KPI | Beräkning | Resultat |
|---|---|---|
| **Test Execution %** | 220 / 250 × 100 | **88 %** |
| **Pass Rate** | 190 / 220 × 100 | **86,4 %** |
| **Reopen Rate** | 7 / 48 × 100 | **14,6 %** |
| **Defect Leakage (föregående release)** | 8 / (72 + 8) × 100 = 8 / 80 × 100 | **10 %** |

**Förbehåll:** de 220 genomförda innehåller även de 12 blockerade testerna (190 + 18 + 12 = 220). Ett blockerat test har inte körts klart, så i praktiken har 208 tester gett ett resultat, vilket är 83,2 % av alla 250. Räknat på dem är Pass Rate 190 / 208 = 91,3 %.

---

## Uppgift 2 – Analysera Defect Trend

| Dag | Nya | Stängda | Netto (nya − stängda) |
|---|---|---|---|
| Mån | 12 | 5 | +7 |
| Tis | 9 | 7 | +2 |
| Ons | 5 | 10 | −5 |
| Tors | 3 | 8 | −5 |
| **Summa** | **29** | **30** | **−1** |

**Ökar eller minskar antalet nya defekter?** De minskar tydligt: 12 → 9 → 5 → 3.

**Stänger teamet fler defekter än de hittar?** Ja sedan onsdag (10 mot 5 och 8 mot 3). Totalt under veckan är det i princip jämnt (30 stängda, 29 nya).

**Är trenden positiv eller negativ?** Positiv. Systemet blir stabilare, och testningen hittar allt färre nya fel.

**Räcker informationen för att rekommendera release?** **Nej.** Trenden är bara en del av bilden:
- Nya defekter hittas fortfarande (3 på torsdagen).
- 3 High-defekter är öppna och 6 väntar på retest.
- Reopen Rate är 14,6 %, så stängda defekter är inte alltid rättade.
- Refund är bara 56 % testat och dubbel refund är inte verifierad.
- Regression övrigt (10 tester) är inte körd alls.
- Trenden säger också mindre om det område vi inte testat färdigt, eftersom färre tester ger färre fynd.

---

## Uppgift 3 – Coverage

| Område | Genomförda / planerade | Coverage |
|---|---|---|
| Regression övrigt | 0 / 10 | **0 %** |
| **Refund** | 14 / 25 | **56 %** |
| Lager | 23 / 25 | 92 % |
| Betalning | 42 / 45 | 93,3 % |
| Order | 33 / 35 | 94,3 % |
| Checkout | 38 / 40 | 95 % |
| Login, Kundvagn, Leverans, Kundprofil | alla | 100 % |

**Vilket område har lägst coverage?** Regression övrigt har lägst (0 %), men **Refund (56 %)** är det område som är viktigast att uppmärksamma som mest otestad.

**Är all coverage lika viktig?** Nej. Coverage ska vägas mot risk:
- Refund är ett högriskområde (gäller kundens pengar). Två av riskerna är inte verifierade: "Refund misslyckas" (delvis) och "Dubbel refund" (ingen). Lägst coverage och högst risk i samma område är det som oroar mest.
- Regression övrigt är mindre brådskande om de 10 testerna ligger i oförändrade eller lågrisk-områden, men de behövs för att se att rättningarna inte förstört något.
- 92–95 % i betalning, order, checkout och lager är bra, men de resterande testerna ligger i kritiska områden och bör inte hoppas över.

**Prioritering under den återstående tiden**
1. **Refund:** kör de 11 återstående testerna med fokus på "refund misslyckas" och "dubbel refund".
2. **Retest** av de 6 defekter som väntar (Ready for Retest) och av de 3 öppna High-defekterna när de rättats.
3. **Resterande tester i betalning (3), order (2), checkout (2) och lager (2).**
4. **Regression övrigt:** minst de delar som rör betalning, order och refund.
5. **De 12 blockerade testerna:** När blockeringen är borta kör dem.

---

## Uppgift 4 – Skapa teststatus

### Teststatus NordicShop Release 4.0, torsdag

**Overall Status:** 🟡 **GUL** – avvikelser och risker finns, men de kan hanteras före Go/No-Go om refund slutförs.

**Progress**
88 % av de planerade testerna är genomförda (220 av 250). 30 tester är ej körda: 11 i refund, 10 i regression övrigt och 9 i övriga områden.

**Testresultat**
190 tester har passerat (86,4 % av genomförda), 18 har fallerat och 12 är blockerade.

**Defect Status**
64 defekter har rapporterats, varav 48 är stängda, 6 väntar på retest och 10 är öppna (0 Critical, 3 High, 5 Medium, 2 Low). Trenden är positiv: nya defekter har minskat från 12 till 3 per dag, och fler stängs än hittas sedan onsdag. 7 av 48 stängda defekter har öppnats igen (14,6 %), så rättningarna behöver retestas noga.

**Coverage**
Login, kundvagn, leverans och kundprofil är fullt testade, och checkout, order, betalning och lager ligger på 92–95 %. **Refund är bara 56 % testat** och regression övrigt (10 tester) är inte körd.

**Risk**
De flesta höga riskerna är verifierade: dubbel debitering, betalning utan order (efter fix), lagersaldo, behörighet och Swish timeout. **Kvarstår:** "refund misslyckas" (delvis verifierad) och **"dubbel refund" (ej verifierad)**. Båda gäller kundens pengar. Föregående release hade 10 % leakage.

**Recommendation – före Go/No-Go**
1. Kör färdigt refund (11 tester) och verifiera "dubbel refund" och "refund misslyckas".
2. Retesta de 6 defekterna som väntar och besluta om de 3 öppna High-defekterna (rätta eller godkänd workaround).
3. Kör regression kring betalning, order och refund, och ta bort blockaden på de 12 blockerade testerna.
4. Om refund inte hinner verifieras: lyft det som en känd risk till Go/No-Go med en tydlig åtgärdsplan (till exempel övervakning efter release och en rollback-plan).

**Status går till 🔴 RÖD** om dubbel refund visar sig vara ett fel som inte hinner rättas före Go/No-Go.
