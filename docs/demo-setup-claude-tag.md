# Demo-setup: Claude Tag en Slack

Hoe de Slack-werkruimte en Claude Tag zijn ingericht voor de demo van De Denkfabriek met Wadlicht Verzekeringen.

> Claude Tag is in publieke bèta. Menu's en knoppen kunnen veranderen. Controleer bij twijfel de [documentatie van Claude Tag](https://claude.com/docs/claude-tag/admins/setup-overview.md).

## De demo's

De demo's lopen live in Slack. Het draaiboek met alle berichten staat onderaan dit document.

| Demo | Kanaal | Wat het laat zien |
|---|---|---|
| 1. Mag de fotolimiet omhoog? | `#wadlicht-intake` | De agent vindt de regels in het brein en weet waarom ze bestaan |
| 2. SchadeMelden | `#wadlicht-intake`, daarna `#wadlicht-ontwikkeling` | Escalatie bij gezondheidsgegevens, stemming door de zaal, en de engineer die het werk verdeelt |
| 3. Van user story naar testscenario | `#wadlicht-intake` | INVEST-toets, regels uit het brein, werkvorm, en testscenario's in Gherkin met regel-ID's |

## Rollen

| Wie | Rol in de demo |
|---|---|
| Yuri | Product owner, in demo 2 daarna engineer |
| Dimitri | Architect en tech lead: bevestigt de werkvorm (ORG-AI-01), en engineer bij het verdelen van het werk |
| Zaal | Menselijke experts: stemmen via Mentimeter bij de escalatie |

## Kanalen

| Kanaal | Agentrol | Gebruikt bij |
|---|---|---|
| `#wadlicht-intake` | Orkestratie: werkvorm bepalen en escaleren | Demo 1, demo 2 tot en met de stemming |
| `#wadlicht-ontwikkeling` | Development agent | Demo 2: het werk verdelen en stap 1 |
| `#wadlicht-verificatie` | Verificatie-agent | Niet in de demo; optioneel, voor vragen na afloop |

Maak de kanalen in Slack en nodig Claude in elk kanaal uit met `/invite @Claude`. Pas dan verschijnen ze in de admin-instellingen.

## Voorwaarden

- Claude-organisatie op een Team- of Enterprise-plan, en jij bent daar **Owner**.
- **Routines** staan aan: Organization settings > Capabilities > Remote sessions > Routines.
- Usage credits geladen (Team-plan) via `claude.ai/admin-settings/usage`, met een lage bestedingslimiet via `claude.ai/admin-settings/usage/claude-tag`.
- Slack-werkruimte gekoppeld aan de Claude-organisatie (`@Claude connect`, koppelcode plakken op `claude.ai/admin-settings/claude-tag`).

## Stap 1: GitHub koppelen (één keer)

1. Ga naar `claude.ai/admin-settings/github`.
2. Klik op **Connect Claude to GitHub** en rond de autorisatie op GitHub af.
3. Klik in de tabel **Connected GitHub accounts** bij **VXCompany** op **Link**. Staat VXCompany er niet bij: **Install on another organization**.

Degene die dit doet, moet eigenaar zijn van de GitHub-organisatie VXCompany én Owner in de Claude-organisatie. Is dat niet zo: gebruik **Copy message** onder "Not a GitHub account owner?" en stuur het naar een eigenaar. Een persoonlijk GitHub-account werkt niet voor Claude Tag.

## Stap 2: repository aan de kanalen geven

1. Open `claude.ai/admin-settings/claude-tag` > **Claude's access** > **Bundles** en maak een bundel "Wadlicht demo".
2. Kies op het tabblad **Repositories** alleen `VXCompany/wadlicht` (niet **Connect all**).
3. Kies onder **Where it applies** > **Add place** de drie kanalen, elk met **Add**.
4. Klik op **Save changes**.

Een sessie kloont de repository pas als die in het eerste bericht van een thread genoemd wordt. Noem `VXCompany/wadlicht` dus in elk eerste bericht. Na het klonen laden `CLAUDE.md` en de skills uit `.claude/skills/`. Hooks uit de repository draaien niet, en `.mcp.json` wordt niet geladen.

## Stap 3: instructies per kanaal

1. Open `claude.ai/admin-settings/claude-tag` > **Channels** en kies het kanaal.
2. Plak op het tabblad **General** de tekst hieronder in **Channel instructions**.
3. Sla op via de balk die onder het veld verschijnt.

Instructies gelden alleen voor nieuwe threads. Begin na een wijziging altijd een nieuwe thread.

### `#wadlicht-intake`

