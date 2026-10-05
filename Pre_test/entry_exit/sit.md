# Entry/Exit-kriterier – SIT (Systemintegrationstest)

**Projekt:** NordicShop
**Testnivå:** SIT – verifierar integrationerna mellan Webb/App, Backend/Order Service, Lagersystem, Payment Provider, Delivery Provider och E-post/SMS Service.

**MUST** = Måste uppfyllas.
**SHOULD** = Bör uppfyllas men avvikelse kan accepteras efter riskbedömning.

## Uppgift 1 – SIT

### SIT Entry Criteria

| # | SIT Entry Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| EN1 | Komponenttest är klart för alla tjänster som ingår, minst 80 % av enhetstesterna passerar och det finns inga öppna fel med prioritet Kritisk. | Obligatoriskt (MUST) |
| EN2 | API-specifikationer finns för alla integrationer (Lagersystem, Payment Provider, Delivery Provider och E-post/SMS) och är godkända av både det ansvariga utvecklingsteamet och motparten (leverantör eller systemägare). | Obligatoriskt (MUST) |
| EN3 | SIT-miljön är uppsatt och ett röktest har gått igenom: alla tjänster svarar och anslutningen till lagersystemet är verifierad. | Obligatoriskt (MUST) |
| EN4 | Det finns åtkomst till Payment Providers testmiljö med testkort och Swish-test. Om den inte finns ska det finnas en fungerande mock av betalflödet. | Obligatoriskt (MUST) |
| EN5 | Testdata finns: minst 20 produkter med olika lagersaldon, varav minst en med saldo 1 för flöde 3, samt testkunder och rabattkoder. | Obligatoriskt (MUST) |
| EN6 | SIT-testfallen för de tre E2E-flödena (köp, avbeställning/återbetalning, sista produkten i lager) är granskade av minst en person som inte skrivit dem och godkända av testledaren. | Önskvärt (SHOULD) |
| EN7 | Ett releaseschema för den delade testmiljön är dokumenterat och godkänt av alla tre utvecklingsteamen, med fasta tider för driftsättning. | Önskvärt (SHOULD) |

### SIT Exit Criteria

| # | SIT Exit Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| EX1 | 100 % av de planerade SIT-testfallen är körda och minst 95 % har passerat. | Obligatoriskt (MUST) |
| EX2 | Det finns inga öppna fel med prioritet Kritisk eller Hög i integrationerna mot Payment Provider och Lagersystem. | Obligatoriskt (MUST) |
| EX3 | Det är verifierat att en avbruten betalning inte skapar någon order och att dubbeldebitering inte sker. | Obligatoriskt (MUST) |
| EX4 | Lagersaldot uppdateras korrekt vid köp och återställs vid avbeställning, verifierat i alla tre E2E-flödena. | Obligatoriskt (MUST) |
| EX5 | Felhanteringen är testad: vid timeout från lagersystemet eller nedtid hos Delivery Provider får kunden ett felmeddelande inom 10 sekunder, ingen order skapas och ingen debitering görs. | Obligatoriskt (MUST) |
| EX6 | Öppna fel med prioritet Medel eller Låg är dokumenterade och har en ansvarig och en åtgärdsplan. | Önskvärt (SHOULD) |
| EX7 | En SIT-testrapport är skriven och godkänd av testledaren. | Önskvärt (SHOULD) |

### Koppling till risker

Kriterierna hänger ihop med riskerna i [test_analys.md](../test_analys.md):

| Risk | Kriterier |
|---|---|
| 1. Det 15 år gamla lagersystemet klarar inte integrationen eller prestandan | EN3, EX4, EX5 |
| 2. Tre utvecklingsteam krockar i den gemensamma testmiljön | EN3, EN7 |
| 3. Betalningsleverantörens testmiljö är instabil eller nere | EN4, EX3 |

## Uppgift 4 – Motivera

De tre viktigaste kriterierna för SIT:

### 1. EX3 – Avbruten betalning skapar ingen order och ingen dubbeldebitering

Betalningen är det enda flöde där ett fel direkt kostar kunden pengar. Om kunden debiteras utan att en order skapas, eller debiteras två gånger, leder det till återbetalningar, ärenden till kundservice och förlorat förtroende. Felet uppstår i övergången mellan Order Service och Payment Provider, så det går bara att hitta på SIT-nivå, inte i komponenttest. Kravet K5 och risk 3 pekar på samma sak.

### 2. EX4 – Lagersaldot uppdateras och återställs korrekt

Lagersystemet är 15 år gammalt och är projektets största risk (risk 1, riskvärde 25). Om saldot blir fel säljer NordicShop varor som inte finns, vilket ger restorder och hög belastning på kundservice (flöde 3). Ett saldo som inte återställs vid avbeställning gör att varor ser slutsålda ut fast de finns. Båda felen syns först när Order Service och Lagersystemet pratar med varandra.

