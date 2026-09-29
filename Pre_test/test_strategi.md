<<<<<<< HEAD
# Workshop – Skapa första versionen av NordicShops teststrategi

## Bakgrund

Ni arbetar vidare med **NordicShop-caset från föregående lektion**.

I förra workshopen analyserade ni projektet och identifierade bland annat:

- testobjekt
- kritiska affärsflöden
- integrationer
- stakeholders
- risker
- beroenden
- frågor som testledaren behöver få svar på

Nu ska ni använda den analysen för att skapa en **första version av NordicShops teststrategi**.

Ni ska använda den utdelade **Mallen för teststrategi**.

---

# Syfte med workshopen

Syftet är att träna på att gå från:

**Projektförståelse → Testanalys → Testbehov → Teststrategi**

Ni ska alltså inte börja skapa detaljerade testfall eller en detaljerad tidsplan.

Fokus ligger på:



> **Hur ska NordicShop övergripande testas?**

---

# Viktigt

Det finns inte ett enda korrekt sätt att utforma en teststrategi.

Olika grupper kan komma fram till olika lösningar.

Det viktiga är att ni kan:

- motivera era val
- koppla strategin till NordicShops risker
- skilja mellan olika testnivåer
- identifiera relevanta testobjekt
- identifiera miljöbehov
- synliggöra sådant ni ännu inte har tillräcklig information om

Om information saknas ska ni **inte hitta på svaret**.

Dokumentera istället frågan under: **Öppna frågor.**

---

# Uppgift

Skapa en första version av **Teststrategi för NordicShop** genom att fylla i följande delar av mallen.

---

# 1. Kortfattad beskrivning

Beskriv kort vad teststrategin gäller.

Texten ska ge läsaren en övergripande förståelse för:

- vilket system strategin gäller
- varför NordicShop utvecklas
- vilka delar lösningen består av
- vad strategin ska användas till

Omfattning:

**Cirka 5–8 meningar.**

### Tänk på

Detta är inte en detaljerad projektbeskrivning.

Läsaren ska snabbt förstå: Vad är NordicShop och vad beskriver denna teststrategi?

---

                                                                                                                                                                                                  39,1          10%


# 2. Termer och förkortningar

Identifiera termer och förkortningar som behöver förklaras för att dokumentet ska vara tydligt.

Ta med minst **5 termer/förkortningar**.

Använd mallens format:

| Term | Förklaring |
| --- | --- |
|  |  |
|  |  |

Det kan exempelvis finnas begrepp kring:

- E2E
- API
- regression
- testmiljö
- felrapport
- externa leverantörer

Välj själva vilka som är relevanta.

---

# 3. Hänvisningar till andra dokument

Identifiera vilka andra dokument eller underlag som teststrategin behöver hänvisa till.

Ni behöver inte ha faktiska länkar.

Ange istället vilka typer av dokument som bör finnas eller användas.

Använd exempelvis:

| Dokument | Beskrivning / sökväg |
| --- | --- |
|  |  |

Fundera på vilka dokument testledaren skulle behöva för att kunna förstå och genomföra strategin.

---

# 4. Öppna frågor

I NordicShop-caset finns information som saknas.

Identifiera minst **4 öppna frågor** som behöver besvaras för att teststrategin senare ska kunna färdigställas.

Använd mallens struktur:

| Öppen fråga | Ansvarig | Måldatum | Status |
                                                                                                                                                                                                  91,1          28%


| --- | --- | --- | --- |
|  |  |  | Öppen |
|  |  |  | Öppen |

Frågorna kan exempelvis handla om:

- testmiljö
- testdata
- prestandakrav
- säkerhetskrav
- externa leverantörer
- tillgänglighet
- tidigare regression
- automation
- produktionsmiljö
- ansvar
- releaseförutsättningar

### Viktigt

En bra testledare hittar inte på svar på sådant som är oklart.

Testledaren: **identifierar frågan, hittar rätt ansvarig och följer upp tills den är besvarad.**

