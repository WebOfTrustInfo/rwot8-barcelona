# Re-inventing Incentive Structures Using DID and Microtransactions
---
by Yancy Ribbens

*Microtransactions and DID (Decentralized Identifiers) can enable a user to curate their online identity, request payment or mark
data private. This article proposes allowing a fee market to develop around what information a user chooses to reveal about their identity in the context of an earned credential.*

Introduction
============

A DID can be anchored to a public blockchain which acts as a registry.
Interrogating a public blockchain allows a user to find, reference,
revoke or update a DID. Only the user possessing the cryptographic material
to a DID can make state changes and prove ownership. Services that
implement DID infrastructure move ownership of identifiers from third parties to
individuals, thereby allowing people ownership of their digital identifiers.

Earners
=======

When an individual earns a credential, they may
choose to advertise or reveal data about the achievement. However, the individual
may not wish details of his/her Personally Identifiable Information
(PII) to be surfaced and associated with a credential.

Issuer
======

An issuer is an entity that issues a credential to an earner. Typically
this issuer knows the person by their first name, last name or other
forms of PII which the issuer uses as identifiers. By using a DID in
lieu of other PII, the issuer could be limited to only the PII that is
relevant to issue the credential and nothing more. For example, the
issuer may require cryptographic proof that has been signed by a government to show
citizenship. When the issuer issues a credential because of a passing
exam, for example, they only need to associate the passing marks with a unique DID
that has citizenship. Other attributes of the earner such as race, age,
name and gender can all be hidden by the owner of the DID because they
are irrelevant to the achievement.

Credential
==========

Example credentials such as Blockcerts and OBI have data attributes for both issuer and earner
(credential recipient). By augmenting a credential to use an issuer DID
and a recipient DID, both issuer and earner can have greater control
over the data that is revealed and associated with the 
credential, assuming no other PII is collected except the DID pubkey.

Issuing Authority
=================

The issuing authority is often a third party entity contracted out by
the issuer and registered with by the earner. This authority may
possess details of PII associated with the issuer as well as the
earner enabling the issuing authority to be an intermediary for PII data.

DID Semantics
=============

BTCR (Bitcoin Resolver), secures an individual's identifiers in the same way as
currency. The owner of the identifier possesses a public key which can be
known to anyone, and a private key known only by the identifier owner (or
trusted interface). This public key can
reference one or more outputs which point to an external resource under
the control of an individual. Example outputs could be, a trusted website, the IP address of their own personal
computer or an IPFS address. If the identifier owner loses control of the
end-point their DID points to, the user's private key can be used to
revoke the DID.  Furthermore, if the identity owner loses the private key, decentralized key
recovery systems using Shamir secret sharing are possible.

Developing a fee market
=======================

Microtransactions, for example, the lightning network, allow
paywalls to be constructed, which reveal information in exchange for
small amounts of currency. Every request for data pertaining to a DID
could be serviced only if the requester meets the payment requested
by the individual. Instead of receiving a microtransaction, the DID owner may
choose to make a DID available to external entities for free. Furthermore, an algorithm
could be constructed to parse arbitrary blockchains in search of a DID with
matching criteria. This could be done by identifying which addresses are
associated with DIDs and either follow the public information or negotiate payment.
