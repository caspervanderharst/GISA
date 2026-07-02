Harmonisatie van authenticatie en vertrouwensmodel bij BgZ- en eOverdracht-uitwisseling
Status: Concept ter bespreking
Datum: 2 juli 2026

# Aanleiding en vraagstelling

De gegevensuitwisselingen BgZ (medisch-specialistische zorg) en eOverdracht (verpleegkundige overdracht) kennen beide een Wegiz-traject en worden in toenemende mate over dezelfde infrastructuren en volgens dezelfde uitwisselpatronen uitgevoerd. Er is geconstateerd dat de beproefde technische afspraak voor de BgZ afwijkt van die voor de eOverdracht. Harmonisatie van authenticatie en autorisatie is randvoorwaardelijk voor een efficiënte en veilige implementatie van beide uitwissselingen.

Deze notitie beantwoordt drie vragen:
1. Hoe wordt op korte termijn de authenticatie van zorgverleners en zorgsystemen geharmoniseerd (interne authenticatie en autorisatie)?
2. Hoe wordt op korte termijn de authenticatie van zorgaanbieders geharmoniseerd (externe authenticatie en autorisatie)?
3. Hoe worden de risico's in het vertrouwensmodel juridisch, organisatorisch en technisch afgedekt?

De beantwoording volgt per vraag, waarbij rekening wordt gehouden met de verschillende architectuurlagen. Hierbij wordt eerst beschreven wat de wettelijke kaders zijn voor interne en externe authenticatie. Het verschil tussen deze twee is van belang voor de verdere uitwerking en de eisen die in het document zijn opgenomen.

Het laatste hoofdstuk bevat een samenvattende lijst van vereisten waaraan zorgaanbieders moeten voldoen om de BgZ- en eOverdracht-uitwisselingen veilig en efficiënt te kunnen uitvoeren.

# Wettelijk kader

## Interne authenticatie

De AVG en de Wabvpz verplichten iedere zorgaanbieder als zelfstandig verwerkingsverantwoordelijke tot passende beveiliging en een voldoende betrouwbaarheidsniveau van authenticatie voor de eigen systemen en medewerkers. De wet schrijft niet voor dat een uitwisselingspartner die authenticatie nogmaals of zelfstandig uitvoert. NEN 7510 en NEN 7512 bieden het normenkader waarmee de betrouwbaarheid van de interne processen aantoonbaar wordt gemaakt richting de partner. Zorgaanbieders zijn verplicht om aan de eisen uit NEN 7510 en NEN 7512 te voldoen.

Het streefbeeld blijft landelijk uniform inloggen via Dezi na inwerkingtreding van de Wet DIAZ, maar ook in dat stelsel blijft de lijn dat de zorgaanbieder de werkrelatie met de zorgmedewerker registreert en de toegang organiseert. Het kortetermijnmodel loopt daarop vooruit.

## Externe authenticatie

De identiteit van de zorgaanbieder als organisatie is wettelijk verankerd via het UZI-register (Wabvpz). Het daaraan gekoppelde abonneenummer (URA) fungeert als de stelselbrede, onweerlegbare organisatie-identifier. Beide uitwisselingen dienen op korte termijn op ditzelfde identificatiestelsel te steunen. Er is geen juridische ruimte of noodzaak voor een afwijkend regime per zorgtoepassing. 

Daarbij past de volgende begripsafbakening: de eIDAS-betrouwbaarheidsniveaus (laag, substantieel, hoog) zijn gedefinieerd voor elektronische identificatiemiddelen van personen en zijn niet van toepassing op certificaten waarmee systemen zich authenticeren. Deze certificaten vallen onder de afspraken van vertrouwensstelsels. De betrouwbaarheid van de organisatieauthenticatie wordt dus niet uitgedrukt in een eIDAS-niveau, maar ontleend aan het gecontroleerde uitgifteproces van het UZI-register en de PKIoverheid-eisen, in combinatie met NEN 7512 voor de eisen aan de verbinding.

# Vraag 1: Authenticatie van zorgverleners en -systemen (korte termijn)

