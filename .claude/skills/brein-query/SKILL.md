---
name: brein-query
description: Beantwoord een vraag vanuit het Gedeelde Brein van Wadlicht, met regel-ID's uit alle niveaus. Gebruik bij "/brein-query <vraag>", of als een agent of engineer vraagt wat mag, welke regels gelden of welke werkvorm een taak krijgt.
---

# Query: een vraag beantwoorden vanuit het brein

Lees eerst `brein/CLAUDE.md`. Dat schema gaat boven deze instructies.

## Stappen

1. **Bepaal wat de vraag raakt:** welk product, welk team, welke onderwerpen (privacy, security, uploads, architectuur, communicatie, werkvorm).
2. **Lees via `brein/index.md`** de relevante pagina's op alle drie de niveaus. Begin altijd bij [[werkvormen-en-autonomie]] als de vraag over een uit te voeren taak gaat. Volg `Afgeleid van`-links omhoog en `Achtergrond`-links naar incidenten.
3. **Kijk ook in `brein/wiki/vragen/`** of de vraag al eerder is beantwoord. Zo ja, controleer of dat antwoord nog klopt.
4. **Pas de rangorde toe:** organisatie gaat voor team, team voor product. Een lager niveau mag aanscherpen. Vind je een versoepeling, meld die apart en baseer het antwoord op de strengste geldige regel.
5. **Bepaal bij een taak de werkvorm** (Autonoom, Gepaard, Mens-geleid) op basis van de regels, en zeg dat de tech lead die bevestigt.
6. **Meld hiaten:** ontbrekende, verouderde (`review_voor` verstreken) of tegenstrijdige kennis. Zeg wat dit betekent voor een agent ([[werkvormen-en-autonomie#ORG-AI-06]]).

## Vorm van het antwoord

1. Het antwoord in één of twee zinnen.
2. Een tabel met onderbouwing:

| Niveau | Regel | Wat het zegt voor deze vraag |
|---|---|---|

3. Relevante achtergrond (bijvoorbeeld een incident), kort.
4. Hiaten, als die er zijn.

Citeer alleen regels die in het brein staan. Vul geen gaten met aannames; zeg dat iets ontbreekt.

## Opslaan

Vraagt de gebruiker om het antwoord op te slaan:

1. Maak `brein/wiki/vragen/VR-<jaar>-NNN-<korte-naam>.md` op basis van `brein/_sjablonen/vraag.md`, met het volgende vrije nummer.
2. Werk `brein/index.md` bij (sectie Vragen).
3. Voeg een regel toe aan `brein/log.md`: `## [JJJJ-MM-DD] query | <vraag>`.

Een opgeslagen antwoord heeft status `concept`. Het is geen nieuwe regel; het verwijst naar regels.
