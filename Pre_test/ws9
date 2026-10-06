# WORKSHOP – Tre team behöver samma testmiljö

## Scenario

NordicShop-projektet har en gemensam SYS-miljö.

Tre utvecklingsteam behöver miljön samtidigt.

## Team A – Betalning

Behöver miljön för:

SIT av kort- och Swishbetalning.

Release:

om 1 vecka.

Tester:

- lyckad betalning
- nekad betalning
- timeout
- betalning → order

Beroenden:

- Payment Provider TEST

## Team B – Kundprofil

Behöver miljön för:

systemtest av ny kundprofil.

Release:

om 4 veckor.

Tester:

- ändra telefonnummer
- ändra adress
- preferenser

Beroenden:

- kunddatabas

## Team C – Order och lager

Behöver miljön för:

regression av order- och lagerflödet.

Release:

om 1 vecka.

Tester:

- order
- lager
- avbeställning
- återbetalning

Beroenden:

- Inventory System

## Problem

Alla tre team behöver SYS:

måndag–onsdag.

Men miljön kan endast ha en stabil releaseversion åt gången.

Team A behöver Build A.

Team B behöver Build B.

Team C behöver Build C.

Det går alltså inte att köra alla tre parallellt.

## Uppgift 1 – Analysera behovet

För varje team:

- vad ska testas?
- hur kritisk är aktiviteten?
- när är release?
- vilka beroenden finns?
- finns alternativ miljö?
- kan något göras utan SYS?

### Team A – Betalning

| **Fråga** | **Svar** |
| --- | --- |
| Vad ska testas? | SIT av kort- och Swishbetalning: lyckad betalning, nekad betalning, timeout, betalning → order |
| Hur kritisk är aktiviteten? | **Mycket kritisk** – betalflödet är affärskritiskt och release är om 1 vecka |
| När är release? | Om 1 vecka |
| Vilka beroenden finns? | Payment Provider TEST |
| Finns alternativ miljö? | Eventuellt separat SIT-miljö för betalning, men troligen inte med fullständig integration mot Payment Provider TEST |
| Kan något göras utan SYS? | Enkla komponenttester och förberedelser kan göras, men SIT kräver SYS |

### Team B – Kundprofil

| **Fråga** | **Svar** |
| --- | --- |
| Vad ska testas? | Systemtest av ny kundprofil: ändra telefonnummer, ändra adress, preferenser |
| Hur kritisk är aktiviteten? | **Mindre kritisk** – release om 4 veckor, ingen omedelbar releasepress |
| När är release? | Om 4 veckor |
| Vilka beroenden finns? | Kunddatabas |
| Finns alternativ miljö? | Ja, möjlighet finns att använda annan miljö eller senarelägga test |
| Kan något göras utan SYS? | Ja, förberedelser, testfall och komponenttester kan göras utan SYS |

### Team C – Order och lager

| **Fråga** | **Svar** |
| --- | --- |
| Vad ska testas? | Regression av order- och lagerflödet: order, lager, avbeställning, återbetalning |
| Hur kritisk är aktiviteten? | **Mycket kritisk** – regression inför release om 1 vecka |
| När är release? | Om 1 vecka |
| Vilka beroenden finns? | Inventory System |
| Finns alternativ miljö? | Eventuellt separat regressionsmiljö, men beroendet mot Inventory System kan vara begränsande |
| Kan något göras utan SYS? | Vissa regressionstester kan förberedas, men hela flödet kräver SYS |

## Uppgift 2 – Prioritera

Prioritera Team A, B och C.

Använd:

- releasekritikalitet
- affärsrisk
- teknisk risk
- beroenden
- konsekvens vid försening

Motivera.

### Prioriteringsordning

- **Team A – Betalning**
- **Team C – Order och lager**
- **Team B – Kundprofil**

### Motivering

**Team A – Betalning (högst prioritet)**

- **Releasekritikalitet:** Release om 1 vecka – mycket hög.
- **Affärsrisk:** Betalflödet är direkt intäktskritiskt. Om betalning inte fungerar kan kunder inte handla.
- **Teknisk risk:** Integration mot Payment Provider TEST är komplex och kräver SIT.
- **Beroenden:** Externt beroende (Payment Provider TEST) som kan vara svårt att styra.
- **Konsekvens vid försening:** Stor – release kan inte genomföras, intäkter påverkas.

**Team C – Order och lager (näst högst prioritet)**