---

# 5. Testnivåer

Detta är en av workshopens viktigaste delar.

Identifiera vilka **testnivåer** som behövs för NordicShop.

Ni ska ta ställning till exempelvis:

- komponent-/enhetstest
- integrationstest
- systemintegrationstest
- systemtest
- acceptanstest

Ni behöver inte använda alla nivåer automatiskt.

Välj de nivåer ni bedömer är relevanta och **motivera varför de behövs**.

För varje vald testnivå ska följande beskrivas:

---

## Syfte och mål

Vad ska testnivån verifiera?

Exempel på frågor:

                                                                                                                                                                                                  145,0-1       46%



- Vad vill vi upptäcka här?
- Vad ska vara verifierat när testnivån är färdig?
- Vilka risker adresseras?

---

## Ansvariga roller

Vilka genomför eller ansvarar för testningen?

Det kan exempelvis vara:

- utvecklare
- testare
- testledare
- verksamhetsrepresentanter
- externa leverantörer

---

## Omfattning

Vad ska testas på denna nivå?

Var tydliga med skillnaden mellan nivåerna.

Undvik att samma sak automatiskt testas på alla nivåer.

---

## Avgränsningar

Vad ingår **inte** på denna testnivå?

Fundera på: Vad verifieras istället på en annan nivå?

---

## Resultat / rapportering

Hur ska resultatet från testnivån följas upp?

Exempel:

- automatiserade testresultat
- teststatus
- felrapporter
- testprotokoll
- sammanfattning till testledare
- acceptansbeslut

---

                                                                                                                                                                                                  198,1         64%


---

# 6. Testmiljö

Beskriv vilken eller vilka testmiljöer NordicShop behöver.

Kom ihåg informationen från caset:

- tre utvecklingsteam arbetar parallellt
- det finns en gemensam testmiljö
- betalningsleverantören har en separat testmiljö
- lagersystemet är gammalt
- externa tjänster ingår

Använd mallens struktur:

| Miljö | Syfte | Viktiga skillnader mot produktion |
| --- | --- | --- |
|  |  |  |
|  |  |  |

Ni ska identifiera minst **två relevanta miljöer**.

---

## Fundera särskilt på

- Vilka system måste finnas tillgängliga?
- Vilka externa integrationer behövs?
- Hur hanteras betalningar?
- Vilken testdata behövs?
- Finns begränsningar?
- Hur skiljer sig miljön från produktion?
- Finns risk för att flera team påverkar varandra?

Om ni inte vet svaret:

> Lägg frågan under **Öppna frågor**.

---

# 7. Testobjekt

Identifiera vad som ska testas.

Ett testobjekt kan exempelvis vara:

- system
- systemdel
- tjänst
- funktion
- integration
- affärsområde

                                                                                                                                                                                                  250,0-1       82%


Använd mallens struktur:

| Testobjekt / område | Vad ska verifieras? | Kommentar / avgränsning |
| --- | --- | --- |
|  |  |  |
|  |  |  |

Identifiera minst **4 testobjekt/områden**.

---

## För varje testobjekt ska ni beskriv---

# 6. Testmiljö

Beskriv vilken eller vilka testmiljöer NordicShop behöver.

Kom ihåg informationen från caset:

- tre utvecklingsteam arbetar parallellt
- det finns en gemensam testmiljö
- betalningsleverantören har en separat testmiljö
- lagersystemet är gammalt
- externa tjänster ingår

Använd mallens struktur:

| Miljö | Syfte | Viktiga skillnader mot produktion |
| --- | --- | --- |
|  |  |  |
|  |  |  |

Ni ska identifiera minst **två relevanta miljöer**.

---

## Fundera särskilt på

- Vilka system måste finnas tillgängliga?
- Vilka externa integrationer behövs?
- Hur hanteras betalningar?
- Vilken testdata behövs?
- Finns begränsningar?
- Hur skiljer sig miljön från produktion?
- Finns risk för att flera team påverkar varandra?

