Harmonisatie van authenticatie en vertrouwensmodel bij BgZ- en eOverdracht-uitwisseling
Status: Concept ter bespreking Datum: 2 juli 2026

# Aanleiding en vraagstelling


De gegevensuitwisselingen BgZ (medisch-specialistische zorg) en eOverdracht (verpleegkundige overdracht) kennen beide een Wegiz-traject en worden in toenemende mate over dezelfde infrastructuren en volgens dezelfde uitwisselpatronen uitgevoerd. Er is geconstateerd dat de beproefde technische afspraak voor de BgZ afwijkt van die voor de eOverdracht. Harmonisatie van authenticatie en autorisatie is daarmee randvoorwaardelijk.

Deze notitie beantwoordt drie vragen:
1. Hoe wordt op korte termijn de authenticatie van zorgverleners en zorgsystemen geharmoniseerd?
2. Hoe wordt op korte termijn de authenticatie van zorgaanbieders geharmoniseerd?
3. Hoe worden de risico's in het vertrouwensmodel juridisch, organisatorisch en technisch afgedekt?

De beantwoording volgt per vraag volgens de architectuurlagen: grondslagen (wet- en regelgeving), bedrijfsarchitectuur (stelsel- en organisatieafspraken), informatie- en applicatiearchitectuur, en technische architectuur.

# Vraag 1: Authenticatie van zorgverleners en -systemen (korte termijn)

Op korte termijn geldt voor beide uitwisselingen hetzelfde federatieve principe: de authenticatie van zorgverleners én van zorgsystemen wordt uitsluitend uitgevoerd door de eigen zorgaanbieder, binnen diens eigen beveiligingsdomein. De andere zorgaanbieder voert géén eigen authenticatie of verificatie op het niveau van de individuele zorgverlener of het individuele systeem uit, maar mag uitgaan van de betrouwbare processen van de uitwisselingspartner. Het vertrouwen verschuift daarmee van middelniveau (het controleren van een authenticatiemiddel van de ander) naar procesniveau (het vertrouwen op een aantoonbaar goed ingericht IAM-proces bij de ander). Alleen de organisatie-identiteit wordt over de organisatiegrens heen geverifieerd (zie vraag 2); alles daarbinnen is de verantwoordelijkheid van de eigen zorgaanbieder.

## Grondslagen

Dit principe past binnen het bestaande wettelijk kader. De AVG en de Wabvpz verplichten iedere zorgaanbieder als zelfstandig verwerkingsverantwoordelijke tot passende beveiliging en een voldoende betrouwbaarheidsniveau van authenticatie voor de eigen systemen en medewerkers. De wet schrijft niet voor dat een uitwisselingspartner die authenticatie nogmaals of zelfstandig uitvoert. NEN 7510 en NEN 7512 bieden het normenkader waarmee de betrouwbaarheid van de interne processen aantoonbaar wordt gemaakt richting de partner. Het streefbeeld blijft landelijk uniform inloggen via Dezi na inwerkingtreding van de Wet DIAZ, maar ook in dat stelsel blijft de lijn dat de zorgaanbieder de werkrelatie met de zorgmedewerker registreert en de toegang organiseert; het kortetermijnmodel loopt daarop vooruit.

## Bedrijfsarchitectuur

De zorgaanbieder richt één intern authenticatie- en autorisatieproces in dat voor alle uitwisselingen, BgZ én eOverdracht, identiek wordt gebruikt. De zorgverlener logt eenmalig in binnen het lokale IAM-domein (conform NEN 7510). De zorgaanbieder staat er als organisatie voor in dat degene die de uitwisseling initieert een geauthenticeerde, geautoriseerde medewerker met een geldige behandelrelatie is. Hetzelfde geldt voor zorgsystemen. Het beheer, de registratie en de authenticatie van systemen die namens de zorgaanbieder communiceren (EPD, ECD, koppelvlak, knooppunt) vallen onder het interne beheerproces van die zorgaanbieder. De uitwisselingspartner hoeft dus niet te weten of te controleren wélk systeem of wélke medewerker aan de andere kant actief is. Hij vertrouwt erop dat de partner dit betrouwbaar heeft ingericht. Dit wederzijds vertrouwen is niet vrijblijvend, maar wordt georganiseerd via geharmoniseerde afspraken. Door toetreding verklaart en toont iedere deelnemer aan dat de interne processen aan de gestelde normen voldoen (zie vraag 3). Voor eOverdracht is dit model bovendien de enige haalbare route, omdat landelijke authenticatiemiddelen op persoonsniveau (UZI-pas) niet in alle delen van de zorg-sector zijn uitgerold.

## Informatie- en applicatiearchitectuur

