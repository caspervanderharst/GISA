# Inleiding
Bij de uitwisseling van medische gegevens tussen zorgaanbieders dienen meerdere kritieke aspecten goed te worden geregeld: gegevensbescherming, informatiebeveiliging, verantwoordelijkheidsverdeling en authenticiteit van de uitwisseling. Deze aspecten zijn juridisch complex en roepen regelmatig vragen op die duidelijkheid vereisen van VWS.

Een voorbeeldcasus is de discussie over identificatie, authenticatie en autorisatie van zorgverleners bij point-to-point-uitwisseling tussen twee zorgaanbieders. Dit memo verkent de juridische en architecturale uitgangspunten daarvoor en vraagt de jurist om uitspraak op basis van geldende wet- en regelgeving (met name AVG, Wabvpz, Wkz, NEN 7510 en NORA).

# Vraag aan de jurist
Klopt het dat uitwisseling plaatsvindt tussen twee verwerkingsverantwoordelijken (zorgaanbieders), de ontvanger geautoriseerd moet worden door de verzender en beiden zelfstandig verantwoordelijk zijn voor de verwerking van de eigen (kopie van de) gegevens?

# Juridische en architecturale uitgangspunten
## Verwerkingsverantwoordelijkheid
Er is sprake van tweeledig eigenaarschap bij de uitwisseling van gegevens. Als zorgaanbieder A gegevens verstrekt aan zorgaanbieder B, ontstaat er feitelijk een situatie met twee verwerkingsverantwoordelijken:
* Zorgaanbieder A blijft verwerkingsverantwoordelijke voor de originele gegevens in de eigen omgeving en bepaalt waarom (op gronde waarvan), hoe en naar wie de uitwisseling plaatsvindt;
* Zorgaanbieder B wordt verwerkingsverantwoordelijke voor de ontvangen kopie binnen de eigen organisatie en draagt verantwoordelijkheid voor verwerking volgens geldende wet- en regelgeving (AVG, Wabvpz).

Beide zorgaanbieders zijn binnen de eigen muren verantwoordelijk voor de verwerking van de gegevens.

## Autorisatie in de uitwisseling
Autorisatie (en daarmee identificatie en authenticatie) moet op twee niveaus worden uitgevoerd:
* **Inter-organisationeel niveau**: Bij het versturen van gegevens naar een andere zorgaanbieder, ongeacht wie de initiërende partij is, moet de verzendende zorgaanbieder de uitwisseling autoriseren. Dit wordt onder andere gedaan op basis van de toestemming van de patiënt. Beide zorgaanbieders moeten zich ervan vergewissen dat de identiteit van de ander klopt.
* **Intra-organisationeel niveau**: Beide zorgaanbieders zijn verantwoordelijke voor de autorisatie van gegevensverwerking door de eigen zorgverleners en de eigen zorgsystemen. Wet- en regelgeving bepaalt het niveau van autorisatie binnen de eigen organisatie.

# Voorbeelden
## Verstrekking
De huisarts van een gezondheidscentrum verwijst een patiënt naar de radioloog in het ziekenhuis.
* **Intra-organisationeel bij het gezondheidscentrum**: Het gezondheidscentrum autoriseert de verwijzing door de huisarts naar het ziekenhuis.
* **Inter-organisationeel**: Het gezondheidscentrum autoriseert de uitwisseling van de verwijzing met het ziekenhuis, onder andere op basis van veronderstelde toestemming.
* **Intra-organisationeel bij het ziekenhuis**: Het ziekenhuis autoriseert de verwerking van de verwijzing door de radioloog.

## Opvraging
De huisarts van een gezondheidscentrum vraagt gezondheidsgegevens op bij het ziekenhuis waar een radioloog gegevens heeft verwerkt.
* **Intra-organisationeel bij het gezondheidscentrum**: Het gezondheidscentrum autoriseert het verzoek tot opvraging door de huisarts.
* **Inter-organisationeel**: Het ziekenhuis autoriseert de uitwisseling van de gegevens met het gezondheidscentrum, onder andere op basis van door de patiënt vastgelegde toestemming.
* **Intra-organisationeel bij het gezondheidscentrum**: Het gezondheidscentrum autoriseert de verwerking van de gegevens door de huisarts.
