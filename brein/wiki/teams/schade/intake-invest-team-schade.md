---
titel: Intake van intenties (INVEST) Team Schade
niveau: team
status: richtinggevend
eigenaar: Team Schade
team: team-schade
regel_prefix: TS-IT
bronnen:
  - "[[2026-06-15-ai-governance-kader-v1]]"
  - "[[2026-10-24-retro-notulen]]"
bijgewerkt: 2026-11-24
review_voor: 2027-05-31
tags: [niveau/team, team/schade]
---

# Intake van intenties (INVEST) Team Schade

Een intentie (user story) gaat pas naar het brein en naar uitvoering als ze helder en toetsbaar genoeg is. We toetsen met INVEST: Independent, Negotiable, Valuable, Estimable, Small, Testable. Bij werk met agents wegen **Testable** en **Small** het zwaarst: die zijn bindend voor de toets. De andere vier geven advies.

De toets wordt uitgevoerd met de skill `invest-toets`, als eerste stap na het plaatsen van een intentie in `#wadlicht-intake`. De toets beoordeelt alleen de formulering. Risico, privacy en werkvorm volgen daarna, uit het brein ([[werkvormen-en-autonomie]]).

> Herkomst: deze afspraken zijn vastgesteld op 24 november 2026 bij de voorbereiding van de demo. Een bronnotitie in `raw/team-schade/` ontbreekt nog. TS-IT-01 en TS-IT-02 zijn wel terug te leiden naar hogere regels.

### TS-IT-01
**Testable: een intentie bevat minstens één acceptatiecriterium dat objectief toetsbaar is: een meetbare grens, een concreet verwacht resultaat of een gegeven-als-dan.**
- Afgeleid van: [[werkvormen-en-autonomie#ORG-AI-02]] (eenduidige en testbare acceptatiecriteria)
- Gewicht: bindend voor de toets
- Bij afwijking: gerichte vragen in de thread naar ontbrekende grenzen of verwachte resultaten. Nooit zelf criteria verzinnen.
- Voorbeeld: "Hoeveel foto's mag een klant maximaal uploaden, en wat ziet hij als hij die grens overschrijdt?"

### TS-IT-02
**Small: een intentie beschrijft één samenhangende wijziging die als geheel te verifiëren en te reviewen is in één korte pull request.**
- Sluit aan op: [[werkafspraken-team-schade#TS-WA-01]] (korte pull requests), [[werkvormen-en-autonomie#ORG-AI-04]] (onafhankelijke controle)
- Gewicht: bindend voor de toets
- Bij afwijking: een voorstel om de intentie op te splitsen in kleinere intenties.
- Voorbeeld: "Foto's uploaden" en "foto's automatisch beoordelen" zijn twee intenties.

### TS-IT-03
**Valuable: de intentie noemt voor wie de wijziging is en welk doel ermee wordt bereikt.**
- Gewicht: advies

### TS-IT-04
**Independent: de intentie is uit te voeren zonder te wachten op andere, nog niet afgeronde intenties.**
- Gewicht: advies
- Bij afwijking: de afhankelijkheid noemen in de thread.

### TS-IT-05
**Negotiable: de intentie beschrijft het gewenste resultaat, niet de technische oplossing.**
- Gewicht: advies
- Toelichting: bij agents gaat eenduidigheid voor onderhandelingsruimte. Een vaste grens (zoals een limiet) is geen oplossing maar een criterium.

### TS-IT-06
**Estimable: de omvang van de intentie is in te schatten.**
- Gewicht: advies
- Toelichting: inschatten weegt bij agentwerk minder zwaar. Alleen melden als de omvang volstrekt onduidelijk is.

## Uitkomst van de toets

| Uitkomst | Wanneer | Wat de agent doet |
|---|---|---|
| **Geschikt** | Voldoet aan TS-IT-01 en TS-IT-02 | Door naar het brein: regels, risico en werkvorm |
| **Verduidelijking nodig** | Voldoet niet aan TS-IT-01, of TS-IT-02 is onduidelijk | Maximaal drie gerichte vragen in de thread, daarna opnieuw toetsen |
| **Opsplitsen** | Te groot volgens TS-IT-02 | Voorstel voor kleinere intenties, wachten op bevestiging |

Advies op TS-IT-03 tot en met TS-IT-06 gaat altijd mee, maar houdt een intentie nooit tegen.

## Relatie met andere regels

- Een geschikte intentie is nog geen toestemming. De werkvorm volgt uit [[werkvormen-en-autonomie]] en de werkafspraken, zoals [[werkafspraken-team-schade#TS-WA-03]] voor uploads.
- De acceptatiecriteria uit TS-IT-01 worden testscenario's volgens [[testscenarios-team-schade]].
