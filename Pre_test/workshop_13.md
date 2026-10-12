# Workshop – Testuppföljning för NordicShop

## Scenario

Vi befinner oss mitt i den två veckor långa testperioden för NordicShop Release 4.0.

- Totalt finns **200 planerade tester**.
- Enligt plan skulle **150 tester** vara genomförda vid dagens slut.

**Aktuell status**

| Status | Antal |
|---|---|
| Planned totalt | 200 |
| Planned till idag | 150 |
| Executed | 120 |
| Passed | 90 |
| Failed | 20 |
| Blocked | 10 |
| Not Run totalt | 80 |

**Defektstatus**

| Severity | Öppna |
|---|---|
| Critical | 1 |
| High | 4 |
| Medium | 9 |
| Low | 12 |

- **Critical:** betalning genomförs men order skapas ibland inte.
- **High (bland annat):** refund återställer inte alltid lager, Swish timeout hanteras felaktigt, kundservice kan komma åt en funktion som rollen inte ska ha.

---

## Uppgift 1 – Progress

**1. Hur många tester ligger projektet efter planen?**

150 − 120 = **30 tester efter planen**. Det är 20 % av de tester som skulle vara klara idag.

**2. Hur stor del av samtliga 200 tester har genomförts?**

120 / 200 = **60 %**. Mot dagens plan är det 120 / 150 = 80 %.

**3. Är testningen "on track"?**

**Nej.** Vi ligger 30 tester efter, och Failed (20) och Blocked (10) innebär att många av de genomförda testerna inte är färdiga utan kräver rättning och omtest. Det är dessutom 80 tester kvar. Takten behöver öka, eller så behöver omfattningen minskas.

Ett viktigt förbehåll: i siffrorna räknas Blocked (10) som genomförda (90 + 20 + 10 = 120). Ett blockerat test har egentligen inte körts klart, så i praktiken är det 110 tester som gett ett resultat, vilket är 55 % av alla 200.

**4. Vilken ytterligare information behöver vi innan vi kan svara säkert?**

- Hur många testdagar som är kvar och hur många tester vi hinner per dag (takten hittills).
- Vilka av de 80 ej körda testerna som är kritiska och inom vilka områden de ligger.
- Varför de 10 testerna är blockerade och när blockaden försvinner.
- När rättningar och nya builds kommer, och hur mycket omtest och regression som krävs.
- Hur många testare som finns tillgängliga resten av perioden.
- Om det finns utvecklare som kan hoppa över till testning.

---

## Uppgift 2 – Testresultat

| Status | Antal | Andel |
|---|---|---|
| Passed | 90 | 75 % av genomförda (90 / 120), 45 % av alla 200 |
| Failed | 20 | 16,7 % av genomförda, 10 % av alla |
| Blocked | 10 | 8,3 % av genomförda, 5 % av alla |
| Not Run | 80 | 40 % av alla 200 |

**Vilken siffra oroar mest, och varför?**

**Not Run (80)** oroar oss mest. Det finns 80 tester (40 %) som är okörda. Det är den största mängden, och vi vet ingenting om hur de ser ut. Den som inte är körd kan dölja fler fel, särskilt om de ligger i betalning, order eller refund, där flest produktionsproblem funnits historiskt.

Näst mest oroar **Failed (20) tillsammans med Blocked (10)**. Det är viktigt att veta om de är kritiska och hur snabbt de blockerade kan åtgärdas så att testning kan påbörjas på dem.

Passed på 75 % ser acceptabelt ut, men siffran säger lite när 40 % av testerna inte körts och det finns kritiska problem.

---

## Uppgift 3 – 100 % Passed

Projektledaren säger: *"Om vi bara kör om testerna efter fixarna och får 100 % Passed borde vi kunna gå live."*

**Varför är resonemanget problematiskt?**

1. **De 80 testerna som inte körts säger ingenting.** Om vi bara kör om de felande testerna blir de 100 % Passed, men 40 % av paketet är fortfarande okänt. Passed mäter bara det som körts.
2. **Fixar kan förstöra något annat (regression).** Ett omtest visar att just det felet är rättat, inte att rättningen inte har skadat något annat. Särskilt riskabelt i order, lager och betalning, som hänger ihop.
3. **Testfallen täcker inte allt.** Ett test som passerar visar bara att det som testas fungerar. Defekter hittas ofta av scenarier som ingen skrivit test för. 100 % Passed betyder inte "inga fel".
4. **Öppna defekter och blockerade tester räknas inte i procenten.** Med 1 Critical och 4 High-defekter och 10 blockerade tester kan Passed-andelen se bra ut samtidigt som risken är hög. Reopen-risken finns också: rättningar fungerar inte alltid första gången.
5. **Tiden och risken.** Rättning, omtest och regression ryms kanske inte före releasen. Ett Go/No-Go ska bygga på risk (kvarstående defekter, coverage och påverkan) och inte bara på en siffra.
6. **Siffran går att påverka.** Om fokus ligger på 100 % Passed finns risken att testfall ändras, tas bort eller att man kör de enkla först. Då mäter siffran något annat än kvalitet.

**Slutsats:** 100 % Passed är ett nödvändigt men inte tillräckligt villkor. Vi behöver även täckning av de kritiska flödena, inga öppna Critical/High-defekter (eller godkända workarounds), verifierade höga risker och regression.