Om ni inte vet svaret:

> Lägg frågan under **Öppna frågor**.

---

# 7. Testobjekt

Identifiera vad som ska testas.

Ett testobjekt kan exempelvis vara:

- system
- systemdel
- tjänst
- funktion
- integration
- affärsområde

                                                                                                                                                                                                  250,0-1       82%
a

### Vad ska verifieras?

Beskriv övergripande vilka egenskaper eller flöden som behöver verifieras.

### Kommentar / avgränsning

Beskriv exempelvis:

- vad som inte ingår
- vad som hanteras av extern leverantör
- vad som verifieras på annan testnivå
- särskilda begränsningar
- viktiga risker

---

# 8. Koppla strategin till tidigare testanalys

När ni fyller i strategin ska ni använda resultatet från föregående workshop.

Kontrollera därför att strategin tar hänsyn till era tidigare identifierade:

---

# Redovisning

Varje grupp presenterar sin teststrategi på cirka **8–10 minuter**.

Ni ska inte läsa upp hela dokumentet.

Presentera istället era viktigaste strategiska val.

Fokusera på:

1. Vilka testnivåer har ni valt?
2. Varför behövs dessa nivåer?
3. Vilka är de viktigaste testobjekten?
4. Hur ser testmiljöbehovet ut?
5. Vilka öppna frågor är mest kritiska att få svar på?
6. Vilka risker har påverkat era val?



=======
# Nordic Shop

## Teststrategi för Nordic Shop

*[Text inom klamrar är exempel och vägledning till författaren. Ta bort vägledningstext innan dokumentet publiceras.]*

*Text inom hakparenteser \<exempel\> ska ersättas av verkliga begrepp. Rubriker som inte används kan markeras med ”Ej applicerbar” eller ”Gäller ej”.*

Följande dokumentegenskaper ska uppdateras:

| **Fält** | **Ange** |
|---|---|
| Ämne | NordicShop, ny e-handelsplattform |
| Författare | Grupp 2 |
| Organisation | Organisationens namn |
| Version | Dokumentets versionsnummer i formatet 0.3 |

# Dokumenthistorik

| **Datum** | **Version** | **Beskrivning** | **Författare** |
|---|---|---|---|
| <2026-09-24> | <0.1> | <Start, test_analys.md> | <Grupp 2> |
| <2026-09-25> | <0.2> | <Ifyllning utav test_strategi.md med mall verktyg att börja ifrån> | <Grupp 2> |
| <2026-09-28> | <0.3> | <En kortfattad beskrivning, några öppna frågor, 3 Testmiljöer> | <Grupp 2> |

# Innehållsförteckning

- 1  Teststrategi för NordicShop
  - 1.1 Kortfattad beskrivning
  - 1.2 Termer och förkortningar
  - 1.3 Hänvisningar till andra dokument
  - 1.4 Öppna frågor
- 2  Testnivåer
  - 2.1 Enhetstest
  - 2.2 Integrationstest
  - 2.3 Systemtest
  - 2.4 Acceptanstest
- 3  Testmiljö
- 4  Testobjekt
  - 4.1 Webb/Mobilapp kärnflöden
  - 4.2 Backend / Order Service
  - 4.3 Lagersystemintegration
  - 4.4 Betalningsintegration
  - 4.5 Leveransintegration
  - 4.6 Behörighet och åtkomstkontroll

# 1  Teststrategi för NordicShop

*[Denna mall är avsedd för att beskriva hur ett system vanligtvis testas. En välskriven teststrategi kan fungera som gemensamt kommunikationsunderlag mellan exempelvis utvecklare, testare och andra berörda roller.]*

## 1.1  Kortfattad beskrivning

*[Beskriv kortfattat vad teststrategin avser. Ange systemets namn.]*