### 3. EN3 – SIT-miljön är uppsatt och röktestad

Utan en fungerande miljö går det inte att köra något SIT-test alls. Tre team delar samma testmiljö (risk 2), och om testet startar i en trasig miljö går testtiden åt till att felsöka miljön i stället för systemet. Det ger falska fel och gör att resultaten inte går att lita på. Kriteriet är billigt att kontrollera men skyddar hela testperioden.

## Uppgift 5 – Kategorisera
### SIT:
| Kategori | Entry | Exit |
|---|---|---|
| **MUST** | SIT-EN1, SIT-EN2, SIT-EN3, SIT-EN4, SIT-EN5 | SIT-EX1, SIT-EX2, SIT-EX3, SIT-EX4, SIT-EX5 |
| **SHOULD** | SIT-EN6, SIT-EN7 | SIT-EX6, SIT-EX7 |

**Motivering:**
- **MUST** är de kriterier som gäller betalning, lager och testmiljö. Om något av dem inte är uppfyllt går det antingen inte att testa, eller så finns det en känd risk att kunder förlorar pengar eller köper varor som inte finns.
- **SHOULD** är kriterier som gäller granskning, planering och dokumentation. De gör testet bättre, men en avvikelse kan accepteras efter en riskbedömning. Ett exempel: om testfallen inte hunnit granskas (EN6) kan testet ändå starta, och granskningen görs parallellt.

## Uppgift 6 – Kontrollera kvaliteten
### SIT:
Varje kriterium har kontrollerats mot de fem frågorna:
**T** = Tydligt? **M** = Mätbart? **A** = Går att avgöra om det är uppfyllt? **R** = Relevant för SIT? **K** = Kopplat till risk?

| # | T | M | A | R | K | Kommentar |
|---|---|---|---|---|---|---|
| SIT-EN1 | Ja | Ja | Ja | Ja | Ja | Visar att komponenterna fungerar var för sig innan de kopplas ihop. |
| SIT-EN2 | Nej → Ja | Ja | Nej → Ja | Ja | Ja | Förbättrad, se nedan. |
| SIT-EN3 | Ja | Ja | Ja | Ja | Ja | Risk 1 och 2. |
| SIT-EN4 | Ja | Ja | Ja | Ja | Ja | Risk 3. |
| SIT-EN5 | Ja | Ja | Ja | Ja | Ja | Krävs för flöde 3 (sista produkten i lager). |
| SIT-EN6 | Nej → Ja | Ja | Nej → Ja | Ja | Ja | Förbättrad, se nedan. |
| SIT-EN7 | Nej → Ja | Ja | Nej → Ja | Ja | Ja | Förbättrad, se nedan. |
| SIT-EX1 | Ja | Ja | Ja | Ja | Ja | Visar att testet är genomfört. |
| SIT-EX2 | Ja | Ja | Ja | Ja | Ja | Risk 1 och 3. |
| SIT-EX3 | Ja | Ja | Ja | Ja | Ja | Krav K5, risk 3. |
| SIT-EX4 | Ja | Ja | Ja | Ja | Ja | Krav K6 och K9, risk 1. |
| SIT-EX5 | Ja | Nej → Ja | Nej → Ja | Ja | Ja | Förbättrad, se nedan. |
| SIT-EX6 | Ja | Ja | Ja | Ja | Ja | Gör det möjligt att gå vidare med kända fel under kontroll. |
| SIT-EX7 | Ja | Ja | Ja | Ja | Ja | Ger underlag för beslutet att gå vidare till systemtest. |

### Förbättrade formuleringar -SIT

Tabellerna i Uppgift 1 innehåller redan de förbättrade formuleringarna.

| # | Före | Problem | Efter |
|---|---|---|---|
| SIT-EN2 | API-specifikationer finns och är godkända för alla integrationer. | Det framgick inte vem som godkänner, så det gick inte att avgöra om kriteriet var uppfyllt. | ...godkända av både det ansvariga utvecklingsteamet och motparten (leverantör eller systemägare). |
| SIT-EN6 | SIT-testfallen är granskade och godkända. | Det framgick inte vem som granskar och godkänner. | ...granskade av minst en person som inte skrivit dem och godkända av testledaren. |
| SIT-EN7 | Ett releaseschema för den delade testmiljön är överenskommet mellan teamen. | "Överenskommet" går inte att kontrollera i efterhand. | ...dokumenterat och godkänt av alla tre utvecklingsteamen, med fasta tider för driftsättning. |
| SIT-EX5 | Timeout och nedtid ger ett kontrollerat felmeddelande och kassan låser sig inte. | "Kontrollerat" och "låser sig inte" går inte att mäta. | ...kunden får ett felmeddelande inom 10 sekunder, ingen order skapas och ingen debitering görs. |
