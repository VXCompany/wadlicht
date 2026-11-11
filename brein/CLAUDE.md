# Schema van het Gedeelde Brein van Wadlicht

Dit bestand bepaalt hoe Claude (en elke andere agent) het Gedeelde Brein leest, bijwerkt en controleert. Het schema is van mensen. Claude wijzigt dit bestand nooit zelf; een wijziging gaat via een voorstel in `wiki/voorstellen/` aan de AI Governance Board.

## Wat het brein is

Het Gedeelde Brein is een LLM-wiki: kennis wordt één keer samengesteld uit bronnen en daarna bijgehouden, in plaats van bij elke vraag opnieuw gezocht. Mensen en agents lezen dezelfde pagina's.

Het brein bevat **wat we weten en verwachten**. Het is geen bewijs. Wat daadwerkelijk getest of aangetoond is, staat in de Evidence Layer (Git, CI, testresultaten), niet hier.

## De drie lagen

| Laag | Map | Wie schrijft | Regel |
|---|---|---|---|
| Bronnen | `raw/` | Mensen | Onveranderlijk. Claude leest, wijzigt en verwijdert nooit. |
| Wiki | `wiki/` | Claude en mensen | Samengestelde kennis met bronverwijzing. Wat Claude mag, hangt af van de status (zie onder). |
| Schema | `CLAUDE.md` | Mensen | Dit bestand. |

