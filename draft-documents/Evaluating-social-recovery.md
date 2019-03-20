# RWOT8: Evaluating social schemes for recovering control of an identifier 

Sean Gilligan, Peg, Adin Schmahmann, Andrew Hughes

### Abstract

As systems where people are required to manage their own keys become more popular, social recovery or reissuance of keys increases in importance. Such systems are inherently empowering to users but safegaurding keys is a hard problem.

We focus on social recovery of control of an identifier. There are several techniques to re-assert control over identifiers including key recovery and issuance of a new key. In many situations it is preferrable to establish a new key than recover the old one. 

We propose a rubrik for evaluating such schemes, and provide some possible schemes to consider.

## Table of Contents

1. Introduction
2. Evaluation Rubric
3. Example Schemes
4. Conclusion

## Introduction

With traditional multi-user systems, such as web-based services where users authenticate with a username and password, there is typically an authority who may revoke, re-issue or modify identifiers when problems arise. In recent years, the limitations of this model have become more apparent, but there are also problems with giving individual users ultimate control of their intentifiers. 

Several proposals have been made for 'social recovery', generally involving consensus of a quorum of trusted peers chosen by the user themself. These offer a promising compromise but there are a multitude of social, technical and contextual factors which should be considered before adopting such a scheme. 

We address this problem by defining a rubrik to help determine the suitability of different social recovery schemes in a particular context.

### A Rubrik for Evaluating Recovery Schemes

#### Definitions:

##### Actors
 - **User**: The entity whose key may need to be recovered
 - **Peers**: The entities who will be assisting the **User** in recovering their identity

##### Lifecycle of Indentifiers:
 - **Setup**: The user does any preparation work required to use the recovery scheme in the future
 - **Stasis**: The time between the user's setup phase and the recovery phase
 - **Recovery**: The recovery method is used to assert control over their identifier

##### Questions:

###### Actor Experience

- Must peers know their involvement before the setup phase?
- Is it neccessary to gain consent from trusted peers?
- What involvement is required from peers during stasis?
  - If it's significant does the scheme have any mitigation efforts?
    - External incentives (friendship, business, family)
    - Uses a peer's existing incentives (e.g. lose funds, phone stops working)
    - Explicit rewards (gamification and/or cryptocurrency)
- What involvement is required from the user during stasis?
- How does the scheme deal with a loss of confidence in one of the peers?

###### Identfier Recovery Scenarios
  * Lost secret - control of the identifier has been lost, but it has not been compromised.  For example, device has fallen in the sea.
  * Compromised secret.  For example, device is stolen.
  * Inheritance after death or incapacitation - we want to enable control of the identifier to our hiers.

###### Threat Model

- Can the scheme work in a distributed architecture (e.g. high latency, partitioned networks, etc.)? 
- How well does the system deal with malicious behaviour of individual peers
- Is there a single point of compromise during recovery?
- Is the anonymity of the trusted peers maintained?
- What security assumptions does the scheme rely on?

###### Externalities
* How to measure/monitor the strength of the backup web?
    * Health check
    * Transitive (indirect) peers
* Network growth problem
    * Use can't rely on their key until they can rely on their peers and their peers rely on their keys.

## Example schemes to consider

### Secret sharing schemes

Threshold based secret sharing schemes, originally proposed by Shamir and Blakley, can be used to recover lost keys by generating a set of shares which are distributed to trusted peers. Shares are points on a polynomial where coefficients are random except for the lowest which is the secret. 

Feldman, Pederson and Berry proposed methods of introducing verification of shares. This mitigates the problem of not being able to identify which share has been maliciously or accidentally modified.

For encryption keys these schemes are very useful, as the integrity of the original key is critical for decrypting existing material.  But for signing keys, when a key has been compromised we are often more interested in establishing a new key than recovering the old one. 

### Threshold signature schemes / Group signatures

Group signatures, originally described by David Chaum in 1991, allow a group member to make a signature which proves they are a group member but does not reveal who they are. Threshold-based group signatures require consensus of a specified quorum of group members, and as such have application in social recovery.

The Boneh–Lynn–Shacham signature scheme, which uses Weil pairings on an elliptic curve, has some desireable properties for group signatures.

Using BLS group signatures it is possible to have a signed message from *m* of *n* members of a group, with an identical signature and public key regardless of which group members signed. 

