---
name: brein-lint
description: Controleer het Gedeelde Brein van Wadlicht op versoepelingen tussen niveaus, tegenstrijdigheden, verouderde pagina's, ontbrekende bronnen en invarianten zonder test. Gebruik bij "/brein-lint" of bij de wekelijkse controle.
---

# Lint: het brein controleren

Lees eerst `brein/CLAUDE.md`. Dat schema gaat boven deze instructies. Je lost niets zelf op. Je meldt, en schrijft voorstellen waar een eigenaar moet beslissen.

## Controles

Loop alle pagina's in `brein/wiki/` langs. Gebruik vandaag als peildatum.

| # | Controle | Ernst |
|---|---|---|
| 1 | **Versoepeling:** een regel op team- of productniveau is soepeler dan een regel op een hoger niveau over hetzelfde onderwerp (langere bewaartermijn, hogere drempel, minder review, verouderde versie). | hoog |
| 2 | **Tegenstrijdigheid:** twee regels op hetzelfde niveau spreken elkaar tegen. | hoog |
| 3 | **Verwijzing naar vervallen bron:** een regel noemt een bron of beleidsversie die is vervangen. | midden |
| 4 | **Verouderd:** `review_voor` ligt in het verleden. | midden |
| 5 | **Onverwerkte bron:** een bestand in `raw/` komt niet voor in `log.md`. | midden |
| 6 | **Invariant zonder test:** een `PRD-*-INV` heeft `Test: nog niet aanwezig`, of noemt een test die niet in de repository bestaat. Bij een product dat nog niet gebouwd is: één samenvattende bevinding. | laag |
| 7 | **Gebroken link of ontbrekende bron:** een wikilink wijst naar een niet-bestaande pagina of kop, of een pagina heeft geen `bronnen`. | laag |
| 8 | **Open voorstellen:** voorstellen met `voorstel_status: open` ouder dan 30 dagen. | laag |

Controleer bij versoepelingen ook de bron in `raw/`, niet alleen de wikipagina.

## Voorstellen

Voor elke bevinding met ernst **hoog** schrijf je een voorstel in `brein/wiki/voorstellen/` (sjabloon `brein/_sjablonen/voorstel.md`), gericht aan de eigenaar van de pagina die moet veranderen. Noem onder **Wat Claude niet zelf doet** expliciet wat onomkeerbaar is of buiten de bevoegdheid van een agent valt, zoals het verwijderen van gegevens of het wijzigen van een bewaartermijn ([[werkvormen-en-autonomie#ORG-AI-03]]).

## Uitvoer

Een tabel met bevindingen, ernstigste bovenaan:

| # | Ernst | Bevinding | Pagina's en regels | Wie beslist | Voorstel |
|---|---|---|---|---|---|

Daarna: aantal pagina's gecontroleerd, aantal bevindingen per ernst.

## Afsluiten

1. Werk `brein/index.md` bij (nieuwe voorstellen).
2. Voeg een regel toe aan `brein/log.md`: `## [JJJJ-MM-DD] lint | wekelijkse controle` met de samenvatting.

## Nooit

- Een bevinding oplossen door een van beide pagina's aan te passen.
- `raw/` of `CLAUDE.md` wijzigen.