Op korte termijn geldt voor beide uitwisselingen hetzelfde federatieve principe: Zorgaanbieders zijn alleen verantwoordelijk voor de identificatie en authenticatie van zorgverleners en zorgsystemen binnen diens eigen beveiligingsdomein (Interne authenticatie). Bij de uitwisseling van zorggegevens voert een zorgaanbieder geen eigen identificatie, authenticatie of verificatie op het niveau van de individuele zorgverlener of het individuele systeem uit die binnen de verantwoordelijkheid van de uitwisselingspartner vallen. Een zorgaanbieder moet uitgaan van de betrouwbare processen van de uitwisselingspartner. Het vertrouwen verschuift daarmee van middelniveau (het controleren van een authenticatiemiddel van de ander) naar procesniveau (het vertrouwen op een aantoonbaar goed ingericht IAM-proces bij de ander). Alleen de organisatie-identiteit wordt over de organisatiegrens heen geverifieerd (zie vraag 2).

Een zorgaanbieder richt één intern authenticatie- en autorisatieproces in dat voor alle uitwisselingen, BgZ en eOverdracht, wordt gebruikt. De zorgverlener logt eenmalig in binnen het lokale IAM-domein (conform NEN 7510). De zorgaanbieder staat er als organisatie voor in dat degene die de uitwisseling initieert een geauthenticeerde, geautoriseerde medewerker met een geldige behandelrelatie is. Hetzelfde geldt voor zorgsystemen. Het beheer, de registratie en de authenticatie van systemen die namens de zorgaanbieder communiceren (EPD, ECD, koppelvlak, knooppunt) vallen onder het interne beheerproces van die zorgaanbieder. 

De uitwisselingspartner hoeft dus niet te weten of te controleren welk systeem of welke medewerker aan de andere kant actief is. Hij vertrouwt erop dat de partner de processen betrouwbaar heeft ingericht. Dit wederzijds vertrouwen is niet vrijblijvend, maar wordt georganiseerd via geharmoniseerde afspraken. Door toetreding verklaart en toont iedere deelnemer aan dat de interne processen aan de gestelde normen voldoen (zie vraag 3). Voor eOverdracht is dit model bovendien de enige haalbare route, omdat landelijke authenticatiemiddelen op persoonsniveau (UZI-pas) niet in alle delen van de zorgsector zijn uitgerold.

## Applicatief niveau

Omdat de partner geen verificatie op persoons- of systeemniveau uitvoert, volstaat het dat de transactie de context meedraagt die nodig is voor autorisatie, logging en herleidbaarheid. Hiervoor worden de organisatie-identiteit (URA) en de rol/functie van de verantwoordelijke zorgverlener / zorgsysteem / afdeling meegegeven. Deze attributen worden meegegeven als verklaring van de zorgaanbieder, niet als te verifiëren bewijs over de zorgmedewerker of het zorgsysteem. De beschikbaarstellende partij gebruikt de rolinformatie uitsluitend voor het autorisatiebesluit conform het autorisatieprotocol van de zorgtoepassing en legt de attributen vast in de logging. Zij valideert niet zelf de onderliggende authenticatie. Door voor BgZ en eOverdracht dezelfde attributenset en hetzelfde verklaringsformaat te hanteren, is het autorisatie- en loggingsproces bij de bron voor beide uitwisselingen identiek.

## Technisch niveau

De ontvangende partij controleert uitsluitend dat de verklaring afkomstig is van de geauthenticeerde organisatie, niet de juistheid van de inhoud. Hoe een zorgaanbieder de interne authenticatie technisch invult (bijvoorbeeld een wachtwoord met MFA, smartcard, UZI-pas waar beschikbaar, single sign-on vanuit het EPD/ECD) is een lokale keuze binnen de normkaders en is voor de uitwisselingspartner niet zichtbaar en niet relevant. Dit maakt het model direct toepasbaar in zowel de BgZ als eOverdracht, en is migratievast richting Dezi.

# Vraag 2: Authenticatie van zorgaanbieders (korte termijn)

De harmonisatie wordt georganiseerd via het geharmoniseerde afsprakenstelsel (Twiin als vertrekpunt). Zorgaanbieders sluiten aan via een Gekwalificeerd Twiin Knooppunt (GtK), met een samenwerkingsovereenkomst en het vertrouwensmodel Twiin als bindende instrumenten. Voor eOverdracht betekent dit dat deelnemende VVT- en ziekenhuisorganisaties onder hetzelfde toetredings- en kwalificatieregime vallen als bij de BgZ, in plaats van bilaterale vertrouwensafspraken.

