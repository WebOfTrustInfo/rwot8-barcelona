## A DID for every thing - Driving Event Data Chain

**Safer & better mobility through verifiable Driving Event Data Chains.**

Presented by Dr. Carsten Stöcker (Spherity GmbH), Dr. Michael Rüther  (Spherity GmbH)

Submitted to Rebooting Web of Trust 8

January 31, 2019, Düsseldorf, Germany

Keywords: decentralized identity, vehicle identity, digital twinning, cryptographically secured data chains, verifiable claims, blockchain, machine learning, agile driving, data chain provenance, audit trails, reputation system

## Inspiration

Driven by technology innovation and ecosystem growth mobility value chains are significantly changing from monolithic, closed to distributed, open systems.

Data flows are dynamically defined and stretch across multiple entities. The trustworthiness and accuracy of output data of a distributed mobility value chain is of increasing importance for the safety within a mobility system. This transformation requires new concepts of digital identity and trust for data transactions among non-human entities.

## Introduction - What our solution does

Our submission for RWoT submission describes an application of the previous RWoT whitepaper "A DID for Everything" [1] leveraging decentralized autonomic data (DAD) and verifiable data chains for driving event data processing. This enables the verification of a given data flow and the trustworthiness of output data. As the output data are used by several mobility control, risk and business systems it is important that any entity can evaluate the trustworthiness of a given output data set.

The decentralized identifier (DID) is a new open standard type of globally unique identifier that offers a model for lifetime scope, portable digital identity that does not depend on any centralized authority and that can never be taken away by third parties. We are using DIDs as a standard identifier in our solution which is supported by the W3C community.

Our approach uses cryptographic data structures to link data objects and to establish a method for data flow provenance [1]. By data flow provenance we mean a mechanism for tracing data item content and control through a processing system including any transformation to the data item. This includes flows with multiple sources, collective sensor fusion and processing by machine learning algorithms. Data flow provenance means not just tracing control but also verifying the end-to-end integrity of every data flow including any transformations (additions, deletions, modifications, combinations, and ML processing).

When a DID and hence data chain of the resultant data is extended to machines, the provenance chain of the data flow can provide the basis for verifiable claims and attestations about the data flow itself as well as for reputation mechanisms. These novel *verifiable data chains* and reputation mechanisms allow to asses trustworthiness, reliability or risk metrics of a given output of a data chain.

The applications of verifiable data chains stretch across multiple use cases including real-time vehicle value, dangerous driving, road and obstacle mapping, usage-based insurance (UBI), reliable feedback loops into driver assistance system (DAS) and autonomous driving infrastructures, V2V/V2I interactions and cooperative mobility systems.

Benefits of data provenance along a digitized value chain include:
-	reliability of data and ML labels in distributed systems
-	increased safety
-	maximized efficiency with less congestion, impact, costs and better services.

Our verifiable data chain concept supports the overall goal to demonstrate the working BC/DLT technology components can be used and scaled today for data provenance in digital value chains. 

## General Approach

### Decentralized identifiers (DIDs)

The resulting combinatorics of possible connections between any given set of entities in a mobility system is an impossibly large number. Yet in today's user journeys or business environments, agents (whether human, machine, or software) increasingly need to communicate, access or transact with a diverse group of these interconnected entities to achieve their goals. This requires an interoperable and ubiquitous method to address, verify and connect these elements together.

We propose to adopt the open decentralized identifier standard (DID) as an open, interoperable addressing standard and to establish mechanisms to resolve DIDs across multiple central or decentral mobility systems [2].

DIDs are the *atomic units* of a new layer of decentralized identity infrastructure. DIDs can be extended from identifiers of people, to any entity, thus to identify every thing. We use DIDs to help identify and manage data sets, objects, machines or software agents through their digital twins, to locations, to events, and even to pure data objects.

DIDs are derived from public private key pairs. We are using innovative cryptographic solutions for secure key management by fragmenting the private key of a DID that never exists in its entirety. Our key management solution is very effective for providing very secure signing transactions e.g. for smart phones, algorithms or data sets. An integration of the key management technology into embedded devices is on our technology roadmap.

A DID has the following required syntax:

`did:method:idstring`

We are using the Ethereum Blockchain and DID method *ethr* for our development work.

`did:ethr:0x5ed65343eda1c46566dff6774132830b2b821b35`

