# Workshop 7 – Entry/Exit för NordicShop

Här slår vi ihop gruppens svar på Uppgift 1–3. Varje testnivå har en egen fil i den här mappen där svaren på Uppgift 4–6 också finns:

- SIT: [sit.md](sit.md)
- Systemtest: `systemtest.md` (inte skapad än)
- Acceptanstest: `acceptanstest.md` (inte skapad än)

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

## Uppgift 2 – Systemtest

### Systemtest Entry Criteria

| # | Systemtest Entry Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| EN1 | | |
| EN2 | | |
| EN3 | | |
| EN4 | | |
| EN5 | | |
| EN6 | | |

### Systemtest Exit Criteria

| # | Systemtest Exit Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| EX1 | | |
| EX2 | | |
| EX3 | | |
| EX4 | | |
| EX5 | | |
| EX6 | | |

## Uppgift 3 – Acceptanstest

### Acceptanstest Entry Criteria

| # | Acceptanstest Entry Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| EN1 | Systemtestets obligatoriska exit-kriterier är uppfyllda: kritiska testfall, behörighetstest och betalningsflöden har passerat, och det finns inga öppna fel med prioritet Kritisk. | Obligatoriskt (MUST) |
| EN2 | Acceptanskriterierna för kraven K1–K10 är dokumenterade och godkända av Product Owner. | Obligatoriskt (MUST) |
| EN3 | Acceptansscenarierna för de tre E2E-flödena och kundservicens arbetsflöde är skrivna i verksamhetens språk och godkända av Product Owner. | Obligatoriskt (MUST) |
| EN4 | Verksamhetsrepresentanterna är bokade med namn för hela testveckan: minst två från kundservice och en administratör. | Obligatoriskt (MUST) |
| EN5 | Testmiljön har produktionslik testdata: minst 20 produkter, testkunder med orderhistorik och ordrar i status betald, skickad och avbeställd, samt inloggningskonton för kundservice och administratör. | Obligatoriskt (MUST) |
| EN6 | Deltagarna har fått en introduktion på högst en timme om testmanuskripten och om hur fel rapporteras, och har fått listan över kända fel från systemtestet. | Önskvärt (SHOULD) |


### Acceptanstest Exit Criteria

| # | Acceptanstest Exit Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| # | Acceptanstest Exit Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| EX1 | 100 % av acceptansscenarierna för de kritiska verksamhetsflödena är körda: köp, avbeställning/återbetalning, sista produkten i lager, kundservice hanterar ett ärende samt administratör ändrar pris och skapar rabattkod. | Obligatoriskt (MUST) |
| EX2 | Det finns inga öppna fel med prioritet Kritisk, och inga öppna fel med prioritet Hög som saknar workaround. | Obligatoriskt (MUST) |
| EX3 | Kundservice har själva verifierat att de kan söka kund, se order och betalningsstatus, avbryta order och initiera återbetalning utan manuella extrasteg utanför systemet. | Obligatoriskt (MUST) |
| EX4 | Varje kvarstående fel har ett dokumenterat beslut som är godkänt av Product Owner: rättas före release, rättas efter release eller accepteras. | Obligatoriskt (MUST) |
| EX5 | Product Owner och verksamhetsansvarig har skriftligt godkänt acceptanstestet (sign-off). | Obligatoriskt (MUST) |
| EX6 | Minst 90 % av alla acceptansscenarier har passerat. | Önskvärt (SHOULD) |
| EX7 | Verksamhetens synpunkter på användbarhet är dokumenterade och har en ansvarig för uppföljning efter release. | Önskvärt (SHOULD) |

### Koppling till risker

Kriterierna hänger ihop med riskerna i [test_analys.md](../test_analys.md):

| Risk | Kriterier |
|---|---|
| 1. Det 15 år gamla lagersystemet klarar inte integrationen eller prestandan | EN5, EX1 |
| 7. Kundservice kan av misstag ändra priser eller behörigheter | EN5, EX1 |
| 9. Vid avbeställning avbryts ordern men återbetalning genomförs inte | EX1, EX3 |
| 10. Kundservice har inte tid att delta i acceptanstest | EN4, EX3, EX5 |

## Uppgift 4 – Motivera

De tre viktigaste kriterierna för acceptanstest:

### 1. EN4 – Verksamhetsrepresentanterna är bokade med namn

Utan verksamheten finns det inget acceptanstest. Kundservice har mycket ordinarie arbete, och risken att de inte har tid är verklig (risk 10). Genom att kräva namn och tid i förväg går det att kontrollera att kriteriet är uppfyllt innan testet startar.

### 2. EX3 – Kundservice har själva verifierat sina arbetsflöden

Ett av projektets verksamhetsmål är att minska kundservicens manuella arbete. Bara kundservice själva kan avgöra om plattformen stödjer deras sätt att arbeta. Om de behöver manuella extrasteg, till exempel vid avbeställning och återbetalning (risk 9), har plattformen inte uppnått målet, även om alla testfall har passerat.

### 3. EX5 – Skriftligt godkännande (sign-off)

Det är verksamheten som äger beslutet om lösningen är tillräckligt bra. Ett skriftligt godkännande visar att Product Owner och verksamheten har accepterat både lösningen och de kvarstående riskerna. Det är ett nödvändigt underlag för Go/No-Go-beslutet.
