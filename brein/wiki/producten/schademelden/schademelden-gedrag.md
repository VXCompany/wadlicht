---
titel: SchadeMelden, gedrag
niveau: product
status: beschrijvend
eigenaar: Team Schade
team: team-schade
regel_prefix: PRD-SCH-GED
bronnen:
  - "[[2026-09-15-productvisie-schademelden]]"
bijgewerkt: 2026-10-25
review_voor: 2027-01-31
tags: [niveau/product, product/schademelden]
---

# SchadeMelden, gedrag

Beoogd gedrag van de eerste versie van [[schademelden]]. Elke stap staat op één scherm en werkt op een telefoon.

### PRD-SCH-GED-01
**Stap 1, polis: de klant vult polisnummer, postcode en geboortedatum in. De app controleert dit via de [[polisregister-api-v2#TP-API-01]] en de polisstatus via [[polisregister-api-v2#TP-API-02]].**
- Bij een onbekende combinatie: een neutrale melding zonder te zeggen welk gegeven niet klopt.
- Bij een niet-actieve polis: de klant wordt doorverwezen naar de klantenservice.

### PRD-SCH-GED-02
**Stap 2, wat is er gebeurd: soort schade (afhankelijk van het producttype), datum, plaats en een omschrijving van maximaal 2.000 tekens. Vraag: "Is er iemand gewond?" (ja of nee).**
- Bij "ja" vraagt de app geen details, maar meldt dat een letselbehandelaar contact opneemt.

### PRD-SCH-GED-03
**Stap 3, foto's: maximaal 10 foto's van maximaal 15 MB per foto, in JPEG, PNG of HEIC.**
- Limieten: zie [[schademelden-invarianten#PRD-SCH-INV-07]].

### PRD-SCH-GED-04
**Stap 4, controleren: de klant ziet een overzicht en verstuurt.**

### PRD-SCH-GED-05
**Stap 5, bevestiging: de klant ziet een meldingsnummer (formaat `SM-JJJJ-NNNNNN`) en krijgt een bevestiging per e-mail.**
- Pas als alles is opgeslagen: zie [[schademelden-invarianten#PRD-SCH-INV-03]].

## Teksten

Alle teksten op B1-niveau, met "je", volgens [[huisstijl-en-tone-of-voice#TM-HS-04]].
