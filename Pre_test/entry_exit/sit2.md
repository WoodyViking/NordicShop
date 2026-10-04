
## Systemtest

| Nr | Entry Criteria | Obligatorisk/Önskevärt |
|---|---|---|
| E1 | Inga kritiska eller affärsblockerande defekter från tidigare testnivå | Obligatorisk |
| E2 | Systemtestmiljön är deployad. | Obligatorisk |
| E3 | Testdata för huvudflöden är redo. | Obligatorisk |
| E4 | Teststrategi och testplan är godkänd. | Önskevärt |
| E5 | All öppna defekter från SIT är listade så att kända fel inte rapporteras igen. | Önskevärt |
| E6 | Testdata kan återställas till utgångsläget på en dag. | Önskevärt |

| Nr | Exit Criteria | Obligatorisk/Önskevärt |
|---|---|---|
| X1 | Kritiska testfall är passerade | Obligatorisk. |
| X2 | Behörighetstest har genomförts och passerat. | Obligatorisk |
| X3 | Betalingsflöden är testade mot leverantörens testmiljö och kritiska testfall passerade. | Obligatorisk |
| X4 | Alla mindre defekter har beslutad hantering som är godkänd av PO. | Önskevärt |
| X5 | Inga nya större defekter har hittats dem senaste 3 testdagarna. | Önskevärt |
| X6 | Dokumentation för testresultat, testfallsstatus och defektlista är uppdaterade. | Önskevärt |

---

## Motivera
### 1. E1 Inga kritiska eller affärsblockerande defekter från tidigare testnivå
Systemtest ska verifiera hela systemet från början till slut, och det går bara om integrationerna mellan Team 1–3 fungerar. Om kritiska defekter från SIT finns kvar blir testfall blockerade, och testarnas begränsade tid (cirka tre veckor, V6–V8) går åt till att felsöka integrationer i stället för att verifiera funktionalitet. Kriteriet hindrar att problem flyttas vidare till en dyrare nivå och skyddar tidsplanen.

### 2. X1 Kritiska testfall är passerade
Det här är systemtestets viktigaste kvalitetsgrind. Kritiska testfall täcker de flöden som webbshopen inte kan fungera utan, till exempel inloggning, kundvagn, checkout och order. Om de inte är passerade vet vi inte om systemet fungerar, och verksamheten skulle få testa en version där huvudflöden brister i acceptanstestet. Det slösar verksamhetens begränsade tid (tidigast V9) och gör att kritiska fel upptäcks för sent för att hinna åtgärdas före release.

### 3. X3 Betalningsflöden testade mot leverantörens testmiljö
Betalning är webbshopens mest affärskritiska flöde: ett fel stoppar intäkterna direkt. Det är också där risken är störst, eftersom det beror på en extern leverantör vars testmiljö är försenad. Stubbar täcker inte allt (till exempel callbacks, autentisering och återbetalning), så de kan inte ersätta test mot den riktiga miljön. Kriteriet gör att betalningstestet inte kan glida förbi Go/No-Go utan ett medvetet beslut.

varför?

---

## Kontrollera kvaliteten


Frågor: Är det tydligt? Är det mätbart? Går det att avgöra om det är uppfyllt? Är det relevant för systemtest? Är det kopplat till risk?
 
| Nr | Tydligt | Mätbart | Avgörbart | Relevant | Risk | Problem | Åtgärd |
|---|---|---|---|---|---|---|---|
| E1 | Nej | Nej | Nej | Ja | Ja | "Kritisk" och "affärsblockerande" är odefinierade. | Definiera med P1/P2 och undantagsregel. |
| E2 | Nej | Nej | Ja | Ja | Ja | Vilken version? Hur vet vi att miljön fungerar? | Lägg till version och röktest. |
| E3 | Nej | Nej | Nej | Ja | Ja | "Redo" går inte att mäta. | Ange vilka flöden, hur mycket och vem kontrollerar. |
| E4 | Nej | Ja | Nej | Ja | Ja | Godkänd av vem? Testplanen för vilken nivå? | Ange godkännare och att det är systemtestets plan. |
| E5 | Ja | Ja | Ja | Ja | Ja | Fungerar, men var och för vem listas de? | Förtydliga var och när (i defektverktyget, före teststart). |
| E6 | Ja | Ja | Nej | Ja | Ja | Ett löfte, inte verifierat. | Kräv att rutinen finns och har provats. |
| X1 | Nej | Nej | Nej | Ja | Ja | Vilka är kritiska? Alla eller de flesta? | Ange 100 % och källa för vad som är kritiskt. |
| X2 | Nej | Nej | Nej | Ja | Ja | För vilka roller? Vilka testfall? | Ange alla roller och att alla behörighetstestfall passerat. |
| X3 | Nej | Nej | Nej | Ja | Ja | Vilka flöden? Vad är "kritiska"? | Ange betalsätt, avbruten betalning, felflöden och 100 % kritiska. |
| X4 | Nej | Ja | Nej | Ja | Ja | "Mindre" är odefinierat. | Definiera som P3/P4, och kräv skriftligt PO-godkännande. |
| X5 | Nej | Ja | Nej | Ja | Ja | "Större" är odefinierat. | Definiera som P1/P2. |
| X6 | Nej | Nej | Nej | Ja | Ja | Vilken dokumentation, var och när? | Ange vad, var och senast när. |

Om svaret är nej:
Förbättra formuleringen