Teststrategin beskriver hur NordicShop normalt testas. Vid varje release genomförs testplanering. Testplaneringen kan dokumenteras i en testplan som kompletterar teststrategin och beskriver eventuella avsteg från strategin.

NordicShop är ett e-handelsföretag som säljer kläder, elektronik och heminredning. Företaget utvecklar en ny e-handelsplattform som ska ersätta den befintliga lösningen, med målet att göra det enklare för kunder att handla, minska antalet avbrutna köp, ge snabbare orderhantering, automatisera lageruppdateringar, stödja fler betalningsalternativ och minska manuellt arbete för kundservice. Lösningen består av en webb- och mobilapp, en backend/Order Service samt integrationer mot ett äldre internt lagersystem och tre externa leverantörer: betalning, leverans och e-post/SMS. Utvecklingen sker agilt av tre parallella team i tvåveckorssprintar, med produktionsrelease planerad om cirka fyra månader. Denna teststrategi beskriver hur NordicShop ska testas på en övergripande nivå: vilka testnivåer som behövs, vilka testobjekt som ska verifieras, vilka testmiljöer som krävs och vilka frågor som fortfarande måste besvaras. Vid varje release genomförs testplanering utifrån denna strategi, vilken kan dokumenteras i en separat testplan som beskriver eventuella avsteg.

## 1.2  Termer och förkortningar

*[Förklara de termer som behövs för att förstå dokumentet. Hänvisa gärna till projektets termordlista om en sådan används.]*

| **Term** | **Förklaring** |
|---|---|
| Felrapport | Ett registrerat ärende för ett identifierat fel. |
| Testverktyg | Verktyg som används för krav-, test- och felhantering. |
| \<Term\> | \<Förklaring\> |
| E2E | Ett testflöde som verifierar en hel kedja av steg, från kundens handling till att alla inblandade system har reagerat korrekt. |
| API | Application Programming Interface. Gränssnitt som system använder för att kommunicera med varandra, t.ex. mellan order service och externa leverantörer. |
| Regression | Testning som säkerställer att ny eller ändrad kod inte har förstört tidigare fungerande funktionalitet. |
| Testmiljö | En miljö avsedd för test, separat från produktion, där system och integrationer kan verifieras utan att påverka riktiga kunder eller data. |
| Mock | En förenklad, konstgjord verision av ett system (t.ex. en betalningsleverantör) som används i test när det riktiga systemet inte är tillgängligt eller lämpligt eller att testa mot. |

## 1.3  Hänvisningar till andra dokument

*[Lista dokument som nämns i teststrategin. Ange vid behov versionsnummer, sökväg/länk, beskrivning och ansvarig/författare.]*

| **Dokument** | **Beskrivning / sökväg** |
|---|---|
| Testplan | \<Länk eller sökväg till testplan\> |
| Fil med testdata | \<Länk eller sökväg till testdata\> |
| SQL-skript | \<Länk eller sökväg till skript\> |
| Testfall | <test_fall.md> |
| Krav | krav.md |

## 1.4  Öppna frågor

*[Beskriv kända öppna frågor eller problem som påverkar innehållet i strategin. Ange ansvarig och datum när respektive fråga ska vara löst.]*

