# Inleiding

Bij de uitwisseling van medische gegevens tussen zorgaanbieders dienen meerdere kritieke aspecten goed te worden geregeld: gegevensbescherming, informatiebeveiliging, verantwoordelijkheidsverdeling en authenticiteit van de uitwisseling. Deze aspecten zijn juridisch complex en roepen regelmatig vragen op die duidelijkheid vereisen van VWS.

Een voorbeeldcasus is de discussie over identificatie, authenticatie en autorisatie van zorgverleners bij point-to-point-uitwisseling tussen twee zorgaanbieders. Dit memo verkent de juridische en architecturale uitgangspunten daarvoor en vraagt de jurist om uitspraak op basis van geldende wet- en regelgeving (met name AVG, Wabvpz, Wkz, NEN 7510 en NORA).

# Vraag aan de jurist
Klopt het dat uitwisseling plaatsvindt tussen twee verwerkingsverantwoordelijken (zorgaanbieders), de verwerkingsverantwoordelijken elkaar moeten autoriseren voor de uitwisselen en beiden zelfstandig verantwoordelijk zijn voor de verwerking van de eigen (kopie van) gegevens?  

# Juridische en architecturale uitgangspunten
## Verwerkingsverantwoordelijkheid
Er is sprake van tweeledig eigenaarschap bij de verstrekking gegevens. Als zorgaanbieder A gegevens verstrekt aan zorgaanbieder B, ontstaat er feitelijk een situatie met twee verwerkingsverantwoordelijken:
* Zorgaanbieder A blijft verwerkingsverantwoordelijke voor de originele gegevens in de eigen omgeving en bepaalt waarom en hoe de uitwisseling plaatsvindt;
* Zorgaanbieder B wordt verwerkingsverantwoordelijke voor de ontvangen kopie binnen de eigen organisatie en draagt verantwoordelijkheid voor verwerking volgens geldende wet- en regelgeving (AVG, Wabvpz).

Binnen de eigen muren zijn beide zorgaanbieders verantwoordelijk voor de verwerking van de gegevens.

## Identificatie, authenticatie en autorisatie (IAA) in de uitwisseling
IAA moet op twee niveaus worden uitgevoerd:
* **Inter-organisationeel niveau**: Tussen de organisaties moet wederzijdse identificatie en authenticatie plaatsvinden. Dit is geen interne aangelegenheid van één partij, maar een gezamelijke verantwoordelijkheid. Beide partijen moeten bewijs hebben van de identiteit van de andere zorgaanbieder en alleen elkaar (dus organisatie) autoriseren.
* **Intra-organisationeel niveau**: Beide zorgaanbieders zijn verantwoordelijke voor de identificatie en authenticatie van de eigen zorgverleners en de eigen zorgsystemen die voor haar gegevens verwerken. Wet- en regelgeving bepaalt het niveau van autorisatie binnen de eigen organisatie.

# Voorbeelden
## Verstrekking
De huisarts van een gezondheidscentrum verwijst een patiënt naar de radioloog in het ziekenhuis.
* **Intra-organisationeel bij het gezondheidscentrum**: Het gezondheidscentrum identificeert en authenticeert de huisarts. Tevens autoriseert het gezondheidscentrum de verwijzing door de huisarts naar het ziekenhuis.
* **Inter-organisationeel**: Het gezondheidscentrum en het ziekenhuis moeten elkaar identificeren en authenticeren volgens de afspraken binnen het stelsel.
* **Intra-organisationeel bij het ziekenhuis**: Het ziekenhuis identificeert en authenticeert de radioloog. Tevens autoriseert het ziekenhuis de verwerking van de verwijzing door de radioloog.

## Opvraging
De huisarts van een gezondheidscentrum vraagt gezondheidsgegevens op bij het ziekenhuis waar een radioloog gegevens heeft verwerkt.
* **Intra-organisationeel bij het gezondheidscentrum**: Het gezondheidscentrum identificeert en authenticeert de huisarts. Tevens autoriseert het gezondheidscentrum de opvraging door de huisarts.
* **Inter-organisationeel**: Het gezondheidscentrum en het ziekenhuis moeten elkaar identificeren, authenticeren en autoriseren volgens de afspraken binnen het stelsel.
* **Intra-organisationeel bij het gezondheidscentrum**: Het gezondheidscentrum identificeert en authenticeert de huisarts. Tevens autoriseert het gezondheidscentrum de verwerking door de huisarts.
