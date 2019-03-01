# DID Key Management in the Browser

By Alberto Elias, André Cruz, Joao Santos and Marton Csernai

## Abstract

There are many projects implementing DIDs, and different DID methods, in many different ways. This paper examines the specific requirements for the Web and browsers. The Web has a different security model than native platforms (e.g. mobile apps) and even, limited access to native device capabilities (e.g secure cryptoprocessor chips). We explore these limitations and how they apply to DID key management including, but not limited to, authentication, signing, key storage, key recovery, synchronization across multiple devices and user experience.

## Outline

1. Key Storage
    1. Vault
    2. Device Key
    3. Session Key
2. Signing, frequent DID actions
    4. Interactions with other DIDs
    5. Claims
    6. Updating DID Docs
    7. Capabilities
3. Multi-Device
    8. Replication
    9. Concurrent Updates
4. Key Recovery
5. Authentication
    10. Pairwise DIDs
6. User Experience
7. Web APIs
    11. Webauthn / Credential Manager
8. Multiple Identities
9. How specific DID methods can be handled in browsers
10. Threats
    12. Stolen Device
    13. MITM
    14. Web Extensions
    15. 3rd Party Libraries