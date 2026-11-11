# Release notes Polisregister API v2

- Datum: 7 april 2026
- Team: Team Polis

## Nieuw

- `GET /v2/polissen/{polisnummer}/status` geeft de status van een polis: `actief`, `opgeschort` of `beeindigd`, plus het producttype.
- `POST /v2/polissen/verificatie` controleert of een combinatie van polisnummer, postcode en geboortedatum bij elkaar hoort. Geeft alleen `true` of `false` terug, geen persoonsgegevens.
- Authenticatie tussen systemen via Microsoft Entra ID (client credentials).
- Rate limit: 20 verzoeken per seconde per afnemer.

## Uitfasering

- API v1 wordt uitgefaseerd per 1 april 2027.
