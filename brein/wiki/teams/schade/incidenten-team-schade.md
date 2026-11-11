---
titel: Incidenten Team Schade
niveau: team
status: beschrijvend
eigenaar: Team Schade
team: team-schade
bronnen:
  - "[[2026-10-22-incidentrapport-INC-2026-041]]"
bijgewerkt: 2026-10-25
review_voor: 2027-04-01
tags: [niveau/team, team/schade]
---

# Incidenten Team Schade

Lessen uit incidenten die effect hebben op hoe we werken of op productkennis.

### INC-2026-041
**20 oktober 2026: 312 schademeldingen kwamen binnen zonder foto's, terwijl de klant een bevestiging kreeg.**
- Bron: [[2026-10-22-incidentrapport-INC-2026-041]]
- Systeem: schadeformulier in Mijn Wadlicht (voorganger van [[schademelden]])
- Wat: de maximale fotogrootte ging van 10 naar 15 MB in het formulier. De gateway stond nog op 12 MB. Foto's tussen 12 en 15 MB werden geweigerd, het formulier ving dat niet af en bevestigde de melding toch.
- Hoe het ontstond: de wijziging leek klein (één constante), is autonoom door een agent uitgevoerd en alle tests waren groen.
- Gevolgen voor kennis en werkwijze:
  - [[werkafspraken-team-schade#TS-WA-03]]: uploads minimaal gepaard
  - [[codeerrichtlijnen-team-schade#TS-CR-04]]: limieten op één plek
  - [[schademelden-invarianten#PRD-SCH-INV-03]]: bevestiging pas na opslag van alle bijlagen
  - [[schademelden-invarianten#PRD-SCH-INV-07]]: limieten gelijk in alle lagen
- Doorwerking: besluit van de AI Governance Board van 4 november 2026 (nog niet verwerkt in het brein).
