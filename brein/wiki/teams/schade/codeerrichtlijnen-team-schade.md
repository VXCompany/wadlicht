---
titel: Codeerrichtlijnen Team Schade
niveau: team
status: richtinggevend
eigenaar: Team Schade
team: team-schade
regel_prefix: TS-CR
bronnen:
  - "[[2026-02-02-referentiearchitectuur-2026]]"
bijgewerkt: 2026-10-05
review_voor: 2027-04-01
tags: [niveau/team, team/schade]
---

# Codeerrichtlijnen Team Schade

### TS-CR-01
**.NET 10 (LTS), C# met nullable reference types aan en warnings als errors.**
- Afgeleid van: [[referentiearchitectuur#ORG-ARC-03]]

### TS-CR-02
**Azure Functions in het isolated worker model.**
- Afgeleid van: [[referentiearchitectuur#ORG-ARC-02]]

### TS-CR-03
**Tests met xUnit. Invariant-tests heten `PRD_<PRODUCT>_INV_<NN>_<omschrijving>`.**
- Sluit aan op: [[werkafspraken-team-schade#TS-WA-02]]

### TS-CR-04
**Limieten en drempels (zoals maximale bestandsgrootte) staan op één plek in de configuratie, niet als constante in code.**
- Bron: [[2026-10-22-incidentrapport-INC-2026-041]], maatregel 2

### TS-CR-05
**Geen persoonsgegevens in logs. Log meldingsnummers, geen namen, adressen of polisgegevens.**
- Afgeleid van: [[privacy-en-bewaartermijnen#ORG-PRV-06]]

### TS-CR-06
**Front-end zonder framework waar het kan: HTML, CSS en een beperkte hoeveelheid JavaScript, binnen de Content Security Policy van de website.**
- Sluit aan op: [[werkafspraken-team-marketing#TM-WA-03]], [[website-wadlicht]]