- **Releasekritikalitet:** Release om 1 vecka – hög.
- **Affärsrisk:** Order- och lagerflödet är kärnverksamhet. Fel leder till felaktiga ordrar och lagerstatus.
- **Teknisk risk:** Regression är viktig för att säkerställa att inget har gått sönder.
- **Beroenden:** Inventory System – internt/externt beroende.
- **Konsekvens vid försening:** Stor – release kan behöva skjutas upp eller släppas med kända risker.

**Team B – Kundprofil (lägst prioritet)**

- **Releasekritikalitet:** Release om 4 veckor – låg.
- **Affärsrisk:** Viktig men inte akut; kundprofilfunktioner är inte intäktskritiska på samma sätt.
- **Teknisk risk:** Lägre – enklare funktioner och färre externa beroenden.
- **Beroenden:** Kunddatabas – hanterbart.
- **Konsekvens vid försening:** Liten – releasen ligger längre fram och kan justeras.

## Uppgift 3 – Skapa miljöplan

Skapa en kalender för:

Måndag → Fredag

Exempel:

| **Dag** | **Team** | **Aktivitet** | **Version/build** |
| --- | --- | --- | --- |
| Måndag | A | SIT betalning | Build A |
| Tisdag | A | SIT betalning (forts.) | Build A |
| Onsdag | C | Regression order/lager | Build C |
| Torsdag | C | Regression order/lager (forts.) | Build C |
| Fredag | B | Systemtest kundprofil | Build B |

### Kommentar till miljöplanen

- **Måndag–tisdag:** Team A prioriteras eftersom deras release är mest kritisk och de behöver SIT mot Payment Provider TEST.
- **Onsdag–torsdag:** Team C får miljön för regression av order- och lagerflödet.
- **Fredag:** Team B får miljön för systemtest av kundprofil.
- Miljön kan endast ha en stabil releaseversion åt gången, därför måste den byggas om mellan teamen.
- Deployment sker kvällstid eller tidig morgon för att maximera testtiden.

## Uppgift 4 – Planera deployment

Beskriv:

- när varje build deployas
- vem som ansvarar
- hur miljön verifieras efter deployment

### Deploymentplan

| **Build** | **Deployas** | **Ansvarig** | **Verifiering** |
| --- | --- | --- | --- |
| Build A | Söndag kväll (inför måndag) | Miljöansvarig / DevOps | Smoke test + verifiering av Payment Provider TEST-anslutning |
| Build C | Tisdag kväll (inför onsdag) | Miljöansvarig / DevOps | Smoke test + verifiering av Inventory System-anslutning |
| Build B | Torsdag kväll (inför fredag) | Miljöansvarig / DevOps | Smoke test + verifiering av kunddatabas |

### Verifiering efter deployment

- **Smoke test** enligt Uppgift 5.
- Kontrollera att rätt build/version är deployad.
- Kontroll av integrationer mot externa system (Payment Provider TEST, Inventory System, kunddatabas).
- Loggkontroll för fel vid uppstart.
- Meddelande till berört team att miljön är redo.

## Uppgift 5 – Smoke Test

Skapa ett kort smoke test med 5 kontroller som körs efter varje deployment.

### Smoke Test – 5 kontroller

- **Startkontroll:** Verifiera att applikationen startar utan fel i loggen.
- **Inloggning:** Verifiera att en testanvändare kan logga in.
- **Betalningsflöde (förenklat):** Genomför en enkel betalningstransaktion mot Payment Provider TEST.
- **Orderflöde (förenklat):** Skapa en order och verifiera att den registreras.
- **Databasanslutning:** Verifiera att applikationen kan läsa och skriva mot aktuell databas (kunddatabas eller Inventory System beroende på build).

### Syfte

Smoke testet säkerställer att miljön är stabil och att de mest kritiska funktionerna fungerar innan teamet börjar sina tester.

## Uppgift 6 – Kommunikation

Beskriv:

- vem informeras om miljöplanen
- hur ändringar kommuniceras
- hur blockerare rapporteras
- vem fattar beslut vid konflikt

### Vem informeras om miljöplanen?

- Alla tre team (A, B, C)
- Projektledaren
- Miljöansvarig / DevOps
- Testledaren
- Eventuellt externa parter (Payment Provider, Inventory System-ansvariga)

### Hur ändringar kommuniceras

- Via gemensam kanal (t.ex. Teams/Slack) och e-post.
- Uppdaterad miljöplan publiceras i projektets dokumentationsyta.
- Vid akuta ändringar: direktmeddelande + telefonkontakt.

