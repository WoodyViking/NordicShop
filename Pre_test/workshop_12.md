# Workshop – 200 regressionstester, men tid för 70

## Scenario

NordicShop ska släppa Release 4.0 om två dagar.

- Regressionstestpaketet innehåller **200 tester**.
- Tiden räcker endast till **70 tester**.
- Vi måste skapa ett riskbaserat regression scope.

**Release 4.0 innehåller:**

- nytt checkout-flöde
- ny Swishintegration
- ändringar i Order Service
- rättning av flera refund-defekter
- mindre förändringar i kundprofil
- textändringar på produktsidor

**Historiskt har flest produktionsproblem funnits inom:** betalning, order, lager och refund.

---

## Uppgift 1 – Gör en Impact Analysis

### Vad har förändrats direkt?

- Checkout (nytt flöde)
- Betalning (ny Swishintegration)
- Order Service
- Refund (rättning av flera defekter)
- Kundprofil (mindre förändringar)
- Produktinformation (textändringar)

### Vad kan påverkas indirekt?

| Indirekt påverkan | Varför |
|---|---|
| Kundvagn | Leder in i det nya checkout-flödet. |
| Lager | Order Service uppdaterar lagersaldot vid köp och avbeställning. |
| Leverans | Leveransvalet görs i checkout. |
| Orderbekräftelse (e-post/SMS) | Skickas från Order Service efter betalning. |
| Avbeställning | Hänger ihop med refund och orderstatus. |
| Login | Köp och kundprofil kräver inloggning, och adressen i profilen används i checkout. |

### Vilka integrationer berörs?

- **Payment Provider:** ny Swishintegration, kort och refund.
- **Inventory System:** via Order Service (saldo vid köp och avbeställning).
- **Delivery Provider:** leveransval i det nya checkout-flödet.
- **Email/SMS Service:** orderbekräftelser och avbeställningsbekräftelser.
- **Kunddatabas:** kundprofilens förändringar.

### Vilka kritiska E2E-flöden påverkas?

| E2E-flöde | Påverkas? | Av vad? |
|---|---|---|
| Köpflöde inklusive betalning | **Ja, direkt** | Nytt checkout, Swish, Order Service |
| Avbeställning och återbetalning | **Ja, direkt** | Refund-rättningar, Order Service |
| Sista produkten i lager | **Ja, indirekt** | Order Service uppdaterar lagersaldot |

### Påverkan per område

| Område | Påverkan | Motivering |
|---|---|---|
| Betalning | **Hög** | Ny Swishintegration, direkt förändring och historiskt problemområde. Fel kostar kunden pengar. |
| Checkout | **Hög** | Helt nytt flöde. |
| Order | **Hög** | Ändringar i Order Service och historiskt problemområde. |
| Refund/avbeställning | **Hög** | Flera rättningar och historiskt problemområde. Gäller kundens pengar. |
| Lager | **Hög** | Indirekt påverkan via Order Service. Historiskt problemområde och det gamla lagersystemet är en stor teknisk risk. |
| Kundvagn | **Medel** | Direkt anslutning till checkout, men oförändrad kod. |
| Leverans | **Medel** | Valet görs i checkout, men själva leveransfunktionen är oförändrad. |
| Kundprofil | **Medel** | Direkt men mindre förändring. Låg affärsrisk, men adressen används i checkout. |
| Login och konto | **Låg** | Oförändrat. Testas ändå indirekt i alla E2E-flöden. |
| Produktsökning | **Låg** | Oförändrat. |
| Produktinformation | **Låg** | Endast textändringar. |
| UI/text | **Låg** | Ingen funktionell förändring. |

---

## Uppgift 2 – Välj 70 tester

