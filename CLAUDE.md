# Wadlicht Verzekeringen, demo-repository

Wadlicht Verzekeringen is een fictieve schadeverzekeraar uit Harlingen (420 medewerkers, toezicht door DNB en AFM), gebruikt voor demonstraties van de hybride software factory van VX Company.

## Opbouw

| Map | Wat | Eigenaar |
|---|---|---|
| `site/` | Publieke website, Hugo, gehost op Azure Static Web Apps | Team Marketing |
| `brein/` | Het Gedeelde Brein: kennis op organisatie-, team- en productniveau (Obsidian-vault) | Per pagina, zie `brein/CLAUDE.md` |
| `.claude/skills/` | Operaties op het brein: `/brein-ingest`, `/brein-query`, `/brein-lint` | AI Governance Board |
| `.github/workflows/` | Bouwen en publiceren van de website | Team Marketing |

## Werken in deze repository

Voordat je een taak uitvoert die code of content wijzigt:

1. Bepaal welk team en welk product de taak raakt.
2. Raadpleeg het Gedeelde Brein (`/brein-query`, of lees via `brein/index.md`): minimaal `brein/wiki/organisatie/werkvormen-en-autonomie.md`, de teampagina's en de productpagina's.
3. Stel de werkvorm vast (Autonoom, Gepaard, Mens-geleid) en noem die vóór je begint. De tech lead bevestigt.
4. Stuit je op ontbrekende, verouderde of tegenstrijdige kennis: stop en meld het (ORG-AI-06).
5. Maak geen commits en push niet zonder opdracht.

Website lokaal bekijken: `cd site && hugo server`.

## Schema van het brein

@brein/CLAUDE.md