### Hur blockerare rapporteras

- Blockerare rapporteras omedelbart i gemensam kanal.
- Testledaren och miljöansvarig taggas.
- Ärendet loggas i projektets ärendehanteringssystem.

### Vem fattar beslut vid konflikt?

- I första hand **testledaren** tillsammans med **projektledaren**.
- Vid resurskonflikt mellan team: **projektledaren** fattar beslut.
- Vid tekniska miljöfrågor: **miljöansvarig / DevOps**.

## Uppgift 7 – Risker

Identifiera minst 3 miljörisker.

Använd:

| **Risk** | **Konsekvens** | **Åtgärd** | **Ägare** |
| --- | --- | --- | --- |

### Riskregister

| **Risk** | **Konsekvens** | **Åtgärd** | **Ägare** |
| --- | --- | --- | --- |
| Deployment misslyckas | Miljön blir otillgänglig, tester försenas | Ha backup plan och tidigare stabil build redo | Miljöansvarig / DevOps |
| Miljön kan bara ha en build åt gången | Team får vänta, release riskerar försenas | Tydlig schemaplanering och prioritering | Testledare |
| Externt beroende (Payment Provider TEST) är otillgängligt | Team A kan inte genomföra SIT | Avtalad SLA och kontaktväg med leverantör | Projektledare |
| Regression hinner inte bli klar | Release med kända fel | Prioritera kritiska testfall, extra testtid | Testledare |
| Kommunikationsbrist mellan team | Dubbelbokning av miljön | Gemensam kanal och tydlig miljöplan | Projektledare |

## FÖRÄNDRING

På tisdag morgon misslyckas deployment för Team A och TEST-miljön blir otillgänglig i fyra timmar.

Samtidigt väntar Team C på att börja sin regression.

## Uppgift 8 – Vad gör testledaren?

Besvara:

- Stoppar ni Team A:s tester?
- När eskalerar ni?
- Får Team C miljön direkt när den kommer tillbaka?
- Hur hanteras Team A:s återstående testbehov?
- Vilken release är mest utsatt?
- Behöver tidsplanen ändras?
- Vad kommunicerar ni till projektledaren?

### Svar

**1. Stoppar ni Team A:s tester?**

Ja, Team A:s tester stoppas omedelbart eftersom miljön är otillgänglig. Testledaren meddelar Team A att avbryta tills miljön är återställd och verifierad.

**2. När eskalerar ni?**

Eskalering sker omedelbart till projektledaren och miljöansvarig när deployment misslyckas och miljön blir otillgänglig. Om felet inte är åtgärdat inom 1–2 timmar eskaleras det vidare enligt beslutstrappan.

**3. Får Team C miljön direkt när den kommer tillbaka?**

Nej. Först måste miljön verifieras med smoke test och säkerställas att Build A fungerar. Därefter gör testledaren en prioritering. Eftersom både Team A och Team C har release om 1 vecka kan Team A behöva fortsätta först, men Team C kan få en tidslucka om Team A inte kan fortsätta omedelbart.

**4. Hur hanteras Team A:s återstående testbehov?**

- Team A får prioritera sina mest kritiska testfall.
- Om möjligt förlängs testtiden under tisdagen eller flyttas till onsdag.
- Alternativt kan vissa tester köras i annan miljö om det är möjligt.
- Om tiden inte räcker kan release behöva skjutas upp eller släppas med kända risker.

**5. Vilken release är mest utsatt?**

Team A release är mest utsatt eftersom deras deployment misslyckades och de har release om 1 vecka och Team C release är utsatt eftersom deras regression försenas.

**6. Behöver tidsplanen ändras?**

Ja, tidsplanen behöver sannolikt justeras. Team A kan behöva mer tid, och Team C kan behöva skjutas fram. En reviderad miljöplan tas fram i samråd med projektledaren.

**7. Vad kommunicerar ni till projektledaren?**

- Deployment för Team A misslyckades och miljön är otillgänglig i fyra timmar.
- Team A tester är stoppade och deras release är i riskzonen.
- Team C väntar på regression och kan också påverkas.
- Åtgärder: felsökning pågår, backup plan aktiveras vid behov, smoke test körs innan miljön släpps.
- Beslut som behövs: prioritering mellan Team A och Team C, eventuell justering av releaseplan.
- Nästa uppdatering: inom 1 timme eller när ny information finns.



