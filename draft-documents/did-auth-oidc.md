# Using OpenID Connect Self-Issued to achieve DID Auth

Authors:

- Ivan Basart
- Egido Casati
- Michael B. Jones
- Andrés Junge
- David Stark
- Oliver Terbu
- Dmitri Zagidulin

## Abstract

Proving control of a DID requires proving ownership of a private key corresponding to a public key for the DID. Of course, this could be done with a new DID-specific protocol. However, there already exist standard protocols for proving ownership of a public/private key pair.

This paper describes how to reuse the OpenID Connect Self-Issued protocol messages to prove control of a DID.  It describes both why and how to do this.  Related topics, such as release of claims are also touched upon.

## Background and Motivations

OpenID Connect is a widely used JSON/REST-based identity protocol.  Section 7 of the OpenID Connect Core [ref] specification defines how to authenticate using an identity that you control yourself, which is represented by a public key.  The authentication protocol messages prove that you are in possession of the private key corresponding to the public key.

We believe that using the OpenID Connect Self-Issued functionality to prove ownership of a DID has multiple advantages.  It reuses existing functionality, possibly accelerating adoption relative to approaches utilizing new custom protocols.

## Use Cases

- Sign into RP
- Sign into RP with a DID
- Presentation of Claims

## ## Terminology

- SIOP - Self-Issued OpenID Connect Provider (Issuer+Holder in the SSI model)
- RP - Relying Party (the Verifier in the SSI model)

Non-Goals / Out of Scope

- Using DID Auth for local authentication of user to the Self-Issued OpenID Provider (fairly obvious, no spec needed)
- Exchange of verifiable claims (separate paper)
- Zero Knowledge Proofs (could be added by experts in the field)
- Issuing access tokens to resources

## Nature of the Design Decisions

- Whenever possible, reuse of existing specs.
- Remain compatible with existing specs that are reused.
- Layer DID auth functionality such that it can be added incrementally without breaking existing uses of the self-issued functionality

## How to Prove Control of a DID

### Keys Used

- The self-issued key used must be one of the DID Authentication Section keys

### Authorization Request

- As specified in OpenID Connect
- (Also see Request Objects section below for additional possibilities)
- Do we want something in the request saying that a DID-based identity is being requested, and if so, what?

### Authorization Response

- Add a claim with name &quot;did&quot; in the ID Token that contains the DID
- Note that the &quot;sub&quot; claim is base64url encoding of JWK Thumbprint, as specified in OpenID Connect Core Section 7

### DID Validation

\&lt;put in some language that this is a layer above the SIOC flow. that this validation is for the did auth use case specifically.\&gt;

When using this flow the client MUST validate the response as follows:

