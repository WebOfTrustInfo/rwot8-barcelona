# Identity Manager Concept

*Authors*: André Cruz, João Santos, Pedro Teixeira

- [Introduction](#introduction)
- [Research: standards & foundations](#research-standards--foundations)
  - [Decentralized Identifiers](#decentralized-identifiers)
  - [Verifiable Credentials](#verifiable-credentials)
  - [Using DID-Auth to prove control of the DID](#using-did-auth-to-prove-control-of-the-did)
- [IDM - Identity Manager](#idm---identity-manager)
  - [Preface](#preface)
  - [IDM Wallet](#idm-wallet)
  - [IDM Wallet UI](#idm-wallet-ui)
  - [IDM Client](#idm-client)
  - [IDM Bridge](#idm-bridge)

## Introduction

The benefits of using P2P technologies, which enable truly decentralized applications to exist, are obvious to those well versed in the topic. However, in order to attain massive user adoption, these decentralized applications need to be better than the incumbents in almost every aspect -- usability being the one where they usually lack the most.

Most of the cryptographic identity solutions out there rely on a single key pair where the public key identifies a single identity. While simple, this solution has many drawbacks, the most important one being that you can't recover your identity if the private key gets compromised. To explore potential solutions, the IPFS [DDC WG](https://github.com/ipfs/dynamic-data-and-capabilities) decided to invest some time researching what decentralized identity solutions may be used. This paper is a follow-up of [RFC Peer-Star-Identity](https://github.com/ipfs-shipyard/peer-star/blob/rfc-identity/docs/rfc-identity.md).

## Research: standards & foundations

### Decentralized Identifiers

Decentralized Identifiers (DIDs) are a new type of identifier for verifiable, "self-sovereign" digital identity. DIDs are fully under the control of the DID subject, independent from any centralized registry, identity provider, or certificate authority.

A DID always identifies a person, organization or thing. They have a specific syntax: `<scheme>:<method>:<method-identifier>` (e.g. `did:ipid:a1B2c3d4E5`).

DIDs resolve to DID-Documents — simple documents that describe how to use that specific DID. Each DID-Document contains at least three things: Cryptographic Material, Authentication Suites and Service Endpoints. Cryptographic Material combined with Authentication Suites provide a set of mechanisms to authenticate as the DID subject (e.g. public keys, pseudonymous biometric protocols, etc.). Service Endpoints enable trusted interactions with the DID subject.

In the real world, people may use different devices to interact with others. Each of those should have their public keys listed in the DID-Document, making it possible to add and remove them as needed while keeping the same DID.

#### Granular permissions & authentication

As previously stated, people use different devices in their daily lives. Each of those devices have different security guarantees. As an example, a device in your home is less likely to be lost or stolen when compared to a mobile phone. On the other hand, a mobile phone may have its storage encrypted which is more secure than an unencrypted one. Having that said, the level of permissions should be considered when adding a new device.

Moreover, if a device is going to be used for authentication, its public key should be listed in the `authentication` field of the DID-Document. This is necessary for `DID-Auth` or other authentication mechanisms to assert that the device is valid for authentication.

### Verifiable Credentials

Verifiable Credentials is a format for interoperable, cryptographically-verifiable digital credentials. DIDs begin by being "trustless" in the sense that they don't directly provide meaningful identity attributes. But trust between DID-identified peers can be built up through the exchange of verifiable credentials - credentials about identity attributes that include cryptographic proof. These proofs can be verified by reference to the issuer's DID and DID-Document.

Because the ecosystem is still in its infancy and there's a lack of trusted issuers, identities may self-issue credentials. More specifically, they may issue credentials that define personal attributes about themselves, like their name and birthdate, and credentials that prove they own certain profiles on social networks, similar to how [Keybase](https://keybase.io) does. As of today, many people trust the mainstream social networks, such as Facebook and Twitter, and identities may use them to post cryptographic proofs that link their profiles to a hash of their DID. As time passes by and the ecosystem gets mature, identities will hold credentials issued by others that may be used in a variety of scenarios and purposes.

### Using DID-Auth to prove control of the DID

DID-Auth is an handshake ceremony where an entity proves control over an identity to a relying party.

In an authentication scenario between an user and an application, the application may want to ensure that the entity is in control of the DID it presented. Similarly, the user being authenticated may also check if the application's DID is in the application's control. Another typical scenario is when an entity requests access to some private data and the holder of the data needs check if that entity is in control of the identity's DID before handing the key to decrypt that data. In both scenarios, verifiable credentials may be exchanged so that the credibility of those identities may be evaluated during the handshake.

## IDM - Identity Manager

### Preface

While DID's, Verifiable Credentials and DID-Auth provide interoperable models for common use-cases, the reality is that current identity wallets are closed in their own DID-method ecosystems.

On one hand, applications wanting to embrace identities using different DID-methods have to integrate with different identity wallets, such as `uPort` and `blockstack`. These wallets have SDKs with different APIs, increasing integration complexity and crippling adoption.
On the other hand, users are asked to authenticate using specific DID-methods because the application they are interacting with is limited by the DID-methods they support. Moreover, and often as a consequence, users are required to use multiple wallets to manage different identities they own. As an example, an user that owns its persona's DID and its company's DID must use different wallets in case they were created using different DID-methods.

The Identity Manager is a unified identity wallet that aims to support multiple DIDs and multiple DID-methods, where:

- Users create and import identities from different DID-methods
- Users manage the verifiable credentials of the identities they have, with an initial focus on self-issued credentials
- Users manage the list of devices for each identity, providing the ability to revoke a compromised device
- Users manage the list of applications they have interacted with, providing the ability to revoke an application
- All the identities' data, such as its verifiable credentials, devices list and applications list, is stored encrypted
- The same identities' data is replicated across wallets to be kept in sync
- Interactions between identities and applications, such as authenticating, signing and verification of signatures, are mediated by the wallet
- Components, interfaces and protocols are detailed and explained in an open specification, allowing anyone to implement their own IDM

From a higher-level perspective, the Identity Manager - or IDM for short - is composed of four components: IDM Wallet, IDM Wallet UI, IDM Client and IDM Bridge:

<img src="https://raw.githubusercontent.com/ipfs-shipyard/pm-idm/master/docs/images/diagram_components-overview.png" alt="">

### IDM Wallet

The IDM Wallet is similar to the physical wallet you carry everyday. It contains all the digital identities of its holder and all the information attached to them in a secure and encrypted way.

Note that the IDM Wallet is an headless component, meaning it has no graphical user interface. Anyone wanting to build such GUIs, may choose from a variety of SDKs written in different programming languages, all based on the [IDM Wallet spec](idm-spec.md#idm-wallet). More information about the IDM Wallet UI can be found later on this document.

There will be a reference IDM Wallet written in JavaScript, suitable to use inside a browser.

#### Locker

The IDM Wallet will have a locking mechanism to protect its access. A variety of locking types may be used to unlock the wallet, such as a passphrase, pattern, typeid, fingerprint, faceid, and other biometric validators. The locker holds a single secret that will be encrypted for each locking type. That single secret will be used to encrypt and decrypt all the data that lives inside the wallet.

#### Managing identities

Users will be able to create identities using their preferred DID-method or import existing ones. They will be guided throughout the process in the UI according to the chosen DID-method.

The outcome of the creation of an identity will be a new DID, a Master Key Pair and a Device Key Pair where their correspondent public keys are listed in the DID-Document. The Master Private Key is in complete control of the DID-Document and should be used as little as possible. For that reason, it should be stored outside the IDM Wallet in a secure and recoverable way. One of those ways is via a Paper Key, where the Master Private Key is printed using machine readable representations, such as a QR code. [Shamir's Secret Sharing](https://en.wikipedia.org/wiki/Shamir%27s_Secret_Sharing) may also be used to split the Master Private Key into different secrets that can be shared with trustees, like family and close friends. Even if the Paper Key is lost, users may recover their Master Private Key by collecting those secrets from them.
For the import case, a Device Key Pair will be created and its public key added to the DID-Document as well. Depending on the DID-method, the Master Private Key might be needed to update the DID-Document.

Some DID-methods might support granular permissions. This enables users to grant a specific set of permissions to different devices based on how secure the device is and how likely it is to be lost or robbed.

#### Managing verifiable credentials

Users will be able to view, add and remove Verifiable Credentials to and from their wallet. As we previously explained in the [Verifiable Credentials](#verifiable-credentials) section, the IDM Wallet will initially focus on self-issued credentials and expand to credentials issued by others when the ecosystem gets mature.

Depending on the identities' DID-methods and their capabilities, where and how the credentials are stored might be pre-defined by the DID-method and may be either off-chain or on-chain. As an example, [EIP780](https://github.com/ethereum/EIPs/issues/780) proposes an on-chain registry for Ethereum based identities to store credentials, enabling persons, smart contracts, and machines to issue credentials about each other. The IDM Wallet will employ best-practices for each DID-method when storing credentials.

#### Authentication on applications

Most applications need to know the identity of the user so that they can provide a customized experience.

Applications may start an authentication process, issuing an authentication request to an IDM Wallet, containing the application DID and Verifiable Credentials with its details, such as the application name, and the credentials it wants to receive from an identity. The IDM Wallet will perform DID-Auth to ensure that the application is in control of the DID it presented. If successful, the user is then prompted to select an identity and to accept what the application is asking for.

If the user accepted the prompt, a new session is created and will be used for any further interactions between that application and that IDM Wallet. The session is composed of a key-pair where the public key is known by both, serving as the session identifier, while the private key is only known by that IDM Wallet. Additionally, all sessions have a max-age, meaning they expire as time passes.

#### Signing artifacts on applications

Applications may want to sign artifacts, such as regular data or ephemeral keys. This will be possible in two different ways:

- Sign with the Session Private Key
- Sign with the Device Private Key

The first method is less intrusive and happens transparently to the user, but is also less secure. More specifically, a robber who steals an IDM Wallet may still sign artifacts with the Session Private Key as long as a session is valid because that key is stored unencrypted. Verifiers will still see those signatures as valid until the DID owner revokes the stolen device.

The second method is more secure as the user is prompted to unlock IDM to decrypt the Device Private Key, but it is more intrusive. The interaction is similar to the authentication process, where the user is prompted inside the IDM Wallet to sign. Because the Device Private Key is encrypted, this gives the DID owner plenty of time to revoke that key in another IDM Wallet.

Ultimately, the application may choose between both methods for different situations depending on the security degree they want to have.

#### Verifying signatures

Any party might verify the authenticity and authorship of artifacts signed by others.

- The verification of an artifact signed by the Session Public Key is performed by:
    1. Verifying the signature of the artifact against the Session Public Key of the author.
    2. Verifying the signature of the Session Public Key against the Device Public Key of the author. This proves that the Session Public Key was authorized by the Device Private Key.
    3. Verifying if the Device Public Key of the author is present in the DID-Document associated with the DID. This proves that the Device Public Key was authorized by the author's identity.
    4. If Device Public Key is flagged as revoked, compare its revocation effective date with the signature date


- The verification of an artifact signed by the Device Public Key is performed by:
    1. Verifying the signature of the artifact against the Device Public Key of the author.
    2. Verifying if the Device Public Key of the author is present in the DID-Document associated with the DID. This proves that the Device Public Key was authorized by the Identity (author).
    3. If Device Public Key is flagged as revoked, compare its revocation effective date with the signature date

#### Managing application sessions

Users will be able to revoke one or all application sessions from within the identity's applications list. After revoking a session, the application will no longer be able to use that session, effectively stopping it from being able to perform operations that require the Session and Device Private Keys.

#### Revoking a device

Users must be able to revoke a device associated with an identity. To do so, the DID-Document needs to be updated in order to signal that the Device Public Key was revoked, including the effective date which is important when verifying signatures.

Depending on the DID-method and the permissions of the Device Private Key, higher level keys or other processes might be necessary to update the DID-Document, such as using the Master Private Key.

The way a public key is declared as revoked is [yet to be standardized](https://github.com/w3c-ccg/did-spec/issues/96) in the DID spec. Nevertheless, a DID-Document may be augmented via the `@context` attribute to support having that information.

#### Replication and synchronization

The same identity might be held inside different IDM Wallets. For that reason, the identities' data, such as its credentials and applications, will be seamlessly replicated to other IDM Wallets using P2P technologies powered by [CRDTs](https://en.wikipedia.org/wiki/Conflict-free_replicated_data_type).

Any data stored off-chain or on-chain as per the DID-method best-practices will be taken into consideration, meaning they will be synchronized accordingly.

### IDM Wallet UI

End users need a graphical user-interface to interact with their IDM Wallet. An IDM Wallet UI is an application that will make use of the most suitable IDM Wallet SDK for the programming language they choose.

Even though anyone can implement its own IDM Wallet UI application, there is a need to define some standards in regards to user journeys, user experience and interactions. For that reason, there will be a reference IDM Wallet UI based on web-technologies to be used inside a browser, that can be packed as an [Electron](https://electronjs.org/) in the future.

#### Reference UI diagrams

User-journeys diagram:

<img src="https://raw.githubusercontent.com/ipfs-shipyard/pm-idm/master/docs/images/diagram_user-journeys.png" alt="" width="1000">

Information Architecture diagram:

<img src="https://raw.githubusercontent.com/ipfs-shipyard/pm-idm/master/docs/images/diagram_information-architecture.png" alt="" width="1000">

#### Reference UI concept

The goal of the reference UI is to have a really polished interface with a premium feel. It must be easy to use, distinct, reliable, accessible and provide a feel of credibility to the users.

<img src="https://raw.githubusercontent.com/ipfs-shipyard/pm-idm/master/docs/images/ui-concept_setup-locker.png" alt="" width="1000">
<img src="https://raw.githubusercontent.com/ipfs-shipyard/pm-idm/master/docs/images/ui-concept_homepage.png" alt="" width="1000">
<img src="https://raw.githubusercontent.com/ipfs-shipyard/pm-idm/master/docs/images/ui-concept_profile-page.png" alt="" width="1000">

### IDM Client

Applications need to interact with the IDM Wallet. This process will be facilitated by the IDM Client, which will be available as multiple SDKs for different programming languages. Each SDK will provide a simple and intuitive interface based on the [IDM Client Spec](idm-spec.md#idm-client) and contain means to authenticate, unauthenticate, sign, verify signatures, amongst others.

There will be a reference IDM Client written in JavaScript, suitable to use inside a browser.

### IDM Bridge

While applications use the IDM Client to interact with an IDM Wallet, the way they reach each other and communicate is handled by the IDM Bridge. Applications run on a variety of contexts, from within browsers to native applications. An IDM Wallet might coexist in the same context as these applications or, more often, in different contexts and even equipments. Below there's a list of possible scenarios and respective solutions:

1. Both an Application and an IDM Wallet running on the same browser, on the same equipment:
	- Solution: Use an iframe and the [postMessage API](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage)
2. An Application running on a browser and an IDM Wallet running as a native OS application, on the same equipment
	- Solution: The IDM Wallet exposes a local [WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API) server on a pre-defined port known by the IDM Client
3. Both the Application and IDM Wallet are native OS applications, running on the same equipment
	- Solution: Use inter-process communication, preferring mechanisms offered by the OS
4. An Application running on a laptop and an IDM Wallet running on a smartphone
    - Solution: Use IPFS's pubsub to find and talk to each other

Conceptually, the IDM Bridge is composed by two parts: the provider-side and the consumer-side. The provider-side is embedded in the IDM Wallet while the consumer-side is embedded in the IDM Client. Each one of the sides have a set of transports that they support to communicate.

Moreover, the IDM Client has a discovery mechanism that finds the most appropriate IDM Wallet to talk to, starting by locating one closer to its own context that also supports one of its transports. For reference, there are various degrees of closeness, from closest to the furthest: exactly the same context (e.g.: within same browser), same machine, same network or different network. The discovery is likely to be more transparent and automatic if both sides are close to each other. For example, in scenario `2`, the IDM Client can try to initiate a WebSocket connection to `localhost:<predefined-port>` to check if there's a IDM Wallet running there. On the contrary, the further both sides are, the less automatic the process is and might require users to mediate the process by scanning QR-codes, inputting numbers, or other mechanisms.

Messages are exchanged from the IDM Client to the IDM Wallet and vice-versa through the IDM Bridge. Those messages will be defined as part of the [IDM Bridge spec](idm-spec.md#idm-bridge) to ensure the interoperability between different implementations.

There will be a reference IDM Bridge written in JavaScript with the goal to solve scenario `1` by leveraging the [postMessage API](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) to create a communication channel between IDM Clients and a IDM Wallet running on a pre-defined domain.