```text
Werk altijd in de repository VXCompany/wadlicht.
Je bent de orkestratie-agent. Je bouwt niets.
Volgorde bij een nieuwe intentie (een bericht met "Nieuwe intentie"):
1. Voer eerst de skill invest-toets uit. Meld de uitkomst met de regel-ID's (TS-IT). Bij "Verduidelijking nodig" of "Opsplitsen": stel je vragen of je voorstel in de thread en raadpleeg het brein nog niet. Toets opnieuw na het antwoord. Sla de toets nooit over.
2. Pas als de intentie geschikt is: lees het brein (brein-query), minimaal werkvormen-en-autonomie en de team- en productpagina's. Stel de werkvorm vast (Autonoom, Gepaard, Mens-geleid) en noem de regels die dat bepalen.
3. Bij Mens-geleid of verplichte review: stop, tag @Dimitri (architect en tech lead) en @Yuri (product owner), en wacht op een expliciet menselijk besluit in de thread. Vraag @Dimitri als tech lead om bevestiging van de werkvorm. @Yuri kan in alle gevallen ook namens Dimitri antwoorden. Leg het besluit vast met wie het nam.
4. Vraagt iemand om testscenario's: schrijf ze volgens testscenarios-team-schade (Gherkin, Nederlands, regel-ID als tag, normaal en grens). Verzin geen waarden die niet in het brein of de intentie staan; meld ontbrekende kennis als hiaat.
Een vraag (geen nieuwe intentie) beantwoord je direct met brein-query, zonder INVEST-toets.
```

> **Let op bij demo 2.** De intentie van demo 2 omvat de hele app SchadeMelden. Met de INVEST-toets is de kans groot dat de agent "Opsplitsen" adviseert (TS-IT-02). Dat kan een mooi moment zijn, maar het verandert het verloop. Oefen demo 2 opnieuw na het wijzigen van deze instructies.

### `#wadlicht-ontwikkeling`

```text
Werk altijd in de repository VXCompany/wadlicht.
Je bent de development agent van Team Schade. Begin pas als er een menselijk besluit uit #wadlicht-intake is genoemd. Lees eerst de invarianten van het product. Werk gepaard: stel per stap voor, de engineer beslist. Werk op een feature-branch en open een pull request. Push nooit naar main. Geen persoonsgegevens in code, logs, testdata of foutmeldingen (ORG-PRV-06). Gebruik alleen fictieve testdata.
```

### `#wadlicht-verificatie`

```text
Werk altijd in de repository VXCompany/wadlicht.
Je bent de verificatie-agent. Je hebt de code niet geschreven en wijzigt haar ook niet (ORG-AI-04). Beoordeel de pull request tegen de invarianten van het product. Schrijf per invariant een test met het regel-ID in de naam. Rapporteer bevindingen per invariant: getoetst, resultaat, wat ontbreekt. Neem randgevallen die mensen aandragen serieus op.
```

## Stap 4: persoonlijke connectors

Op een Team-plan kun je persoonlijke connectors in kanalen niet uitzetten. Claude vraagt wel eerst toestemming, met een melding die alleen de aanvrager ziet.

- Kies **Don't allow**.
- Sla nooit **Allow** op als vaste keuze. Controleer in de Claude-app in Slack op het tabblad **Home** dat **Ask every time** aan staat.
- Het veiligst: verstuur de berichten op het scherm vanaf een account zonder connectors op claude.ai.

## Stap 5: testen

Start in elk kanaal een nieuwe thread:

```text
@Claude wat kun je vanuit dit kanaal bereiken in VXCompany/wadlicht?
```

En in dezelfde thread:

```text
@Claude herhaal je kanaalinstructies
```

## Beveiliging van main

Kanaalinstructies zijn richtlijnen, geen harde blokkade. Zet daarom in GitHub branch protection op `main`: alleen via pull request, met minimaal één review. Claude opent pull requests als de Claude GitHub App. Dat beschermt ook de beginstand van de demo (tag `demo-start`).

## Draaiboek: de berichten

Begin elke demo in een **nieuwe thread**. Noem `VXCompany/wadlicht` in het eerste bericht van elke thread, anders kloont de sessie de repository niet.

### Demo 1, `#wadlicht-intake`

```text
@Claude Vraag over VXCompany/wadlicht: mag ik de maximale fotogrootte voor de upload in SchadeMelden ophogen van 15 naar 20 MB? En kan een agent dat zelfstandig doen?
```

Verwacht: niet zelfstandig. TS-WA-03 (uploads minimaal gepaard), PRD-SCH-INV-07 (overal dezelfde limiet) en incident INC-2026-041 als reden.

### Demo 2, `#wadlicht-intake`: de intentie (product owner)

```text
@Claude Nieuwe intentie voor VXCompany/wadlicht.

Als product owner wil ik dat klanten een schade kunnen melden zonder in te loggen, ook op hun telefoon. Voeg de app SchadeMelden toe aan de website, zoals beschreven op de productpagina's in het brein.

Wat ik verwacht van de eerste versie:
- de vijf stappen uit schademelden-gedrag
- een bevestiging met meldingsnummer per e-mail
- alleen particuliere verzekeringen

Bepaal eerst welke regels gelden en welke werkvorm dit krijgt. Begin nog niet met bouwen.
```

Verwacht: Mens-geleid door ORG-AI-03 (de app legt vast of er iemand gewond is). De agent tagt de architect en de product owner en wacht.

### Demo 2, `#wadlicht-intake`: de architect en tech lead (Dimitri)

