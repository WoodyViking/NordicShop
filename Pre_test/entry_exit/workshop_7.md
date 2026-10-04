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
| EN3 | Acceptansscenarierna för de tre E2E-flödena och kundservicens arbetsflöde är godkända av Product Owner, och minst en person från kundservice har läst dem och bekräftat att de kan följa stegen utan hjälp. | Obligatoriskt (MUST) |
| EN4 | Verksamhetsrepresentanterna är bokade med namn för hela testveckan: minst två från kundservice och en administratör. | Obligatoriskt (MUST) |
| EN5 | Testmiljön har produktionslik testdata: minst 20 produkter, testkunder med orderhistorik och ordrar i status betald, skickad och avbeställd, samt inloggningskonton för kundservice och administratör. | Obligatoriskt (MUST) |
| EN6 | Deltagarna har fått en introduktion på högst en timme om testmanuskripten och om hur fel rapporteras, och har fått listan över kända fel från systemtestet. | Önskvärt (SHOULD) |


### Acceptanstest Exit Criteria

| # | Acceptanstest Exit Criteria | Obligatoriskt/Önskvärt |
|---|---|---|
| EX1 | 100 % av acceptansscenarierna för de kritiska verksamhetsflödena är körda: köp, avbeställning/återbetalning, sista produkten i lager, kundservice hanterar ett ärende samt administratör ändrar pris och skapar rabattkod. | Obligatoriskt (MUST) |
| EX2 | Det finns inga öppna fel med prioritet Kritisk. Varje öppet fel med prioritet Hög har en workaround som är dokumenterad och godkänd av Product Owner. | Obligatoriskt (MUST) |
| EX3 | Kundservice har själva verifierat att de kan söka kund, se order och betalningsstatus, avbryta order och initiera återbetalning utan manuella extrasteg utanför systemet. | Obligatoriskt (MUST) |
| EX4 | Varje kvarstående fel har ett dokumenterat beslut som är godkänt av Product Owner: rättas före release, rättas efter release eller accepteras. | Obligatoriskt (MUST) |
| EX5 | Product Owner och verksamhetsansvarig har skriftligt godkänt acceptanstestet (sign-off). | Obligatoriskt (MUST) |
| EX6 | Minst 90 % av alla acceptansscenarier har passerat. | Önskvärt (SHOULD) |
| EX7 | Alla deltagare har lämnat sina synpunkter på användbarhet i ett gemensamt formulär, och varje synpunkt har en ansvarig och ett beslut: åtgärdas före release, åtgärdas efter release eller åtgärdas inte. | Önskvärt (SHOULD) |

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

### 1. EX1 – De kritiska verksamhetsflödena är körda

Köp, avbeställning/återbetalning och sista produkten i lager är de flöden där kunden betalar, får pengar tillbaka eller riskerar att köpa en vara som inte finns. Det är också i de flödena kundservice behöver kunna hjälpa kunden när något går fel. Om verksamheten inte har kört dem vet vi inte om plattformen fungerar i verkliga situationer, bara att den fungerar i testarnas testfall. Kriteriet är kopplat till risk 1 (lagersystemet) och risk 9 (avbeställning utan återbetalning).

### 2. EX2 – Inga kritiska fel och inga höga fel utan godkänd workaround

Acceptanstestet är den sista testnivån före release. Ett kritiskt fel som finns kvar här går direkt ut till kunderna, till exempel att en kund debiteras utan att få någon order, eller att en återbetalning aldrig genomförs. Fel med prioritet Hög kan accepteras bara om det finns en workaround som Product Owner har godkänt, så att kundservice vet hur de ska hantera felet efter release.

### 3. EN1 – Systemtestets obligatoriska exit-kriterier är uppfyllda

Verksamheten har begränsad tid, och kundservice måste sköta sitt ordinarie arbete samtidigt (risk 10). Om acceptanstestet startar med kritiska fel kvar från systemtestet går testtiden åt till att hitta fel som testarna borde ha hittat, i stället för att verifiera verksamhetens arbetsflöden. Kriteriet är billigt att kontrollera men skyddar hela testveckan.

### 3. EX5 – Skriftligt godkännande (sign-off)

