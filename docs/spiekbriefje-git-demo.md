# Spiekbriefje: git voor de demo's van De Denkfabriek

Repository: `VXCompany/wadlicht`. De tag `demo-start` is de vaste beginstand.
**Main blijft altijd in de beginstand**: de Slack-sessies klonen vanaf GitHub.

## 1. Eén keer: tag zetten

```bash
git switch main
git pull
git status                      # moet schoon zijn
git tag -a demo-start -m "Beginstand demo Denkfabriek"
git push origin demo-start
```

## 2. Voor elke proefronde

```bash
git switch -C proefdraai demo-start
git status                      # moet schoon zijn
```

`-C` maakt de branch opnieuw aan als hij al bestaat. Obsidian springt vanzelf mee.

## 3. Na een proefronde

Bekijk eerst wat er veranderd is:

```bash
git status
git diff
```

Bewaren om na te kijken:

```bash
git stash push -u -m "proefronde 1"
git stash list                  # overzicht van bewaarde rondes
```

Of weggooien:

```bash
git restore .
git clean -fd                   # let op: verwijdert ook nieuwe bestanden van de agent
```

Daarna weer naar stap 2.

## 4. Opruimen na Slack

Slack-sessies maken eigen branches en pull requests. **Nooit naar main mergen.**

```bash
git fetch --prune
git branch -r                   # overzicht van branches op GitHub
git push origin --delete <branchnaam>
```

Sluit daarnaast de pull request op GitHub.

## 5. Beginstand bewust aanpassen

Alleen als je het brein of de site echt wilt verbeteren.

```bash
git switch main
# wijziging maken
git add <bestanden>
git commit -m "Beschrijving"
git push
git tag -f -a demo-start -m "Beginstand demo Denkfabriek"
git push -f origin demo-start
```

Controleer daarna dat de haakjes er nog in zitten:

- Demo 2: `brein/raw/organisatie/2026-11-04-besluit-ai-governance-board.md` is nog niet verwerkt (geen voorstel over uploads in `brein/wiki/voorstellen/`).
- Demo 3: `PRD-SCH-INV-05` in `brein/wiki/producten/schademelden/schademelden-invarianten.md` zegt nog 10 jaar.

## 6. Obsidian-ruis (optioneel, vóór het zetten van de tag)

Voeg toe aan `.gitignore`:

```
brein/.obsidian/workspace*.json
```

## 7. Op de dag zelf

```bash
git switch -C proefdraai demo-start
git status                      # schoon? dan sta je goed
```

- Claude Code starten vanuit de root van de repository.
- Obsidian open op de vault `brein/`.
- In Slack geen openstaande threads of pull requests van het oefenen.