```text
@Claude Als tech lead bevestig ik de werkvorm Mens-geleid. ADR-001 blijft het uitgangspunt. Voor de letselindicatie wil ik eerst weten: waar slaan we die op, wie kan haar zien (PRD-SCH-INV-04), en blijft alles in de EU (ORG-PRV-05)? Zet de opties op een rij, dan beslissen we.
```

### Demo 2, `#wadlicht-intake`: het besluit na de stemming

A, goedkeuren:

```text
@Claude Besluit van de menselijke experts in de zaal: goedgekeurd, werkvorm Mens-geleid. Leg het besluit vast met wie het nam en zet het werk klaar voor #wadlicht-ontwikkeling.
```

B, goedkeuren met extra eis:

```text
@Claude Besluit van de menselijke experts in de zaal: goedgekeurd, werkvorm Mens-geleid, met als extra eis: [eis uit de zaal]. Leg het besluit vast met wie het nam en neem de eis op in de opdracht voor #wadlicht-ontwikkeling.
```

C, afkeuren (dan stopt de demo hier):

```text
@Claude Besluit van de menselijke experts in de zaal: nog niet bouwen. Terug naar de product owner. Leg het besluit vast en zet op een rij wat er eerst duidelijk moet zijn.
```

Kopieer daarna de link naar het besluitbericht (in Slack: **Kopieer link**). Die heb je nodig in het ontwikkelkanaal: een sessie in een ander kanaal ziet de intake-thread niet vanzelf.

### Demo 2, `#wadlicht-ontwikkeling`: bouwen (Yuri als engineer)

```text
@Claude Ik ben de engineer en ga beginnen met bouwen aan SchadeMelden in VXCompany/wadlicht. Het besluit uit #wadlicht-intake: [link naar de thread]
```

```text
@Claude Kun je samen met mij het totale werk even verdelen?
```

```text
@Claude Ik wil graag dat je stap 1 doet, maar Dimitri en ik doen de rest.
```

Hoe dit verder loopt, is niet belangrijk voor het verhaal. Het punt: de engineer verdeelt het werk, de agent doet een afgebakend stuk.

### Demo 3, `#wadlicht-intake`: van user story naar testscenario

Volgt de vijf stappen van de denkfabriek: intentie, kennis, beslissingen, bewijs, leren.

**1. Intentie, bewust vaag** (product owner):

```text
@Claude Nieuwe intentie voor VXCompany/wadlicht.

Als klant wil ik foto's uploaden bij mijn schademelding in SchadeMelden, zodat mijn claim sneller wordt afgehandeld.
```

Verwacht: INVEST-toets "Verduidelijking nodig". TS-IT-01 (Testable) voldoet niet: geen grenzen en geen verwacht resultaat. De agent stelt gerichte vragen en raadpleegt het brein nog niet.

Zeg: "De agent kijkt eerst of het verzoek helder en toetsbaar genoeg is, voordat hij iets gaat bouwen."

**2. Verduidelijking** (product owner, in dezelfde thread):

```text
@Claude Een klant mag maximaal 10 foto's toevoegen van elk maximaal 15 MB, in JPEG, PNG of HEIC. Bij meer foto's of een te grote foto ziet de klant een duidelijke melding en wordt de foto niet toegevoegd.
```

Verwacht: INVEST-toets "Geschikt". Daarna haalt de agent de regels op: PRD-SCH-GED-03, PRD-SCH-INV-07 (limieten in elke laag gelijk), PRD-SCH-INV-03 (bevestiging pas na opslag), PRD-SCH-INV-08 en ORG-SEC-05 (scannen), en incident INC-2026-041 als achtergrond. Werkvorm: Gepaard door TS-WA-03 (uploads nooit autonoom). De agent vraagt @Dimitri om bevestiging.

Zeg: "Nu haalt hij op wat de organisatie al weet, en hij laat precies zien uit welke regel dat komt." En bij de werkvorm: "De AI stelt voor, maar vaste regels bepalen de ondergrens."

**3. Bevestiging** (Dimitri als tech lead):

```text
@Claude Als tech lead bevestig ik de werkvorm Gepaard.
```

**4. Bewijs** (product owner):

```text
@Claude Maak de testscenario's voor deze intentie.
```

Verwacht: Gherkin in het Nederlands, elk scenario met een regel-ID als tag (TS-SC-02), per regel een normaal en een grensgeval (TS-SC-03), en de acceptatiecriteria uit de intentie met `@intentie` (TS-SC-04). Vergelijk met het voorbeeld in `brein/wiki/teams/schade/testscenarios-team-schade.md`.

Zeg: "Elke regel wordt een controle, en je ziet bij elk scenario uit welke regel het komt."

**5. Leren:** wijs in de uitvoer op een hiaat dat de agent meldt, als hij dat doet (bijvoorbeeld een ontbrekende waarde, TS-SC-07). Zeg: "Wat hij nieuw ontdekt, stelt hij voor aan het brein, en een mens beslist."

## Na het oefenen

- Merge geen pull requests van de agents naar main.
- Sluit ze op GitHub en verwijder hun branches.
- Controleer dat Slack geen openstaande threads van het oefenen op het scherm laat zien.
