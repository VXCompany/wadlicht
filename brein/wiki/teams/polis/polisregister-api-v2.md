---
titel: Polisregister API v2
niveau: team
status: beschrijvend
eigenaar: Team Polis
team: team-polis
regel_prefix: TP-API
bronnen:
  - "[[2026-04-07-release-polisregister-api-v2]]"
bijgewerkt: 2026-04-10
review_voor: 2027-04-01
tags: [niveau/team, team/polis, api]
---

# Polisregister API v2

De API waarmee andere teams polisgegevens controleren. Eigenaar: [[team-polis]]. Afnemer onder meer: [[schademelden]].

## Operaties

### TP-API-01
**`POST /v2/polissen/verificatie` controleert of polisnummer, postcode en geboortedatum bij elkaar horen. Antwoord: `{ "geldig": true | false }`. Geen persoonsgegevens in het antwoord.**
- Bron: [[2026-04-07-release-polisregister-api-v2]]

### TP-API-02
**`GET /v2/polissen/{polisnummer}/status` geeft `actief`, `opgeschort` of `beeindigd`, plus het producttype (`auto`, `woon`, `avp`, `zakelijk`).**
- Bron: [[2026-04-07-release-polisregister-api-v2]]

## Gebruik

- Authenticatie tussen systemen via Microsoft Entra ID (client credentials). Het geheim staat in Key Vault ([[informatiebeveiliging#ORG-SEC-02]]).
- Rate limit: 20 verzoeken per seconde per afnemer.
- API v1 wordt uitgefaseerd per 1 april 2027 ([[referentiearchitectuur#ORG-ARC-05]]).
- Een OpenAPI-specificatie is op aanvraag beschikbaar bij Team Polis. **Hiaat:** de specificatie staat nog niet in het brein of in deze repository.
