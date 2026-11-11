---
titel: SchadeMelden, API en afhankelijkheden
niveau: product
status: beschrijvend
eigenaar: Team Schade
team: team-schade
regel_prefix: PRD-SCH-API
bronnen:
  - "[[2026-09-15-productvisie-schademelden]]"
  - "[[2026-04-07-release-polisregister-api-v2]]"
bijgewerkt: 2026-10-25
review_voor: 2027-01-31
tags: [niveau/product, product/schademelden, api]
---

# SchadeMelden, API en afhankelijkheden

Beoogde API van [[schademelden]]. De API draait als Azure Functions achter de Static Web App, zie [[schademelden-adr-001-architectuur]].

## Eigen API

### PRD-SCH-API-01
**`POST /api/verificatie`: controleert polisgegevens via het Polisregister. Antwoord: geldig of niet, en het producttype. Met rate limiting per IP-adres.**
- Afgeleid van: [[informatiebeveiliging#ORG-SEC-01]]

### PRD-SCH-API-02
**`POST /api/meldingen`: maakt een concept-melding aan en geeft een upload-URL per foto terug. Idempotent op een sleutel die de browser meestuurt.**
- Ondersteunt: [[schademelden-invarianten#PRD-SCH-INV-02]]

### PRD-SCH-API-03
**`POST /api/meldingen/{id}/versturen`: controleert dat alle foto's zijn opgeslagen en gescand, registreert de melding definitief, geeft het meldingsnummer terug en verstuurt de bevestigingsmail.**
- Ondersteunt: [[schademelden-invarianten#PRD-SCH-INV-03]]

## Afhankelijkheden

| Afhankelijkheid | Eigenaar | Gebruik | Kennis |
|---|---|---|---|
| Polisregister API v2 | [[team-polis]] | Verificatie en polisstatus | [[polisregister-api-v2]] |
| Azure Blob Storage | Team Schade | Opslag van foto's, private endpoint | [[referentiearchitectuur#ORG-ARC-04]] |
| Microsoft Defender for Storage | Platformteam | Malwarescan bij upload | [[informatiebeveiliging#ORG-SEC-05]] |
| Azure Communication Services (e-mail) | Platformteam | Bevestigingsmail | nog geen kennis in het brein |
| Schadebehandelsysteem | Team Schade | Ontvangt de definitieve melding | nog geen kennis in het brein |

## Hiaten

- De koppeling met het schadebehandelsysteem is nog niet beschreven.
- De OpenAPI-specificatie van de Polisregister API v2 ontbreekt in het brein.
