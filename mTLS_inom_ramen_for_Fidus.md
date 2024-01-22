![Skolverkets logotyp](media/Skolverket.png)

# mTLS inom ramen för Fidus

För att säkerställa åtkomst till Skolverkets provisioneringstjänst för digitala nationella prov (DNP) används ömsesidig transportlagersäkerhet, ofta benämnd mutual TLS (mTLS[^1]). mTLS innebär att både huvudmannen och Skolverket autentiserar sig för varandra vid anslutningen med certifikat där organisations-numret används som identifierare.

Styrgruppen beslutade i december 2023 att Fidus interfederation utökas med funktioner för autentisering med stöd av Federated TLS Authentication (FedTLS[^2]).

Machine and Organization Authentication (Moa[^3]) är den praktiska tillämpningen av FedTLS för autentisering till provisioneringstjänsten för DNP. Fidus stödjer i och med styrgruppens beslut den tekniska profilen[^4] för Moa.

Utöver FedTLS accepterar provisioneringstjänsten för DNP kvalificerade certifikat för webbserverautentisering (QWAC[^5]) i enlighet med eIDAS-förordningen (EU 910/2014) [^6]. Certifikaten behöver vara försedda med attribut för klientautentisering och innehålla organisationsnummer.

Under en övergångsperiod accepterar provisioneringstjänsten för DNP även historiskt etablerade funktionscertifikat som utfärdats före 2024-07-01 från följande utfärdare:

-   SITHS e-id funktionscertifikat (Inera)
-   E-identitet för offentlig sektor – EFOS (Försäkringskassan)
-   ExpiTrust EID CA V4[9] (tidigare Steria AB e-Tjänstelegitimationer Kort CA v2 hos Expisoft AB)

Certifikaten behöver vara försedda med attribut för klientautentisering och innehålla organisationsnummer.

[^1]: https://en.wikipedia.org/wiki/Mutual_authentication

[^2]: https://datatracker.ietf.org/doc/draft-halen-fed-tls-auth/

[^3]: https://wiki.federationer.internetstiftelsen.se/pages/viewpage.action?pageId=20545581

[^4]: https://wiki.federationer.internetstiftelsen.se/display/IF/Moa+technical+profiles

[^5]:  https://eidas.ec.europa.eu/efda/tl-browser/\#/screen/search/type/3?searchCriteria=eyJjb3VudHJpZXMiOlsiQVQiLCJCRSIsIkJHIiwiQ1kiLCJDWiIsIkRFIiwiREsiLCJFRSIsIkVMIiwiRVMiLCJGSSIsIkZSIiwiSFIiLCJIVSIsIklFIiwiSVMiLCJJVCIsIkxJIiwiTFQiLCJMVSIsIkxWIiwiTVQiLCJOTCIsIk5PIiwiUEwiLCJQVCIsIlJPIiwiU0UiLCJTSSIsIlNLIiwiVUsiXSwicVNlcnZpY2VUeXBlcyI6WyJRV0FDIl19

[^6]: https://eur-lex.europa.eu/legal-content/SV/TXT/?uri=CELEX:32014R0910
