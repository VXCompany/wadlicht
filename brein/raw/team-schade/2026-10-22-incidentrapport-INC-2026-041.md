# Incidentrapport INC-2026-041: schademeldingen zonder foto's

- Datum incident: 20 oktober 2026, 09.12 tot 16.40 uur
- Team: Team Schade
- Systeem: schadeformulier in Mijn Wadlicht (voorganger van SchadeMelden)
- Opgesteld door: tech lead Team Schade (Ruben Kingma)
- Status: afgesloten, 22 oktober 2026

## Wat er gebeurde

Op 20 oktober is de maximale grootte van een foto in het schadeformulier verhoogd van 10 naar 15 MB. De wijziging bestond uit het aanpassen van één constante en is autonoom door een development agent uitgevoerd. Alle tests waren groen.

De limiet van de upstream gateway stond nog op 12 MB. Foto's tussen 12 en 15 MB werden door de gateway geweigerd. Het formulier ving die fout niet af en stuurde de melding zonder foto's door. De klant kreeg wel een bevestiging dat de melding compleet was ontvangen.

## Gevolgen

- 312 schademeldingen kwamen binnen zonder de foto's die de klant had toegevoegd.
- Schadebehandelaars hebben alle 312 klanten opnieuw benaderd. Gemiddeld liep de afhandeling 4 werkdagen vertraging op.

## Oorzaken

1. De limiet stond op twee plekken (formulier en gateway). Dat stond nergens beschreven.
2. Er was geen test die controleerde dat een melding pas wordt bevestigd als alle bijlagen zijn opgeslagen.
3. De wijziging leek klein en is als routinewerk behandeld.

## Maatregelen

1. De klant krijgt pas een bevestiging nadat de melding én alle bijlagen veilig zijn opgeslagen. Wordt een invariant voor SchadeMelden.
2. Limieten staan op één plek in de configuratie, en die plek wordt gedocumenteerd.
3. Wijzigingen aan uploads worden niet meer autonoom uitgevoerd. Zie retro van 24 oktober.
