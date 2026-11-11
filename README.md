# Wadlicht Verzekeringen

Demo-repository van **Wadlicht Verzekeringen**, een fictieve schadeverzekeraar uit Harlingen. Gebruikt door VX Company om de hybride software factory en het Gedeelde Brein te demonstreren.

> Wadlicht bestaat niet. Alle namen, regels, cijfers en contactgegevens zijn verzonnen.

## Inhoud

| Map | Wat |
|---|---|
| [`site/`](site/) | De publieke website: Hugo, eigen thema, Azure Static Web Apps |
| [`brein/`](brein/) | Het Gedeelde Brein: organisatie, Team Marketing, Team Schade, Team Polis en product SchadeMelden. Open als vault in Obsidian. |
| [`.claude/skills/`](.claude/skills/) | `/brein-ingest`, `/brein-query`, `/brein-lint` voor Claude Code |
| [`.github/workflows/`](.github/workflows/) | Bouwen en publiceren naar Azure Static Web Apps |
| [`docs/`](docs/) | Inrichting van de demo: [Claude Tag en Slack](docs/demo-setup-claude-tag.md), [spiekbriefje git](docs/spiekbriefje-git-demo.md) |

## Website lokaal draaien

Vereist [Hugo](https://gohugo.io) extended, versie 0.158 of hoger (getest met 0.169.0).

```bash
brew install hugo      # macOS
cd site
hugo server
```

Open http://localhost:1313.

## Publiceren naar Azure

1. Maak een Static Web App aan, bijvoorbeeld:

   ```bash
   az staticwebapp create \
     --name swa-wadlicht-demo \
     --resource-group rg-wadlicht-demo \
     --location westeurope \
     --sku Free
   ```

   Voor de latere SchadeMelden-API (gekoppelde Azure Functions) is het Standard-plan nodig.

2. Haal het deployment-token op en zet het als GitHub-secret `AZURE_STATIC_WEB_APPS_API_TOKEN`:

   ```bash
   az staticwebapp secrets list --name swa-wadlicht-demo --query "properties.apiKey" -o tsv
   ```

3. Push naar `main`. De workflow bouwt de site met Hugo en publiceert `site/public`. Pull requests krijgen een previewomgeving.

## Het Gedeelde Brein

Zie [`brein/README.md`](brein/README.md) en het schema in [`brein/CLAUDE.md`](brein/CLAUDE.md).
