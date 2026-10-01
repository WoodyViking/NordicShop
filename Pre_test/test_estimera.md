
# Estimering

---

| De 20 funktionerna | Risk | Motivation |
|---|---|---|
| 1. Registrera konto | Medium | Är viktigt men inte är något som behövs för att kunden ska kuna handla |
| 2. Login | Hög | Är säkerhets relaterat och viktigt att det inte går fel med inloggning |
| 3. Lås konto efter tre felaktiga loginförsök | Hög | | Är säkerhets relaterat och viktigt att det inte går att bruteforca |
| 4. Återställ lösenord | Hög | | Är säkerhets relaterat och viktigt att det inte går fel med att kunna återställa ett lösenord |
| 5. Produktsökning | Låg | Icke affärs kritisk, kunden behöver ha mer sökalternativ för att ta sig till produkter |
| 6. Produktfilter | Låg | Icke affärs kritisk, kunden behöver ha mer sökalternativ för att ta sig till produkter |
| 7. Produktinformation | Låg | Är inte för viktigt att kunden kan se information om produkter som dem kanske redan vet om, men påverkar kunder som vill veta mer |
| 8. Kundvagn | Hög | Affärs kritist att happy path för köp fungerar |
| 9. Rabattkod | Låg | Inte för viktig att den fungerar direkt i release utan kan  |
| 10. Checkout | Hög | Är viktigt att pengarna rullar in och då måste checkouten fungera korrekt |
| 11. Kortbetalning | Hög | De flesta använder kort så är viktigt att det fungerar |
| 12. Swishbetalning | Hög | Det blir mer populärt med swish så är viktigt att det fungerar |
| 13. Orderskapande | Hög | Är viktigt att kunden vet om det fins produkter att köpa i lagret |
| 14. Lageruppdatering | Hög | Är viktigt att kunden vet om det fins produkter att köpa i lagret |
| 15. Leveransalternativ | Medium | Är viktigt för kunden att det finns alternativ för leverans |
| 16. Orderbekräftelse via e-post | Hög | Är viktigt att kunden kan veta att deras beställning har gått igenom |
| 17. Orderhistorik | Låg | Det är inte så viktigt att kunden kan kolla tillbaka på gamla beställningar |
| 18. Avbeställning | Hög | Är bra för kunden att kunna avbeställa saker dem besällt om dem ångrar sig och inte får något dem inte vill ha |
| 19. Återbetalning | Hög | Kunden måste få sina pengar tillbaka om dem gör en avbeställning och inte få fel summa |
| 20. Behörigheter för kundservice och admin | Hög | Säkerhets risk om behörigheterna inte fungerar och inte går för admin att utföra sina saker |

---
 
| Funktion | Analys | Testdesign | Testdata | Genomförande | Regression | Felomtest | Totalt |
|---|---|---|---|---|---|---|---|
| Registrera konto | 2 | 3 | 1 | 4 | 2 | 1 | 11 |
| Login | 1 | 3 | 1 | 4 | 1 | 2 | 12 |
| Lås konto | 2 | 2 | 1 | 1 | 1 | 2 | 9 |
| Återställ lösenord | 3 | 4 | 2 | 4 | 3 | 2 | 18 |
| Produktsökning | 1 | 2 | 1 | 4 | 2 | 1 | 11 |
| Produktfilter | 2 | 2 | 2 | 2 | 2 | 2 | 12 |
| Produktinformation | 1 | 1 | 1 | 2 | 1 | 1 | 7 |
| Kundvagn | 5 | 6 | 3 | 8 | 4 | 3 | 29 |
| Rabattkod | 2 | 1 | 1 | 1 | 1 | 1 | 7 |
| Checkout | 3 | 5 | 6 | 4 | 6 | 2 | 26 |
| Kortbetalning | 4 | 5 | 3 | 8 | 4 | 4 | 28 |
| Swishbetalning | 3 | 4 | 2 | 4 | 3 | 2 | 18 |
| Orderskapande | 3 | 5 | 2 | 6 | 4 | 2 | 22 |
| Lageruppdatering | 4 | 7 | 3 | 10 | 6 | 3 | 33 |
| Leveransalternativ | 2 | 2 | 1 | 4 | 1 | 1 | 11 |
| Orderbekräftelse | 1 | 3 | 2 | 4 | 2 | 2 | 14 |
| Orderhistorik | 1 | 2 | 1 | 3 | 1 | 1 | 9 |
| Avbeställning | 3 | 6  | 3 | 8 | 5 | 4 | 29 |
| Återbetalning | 4 | 5 | 3 | 8 | 5 | 4 | 29 |
| Behörigheter | 3 | 6  | 4 | 8 | 5 | 3 | 29 |
| **TOTALT** | 50 | 74 | 43 | 97 | 59 | 43 | 364 |