| **Öppen fråga** | **Ansvarig** | **Måldatum** | **Status** |
|---|---|---|---|
| \<Fråga\> | \<Namn\> | \<åååå-mm-dd\> | \<Öppen/Stängd\> |
| Hur säkerställer vi realistisk och konsekvent testdata (produkter, priser, lagersaldon) i den gemensamma testmiljön, med tre team som delar på den? | Testledare / Utvecklingsteam | <åååå-mm-dd> | Öppen |
| Vilka konkreta prestandamål gäller för "snabbare orderhantering" (svarstider, antal samtidiga användare)? | Product Owner | <åååå-mm-dd> | Öppen |
| Ska en extern säkerhetsgranskning/penetrationstest genomföras av kassan och kunddatabasen innan release? | Product Owner / Säkerhetsansvarig | <åååå-mm-dd> | Öppen |
| Har det 15 år gamla lagersystemet ett tillgängligt API, eller sker kommunikationen via filöverföring/databas? | Utvecklingsteam (lagersystem) | <åååå-mm-dd> | Öppen |
| Vilka webbläsare, operativsystem och mobila enheter ska plattformen stödja och testas på? | Product Owner | <åååå-mm-dd> | Öppen |
| Hur hanteras versionshantering och släppschema i den delade testmiljön så att de tre teamen inte stör varandras tester? | Testledare / Utvecklingsteam | <åååå-mm-dd> | Öppen |
| Vilken testdata och åtkomst kan vi få till betalningsleverantörens separata testmiljö? | Testledare / Extern leverantör (betalning) | <åååå-mm-dd> | Öppen |
|  |  |  |  |

# 2  Testnivåer

*[Beskriv samtliga testnivåer som ska tillämpas vid test av systemet, exempelvis komponenttest, integrationstest, systemtest och acceptanstest. Tydliggör skillnaden mellan nivåerna för att minska risken för luckor och onödig dubblering.]*

## 2.1  komponent-/enhetstest

*[Beskriv vilka roller som genomför testerna, testnivåns syfte och mål, mottagare av resultat samt omfattning och avgränsning.]*

## 2.2 integrationstest


# 3  Testmiljö

*[Beskriv kortfattat testmiljön eller testmiljöerna. Beskriv likheter och skillnader jämfört med produktionsmiljön. Komplettera gärna med en skiss över system och integrationer.]*

| **Miljö** | **Syfte** | **Viktiga skillnader mot produktion** |
|---|---|---|
| Gemensam testmiljö (delad av de tre utvecklingsteamen) | Integrationstest och systemtest av webb/app, backend och interna flöden. | Delas av tre team, risk för att förändringar krockar; sannolikt lägre kapacitet än produktion. |
| Betalningsleverantörens separata testmiljö | Integrationstest av betalningsflöden (Visa, Mastercard, Swish) med testkort/testdata. | Egen, isolerad miljö hos extern part; kräver separat åtkomst och testdata. |
| Acceptans-/stagingmiljö (så nära produktion som möjligt) | Acceptanstest och slutlig verifiering av kompletta flöden inför release. | Bör efterlikna produktion, men med begränsad/anonymiserad testdata och utan skarpa betalningar. |

# 4  Testobjekt

*[Beskriv på övergripande detaljnivå vad som ska testas. Det kan vara testområden, testomfattning, systemdelar, program, integrationer eller ett mindre antal konkreta testfall.]*


## 4.1  Webb/Mobilapp – kärnflöden
 
| **Testobjekt / område** | **Vad ska verifieras?** | **Kommentar / avgränsning** |
|---|---|---|
| Registrering, inloggning, sök, kundvagn, rabattkod, betalning, orderöversikt | Att flödena fungerar tekniskt korrekt end-to-end. | UI/UX-utseende (layout, grafisk profil) avgränsas från denna strategi. |
 
## 4.2  Backend / Order Service
 
| **Testobjekt / område** | **Vad ska verifieras?** | **Kommentar / avgränsning** |
|---|---|---|
| Orderhantering, statusuppdateringar, triggers | Att korrekta anrop/triggers går till lagersystem, betalning, leverans och e-post/SMS. | Den tekniska implementationen hos externa system testas inte. |
 
## 4.3  Lagersystemintegration
 
| **Testobjekt / område** | **Vad ska verifieras?** | **Kommentar / avgränsning** |
|---|---|---|
| Lagersaldo vid köp och avbeställning | Att saldo uppdateras/återställs korrekt, samt beteende vid hög belastning eller timeout. | Själva lagersystemets kod testas inte – fokus på gränssnittet. Hög risk pga systemets ålder. |
>>>>>>> 8f30e3f0f105313b37c45cbaf5ab82f7b55aac91
