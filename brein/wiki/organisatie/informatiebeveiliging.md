---
titel: Informatiebeveiliging
niveau: organisatie
status: bindend
eigenaar: CISO
regel_prefix: ORG-SEC
bronnen:
  - "[[2026-03-12-informatiebeveiligingsbeleid-v4]]"
bijgewerkt: 2026-03-20
review_voor: 2027-03-01
tags: [niveau/organisatie, domein/security]
---

# Informatiebeveiliging

Regels uit het [[2026-03-12-informatiebeveiligingsbeleid-v4|informatiebeveiligingsbeleid versie 4]]. Kader: DORA en de DNB Good Practice Informatiebeveiliging.

### ORG-SEC-01
**Klantfuncties die persoonsgegevens tonen, vereisen inloggen met tweestapsverificatie. Functies die alleen gegevens ontvangen, mogen zonder inloggen als de klant zich verifieert met polisgegevens en er rate limiting is.**
- Bron: [[2026-03-12-informatiebeveiligingsbeleid-v4]], punt 1

### ORG-SEC-02
**Geheimen staan in Azure Key Vault of in de beveiligde instellingen van het platform, nooit in een repository.**
- Bron: [[2026-03-12-informatiebeveiligingsbeleid-v4]], punt 2

### ORG-SEC-03
**Webapplicaties gebruiken alleen HTTPS en zetten beveiligingsheaders, waaronder een Content Security Policy.**
- Bron: [[2026-03-12-informatiebeveiligingsbeleid-v4]], punt 3

### ORG-SEC-04
**Kwetsbaarheden in afhankelijkheden met een CVSS-score van 7.0 of hoger blokkeren de build.**
- Bron: [[2026-03-12-informatiebeveiligingsbeleid-v4]], punt 4
- Uitzondering: alleen met schriftelijk akkoord van de CISO, maximaal 30 dagen.

### ORG-SEC-05
**Uploads worden op malware gescand voordat ze worden verwerkt. Het bestandstype wordt gecontroleerd op inhoud, niet op extensie.**
- Bron: [[2026-03-12-informatiebeveiligingsbeleid-v4]], punt 5

### ORG-SEC-06
**Beveiligingsrelevante gebeurtenissen gaan naar de centrale SIEM en worden één jaar bewaard.**
- Bron: [[2026-03-12-informatiebeveiligingsbeleid-v4]], punt 6
