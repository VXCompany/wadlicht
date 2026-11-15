# Demo-setup: Claude Tag en Slack

Hoe de Slack-werkruimte en Claude Tag zijn ingericht voor de demo van De Denkfabriek met Wadlicht Verzekeringen.

> Claude Tag is in publieke bèta. Menu's en knoppen kunnen veranderen. Controleer bij twijfel de [documentatie van Claude Tag](https://claude.com/docs/claude-tag/admins/setup-overview.md).

## De twee demo's

Beide demo's lopen live in Slack. Het draaiboek met alle berichten staat onderaan dit document.

| Demo | Kanaal | Wat het laat zien |
|---|---|---|
| 1. Mag de fotolimiet omhoog? | `#wadlicht-intake` | De agent vindt de regels in het brein en weet waarom ze bestaan |
| 2. SchadeMelden | `#wadlicht-intake`, daarna `#wadlicht-ontwikkeling` | Escalatie bij gezondheidsgegevens, stemming door de zaal, en de engineer die het werk verdeelt |

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
Je bent de orkestratie-agent. Je bouwt niets. Lees voor elke intentie het brein: minimaal werkvormen-en-autonomie en de team- en productpagina's. Stel de werkvorm vast (Autonoom, Gepaard, Mens-geleid) en noem de regels die dat bepalen. Bij Mens-geleid of verplichte review: stop, tag @Dimitri (architect en tech lead) en @Yuri (product owner), en wacht op een expliciet menselijk besluit in de thread. Vraag @Dimitri als tech lead om bevestiging van de werkvorm. Leg het besluit vast met wie het nam.
```

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

## Na het oefenen

- Merge geen pull requests van de agents naar main.
- Sluit ze op GitHub en verwijder hun branches.
- Controleer dat Slack geen openstaande threads van het oefenen op het scherm laat zien.
