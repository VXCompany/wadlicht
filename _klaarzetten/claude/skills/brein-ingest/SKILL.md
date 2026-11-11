---
name: brein-ingest
description: Verwerk een nieuwe bron uit brein/raw/ in het Gedeelde Brein van Wadlicht. Gebruik bij "/brein-ingest <pad>", of als iemand vraagt een besluit, notulen, beleid of incidentrapport in het brein te verwerken.
---

# Ingest: een nieuwe bron verwerken

Je verwerkt één bron uit `brein/raw/` in de wiki van het Gedeelde Brein. Lees eerst `brein/CLAUDE.md`. Dat schema gaat boven deze instructies.

## Invoer

Een pad onder `brein/raw/` (bijvoorbeeld `raw/organisatie/2026-11-04-besluit-ai-governance-board.md`). Paden zijn relatief aan `brein/`. Geen pad gegeven: vraag erom. Pad buiten `raw/`: weiger en leg uit dat alleen bronnen in `raw/` worden verwerkt.

## Stappen

1. **Lees** `brein/CLAUDE.md`, `brein/index.md` en de laatste twintig regels van `brein/log.md`. Controleer in het log of deze bron al is verwerkt; zo ja, meld dat en vraag of hij opnieuw moet.
2. **Lees de bron.** Wijzig hem nooit.
3. **Splits de bron in losse besluiten, regels of feiten.** Bepaal per onderdeel:
   - op welk niveau het hoort (organisatie, team, product);
   - op welke bestaande pagina, of dat er een nieuwe nodig is;
   - de status van die pagina.
4. **Handel per onderdeel volgens de status van de doelpagina:**
   - `beschrijvend` of `concept`: werk de pagina bij. Voeg de bron toe aan `bronnen`, zet `bijgewerkt` op vandaag.
   - `richtinggevend` of `bindend`: wijzig de pagina **niet**. Schrijf een voorstel in `brein/wiki/voorstellen/` op basis van `brein/_sjablonen/voorstel.md`. Gebruik het volgende vrije nummer `VS-<jaar>-NNN`. Vul altijd de kop **Wat Claude niet zelf doet** in.
   - Nieuwe pagina nodig op organisatie- of teamniveau met bindende of richtinggevende inhoud: maak geen pagina, maar een voorstel.
5. **Zoek doorwerking.** Welke regels op lagere niveaus raken door dit besluit? Noem ze in het voorstel onder **Geraakt**. Wordt een lagere regel overbodig of strijdig, meld dat; pas hem niet aan.
6. **Werk `brein/index.md` bij** (nieuwe pagina's en voorstellen).
7. **Voeg een regel toe aan `brein/log.md`** in het vaste formaat: `## [JJJJ-MM-DD] ingest | <pad>` met daaronder per onderdeel wat er is gebeurd.

## Uitvoer naar de gebruiker

Een tabel per besluit of onderdeel:

| Onderdeel | Doelpagina | Status | Wat Claude deed |
|---|---|---|---|

Daaronder: welke voorstellen zijn aangemaakt en wie beslist, en een `git status`-overzicht van gewijzigde bestanden. Benadruk welke bindende pagina's **niet** zijn aangeraakt.

## Nooit

- Bestanden in `raw/` wijzigen.
- Bindende of richtinggevende pagina's inhoudelijk wijzigen, ook niet "alvast".
- `CLAUDE.md` wijzigen.
- Commits maken. De gebruiker reviewt en commit zelf.
