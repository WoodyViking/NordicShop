# WORKSHOP – Skapa Entry/Exit för NordicShop (Del 2)

# SCENARIOFÖRÄNDRING 1

Status inför systemtest:

- Testmiljön är tillgänglig.
- Rätt build är deployad.
- Testdata finns för 80 % av testerna.
- Betalningsintegrationen fungerar.
- Lagerintegrationen är instabil.
- Två high-defekter från SIT är fortfarande öppna.
- Ingen Critical-defekt är öppen.
- Systemtestet är planerat att börja imorgon.

---

# Uppgift 7 – Starta eller inte?

Besvara:

1. Är Entry Criteria uppfyllda?
  Nej.
2. Vilka är inte uppfyllda?
  ST-EN1, 
3. Kan systemtest starta delvis?
  Om det finns en workaround.
4. Vilka tester bör vänta?
  De tester som inte har testdata.
5. Vilken risk finns?
  Att man inte uppnår exit p.g.a. de 2 defekterna.
6. Vad kommunicerar ni till projektledaren?
   Att vi inte uppfyller kriterierna, så om det finns en workaround för ST-EN.
---

# Scenario 2 – Avsluta systemtest?

Status:

- 95 % av planerade tester är genomförda
- 97 % av genomförda tester är Passed
- alla kritiska E2E-flöden är genomförda
- inga Critical-defekter
- 3 High-defekter öppna
- en High-defekt påverkar återbetalning
- kritisk regression är klar
- 18 lågprioriterade tester är inte körda

---

# Uppgift 8 – Är Exit uppfyllt?

Diskutera:

1. Kan systemtestet avslutas?  
  Ja.
2. Vilken information behöver ni om de tre High-defekterna? 
  Påverkar de betalningsflödena? Att det inte hittades/upptäcktes något affärsflöde de    senaste dagarna.
3. Är 97 % Passed tillräckligt?
  Ja
4. Vilken roll spelar återbetalningsfelet?
   Att vi får lösa det manuellt via kundservice.
5. Finns det residual risk?
  
6. Vad rekommenderar ni?
  
