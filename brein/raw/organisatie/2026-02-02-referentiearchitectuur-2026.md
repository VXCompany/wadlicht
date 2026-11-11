# Referentiearchitectuur 2026

- Eigenaar: Enterprise architect (Pieter Zijlstra)
- Ingangsdatum: 2 februari 2026
- Laatste aanpassing: 1 oktober 2026 (runtimeversies)

## Platform

- Cloud: Microsoft Azure. Regio West Europe, uitwijk naar North Europe.
- Publieke websites en eenvoudige webapplicaties: Azure Static Web Apps. Server-side logica via Azure Functions, gekoppeld aan de Static Web App.
- Bestanden: Azure Blob Storage met private endpoints. Geen publieke containers.
- Infrastructuur als code: Bicep.

## Talen en runtimes

- .NET 10 (LTS) met C#. .NET 8 wordt per november 2026 niet meer ondersteund; bestaande applicaties migreren uiterlijk Q1 2027.
- Java 21 (LTS) of Java 25 (LTS). Java 17 is uitgefaseerd.

## Integratie

- Teams koppelen via gedocumenteerde REST API's met een OpenAPI-specificatie.
- API's zijn geversioneerd. Een oude versie blijft minimaal 6 maanden beschikbaar na aankondiging van uitfasering.
