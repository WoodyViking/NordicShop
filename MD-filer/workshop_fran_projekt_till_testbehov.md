# Workshop – Från projekt till testbehov

## Syfte

Ni har precis kommit in i ett nytt projekt som testledare. Projektet ska utveckla och lansera en ny digital tjänst.

Innan ni kan skapa en teststrategi eller testplan behöver ni förstå:

- Vad ska egentligen testas?
- Vilka delar är viktigast?
- Hur hänger systemen ihop?
- Vilka personer och team behöver involveras?
- Vilka risker finns?
- Vilken information saknas?

Målet med workshopen är att träna på att gå från **projektinformation → testanalys → testbehov**.

---

## Case – NordicShop

NordicShop är ett större e-handelsföretag som säljer kläder, elektronik och heminredning. Företaget utvecklar en ny e-handelsplattform som ska ersätta den befintliga lösningen.

### Verksamhetsmål

Den nya plattformen ska:

- göra det enklare för kunder att handla
- minska antalet avbrutna köp
- ge snabbare orderhantering
- automatisera lageruppdateringar
- stödja fler betalningsalternativ
- minska manuellt arbete för kundservice

Plattformen ska lanseras om 4 månader.

---

## Användare

Systemet används av flera olika användargrupper.

### Kund

Kan:

- registrera konto
- logga in
- söka produkter
- lägga produkter i kundvagn
- använda rabattkod
- genomföra köp
- välja leverans
- se sina beställningar
- avbryta order innan den skickats

### Kundservice

Kan:

- söka efter kunder
- se kundens order
- se betalningsstatus
- avbryta order
- initiera återbetalning

### Administratör

Kan:

- administrera produkter
- ändra priser
- skapa rabattkoder
- hantera användarbehörigheter

---

## Systemlandskap

NordicShop består av flera system och externa tjänster.

```
                    ┌──────────────────┐
                    │       KUND       │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    NordicShop    │
                    │ Webb / Mobilapp  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    Backend /     │
                    │  Order Service   │
                    └───┬─────┬─────┬──┘
              ┌─────────┘     │     └─────────┐
              ▼               ▼               ▼
     ┌──────────────┐ ┌──────────────┐ ┌──────────────┐
     │   Payment    │ │  Lagersystem │ │   Delivery   │
     │   Provider   │ │              │ │   Provider   │
     └──────┬───────┘ └──────────────┘ └──────────────┘
            │
            ▼
     ┌──────────────┐
     │     Bank /   │
     │  Kort/Swish  │
     └──────────────┘

                    ┌──────────────────┐
                    │ E-post / SMS     │
                    │ Service          │
                    └──────────────────┘
```

NordicShop äger själva:

- webbplatsen
- mobilappen
- backend
- Order Service

Betalningsleverantören, leveranstjänsten och SMS/e-posttjänsten hanteras av externa leverantörer.

Lagersystemet är ett äldre internt system.

---

## Krav

Följande krav har hittills dokumenterats.

### K1 – Inloggning

Kunden ska kunna skapa konto och logga in med e-postadress och lösenord.

Efter tre felaktiga inloggningsförsök ska kontot låsas i 30 minuter.

### K2 – Produkter

Kunden ska kunna:

- söka produkter
- filtrera produkter
- se pris
- se lagerstatus
- se produktinformation

### K3 – Kundvagn

Kunden ska kunna:

- lägga produkter i kundvagnen
- ändra antal
- ta bort produkter

Produkter som inte längre finns i lager får inte kunna köpas.

### K4 – Rabatt

Kunder kan använda rabattkoder.

En rabattkod kan:

- ha ett giltighetsdatum
- ha ett minsta ordervärde
- endast kunna användas en gång per kund

### K5 – Betalning

Kunden ska kunna betala med:

- Visa
- Mastercard
- Swish

En order får endast skapas om betalningen har godkänts.

Kunden får inte debiteras två gånger för samma order.

### K6 – Lager

När en order genomförs ska lagersaldot automatiskt uppdateras.

Om produkten tar slut ska den inte längre kunna köpas.

### K7 – Leverans

Kunden ska kunna välja mellan:

- hemleverans
- ombud

Leveransalternativ och pris hämtas från en extern leveranstjänst.

### K8 – Orderbekräftelse

När ett köp är genomfört ska kunden få:

- orderbekräftelse via e-post
- ordernummer
- information om betalning
- information om leverans

