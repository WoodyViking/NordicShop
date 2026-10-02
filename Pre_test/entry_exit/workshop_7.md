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
| EN1 | | |
| EN2 | | |
| EN3 | | |
| EN4 | | |
| EN5 | | |
| EN6 | | |

### Acceptanstest Exit Criteria

| # | Acceptanstest Exit Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| EX1 | | |
| EX2 | | |
| EX3 | | |
| EX4 | | |
| EX5 | | |
| EX6 | | |