Det är verksamheten som äger beslutet om lösningen är tillräckligt bra. Ett skriftligt godkännande visar att Product Owner och verksamheten har accepterat både lösningen och de kvarstående riskerna. Det är ett nödvändigt underlag för Go/No-Go-beslutet.

## Uppgift 5 – Kategorisera

| Kategori | Entry | Exit |
|---|---|---|
| **MUST** | EN1, EN2, EN3, EN4, EN5 | EX1, EX2, EX3, EX4, EX5 |
| **SHOULD** | EN6 | EX6, EX7 |

**Motivering:**
- **MUST** är de kriterier som gäller verksamhetens deltagande, de kritiska verksamhetsflödena och det formella godkännandet. Om något av dem inte är uppfyllt kan verksamheten inte genomföra testet, eller så finns det inget giltigt underlag för releasebeslutet.
- **SHOULD** är kriterier som gör testet effektivare och ger underlag för förbättringar. En avvikelse kan accepteras efter riskbedömning. Ett exempel: om introduktionen (EN6) inte hinner hållas kan en testare i stället stödja deltagarna på plats under testet.

## Uppgift 6 – Kontrollera kvaliteten

Varje kriterium har kontrollerats mot de fem frågorna:
**T** = Tydligt? **M** = Mätbart? **A** = Går att avgöra om det är uppfyllt? **R** = Relevant för acceptanstest? **K** = Kopplat till risk?

| # | T | M | A | R | K | Kommentar |
|---|---|---|---|---|---|---|
| EN1 | Ja | Ja | Ja | Ja | Ja | Verksamheten ska inte hitta kritiska fel som systemtestet borde ha hittat. |
| EN2 | Ja | Ja | Ja | Ja | Ja | Utan acceptanskriterier går det inte att avgöra om testet är godkänt. |
| EN3 | Ja | Ja | Ja | Ja | Ja | Kundservice bekräftar själva att de kan följa scenarierna. Risk 10. |
| EN4 | Nej → Ja | Ja | Nej → Ja | Ja | Ja | Förbättrad, se nedan. Risk 10. |
| EN5 | Ja | Ja | Ja | Ja | Ja | Lager och behörigheter kan inte testas utan rätt data och konton. Risk 1 och 7. |
| EN6 | Ja | Ja | Ja | Ja | Ja | Gör att testtiden används till testning i stället för frågor om verktyget. |
| EX1 | Ja | Ja | Ja | Ja | Ja | Täcker de tre E2E-flödena och verksamhetens egna flöden. Risk 1, 7 och 9. |
| EX2 | Ja | Ja | Ja | Ja | Ja | Samma prioritetsnivåer som i SIT. |
| EX3 | Ja | Nej → Ja | Nej → Ja | Ja | Ja | Förbättrad, se nedan. Risk 9 och 10. |
| EX4 | Ja | Ja | Ja | Ja | Ja | Ledningen vet vilka fel som finns kvar vid release. |
| EX5 | Ja | Ja | Ja | Ja | Ja | Ger underlag för Go/No-Go-beslutet. |
| EX6 | Ja | Ja | Ja | Ja | Ja | Mindre viktiga scenarier kan accepteras efter riskbedömning. |
| EX7 | Ja | Nej → Ja | Nej → Ja | Ja | Ja | Förbättrad, se nedan. |

### Förbättrade formuleringar

Tabellerna i Uppgift 3 innehåller redan de förbättrade formuleringarna.

| # | Före | Problem | Efter |
|---|---|---|---|
| EN4 | Verksamheten är tillgänglig för acceptanstest. | Det framgick inte vilka personer eller hur länge, så det gick inte att avgöra om kriteriet var uppfyllt. | ...bokade med namn för hela testveckan: minst två från kundservice och en administratör. |
| EX3 | Kundservice är nöjd med systemet. | "Nöjd" är subjektivt och går inte att mäta. | Kundservice har själva verifierat att de kan söka kund, se order och betalningsstatus, avbryta order och initiera återbetalning utan manuella extrasteg. |
| EX7 | Verksamhetens synpunkter på användbarhet är dokumenterade. | Synpunkter är subjektiva, och det gick inte att avgöra när kriteriet var uppfyllt. | Alla deltagare har lämnat sina synpunkter i ett gemensamt formulär, och varje synpunkt har en ansvarig och ett beslut. |
