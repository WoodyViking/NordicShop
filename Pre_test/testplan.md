# MALL FÖR TESTPLAN

**\<Företagsnamn>**  
\<Projektnamn>  
Testplan för  NordicShop  
**Version 0.1**

## Dokumenthistorik

| **Version** | **Datum** | **Författare** | **Kommentar** |
| --- | --- | --- | --- |
| \<0.1> | \<2026-09-24> | \<Grupp 2> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |

*Använd mallen som ett styrande dokument för ett specifikt testuppdrag, en release eller en testperiod. Ersätt all text inom \<hakparenteser> och anpassa avsnitten efter projektets behov.*

# Innehåll

- [1 Unik identifiering](#1--unik-identifiering)
- [2 Inledning](#2--inledning)
  - [2.1 Kortfattad beskrivning](#21--kortfattad-beskrivning)
  - [2.2 Bakgrund](#22--bakgrund)
  - [2.3 Syfte och mål](#23--syfte-och-mål)
  - [2.4 Termer och förkortningar](#24--termer-och-förkortningar)
  - [2.5 Hänvisningar till andra dokument](#25--hänvisningar-till-andra-dokument)
  - [2.6 Öppna frågor](#26--öppna-frågor)
- [3 Testobjekt](#3--testobjekt)
- [4 Omfattning](#4--omfattning)
- [5 Avgränsning](#5--avgränsning)
- [6 Tillvägagångssätt](#6--tillvägagångssätt)
  - [6.1 Iterationer](#61--iterationer)
- [7 Start- och slutkriterier](#7--start--och-slutkriterier)
  - [7.1 Kriterier för att inleda testarbetet](#71--kriterier-för-att-inleda-testarbetet)
  - [7.2 Kriterier för att avsluta testarbetet](#72--kriterier-för-att-avsluta-testarbetet)
- [8 Avbrytande- och återupptagandekriterier](#8--avbrytande--och-återupptagandekriterier)
  - [8.1 Kriterier för att avbryta testerna](#81--kriterier-för-att-avbryta-testerna)
  - [8.2 Kriterier för att återuppta testarbetet](#82--kriterier-för-att-återuppta-testarbetet)
- [9 Testdokumentation](#9--testdokumentation)
- [10 Testaktiviteter](#10--testaktiviteter)
- [11 Testmiljö](#11--testmiljö)
  - [11.1 Hård- och mjukvara](#111--hård--och-mjukvara)
  - [11.2 Testverktyg](#112--testverktyg)
  - [11.3 Lokaler](#113--lokaler)
- [12 Ansvar](#12--ansvar)
- [13 Resurs- och utbildningsbehov](#13--resurs--och-utbildningsbehov)
- [14 Tidplan](#14--tidplan)
  - [14.1 Första testomgången](#141--första-testomgången)
  - [14.2 Påföljande testomgångar](#142--påföljande-testomgångar)
- [15 Risker och oförutsedda händelser](#15--risker-och-oförutsedda-händelser)
- [16 Godkännande av testplanen](#16--godkännande-av-testplanen)

# 1  Unik identifiering

*Ange ett unikt ID för testplanen, exempelvis projekt-/systemprefix + löpnummer eller versions-ID.*

\<Beskriv här>




# 2  Inledning

*Beskriv sammanhanget för testplanen och vad dokumentet ska styra.*

\<Beskriv här>

## 2.1  Kortfattad beskrivning

*Sammanfatta vilken testinsats planen avser, vilken release/version som testas, målgrupp samt vem som ansvarar för dokumentet.*

\<Beskriv här>

## 2.2  Bakgrund

*Beskriv projektets eller förändringens bakgrund, verksamhetsbehovet och varför testningen genomförs.*

\<Beskriv här>

## 2.3  Syfte och mål

*Beskriv vad testerna ska verifiera och vilka konkreta mål som ska vara uppnådda efter avslutad testperiod.*

\<Beskriv här>

## 2.4  Termer och förkortningar

*Förklara projektspecifika termer, förkortningar, verktygsnamn och begrepp som behövs för att förstå testplanen.*

| **Term** | **Förklaring** |
| --- | --- |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| Felrapport | Ett registrerat ärende för ett identifierat fel. |
| Testverktyg | Verktyg som används för krav-, test- och felhantering. |
| \<Term\> | \<Förklaring\> |
| E2E | Ett testflöde som verifierar en hel kedja av steg, från kundens handling till att alla inblandade system har reagerat korrekt. |
| API | Application Programming Interface. Gränssnitt som system använder för att kommunicera med varandra, t.ex. mellan order service och externa leverantörer. |
| Regression | Testning som säkerställer att ny eller ändrad kod inte har förstört tidigare fungerande funktionalitet. |
| Testmiljö | En miljö avsedd för test, separat från produktion, där system och integrationer kan verifieras utan att påverka riktiga kunder eller data. |
| Mock | En förenklad, konstgjord verision av ett system (t.ex. en betalningsleverantör) som används i test när det riktiga systemet inte är tillgängligt eller lämpligt eller att testa mot. |


## 2.5  Hänvisningar till andra dokument

*Lista relevanta styrande eller stödjande dokument, till exempel kravspecifikation, projektplan, teststrategi, felhanteringsprocess och testspecifikationer.*

| **Dokument** | **Beskrivning / sökväg / länk** |
| --- | --- |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| Testplan | \<Länk eller sökväg till testplan\> |
| Fil med testdata | \<Länk eller sökväg till testdata\> |
| SQL-skript | \<Länk eller sökväg till skript\> |
| Testfall | <test_fall.md> |
| Krav | krav.md |



## 2.6  Öppna frågor

*Lista frågor eller beslut som ännu inte är lösta och som kan påverka testplanen.*

| **Fråga** | **Ansvarig** | **Senast datum** | **Status** |
| --- | --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 3  Testobjekt

*Beskriv vad som ska testas: system, delsystem, funktioner, integrationer, API:er, batchjobb, rapporter eller andra komponenter. Ange gärna version/build och ägare.*

| **Testobjekt** | **Beskrivning** | **Version / build** |
| --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 4  Omfattning

*Beskriv vad som ingår i testningen. Koppla gärna till krav, affärsflöden, testnivåer, testtyper och prioriterade områden.*

\<Beskriv här>

| **Område / flöde** | **Testnivå / testtyp** | **Prioritet** | **Kommentar** |
| --- | --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 5  Avgränsning

*Beskriv uttryckligen vad som inte ska testas i denna testinsats och varför. Ange vid behov vem som ansvarar för testningen utanför denna plan.*

| **Avgränsning** | **Motivering** | **Ansvar utanför planen** |
| --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 6  Tillvägagångssätt

*Beskriv hur testningen ska genomföras, exempelvis riskbaserat, kravbaserat, utforskande eller iterativt. Beskriv prioritering, felhantering, omtest, regression, rapportering och eventuell automatisering.*

**Riskbaserat.** Prioriteringen följer MUST/SHOULD/COULD i kapitel 4 och riskerna i `test_analys.md`. De största riskerna är det gamla lagersystemet (risk 1), den delade testmiljön (risk 2), betalningsleverantörens testmiljö (risk 3), kontolåsningen (risk 6) och den minskade testkapaciteten (risk 11).

**Testnivåer.** Komponent-/enhetstest görs av utvecklingsteamen. Testteamet genomför SIT och systemtest. Verksamheten genomför acceptanstest med stöd av testteamet. Varje nivå har entry- och exit-kriterier (kapitel 7).

**Testtyper.** Funktionell test och säkerhetstest behålls fullt ut. Prestanda, kompatibilitet och användbarhet reduceras (kapitel 5).

**Testdesign.**
- MUST: fullständiga testfall med positiva och negativa fall. Integrationerna testas alltid för nedtid, timeout, felaktig data och dubbla meddelanden.
- SHOULD: huvudscenario och de viktigaste felfallen.
- COULD: checklistor och utforskande test.
- Testtekniker: ekvivalensklasser och gränsvärden (rabattkod, kontolåsning, lagersaldo 0 och 1) samt tillståndsbaserade test för orderstatus.

**Testdata.** En gemensam uppsättning används för flera funktioner: minst 20 produkter med olika saldon (minst en med saldo 1), testkunder med orderhistorik, ordrar i status betald, skickad och avbeställd, samt konton för kundservice och administratör. Testkort och Swish-testnummer kommer från Payment Provider. Ingen riktig kunddata används (öppen fråga #14).

**Betalning.** I SIT används Payment Providers testmiljö, och en mock om den är otillgänglig. I systemtest krävs den riktiga testmiljön, eftersom en mock inte täcker återanrop, autentisering och återbetalning.

**Felhantering.** Fel registreras i defektverktyget med steg, förväntat och faktiskt resultat, build och loggar. Prioritet: Kritisk (blockerar ett affärsflöde, ingen workaround), Hög, Medel, Låg. Daglig defect triage leds av testledaren tillsammans med utvecklingsteamen.

**Omtest.** Alla rättade fel med prioritet Kritisk och Hög omtestas innan de stängs. Mindre kosmetiska fel kan samlas och omtestas tillsammans.

**Regression.** MUST-områden regressionstestas fullt ut, i första hand automatiserat. SHOULD-områden får ett kort röktest. COULD-områden regressionstestas inte.

**Automation (Förslag).** Utvecklingsteamen tar över mer av komponenttesterna och den automatiserade regressionen av MUST-flödena, så att testarna frigör tid. Röktest körs automatiskt vid varje driftsättning i den delade miljön.

**Rapportering.** Veckovis teststatus till projektledaren och Product Owner (körda, passerade och blockerade testfall, öppna fel per prioritet, risker). Testrapport efter SIT och systemtest. Slutrapport och Go/No-Go-underlag i V11.

## 6.1  Iterationer

*Beskriv testcykler/testomgångar och vad som sker i varje cykel, till exempel test, omtest och regression.*

| **Fas** | **Syfte** | **Genomförande** |
| --- | --- | --- |
| SIT | Verifiera integrationerna (lager, betalning, leverans, e-post/SMS) och de tre E2E-flödena. | V4–V6. Omtest löpande. |
| Systemtest | Verifiera hela systemet funktionellt och säkerhetsmässigt, inklusive behörigheter och betalning mot den riktiga testmiljön. | V6–V8. Omtest löpande. |
| Omtest | Verifiera rättade fel. | Löpande V5–V9, styrt av defect triage. |
| Regression | Säkerställa att rättningar inte förstört befintlig funktionalitet. | V8–V10. MUST fullt ut, SHOULD som röktest. |
| Acceptanstest | Verksamheten verifierar mot K1–K10 och sina egna arbetsflöden. | V9–V10. Koden fryses efter V9, därefter endast kritiska rättningar. |
| Release readiness och Go/No-Go | Slutrapport och beslutsunderlag. | V10–V11. |
| Release och sanity test | Produktionssättning och kontroll av de kritiska flödena i produktion. | V12. |

# 7  Start- och slutkriterier

*Definiera objektiva kriterier för när testningen får starta och när den kan betraktas som avslutad.*

## 7.1  Kriterier för att inleda testarbetet

- \<Testmiljö är installerad och tillräckligt stabil>
- \<Nödvändiga testdata finns tillgängliga>
- \<Krav/acceptanskriterier är tillräckligt tydliga>
- \<Överenskommen andel testfall är framtagna och granskade>

## 7.2  Kriterier för att avsluta testarbetet

- \<Planerade kritiska tester är genomförda>
- \<Inga öppna blockerande/kritiska fel över accepterad nivå>
- \<Överenskommen testtäckning och resultatnivå är uppnådd>
- \<Kvarstående risker är dokumenterade och accepterade>

# 8  Avbrytande- och återupptagandekriterier

*Definiera när testningen ska pausas eftersom fortsatt testning inte är meningsfull, samt vad som krävs för att återuppta den.*

## 8.1  Kriterier för att avbryta testerna

- \<Testmiljön är instabil eller otillgänglig>
- \<För många blockerande/kritiska fel>
- \<Nödvändiga nyckelpersoner, testdata eller beroenden saknas>
- \<Leveransen bedöms inte vara testbar>

## 8.2  Kriterier för att återuppta testarbetet

- \<Blockerande problem är åtgärdade och verifierade>
- \<Miljö och beroenden är åter stabila>
- \<Beslut om återstart är fattat av ansvarig roll>

# 9  Testdokumentation

*Beskriv vilka testartefakter som ska tas fram, var de lagras och vem som ansvarar för dem.*

| **Dokument / artefakt** | **Beskrivning** | **Ansvarig** |
| --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 10  Testaktiviteter

*Lista de viktigaste aktiviteterna från testanalys och planering till genomförande, felhantering, uppföljning och testrapport.*

| **ID** | **Aktivitet** | **Ägare** |
| --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 11  Testmiljö

*Beskriv testmiljön och viktiga skillnader mot produktion. Dokumentera integrationer, beroenden, testdata, åtkomst och ansvar.*

## 11.1  Hård- och mjukvara

| **Komponent** | **Version / konfiguration** | **Skillnad mot produktion** | **Ansvarig** |
| --- | --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |

## 11.2  Testverktyg

| **Verktyg** | **Användningsområde** | **Ansvarig** |
| --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |

## 11.3  Lokaler

*Beskriv särskilda lokaler, enheter eller fysisk utrustning som krävs. Om ej relevant, ange Ej applicerbart.*

\<Beskriv här>

# 12  Ansvar

*Tydliggör ansvar, mandat, eskaleringsvägar och vem som fattar beslut om exempelvis teststart, avbrott och Go/No-Go.*

| **Roll** | **Ansvar / mandat** | **Namn / funktion** |
| --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 13  Resurs- och utbildningsbehov

*Ange resurser, omfattning/tillgänglighet, funktion och eventuella utbildnings- eller onboardingbehov.*

| **Namn / resurs** | **Omfattning** | **Funktion** | **Organisation / team** |
| --- | --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 14  Tidplan

*Beskriv testperioden, viktiga milstolpar och planerade testomgångar. Anpassa efter projektets leveransmodell.*

| **Aktivitet / milstolpe** | **Start** | **Slut** | **Ansvarig** | **Kommentar** |
| --- | --- | --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |

## 14.1  Första testomgången

| **Fas** | **Varaktighet / datum** |
| --- | --- |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> |

## 14.2  Påföljande testomgångar

*Beskriv hur efterföljande testomgångar planeras, vad som återanvänds och hur omfattningen styrs av felutfall och risk.*

\<Beskriv här>

# 15  Risker och oförutsedda händelser

*Dokumentera risker som kan påverka testningen eller leveransen. Ange konsekvens/kommentar, förebyggande eller korrigerande åtgärd, ägare och prioritet.*

| **Risk** | **Konsekvens / kommentar** | **Åtgärd** | **Ägare** | **Prioritet** |
| --- | --- | --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |

# 16  Godkännande av testplanen

*Ange vilka roller/personer som ska godkänna testplanen och när godkännandet skedde.*

| **Namn / roll** | **Beslut** | **Datum** | **Kommentar** |
| --- | --- | --- | --- |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
| \<Fyll i> | \<Fyll i> | \<Fyll i> | \<Fyll i> |
