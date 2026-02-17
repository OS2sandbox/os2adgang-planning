# Reference architecture proposal
> Example diagram using the [C4 Model](https://c4model.com/) of how version 0.9 could be designed to integrate with [the danish municipal SAML Idp](https://digitaliseringskataloget.dk/integration/sf1511) and [organization SOAP/XML metadataprovider](https://digitaliseringskataloget.dk/integration/sf1500)

```mermaid
C4Context
  title C4 System Context diagram - Fælleskommunal Adgangsstyring og Organisations data
  
  %% --- The Entire Enterprise Context ---
  Enterprise_Boundary(OrgBoundary, "Os2AI") {

    %% APPLICATION DOMAIN
    System_Boundary(Application, "Application Domain") {
      System(appA, "OS2 Appllication 1", "")
      System(appC, "OS" Application 2", "")
    }
          
    %% PLATFORM DOMAIN
    System_Boundary(platform, "Platform Service Domain") {
      Container_Boundary(Keycloak, "Identity & Acess Management") {
        Container(keycloak_core, Identity & Access Management, "Keycloak", "Manages authentication, authorization, and security")
        %% Component definition inside the Container for visual grouping
        Component(spi, "Metadata Adapter", "Keycloak SPI - fk_org.jar", "Fetches attributes via SOAP and maps to OIDC claims")
      }
      System_Boundary(configmaps, "ConfigMaps") {
        Component(config, "FKA IDP config", "ConfigMap - realm.json", "Realm & broker configuration")
      }
    }
  }


Enterprise_Boundary(KOMBITBoundary, "KOMBIT") {
    System_Ext(fkadg, "Fælleskommunal Adgangsstyring (FKA)", "SAML Idp")
    System_Ext(fkorg, "Fælleskommunal Organisation (FKO)", "SOAP/XML Metadata attributes/roles.")
}
  
  
  %% --- Relationships (The Flow) ---

  %% Identity Brokering
  Rel(keycloak_core, config, "Read config")
  Rel(keycloak_core, fkadg, "SAML Identity Lookup")
  Rel(keycloak_core, spi,"Provide user context")
  Rel(spi, fkorg, "Metadata Lookup", "SOAP/XML over HTTPS")
  Rel(keycloak_core, appA, "Authentication", "OpenID Connect")
  Rel(keycloak_core, appC, "Authenticated User", "OpenID Connect")
  
  UpdateLayoutConfig($c4ShapeInRow="2")
```
