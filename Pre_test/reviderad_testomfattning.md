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
| Avbeställning | Could | Kund blir påverkad, men kund kan kontakta oss för att ändra manuellt. |
| Behörighet (kundservice och administratör)| Should | Säkerhetsrelevant, men inte lika hög risk som betallning. |
| Leverans | Could | Påverkar kundupplevelse men stopar inte som ett betalningsfel. |
| Orderbekräftelse | Should | Viktigt för förtroende, men kan göras manuellt. |
| Rabattkod | Could | Det är inget som är affärskrittiskt och kund kan återbetallas om något går fel. |
| Administrationsvertyg | Could | Inte så många användare och påverkar inte kund. |
| Grundläggande sök| Could | Det ska gå att hitta varor utan att behöva sökverktyget så påverkar användare men behövs inte för kundflödet. |
| UI/UX-utseende | Could | Inte viktigt att hemsidan har ett perfekt utseende och har redan låg priritet i från testanalysen. |

---

# Steg 2 – Kritiska affärsflöden

Identifiera vilka **tre E2E-flöden** ni absolut inte skulle vilja gå live utan att verifiera.

Motivera.

---

# Steg 3 – Regression

Bestäm:

- vad som måste regressionstestas
- vad som kan få reducerad regression
- vad som eventuellt kan utgå

---

# Steg 4 – Testnivåer

Analysera om samtliga planerade testnivåer fortfarande ska genomföras.

Får någon nivå:

- reducerad omfattning?
- ändrad prioritering?

Motivera.

---

# Steg 5 – Testtyper

Ta ställning till:

- funktionell testning
- säkerhet
- prestanda
- kompatibilitet
- användbarhet

Vad måste behållas?

Vad kan reduceras?

---

# Steg 6 – Out of Scope

Identifiera vad som nu aktivt tas bort eller reduceras från testomfattningen.

Det ska vara tydligt dokumenterat.

---

# Steg 7 – Kvarstående risk

Identifiera minst **5 risker** som uppstår på grund av den reducerade testomfattningen.

Exempel:

| Reducerad testning | Kvarstående risk |
| --- | --- |
|  |  |
|  |  |

---

# Steg 8 – Kommunicera till projektledaren

Formulera en kort testledarrapport på max **5–7 meningar**.

Den ska beskriva:

- vad som har förändrats
- vad ni prioriterar
- vad ni reducerar
- vilka risker detta innebär
- eventuell rekommendation