As our technology stack is blockchain agnostic any other DID method based on alternative blockchains can be integrated and used.

### Verifiable claims

DIDs are only the base layer of decentralized identity infrastructure. The next higher layer (where most of the value is unlocked), are verifiable claims [3,4]. This is the technical term for a digitally signed electronic data structure that conforms to the interoperability standards being developed by the W3C Verifiable Credentials Working Group.

Verifiable claims can be either self-issued by an entity such as a machine to provide a proof about authenticity and integrity of data or they can be issued by a third party (issuer, e.g. OEM, government, TÜV, service provider, bank).

In mobility systems any entity might want to transact with any other entity. This means entities are engaging with each other in a dynamically defined, on-demand way. It is not pre-defined which entities interact among each other. To ensure efficient transactions any new entity in a mobility value chain must be able to independently verify other counter parties.

To achieve this objective, we are using the DID approach and are anchoring the verifiable claims on a distributed ledger technology to move the *cryptographic root of trust* from central systems into a decentral, interoperable infrastructure.

### Digital twins that are verifiable

A digital twin is a digital representation of a biological entity (human, living organism, organization), a physical entity (objects, machines), a digital entity (digital asset, software agent) or any system formed of any combination of individual entities.

Digital twins can represent objects and entities as varied as a IoT sensors, ECUs, spare parts, vehicles, traffic lights, access gates, human users, or a city, and everything else in between. More recently they have started to be used to represent intangible entities like services, code, data, processes and knowledge. Digital twin data can consist of any life-cycle attributes and IoT sensor, telematics or compute data.

A verifiable digital twin is a digital twin with attributes that are represented by verifiable claims. These attributes such as a birth certificate, authentication proof, a calibration report or sensor data attestations can be independently verified by any third party.

This type of digital twin provides verifiable data about its creation, life-cycle, sensor readings, actuator commands or transactions. These verifiable data can be used for audit trails, decision making and for feedback loops in (autonomous) control systems.

### Verifiable driving event data chain

A data chain is a cryptographic data structure that chains signed data objects together and establishes a method for data flow provenance. Data flow provenance allows verifying the end-to-end integrity of every data flow object and its transformations (additions, deletions, modifications, combinations, and machine learning processing).

Processing of driving event data is operational in multiple mobility disciplines. Driving event data processing can include multiple data sources, parties, algorithms and processing steps. A human or non-human end-user of driving event data chains needs to be able to validate trustworthiness and accuracy of data chain output data. This requirement becomes of critical importance when the output data is used in safety or security relevant use cases or to make economic decision with significant commercial values involved.

For establishing a verifiable data chain, we link signed objects together. The following code snippet is a payload example with a machine learning label (red traffic light), information about the algorithm that created the label (Algorithm 1) and a link to the previous data chain block (previous block ID).