---

## Uppgift 3 – Beskriv hur ni estimerade
 
För minst fem funktioner ska ni beskriva vilken metod ni använde.
 
1. Återbetalning 
vi är oerfarna testare

2. Login
Vi är oerfarna

3. Lageruppdatering
Three-point

4. Swishbetalning
Three-point

5. Behörighet
Vi använde WBS där vi bröt ner arbetet i roller

---

## Uppgift 4 – Three-Point Estimation
 
Välj tre funktioner med hög osäkerhet.
 
För varje funktion uppskattar ni:
 
- Optimistic
- Most Likely
- Pessimistic

| Funktion | O | M | P | Viktat estimat |
|---|---|---|---|---|
| Lageruppdatering | 25 | 33 | 40 | 33 |
| Swishbetalning | 10 | 18 | 26 | 18 |
| Återbetalnng | 21 | 29 | 37 | 29 |
 
Använd:
 
```
(O + 4M + P) / 6
```

---

## Uppgift 5 – Buffert
 
Diskutera vilka osäkerheter projektet har.
 
Exempel:
 
- externa integrationer
- gemensam testmiljö
- gammalt lagersystem
- testdata
- många team
- förväntade defekter
Bestäm sedan:
 
Behöver ni en buffert?

Om ja:
 
- hur stor?
- varför?
- vilka osäkerheter ska bufferten hantera?
Bufferten ska motiveras.

20%
Vi är oerfarna


---

## Uppgift 6 – Kapacitetsplanering
 
Anta att varje testare har:
 
30 effektiva testtimmar per vecka.
 
Ni har:
 
4 testare.
 
Beräkna:
 
- **A.** Hur många effektiva testtimmar har teamet per vecka?
120 per vecka

- **B.** Hur många veckor krävs för ert estimerade testarbete?
3,64 veckor

- **C.** Är planen realistisk?
Nej eftersom vi är oerfarna så kommer det att gå långsammare

- **D.** Vilka antaganden bygger er plan på?
Att ingen blir sjuk, att lärarna har förberet oss för alla problem som vi kommer stöta på i arbetet.
Att testmiljön fungerar som förväntat. 

---

## Uppgit 7 - Planer om

1. 364+buffert=480h
2. 480-109=371h
3. 371-364=7h så 7h extra har vi, om vi klarar av utan buffert tiden
En av de fyra testarna försvinner med omedelbar verkan. Releasedatumet är oförändrat.

**1. Hur mycket kapacitet hade ni tidigare?**
4 testare × 30 timmar × 4 veckor = **480 timmar**

**2. Hur mycket kapacitet har ni nu?**
3 testare × 30 timmar × 4 veckor = **360 timmar**
Vi har förlorat 120 timmar, alltså 25 % av kapaciteten.

**3. Hur många timmar saknas för att genomföra ursprunglig plan?**
Ursprunglig plan inklusive buffert: 439 timmar
Ny kapacitet: 360 timmar
**Saknas: 439 − 360 = 79 timmar**

Även utan buffert räcker kapaciteten inte: 366 − 360 = 6 timmar saknas. Vi skulle då dessutom inte ha någon buffert alls, trots att projektet har stora osäkerheter.

**4. Hur påverkas tidsplanen?**
Med 3 testare har vi 90 timmar per vecka. Den ursprungliga planen skulle då ta 439 / 90 = **4,9 veckor**, alltså nästan 5 veckor i stället för 4. Vi skulle bli ungefär en vecka sena. Eftersom releasedatumet ligger fast måste vi i stället minska testomfattningen.

**Vårt mål:** Minska testarbetet till cirka 300 timmar, så att vi har ungefär 20 % buffert kvar inom 360 timmar.

---
---

## Uppgift 8 - Prioritera om

