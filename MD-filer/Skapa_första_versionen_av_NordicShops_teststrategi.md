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

Använd mallens struktur:

| Testobjekt / område | Vad ska verifieras? | Kommentar / avgränsning |
| --- | --- | --- |
|  |  |  |
|  |  |  |

Identifiera minst **4 testobjekt/områden**.

---

## För varje testobjekt ska ni beskriva

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