De harmonisatie wordt georganiseerd doordat beide uitwisselingen onder één gemeenschappelijk stelsel van afspraken worden gebracht. Zorgaanbieders nemen deel via een gekwalificeerd koppel- of knooppunt en committeren zich via een deelnemersovereenkomst aan hetzelfde vertrouwensmodel, ongeacht of zij de BgZ of de eOverdracht uitwisselen. Toetreding vereist dat de organisatie-identiteit eenmalig en betrouwbaar is vastgesteld en gekoppeld aan het technische aansluitpunt. Daarmee vervalt de noodzaak van bilaterale vertrouwensafspraken.

## Applicatief niveau

De organisatie-identiteit (URA) wordt in beide uitwisselingen op dezelfde plaats in de transactie meegegeven en gevalideerd, conform geharmoniseerde afspraken. Het knooppunt treedt op als technisch vertegenwoordiger van de zorgaanbieder, de verantwoordelijkheid blijft bij de zorgaanbieder zelf.

De organisatie-identiteit (URA) wordt in beide uitwisselingen op dezelfde plaats in de transactie meegegeven en gevalideerd, conform geharmoniseerde afspraken. Waar een knooppunt of intermediair optreedt als technisch vertegenwoordiger van de zorgaanbieder, blijft de zorgaanbieder zelf de geïdentificeerde en verantwoordelijke partij. De architectuur moet de oorspronkelijke organisatie-identiteit daarom end-to-end meevoeren en niet vervangen door die van de intermediair.

