# Using OpenID Connect Self-Issued to achieve Verifiable Credentials Presentation

## Authors:
 -Michael B. Jones
- Egidio Casati
- Andrés Junge
- Oliver Terbu
- Dmitri Zagidulin

## Abstract
Use Cases
Technical Details
(Optional) Registration
Authorization Request
Requesting Claims in the Authorization Request
Authorization Response
Authorization Response Validation
Profile-specific Validation Rules for the Claims
Layers of Interoperability
W3C Verifiable Credentials Presentation using SIOP
Questions
Related Specs, for Reference

Outline	1
Abstract	1
Use Cases	2
Technical Details	2
(Optional) Registration	2
Authorization Request	2
Requesting Claims in the Authorization Request	2
Authorization Response	2
Authorization Response Validation	2
Profile-specific Validation Rules for the Claims	3
Layers of Interoperability	3
W3C Verifiable Credentials Presentation using SIOP	3
Questions	4
Related Specs, for Reference	4

## Abstract

TBD: It is a business decision to make use of the W3C VC Presentation and not mandatory.
Use Cases
Send requested verifiable credential to RP using OpenID Connect, e.g., Self-Issued OP (SIOP)
Example: User is opening a bank account. On registration, the Bank (acting as the RP), wants to request one or more Verifiable Credentials from the user. The user’s wallet (acting as the Self-Issued OpenID Connect Provider) presents the user with the bank’s request (so they can select which credentials to send back). The wallet can then send the credentials back to the bank.


The RP can do this via a Self Issued OpenID Connect authorization request flow. 1) (Optional) The RP can register with the user’s wallet (acting as the Self-Issued OP), to provide signing and encryption keys, for example. 2) The RP performs the regular self-issued Authorization request,
Technical Details
(Optional) Registration
RP has a chance to register keys for signing and encryption (for the auth request below)
Authorization Request
As specified in OpenID Connect
(Also see Request Objects section below for additional possibilities)
Request object: signed/encrypted
plain
Requesting Claims in the Authorization Request

types of credentials requested
discuss scopes (wrt. registration)
possibly address schemas
need to address restricting source (e.g. we need claims only from Canadian sources)

## Authorization Response

The authorization response contains the requested verifiable credentials in the id token.

## Authorization Response Validation


### Profile-specific Validation Rules for the Claims

In contrast to the OIDC specification, this document defines validation rules in case W3C Verifiable Credentials Presentation was included in the id token. Note, other methods exist to express and encode  
Layers of Interoperability
There are two layers of interoperability. First, it should be possible to demonstrate interoperability with traditional OIDC clients that implement the SIOP specification. This means, if OIDC claims/scopes were requested, the resulting W3C credentialsSubject will not be interpreted as a W3C Verifiable Credential Presentation. OIDC clients will inspect the signature of the id_token and verify the signature according to the OIDC SIOP specification.  Secondly, clients that additionally implement the W3C VC specification would extract the W3C VC Presentation from the id_token, and verify the proof. The proof follows the W3C VC Presentation specification, i.e., it is represented either as a JWS, or a JSON-LD proof.

## Compliance with OpenID Connect

## Compliance with W3C Verifiable Credentials Specification

	TBD: what is the role of distributed and aggregated claims?
W3C Verifiable Credentials Presentation using SIOP
RP request W3C VC in the OIDC authorization request using the claim and scope parameter.
The id token could be seen as the W3C VC Presentation. The id token could either be the W3C Verifiable Credentials Pr can be conveyed as OIDC claims in the id token.
Relationship to Aggregated and Distributed Claims and define Validation Rules in the DID Context.
...


OIDC
W3C Spec
Plain id_token

```
{
   "iss": "http://server.example.com",
   "sub": "248289761001",
   "aud": "s6BhdRkqt3",
   "nonce": "n-0S6_WzA2Mj",
   "exp": 1311281970,
   "iat": 1311280970,
   "name": "Jane Doe",
   "given_name": "Jane",
   "family_name": "Doe",
   "gender": "female",
   "birthdate": "0000-10-31",
   "email": "janedoe@example.com",
   "picture": "http://example.com/janedoe/me.jpg"
  }
```

Aggregated Claims (OIDC)

```
{
  "name": "Jane Doe",
  "given_name": "Jane",
  "family_name": "Doe",
  "birthdate": "0000-03-22",
  "eye_color": "blue",
  "email": "janedoe@example.com",
  "_claim_names": {
    "address": "src1",
    "phone_number": "src1"
  },
  "_claim_sources": {
    "src1": {
      "JWT": "jwt_header.jwt_claims.jwt_signature"  <- JWT compact serialization
    }
  }
}
```

JSON object that MUST contain the JWT member whose value is a JWT [JWT] that MUST contain all the Claims in the _claim_names object that references the corresponding _claim_sources member. Other members MAY be present.

```
// This is a single JWT:
{
  "iss": "did:example:ebfeb1f712ebc6f1c276e12ec21",
  "jti": "urn:uuid:3978344f-8596-4c3a-a978-8fcaba3903c5",
  "aud": "did:example:4a57546973436f6f6c4a4a57573",
  "iat": "1541493724",
  "exp": "1573029723",
  "nonce": "343s$FSFDa-",
  "vp": {
    "type": ["VerifiablePresentation"],
    // base64url-encoded JWT as string
    "verifiableCredential": ["..."]   <- where ‘address’ and ‘phone_number’ claims would go
  }
}
```

Distributed Claims (OIDC)

```
{
  "name": "Jane Doe",
  "given_name": "Jane",
  "family_name": "Doe",
  "email": "janedoe@example.com",
  "birthdate": "0000-03-22",
  "eye_color": "blue",
  "_claim_names": {
    "payment_info": "src1",
    "shipping_address": "src1",
    "credit_score": "src2"
  },
  "_claim_sources": {
    "src1": {
      "endpoint": "https://bank.example.com/claim_source"
    },
    "src2": {
      "endpoint": "https://creditagency.example.com/claims_here",
      "access_token": "ksj3n283dke"
    }
  }
}
```

Questions
Where to put the W3C Verifiable Credential claims? (ID Token, etc..)
Related Specs, for Reference
* https://openid.net/specs/openid-connect-core-1_0.html
* https://www.youtube.com/watch?v=tTeN_SxQ_OI , [NS18]
* https://nat.sakimura.org/2018/12/11/todo-list-for-self-issued-op/ , [NS18]
* https://iiw.idcommons.net/OIDC_DID-Auth_Profile , [II18]
* https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/did-auth.md , [RWOT6]
* https://iiw.idcommons.net/Open_ID_v._FIDO_v._SSI
* https://w3c.github.io/vc-data-model/#json-web-token , [W3C]
* https://joinup.ec.europa.eu/sites/default/files/document/2015-11/eidas_saml_attribute_profile_v1.0_2.pdf (IT national eIDAS SAML Attribute profile]