| Område | Totalt | Valda | Andel valda |
|---|---|---|---|
| Login och konto | 15 | **2** | 13 % |
| Produktsökning | 15 | **1** | 7 % |
| Produktinformation | 15 | **2** | 13 % |
| Kundvagn | 20 | **5** | 25 % |
| Checkout | 25 | **11** | 44 % |
| Betalning | 30 | **14** | 47 % |
| Order | 25 | **11** | 44 % |
| Lager | 15 | **8** | 53 % |
| Leverans | 10 | **3** | 30 % |
| Refund | 15 | **9** | 60 % |
| Kundprofil | 10 | **3** | 30 % |
| UI/text | 5 | **1** | 20 % |
| **Totalt** | **200** | **70** | 35 % |

### Motivering av de större prioriteringarna

**Hög påverkan: 53 av 70 tester (76 %)**

- **Betalning, 14 tester.** Största delen av testerna eftersom både ny Swishintegration och historiska problem finns här. Fokus på Swish (godkänd, nekad, avbruten, timeout), regression av kortbetalning, avbruten betalning ger ingen order, dubbeldebitering och callbacks.
- **Checkout, 11 tester.** Helt nytt flöde. Täcker alla steg från kundvagn till bekräftelse, leveransval, rabattkod i checkout och felvägar.
- **Order, 11 tester.** Order Service har ändrats. Täcker orderskapande, statusar, order efter misslyckad betalning och orderbekräftelse.
- **Refund, 9 tester (60 %, högst andel).** Området har både rättade defekter och historiska problem. Täcker hela avbeställnings- och återbetalningsflödet, att orderstatus uppdateras och att lagersaldot återställs, samt retest av de rättade defekterna.
- **Lager, 8 tester.** Lager är inte direkt ändrat, men Order Service uppdaterar det. Täcker saldo vid köp och avbeställning, saldo 0 och 1 (sista produkten) och fel från lagersystemet.

**Medel påverkan: 11 av 70 tester**

- **Kundvagn, 5 tester.** Kundvagnen leder in i checkout och testas dessutom i varje E2E-flöde. Vi tar de viktigaste flödena (lägg till, ta bort, ändra antal, produkt slut).
- **Leverans, 3 tester.** Hemleverans, ombud och en felvariant i checkout.
- **Kundprofil, 3 tester.** Ändra telefon, adress och preferenser (varje ändring får ett test).

**Låg påverkan: 6 av 70 tester**

- **Login och konto, 2 tester.** Inloggning och kontolåsning (säkerhet). Login används ändå i alla E2E-flöden.
- **Produktsökning, 1 test.** Smoke test av att sökning ger träffar.
- **Produktinformation, 2 tester.** Visuell kontroll av de ändrade texterna och att pris visas rätt.
- **UI/text, 1 test.** Kort kontroll av att sidorna visas.

### Hur väljer vi vilka tester inom varje område?

1. Tester som täcker **ändrad kod** och de tre E2E-flödena.
2. Tester som **hittat fel historiskt**.
3. Tester som är **automatiserade** (snabbast att köra).
4. Tester för **felvägar** (nekad, avbruten, timeout) före fler varianter av samma lyckade flöde.

---

## Kvarstående risker (130 tester körs inte)

| Ej testat | Risk |
|---|---|
| 13 av 15 login-tester, 14 av 15 sök-tester | Fel i oförändrade områden kan finnas kvar, men sannolikheten är låg. |
| 15 av 20 kundvagnstester | Fel i sällsynta kundvagnsvarianter kan nå produktion. |
| Fler varianter i betalning (16 tester) och checkout (14 tester) | Ovanliga betalningsfall eller kombinationer i checkout kan ge fel. |
| Fler varianter i order (14 tester) och lager (7 tester) | Sällsynta statusövergångar eller lagerfel kan missas. |
| UI/text, produktinformation | Kosmetiska fel kan nå kunderna. |

**Åtgärder:** förstärkt övervakning av betalning, order och lager de första dagarna efter release, möjlighet att snabbt återgå till föregående version (rollback), och att resterande tester körs efter releasen om tid finns.
