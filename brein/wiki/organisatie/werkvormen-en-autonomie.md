---
titel: Werkvormen en autonomie van agents
niveau: organisatie
status: bindend
eigenaar: AI Governance Board
regel_prefix: ORG-AI
bronnen:
  - "[[2026-06-15-ai-governance-kader-v1]]"
bijgewerkt: 2026-06-20
review_voor: 2026-12-15
tags: [niveau/organisatie, domein/ai]
---

# Werkvormen en autonomie van agents

Regels uit het [[2026-06-15-ai-governance-kader-v1|kader voor AI in softwareontwikkeling]]. Deze pagina is de ondergrens: een team mag strenger zijn, nooit soepeler.

| Werkvorm | Wie voert uit | Verificatie |
|---|---|---|
| Autonoom | Agent | Verificatie-agent en quality gates, steekproef door engineer |
| Gepaard | Engineer en agent samen | Verificatie-agent, review door een andere engineer |
| Mens-geleid | Engineer, agent assisteert | Review door een andere engineer, specialist waar vereist |

### ORG-AI-01
**Elke taak krijgt een werkvorm: Autonoom, Gepaard of Mens-geleid. De tech lead van het team bevestigt de werkvorm.**
- Bron: [[2026-06-15-ai-governance-kader-v1]], Werkvormen

### ORG-AI-02
**Autonoom mag alleen bij laag risico, een bekend patroon, eenduidige en testbare acceptatiecriteria, en complete en actuele productkennis.**
- Bron: [[2026-06-15-ai-governance-kader-v1]], Wanneer autonoom

### ORG-AI-03
**Altijd mens-geleid: authenticatie en autorisatie, verwerking van gezondheidsgegevens, betalingen en uitkeringen, en wijzigingen aan bewaartermijnen en verwijderprocessen.**
- Bron: [[2026-06-15-ai-governance-kader-v1]], Altijd mens-geleid

### ORG-AI-04
**Wie het werk doet, controleert het niet. Dat geldt voor agents en mensen.**
- Bron: [[2026-06-15-ai-governance-kader-v1]], Overige regels

### ORG-AI-05
**Agents wijzigen geen bindende of richtinggevende kennis. Ze schrijven een voorstel.**
- Bron: [[2026-06-15-ai-governance-kader-v1]], Overige regels
- Uitwerking: het schema van het brein (`CLAUDE.md`)

### ORG-AI-06
**Een agent die ontbrekende, verouderde of tegenstrijdige kennis tegenkomt, stopt en draagt het werk over aan een engineer.**
- Bron: [[2026-06-15-ai-governance-kader-v1]], Overige regels

### ORG-AI-07
**Publicatie van klantgerichte content (website, e-mail aan klanten) vereist goedkeuring door een mens.**
- Bron: [[2026-06-15-ai-governance-kader-v1]], Overige regels
- Zie ook: [[klantcommunicatie#ORG-COM-05]]
