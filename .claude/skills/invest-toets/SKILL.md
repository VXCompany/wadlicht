---
name: invest-toets
description: Toets een nieuwe intentie (user story) aan de INVEST-afspraken van het team (TS-IT-01 t/m 06) voordat het brein wordt bevraagd. Gebruik bij "/invest-toets <intentie>" en altijd als eerste stap bij een nieuwe intentie in #wadlicht-intake.
---

# INVEST-toets: is de intentie klaar voor het brein?

Lees eerst `brein/CLAUDE.md`. Dat schema gaat boven deze instructies.

Deze toets beoordeelt alleen de **formulering** van de intentie. Regels, risico en werkvorm komen daarna, met `/brein-query`.

## Stappen

1. **Bepaal het team** dat eigenaar is van het product dat de intentie raakt (via `brein/index.md` en de productpagina's). Voor SchadeMelden is dat Team Schade.
2. **Lees de INVEST-afspraken van dat team.** Voor Team Schade: `brein/wiki/teams/schade/intake-invest-team-schade.md`. Heeft het team geen INVEST-pagina, toets dan alleen op [[werkvormen-en-autonomie#ORG-AI-02]] (eenduidige en testbare acceptatiecriteria) en meld het hiaat.
3. **Beoordeel de intentie per regel**, TS-IT-01 tot en met TS-IT-06. Gebruik alleen wat in de intentie staat.
4. **Bepaal de uitkomst:**
   - **Geschikt:** voldoet aan TS-IT-01 (Testable) en TS-IT-02 (Small).
   - **Verduidelijking nodig:** voldoet niet aan TS-IT-01, of de omvang is onduidelijk.
   - **Opsplitsen:** omvat meer dan één samenhangende wijziging (TS-IT-02).
5. **Geef advies** op TS-IT-03 tot en met TS-IT-06, alleen als er iets te melden is. Advies bepaalt nooit de uitkomst.

## Vorm van het antwoord

```
INVEST-toets: <Geschikt | Verduidelijking nodig | Opsplitsen>

Bindend
- TS-IT-01 Testable: voldoet / voldoet niet. <één zin waarom>
- TS-IT-02 Small: voldoet / voldoet niet. <één zin waarom>

Advies
- <TS-IT-0N>: <één zin>   (alleen als er iets te melden is)

Vragen of voorstel   (alleen bij verduidelijking of opsplitsen)
1. <gerichte vraag of kleinere intentie>
```

Maximaal drie vragen. Stel ze zo dat het antwoord direct een toetsbaar criterium oplevert, bijvoorbeeld: "Hoeveel foto's mag een klant maximaal uploaden, en wat ziet hij bij meer?"

Is de uitkomst **Geschikt**, sluit dan af met de acceptatiecriteria zoals je ze hebt begrepen, in één lijstje. Die zijn de basis voor de testscenario's ([[testscenarios-team-schade]]).

## Grenzen

- Verzin geen acceptatiecriteria of waarden. Ontbreken ze, stel een vraag.
- Haal geen waarden uit het brein om de intentie aan te vullen. Dat gebeurt in de volgende stap, met bronvermelding.
- Beoordeel geen risico, privacy of werkvorm. Een geschikte intentie is nog geen toestemming.
- Wijzig de INVEST-pagina niet. Hiaten of onduidelijkheden meld je; een wijziging gaat via een voorstel ([[werkvormen-en-autonomie#ORG-AI-05]]).
- De toets wordt niet in `brein/log.md` vastgelegd. Het resultaat staat in de thread.