<pre><code>HEADER: PAYLOAD TOKEN TYPE & SIGNATURE ALGORITHM
{
"typ": "JWT",
"alg": "ES256K-R"
}
</code></pre>
<pre><code>PAYLOAD: DATA
{
  {
  "iat": 1546724123,
  "exp": 1546810523,
  "signer": {
    "type": "algorithm",
    "name": "Algorithm 1"
  },
  "data": {
    "claim": {
      "predictionLabel": "red traffic light, red traffic signal, stoplight",
      "predictionProb": "0.983483",
      "did": "did:ethr:0xe405b9ecb83582e4edc546ba27867ee6f46a940d"
    },
    "previousBlockId": "b86d95d0-1131-11e9-982e-51c29ca1f26e",
    "previousBlockHash": "307b817de9b7175db0ded0ea9576027efd64fb21"
  },
  "iss": "did:ethr:0x5ed65343eda1c46566dff6774132830b2b821b35"
}
</code></pre>

The data chain object can be verified by validating the signature of the payload. Cryptographic data chains enable users to validate the provenance of entire driving event data processing chains including the authenticity and integrity of the input data, the output data and the provenance of sensing devices and the processing algorithms.

We recommend to
-	establish verifiable data chains for driving event data processing,
-	provide a DID for every entity and data set,
-	integrate the data chains with DID registries (e.g. validated list of OEMs).

The verifiable digital twins are addressable by their DIDs and providing information about organizations, sensors telematics devices, data sets, external data sources, software algorithms and users involved in the data chain.

This approach is of particular value when validation or benchmarking data are available about the sensing devices, vehicles and the algorithms that are processing the driving event data. In combination with a reputation or validation system any user can calculate trustworthiness and accuracy metrics about the output data.

As a next step, reputation methods can be integrated for both, individual digital twins and entire data chains. Further standardization work on data chain trustworthiness and accuracy metrics need to be done.

### Design principles

For our digital twin and data chain integration work we are applying the following design principles:

|Principle |Description  |
|--------|--------|
|**From VINs to value chains** | Abstracting the *Concept of Identity* to a mobility system of vehicles, IoT, road & travel infrastructure, mobility systems, ML agents, driving event data set, autonomous driving/DAS feedback loops, markets and humans. Exchanging data among those entities. E2E data provenance along a value chain.|
|**Blockchain-agnostic**   |Use blockchain for anchoring attestations or verifiable claims. Decision on which blockchain to anchor claims based on user preferences or economic metrics such as Tx costs. Use of fiat-backed stable coins for micropayments.|
|**Scalable integration** |Integrated technology stack consisting of off-chain data structures, serverless cloud infrastructure, secure key management, DIDs, ML agents, sensor data, data chain fusion and blockchain connectors.|
|**Responsibility Segregation**| Implementation of this common pattern for micro services design that supports scalability and maintainability of our solution.|
|**Standards**|Use of existing W3C, Industry 4.0 and Automotive data standards and semantic models to ensure adaptability and portability of our solution.|
|**Business value**|Focusing on simple data integrity and authenticity problems within existing value chains. Retrofitting of existing infrastructures to scale adoption.|

### Agile driving event data chain for automotive use cases

Dangerous driving events can be divided into two groups: (1) the interaction between a driver’s vehicle and the road environment, and (2) the interaction between a driver’s vehicle and nearby vehicles [5].

Diverse methods for enhancing driving safety have been proposed. Such methods can be roughly classified as passive or active. Passive methods (e.g., seat-belts, airbags, and anti-lock braking systems), which have significantly reduced traffic fatalities, were originally introduced to diminish the degree of injury from an accident. By contrast, active methods are designed to prevent accidents from occurring. Driver assistance systems (DAS) are designed to alert the driver - or an autonomous driving module - as quickly as possible to a potentially dangerous situation.

The two classes of driving events may occur simultaneously and lead to certain serious traffic situations. Automotive industry is working on active methods and systems including machine learning algorithms to analyze these two kinds of events and determine *dangerous situations* from data collected by various sensors and data from external sources. The machine learning output labels about dangerous curves, road obstacles or poor vehicle conditions are fed into control, transaction and risk systems. In distributed mobility systems the trustworthiness and accuracy of the output labels must be independently verifiable.

> Key question: How can I trust vehicle identity data, 3rd party data and machine learning labels that are created and processed along a distributed mobility value chain?

To achieve trustworthiness of output labels we are planning to blend our verifiable data chain technology with historic driving event data and black box algorithms to build a verifiable agile driving solution:
-	Interoperable decentral identity and verifiable digital twinning protocol
-	Cryptographically secured and blockchain-enabled data chains
-	E2E integration of remote sensing (telematics) data and machine learning algorithms

Our approach demonstrates how the following **trust** problems can be addressed with DLT:
-	Vehicle provenance and configuration
-	Provenance, verifiability and integrity of the driving event input data (or telematics data)
-	Integrity and transparency of driving event data chain when multiple 3rd party intermediaries are involved
-	Credentials about benchmarking of ML algorithms and training data
-	Aggregated accuracy and trustworthiness of predicted ML labels and attributes

## Challenges we ran into

Over the course of the implementation of our verifiable data chain we ran into the following challenges:
1.	Providing DID identity to individual data sets and algorithms
2.	No reference implementations for verifiable data chains
3.	No common semantic standards for automotive digital twin
4.	Lack of validated source code for scalable issuing and anchoring of verifiable claims (>100.000 Tx/s)
5.	Getting access to sensible OEM agile driving data and real algorithms
6.	Lack of E2E driving event data models and architectures (location, transport, events, processing)

We solved (1.) and (2.) with our data chain implementation. We researched W3C vehicle signalling standards and semantic web as well industry 4.0 standards to address (3.).

We are testing the *sidetree protocol* on IPFS that might lead to a solution for (4.). We are planning to benchmark the protocol in the next weeks.

We are planning to work with an OEM on (5.).

Data model implementation patterns need to be created in order to enable effective implementation of cyber physical systems (CPS). This is a general task to be done regardless of the use of DLT technology. To address (6.) we are working with the German Centre of Artificial Intelligence (DFKI) on a CPS integration methodology, a data modelling methodology and reusable data model implementation patterns for verifiable data chains.

## Accomplishments that we are proud of

We accomplished the development of verifiable data chains including the following technology components:
-	DID manager
-	Secure key management
-	HD identity wallet
-	Verifiable claims
-	Deployment on severless cloud functions on AWS
-	Integration of tensor flow algorithms for image processing
-	Implementation of corporate requirements for vault/wallet policies

We are now planning to integrate historic agile driving data and a black box algorithm with our existing data chain solution on Amazon Web Services. We are planning to demonstarte our solution on RWoT 8.

## What we learned

Our primary leanings are around the following areas of interest:
-	Abstraction of the DID method to any object
-	Identity solutions for machine learning agents
-	Scalability of off-chain data structures
-	Integration of serverless cloud infrastructure with key management and identity wallets
-	Verifiability of data chains
-	Applicability of data chains for above mentioned data-driven business solutions

## What's next: our broader objective

Our broader objective is to establish a scalable digital twin protocol and a technology layer for *autonomous things*. We call these digital twins *autonomous digital twins that are verifiable, semantic and privacy-preserving*.

We are integrating further W3C and Industry 4.0 standards to establish a semantic digital twin network. Our work integrates further innovation in cryptography and privacy-preserving solutions to achieve GDPR compliance for both, the human and non-human entities.

We are looking forward to field test our solution in a complete mobility ecosystem.

### Addendum - Key Management in accordance to Corporate Requirements

We just integrated our Corporate Wallet solution for managing private keys of the entities involved in the drivint event data chain demo.

Key management is done via vaults. Vault policies are defined in accordance to compliance requirements of an enterprise. We are using the following set-up for identities and vaults:

**Account**: Entities that require identity(-ies). Accounts are spaces where identities can be managed. An account can be created for human, legal entity, machine or any other physical or virtual object. Inside of accounts, we work with: Participants, Vaults and Sub-Identities. Sub-Identities are represented by wallets (key-pairs) and managed inside vaults.

**Participant**: Participant devices can be created within a particular account. After requesting participant creation, it needs to be activated on a dedicated iOS device or with a cloud software agents (embedded devices to be supported later), to further trace operations from vaults of the corresponding account where participant was specified as a quorum member, so that it can provide approvals for pending operations. In the essence, participant’s device, holds the secret that gives it a possibility to manipulate wallets that exist inside connected Vaults.

**Vault**: Vaults are managed identity groups. Vaults group a single or multiple wallets, and define quorum policies for managing them. At the time of vault creation, there is a need to specify the list of participants that will have a right to approve operations on behalf of wallets identities that can be generated within.

**Sub-identity/Persona/Wallet**: Each vault can have multiple wallets which are sub-identities (or personas) for of vault group or account holder. As an example, let’s consider that some wallet identity is being used to sign some data in order to build a verifiable claim. In this case, after the signing process will start, participants that correspond to a respective vault, will be notified about a pending operation. And after gathering the required number of approvals, the operation will be processed.

**Vault Quorum Policy**: Vault’s Quorum Policy is a rule set. Vault’s Quorum Policy is being defined at vault creation time. It describes the list of participants who participate in a quorum and the number of required approvals that need to be collected from all vault’s participants for progressing a operation (signing or joining a vault).

In case you are interested in the above, we would be happy to demonstrate the integration of vaults with legal entities, identity/device management and digital twinning for machine twins at RWoT 8.

## References

[1][ A DID for Everything - Rebooting Web of Trust Working Draft](http://https:// github.com/WebOfTrustInfo/rwot7/blob/master/draft-documents/ A_DID_for_everything.md)
[2][ W3C DID Specification](https://w3c-ccg.github.io/did-spec/)
[3][ W3C Verifiable Claims](https://www.w3.org/2017/vc/WG/)
[4][ Decentral Identity Foundation](https://identity.foundation)
[5][ Dangerous Driving Event Analysis System by a Cascaded Fuzzy Reasoning Petri Net](https://www.researchgate.net/publication/
224650669_Dangerous_Driving_Event_Analysis_System_by_a_Cascaded_Fuzzy_Reas oning_Petri_Net)
