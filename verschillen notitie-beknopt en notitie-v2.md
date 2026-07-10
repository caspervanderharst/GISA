# Inventarisatie: verschillen tussen notitie-v2.md en notitie-beknopt.md

Beide notities delen de kern (federatief vertrouwensmodel, URA/UZI, OAuth 2.0 + FAPI 2.0 + RAR, `private_key_jwt`, mTLS, veronderstelde toestemming, bevraging-use case). Hieronder de onderwerpen die in de één wél en in de ander níet (of veel beperkter) aan bod komen.

## Alleen in `notitie-v2` (ontbreekt in beknopt)

**Structuur & inleidende delen**
- Aparte **leeswijzer** (§1.3) en expliciete **vraagstelling** met vertaling van de 3 memo-vragen naar 3 herformuleerde vragen (§1.2).
- Duiding van de memo-inhoud: onenigheid over **interpretatie van NEN 7512** en welke zorgverlener-authenticatie nodig is (§1.1).
- Volledige **begrippen- en afkortingentabel** (§2).

**Conceptueel kader**
- Het expliciete onderscheid **interne vs. externe authenticatie & autorisatie** als rode draad (§4).
- Uitgebreide, didactische uitwerking van het federatieve model: de **paspoort/EU-analogie**, de twee routes ("vertrouwen op het middel" vs. "vertrouwen op het proces") (§5.1–5.3).
- De **zeven bouwstenen** van het vertrouwensmodel (identificatie, authenticatie, autorisatie, behandelrelatie, patiënttoestemming, logging, transparantie) (§5.4).
- **eIDAS-begripsafbakening**: betrouwbaarheidsniveaus gelden voor personen, niet voor systeemcertificaten (§4.3, §8.2).

**Risicoborging (vraag 3)**
- De volledige **matrix van drie momenten (vooraf/doorlopend/achteraf) × drie sporen (juridisch/organisatorisch/technisch)** (§8).
- Concrete **toetredingseisen, audits, hercertificering, sleutelrotatie, sanctie-/uitsluitingsregime** en stelselbeheerder (§8.3).

**Technische uitwerking**
- Expliciete **afweging Verifiable Credentials / EU Business Wallet / eIDAS 2.0** en waarom die (nog) niet gekozen worden (§9.1).
- Bredere **OAuth-uitleg**: alle flows (Authorization Code/PKCE, Device Code, Refresh Token) en alle client-authenticatiemethoden (§9.2).
- Vergelijking van de profielen **SMART Backend Services, IHE IUA en UDAP B2B** met voor-/nadelen (§9.4).
- **Bijlage A: normatieve requirements** (NL.GISA.*, met SHALL/SHOULD/MAY) en de **requirements-mappingtabel** (§9.7).
- Vermelding van **DICOM/niet-FHIR endpoints en scopes**, plus "niet in beton gegoten / verbetervoorstellen welkom" (§9.8).
- Genoemde begrippen die in beknopt ontbreken: **Wegiz, IAM, ECD, EHDS/Xt-EHR/Euridice, Dynamic Client Registration (DCR), Generieke Functie Adressering**.

**Illustraties**
- Twee **afbeeldingen** (federatief model + borgingsmatrix).

## Alleen in `notitie-beknopt` (ontbreekt of impliciet in v2)

- **WGBO expliciet** als grondslag ("noodzakelijk voor de uitvoering van de behandelingsovereenkomst"). v2 noemt WGBO niet met naam.
- Expliciete stelling dat de behandelrelatie/behandelovereenkomst **niet schriftelijk hoeft te worden vastgelegd**.
- **Vijf genummerde technische eisen** als compacte, zelfstandige lijst (§4) — v2 verspreidt deze over meerdere hoofdstukken en de requirements-bijlage.
- **HL7 en IHE** genoemd als organisaties die OAuth 2.0 voorschrijven (v2 noemt dit niet zo).
- In het **sequentiediagram**: expliciete **CA-deelnemer (UZI-register) met OCSP/CRL-intrekkingscontroles** als aparte stappen én expliciete **verificatie van de handtekening op het access token door de client**. (In v2 staat OCSP/CRL alleen in requirement ZA.6, niet in het diagram; het diagram van v2 heeft geen CA-participant.)
- Het **`locations`-attribuut** wordt in beknopt expliciet toegelicht als door RAR ondersteund standaardattribuut.

## Belangrijkste observatie

De verschillen zijn vooral **detailniveau en vorm**, niet inhoudelijke tegenspraak. `notitie-v2` is de volledige, genummerde versie met kader, requirements en afwegingen; `notitie-beknopt` comprimeert dit tot de kernboodschap maar bevat een paar **concrete details die in v2 ontbreken** — met name de expliciete **WGBO-grondslag**, de **HL7/IHE-verwijzing** en de **OCSP/CRL- en access-token-verificatiestappen in het diagram**. Als beknopt de definitieve samenvatting wordt, zijn dat de punten om te checken of ze bewust zijn weggelaten of juist teruggebracht moeten worden naar v2.