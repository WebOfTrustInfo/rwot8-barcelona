# Rebooting the Web of Trust VIII: Barcelona (March 2019)

This repository contains documents related to RWOT8, the eighth
Rebooting the Web of Trust design workshop, which will run in
Barcelona, Spain on March 1st to 3rd, 2019. The goal of the workshop
was to generate five technical white papers and/or proposals on topics
decided by the group that would have the greatest impact on the
future.

Visit http://rwot8.eventbrite.com for more information and to purchase tickets.

[Event details for attendees (schedule, hotels, transportation) (pdf 14MB)](https://nbviewer.jupyter.org/github/WebOfTrustInfo/website/blob/gh-pages/welcome-pack/rwot8-barcelona-welcome-pack.pdf)

##  Topics & Advance Readings

In advance of the design workshop, all participants produced a one-or-two page topic paper to be shared with the other attendees on either:

* A specific problem that they wanted to solve with a web-of-trust solution, and why current solutions (PGP or CA-based PKI) can't address the problem?
* A specific solution related to the web-of-trust that you'd like others to use or contribute to?

**NOTE:** To add a paper, create a pull request to this repo with your contribution (preferably .md file or PDF), along with updates to the README.md here and in the Topics and Advanced Readings folder with a link to your paper and your name. Please also include a byline with contact information in the paper itself.

Here are the advanced readings to date:

### Primers

These primers overview major topics which are likely to be discussed
at the design workshop. If you read nothing else, read these. (But
really, read as much as you can!)

* [DID Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-primer.md) — Decentralized Identifiers ([extended version](https://github.com/WebOfTrustInfo/rwot7-fall2018/blob/master/topics-and-advance-readings/did-primer-extended.md) also available)
* [Functional Identity Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/functional-identity-primer.md) — A different way to look at identity
* [Verifiable Credentials Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-credentials-primer.md) — the project formerly known as Verifiable Claims
* [Glossary of Terms](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/glossary-primer.md) — A terse lexicon of Web of Trust words

### Decentalized Identifiers (DID)
* [A DID for Every Thing: Driving Event Data Chain](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/A-DID-for-every-thing---Agile-Driving-Data-Chain.md)
  * by Carsten Stöcker and Michael Rüther
  * "Our broader objective is to establish a scalable digital twin protocol and a technology layer for autonomous things."
  * #verifiableclaims #reputation #IoT

* [Identity Manager Concept](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/idm-concept.md)
  * by André Cruz, João Santos, and Pedro Teixeira
  * The Identity Manager is a unified identity wallet that aims to support multiple DIDs and multiple DID-methods
  * #DID #VC #DID-Auth #apps #UI #UX #wallet
  * [Specification](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/idm-spec.md)

* [DID Namespace Records](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-namespace-records.md)
  * by Drummond Reed
  * "Besides discoverability of different decentralized networks, DID namespace linking also enables building bridges between different governance frameworks and trust assurance models—key building blocks of a global web of trust."
  * #reputation

* [Peer-to-peer DIDs](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/P2P-DID.md)
  * by Brent Zundel
  * "Work on a DID Method spec for P2P DIDs as a special subset of DIDs that are not universally resolvable on some ledger or central storage infrastructure, but only within the group where they are used."
  * #ledgerless
  * [Specification](https://github.com/brentzundel/peer-did-method-spec)

* [Proof of Key Ownership with OpenID Connect Self-Issued Identities](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/Proof_of_Key_Ownership_with_OpenID_Connect_Self-Issued_Identities.md)
  * by Michael B. Jones
  * "Proving ownership of a DID requires proving ownership of a private key corresponding to a public key for the DID.  Microsoft is experimenting with using OpenID Connect Self-Issued Identities to prove ownership of DIDs."
  * #OpenID #Connect #Self-Issued #DID

* [Universal ID Framework](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/universal-id-framework.md)
  * by Shigeya Suzuki
  * "One of the ways to support references for multiple ID scheme everywhere is developing a general Universal ID Reference scheme, which covers not only the references to DID but also Distinguish Name-based scheme or possibly others."
  * #PKI #interoperability

* [Identity Containers. Blockchain implementation proposal with DIDs & ERC725](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/identity-containers.md)
  * by Alex Puig
  * "Long story short, We suggest to store just a Merkle Root of the keys and claims being holded by an entity (user, organization..,) and set a list standard endpoints to query and interact between entities. This way most of the information is transferred off-chain and the whole system should be GDPR compliant."
  * #VC #ERC725 #DKPI #GDPR
  * [Full Proposal](https://gitlab.com/caelumlabs/sikaris)

* [Digital Trust Protocol](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/DigitalTrustProtocol.md)
  * by Carsten Keutmann and Tim Pastoor
  * "The Digital Trust Protocol (DTP) is a solution for the handling of trust in the digital space. The protocol is broadly designed to work with all aspects of trust; this includes identity, reputation, and security. The Protocol allows anyone, including software, to issue their own cryptographic identities, for the use of trust and reputation and be able to verify those of others, without the need for a trusted third party."
  * #VC #DPKI #reputation

* [Current Status of the DID Specification](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-spec-current-status.md)
  * by Amy Guy and Dmitri Zagidulin
  * A summary of open issues and discussion topics for moving the [DID Specification](https://w3c-ccg.github.io/did-spec/) forward.
  * #DID #W3C #CCG

* [Universal DID Operations](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Universal-DID-Operations.md)
  * by Markus Sabadello and Nader Helmy
  * "Interest in building blockchain-agnostic SSI solutions is increasing, so let's expand the concept of the Universal Resolver to more DID operations, like Create, Update and Revoke."
  * #DID #DPKI

* [Staying Anonymous With DIDs](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Anonymous_DIDs.md)
    * by David Stark
    * If we use DIDs and Verifiable Credentials how can we make sure that users are not being tracked across the web.

* [Decentralized Identity Fee Market](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-fee-market-using-micropayments.md)
    * by Yancy Ribbens
    * Micro-payments and DID (Decentralized Identities) can enable a user to curate their online identity, request payment or mark
data private. This article proposes allowing a fee market to develop around what information a user chooses to reveal about their identity in the context of verifiable credentials.

### General Self-Sovereign Identity
* [A Self-Sovereign Identity Framework/Thought Model proposal](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/SSI-FrameworkProposal.md)
  * by Rieks Joosten
  * "The SSIF provides a thought model and corresponding terminology that allows us to think in a precise manner about SSI within the context of its purpose(s) - which for us is the generic enablement of electronic support for (administrative) business transactions."
  * #commonlanguage
  * [Model](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/SSI-FrameworkProposal/SSI-FrameworkProposal.pdf)

* [Aligning SSI with European Union identity legislation (aka eIDAS Regulation)](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Aligning-SSI-with-European-Union-Identity-legislation-eIDAS.md)
  * by Nacho Alamillo and Santi Casas
  * "This paper aims to advance the alignment of SSI solutions with the eIDAS Regulation regarding electronic identification."
  * #DID #eIDAS
  
* [The Untimely Death of SSI](https://github.com/mxshea/rwot8-barcelona/blob/master/topics-and-advance-readings/the-untimely-death-of-ssi.md)
  * by Michael Shea
  * "This paper aims aims to provide a strategic analysis of the SSI space to identify the areas where additional focus is needed to prevent a mis-direction, hijacking or failure to reach a critical market presence."
  * #ssi #strategy
  
### Identity Philosophy
* [On Interpersonal Data](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/on-interpersonal-data.md)
  * by Philip Sheldrake
  * "It turns out that there is very few data that may be described as purely personal data. That lunch date, that genome map, those photos, that joint bank account — all turn out to be interpersonal data."
  * #data #reputation
* [Structures of Identity](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/structures_of_identity.pdf)
  * by Ethan Brown
  * Graphical explorations of current identity structures and alternatives.
  * #namespace

### Rights Frameworks
* [Legal Frameworks for Humanity in the Digital Age](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/rightsframeworks.md)
  * by Elizabeth M. Renieris
  * "We are allowing the tides of technology and commerce to haphazardly turn everything into commodifiable data. But will we allow ourselves to be reduced to data points and, worse yet, commodified? If we are not deliberate about designing the correct legal frameworks for humanity in the data-driven age, we risk losing sight of our fundamental rights as humans."
  * #data #rights

### Misc.
* [PSDAD - Data Format with Secure Semantics](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/psdad.md)
  * by Sandro Hawke
  * "Existing data serialization formats like JSON, JSON-LD, XML, and even ASN.1 (with its various encoding rules) work well enough for conventional computing environments, but they fall short when high levels of both trust and decentralization are required. PSDAD (plaintext self-describing assertional data) is a proposed new approach which uses natural language strings simultaneously as identifiers, delimiters, and documentation, resulting in a surprisingly simple and robust system with distinct advantages over known approaches in certain environments."
  * #data
  * [Specification](https://sandhawke.github.io/psdad/spec.html)

* [The Universal Ledger Agent: a Logical Result of Rabobank's Journey in Blockchain-based self-sovereign identity](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/universal-ledger-agent.md)
  * by David Lamers
  * "The universal ledger agent (ULA) is a component that is implemented by the app and the verifier. The ULA makes it possible to retrieve credentials from issuers, independently which standards and blockchain they use. Also, a verifier can accept and verify credentials from multiple standards."
  * #DID #VC #GDPR #ERC780

* [OIDC Profile for SSI](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/oidc-profile-for-ssi.md)
  * by Oliver Terbu and Andres Junge
  * "The goal is to continue the work on an OIDC profile for SSI based on [NS18] and [II18], and finalize the first version of it."
  * #VC

* [Introductory Capability DHT Concept](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/introductory-capability-dht-concept.md)
  * by James Foley
  * Considering the concept of a DHT for Introductory Capability Routing for object capability based decentralized applications.

* [Zero-knowledge proofs in identity systems](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Zero-knowledge-Proofs.md)

  * by Jordi Baylina and David Suarez
  * "Privacy is key to identity systems, and Zero-knowledge proofs (ZKP) are core to maintain confidentiality over user data, but still being able to transact by receiving claims and proving these to a third party."

* [GDPR and the right to erasure](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/RightToErasure.md)

  * by Oleg Burundukov and Eduardo Moraes de Morais
  * In accordance to GDPR law, an owner of data has the right to withdraw the initial consent and to request to erase the data. To execute this the owner has to hold an evidence of the interaction. The owner of digital data needs to obtain the digital proof of what and with whom the data have been disclosed.

* [Handshake](./topics-and-advance-readings/handshake.md)

  * by Boyma Fahnbulleh
  * Handshake is a decentralized, permissionless naming protocol compatible with DNS. The aim of the protocol is to replace the root zone file and the root servers with a public commons.


### Social Key Recovery
* [A New Approach to Social Key Recovery](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/social-key-recovery.md)
  * by Christopher Allen and Mark Friedenbach
  * "The goal of social key recovery is for the user to specify groups of individuals that together possess the ability to recover the root secret of a wallet."
  * #shamirsecretsharing #sss #keymanagement #masterseed #keyrecovery

* [Security Considerations of Shamir's Secret Sharing](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/security_shamirs.md)
  * by Peg
  * "Issues with private key management often pose barriers to the adoption of empowering decentralised technologies and this is exactly what this project aims to address. ...
  Threshold-based secret sharing schemes provide a powerful tool to address the private-key custody problem. There are promising solutions to the issues explored in this article. However, we have focussed here mainly on technical limitations of such schemes."
  * #reputation #shamirsecretsharing #keymanagement

* [Implementing of threshold schemes](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/implementing-threshold-schemes.md)
  * by Daan Sprenkels
  * "Shamir secret sharing is a method to split secrets into shares, and to later recombine them. However, it does not feature integrity protection of the secret.
  This article elaborates on Feldman VSS and Pederson VSS, which *do* protect the message integrity.
  Furthermore, we show how hashing the shares also protects the message integrity, but is vulnerable to a cheating dealer.
  * #shamirsecretsharing #keymanagement

### UX and Use Cases

* [Bringing the Dependencies of a BTCR Wallet to the Swift Ecosystem](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/bringing-dependencies-btcr-wallet-to-swift-ecosystem.md)
  * by Wolf McNally for Blockchain Commons
  * "While all the code to implement something as complex as a DID resolver or registrar could be written entirely in Swift, it makes sense to leverage code already written in other languages, and use Swift as a top-level language used to tie heterogenous modules into a unified application, whether it be a mobile application or server. This document surveys programing languages and technologies of interest, discusses issues of interoperating with Swift, and lists software packages of note."
  * #Swift #UX #iOS #DID

* [Digital Identity for the Homeless](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Digital-Identity-for-the-Homeless.md)
  * by Mike Varley and Matthew Wong
  * "The focus of this topic is how to apply existing decentralized digital ID solution to help individuals experiencing homelessness in the city (Toronto). E.g. how to reserve services such as overnight shelters with digital ID, keep track of certificate offered by free public organized re-training programs, and built credibility via repeat use the the same digital ID with varies services run by non-profit organizations in the city etc."
  * #reputation

* [Designing an Educational Credentialing Ecosystem](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/educational-credentialing-ecosystem.md)
  * by Kim Hamilton Duffy, J. Philipp Schmidt, and Joe Andrieu
  * "One goal of this exercise was to understand whether (1) certain emerging SSI standards -- including Verifiable Credentials (VCs), Decentralized Identifiers (DIDs) -- and (2) blockchain anchoring are essential to the simplified digital verifiable credentialing system. If so, we wanted to trace them to specific requirements.
  An additional goal was defining a threat model, to understand which aspects could be handled by the system, and which must be addressed by other systems. ...
  Our concern is that an effective digital credentialing ecosystem would make fraud within an issuing organization more appealing, so our final goal of this paper is to raise awareness among the broader SSI community."
  * #DID #VC

* [Assist underrepresented groups when entering the labour market through self sovereign identity](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/diverse-teams.md)
  * by Karolin Siebert
  * "As a consequence of increasing migration we have workers educated by a wild mix of educational systems, this should not be limiting them from approaching and receiving positions that they actually would like to work in and would be suitable for. Official diplomas and certificates, proving previous studies and work experience, are not necessarily recognised, available in physical form or easily translatable in a certified manner. In addition to that and estimate of the World Bank states that 1 Billion of people are without a formal identity. Being assigned one would give them better access to the work market since just their physical presence and knowledge is not enough in many cases, but rather we require proof for education and experience."
  * #DID #VC


* [Where's the UX?](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-ux.md)
  * by Alberto Elias
  * "I've been doing some user testing with both developers and non-technical folks and every single one of them has complained about the authentication and registration flows. We all agree that this work is for nothing if people don't end up using them. This community is definitely human-focused, but initial DID implementations haven't nailed the user experience yet."
  * #DID #VC #socialkeyrecovery

* [Designing Identity for People & Places](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/identity-for-people-places.md)
  * by Venn Agency - Sam Chase, Joni McKervey, and Benji Miller
  * "This paper will explore how we may architect a more complete individual sovereignty via privacy and place identity as a person moves between private and public physical locations (home, transit, work etc). ​ By mapping our rights and reasonable expectations to privacy across different contexts and comparing with the rights of devices in our spaces, we’ll seek to outline systems of access and control that work in accordance with the rights and needs of both sides."
  * #DID #IoT

* [Journalistic use-cases for SSI: signatures, verified claims, and canonical-text registries](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/journalistic-use-cases.md)
  * by Juan Caballero and Jefferson Sofarelli
  * "Our long-term proposal is to design an SSI-platform-agnostic DID widget or middle-ware system for CMSs such that at the time of committing a canonical version of a published piece on a given publication's CMS, that canonical version could be hashed and signed, with signature and hash being stored in an immutable, external record against which the signature could later be checked (i.e., making a verifiable claim of authorship linking the article's original published form to a DID controlled by its author)."
  * #DID #VC #reputation

* [Financing a Self-sovereign Technology Stack](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/financing-self-sovereign-stack.md)
  * by Adrian Gropper
  * Business models for autonomy through self-sovereign identity and self-sovereign technology are experimental. The standards are just starting to gel. Business structures for sustainable decentralized and potentially autonomous systems are still to be invented.
  * #agent #business

* [Designing Trust in Identity Systems](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Designing%20Trust%20in%20Identity%20Systems.md)
  * By Bentley Farrington & Bart Suichies
  * Putting the ID holder at the center of an identity system comes with great opportunity, but also introduces new risks and barriers to adoption. Many of these are non-technical and such, should be explored in multi-disciplanary way. We propose a human centered design approach to tackle some of these issues and help shift the focus to not just the technical feasibility, but also inclusive usability. This is a prerequisite to creating an identity system which combines technical and human trust elements.
  * #UX #trust #adoption #design

### Verifiable Claims (VC)
* [EU Digital Signature vs. VC Model](https://drive.google.com/file/d/1ehi0WMEJWNZV5Cx4wXsqPQC-wRcF4Zi2/view)
  * by L. Boldrin
  * To some extent a pdf signed document (or xml, json...) can be used to make trustworthy information about me available to a verifier. People ask: Why do we need VCs? What is the additional value they bring? This note provides an initial hyoothesis which I would like you to challenge: VCs without ledger provide, as added value, subject confirmation and anonymity/pseudonimity support. VCs with ledger provide, as a further value, just VC revocation."
  * #digitalsignature

* [How Do We Bootstrap the Web of Trust for VC](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/bootstrap_web-of-trust_reliance-lifecycle.md)
  * by Matt Stone and Dan Burnett
  * "In the world of Verifiable Credentials, it is essential that Verifiers can trust Issuers. To this end, there must be a common understanding of the 'functional identity' of the Issuer. How do humans establish the appropriate level understanding to trust the artifact with conviction? i.e. how does one link 'this key' to 'that real world entity (person, company, etc)'"
  * #DID #reputation
* [Multi-Factor Attribute Trust](https://github.com/wip-abramson/rwot8-barcelona/blob/master/topics-and-advance-readings/trusting-attributes.md)
  * By Will Abramson
  * "Developing flexible mechanisms for judging the trust of an attribute presentation is going to be essential to driving the network affects needed for widespread adoption of Verifiable Credential based identity networks."

* [Verifiable Claims for Postal Address](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-postal-address-claims.md)
  * by Moses MA
  * "This is a proposal to facilitate the collaborative drafting of a technical paper that describes the principles and key design considerations for a use case for verifiable physical address claims. Individuals within the global postal network now seek to understand the “decentralization revolution” and help to develop game-changing, blockchain-powered new business models for the world."

* [Using Immutable Data Objects](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Using-Immutable-Data-Objects.md) by Ken Ebert
  * by Ken Ebert
  * "Verifiable Credentials are strengthened by providing immutable data objects that
  provide a full definition of the data being signed.
  This is particularly true for objects with ZKP style signatures,
  where a more granular description of the data is required in order to support
  disclosure and predicate proofs on a per-property basis."
  * #VC #Schema #ZKP

### Specifications
* [Multiformat Superfriends (The Multibase, Multihash, and Hashlink Specifications)](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/multiformat-superfriends.md)
  * by Manu Sporny and Ganesh Annan

* [Current Status of the DID Specification](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-spec-current-status.md)
  * by Amy Guy and Dmitri Zagidulin
  * A summary of open issues and discussion topics for moving the [DID Specification](https://w3c-ccg.github.io/did-spec/) forward.
  * #DID #W3C #CCG

* [Identity Manager Specification](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/idm-spec.md)
  * by Adin Schmahmann, André Cruz, and Pedro Teixeira
  * A draft specification of the Identity Manager components, interfaces and protocols
  * #spec #DID #VC #DID-Auth #apps #wallet

* [Peer-to-peer DID Specification](https://github.com/brentzundel/peer-did-method-spec)
  * by Brent Zundel

* [PSDAD Specification](https://sandhawke.github.io/psdad/spec.html)
  * by Sandro Hawke

* [Verifiable Displays: secure presentation of Verifiable Credentials in HTML](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-displays-in-HTML.md)
  * by Bohdan Andriyiv
  * A rough outline of the specification for tamper-proofed, future-proofed, “anywhere renderable”, "truly portable" Verifiable Displays of Verifiable Credentials in HTML format.
  * #VerifiableDisplays, #VerifiableCredentials, #Hashlink, #HTML
