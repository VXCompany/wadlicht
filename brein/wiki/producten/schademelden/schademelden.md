---
titel: SchadeMelden
niveau: product
status: beschrijvend
eigenaar: Team Schade
team: team-schade
bronnen:
  - "[[2026-09-15-productvisie-schademelden]]"
  - "[[2026-10-24-retro-notulen]]"
bijgewerkt: 2026-10-25
review_voor: 2027-01-31
tags: [niveau/product, product/schademelden]
---

# SchadeMelden

**Status van het product: in ontwikkeling.** Er is nog geen code. De bouw start in november 2026, als app op de [[website-wadlicht]].

## Wat het is

Een eenvoudige webapplicatie op de website van Wadlicht waarmee een klant zonder in te loggen een schade meldt, ook op een telefoon. Vervangt het schadeformulier in Mijn Wadlicht.

- Product owner: Fenna de Jong
- Team: [[team-schade]]
- Bron: [[2026-09-15-productvisie-schademelden]]

## Scope eerste versie

| Wel | Niet |
|---|---|
| Particuliere auto-, woon- en inboedel- en aansprakelijkheidsverzekeringen | Zakelijke verzekeringen |
| Foto's toevoegen | Video, documenten anders dan foto's |
| Registreren *dat* er letsel is | Medische details uitvragen |
| Bevestiging met meldingsnummer per e-mail | Status van de melding volgen (komt later, vereist inloggen) |

## Productkennis

| Pagina | Wat |
|---|---|
| [[schademelden-gedrag]] | De stappen die de klant doorloopt |
| [[schademelden-invarianten]] | Wat altijd waar moet blijven (PRD-SCH-INV) |
| [[schademelden-api-en-afhankelijkheden]] | Eigen API, gebruik van het Polisregister, opslag |
| [[schademelden-adr-001-architectuur]] | Architectuurkeuze |

## Regels die dit product raken

| Regel | Waarom |
|---|---|
| [[werkvormen-en-autonomie#ORG-AI-03]] | Letselindicatie is gezondheidsgegeven: mens-geleid |
| [[werkafspraken-team-schade#TS-WA-03]] | Uploads: minimaal gepaard |
| [[informatiebeveiliging#ORG-SEC-01]] | Melden zonder inloggen mag, met verificatie en rate limiting |
| [[informatiebeveiliging#ORG-SEC-05]] | Malwarescan op foto's |
| [[privacy-en-bewaartermijnen#ORG-PRV-04]] | Bewaartermijn foto's |
| [[werkafspraken-team-marketing#TM-WA-05]] | De app gebruikt kop, voet en huisstijl van de website |
| [[klantcommunicatie#ORG-COM-03]] | Teksten in de app op B1-niveau |

## Succes

- 70% van de meldingen via SchadeMelden binnen zes maanden na livegang.
- Minder dan 5% van de meldingen onvolledig.
