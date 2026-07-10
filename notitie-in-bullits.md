Intro met bullets

Juridisch kader:
Zorgaanbieder (bronhoudend) is niet verantwoordelijk voor authenticatie van zorgverleners (medewerkers) of systemen bij een andere zorgaanbieder
Wel is de bronhouder verantwoordelijk om vast te stellen wie de andere zorgaanbieder is; en wat het doel is van de uitwisseling
Er moet voor eOverdracht en BGZ-verwijzing sprake zijn van een (startende) behandelrelatie, maar er is geen verplichting om dit schriftelijk vastgelegd te hebben.

Bij verwijzingen weet je de behandelrelatie je kun je toestemming veronderstellen. Doelstelling/grondslag voor uitwisseling staat daarmee ook vast.

Eisen voor authenticatie en autorisatie voor uitwisseling:
Wederzijds vaststellen identiteit zorgaanbieder
Doelstelling moet expliciet genoemd worden om ervoor te zorgen dat deze doelstelling te onderscheiden is andere doelstellingen (later te ondersteunen uitwisselingen/doelstellingen).



—

Kern elementen techniek
OAuth2
Client credentials flow
Client auth via private key JWT
Aanvullende maatregelen uit FAPI
Extra zorgattributen op basis van Rich auth request (RAR)

Onderbouwing kern elementen techniek:

Niet zelf verzinnen - hergebruik van bewezen internationale ontwikkelingen en standaarden, en in de praktijk actief gebruikt en geaudit

Voorsorteren op LDN ontwikkeling - dat mTLS voor transportlaag voorschrijft, waarbij nu de aanname is dat de gebruikte certificaten niet uitsluitend voor zorgaanbieder(-identificatie) bedoeld zijn, maar ook, bijvoorbeeld, voor dienstverleners.

Veilig protocol -> FAPI 2.0 beproefde en gedragen internationale standaard, bundelt best practises rondom OAuth -> geen mTLS -> private key JWT
OAuth2: geen discussie - de defacto standaard
Client credentials flow: geen actieve gebruiker, de defacto standaard voor dit soort uitwisselingen
CA via PK JWT: onafhankelijk van transport; defacto standaard, onderbouwd door FAPI
Maatregelen uit FAPI (zie eerder)
Binnen Nederland claims nodig voor purpose-of-use (grondslag), FAPI stelt voor hiervoor standaard extensie object te gebruiken
Locations (resource server(s) waartoe je toegang vraagt) is ook standaard FAPI/RAR ondersteund attribuut
Access token signed is gangbaar, nodig vanwege gebrek mTLS

Bij pull die niet vooraf gaat door notify (dus geen verwijzing - geen behandelrelatie) zien wij hetzelfde model (geen zorgverlener in uitwisseling), wel is er een aanvullende maatregel nodig voor informatiebeveiligingsdoeleinden in dit scenario. Ook bij deze pull moet de zorgaanbieder type erbij.
