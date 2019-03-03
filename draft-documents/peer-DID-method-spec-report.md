# Peer DID Method Specification Report

## Authors
  Brent Zundel
  Timo Welde
  Mike Varley

## Contributer

# Abstract

This paper consists of objectives, use cases and observations around a peer-to-peer DID method, based off a draft specification submitted to RWOT8. The following abstract is from that draft specification.

This DID method spec conforms to the requirements in the DID specification currently published by the W3C Credentials Community Group. For more information about DIDs and DID method specifications, please see the DID Primer and DID Spec.
This document defines a "peer" DID Method that can be used independent of any source of truth external to the relationship in which it is used. The method is cheap, fast, scalable, and secure. It is suitable for most private relationships between people, organizations, and IoT things. DIDs associated with this method are also promotable to a more public context. That is, blockchains with different DID methods can graft some or all peer DIDs into their namespace(s) with no risk of accidental collision, and no loss of meaning. Peer DID will have a recognizable and consistent identity in all of them.


# Objectives
- p2p DIDs are transactional - they may be used for one or more transaction between parties.
- p2p did communication/resolution does not require a Universal Resolver - documents are self contained in a message protocol.
- p2p did exchange is for the purposes of establishing secure communication, but Trust in the peers must be established at another level step (in person, out of band, using Verifiable Credentials, using other attestations)
- p2p DIDs communication / protocol is not bound to any specific ledger based DID service or design model
- p2p DIDs are interoperable with Ledger (anchored) backed DIDs; the ‘anchored’ DID documents can be exchanged over this methodology and treated as ‘peer’. 
- create an n-wise peer DID spec - of which a use case is pairwise DID exchange.

# Use Cases

Two or more individuals can create DIDs “without any overhead”: infrastructure, registry costs, or time penalty, or even network requirement.

Two service entities wish to communicate in an ‘anonymous but trusted’ way for a data exchange transaction, but do not need this relationship persisted beyond the transaction lifetime.

In a doctor, hospital, patient context these three entities may wish to establish trusted communication channels for delegating care or sharing information (securely) regarding the other parties (the hospital sharing a record with the doctor and the patient seeing the exchange has occurred).


# Spec Review Observations

## Groups section
- It should be made clear that if an Alice and Bob are already connected (through peer DIDs) they would need to create new peer DIDs when adding another party Carol (both to each other and for Carol).

- Removing participants from a Group is basically recreating the group without the person who is 'removed'.

## Protocol - Message Format section

- Indy HIPE message protocol is referenced - with the desire to be as close to JWE "as possible" 


# Next Steps