Omdat de partner geen verificatie op persoons- of systeemniveau uitvoert, volstaat het dat de transactie de context meedraagt die nodig is voor autorisatie, logging en herleidbaarheid. Hiervoor worden de organisatie-identiteit (URA) en de rol/functie van de verantwoordelijke zorgverlener / zorgsysteem / afdeling meegegeven. Deze attributen worden meegegeven als verklaring van de zorgaanbieder, niet als te verifiëren bewijs over de zorgmedewerker of het zorgsysteem. De beschikbaarstellende partij gebruikt de rolinformatie uitsluitend voor het autorisatiebesluit conform het autorisatieprotocol van de zorgtoepassing en legt de attributen vast in de logging. Zij valideert niet zelf de onderliggende authenticatie. Door voor BgZ en eOverdracht dezelfde attributenset en hetzelfde verklaringsformaat te hanteren, is het autorisatie- en loggingsproces bij de bron voor beide uitwisselingen identiek.

##Technische architectuur

De ontvangende partij controleert uitsluitend dat de verklaring afkomstig is van de geauthenticeerde organisatie en integer is, niet de juistheid van de inhoud. Hoe een zorgaanbieder de interne authenticatie technisch invult (bijvoorbeeld een wachtwoord met MFA, smartcard, UZI-pas waar beschikbaar, single sign-on vanuit het EPD/ECD) is een lokale keuze binnen de normkaders en is voor de uitwisselingspartner niet zichtbaar en niet relevant. Dit maakt het model direct toepasbaar in zowel de BgZ als eOverdracht, en is migratievast richting Dezi.

#Vraag 2: Authenticatie van zorgaanbieders (korte termijn)

##Grondslagen

De identiteit van de zorgaanbieder als rechtspersoon is wettelijk verankerd via het UZI-register (Wabvpz). Het URA-nummer fungeert als de stelselbrede, onweerlegbare organisatie-identifier. Beide uitwisselingen dienen op korte termijn op ditzelfde identificatiestelsel te steunen; er is geen juridische ruimte of noodzaak voor een afwijkend regime per zorgtoepassing.

## Bedrijfsarchitectuur

De harmonisatie wordt georganiseerd via het geharmoniseerde afsprakenstelsel (Twiin als vertrekpunt). Zorgaanbieders sluiten aan via een Gekwalificeerd Twiin Knooppunt (GtK), met een samenwerkingsovereenkomst en het vertrouwensmodel Twiin als bindende instrumenten. Voor eOverdracht betekent dit dat deelnemende VVT- en ziekenhuisorganisaties onder hetzelfde toetredings- en kwalificatieregime vallen als bij de BgZ, in plaats van bilaterale vertrouwensafspraken.
Informatie- en applicatiearchitectuur
De organisatie-identiteit (URA) wordt in beide uitwisselingen op dezelfde plaats in de transactie meegegeven en gevalideerd, conform geharmoniseerde afspraken. Het knooppunt treedt op als technisch vertegenwoordiger van de zorgaanbieder, de verantwoordelijkheid blijft bij de zorgaanbieder zelf.

##Technische architectuur

De authenticatie van de zorgaanbieder gebruikt op korte termijn op twee complementaire mechanismen die voor BgZ en eOverdracht identiek worden ingericht.

Ten eerste wordt de transportlaag beveiligd met wederzijdse TLS (mTLS) op basis van PKIoverheid/UZI-servercertificaten, waarbij de validatie van de zorgaanbiederidentiteit plaatsvindt tegen het publieke UZI-servercertificaat waarin het door het UZI-register uitgegeven URA is opgenomen. Dit borgt de authenticatie van de organisatie op verbindingsniveau (NEN 7512) en is het enige op korte termijn beschikbare middel voor systeem-tot-systeemauthenticatie op voldoende betrouwbaarheidsniveau.
Ten tweede wordt de organisatie-identiteit op berichtniveau geborgd via ondertekende tokens (JWT's) waarvan de handtekening wordt gevalideerd met behulp van JWKS (JSON Web Key Set). Iedere deelnemende zorgaanbieder (of diens knooppunt) publiceert de publieke sleutels waarmee zijn tokens zijn ondertekend op een JWKS-endpoint, conform geharmoniseerde afspraken. De ontvangende partij haalt de sleutelset op via dit endpoint en valideert daarmee dat het token daadwerkelijk door de geclaimde organisatie is afgegeven en onderweg niet is gewijzigd. De binding tussen het JWKS-endpoint en de organisatie-identiteit (URA) wordt geborgd doordat het endpoint zelf uitsluitend via een mTLS-verbinding met UZI-servercertificaat wordt ontsloten en de endpointregistratie onderdeel is van de toetreding tot het afsprakenstelsel.

De twee mechanismen dekken verschillende risico's af en zijn beide noodzakelijk. mTLS authenticeert de verbinding tussen twee systemen (kanaalbeveiliging), terwijl JWKS-gebaseerde tokenvalidatie de authenticiteit en integriteit van de individuele verklaring borgt, ook wanneer die via tussenliggende knooppunten of over meerdere schakels wordt doorgegeven. Juist in een landschap met knooppunten (GtK's) tussen bron- en doelsysteem is berichtniveaubeveiliging onmisbaar, omdat mTLS alleen hop-by-hop werkt en geen end-to-end-garantie geeft over wie de oorspronkelijke afzender is. Sleutelrotatie verloopt via het JWKS-endpoint zonder dat uitwisselpartners handmatig sleutelmateriaal hoeven uit te wisselen, wat het stelsel schaalbaar en beheersbaar houdt.