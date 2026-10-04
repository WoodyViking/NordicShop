
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
Systemtest ska verifiera hela systemet från början till slut, och det går bara om integrationerna fungerar. Om kritiska defekter från SIT finns kvar blir testfall blockerade, och testarnas begränsade tid går åt till att felsöka integrationer i stället för att verifiera funktionalitet. Kriteriet hindrar att problem flyttas vidare till en dyrare nivå och skyddar tidsplanen.

### 2. X1 Kritiska testfall är passerade
Kritiska testfall täcker de flöden som webbshopen inte kan fungera utan, till exempel inloggning, kundvagn, checkout och order. Om de inte är passerade vet vi inte om systemet fungerar, och verksamheten skulle få testa en version där huvudflöden brister i acceptanstestet. Det kan göra att kritiska fel upptäcks för sent för att hinna åtgärdas före release.

### 3. X3 Betalningsflöden testade mot leverantörens testmiljö
Betalning är webbshopens mest affärskritiska flöde: ett fel stoppar intäkterna direkt. Risken är dessutom stor, eftersom det beror på en extern leverantör vars testmiljö kan bli försenad... Stubbar täcker inte allt (till exempel callbacks, autentisering och återbetalning), så de kan inte ersätta test mot den riktiga miljön. Kriteriet gör att betalningstestet inte kan gå förbi Go/No-Go utan ett medvetet beslut.

---

## Kontrollera kvaliteten


Frågor: Är det tydligt? Är det mätbart? Går det att avgöra om det är uppfyllt? Är det relevant för systemtest? Är det kopplat till risk?
 

| Nr | Tydligt | Mätbart | Avgörbart | Relevant | Risk | Problem | Åtgärd |
|---|---|---|---|---|---|---|---|
| E1 | Nej | Nej | Nej | Ja | Ja | "Kritisk" och "affärsblockerande" är odefinierade. | Beskriv effekten direkt: blockerar ett affärsflöde eller saknar workaround. Lägg till undantagsregel. |
| E2 | Nej | Nej | Ja | Ja | Ja | Vilken version? Hur vet vi att miljön fungerar? | Lägg till version och röktest. |
| E3 | Nej | Nej | Nej | Ja | Ja | "Redo" går inte att mäta. | Ange vilka flöden, hur mycket och vem kontrollerar. |
| E4 | Nej | Ja | Nej | Ja | Ja | Godkänd av vem? Testplanen för vilken nivå? | Ange godkännare och att det är systemtestets plan. |
| E5 | Ja | Ja | Ja | Ja | Ja | Fungerar, men var och för vem listas de? | Förtydliga var och när. |
| E6 | Ja | Ja | Nej | Ja | Ja | Ett löfte, inte verifierat. | Kräv att rutinen finns och har provats. |
| X1 | Nej | Nej | Nej | Ja | Ja | Vilka är kritiska? Alla eller de flesta? | Namnge de kritiska flödena och kräv lösta. |
| X2 | Nej | Nej | Nej | Ja | Ja | För vilka roller? Vilka testfall? | Ange alla roller och att alla behörighetstestfall passerat. |
| X3 | Nej | Nej | Nej | Ja | Ja | Vilka flöden? Vad är "kritiska"? | Ange betalsätt, avbruten betalning och felflöden, och att alla testfall passerat. |
| X4 | Nej | Ja | Nej | Ja | Ja | "Mindre" är odefinierat. | Beskriv effekten: defekter som inte blockerar något affärsflöde. Kräv skriftligt PO-godkännande. |
| X5 | Nej | Ja | Nej | Ja | Ja | "Större" är odefinierat. | Beskriv effekten: blockerar ett affärsflöde eller saknar workaround. |
| X6 | Nej | Nej | Nej | Ja | Ja | Vilken dokumentation, var och när? | Ange vad, var och senast när. |



### Förbättrade kriterier

| Nr | Förbättrat kriterium | Obligatoriskt/Önskvärt | Risk som kriteriet hanterar |
|---|---|---|---|
| E1 | Inga öppna defekter från SIT som blockerar ett affärsflöde eller saknar workaround. Undantag kräver testledarens skriftliga godkännande. | Obligatoriskt | Blockerade testfall och felsökning av integrationer. |
| E2 | Systemtestmiljön är deployad med den avsedda versionen och röktest är passerat till godkändnivå. | Obligatoriskt | Testresultat blir ogiltiga på grund av fel version eller instabil miljö. |
| E3 | Testdata för huvudflödena (konto, produkt, kundvagn, order, lager, leverans) är laddad och stickprovskontrollerad. | Obligatoriskt | Falska resultat eller blockerade flöden på grund av data. |
| E4 | Teststrategi och systemtestets testplan är godkända av testledaren och Product Owner. | Önskvärt | Testarna arbetar utan gemensam plan. |
| E5 | Alla öppna defekter från SIT är listade i defektverktyget och delade med testarna före teststart. | Önskvärt | Dubbelrapportering av kända fel. |
| E6 | Rutin för att återställa testdata till utgångsläget finns och har provats, och återställningen tar högst en arbetsdag. | Önskvärt | Förstörd testdata stoppar retest och omkörning. |
| X1 | Alla testfall för kritiska affärsflöden (inloggning, kundvagn, checkout, order) är exekverade och till 100 % passerade. | Obligatoriskt | Kritiska fel går vidare till acceptanstest. |
| X2 | Behörighetstest är genomfört för alla roller (kund, administratör, kundtjänst) och alla behörighetstestfall är passerade. | Obligatoriskt | Obehöriga får åtkomst eller behöriga nekas. |
| X3 | Betalningsflödena (alla betalsätt, avbruten betalning och felflöden) är testade mot leverantörens testmiljö och alla betalningstestfall är passerade. | Obligatoriskt | Fel i betalning upptäcks först i produktion. |
| X4 | Alla öppna defekter som inte blockerar något affärsflöde har en beslutad hantering (fixas före eller efter release), skriftligt godkänd av Product Owner. | Önskvärt | Okända kvarstående defekter. |
| X5 | Inga nya defekter som blockerar ett affärsflöde eller saknar workaround har hittats under de senaste 3 testdagarna. | Önskvärt | Systemet är fortfarande instabilt. |
| X6 | Testresultat, testfallsstatus och defektlista är uppdaterade i testverktyget senast sista testdagen, och testrapporten är arkiverad. | Önskvärt | Resultat går inte att spåra eller återanvända. |
 
### Kontroll efter förbättring
 
| Nr | Tydligt | Mätbart | Avgörbart | Relevant | Risk |
|---|---|---|---|---|---|
| E1 | Ja | Ja | Ja | Ja | Ja |
| E2 | Ja | Ja | Ja | Ja | Ja |
| E3 | Ja | Ja | Ja | Ja | Ja |
| E4 | Ja | Ja | Ja | Ja | Ja |
| E5 | Ja | Ja | Ja | Ja | Ja |
| E6 | Ja | Ja | Ja | Ja | Ja |
| X1 | Ja | Ja | Ja | Ja | Ja |
| X2 | Ja | Ja | Ja | Ja | Ja |
| X3 | Ja | Ja | Ja | Ja | Ja |
| X4 | Ja | Ja | Ja | Ja | Ja |
| X5 | Ja | Ja | Ja | Ja | Ja |
| X6 | Ja | Ja | Ja | Ja | Ja |