Daarnaast: `index.md` (catalogus van alle wikipagina's) en `log.md` (chronologisch logboek, alleen aanvullen).

## Kennisniveaus en rangorde

| Niveau | Map | Eigenaar | Kleur in Obsidian |
|---|---|---|---|
| Organisatie | `wiki/organisatie/` | Per pagina: CISO, Privacy Officer, AI Governance Board, Enterprise architect, Compliance | blauw |
| Team | `wiki/teams/<team>/` | Het team (tech lead of teamlead) | oranje |
| Product | `wiki/producten/<product>/` | Het productteam, engineers zijn beheerder | groen |
| Voorstel | `wiki/voorstellen/` | Indiener, beslissing bij eigenaar van de doelpagina | rood |
| Vraag | `wiki/vragen/` | Opgeslagen antwoorden | paars |

**Rangorde: organisatie gaat voor team, team gaat voor product.**
**Een lager niveau mag een regel aanscherpen, nooit versoepelen.**

Voorbeelden: een team mag een strengere CVSS-drempel hanteren dan het beleid (bijvoorbeeld blokkeren vanaf 6.0 als het beleid 7.0 zegt), maar geen soepelere (9.0). Een product mag gegevens korter bewaren dan het beleid, nooit langer.

## Status van een pagina

Elke wikipagina heeft een `status` in de frontmatter. Die bepaalt wat Claude mag.

| Status | Bijvoorbeeld | Wat Claude mag |
|---|---|---|
| `bindend` | Beleid, referentiearchitectuur | Lezen en citeren. Inhoud wijzigen alleen via een voorstel in `wiki/voorstellen/`. |
| `richtinggevend` | Werkafspraken, richtlijnen, huisstijl | Links, spelling en opmaak herstellen. Inhoud via een voorstel. |
| `beschrijvend` | Productgedrag, invarianten, API-contracten | Bijwerken. Een engineer van het eigenaarsteam accepteert de wijziging via de review in git. |
| `concept` | Voorstellen, opgeslagen vragen | Vrij bijwerken. |

Twijfel je over de status, behandel de pagina dan als `bindend`.

## Frontmatter

Elke wikipagina begint met:

```yaml
---
titel: Privacy en bewaartermijnen
niveau: organisatie            # organisatie | team | product | voorstel | vraag
status: bindend                # bindend | richtinggevend | beschrijvend | concept
eigenaar: Privacy Officer
team:                          # alleen bij team- en productpagina's, bijv. team-schade
regel_prefix: ORG-PRV          # als de pagina regels met een ID bevat
bronnen:
  - "[[2026-10-01-privacybeleid-v3]]"
bijgewerkt: 2026-10-03
review_voor: 2027-04-01        # na deze datum markeert de lint de pagina als verouderd
tags: [niveau/organisatie]
---
```

## Regel-ID's

Elke regel, afspraak of invariant heeft een vaste code. De code staat als kop van niveau 3, zodat je er rechtstreeks naar kunt linken: `[[privacy-en-bewaartermijnen#ORG-PRV-03]]`.

| Niveau | Formaat | Voorbeeld |
|---|---|---|
| Organisatie | `ORG-<DOMEIN>-NN` | `ORG-PRV-03`, `ORG-SEC-04`, `ORG-AI-03`, `ORG-ARC-02`, `ORG-COM-01` |
| Team | `T<team>-<SOORT>-NN` | `TS-WA-03` (Team Schade, werkafspraak), `TP-WA-04` (Team Polis), `TM-HS-02` (Team Marketing, huisstijl) |
| Product | `PRD-<PRODUCT>-<SOORT>-NN` | `PRD-SCH-INV-04` (SchadeMelden, invariant), `PRD-SCH-API-01` |
| Voorstel | `VS-<jaar>-NNN` | `VS-2026-001` |
| Vraag | `VR-<jaar>-NNN` | `VR-2026-001` |

Codes worden nooit hergebruikt. Een vervallen regel blijft staan met `**Vervallen per <datum>**` en een verwijzing naar de vervanger.

Een regel op team- of productniveau die voortkomt uit een hogere regel, linkt omhoog met `Afgeleid van:`. Elke productinvariant noemt de test die haar controleert (`Test:`). De naam van die test bevat het regel-ID met underscores, bijvoorbeeld `PRD_SCH_INV_04_letselindicatie_alleen_zichtbaar_voor_letselbehandelaar`.

Vorm van een regel:

```markdown
### ORG-PRV-03
**Gezondheidsgegevens bij een schade zijn alleen toegankelijk voor medewerkers met de rol letselbehandelaar.**
- Bron: [[2026-10-01-privacybeleid-v3]], paragraaf 4.2
- Toelichting: ...
```

## Links

- Gebruik Obsidian-wikilinks op bestandsnaam: `[[privacy-en-bewaartermijnen]]`. Bestandsnamen zijn uniek in de hele vault.
- Elke bewering op een wikipagina is terug te leiden naar een bron in `raw/` of naar een hogere regel.
- Verwijs naar code, tests en releases met een pad of URL in de repository. Kopieer geen testresultaten in het brein.

## Operaties

Er zijn drie operaties, vastgelegd als skills in `.claude/skills/`:

| Operatie | Skill | Wat |
|---|---|---|
| Ingest | `/brein-ingest <pad in raw/>` | Nieuwe bron verwerken. Beschrijvende kennis bijwerken, voor bindende en richtinggevende kennis een voorstel schrijven. |
| Query | `/brein-query <vraag>` | Vraag beantwoorden met regel-ID's uit alle niveaus. Hiaten melden. Op verzoek het antwoord opslaan in `wiki/vragen/`. |
| Lint | `/brein-lint` | Controleren op versoepelingen, tegenstrijdigheden, verouderde pagina's, ontbrekende bronnen en invarianten zonder test. |

Elke operatie werkt `index.md` en `log.md` bij.

## Voorstellen

Een voorstel is een pagina in `wiki/voorstellen/` op basis van `_sjablonen/voorstel.md`, met status `concept`. Het voorstel bevat: aanleiding, de huidige tekst, de voorgestelde tekst, welke regels en pagina's geraakt worden, en een kop **Wat Claude niet zelf doet**. De eigenaar van de doelpagina beslist. Pas na een besluit wijzigt een mens de doelpagina, of geeft een mens Claude daar expliciet opdracht toe.

## Wat Claude nooit doet

- Bestanden in `raw/` wijzigen, verplaatsen of verwijderen.
- De inhoud van een `bindend` of `richtinggevend` pagina wijzigen zonder besluit van de eigenaar.
- Dit schema wijzigen.
- Een tegenstrijdigheid zelf oplossen door één van beide kanten aan te passen. Claude meldt haar en noemt wie beslist.
- Onomkeerbare acties voorstellen als vanzelfsprekend, zoals het verwijderen van klantgegevens. Die horen bij de eigenaar.
- Persoonsgegevens van klanten of medewerkers in het brein zetten. Rollen en functies wel, namen alleen van eigenaren en teamleden.

## Werkwijze bij gebruik door een development agent

Een agent die een taak uitvoert, leest vooraf:

1. de organisatiepagina's die de taak raakt (minimaal [[werkvormen-en-autonomie]]);
2. de teampagina's van het team dat eigenaar is;
3. de productpagina's, inclusief invarianten en afhankelijkheden.

Stuit de agent op ontbrekende, verouderde of tegenstrijdige kennis, dan stopt hij en draagt het werk over aan een engineer ([[werkvormen-en-autonomie#ORG-AI-06]]).
