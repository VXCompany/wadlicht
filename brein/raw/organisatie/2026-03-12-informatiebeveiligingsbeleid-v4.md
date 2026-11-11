# Informatiebeveiligingsbeleid, versie 4

- Vastgesteld door: directie, op voorstel van de CISO
- Ingangsdatum: 12 maart 2026
- Eigenaar: CISO (Joost Visser)
- Kader: DORA, DNB Good Practice Informatiebeveiliging

## Hoofdpunten

1. Klantfuncties die persoonsgegevens **tonen** vereisen inloggen met tweestapsverificatie. Functies die alleen gegevens **ontvangen**, zoals een melding, mogen zonder inloggen als de klant zich verifieert met polisgegevens en er misbruikbeperking (rate limiting) is ingericht.
2. Geheimen (sleutels, wachtwoorden, connection strings) staan in Azure Key Vault of in de beveiligde instellingen van het platform. Nooit in een repository.
3. Alle webapplicaties gebruiken uitsluitend HTTPS en zetten beveiligingsheaders, waaronder een Content Security Policy.
4. Bekende kwetsbaarheden in afhankelijkheden met een **CVSS-score van 7.0 of hoger** blokkeren de build. Een uitzondering kan alleen met schriftelijk akkoord van de CISO en is maximaal 30 dagen geldig.
5. Bestanden die van buiten komen (uploads) worden op malware gescand voordat ze worden verwerkt. Het bestandstype wordt gecontroleerd op inhoud, niet op extensie.
6. Beveiligingsrelevante gebeurtenissen gaan naar de centrale SIEM en worden één jaar bewaard.
