---
titel: Werkafspraken Team Schade
niveau: team
status: richtinggevend
eigenaar: Team Schade
team: team-schade
regel_prefix: TS-WA
bronnen:
  - "[[2026-10-24-retro-notulen]]"
  - "[[2026-10-22-incidentrapport-INC-2026-041]]"
bijgewerkt: 2026-10-25
review_voor: 2027-04-01
tags: [niveau/team, team/schade]
---

# Werkafspraken Team Schade

### TS-WA-01
**We werken trunk-based met korte pull requests. Elke pull request heeft minimaal één menselijke reviewer die het werk niet zelf deed.**
- Afgeleid van: [[werkvormen-en-autonomie#ORG-AI-04]]

### TS-WA-02
**Elke productinvariant heeft minimaal één test met het regel-ID in de naam.**
- Bron: [[2026-10-24-retro-notulen]]
- Voorbeeld: `PRD_SCH_INV_03_bevestiging_pas_na_opslag_alle_bijlagen`

### TS-WA-03
**Wijzigingen aan bestandsuploads (limieten, opslag, verwerking, foutafhandeling) voeren we minimaal gepaard uit, met review door een tweede engineer. Nooit autonoom.**
- Bron: [[2026-10-24-retro-notulen]], naar aanleiding van [[incidenten-team-schade#INC-2026-041]]
- Afgeleid van: [[werkvormen-en-autonomie#ORG-AI-02]] (aanscherping: op organisatieniveau is zo'n wijziging niet uitgesloten van autonoom werk)
- Geldt sinds: 24 oktober 2026

### TS-WA-04
**Klantgerichte wijzigingen gaan live achter een feature flag, zodat we ze zonder nieuwe release kunnen uitzetten.**

### TS-WA-05
**Definition of Done: code gereviewd, tests groen inclusief invariant-tests, productkennis in het brein bijgewerkt of een voorstel daarvoor ingediend, evidence vastgelegd in de pull request (werkvorm, wie maakte, wie verifieerde).**
- Afgeleid van: [[werkvormen-en-autonomie#ORG-AI-01]], [[werkvormen-en-autonomie#ORG-AI-04]]
