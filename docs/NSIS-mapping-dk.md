| **NSIS-krav** | **Beskrivelse** | **Relevant Authentik-funktion / dokumentation** |
|--------------|------------------|--------------------------------------------------|
| **3.1.1 – Ansøgning og registrering** | Brugeren skal registreres med tilstrækkelig identitetskontrol | [Identity Sources](https://docs.goauthentik.io/docs/security) – Integration med eksterne IdP’er (fx MitID, LDAP, SAML) |
| **3.2.1 – Styrke af identifikationsmidler (IAL)** | Krav til styrke og sikkerhed af identitetsmidler | [MFA Setup](https://docs.goauthentik.io/docs/security) – Understøtter TOTP, WebAuthn, Duo |
| **3.3.1 – Autentifikationsmekanismer (AAL)** | Krav til autentifikationsstyrke og -protokoller | [Authentication Flows](https://docs.goauthentik.io/docs/security) – OIDC, SAML, step-up MFA |
| **4.1.3 – Informationssikkerhedsledelse** | Krav til ISMS og sikkerhedspolitikker | Dækkes af ISO 27001-certificeret datacenter og jeres ISMS |
| **4.1.4 – Logning** | Krav om logning af hændelser og adgang | [Logging](https://docs.goauthentik.io/docs/security) – Loginforsøg, flow-udførelser, systemændringer |
| **4.1.6 – Tekniske kontroller** | Kryptering, adgangsstyring, netværkssikkerhed | [Security Hardening](https://docs.goauthentik.io/docs/security) – TLS, RBAC, scopes, API-begrænsning |
| **4.1.7 – Anmeldelse og revision** | Krav om dokumentation og revisorerklæring | Brug NSIS kontrolskema og bilag 2–5. Authentik dokumenteres som komponent |
| **3.2.3 – Suspendering og spærring** | Mulighed for at deaktivere identiteter | [User Management](https://docs.goauthentik.io/docs/security) – Deaktivering og suspendering af brugere |
| **3.3 – Tokenhåndtering og sessioner** | Krav til session lifetime, tokenbeskyttelse | [OAuth2 Provider Settings](https://docs.goauthentik.io/docs/security) – TTL, scopes, session policies |
