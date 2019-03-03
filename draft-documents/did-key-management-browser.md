By Alberto Elias, André Cruz and João Santos

# Outline
- [Outline](#outline)
- [Abstract](#abstract)
  - [Introduction](#introduction)
  - [Glossary](#glossary)
  - [Key Storage](#key-storage)
    - [Storage](#storage)
      - [Vault](#vault)
      - [Keychain](#keychain)
      - [Shared Storage](#shared-storage)
      - [Cache](#cache)
    - [Keys](#keys)
      - [Master Key](#master-key)
      - [Device Key](#device-key)
      - [Session Key](#session-key)
  - [Multi-Device](#multi-device)
    - [Replication](#replication)
    - [Concurrent Updates](#concurrent-updates)
  - [Authentication](#authentication)
    - [Pairwise DIDs](#pairwise-dids)
  - [Frequent DID actions](#frequent-did-actions)
  - [Key Recovery](#key-recovery)
  - [Multiple Identities](#multiple-identities)
  - [User Experience](#user-experience)
  - [Web APIs](#web-apis)
    - [WebAuthn](#webauthn)
  - [Specific DID Methods](#specific-did-methods)
  - [Threats](#threats)
    - [Stolen Device](#stolen-device)
    - [MITM](#mitm)
    - [Web Extensions](#web-extensions)
    - [3rd Party Libraries](#3rd-party-libraries)
  
# Abstract

There are many projects implementing DIDs, and different DID methods, in many different ways. This paper examines the specific requirements for the Web and browsers. The Web has a different security model than native platforms (e.g. mobile apps) and even, limited access to native device capabilities (e.g secure cryptoprocessor chips). We explore these limitations and how they apply to DID key management including, but not limited to, authentication, signing, key storage, key recovery, synchronization across multiple devices and user experience.

## Introduction

DIDs are highly dependant on asymmetric cryptographic keys. We use these keys to prove ownership of a DID and to do different actions from that identity. If we lose them, we lose control of our identity. There are many ways to mitigate these risks with different key recovery methods, using proxy keys or actual key management on a device. Key management on the browser has different limitations for secure key management.

## Glossary

Cryptographic Keys:

Master Key:

Device Key:

Session Key: 

Vault:

Keychain:

Cache:

Device Secret:

Shared Secret:

Web Extension:

Lock: 


## Key Storage

Storing keys in the browser has a specific limitation native applications don't have: you can't hide anything. Storage is only limited by the origin, but many things can access that storage like 3rd party libraries, a web extension or a physical person with device access. That forces us to encrypt all stored data, but whatever you use to encrypt/decrypt (passphrase, finger print, iris scanner…) can't be stored on the device. We end up with the person having to introduce the encryption lock, but prompting for that lock would mean a bad user experience. Here we examine a possible solution which attempts to balance user experience with security.

We propose 4 storage blobs: vault, keychain, shared storage and cache; 3 types of keys: master key, device key and session key; and 2 types of secrets: device secret and shared secret.


### Storage

We store different elements related to the identity like keys tied to the identity, encryption secrets, verifiable credentials or the DID Document. Depending on its use and importance, we will require different storage options: vault, keychain, shared storage and cache.


#### Vault

There is one vault per device. The vault is only unlocked using different locks provided by the person. These could be, but not limited to: passphrase, finger print, iris scan, behaviour biometrics etc. The vaults sole purpose is to store the _Device Secret_ (more below), which is used to encrypt everything else that is stored on the device. If there is information stored regarding multiple identities, they will all be encrypted by the same _Device Secret_ stored in the single Vault.

When entering a DID Key Management app for the first time on a device, the Vault is the first thing that is created. All other storage options MUST use the _Device Secret_ to encrypt their data.


#### Keychain

There is one keychain per identity. They keychain stores the _Device Key_ and _Shared Key_ for each identity.


#### Shared Storage

Information like Verifiable Credentials that must be in sync between all devices that control an identity are added to the **Shared Storage**. Information is encrypted with the _Shared Secret_ before being encrypted with the _Device Secret_.


#### Cache

Information like the DID Document or a public profile will be accessed frequently, and resolving it could add a significant lag to the experience. Non-critical and public information will be added to the cache.


### Keys


#### Master Key

There is 1 _Master Key _per identity. This is generated when an identity is created. Some DID methods may differ, but generally, we can abstract it to one key. The_ **Master Key**_ SHOULD be stored in the Vault until the DID is fully created in case of a problem and the identity creation process needs to be restarted. Once the DID has been created, the **Master Key** MUST be deleted, though the person MUST have some way of backing it up before (e.g. saving a seed phrase, using a service).


#### Device Key

There is a _Device Key_ per device per identity. All specific actions with the identity on a specific device is done with the _Device Key_.

They can only be revoked using the **Master Key**. 

Even if a device gets stolen, the robber won't be able to use most features without unlocking the Device Private Key as all the information stored locally will be encrypted with the Device Public Key.


#### Session Key

There is a **Session Key **per application per device per identity. When an application does DID Auth with the Key Manager, it creates a **Session Key** so the application can sign on behalf of the person without needing to prompt constantly. 

They are revoked using the **Device Key**.


## Multi-Device

Once an Identity has been imported to a new device, the new device will need to receive the _Share Key_ via some transport (LibP2P, Secure Web Sockets, Bluetooth, NFC, QR Code...). 

Any meaningful event on the Key Manager, such as the removal of an identity or the addition of a Verifiable Credential, will be broadcasted to interested parties. This allows applications to immediately react to certain events by subscribing to them on the Key Manager.


### Replication


### Concurrent Updates


## Authentication

The session is composed of a key-pair _Session Key_ where the public key is known by both, serving as the session identifier, while the private key is only known by Key Manager. Additionally, all sessions have a max-age, meaning they expire as time passes.


### Pairwise DIDs


## Frequent DID actions

An identity is constantly interacting with other identities, them being people or devices or organizations. They exchange Verifiable Credentials, capabilities and other varied types of messages. As these interactions occur constantly, we expect them to happen seamlessly for people for a good user experience. For DIDs, most of these interactions depend on signing information. Based on our proposal, this is done via the _Session Key _or the _Device Key_.

(Details tradeoffs)

A less common action is updating a DID Document, which we should also evaluate.


## Key Recovery

This is specific to each DID method and has no implications to the browser model apart from the issues mentioned in Key Storage.


## Multiple Identities


## User Experience

None of this work makes sense if people don't actually use our identity systems. That's why we prioritise user experience and make it a strict limitation when analyzing different options and tradeoffs. 


## Web APIs


### WebAuthn

The emergence of web libraries designed to deal with storage and access control to keys that can be used for strong authentication purpose, such as WebAuthN can be leveraged to manage access control to the Vault. Features such as biometric authentication (by a fingerprint reader) ensure a good user experience, but can be a single point of failure (e.g. the user's finger/fingerprint reader might get damaged).


## Specific DID Methods

Different DID methods have different limitations. Some depend entirely on the concept of a _Master Key_, others have a proxy setup with the actual controller of an identity (e.g. a smart contract like ERC 725). A feature which appears to be comons across all DID methods is that at any point in time, there is a certain secret key which gives the party in its control the capability do act on behalf of that identity. Thus, a possible strategy to offer a DID agnostic platform is to use the the Vault to provide access to these secrets. For example, in the case of IPID, the vault would store the RSA or ed25519 key which gives access to the IPID DID Document, while in the case of ERC725 the vault would store an ECDSA private key (which could then be used to generate the public key, and Ethereum address).


## Threats


### Stolen Device


### MITM


### Web Extensions


### 3rd Party Libraries

Resources:


*   [https://github.com/digitalbazaar/crypto-ld](https://github.com/digitalbazaar/crypto-ld) 
    *   A Javascript library for cryptographic operations using Linked Data
*   <span style="text-decoration:underline;">🌟 [https://github.com/digitalbazaar/web-credential-handler](https://github.com/digitalbazaar/web-credential-handler)</span>
*   [https://github.com/digitalbazaar/did-cli](https://github.com/digitalbazaar/did-cli) 
    *   Did-cli for the VEres-one ledger
*   [https://w3c.github.io/web-ledger/](https://w3c.github.io/web-ledger/) 
    *   A format and protocol for decentralized ledgers on the Web
*   [https://github.com/digitalbazaar/authorization.io](https://github.com/digitalbazaar/authorization.io) 
    *   A Credential Handler is an event handler for credential request and credential storage events. The [Credential Handler API](https://w3c-ccg.github.io/credential-handler-api)helps solve the [Nascar Problem](https://indieweb.org/NASCAR_problem). The [Credential Handler API](https://w3c-ccg.github.io/credential-handler-api) enables websites to install Credential Handlers that can respond when users visit other websites that request or store credentials.
*   🌟 **[https://github.com/digitalbazaar/did-io](https://github.com/digitalbazaar/did-io) **
    *   **A [DID](https://w3c-ccg.github.io/did-spec/) (Decentralized Identifier) resolution library for Javascript**
*   [https://github.com/digitalbazaar/web-ledger-cli](https://github.com/digitalbazaar/web-ledger-cli) 