### K9 – Avbeställning

Kunden ska kunna avbeställa en order så länge ordern inte har skickats.

Vid avbeställning ska:

1. ordern avbrytas
2. betalningen återbetalas
3. lagersaldot återställas
4. kunden få en bekräftelse

### K10 – Behörighet

Kundservice ska kunna se kundens order och betalningsstatus.

Kundservice får inte ändra produktpriser eller användarbehörigheter. Endast administratörer får göra detta.

---

## Viktig projektinformation

Projektet består av:

- 3 utvecklingsteam
- 1 Product Owner
- 1 projektledare
- 4 testare
- 1 testledare
- representanter från kundservice
- externa leverantörer

Utvecklingen sker agilt i tvåveckorssprintar.

Produktionsrelease är planerad om 4 månader.

Det finns en gemensam testmiljö som används av alla tre utvecklingsteam.

Lagersystemet är cirka 15 år gammalt och dokumentationen är begränsad.

Betalningsleverantören har en separat testmiljö.

---

## Uppgift

Ni arbetar i grupper och agerar testledare för NordicShop.

Analysera informationen ni har fått och ta fram ett första underlag för testarbetet.

Ni ska identifiera följande sex områden.

### 1. Testobjekt

Identifiera vad som behöver testas.

Ett testobjekt kan vara:

- ett system
- en applikation
- en tjänst
- en funktion
- ett API
- en integration

För varje testobjekt ska ni kort beskriva:

| Testobjekt | Vad behöver verifieras? | Prioritet (Hög/Medel/Låg) |
|------------|-------------------------|---------------------------|
|            |                         |                           |

Fundera särskilt på: **Vad ingår egentligen i vårt testansvar?**

### 2. Kritiska affärsflöden

Identifiera minst tre kritiska E2E-flöden.

Beskriv varje flöde från början till slut.

Exempel på format:

```
Kund → Funktion A → System B → Integration C → Resultat
```

För varje flöde:

- Vad är verksamhetsmålet?
- Vilka system ingår?
- Vad händer om flödet inte fungerar?
- Hur kritiskt är flödet?

### 3. Integrationer

Identifiera samtliga viktiga integrationer.

Använd gärna följande tabell:

| Från | Till | Information | Vad kan gå fel? |
|------|------|-------------|-----------------|
|      |      |             |                 |

Fundera exempelvis på:

- Vad händer om mottagande system är nere?
- Vad händer vid timeout?
- Vad händer om fel information skickas?
- Vad händer om samma meddelande skickas två gånger?

### 4. Stakeholders

Identifiera vilka personer, roller, team och organisationer som är viktiga för testarbetet.

För varje stakeholder:

| Stakeholder | Vad behöver testledaren från dem? | Vad behöver de från testledaren? |
|-------------|-----------------------------------|----------------------------------|
|             |                                   |                                  |

Fundera på:

- Vem känner verksamheten?
- Vem kan svara på tekniska frågor?
- Vem ansvarar för externa system?
- Vem prioriterar?
- Vem behöver teststatus?
- Vem behöver involveras inför release?

### 5. Risker

Identifiera minst 8 risker.

Riskerna kan vara:

- affärsrisker
- tekniska risker
- säkerhetsrisker
- integrationsrisker
- projektrisker
- testrisker

Använd följande format:

| Risk | Sannolikhet (L/M/H) | Konsekvens (L/M/H) | Risknivå (L/M/H) | Möjlig teståtgärd |
|------|---------------------|--------------------|------------------|-------------------|
|      |                     |                    |                  |                   |

Fundera på: **Vad kan gå fel och vad blir konsekvensen?**

### 6. Frågor som testledaren behöver få svar på

Ni har inte fått all information ni behöver. Det är medvetet.

Som testledare behöver ni identifiera vad som fortfarande är oklart.

Ta fram minst 10 frågor som ni skulle vilja ställa innan ni skapar teststrategin.

Fundera på:

- scope
- tidplan
- testmiljö
- testdata
- integrationer
- ansvar
- säkerhet
- prestanda
- regulatoriska krav
- release
- tidigare problem
- automation

---

## Presentation

Varje grupp presenterar sin analys på cirka 8–10 minuter.

Fokus ligger på att kunna:

**identifiera → prioritera → motivera**

Ni ska kunna förklara: **Varför tycker vi att detta är viktigt för testarbetet?**
