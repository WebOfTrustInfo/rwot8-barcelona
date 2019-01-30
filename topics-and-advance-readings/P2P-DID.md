# Peer to Peer DIDs
by Brent Zundel (with much input from Daniel Hardman)

## Abstract
Multiple DID methods are under development, each based on a different support structure
(e.g. Veres One, Sovrin, IPFS, etc). During development of standard DID method specifications,
and while exploring certain DID-related use cases, there has arisen the notion of a "ledgerless"
DID, i.e. a DID that is not anchored to any infrastructure. We call these peer to peer (P2P)
DIDs because the first use cases that explored the need for ledgerless DID were peer to peer
messaging scenarios.

## Proposal
* Work on a DID Method spec for P2P DIDs as a special subset of DIDs that are not universally
resolvable on some ledger or central storage infrastructure, but only within the group where
they are used. [Draft of P2P DID Method Spec.](https://github.com/brentzundel/peer-did-method-spec)
* Show how a P2P DID could be added/converted to an existing DID method.

## Requirements
* P2P DIDs should be probabilistically unique among the set
  of all possible P2P DIDs.
* A P2P DID may be later made public by anchoring on infrastructure
  and converting into a DID that resolves according to the DID method
  specification for that infrastructure.
* A P2P DID may be anchored to multiple infrastructures simultaneously.
