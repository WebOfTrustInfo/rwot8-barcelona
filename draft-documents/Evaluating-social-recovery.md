# RWOT8: Evaluating social schemes for recovering control of an identifier 

Sean Gilligan, Peg, Adin Schmahmann, Andrew Hughes, Christopher Allen

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

With traditional multi-user systems, such as web-based services where users authenticate with a username and password, there is typically an authority who may revoke, re-issue or modify identifiers when problems arise. In recent years, the limitations of this model have become more apparent, but there are also problems with giving individual users ultimate control of their identifiers. 

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

### Master Secret Recovery

(TBW about master keys, HD derivation, recovery words, etc.)

Multiple keys or passwords can be generated deterministically from a single master key. This has implications for recovery as it means it is only nessecary to safeguard a single master key. Furthermore, the key can be stored as a mnemonic phrase of consisting of dictionary words, which are easier for humans to read, write or remember.

#### Secret sharing schemes

Threshold based secret sharing schemes, originally proposed by Shamir and Blakley, can be used to recover lost keys by generating a set of shares which are distributed to trusted peers. Shares are points on a polynomial where coefficients are random except for the lowest which is the secret. 

Feldman, Pederson and Berry proposed methods of introducing verification of shares. This mitigates the problem of not being able to identify which share has been maliciously or accidentally modified.

For encryption keys these schemes are very useful, as the integrity of the original key is critical for decrypting existing material.  But for signing keys, when a key has been compromised we are often more interested in establishing a new key than recovering the old one. 

Secret sharing could be used for identifier or account recovery as follows:

- The identifier holder, Alice, initially creates a signed message announcing that a root public key `R_pub` is the ultimate controller of Alice's identifier.

- Alice uses a secret sharing scheme to distribute the corresponding private key `R_priv` amongst m of n of her friends and deletes any traces of `R_priv` from her machine

- In the event of that Alice loses control of her identifier she contacts m of n group members and asks them to return their secret shares to her.

- Alice then computes `R_priv` and publishes a signed, timestamped message that reasserts Alice's control over her identifier. 

- Any client software which seeks to validate Alice's identifier must resolve the identifiers current status by looking for messages published by `R_priv`. 

Advantages: 
 - Anonymity of group members is maintained
 - This scheme is easily compatible with schemes where identifiers are controlled by private signing keys and where it is possible to define key or identifier hierarchies

Issues:
 - Alice must recover the root private key `R_priv` on a trusted device. If that single device is compromised Alice's identifier essentially becomes unrecoverable.
 - Alice must trust her friends to protect the secrecy and integrity of her key shares, which they have no stake in.
   - If Alice's friends have public encryption keys she can encrypt the shares for her friends and store the encrypted shares in a location that is trusted for availability

### Capability Recovery

(TBW One use to enable a change (for instance a single UTXO), requirements reliability, custody, fiduciary responsiblity)
One particular thing is that Capabilility recover can better help in case of key compromise.
Many capabilities each potentially different agents.

#### Threshold signature schemes / Group signatures

Group signatures, originally described by David Chaum in 1991, allow a group member to make a signature which proves they are a group member but does not reveal who they are. Threshold-based group signatures require consensus of a specified quorum of group members, and as such have application in social recovery.

##### Boney-Lynn-Shacham

The Boneh–Lynn–Shacham signature scheme, which uses Weil pairings on an elliptic curve, has some desireable properties for group signatures.

Using BLS group signatures it is possible to have a signed message from *m* of *n* members of a group, with an identical signature and public key regardless of which group members signed.

This has implications for privacy, as verification is possible without needing to know which group members signed, or even the public keys of any individual group members. 

##### MuSig

Threshold signatures are also possible with the MuSig signature scheme, which is based on Schnorr signatures and builds upon the Bellare-Nevan multi-signature scheme by also allowing key aggregation.

MuSig signatures are provable unmalleable, meaning that given a message and a signature, it is not possible to produce another signature which is valid for that message with the same keypair.

##### Application for social recovery

Threshold signatures could be used for identifier or account recovery as follows:

- The identifier holder, Alice, initially publishes a signed message announcing the aggregated public key of the group who are empowered to make assertions on her behalf.

- In the event of key loss or compromise, Alice generates a new keypair, send her group members a signed, timestamped message containing her new public key, and contacts them out of band to confirm it was her. 

- n of m group members sign the message and their signatures are aggregated to produce and publish a single, signed message with Alice's new public key, which also serves to revoke the old one. 

- Any client software which seeks to validate messages from Alice must resolve her current public key by looking for messages published by her trusted group. 

- Alice publishes another signed message with her new key confirming the public key of her trusted group.

Advantages: 
 - Anonymity of group members is maintained

Issues:
 - Unlike secret sharing schemes like Shamirs, this recovery mechanism requires changes to the system using it. It cannot be used for existing systems which have not implemented this mechanism. 

#### Social Identifier Post-Recovery in Offline/Distributed Systems

Since identifiers are recovered by messages signed by a trusted group, in order for the network to learn about changes to an identifier it is important the these recovery messages are propagated.

In centralized systems this is trivial since the centralized authority is trusted to propagate messages from users.

In decentralized linear consensus systems (e.g. proof of stake blockchains) the propagation of messages can be tied to the consensus mechanism. For example, Alice knows Bob saw her identifier update method as long as Bob has seen data consensus from after Alice published her update. Alice can then assume Bob has seen her update as long as Bob would notice something wrong if the consensus system stalled/did not make progress.

In distributed systems, establishing a model for consensus is more difficult. However, one model that can be used is fork-consistency. With fork-consistency Alice can assert that Bob has seen her update `U` as long as Bob has seen any update Alice has made since `U`. In these systems the ability to see fresh/accurate data is gated by the amount of information in the system. For example, in bitcoin Alice's protection against Bob seeing a forked blockchain is that if Bob has any interaction with a peer using the correct blockchain he will realize he should look for more information before using Alice's identifier.

#### ZK Key Ceremonies

(TBW: Instead of a hardware generation of a keys, it may possible to have a personal version of the Z-Cash ceremony where your peers create via MPC a key for you (or for all the peers), along with a shared proof that the key (or keys) were properly created. It may also be possible later for a threshold of those same peers to create a new key for you later, and using the old proof provide a new proof that the new key is created by the same people that created the old key.)

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

TODO: Look for and include existing references on the network and social issues we've raised above. 

 
### Revocation of compromised keys

[Permanent Revocation Systems - Brownstein, Gilboa,Dolev](https://www.cs.bgu.ac.il/~frankel/TechnicalReports/2017/17-02.pdf)