1. Verify the response is a valid Self-Issued OpenID Provider Response (as specified in Section 7.4 of the OpenID Connect Core specification
2. The id token returned contains the additional attribute &quot;did&quot; and that it is a valid DID format. (Conforms to the ABNF rules of the DID spec). Note: If the ID Token does _not_ contain a &quot;did&quot; attribute, it may still be a valid SIOC ID Token, but it is not a valid DID Auth response.
3. Perform a [DID Resolution](https://w3c-ccg.github.io/did-resolution/) operation (the specifics vary by individual DID method, but typically involves using a resolver retrieve the DID document specified by the did attribute in the ID Token).
4. The self-issued key used to sign the response (specified in the sub\_jwk claim) is present and not expired or revoked in the &quot;authentication&quot; attribute of the DID Document. The key specified in the DID Document can be in various formats and

TODO: Ask M. Jones about Section 7.1 SIOC Discovery -- the static configuration value implies that ONLY RS256 algorithm is supported as an ID Token signing algorithm.

- Steps are layered on top of the self-issued ID Token validation steps
- First do self-issued validation steps
- Then retrieve the DID
- Verify that the self-issued key is one of the DID Authentication Section keys
- Verify that the algorithm used with the key is the one specified in the DID. (Note, conversion/translation between the algorithms from JOSE format to Linked Data keys format will likely need to be done, and is out of scope of this document.)
- Verify that the DID key has not expired or been revoked, in cases where expiration and/or revocation is possible

### Relationship to Other OpenID Connect Features

#### Provider Selection via DID Document

- A DID Document could optionally contain (in the serviceEndpoint section) the user&#39;s preferred OpenID Connect Provider (or a set of preferred providers). For example: …
This is useful for situations where a user&#39;s DID is already known by the RP (or transmitted out of band).

#### Provider Discovery

- Discuss using key sets in the self-issued discovery doc
  - A jwk\_set value could be included in the discovery information
- DID Auth as a Provider Discovery method for OIDC ?
- If the OP&#39;s DID has encryption keys, they could be advertised in the OP&#39;s jwk\_set discovery information

#### Dynamic Registration

- (Optional) Can we discuss the ability for a client app to use a DID as its client\_id (instead of a redirect\_uri)? Both in the Registration request -- [Section 7.2.1](https://openid.net/specs/openid-connect-core-1_0.html#RegistrationParameter), self issued `registration` , param, and [Dynamic Registration](https://openid.net/specs/openid-connect-registration-1_0.html) spec, and in the Authorization request?
- If the RP has a DID, keys used to encrypt content to that DID could be advertised in the RP&#39;s jwk\_set or jwk\_uri parameters if encrypted ID Tokens are being used

#### Presentation of Claims

- Already supported by OpenID Connect spec
- Can include any claims pertinent to use case
- For instance, could include some claims using JWT claim definitions from W3C Verifiable Credentials spec, if relevant to the use case
- As specified in OpenID Connect Core, aggregated and distributed claims can be used in responses, including in Self-Issued ID Tokens
  - For instance, National eID claims, such as claims from EIDAS claim providers could be represented in that way
- Note that OpenID Connect does not define validation rules for claims issued by third parties, as they are in general, specific to the use case

#### Request Objects

- Request Objects could be used to authenticate RP
- Request Object signing key could come from an RP DID

#### Non-Self-Issued OpenID Connect Flows

- Flows using a third party OP cannot be used to prove control of a DID
  - They lack the public key as the identifier of the subject of the identity
- A &quot;did&quot; claim could be returned as a UserInfo or ID Token claim, which means that the OP is asserting that the DID is associated with the End User

## Conclusions

- Reuse of the OpenID Connect Self-Issued mechanism to prove control of a DID is effective and straightforward.  The authors believe that reusing this mechanism will be more effective in promoting DID adoption than using a new custom DID authentication protocol.

## Open Questions

- To be explored and specified further: Use case where the Self-Issued flow is being initiated from a Desktop browser (or other environment that does not have a protocol handler installed). Current deployed or proposed solutions:
  - This is currently being solved by methods like uPort via a combination of QR code which contains a JWT request that includes the response callback of the RP.
  - Potentially could be solved by an agreed-upon site hosted by the community, &quot;Log in with SSI&quot;, that would redirect desktop user to a page that shows the QR code.

## RWoT Paper Initial Proposals:

- [OIDC Profile for SSI](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/oidc-profile-for-ssi.md)  by Oliver Terbu, Andres Junge
- [Proof of Key Ownership with OpenID Connect Self-Issued Identities](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Proof_of_Key_Ownership_with_OpenID_Connect_Self-Issued_Identities.md)

## Related Specs, for Reference:

- [https://openid.net/specs/openid-connect-core-1\_0.html](https://openid.net/specs/openid-connect-core-1_0.html)
- [https://www.youtube.com/watch?v=tTeN\_SxQ\_OI](https://www.youtube.com/watch?v=tTeN_SxQ_OI) , [NS18]
- [https://nat.sakimura.org/2018/12/11/todo-list-for-self-issued-op/](https://nat.sakimura.org/2018/12/11/todo-list-for-self-issued-op/) , [NS18]
- [https://iiw.idcommons.net/OIDC\_DID-Auth\_Profile](https://iiw.idcommons.net/OIDC_DID-Auth_Profile) , [II18]
- [https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/did-auth.md](https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/did-auth.md) , [RWOT6]
- [https://iiw.idcommons.net/Open\_ID\_v.\_FIDO\_v.\_SSI](https://iiw.idcommons.net/Open_ID_v._FIDO_v._SSI)
- [https://w3c.github.io/vc-data-model/#json-web-token](https://w3c.github.io/vc-data-model/#json-web-token) , [W3C]
