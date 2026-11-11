---
titel: Website wadlicht
niveau: team
status: beschrijvend
eigenaar: Team Marketing
team: team-marketing
bronnen:
  - "[[2026-09-08-kickoff-websitevernieuwing]]"
bijgewerkt: 2026-11-11
review_voor: 2027-05-01
tags: [niveau/team, team/marketing]
---

# Website Wadlicht

De publieke website van Wadlicht. Gebouwd met Hugo, gehost op Azure Static Web Apps ([[referentiearchitectuur#ORG-ARC-02]]).

## Opbouw in de repository

| Pad | Inhoud |
|---|---|
| `site/hugo.toml` | Configuratie, menu's, algemene gegevens (plaats, e-mail) |
| `site/content/` | Pagina's als Markdown: home, over ons, visie, verzekeringen, nieuws, contact, privacy |
| `site/layouts/` | Eigen templates (geen extern thema): `baseof`, `index`, `list`, `single`, partials voor kop, voet en kaarten |
| `site/assets/css/main.css` | Alle opmaak, met de huisstijlkleuren als variabelen ([[huisstijl-en-tone-of-voice#TM-HS-01]]) |
| `site/static/` | Lettertypen, beeldmerk, favicon, `staticwebapp.config.json` |
| `.github/workflows/azure-static-web-apps.yml` | Bouwt met Hugo en publiceert naar Azure Static Web Apps |

## Pagina's

Home, Verzekeringen (auto, woon en inboedel, aansprakelijkheid, bedrijven), Over ons, Onze visie, Nieuws, Contact, Privacy.

Er is nog geen pagina of menu-item voor schade melden. [[schademelden]] komt later als app op de website ([[werkafspraken-team-marketing#TM-WA-05]]).

## Beveiliging en privacy

- `staticwebapp.config.json` zet beveiligingsheaders en een Content Security Policy die alleen eigen bronnen toestaat ([[informatiebeveiliging#ORG-SEC-03]]).
- Geen cookies, geen externe scripts of lettertypen ([[werkafspraken-team-marketing#TM-WA-03]]). De privacypagina belooft dit ook; een wijziging die dit doorbreekt, vraagt aanpassing van die pagina.

## Lokaal bekijken

```bash
cd site
hugo server
```

## Publiceren

Een push naar `main` met wijzigingen in `site/` start de workflow. Pull requests krijgen een previewomgeving. Het deployment-token staat als GitHub-secret `AZURE_STATIC_WEB_APPS_API_TOKEN` ([[informatiebeveiliging#ORG-SEC-02]]).

## Bekende beperkingen

- De Static Web App moet nog worden aangemaakt in Azure en het token als secret worden ingesteld.
- Voor gekoppelde Azure Functions (nodig voor [[schademelden]]) is het Standard-plan van Static Web Apps nodig.
