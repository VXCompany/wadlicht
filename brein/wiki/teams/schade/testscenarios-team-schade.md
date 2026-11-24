---
titel: Testscenario's in Gherkin Team Schade
niveau: team
status: richtinggevend
eigenaar: Team Schade
team: team-schade
regel_prefix: TS-SC
bronnen:
  - "[[2026-10-24-retro-notulen]]"
  - "[[2026-06-15-ai-governance-kader-v1]]"
bijgewerkt: 2026-11-24
review_voor: 2027-05-31
tags: [niveau/team, team/schade]
---

# Testscenario's in Gherkin Team Schade

Elke regel uit het brein die een intentie raakt, wordt aantoonbaar gecontroleerd met een leesbaar testscenario. De scenario's zijn begrijpelijk zonder technische kennis en traceerbaar naar de regel waar ze uit voortkomen. Ze beschrijven verwacht gedrag; het bewijs dat ze slagen staat in Git en CI, niet in het brein.

> Herkomst: deze afspraken zijn vastgesteld op 24 november 2026 bij de voorbereiding van de demo. Een bronnotitie in `raw/team-schade/` ontbreekt nog. TS-SC-02 bouwt voort op [[werkafspraken-team-schade#TS-WA-02]].

### TS-SC-01
**Testscenario's schrijven we in Gherkin, in het Nederlands, met `# language: nl` bovenaan.**

### TS-SC-02
**Elk scenario krijgt als tag het regel-ID (of de ID's) waar het uit voortkomt, bijvoorbeeld `@PRD-SCH-INV-07`. Een scenario zonder regel-ID is niet toegestaan.**
- Afgeleid van: [[werkafspraken-team-schade#TS-WA-02]] (regel-ID in de testnaam)
- Toelichting: wordt een scenario later een geautomatiseerde test, dan volgt de testnaam [[codeerrichtlijnen-team-schade#TS-CR-03]].

### TS-SC-03
**Per toepasselijke regel is er minstens één scenario voor de normale situatie en één voor de grens of de afwijking.**
- Voorbeeld: binnen de fotolimiet uploaden, en de limiet overschrijden.

### TS-SC-04
**Elk acceptatiecriterium uit de intentie is gedekt door minstens één scenario. Zo'n scenario krijgt ook de tag `@intentie`.**
- Sluit aan op: [[intake-invest-team-schade#TS-IT-01]]

### TS-SC-05
**Scenario's beschrijven wat een gebruiker doet en ziet, niet hoe het systeem het technisch oplost. Geen schermnamen, knoppen, databases of API's in de stappen.**

### TS-SC-06
**Elk scenario toetst één gedrag, met één Als-stap. Meerdere Dan-stappen mogen, zolang ze over hetzelfde gedrag gaan.**

### TS-SC-07
**Gebruik de concrete waarden uit het brein. Ontbreekt een waarde, verzin die dan niet: meld het hiaat en draag het werk over.**
- Afgeleid van: [[werkvormen-en-autonomie#ORG-AI-06]]

### TS-SC-08
**Wie de scenario's schrijft, keurt ze niet zelf goed. Een verificatie-agent of een engineer controleert TS-SC-02 tot en met TS-SC-04.**
- Afgeleid van: [[werkvormen-en-autonomie#ORG-AI-04]]

## Voorbeeld

Voor de fotostap van [[schademelden]], met de limieten uit [[schademelden-gedrag#PRD-SCH-GED-03]] en [[schademelden-invarianten#PRD-SCH-INV-07]]:

```gherkin
# language: nl
Functionaliteit: Foto's toevoegen aan een schademelding

  @PRD-SCH-GED-03 @intentie
  Scenario: Klant voegt foto's toe binnen de limiet
    Gegeven een klant die een schade meldt
    Als de klant 5 foto's van elk 4 MB toevoegt
    Dan worden de 5 foto's aan de melding toegevoegd

  @PRD-SCH-INV-07 @intentie
  Scenario: Klant voegt meer foto's toe dan toegestaan
    Gegeven een klant die al 10 foto's heeft toegevoegd
    Als de klant nog een foto toevoegt
    Dan ziet de klant een melding dat er maximaal 10 foto's mogen
    En blijft de melding 10 foto's bevatten

  @PRD-SCH-INV-07
  Scenario: Klant kiest een foto die te groot is
    Gegeven een klant die een schade meldt
    Als de klant een foto van 16 MB kiest
    Dan ziet de klant vóór het versturen een melding dat een foto maximaal 15 MB mag zijn
    En wordt de foto niet toegevoegd

  @PRD-SCH-INV-03
  Scenario: Opslaan van een foto mislukt
    Gegeven een klant die een melding met 3 foto's verstuurt
    Als het opslaan van één foto mislukt
    Dan krijgt de klant geen bevestiging
    En ziet de klant een foutmelding met de mogelijkheid het opnieuw te proberen
```

Het laatste scenario komt voort uit [[incidenten-team-schade#INC-2026-041]].
