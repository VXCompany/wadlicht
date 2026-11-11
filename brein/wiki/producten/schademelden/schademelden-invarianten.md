---
titel: SchadeMelden, invarianten
niveau: product
status: beschrijvend
eigenaar: Team Schade
team: team-schade
regel_prefix: PRD-SCH-INV
bronnen:
  - "[[2026-09-15-productvisie-schademelden]]"
  - "[[2026-10-22-incidentrapport-INC-2026-041]]"
bijgewerkt: 2026-10-25
review_voor: 2027-01-31
tags: [niveau/product, product/schademelden]
---

# SchadeMelden, invarianten

Wat altijd waar moet blijven in [[schademelden]], ongeacht welke wijziging. Volgens [[werkafspraken-team-schade#TS-WA-02]] krijgt elke invariant een test met het ID in de naam. Het product is nog niet gebouwd, dus er zijn nog geen tests.

### PRD-SCH-INV-01
**Een melding hoort altijd bij een actieve polis.**
- Afgeleid van: [[polisregister-api-v2#TP-API-02]]
- Test: nog niet aanwezig

### PRD-SCH-INV-02
**Een melding wordt precies één keer geregistreerd, ook als de klant twee keer op versturen drukt of de verbinding wegvalt.**
- Test: nog niet aanwezig

### PRD-SCH-INV-03
**De klant krijgt pas een bevestiging nadat de melding én alle bijlagen veilig zijn opgeslagen. Mislukt de opslag van een bijlage, dan krijgt de klant een foutmelding en kan het opnieuw proberen.**
- Bron: [[2026-10-22-incidentrapport-INC-2026-041]], maatregel 1
- Achtergrond: [[incidenten-team-schade#INC-2026-041]]
- Test: nog niet aanwezig

### PRD-SCH-INV-04
**Een letselindicatie is alleen zichtbaar voor medewerkers met de rol letselbehandelaar. De app vraagt geen medische details.**
- Afgeleid van: [[privacy-en-bewaartermijnen#ORG-PRV-03]], [[privacy-en-bewaartermijnen#ORG-PRV-02]]
- Werkvorm voor wijzigingen: mens-geleid ([[werkvormen-en-autonomie#ORG-AI-03]])
- Test: nog niet aanwezig

### PRD-SCH-INV-05
**Foto's en bijlagen worden 10 jaar na het afsluiten van het schadedossier bewaard en daarna verwijderd.**
- Afgeleid van: privacybeleid versie 2 (april 2025)
- Test: nog niet aanwezig

### PRD-SCH-INV-06
**Meldingen en foto's worden alleen opgeslagen in Azure-regio's binnen de EU (West Europe, North Europe), in opslag zonder publieke toegang.**
- Afgeleid van: [[privacy-en-bewaartermijnen#ORG-PRV-05]], [[referentiearchitectuur#ORG-ARC-04]]
- Test: nog niet aanwezig (infrastructuurtest op Bicep)

### PRD-SCH-INV-07
**Uploadlimieten (maximaal 15 MB per foto, maximaal 10 foto's) zijn in elke laag gelijk: browser, API, gateway en opslag. Ze staan op één plek in de configuratie. Een te groot bestand wordt geweigerd vóór het versturen, met een begrijpelijke melding.**
- Bron: [[2026-10-22-incidentrapport-INC-2026-041]], maatregel 2
- Afgeleid van: [[codeerrichtlijnen-team-schade#TS-CR-04]]
- Werkvorm voor wijzigingen: minimaal gepaard ([[werkafspraken-team-schade#TS-WA-03]])
- Test: nog niet aanwezig

### PRD-SCH-INV-08
**Foto's worden op malware gescand en op bestandstype gecontroleerd voordat een medewerker ze kan openen.**
- Afgeleid van: [[informatiebeveiliging#ORG-SEC-05]]
- Test: nog niet aanwezig