This could be used for identifier or account recovery as follows:

- The identifier holder, Alice, initially publishes a signed message announcing the public key of the group who are empowered to make assertions on her behalf.

- In the event of key loss or compromise, Alice generates a new keypair, contacts m of n group members and gives them her new public key. 

- The group publishes a signed, timestamped message with Alice's new public key, which also serves to revoke the old one. 

- Any client software which seeks to validate messages from Alice must resolve her current public key by looking for messages published by her trusted group. 

- Alice publishes another signed message with her new key announcing the public key of her trusted group.

Advantages: 
 - Anonymity of group members is maintained

Issues:
 - Clients must have access to most recent messages in order to resolve Alice's current key.  This is difficult with distributed or offline-first systems.
 - Unlike secret sharing schemes like Shamirs, this recovery mechanism requires changes to the system using it. It cannot be used for existing systems which have not implemented this mechanism. 

### Schnorr signatures (TODO)

### Rubric Evaluations (WIP)

Classic Shamir Usage:
 - Peers are asked to store User's recovery data
 - Peers are required to protect User's recovery data (and report issues if the recovery data is leaked)
 - User doesn't need to do anything during stasis
 - Relies on the channels peers use to send the recovery data to the user being private. Relies on the user's device being private
 -  Requires redoing the setup phase (reissuing recovery data to all peers)
 -  They are allowed to withhold or send incorrect recovery data
 -  Yes, the user device
 -  Yes, assuming that the channels peers use for sending recovery data are anonymous and protected from traffic analysis

Multi Signature Schemes:

- Peers not required to store information beyond what they already have
- Peers required to protect their keys (and report issues if their keys are compromised)
- User doesn't need to do anything during stasis
- Requires redoing the setup phase (no peer interaction required)

### Conclusion (TODO)

> [name=peg] somewhere in the conclusion i would like to mention again this distinction between the need to recover lost encryption keys, and the need to re-establish new signing keys (not much point in recovering them). as this was the biggest 'aha' thing i took home from RWOT.

## References (TODO)

- [Boneh, Lynn & Shacham 'Short Signatures from the Weil Pairing' - Journal of Cryptology, Sept 2004 Vol 17 Issue 4 p297-319](https://link.springer.com/article/10.1007%2Fs00145-004-0314-9)
- [Gennaro Jarecki - Secure distributed key generation for discrete log](https://www.semanticscholar.org/paper/Secure-Distributed-Key-Generation-for-Discrete-Log-Gennaro-Jarecki/bf9e630c13f570e2df05b6dcce3ea987015af7c3)
- [Threshold Signatures on the keep network](https://blog.keep.network/threshold-signatures-ff2c2b98d9c7)
- [Parity's 'secret store' distributed key generation](https://wiki.parity.io/Secret-Store)
- [BLS Signatures: better than Snorr - Medium ariticle](https://medium.com/cryptoadvance/bls-signatures-better-than-schnorr-5a7fe30ea716)
- [Practical Threshold Signatures - Victor Shoup](https://www.iacr.org/archive/eurocrypt2000/1807/18070209-new.pdf) on RSA, from 2000
- [Dfinity's implementation of Distributed Key Generation using BLS](https://github.com/dfinity/dkg)
- [web based demo of verifiable secret sharing using BLS](https://herumi.github.io/bls-wasm/bls-demo.html)
- [Colic, Petar Hlad - Anonymous Threshold Signatures](https://upcommons.upc.edu/bitstream/handle/2117/119360/memoria.pdf?sequence=1&isAllowed=y)
- [Back and Zheng - Identity-Based Threshold Signature Scheme from the Bilinear Pairings](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.157.6146&rep=rep1&type=pdf)
- [Gregory Maxwell, Andrew Poelstra1, Yannick Seurin, and Pieter Wuille - Simple Schnorr Multi-Signatures with Applications to Bitcoin](https://eprint.iacr.org/2018/068.pdf)

TODO: Look for and incoude existing references on the network and social issues we've raised above. 

 
### Revocation of compromised keys

[Permanent Revocation Systems - Brownstein, Gilboa,Dolev](https://www.cs.bgu.ac.il/~frankel/TechnicalReports/2017/17-02.pdf)