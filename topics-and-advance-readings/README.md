If you will be attending Rebooting the Web of Trust Spring 2019 in Barcelona, Spain, please upload your topic papers and advanced readings to this directory with a pull request (or, if you don't know how, post an issue).

_Please see the [Web of Trust Info website](http://www.weboftrust.info/) for more information about our community. Go to [Eventbrite](https://www.eventbrite.com/e/rebooting-the-web-of-trust-viii-spring-2019-barcelona-tickets-54843077120) to register for this event._

##  Topics & Advance Readings

In advance of the design workshop, all participants produced a one-or-two page topic paper to be shared with the other attendees on either:

* A specific problem that they wanted to solve with a web-of-trust solution, and why current solutions (PGP or CA-based PKI) can't address the problem?
* A specific solution related to the web-of-trust that you'd like others to use or contribute to?

**NOTE:** To add a paper, create a pull request to this repo with your contribution (preferably .md file or PDF), along with updates to the README.md in this folder and at the top of the repo with a link to your paper and your name. Please also include a byline with contact information in the paper itself.

### Topical Listing

#### Primers

These primers overview major topics which are likely to be discussed
at the design workshop. If you read nothing else, read these. (But
really, read as much as you can!)

* [DID Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-primer.md) — Decentralized Identifiers ([extended version](https://github.com/WebOfTrustInfo/rwot7-fall2018/blob/master/topics-and-advance-readings/did-primer-extended.md) also available)
* [Functional Identity Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/functional-identity-primer.md) — A different way to look at identity
* [Verifiable Credentials Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-credentials-primer.md) — the project formerly known as Verifiable Claims
* [Glossary of Terms](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/glossary-primer.md) — A terse lexicon of Web of Trust words


#### Decentalized Identifiers (DID)
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

* [Proof of Key Ownership with OpenID Connect Self-Issued Identities](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Proof_of_Key_Ownership_with_OpenID_Connect_Self-Issued_Identities.md)
  * by Michael B. Jones
  * "Proving ownership of a DID requires proving ownership of a private key corresponding to a public key for the DID.  Microsoft is experimenting with using OpenID Connect Self-Issued Identities to prove ownership of DIDs."
  * #OpenID #Connect #Self-Issued #DID

* [Querying Bitcoin blockchain for BTCR support](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/supporting-btcr.md)
  * by Kulpreet Singh
  * "I describe the progress made during the BTCR hackathon towards providing a community service for querying the bitcoin blockchain as a means to support clients building BTCR DID resolvers using the BTCR DID method."

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

* [Re-inventing Incentive Structures Using DID and Microtransactions](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-fee-market-using-micropayments.md)
    * by Yancy Ribbens
    * Microtransactions and DID (Decentralized Identifiers) can enable a user to curate their online identity, request payment or mark
data private. This article proposes allowing a fee market to develop around what information a user chooses to reveal about their identity in the context of an earned credential.

* [W3C Strong Authentication and Identity Workshop Report (DRAFT)](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/w3c-identity-workshop-report.md)
    * by The W3C Strong Authentication and Identity Workshop Program Committee and Participants
    * A draft report from the W3C Strong Authentication and Identity Workshop
noting the topics covered during the workshop as well as the outcomes and next
steps identified by the workshop participants.

#### General Self-Sovereign Identity
* [A Self-Sovereign Identity Framework/Thought Model proposal](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/SSI-FrameworkProposal.md)
  * by Rieks Joosten
  * "The SSIF provides a thought model and corresponding terminology that allows us to think in a precise manner about SSI within the context of its purpose(s) - which for us is the generic enablement of electronic support for (administrative) business transactions."
  * #commonlanguage
  * [Model](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/SSI-FrameworkProposal/SSI-FrameworkProposal.pdf)

* [Aligning SSI with European Union identity legislation (aka eIDAS Regulation)](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Aligning-SSI-with-European-Union-Identity-legislation-eIDAS.md)
  * by Nacho Alamillo and Santi Casas
  * "This paper aims to advance the alignment of SSI solutions with the eIDAS Regulation regarding electronic identification."
  * #DID #eIDAS

* [Decentralized Digital Identity: The Book](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/decentralized-digital-identity-book.md)
  * by Alex Preukschat and Drummond Reed
  * Outline for a book on decentralized digital identity

* [A Notebook Workbench for SSI](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/notebook-workbench.md)
  * by Eric Welton
  * "The technical cost of experimenting with and evaluating web-of-trust technology, SSI and other, remains bewilderingly high. This situation hinders broad adoption."

* [The Untimely Death of SSI](https://github.com/mxshea/rwot8-barcelona/blob/master/topics-and-advance-readings/the-untimely-death-of-ssi.md)
  * by Michael Shea
  * "This paper aims aims to provide a strategic analysis of the SSI space to identify the areas where additional focus is needed to prevent a mis-direction, hijacking or failure to reach a critical market presence."
  * #ssi #strategy

#### Sybil Resistance
* [Attention as a Source of Scarcity for Decentralized Identity Systems](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Attention%20as%20a%20Source%20of%20Scarcity%20for%20Decentralized%20Identity%20Systems.pdf)
  * by Maciej Laskus
  * This paper proposes a new approach to introducing scarcity into identity systems without sacrificing privacy and self-sovereignty.
The method relies on quantifying attention flows between identities. It is predicated on the fact that attention is a basic element of all cognitive processes. It is also limited and therefore is a natural source of scarcity.
  * #Sybil-resistance #scarcity #attention

#### Graph analysis
* [Humanity's API - solving Fermi paradox](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/humanity-API.md)
  * by Bohdan Andriyiv
  * Explaining existence of Fermi paradox due to the humanity's lack of advanced cooperation technologies that enable optimal cooperation on the global scale. Positing a hypothesis that when humanity has such technology it will enable us to contact and to be contacted by interstellar civilizations.
  * #Fermi_paradox, #hypothesis, #graph_analysis, #humanity

* [I see graphs everywhere. On the importance of graphs and graph analysis way of thinking.](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/graphs-everywhere.md)
  * by Bohdan Andriyiv
  * A call to look at identity and other RWOT problem space through the graph analysis lenses
  * #graphs, #graph_analysis #short_topic_paper_to_open_discussion

* [Why webs of trust work, even the PGP one?](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/why-WOTs-work.md)
  * by Bohdan Andriyiv
  * Challenging widespread notion that Webs of Trust do not work. They work. They just need customization as per their purposes and environments.
  * #Web_of_Trust, #PGP, #graph_analysis, #short_topic_paper_to_open_discussion

* [Higher-Definition Digital Identity] (https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/higher-definition-identity.md)
 * Shaun Conway
 * Introducing the idea of stateful identity graphs to increase the resolution and fidelity of verifiable credentials.
 * #graphs #merkle_dag #information_theory #personal_data #short_topic_paper_to_open_discussion

#### Identity Philosophy
* [Digital Contraception](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/digital-contraception.md)
  * by Mitzi László
  * "The question of personal data falls into an unknown territory in between corporate ownership, intellectual property, and slavery."
* [On Interpersonal Data](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/on-interpersonal-data.md)
  * by Philip Sheldrake
  * "It turns out that there is very few data that may be described as purely personal data. That lunch date, that genome map, those photos, that joint bank account — all turn out to be interpersonal data."
  * #data #reputation
* Structures of Identity [PDF](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/structures_of_identity.pdf) [MD](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/structures_of_identity.md)
  * by Ethan Brown
  * Graphical explorations of current identity structures and alternatives.
  * #namespace
* [Contextual Non-Discrete Identity](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/contextual_nondiscrete_identity.md)
  * by Siu Kei Chung
  * Philosphical exploration of non-discrete identities based on context of application.
  * #context #data #relative

#### Rights Frameworks
* [Legal Frameworks for Humanity in the Digital Age](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/rightsframeworks.md)
  * by Elizabeth M. Renieris
  * "We are allowing the tides of technology and commerce to haphazardly turn everything into commodifiable data. But will we allow ourselves to be reduced to data points and, worse yet, commodified? If we are not deliberate about designing the correct legal frameworks for humanity in the data-driven age, we risk losing sight of our fundamental rights as humans."
  * #data #rights

#### Misc.

* [Credentials and Correlation](./topics-and-advance-readings/credentials-and-correlation.md)
  * by Jack Poole
  * How can users be educated of the privacy implications of sharing multiple attributes about one’s identity, and what role can software agents have?

* [Data Value Realisation: Control, Commons & Ownership](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/data-vala-realization.md)
  * by Katryna Dow
  * "Since data is becoming a key measure of whether a company will remain relevant through the digital revolution (Opher et. al., 2016), new approaches and business models are required to meet the needs of the changing marketplace (Opher et. al., 2016). To address these increasing data value issues, a number of data-value models and frameworks are emerging, including: Data as Labor; Data as Property; Data Commons; and Open Data. This paper explores the aforementioned frameworks in the context of the emerging human-centred data economy."

* [Decentralized Trust for Software Components](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/code-and-file-signing.adoc)
  * by Sean Gilligan
  * "A computing device cannot be secure if an attacker is able to surreptitiously insert malicious code on it. Current solutions for signing and verifying computer software — both source code and binaries — generally rely on the same flawed, hierarchical systems as our network connections do."

* [GDPR and the right to erasure](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/RightToErasure.md)
  * by Oleg Burundukov and Eduardo Moraes de Morais
  * In accordance to GDPR law, an owner of data has the right to withdraw the initial consent and to request to erase the data. To execute this the owner has to hold an evidence of the interaction. The owner of digital data needs to obtain the digital proof of what and with whom the data have been disclosed.

* [Handshake](./topics-and-advance-readings/handshake.md)
  * by Boyma Fahnbulleh
  * Handshake is a decentralized, permissionless naming protocol compatible with DNS. The aim of the protocol is to replace the root zone file and the root servers with a public commons.

* [Introductory Capability DHT Concept](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/introductory-capability-dht-concept.md)
  * by James Foley
  * Considering the concept of a DHT for Introductory Capability Routing for object capability based decentralized applications.

* [Is the Universe a blockchain?  A cryptographic model of the Universe. ](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/universe-is-blockchain.md)
  * by Bohdan Andriyiv
  * Exploring analogies between blockchain and the universe.
  * #crackpotting, #fun_with_physics

* [OIDC Profile for SSI](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/oidc-profile-for-ssi.md)
  * by Oliver Terbu and Andres Junge
  * "The goal is to continue the work on an OIDC profile for SSI based on [NS18] and [II18], and finalize the first version of it."
  * #VC

* [PSDAD - Data Format with Secure Semantics](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/psdad.md)
  * by Sandro Hawke
  * "Existing data serialization formats like JSON, JSON-LD, XML, and even ASN.1 (with its various encoding rules) work well enough for conventional computing environments, but they fall short when high levels of both trust and decentralization are required. PSDAD (plaintext self-describing assertional data) is a proposed new approach which uses natural language strings simultaneously as identifiers, delimiters, and documentation, resulting in a surprisingly simple and robust system with distinct advantages over known approaches in certain environments."
  * #data
  * [Specification](https://sandhawke.github.io/psdad/spec.html)

* [Rethinking Priorities: Should Identity Systems Divide or Unite People?](https://bford.info/2019/02/08/identity/)
  * by Bryan Ford
  * "The problem of identity has become a hot topic, with the idea of self-sovereign identity in particular attracting significant excitement. The essence of the idea, in short, is to put users in charge of how their identities and personal data are used. Self-sovereign identity posits that users should decide how much and what aspects of their identities to disclose in any situation, and should know and have control over what that information is used for."

* [RWOT local chapters](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/RWOT-local-chapters.md)
  * by Bohdan Andriyiv
  * Exploring the need for local RWOT-like face to face meetings.
  * #local_communities, face_to_face_meetings, #short_topic_paper_to_open_discussion

* [The United Humans - can it really work?](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/united-humans-critiqal-questions.md)
  * by Bohdan Andriyiv
  * Positing a list of critical questions to the central points of The United Humans project.
  * #critique, #short_topic_paper_to_open_discussion

* [The Universal Ledger Agent: a Logical Result of Rabobank's Journey in Blockchain-based self-sovereign identity](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/universal-ledger-agent.md)
  * by David Lamers
  * "The universal ledger agent (ULA) is a component that is implemented by the app and the verifier. The ULA makes it possible to retrieve credentials from issuers, independently which standards and blockchain they use. Also, a verifier can accept and verify credentials from multiple standards."
  * #DID #VC #GDPR #ERC780

* [Zero-knowledge proofs in identity systems](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Zero-knowledge-Proofs.md)
  * by Jordi Baylina and David Suarez
  * "Privacy is key to identity systems, and Zero-knowledge proofs (ZKP) are core to maintain confidentiality over user data, but still being able to transact by receiving claims and proving these to a third party."


#### Social Key Recovery
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

* [Social Key Recovery Design and Implementation](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Socia_%20Key_Recovery_design_implentation.md)
  * by Hank Chiu, Hankuan Yu, Justin Lin & Jon Tsai
  * "Social Key Recovery aims to provide an alternative and interesting way to help user backup their cryptocurrency mnemonic phrase. Currently user needs manually to write down all his mnemonic phrase on a piece of paper and locks it in a safe, which is troublesome to user. To solve user’s pain in backup, Social Key Recovery tries to propose a social way to help user backup their mnemonic phrase."
  * #shamirsecretsharing #sss #keymanagement #keyrecovery

* [SLIP-0039: Shamir's Secret-Sharing for Mnemonic Codes](https://github.com/satoshilabs/slips/blob/master/slip-0039.md)
  * by The TREZOR Team
  * A new standard for cryptocurrency wallets allowing users to split their BIP-32 master seed into multiple shares using Shamir's secret sharing scheme in an inter-operable manner.

* [Joram 2.0.0](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/joram.2.0.0.md) by Joe Andrieu and Bob Clint

#### UX and Use Cases

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

* [Generating Actionable Intelligence with Wallets and Agents for People & Places](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/identity-for-people-places.md)
  * by Venn Agency - Sam Chase, Joni McKervey
  * "The purpose of this paper is to discuss building in the principals of sovereign identity systems
for places as well as people to better manage multiple stakeholders and layers of access, while
preserving both the saliency of digital information and the individual privacy and protections of
the physical world."
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

* [Applying POLA to User Interaction](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Applying_POLA_to_User_Interaction.md)
  * By Bill Tulloh
  * Object capabilities (ocaps) are increasingly recognized as an important tool for achieving the goals of self-sovereign identity. Many of the principles of self-sovereign identity, such as minimization and protection, can best be achieved through the disciplined pursuit of the principle of least authority that ocaps enable. This paper examines how POLA can be extended to better protect users when exercising their self-sovereign identity.
  * #UX #Ocaps

* [Joram 2.0.0](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/joram.2.0.0.md)
  * By Joe Andrieu and Bob Clint
  * Joram is a Syrian refugee who has found his way to Greece. We describe in simple prose his experience through the 15 stages of the Information Lifecyce Enagement Model. This update to Joram 1.0.0 includes stronger authentication and social key recovery. 

* [Providing Decentralized Identity to the most vulnerable populations](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Providing_Decentralized_Identity_to_the_most_vulnerable_populations.md)
  * By Jeremi Joslin, Greg Martel and Hailey Park
  * A Decentralized Identity stored on a smart card is used to provide a digital identity to people in the least developed areas of the planet.
  * #humanitarian #SDG

* [#SSI20XX - Model Use-Case Definitions and Implementation](./topics-and-advance-readings/ssi20XX-model-use-case-def.md)
  * by Martin Riedel
  * "This paper proposes that a vision statement (for example #SSI20XX) containing a very limited set of highly specified use-cases and UX descriptions will allow solution providers to commit to a common implementation goal which can greatly benefit solution interoperability and provide valuable feedback to existing specifications in the field of SSI."
  * #use-cases #interoperability #implementation #vision

#### Verifiable Claims (VC)
* [EU Digital Signature vs. VC Model](https://drive.google.com/file/d/1ehi0WMEJWNZV5Cx4wXsqPQC-wRcF4Zi2/view)
  * by L. Boldrin
  * To some extent a pdf signed document (or xml, json...) can be used to make trustworthy information about me available to a verifier. People ask: Why do we need VCs? What is the additional value they bring? This note provides an initial hyoothesis which I would like you to challenge: VCs without ledger provide, as added value, subject confirmation and anonymity/pseudonimity support. VCs with ledger provide, as a further value, just VC revocation."
  * #digitalsignature

* [Exploring adoptation of VC sharing to provide value today](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/exploring_adoption_of_sharing_vcs.md)
  * by Snorre Lothar von Gohren Edwin
  * "With Verifiable Credentials it is important to ask the question what are we expecting the issuer, the holder, and / or the verifier to do? While still making it simple enough for all the users and keeping the needed level of trustworthiness. Sharing is what provides the end value for both the verifying and the sharing party. If there is no sharing, the issuance of the VC has gone to waste. Hence if we are to provide value for the sharing party today, we have to ask the questions of where is this adopted, how can we make this adoption effortless? Can we put most of the work on the service providers? Is the user or another service expected to install software? If so, install software where? Is that software domain-specific or integrated with some existing software?"

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

* [Verifiable Displays: secure presentation of Verifiable Credentials in HTML](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-displays-in-HTML.md)
  * by Bohdan Andriyiv
  * A rough outline of the specification for tamper-proofed, future-proofed, “anywhere renderable”, "truly portable" Verifiable Displays of Verifiable Credentials in HTML format.
  * #VerifiableDisplays, #VerifiableCredentials, #Hashlink, #HTML

* [Using Immutable Data Objects](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Using-Immutable-Data-Objects.md) by Ken Ebert
  * by Ken Ebert
  * "Verifiable Credentials are strengthened by providing immutable data objects that
  provide a full definition of the data being signed.
  This is particularly true for objects with ZKP style signatures,
  where a more granular description of the data is required in order to support
  disclosure and predicate proofs on a per-property basis."
  * #VC #Schema #ZKP

* [W3C Strong Authentication and Identity Workshop Report (DRAFT)](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/w3c-identity-workshop-report.md)
    * by The W3C Strong Authentication and Identity Workshop Program Committee and Participants
    * A draft report from the W3C Strong Authentication and Identity Workshop
noting the topics covered during the workshop as well as the outcomes and next
steps identified by the workshop participants.

* [Minimal implementation of verifiable credentials for a community of practice use case on an agent-centric distributed platform](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/vcs-agent-centric.md)
  * by Jakub Lanc
  * We experiment with a minimal Verifiable Credentials-like system implementation on a distributed agent-centric platform (Holochain), explore its suitability for use cases related to distributed communities of practice and discuss the specifics of such use cases.
  * #VC #Agent-centric #Education

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

* [libp2p for DID Authentication and the exchange of Verifiable Credentials](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/libp2p_did_auth..md)
  * by jonnycrunch
  * "In our last paper we presented how IPLD could be used as a generalized framework to repesent and resolve the DID document. In this paper, we will describe a way to perform DID authenication and thereby proove ownership of the private key that is presented in the DID document utilizing the libp2p protocol."
  * #DID Auth #libp2p #ipfs #ipid #verifiableclaims
  
### Alphabetical Listing

* [Aligning SSI with European Union identity legislation (aka eIDAS Regulation)](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Aligning-SSI-with-European-Union-Identity-legislation-eIDAS.md) by Nacho Alamillo and Santi Casas
* [Applying POLA to User Interaction](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Applying_POLA_to_User_Interaction.md) by Bill Tulloh
* [Assist underrepresented groups when entering the labour market through self sovereign identity](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/diverse-teams.md) by Karolin Siebert
* [Bringing the Dependencies of a BTCR Wallet to the Swift Ecosystem](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/bringing-dependencies-btcr-wallet-to-swift-ecosystem.md) by Wolf McNally for Blockchain Commons
* [Contextual Non-discrete Identity](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/contextual_nondiscrete_identity.md) by Siu Kei Chung
* [Current Status of the DID Specification](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-spec-current-status.md) by Amy Guy and Dmitri Zagidulin
* [Credentials and Correlation](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/credentials-and-correlation.md) by Jack Poole
* [Data Value Realisation: Control, Commons & Ownership](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/data-vala-realization.md) by Katryna Dow
* [Decentralized Digital Identity: The Book](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/decentralized-digital-identity-book.md) by Alex Preukschat and Drummond Reed
* [Decentralized Identity Fee Market](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-fee-market-using-micropayments.md) by Yancy Ribbens
* [Decentralized Trust for Software Components](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/code-and-file-signing.adoc) by Sean Gilligan
* [Designing an Educational Credentialing Ecosystem](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/educational-credentialing-ecosystem.md) by Kim Hamilton Duffy, J. Philipp Schmidt, and Joe Andrieu
* [Designing Identity for People & Places](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/identity-for-people-places.md) by Venn Agency - Sam Chase, Joni McKervey, Benji Miller
* [Designing Trust in Identity Systems](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Designing%20Trust%20in%20Identity%20Systems.md) by Bentley Farrington & Bart Suichies
* [A DID for Every Thing: Driving Event Data Chain](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/A-DID-for-every-thing---Agile-Driving-Data-Chain) by Carsten Stöcker and Michael Rüther
* [DID Namespace Records](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-namespace-records.md) by Drummond Reed
* [Digital Contraception](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/digital-contraception.md) by Mitzi László
* [Digital Trust Protocol](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/DigitalTrustProtocol.md) by Carsten Keutmann and Tim Pastoor
* [Exploring adoptation of VC sharing to provide value today](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/exploring_adoption_of_sharing_vcs.md) by Snorre Lothar von Gohren Edwin
* [Financing a Self-sovereign Technology Stack](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/financing-self-sovereign-stack.md) by Adrian Gropper
* [GDPR and the right to erasure](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/RightToErasure.md) by Oleg Burundukov and Eduardo Moraes de Morais
* [Handshake](./handshake.md) by Boyma Fahnbulleh
* [How Do We Bootstrap the Web of Trust for VC](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/bootstrap_web-of-trust_reliance-lifecycle.md) by Matt Stone and Dan Burnett
* [Humanity's API - solving Fermi paradox](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/humanity-API.md) by Bohdan Andriyiv
* [Identity Containers. Blockchain implementation proposal with DIDs & ERC725](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/identity-containers.md) by Alex Puig
* [Identity Manager Concept](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/idm-concept.md) by André Cruz and João Santos
* [Identity Manager Specification](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/idm-spec.md) by Adin Schmahmann, André Cruz and Pedro Teixeira
* [Implementing threshold schemes](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/implementing-threshold-schemes.md) by Daan Sprenkels
* [Introductory Capability DHT Concept](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/introductory-capability-dht-concept.md) by James Foley
* [I see graphs everywhere. On the importance of graphs and graph analysis way of thinking.](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/graphs-everywhere.md) by Bohdan Andriyiv
* [Is the Universe a blockchain?  A cryptographic model of the Universe. ](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/universe-is-blockchain.md) by Bohdan Andriyiv
* [Joram 2.0.0](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/joram.2.0.0.md) by Joe Andrieu and Bob Clint
* [Journalistic Use Cases for SSI](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/journalistic-use-cases.md) by Juan Caballero & Jefferson Sofarelli
* [Legal Frameworks for Humanity in the Digital Age](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/rightsframeworks.md) by Elizabeth M. Renieris
* [libp2p for DID Authentication and the exchange of Verifiable Credentials](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/libp2p_did_auth..md) by jonnycrunch
* [Minimal implementation of verifiable credentials for a community of practice use case on an agent-centric distributed platform](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/vcs-agent-centric.md) by Jakub Lanc  
* [Multi-Factor Attribute Trust](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/trusting-attributes.md) by Will Abramson
* [Multiformat Superfriends](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/multiformat-superfriends.md) by Manu Sporny and Ganesh Annan
* [A New Approach to Social Key Recovery](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/social-key-recovery.md) by Christopher Allen & Mark Friedenbach
* [A Notebook Workbench for SSI](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/notebook-workbench.md) by Eric Welton
* [OIDC Profile for SSI](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/oidc-profile-for-ssi.md) by Oliver Terbu, Andres Junge
* [On Interpersonal Data](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/on-personal-data.md) by Philip Sheldrake
* [Peer-star Identity Manager](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/IdentityManager.md) by André Cruz & João Santos, Pedro Teixeira
* [Peer-to-peer DIDs](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/P2P-DID.md) by Brent Zundel
* [Proof of Key Ownership with OpenID Connect Self-Issued Identities](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Proof_of_Key_Ownership_with_OpenID_Connect_Self-Issued_Identities.md) by Michael B. Jones
* [PSDAD - Data Format with Secure Semantics](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/psdad.md) by Sandro Hawke
* [Querying Bitcoin blockchain for BTCR support](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/supporting-btcr.md) by Kulpreet Singh
* [Rethinking Priorities: Should Identity Systems Divide or Unite People?](https://bford.info/2019/02/08/identity/) by Bryan Ford
* [RWOT local chapters](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/RWOT-local-chapters.md) by Bohdan Andriyiv
* [Security Considerations of Shamir's Secret Sharing](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/security_shamirs.md) by Peg
* [A Self-Sovereign Identity Framework/Thought Model proposal](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/SSI-FrameworkProposal.md) by Rieks Joosten
* [Social Key Recovery Design and Implementation](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Socia_%20Key_Recovery_design_implentation.md) by Hank Chiu, Hankuan Yu, Justin Lin & Jon Tsai
* [Staying Anonymous With DIDs](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Anonymous_DIDs.md) by David Stark
* Structures of Identity [PDF](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/structures_of_identity.pdf) [MD](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/structures_of_identity.md) by Ethan Brown
* [Universal DID Operations](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Universal-DID-Operations.md) by Markus Sabadello and Nader Helmy
* [Universal ID Framework](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/universal-id-framework.md) by Shigeya Suzuki
* [Digital Identity for the Homeless](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Digital-Identity-for-the-Homeless.md) by Mike Varley and Matthew Wong
* [The Universal Ledger Agent: a Logical Result of Rabobank's Journey in Blockchain-based self-sovereign identity](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/universal-ledger-agent.md) by David Lamers
* [The United Humans - can it really work?](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/united-humans-critiqal-questions.md) by Bohdan Andriyiv
* [The Untimely Death of SSI](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/the-untimely-death-of-ssi.md) by Michael Shea
* [Using Immutable Data Objects](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Using-Immutable-Data-Objects.md) by Ken Ebert
* [Verifiable Claims for Postal Addresses](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-postal-address-claims.md) by Moses MA
* [Verifiable Displays: secure presentation of Verifiable Credentials in HTML](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-displays-in-HTML.md) by Bohdan Andriyiv
* [W3C Strong Authentication and Identity Workshop Report (DRAFT)](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/w3c-identity-workshop-report.md) by The W3C Strong Authentication and Identity Workshop Program Committee and Participants
* [Where's the UX?](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-ux.md) by Alberto Elias
* [Why webs of trust work, even the PGP one?](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/why-WOTs-work.md) by Bohdan Andriyiv
* [Zero-knowledge proofs in identity systems](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Zero-knowledge-Proofs.md) by Jordi Baylina and David Suarez
* [Can Name Services provide Persistent Human-meaningful Names Linked To A Self Sovereign Identity DID Without Compromising SSI?](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/name-services-and-ssi.md) by Toby Tremayne and Ryan Gill


### Primers

These primers overview major topics which are likely to be discussed
at the design workshop. If you read nothing else, read these. (But
really, read as much as you can!)

* [DID Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-primer.md) — Decentralized Identifiers ([extended version](https://github.com/WebOfTrustInfo/rwot7-fall2018/blob/master/topics-and-advance-readings/did-primer-extended.md) also available)
* [Functional Identity Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/functional-identity-primer.md) — A different way to look at identity
* [Verifiable Credentials Primer](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-credentials-primer.md) — The project formerly known as Verifiable Claims
* [Glossary of Terms](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/glossary-primer.md) — A terse lexicon of Web of Trust words