| Funktion | Risk | MUST/SHOULD/COULD | Ny testomfattning | Motivering |
|---|---|---|---|---|
| Lås konto | Hög | MUST | 9 h (oförändrat) | Säkerhetsrisk. Brute force-attacker kan inte rättas i efterhand. |
| Kundvagn | Hög | MUST | 29 h (oförändrat) | Del av happy path för köp. |
| Checkout | Hög | MUST | 26 h (oförändrat) | Utan checkout ingen försäljning. |
| Kortbetalning | Hög | MUST | 28 h (oförändrat) | De flesta kunder betalar med kort, och fel kostar pengar direkt. |
| Swishbetalning | Hög | MUST | 18 h (oförändrat) | Extern integration med hög osäkerhet. |
| Orderskapande | Hög | MUST | 22 h (oförändrat) | Risk att kunden betalar men ingen order skapas. |
| Lageruppdatering | Hög | MUST | 33 h (oförändrat) | Gammalt system med störst teknisk osäkerhet. |
| Avbeställning | Hög | MUST | 29 h (oförändrat) | Flera steg i flera system måste lyckas. |
| Återbetalning | Hög | MUST | 29 h (oförändrat) | Gäller kundens pengar. |
| Behörigheter | Hög | MUST | 29 h (oförändrat) | Säkerhetsrisk om kundservice kan ändra priser eller behörigheter. |
| Login | Hög | SHOULD | 8 h (från 12) | Testas även indirekt i alla E2E-flöden, eftersom kunden loggar in i varje köp. |
| Återställ lösenord | Hög | SHOULD | 9 h (från 18) | Huvudscenario och test av att återställningslänken slutar gälla. Kundservice kan hjälpa till i nödläge. |
| Orderbekräftelse | Hög | SHOULD | 8 h (från 14) | Kontroll av att e-post skickas med rätt innehåll. Kan skickas manuellt i nödläge. |
| Registrera konto | Medium | SHOULD | 7 h (från 13) | Huvudscenario och viktigaste felfall. Testas även via E2E. |
| Leveransalternativ | Medium | SHOULD | 7 h (från 11) | Hemleverans och ombud i standardfall. Färre varianter. |
| Produktsökning | Låg | COULD | 3 h (från 11) | Kort utforskande testsession. |
| Produktfilter | Låg | COULD | 2 h (från 12) | Snabb kontroll av de vanligaste filtren. |
| Produktinformation | Låg | COULD | 2 h (från 7) | Kontrolleras indirekt via köpflödet. |
| Rabattkod | Låg | COULD | 2 h (från 7) | Snabb kontroll av en giltig och en ogiltig kod. Rabattkoder bör inte aktiveras vid lansering. |
| Orderhistorik | Låg | COULD | 2 h (från 9) | Kort kontroll av att kundens ordrar visas. |
## Uppgift 9 – Vad reducerar ni?

Ni måste nu bestämma om ni reducerar:

- analys
- testdesign
- testdata
- testgenomförande
- regression
- felomtest
Var försiktiga.

Exempel:

Att säga:

> "Vi tar bort allt felomtest."

kan skapa mycket hög risk eftersom rättade kritiska defekter då inte verifieras.

Diskutera därför:

Vad kan faktiskt reduceras utan att skapa oacceptabel risk?

**Analys – reduceras lite.**
För SHOULD- och COULD-funktioner återanvänder vi analysen från vår tidigare riskanalys och kravgenomgång. MUST-funktionerna analyseras fullt ut.

**Testdesign – reduceras för SHOULD och COULD.**
För COULD-funktioner skriver vi inga detaljerade testfall, utan använder checklistor och utforskande testning. För SHOULD-funktioner designar vi färre varianter.

**Testdata – reduceras något.**
Vi använder en gemensam uppsättning testdata för flera funktioner i stället för separat testdata per funktion. Testdata för lager och betalning, till exempel saldo 0 och 1, testkort och Swish-nummer, behålls fullt ut.

**Testgenomförande – reduceras för SHOULD och COULD.**
SHOULD-funktioner testas med huvudscenario och de viktigaste felfallen. COULD-funktioner testas i korta utforskande sessioner. MUST-funktioner testas enligt plan.

**Regression – reduceras för SHOULD och COULD, men aldrig för MUST.**
MUST-funktionerna regressionstestas fullt ut, helst automatiserat. SHOULD-funktionerna får ett kort röktest. COULD-funktionerna regressionstestas inte.

**Felomtest – reduceras inte för allvarliga fel.**
Alla rättade kritiska och allvarliga defekter måste omtestas. Annars vet vi inte om felet faktiskt är rättat, och vi riskerar att släppa ett system med kända kritiska fel. Det enda vi kan reducera är omtest av mindre kosmetiska fel, som kan samlas och omtestas tillsammans om tid finns.

**Det vi inte kan reducera utan oacceptabel risk:**
Testgenomförande, regression och felomtest för MUST-funktionerna. Det är där pengar, säkerhet och kundförtroende står på spel.

---

## Uppgift 10 – Presentera för projektledaren

Ni ska nu agera testledare.

Projektledaren säger:

> "Releasedatumet ligger fast. Kan ni fortfarande hinna?"

Förbered ett svar på 2–3 minuter.

Svaret ska innehålla:

1. Vad har förändrats?
2. Hur påverkas kapaciteten?



