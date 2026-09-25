**MALL FÖR TESTSTRATEGI**

**<Företagsnamn>**

<Projektnamn>

Teststrategi för <namn på systemet eller motsvarande>

**Version <x.y>**

*[Text inom klamrar är exempel och vägledning till författaren. Ta bort vägledningstext innan dokumentet publiceras.]*

*Text inom hakparenteser <exempel> ska ersättas av verkliga begrepp. Rubriker som inte används kan markeras med "Ej applicerbar" eller "Gäller ej".*

Följande dokumentegenskaper ska uppdateras:

| **Fält** | **Ange** |
| --- | --- |
| Ämne | Projektets eller systemets namn |
| Författare | Författarens för- och efternamn |
| Organisation | Organisationens namn |
| Version | Dokumentets versionsnummer i formatet 1.2 |

# Dokumenthistorik

| **Datum** | **Version** | **Beskrivning** | **Författare** |
| --- | --- | --- | --- |
| <åååå-mm-dd> | <x.x> | <detaljer> | <namn> |
| | | | |

# Innehållsförteckning

1. Teststrategi för <namn på systemet eller motsvarande>
   - 1.1 Kortfattad beskrivning
   - 1.2 Termer och förkortningar
   - 1.3 Hänvisningar till andra dokument
   - 1.4 Öppna frågor
2. Testnivåer
   - 2.1 <Benämning på testnivå 1>
3. Testmiljö
4. Testobjekt
   - 4.1 <Benämning på testobjekt 1>

# 1 Teststrategi för <namn på systemet eller motsvarande>

*[Denna mall är avsedd för att beskriva hur ett system vanligtvis testas. En välskriven teststrategi kan fungera som gemensamt kommunikationsunderlag mellan exempelvis utvecklare, testare och andra berörda roller.]*

## 1.1 Kortfattad beskrivning

*[Beskriv kortfattat vad teststrategin avser. Ange systemets namn.]*

Teststrategin beskriver hur <systemets namn> normalt testas. Vid varje release genomförs testplanering. Testplaneringen kan dokumenteras i en testplan som kompletterar teststrategin och beskriver eventuella avsteg från strategin.

## 1.2 Termer och förkortningar

*[Förklara de termer som behövs för att förstå dokumentet. Hänvisa gärna till projektets termordlista om en sådan används.]*

| **Term** | **Förklaring** |
| --- | --- |
| Felrapport | Ett registrerat ärende för ett identifierat fel. |
| Testverktyg | Verktyg som används för krav-, test- och felhantering. |
| <Term> | <Förklaring> |

## 1.3 Hänvisningar till andra dokument

*[Lista dokument som nämns i teststrategin. Ange vid behov versionsnummer, sökväg/länk, beskrivning och ansvarig/författare.]*

| **Dokument** | **Beskrivning / sökväg** |
| --- | --- |
| Testplan | <Länk eller sökväg till testplan> |
| Fil med testdata | <Länk eller sökväg till testdata> |
| SQL-skript | <Länk eller sökväg till skript> |

## 1.4 Öppna frågor

*[Beskriv kända öppna frågor eller problem som påverkar innehållet i strategin. Ange ansvarig och datum när respektive fråga ska vara löst.]*

| **Öppen fråga** | **Ansvarig** | **Måldatum** | **Status** |
| --- | --- | --- | --- |
| <Fråga> | <Namn> | <åååå-mm-dd> | <Öppen/Stängd> |
| | | | |

# 2 Testnivåer

*[Beskriv samtliga testnivåer som ska tillämpas vid test av systemet, exempelvis komponenttest, integrationstest, systemtest och acceptanstest. Tydliggör skillnaden mellan nivåerna för att minska risken för luckor och onödig dubblering.]*

## 2.1 <Benämning på testnivå 1>

*[Beskriv vilka roller som genomför testerna, testnivåns syfte och mål, mottagare av resultat samt omfattning och avgränsning.]*

# 3 Testmiljö

*[Beskriv kortfattat testmiljön eller testmiljöerna. Beskriv likheter och skillnader jämfört med produktionsmiljön. Komplettera gärna med en skiss över system och integrationer.]*

| **Miljö** | **Syfte** | **Viktiga skillnader mot produktion** |
| --- | --- | --- |
| <Testmiljö 1> | <Beskriv> | <Beskriv> |
| <Testmiljö 2> | <Beskriv> | <Beskriv> |

# 4 Testobjekt

*[Beskriv på övergripande detaljnivå vad som ska testas. Det kan vara testområden, systemdelar, program, integrationer eller ett mindre antal konkreta testfall.]*

## 4.1 <Benämning på testobjekt 1>

| **Testobjekt / område** | **Vad ska verifieras?** | **Kommentar / avgränsning** |
| --- | --- | --- |
| <Objekt 1> | <Beskriv> | <Beskriv> |
| <Objekt 2> | <Beskriv> | <Beskriv> |
| <Objekt 3> | <Beskriv> | <Beskriv> |
