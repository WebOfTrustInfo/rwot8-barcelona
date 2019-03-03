# Establishing the Identity of the Issuer by the Verifier in Verifiable Credentials

![](https://i.imgur.com/6M9EMuY.jpg)

## Abstract
To be completed

## Problem statementent / purpose
Trust according to [LDAPWiki](https://ldapwiki.com/wiki/Trust), requires:

>One party (trustor) is willing to rely on the actions of another party (trustee)

Trust is based on experience and/or evidence as well as fundamental properties such as identity, integrity.

The implied requirement for trust is that the trustor understands who they are trusting, i.e. the identity of the trustee. 

In the Verifiable Credential space this translates to how the Verifier can determine the real world identity of the Issuer of the Verifiable Credential.

Current Decentralised systems (VC with DID?) ensured the integrity (tamper evidence and providence?) of the credentials issued against a subject.
Based W3C specs, the value associated with the issuer property in the Verifiable credentials MUST identify an issuer that is known to and trusted by the verifier.
Having said that, the Verifiable Credentials Data Model does not provide the means nor the process to link the Issuerd digital presence to the offline world.

This paper aims to explore the processes that a verifier may follow to establish the identity of an Issuer of the presented credentials.

As a result, this paper won't define the processes that result in a verifier deciding that a particular credential is fit-for-purpose or acceptable for their needs.

## Verifier pain/desired benefits (maybe this can be a subparagraph of the problem solving)

- Reduce the risk associated with giving access to their services by building the required level of confidence/trust in the Subject (ultimately, the verifier wants to ensure not only the cryptographic authenticity of a credentals but also the authenticity of who stands behind the presented credential).
- One of the advantge of **provable identity** is about making transactions faster/service onboarding easier. e.g. user does not have to spend days/hours to collect proof over again as they can re-use them with multiple verifiers. With centralized systems today, the task of presenting proof, they do not leverage the fact the same User went through the process he/she did once already. **Provable identity** is introducing a new challenge with trusting the issuer. In a centrilized system you are the one directly asking for claims to the User and using your own resources/service providers to inspect them, the trust is implied. When moving to a Portable Identity system/credentials based system, you do not have that link based on personal experience. By introducing verifiable credentials we are disintermediating the verifier from the Issuer. 
- Easy and effective ways to establish the appropirate level of trust in the Issuer/presented credential required to build the confidence describe above. 
- Scalability: the ability to establish trust needs to work with the ecosystem growing from the initial early adopt stage; at the very beginning, trust in the Issuer will predominantly based on direct relationship between the Issuer and the Verifier (i know you in the real world, I trust you, )
- Liability: this is driven by multiple factors, such as Identity of the Issuer, level of Trust in the Issuer and quality of the credential issued (Level of Assurance of the credential, e.g. based on a given process, a given type of claims/proof etc..). 

## Background and Gaps

(picture)

When the Subject is holding the Credential:
- Issuers may issue Verifiable Credential to a Subject (**subject/issuer** pairwise relationship).
- Subject may present a Verifiable Credential to a verifier (**holder/verifier** pairwise relationship).
- the Verifier may or may not understand the true identity of the Verifier 
    - (what are the processes to originate the missing **verifer<->issuer** trust) 


## Processes
[mc] (We might want to include a section here which explain also the fact some of the approach we have a temporal scale, with some of the options being more suitable to theinitial stage, while others might be more suitable as the ecosystem mature). Include picture of time scale.

(in the following discussion, we use a notation to describe a verifiable credential name VCn issued by issuer I, for a subject S as VCn(I;S) )

As a verifier, when I first see a new issuer, I may...

1. check them on a list:
    A. see that the issuer is in a public registry ([BC VON](https://vonx.io)) 
    B. see that the issuer is in a commercial registry
    C. see that the issuer is in a p2p list

2. Use legacy registers

3. Use a “web of trust” of Verifiable Credentials issued by the group of issuers to each other

![](https://i.imgur.com/uCoIBEx.jpg)


### 1. Use a registry

Registry might be hosted by public or private entities.

Although these might face the same problems described at [Problems with the Public Key Infrastructure (PKI) for the World Wide Web](https://tools.ietf.org/html/draft-housley-web-pki-problems-02), a public registry can help verifiers start trusting credentials from issuers listed on that registry.

#### The Verifiable Organization Network (VON) example 

> The VON project is particularly focused on bootstrapping the trust attribute of the SSI approach for organizational entities. We aim to create a trusted digital network of verifiable data about organizations, which is globally connected, interoperable, secure, and easy to join. 
> 
> The challenge in creating an organizational SSI network is:
>
> - Supply: Services don’t supply verifiable credentials because there are no organizations with their own SSI digital wallets.
> - Demand: Organizations don’t have their own SSI digital wallets because there are no services that supply verifiable credentials.
 

The idea behind that approach is to bootstrap part of a SSI network by creating credential schemes, helping spinning up government-backed Issuers and providing VC and wallets, so that more and more Entities can start using them, thus driving a true bootsraping process.

While this approach is not focused on solving the verifier/issuer trust issue we are tackling, it indirectly does. 

It defines Authoritative Public Registries, which operate OrgBook instances:

>An OrgBook instance is an implementation of a verifiable credential registry, a “community digital wallet” holding verifiable credentials about entities registered in the operating jurisdiction. An OrgBook is used by VON issuer/verifier agents that request proofs of claims held by the OrgBook about entities and that issue verifiable credentials to the OrgBook instance. Each OrgBook instance is operated by an authoritative public registry, and all the verifiable credentials held are linked to those registered entities

![](https://i.imgur.com/vsaXgiN.jpg)

#### Import a list of trusted sources
Use a list of "trusted DIDs" from known source:

   - static list (one time import)
   - reference to DID doc w/ trusted DIDs embedded (may change over time)

### 2. Use legacy identity registers
This approach relies on existing internet registers which are used in everyday live. Currently, X.509 certificates are widely used in many internet protocols. For instance in TLS/SSL, this protocol provides the 'green lock' in your webbrowser. It creates a secure connection between the webserver and your browser. To create this trust, the browser relies on a set of root Certification Authorities (CA). Trust is built upon a chain of one root CA, multiple and possibly multiple layers of intermediate CA's and end-entities (users in the diagram below).

![](https://i.imgur.com/jfPBXzz.jpg)
[Image source](https://k-learn.adb.org/system/files/materials/2018/05/201805-self-sovereign-identity-converging-forces-challenges-and-opportunities.pdf) 

One could use the same PKI infrastructure for verifiable credentials. In the DID document one can include his X.509 public key and sign the verifiable credential with the corresponding private key. The verifier then respects the existing root for validating ownership of the keys. Possibly, it can select a subset of companies he/she wants to trust. He can do so, by retrieving the public keys of the webserver.


Issue to research: I think they expire, how to handle this when an expired one is in a did doc 


<!-- (trust resolver) inspects the DID document of the issuer to find and review legacy idendity information such as web-server's X.509 certificates for TLS, or x.509 certificate, etc. (respect existing root) -->



### 3. Use a "web of trust" of Verifiable Credentials issued by the group of issuers to each other
Verifier can use Verifiable Credentials issued by community/network of issuers to each other to estimate the level of trust it can provide to the Verifiable Credential provided by the issuer that is the part of the network of issuers - "web of trust". 
Verifier can use the following techniques to estimate the trust level it can extend to the issuer and the "web of trust" of issuers:
- estimate simplicity/explicitly of the relations in the "web of trust" of issuers
- estimate how simply and deeply it is possible to traverse/analyse "web of trust"
- find shortest path to well known global high-trust issuer in the "web of trust"
- find shortest path to local (contextual) high-trust issuer in the "web of trust"
- find, count and estimate quality of paths (path length, intermediary issuer, the quality of "connectors"/bottle necks) to the biggest component of the well known high level trust nodes
- find, count and estimate quality of paths (path length, intermediary nodes, the quality of "connectors"/bottle necks) to local (known to verifier to be trustable) high-trust "web of trust" 
- estimate the availability of rich data connected to "web of trust" - to check linkability of issuers to the "real world"
- use tools for manual/visual human-readable graph analysis (see image below)

![](https://i.imgur.com/fWoMLv0.png)
[Image source](https://k-learn.adb.org/system/files/materials/2018/05/201805-self-sovereign-identity-converging-forces-challenges-and-opportunities.pdf) 

## References

- https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/bootstrap_web-of-trust_reliance-lifecycle.md
- [Verifiable Credentials Data Model](https://w3c.github.io/vc-data-model/#trust-model)
- [The VON Orgbook](https://vonx.io/getting_started/orgbook/)
- https://ldapwiki.com/wiki/Trust
- [Verifiable Credentials Terminogy](https://w3c.github.io/vc-data-model/#terminology)
- [PGP Paradigm](https://github.com/WebOfTrustInfo/rwot1-sf/blob/master/topics-and-advance-readings/PGP-Paradigm.pdf)


## Authors

- Matt Stone, Brightlink, [@stonematt](https://github.com/stonematt)
- Michela Casaldi, , [LinkedIN](https://www.linkedin.com/in/michelacasaldi/)
- Shigeya Suzuki, Keio University
- Xavier Vila Pueyo, Validated ID, [@xvilapueyo](https://twitter.com/xvilapueyo)
- Bohdan Andriyiv, [@drabiv](https://twitter.com/Drabiv)
- David Lamers, [@dlamers](https://github.com/dlamers)