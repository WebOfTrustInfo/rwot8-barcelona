# OIDC Profile for SSI
By Oliver Terbu, Andres Junge

## Introduction
The current online authentication and identity landscape is dominated by the typical Identity Provider (IdP) pattern. Protocols like OpenID Connect (OIDC) [OIDC] respectively OAuth2 and the Security Markup Language (SAML) Web Browser SSO profile is mostly used in this area. For example, behind the scenes, Google uses the OIDC protocol in their sign-in button. After user authentication and consent, and depending on the flow, clients, i.e., Relying Parties (RP), will receive up to three different tokens, i.e., id token, refresh token, access token. The RP will use these tokens with the IdP to obtain data about the user:

- The id token can already contain personally identifiable information, i.e., the requested data about the user.
- The access token (typically a bearer token) provides access to the user info endpoint, which allows the RP to request or refresh the required data. The IdP usually hosts the user info endpoint.
- Because access tokens are valid for a shorter period, the refresh token could be used to obtain a new access token.

This approach typically has an impact on the user’s privacy by allowing the OpenID Connect Provider (OP) to track the user's behavior. Furthermore, relying on a bearer token has also security implications. Of course, mechanisms like token binding exist to mitigate the security issues, but they are still not common practice. While SAML loses its importance, OIDC is still there, actively maintained, and has a lot of support from the industry and many independent OIDC client implementations are available. Depending on the area, e.g., telcos or government, dedicated OIDC profiles were created that specifically address their requirements. An OIDC profile is a specific conformity configuration of pieces of the OIDC specifications, e.g., flows, parameters. While the traditional IdP approach has a lot of downsides, the underlying  OIDC protocol could provide enough flexibility to support SSI.

## Goal

The goal is to continue the work on an OIDC profile for SSI based on [NS18] and [II18] and finalize the first version of it. The profile should support SSI wallets without needing to have a central IdP. It is assumed that the user controls and provides consent with an SSI wallet. We anticipate that this will likely be a mobile app on Android and iOS. Of course, an online wallet should also be considered. While it is possible that the SSI wallet directly provides the data, it should still be possible for an RP to obtain data about the user while the SSI wallet is offline. 

During RWOT6, people from the SSI community already identified that OIDC due to its flexibility it could play a specific role in DID Authn [RW18]. Nat Sakimura, Chair of the OpenID Foundation, started an article how OIDC could be used in an SSI system [NS18]. The main idea was to make use of the Self-Issued OP (SIOP) specification that is part of the OIDC core specification. An SSI wallet on an edge device like a smartphone could act as a SIOP. However, DID support and how to leverage DIF concepts was not described in this context. At IIW IIWXXVII, a session on the feasibility of an OIDC profile for DID Authn was hosted to validate a similar approach based on DIDs and concepts developed by the SSI community [II18]. 

## OIDC Profile
The goal is to continue the work on an OIDC profile for SSI based on [NS18] and [II18], and finalize the first version of it. The profile should support SSI wallets without needing to have a central IdP. It is assumed that the user controls and provides consent with an SSI wallet.  We anticipate that this will likely be a mobile app on Android and iOS. Of course, an online wallet should also be considered. While it is possible that the data is directly provided by the SSI wallet, it should still be possible for an RP to obtain data about the user while the SSI wallet is offline.  

The approach entails the following:
- Leverage existing OIDC flows, i.e., request/response message, and data structures
- Use the SIOP specification to solve OP discovery
- Use the aggregated and distributed claims OIDC specification to support multiple verifiable credentials issuer. Essentially, this means the id token contains a multitude of JWT issued by different issuers.
- The SSI holder signs the id token itself.
- Add DID support for request and response message, i.e., JWT. This was already addressed as part of the ongoing W3C Verifiable Credentials specification [W3C].
- Client-side DID Auth could additionally protect user info endpoint. 

The following challenges need to be tackled by the OIDC profile:
- How to align the id token with the DID specification?
- How to align the id token format with the W3C VC specification?
- How to provide access to the data when the user is offline?
- How to ensure and improve privacy and mitigate mining the user?
- How to deal with client registration?
- How to achieve end to end encryption?
- How to enable encrypted data stores?
- ...

## References
* https://openid.net/specs/openid-connect-core-1_0.html
* https://www.youtube.com/watch?v=tTeN_SxQ_OI, [NS18]
* https://nat.sakimura.org/2018/12/11/todo-list-for-self-issued-op/, [NS18]
* https://iiw.idcommons.net/OIDC_DID-Auth_Profile, [II18]
* https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/did-auth.md, [RW18]
* https://iiw.idcommons.net/Open_ID_v._FIDO_v._SSI
* https://w3c.github.io/vc-data-model/#json-web-token, [W3C]