De organisatie-identiteit wordt op berichtniveau geborgd via ondertekende tokens (JWT's) waarvan de handtekening wordt gevalideerd met behulp van JWKS (JSON Web Key Set). Iedere deelnemende zorgaanbieder publiceert de publieke sleutels waarmee zijn tokens zijn ondertekend op een JWKS-endpoint, conform geharmoniseerde afspraken. De ontvangende partij haalt de sleutelset op via dit endpoint en valideert daarmee dat het token daadwerkelijk door de geclaimde organisatie is afgegeven en onderweg niet is gewijzigd. De binding tussen het JWKS-endpoint en de organisatie-identiteit (URA) wordt geborgd doordat het endpoint zelf uitsluitend via een mTLS-verbinding (zie technische niveau) met UZI-servercertificaat wordt ontsloten en de endpointregistratie onderdeel is van de toetreding tot het afsprakenstelsel.

## Technisch niveau

De transportlaag wordt beveiligd met wederzijdse TLS (mTLS) op basis van UZI-servercertificaten, waarbij de validatie van de zorgaanbiederidentiteit plaatsvindt tegen het publieke UZI-servercertificaat waarin het door het UZI-register uitgegeven URA is opgenomen. Dit borgt de authenticatie van de organisatie op verbindingsniveau (NEN 7512) en is het enige op korte termijn beschikbare middel voor systeem-tot-systeemauthenticatie op voldoende betrouwbaarheidsniveau.

# Vraag 3: Afdekking van risico's in het vertrouwensmodel

## De centrale ontwerpbeslissing en het bijbehorende risico

Het vertrouwensmodel van deze geharmoniseerde uitwisselingen rust op één expliciete ontwerpbeslissing: een zorgaanbieder verifieert bij uitwisseling niets op het niveau van de individuele zorgverlener of het individuele zorgsysteem van de partner, maar vertrouwt op de betrouwbare inrichting van diens interne processen. De enige verificatie die de organisatiegrens uitvoert, is die van de organisatie-identiteit zelf. De dossierhouder, op wie de geheimhoudingsplicht rust en die daarom zekerheid moet hebben over wie hij toestaat gegevens te verwerken, ontleent die zekerheid dus niet aan eigen controle in de transactie, maar aan het stelsel als geheel.

Het kernrisico volgt direct uit deze beslissing: een tekortschietend intern proces bij één deelnemer werkt door in de vertrouwelijkheid van dossiers bij alle uitwisselpartners, zonder dat die partners dit in de transactie kunnen detecteren. De borging moet daarom volledig worden georganiseerd op drie momenten buiten de transactie:

1. vooraf (toetreding),
2. doorlopend (toezicht en beheer) en 
3. achteraf (herleidbaarheid en aansprakelijkheid).

De zeven onderdelen van het vertrouwensmodel (identificatie, authenticatie, autorisatie, behandelrelatie, patiënttoestemming, logging en transparantie) worden langs deze drie momenten en langs drie sporen afgedekt.

## Juridisch

Iedere zorgaanbieder is en blijft zelfstandig verwerkingsverantwoordelijke (AVG) voor de verwerking van persoonsgegevens in de eigen systemen, met inbegrip van het knooppunt of de intermediair die namens hem optreedt. De zorgaanbieder is het aanspreekpunt voor betrokkenen bij de uitoefening van hun privacyrechten. Het federatieve model verschuift die verantwoordelijkheid niet, maar maakt haar scherp belegbaar: omdat de partner uitsluitend afgaat op verklaringen van de zorgaanbieder, is die zorgaanbieder juridisch volledig aansprakelijk voor de juistheid daarvan. De deelnemersovereenkomst bij het geharmoniseerde afsprakenstelsel legt dit vast, inclusief aansprakelijkheids- en vrijwaringsbepalingen, zodat de dossierhouder die te goeder trouw op een onjuiste verklaring heeft vertrouwd, juridisch is gedekt. Daarmee wordt "uitgaan van de betrouwbare processen van de partner" omgezet van een feitelijke aanname in een afdwingbare contractuele garantie. 

De wettelijke verplichtingen uit de Wabvpz rond logging en het inzagerecht van de cliënt gelden onverkort aan beide zijden en vormen de juridische basis voor de totale herleidbaarheid achteraf. 

Tot slot borgt het juridisch spoor de zuiverheid van de gehanteerde betrouwbaarheidskaders: de organisatieauthenticatie ontleent haar betrouwbaarheid aan het wettelijk geregelde uitgifteproces van het UZI-register, terwijl voor de lokale authenticatie van zorgverleners een afgesproken eIDAS-betrouwbaarheidsniveau als norm geldt.

## Organisatorisch

Omdat controle in de transactie per ontwerp ontbreekt, is het toetredingsproces de eerste en belangrijkste verdediging. Voorwaarden voor deelname zijn:

* een betrouwbaar vastgestelde organisatie-identiteit (URA) gekoppeld aan het technische aansluitpunt,
* kwalificatie van het knooppunt of koppelvlak, 
* aantoonbare conformiteit aan NEN 7510 en een ingericht IAM-proces dat zowel medewerker- als systeemidentiteiten omvat en
* het JWKS-endpoint waarmee de organisatie haar verklaringen ondertekent en publiceert.

Het vertrouwen tussen partners is daarmee georganiseerd. Iedere deelnemer heeft vooraf aangetoond dat de processen waarop anderen vertrouwen daadwerkelijk op orde zijn. De doorlopende borging bestaat uit periodieke audits en hercertificering, beheerprocessen voor sleutelrotatie en intrekking bij compromittering, en een sanctie- en uitsluitingsregime van de stelselbeheerder waarmee een deelnemer wiens processen niet langer voldoen snel uit het vertrouwensdomein kan worden verwijderd. De registratie van het JWKS-endpoint als onderdeel van de toetreding maakt die uitsluiting technisch direct door te voeren. 

Het onderdeel transparantie borgt dat iedere deelnemer voor aansluiting weet op welke afspraken de anderen vertrouwen en waaraan hij zelf gehouden is. Binnen elke organisatie is regulier autorisatiebeheer de voorwaarde voor de betrouwbaarheid van de verklaringen die namens de organisatie worden afgegeven.

## Technisch
De technische maatregelen verifiëren niet de inhoud van verklaringen, maar borgen herkomst, integriteit en herleidbaarheid. Op verbindingsniveau garandeert mTLS met UZI-servercertificaten (NEN 7512) dat communicatie uitsluitend plaatsvindt tussen toegetreden, geauthenticeerde organisaties. In combinatie met het gebruik van JKWS is daarmee op meerdere niveaus bewezen welke organisatie de uitwisselingspartner is.

Logging conform NEN 7513 aan beide zijden legt vast welke zorgverlener, in welke rol, namens welke organisatie toegang heeft gehad. Hierdoor is elke raadpleging herleidbaar en het inzagerecht van de patiënt kan worden waargemaakt. De autorisatiecontrole bij de bron, op basis van de meegeleverde rolinformatie conform het autorisatieprotocol van de zorgtoepassing, vormt de laatste technische begrenzing. Ook bij een volledig vertrouwde partner worden nooit meer gegevens verstrekt dan de rol en de zorgtoepassing rechtvaardigen. Dataminimalisatie fungeert daarmee als vangnet dat de impact van een eventueel falend proces bij de partner begrenst.

# Requirements

In deze specificatie worden sommige woorden bewust in HOOFDLETTERS geschreven, zoals MOET, MAG NIET, BEHOORT en MAG. Dit markeert normatieve kracht en helpt om eisen, aanbevelingen en opties eenduidig te onderscheiden:

* MOET / MOETEN (SHALL): harde eis.
* MAG NIET (SHALL NOT): expliciet verbod.
* BEHOORT (SHOULD): sterke aanbeveling waarvan alleen met goede redenen afgeweken kan worden.
* MAG (MAY): toegestane optie.

## Identificatie en authenticatie van de zorgaanbieder

1. De zorgaanbieder MOET geregistreerd zijn in het UZI-register en MOET het URA-nummer als enige organisatie-identifier hanteren in beide uitwisselingen.
2. De zorgaanbieder MOET beschikken over een geldig UZI-servercertificaat waarin het URA is opgenomen, ten behoeve van systeem-tot-systeemauthenticatie.
3. Alle uitwisselverbindingen MOETEN worden opgezet met wederzijdse TLS (mTLS) op basis van dit UZI-servercertificaat, conform NEN 7512.
4. De zorgaanbieder (of het knooppunt dat namens hem optreedt) MOET alle uitgaande verklaringen (tokens) cryptografisch ondertekenen en MOET de bijbehorende publieke sleutels publiceren op een JWKS-endpoint.
5. Het JWKS-endpoint MOET uitsluitend ontsloten worden via een mTLS-verbinding met UZI-servercertificaat en MOET geregistreerd zijn als onderdeel van de toetreding, zodat de binding tussen endpoint en URA geborgd is.
6. De ontvangende partij MOET van ieder inkomend token de handtekening valideren via het JWKS-endpoint van de afgevende organisatie, alvorens de transactie te verwerken.
7. De zorgaanbieder MAG een knooppunt of intermediair inzetten als technisch vertegenwoordiger. De oorspronkelijke organisatie-identiteit (URA) MOET daarbij end-to-end worden meegevoerd en MAG NIET worden vervangen door de identiteit van de intermediair.

## Authenticatie van zorgverleners en zorgsystemen

8. De zorgaanbieder MOET de authenticatie van eigen zorgverleners en eigen zorgsystemen zelfstandig uitvoeren binnen het eigen beveiligingsdomein.
9. Een uitwisselende partij MAG NIET zelf authenticatie of verificatie uitvoeren op het niveau van individuele zorgverleners of individuele systemen van de uitwisselpartner. De uitwisselende partij MOET uitgaan van de betrouwbare processen van de partner zoals geborgd via het stelsel.
10. Het lokale inlogproces voor zorgverleners MOET voldoen aan het in de afspraken vastgelegde eIDAS-betrouwbaarheidsniveau. De zorgaanbieder MAG de technische invulling daarvan zelf kiezen (bijvoorbeeld multifactorauthenticatie, smartcard of single sign-on vanuit het EPD/ECD), mits binnen de normkaders.
11. De zorgaanbieder MOET de identiteiten en de authenticatie van alle systemen die namens hem communiceren (EPD, ECD, koppelvlak, knooppunt) beheren binnen het eigen IAM-proces.
12. De zorgaanbieder MOET er als organisatie voor instaan dat iedere door hem geïnitieerde uitwisseling wordt uitgevoerd door een geauthenticeerde, geautoriseerde medewerker met een geldige behandelrelatie.
13. Iedere transactie MOET als door de zorgaanbieder afgegeven verklaring de volgende attributen meedragen: de organisatie-identiteit (URA) en de rol/functie van de handelende zorgverlener, het zorgsysteem of de afdeling.
14. Voor BgZ en eOverdracht MOETEN dezelfde attributenset en hetzelfde verklaringsformaat worden gehanteerd. Het verklaringsformaat BEHOORT aan te sluiten op OpenID Connect, met het oog op migratie naar het Dezi-stelsel.

## Toetreding en organisatorische borging

15. De zorgaanbieder MOET zijn toegetreden tot het geharmoniseerde vertrouwensstelsel via een ondertekende deelnemersovereenkomst. Eén toetreding volstaat voor beide uitwisselingen.
16. De organisatie-identiteit MOET bij toetreding eenmalig en betrouwbaar zijn vastgesteld en gekoppeld aan het technische aansluitpunt.
17. Het gebruikte knooppunt of koppelvlak MOET gekwalificeerd zijn conform het toetredingsproces van het stelsel.
18. De zorgaanbieder MOET informatiebeveiligingsmanagement aantoonbaar conform NEN 7510 hebben ingericht.
19. De zorgaanbieder MOET een IAM-proces hebben ingericht dat zowel medewerker- als systeemidentiteiten omvat, met ten minste: functiescheiding, periodieke herbeoordeling van toegangsrechten en levenscyclusbeheer van accounts.
20. De zorgaanbieder MOET beheerprocessen hebben ingericht voor cryptografisch sleutelmateriaal. Sleutelrotatie MOET via het JWKS-endpoint verlopen; bij (vermoede) compromittering MOETEN de betreffende sleutels onmiddellijk worden ingetrokken.
21. De zorgaanbieder MOET meewerken aan periodieke audits en hercertificering en MOET het sanctie- en uitsluitingsregime van de stelselbeheerder aanvaarden.
22. De zorgaanbieder MOET voor aansluiting kennis hebben genomen van de geldende stelselafspraken en MOET zorgdragen dat betrokken zorgverleners op de hoogte zijn van het toegangs- en uitwisselbeleid (transparantie).

## Autorisatie

23. De beschikbaarstellende partij MOET bij iedere opvraging een autorisatiecontrole uitvoeren op basis van de meegeleverde rolinformatie, conform het autorisatieprotocol van de betreffende zorgtoepassing.
24. Er MAG NIET méér worden verstrekt dan de rol en de zorgtoepassing rechtvaardigen (dataminimalisatie), ook niet aan een volledig vertrouwde partner.
25. De ontvangende partij MOET uitsluitend de herkomst en integriteit van de verklaring valideren en MAG NIET de inhoudelijke juistheid ervan zelf verifiëren. Die juistheid is via het stelsel geborgd en contractueel gegarandeerd.

## Logging, herleidbaarheid en rechten van de patiënt

26. Beide partijen MOETEN iedere uitwisseling loggen conform NEN 7513, zodanig dat vastligt welke interne zorgverlener of externe zorgaanbieder in welke rol toegang heeft gehad.
27. De logging en de meegeleverde attributen MOETEN de zorgaanbieder in staat stellen het inzagerecht van de patiënt (Wabvpz) waar te maken, ook voor raadplegingen waarvan de authenticatie buiten het eigen domein plaatsvond.
28. De borging van behandelrelatie en patiënttoestemming MOET zijn belegd conform de per zorgtoepassing in het afsprakenstelsel vastgelegde verdeling.

## Juridische verantwoordelijkheid en aansprakelijkheid

29. Iedere zorgaanbieder MOET als zelfstandig verwerkingsverantwoordelijke (AVG) optreden voor de verwerking in de eigen systemen, met inbegrip van het knooppunt dat namens hem optreedt, en MOET het aanspreekpunt zijn voor betrokkenen bij privacyrechtverzoeken. Deze verantwoordelijkheid MAG NIET contractueel worden overgedragen aan een intermediair of uitwisselpartner.
30. De zorgaanbieder MOET volledige aansprakelijkheid aanvaarden voor de juistheid van alle namens hem afgegeven verklaringen: de identiteit en rol van de zorgverlener, de integriteit van het handelende systeem en het bestaan van de behandelrelatie.
31. De zorgaanbieder MOET de aansprakelijkheids- en vrijwaringsbepalingen uit de deelnemersovereenkomst aanvaarden, waarmee de partner die te goeder trouw op een verklaring vertrouwt juridisch is gedekt.