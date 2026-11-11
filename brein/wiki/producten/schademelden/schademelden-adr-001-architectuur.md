---
titel: "ADR-001: SchadeMelden als app binnen de Static Web App"
niveau: product
status: beschrijvend
eigenaar: Team Schade
team: team-schade
regel_prefix: PRD-SCH-ADR
adr_status: geaccepteerd
bronnen:
  - "[[2026-09-08-kickoff-websitevernieuwing]]"
  - "[[2026-02-02-referentiearchitectuur-2026]]"
bijgewerkt: 2026-10-28
review_voor: 2027-04-01
tags: [niveau/product, product/schademelden, adr]
---

# ADR-001: SchadeMelden als app binnen de Static Web App

- Status: geaccepteerd, 28 oktober 2026
- Besloten door: Ruben Kingma (tech lead Team Schade), na overleg met Nadia (webdeveloper Team Marketing) en Pieter Zijlstra (Enterprise architect)

## Context

[[schademelden]] moet op de website van Wadlicht komen, met dezelfde kop, voet en huisstijl ([[werkafspraken-team-marketing#TM-WA-05]]). De website is een Hugo-site op Azure Static Web Apps ([[website-wadlicht]]).

## Besluit

1. De front-end van SchadeMelden is een sectie van de Hugo-site (`site/content/schade-melden/` met een eigen layout), gebouwd met HTML, CSS en een beperkte hoeveelheid JavaScript ([[codeerrichtlijnen-team-schade#TS-CR-06]]).
2. De API is een Azure Functions-app in .NET 10, isolated worker, gekoppeld aan de Static Web App als backend. Code in `api/` in deze repository.
3. Foto's gaan via een kortlevende upload-URL rechtstreeks naar Blob Storage, niet via de Functions-app.

## Alternatieven

| Alternatief | Waarom niet |
|---|---|
| Losse single-page app op een eigen domein | Eigen huisstijl en navigatie, botst met TM-WA-05 |
| Formulier in Mijn Wadlicht laten | Vereist inloggen, werkt slecht op telefoons |
| Foto's via de Functions-app uploaden | Extra limiet in een extra laag, precies wat bij [[incidenten-team-schade#INC-2026-041]] misging |

## Gevolgen

- De Static Web App heeft het Standard-plan nodig voor een gekoppelde Functions-app.
- Team Schade en Team Marketing werken in dezelfde repository. Wijzigingen aan menu en homepage gaan gepaard met Team Marketing ([[werkafspraken-team-marketing#TM-WA-05]]).
- **Te verifiëren bij de bouw:** de ondersteunde runtimeversies voor gekoppelde Functions-apps en de netwerkopzet voor private endpoints.
