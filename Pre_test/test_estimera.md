
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
3,03 veckor

- **C.** Är planen realistisk?
Nej eftersom vi är oerfarna så kommer det att gå långsammare

- **D.** Vilka antaganden bygger er plan på?
Att ingen blir sjuk, att lärarna har förberet oss för alla problem som vi kommer stöta på i arbetet.
Att testmiljön fungerar som förväntat. 


