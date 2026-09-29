## Steg 1 – Prioritera testobjekten

Kategorisera NordicShops områden som:

### MUST TEST

Måste testas före release.

### SHOULD TEST

Bör testas om tid finns.

### COULD TEST

Kan reduceras eller flyttas.

Använd följande tabell:

| Område | Prioritet | Motivering |
| --- | --- | --- |
|  | Must/Should/Could |  |
| Inloggning och utloggning | Must | Är säkerthetsrisk om det går att bruteforca systemet. |
| Kundvagn köpflöde | Must | Utan fungerande köpflödet fungerar inget. |
| Lagersaldo | Must | Måste fungera för att affärsflödet ska kunna fungera. |
| Order service | Must | Är viktigt för att företaget ska kunna ha kol på kundens beställningar och påverkar hela affärs flödet |
| Betallning | Must | Måste fungera för att försäljning ska fungera och kostar pengar om det inte fungerar. |
| Avbeställning | Must | Kund blir påverkad, men kund kan kontakta oss för att ändra manuellt. |
| Behörighet (kundservice och administratör)| Should | Säkerhetsrelevant, men inte lika hög risk som betallning. |
| Leverans | Could | Påverkar kundupplevelse men stopar inte som ett betalningsfel. |
| Orderbekräftelse | Should | Viktigt för förtroende, men kan göras manuellt. |
| Rabattkod | Could | Det är inget som är affärskrittiskt och kund kan återbetallas om något går fel. |
| Administrationsvertyg | Must | Utan administration kan inte kunden få hjälp när saker går fel. |
| Grundläggande sök| Could | Det ska gå att hitta varor utan att behöva sökverktyget så påverkar användare men behövs inte för kundflödet. |
| UI/UX-utseende | Could | Inte viktigt att hemsidan har ett perfekt utseende och har redan låg priritet i från testanalysen. |

---

# Steg 2 – Kritiska affärsflöden

Identifiera vilka **tre E2E-flöden** ni absolut inte skulle vilja gå live utan att verifiera.
## Köpflöde
Det viktigaste för att affärsflödet ska fungera, utan köpflöde så fungerar inte butiken och NordicShop tjänar inga pengar.

## Avbeställning och återbetalning
Om kunden ändrat sig så måste det gå för kunden att ändra sin beställning annars blir kunden riktigt arg.

## Slutsåld produkt och lager
Att kunden förlorar förtroende om det inte finns produkten de försöker köpa i affären eller inte kan köpa en produkt som affären tror fins tillgängligt.
Motivera.

---

# Steg 3 – Regression

## Behövs
- Köpflödet
- Betalning
- Order service
- Avbeställning och återbetalning
- Inloggning och behörigheter

## Reducerad regression
- Rabattkod
- Leverans

## Kan utgå
- Sökfunktioner
- UI/UX-utseende och layout
- Regression i älde webläsare och enheter

---

# Steg 4 – Testnivåer

Analysera om samtliga planerade testnivåer fortfarande ska genomföras.

Får någon nivå:

- reducerad omfattning?
- ändrad prioritering?

| Testnivå | Förändring | Motivering |
| --- | --- | --- |
| E2E | Hög pritritering | Happy path för kundflödet måste funka och säkerhet |
| Integrationer |  ||
| Enhetstest |||


---

# Steg 5 – Testtyper

Ta ställning till:


## Vad måste behållas?
Funktionell testning är viktig eftersom happy path måste testas för att se till att produkten fungerar.
Säkerhet viktigt för att allt som är viktigt kan påverkas om säkerheten falleras.
## Vad kan reduceras?
Prestanda är endast viktigt att systemet snurrar och att det inte påverkar säkerheten om det går för dåligt
Kompatibilitet är viktigt men kan minskas till dem webbläsare/enheter som flesta av användare använder.
Använbarhet är inte lika viktigt att det finns i produktion.

---

# Steg 6 – Out of Scope

Identifiera vad som nu aktivt tas bort eller reduceras från testomfattningen.

Det ska vara tydligt dokumenterat.
Det vi tar bort är UI/UX-utseende som inte är viktigt för systemets funktion.
Webbläsare som inte är så använda av dem flest användare behöver inte testas.
Sökfunktioner är inte viktiga systemets funktion och kan göras efter systemet är färdigt.

---

# Steg 7 – Kvarstående risk

Identifiera minst **5 risker** som uppstår på grund av den reducerade testomfattningen.

Exempel:


| Reducerad testning | Kvarstående risk |
|---|---|
|  Rabattkoder testas inte före release | En kod kan användas flera gånger, ge fel belopp eller fungera trots att den har gått ut. Det ger ekonomisk förlust. Kunder som inte får utlovad rabatt kontaktar kundservice. |
| Begränsat prestandatest | Plattformen kan bli långsam eller gå ner vid en kampanj med oväntat hög trafik. |
| Äldre webbläsare och enheter testas inte | Vissa kunder kan inte slutföra köp, vilket ger fler avbrutna köp. |
| Kortare acceptanstest | Kundservice kan upptäcka problem i sitt arbetsflöde först efter release, vilket ger mer manuellt arbete. |
| Reducerad regression | En sen buggfix kan förstöra något i ett område vi inte testar om. |
| Leverans testas bara i standardfallet | Fel pris eller saknade alternativ för ombud kan leda till missnöjda kunder. |
| Fördjupad tillgänglighetstest tas bort | Risk att lagkraven på tillgänglighet inte uppfylls. |

Åtgärder för att minska risken: förstärkt övervakning efter release, en beredskapsgrupp de första dagarna, möjlighet att snabbt stänga av rabattkoder och en tydlig rollback-plan.


---

# Steg 8 – Kommunicera till projektledaren

Formulera en kort testledarrapport på max **5–7 meningar**.

Den ska beskriva:

Nu när vi har mindre tid för att testa, så har vi behövt reducera och prioritera för att systemet forfarande ska kunna upnå viktiga happy path 
Vi har ändrat prioriteringen för att se till att dem kritiska flödena kan fungera (happypath)
Vi har reducerat testandet utav utseendet av hemsidan, prestandan duger med att köra personbil för hemsidan och olika enheter/webläsare kan reduceras till dem viktiga som dem fleta användare använder.
Risker blir att kunder inte vill stanna på en långsam eller en icke användar vänlig (sökfunktioner, kronglig UI/UX) hemsida.
En rekomendation är AI för verifiering utav test/kod så vi kan fokusera på validering.
