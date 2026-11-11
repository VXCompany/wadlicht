---
titel: Referentiearchitectuur
niveau: organisatie
status: bindend
eigenaar: Enterprise architect
regel_prefix: ORG-ARC
bronnen:
  - "[[2026-02-02-referentiearchitectuur-2026]]"
bijgewerkt: 2026-10-02
review_voor: 2027-02-01
tags: [niveau/organisatie, domein/architectuur]
---

# Referentiearchitectuur

Uit de [[2026-02-02-referentiearchitectuur-2026|referentiearchitectuur 2026]], inclusief de aanpassing van 1 oktober 2026.

### ORG-ARC-01
**Microsoft Azure, regio West Europe, met uitwijk naar North Europe.**
- Bron: [[2026-02-02-referentiearchitectuur-2026]], Platform
- Ondersteunt: [[privacy-en-bewaartermijnen#ORG-PRV-05]]

### ORG-ARC-02
**Publieke websites en eenvoudige webapplicaties draaien op Azure Static Web Apps. Server-side logica via Azure Functions die aan de Static Web App gekoppeld zijn.**
- Bron: [[2026-02-02-referentiearchitectuur-2026]], Platform

### ORG-ARC-03
**Backends gebruiken .NET 10 (LTS) of Java 21/25 (LTS). .NET 8 en Java 17 zijn uitgefaseerd; bestaande applicaties migreren uiterlijk Q1 2027.**
- Bron: [[2026-02-02-referentiearchitectuur-2026]], Talen en runtimes

### ORG-ARC-04
**Bestanden staan in Azure Blob Storage met private endpoints. Geen publieke containers.**
- Bron: [[2026-02-02-referentiearchitectuur-2026]], Platform

### ORG-ARC-05
**Teams koppelen via geversioneerde REST API's met een OpenAPI-specificatie. Een oude versie blijft minimaal 6 maanden beschikbaar na aankondiging van uitfasering.**
- Bron: [[2026-02-02-referentiearchitectuur-2026]], Integratie

### ORG-ARC-06
**Infrastructuur wordt beschreven als code in Bicep.**
- Bron: [[2026-02-02-referentiearchitectuur-2026]], Platform
