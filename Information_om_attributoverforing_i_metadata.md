![Skolverket](media/Skolverket.png)

# Information om attributöverföring i metadata

Att automatisera och förenkla överföring av attribut såsom personuppgifter vid federativ inloggning är nödvändigt för skalbar användning av tjänster inom identitetsfederationer. Om inte någon typ av automatisering genomförs måste varje identitetsutfärdare ta reda på och genomföra manuell konfiguration av vilka attribut som en specifika tjänst behöver. Skolfederation och SWAMID hanterar detta på olika sätt idag och gissningsvis ev. ytterligare fedarationer kommer ha sina egna modeller. Baserat på detta föreslår jag efter diskussion med Stefan nedanstående modell som fungerar för både Skolfederation och SWAMID.

De tjänster som förmedlas via Fidus definierar vilka attribut de behöver för att åtkomst till tjänsten ska fungera genom att följa modellen för begärda attribut i metadata såsom definierat i avsnitt 2.4.4.2 i Metadata for the OASIS Security Assertion Markup Language (SAML) V2.0[1]) inkl. flagga för att attributet krävs. Attribut som får begäras på detta sätt är attribut som behövs för att ge användaren tillgång till tjänsten samt attribut som är nödvändiga för ev. personalisering. För de tjänster i Fidus som har användare vid universitet och högskolor ska även SWAMIDs modell för entitetskategorier användas, se nedan.

Exempel på begäran av attribut i metadata:

``` xml
<md:AttributeConsumingService index="1">
    <md:ServiceName xml:lang="sv">Tjänstenamn på svenska</md:ServiceName>
    <md:ServiceName xml:lang="en">Tjänstenamn på engelska</md:ServiceName>
    <md:RequestedAttribute FriendlyName="displayName" Name="urn:oid:2.16.840.1.113730.3.1.241" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri" isRequired="true"/>
    <md:RequestedAttribute FriendlyName="eduPersonPrincipalName" Name="urn:oid:1.3.6.1.4.1.5923.1.1.1.6" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri" isRequired="true"/>
    <md:RequestedAttribute FriendlyName="mail" Name="urn:oid:0.9.2342.19200300.100.1.3" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri" isRequired="true"/>
    <md:RequestedAttribute FriendlyName="eduPersonScopedAffiliation" Name="urn:oid:1.3.6.1.4.1.5923.1.1.1.9" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri" isRequired="true"/>
</md:AttributeConsumingService>
```

Skolfederation erbjuder idag ingen automatiskt konfiguration av attributöverföring baserad på information i metadata. De diskuterar om de ska använda ovanstående standard från OASIS för attributöverföring inkl. ett nytt stödverktyg för skolhuvudmän. Stödverktyget tillsammans med specifikt metadataflöde för skolhuvudmannen skulle ge möjlighet till enklare konfiguration av attributöverföring baserat på metadata istället för manuell konfiguration för varje enskild tjänst. Även om Skolfederation idag inte har ett tekniskt stöd för hantering av begärda attribut för metadata förenklar denna markering för skolhuvudmän att fatta informerade beslut om attributöverföring.

SWAMID använder idag automatiserad attributreelase genom entitetskategorier. En entitetskategori är i princip en markering i metadata som talar om hur och vilka attribut som tjänsten förväntar sig inkl. varför från identitetsutfärdaren. Entitetkategorier är definierade i RFC 8409. För tjänster registrerade i Fidus kommer SWAMID att använda entitetskategorin GÉANT Data Protection Code of Conduct for Service Providers in EU/EEA (CoCo)[3]. Denna entitetskategori använder i korthet ovanstående standard från OASIS för att definiera vilka attribut som måste överföras samt har ett krav på att en html-baserad privacy policy, på både svenska och engelska, måste skrivas och läggas in i metadata med beskrivning om hur entitetskategorin uppfylls samt innehållandes URL-hänvisning via URL. SWAMID har tagit fram en mall för hur man kan skriva en sådan privacy policy[4].

## Referenser

- [1] OASIS Security Assertion Markup Language (SAML) V2.0: (https://docs.oasis-open.org/security/saml/v2.0/saml-metadata-2.0-os.pdf)

- [2] RFC 8409 - The Entity Category Security Assertion Markup Language (SAML) Attribute Types: (https://tools.ietf.org/html/rfc8409)

- [3] GÉANT Data Protection Code of Conduct for Service Providers in EU/EEA (CoCo): (http://www.geant.net/uri/dataprotection-code-of-conduct/v1)

- [4] SWAMIDs exempelmall för Privacy Policy: (https://wiki.sunet.se/display/SWAMID/Service+Provider+Privacy+Policy+Template)
