# Decentralized Identity Fee Market
---
by Yancy Ribbens

*Micro-payments and DID (Decentralized Identities) can enable a user to
curate their online identity, request payment or mark data private. This
article proposes allowing a fee market to develop around what
information a user chooses to reveal about their identity in the context
of verifiable credentials.*

Introduction
============

DID (Decentralized Identity) enables a user to control one or more online
identities. These identities can be verifiable due to the cryptographic
attestations that can be made. For example, A DID can be signed by an
entity, such as a government, to improve the quality and reliability of
information attached to the identity.

A DID can be anchored to a public blockchain which acts as a registry.
Interrogating a public blockchain allows a user to find, reference,
revoke or update a DID. Only the user possessing cryptographic evidence
to a DID can make state changes and prove ownership. Services that
implement DID infrastructure allow users to be the source of truth for
their online identity, removing ownership from third parties or other
central authorities.

Earners
=======

When a user earns a credential that is verifiable, that user may
advertise or reveal data about his/her achievement. However, the user
may not wish details of his/her Personally Identifiable Information
(PII) to be surfaced and associated with that credential. By associating
a DID with the credential the user can reveal only the details they
wish.

Issuer
======

An issuer is an entity that issues a credential to an earner. Typically
this issuer knows the user by their first name, last name, SSN or other
forms of PII which the issuer uses as identification. By using a DID in
lieu of other PII, the issuer is limited to only the PII that is
relevant to issue the credential and nothing more. For example, the
issuer may require a DID that has been signed by a government to show
citizenship. When the issuer issues a credential because of a passing
exam, they only need to associate the passing marks with a unique DID
that has citizenship. Other attributes of the earner such as race, age,
name and gender can all be hidden by the owner of the DID because they
are irrelevant to the achievement.

Credential
==========

An earner is the recipient and the holder of the credential issued by
the issuer. Example credentials are Blockcerts and OBI. These
credentials types have data attributes for both issuer and earner
(credential recipient). By augmenting a credential to use an issuer DID
and a recipient DID, both issuer and earner can have greater control
over the data that is revealed and associated with the verifiable
credential.

Issuing Authority
=================

The issuing authority is often a third party entity contracted out by
the issuer and registered with by the earner. This authority may
possesses details of PII associated with the issuer as well as the
earner. This allows the issuing authority to be an intermediary for PII
data. However, if a DID was used, the issuing authority would have only
the details revealed by the the earner and issuer DID.

DID Semantics
=============

A DID gives users greater sovereignty over their data by enabling the
user to be the source of truth of their identity. In the case of BTCR
(Bitcoin Resolver), the user identity is secured in the same way as
currency. The owner of the identity possesses a public key which can be
known to anyone, and a private key known only by the identity holder (or
software interface the identity owner trusts). This public key can
reference one or more outputs which point to an external resource under
control of the user. Example outputs could be, a web site the user
trusts to store their identity, the IP address of their own personal
computer or an IPFS address. If the user ever loses control of the
end-point their DID points to, the user's private key can be used to
revoke the DID.

Developing a fee market
=======================

Micro-payments, for example the bitcoin lightning network, allow
paywalls to be constructed, which reveal information in exchange for
small amounts of currency. Every request for data pertaining to a DID
can be serviced only if the requester meets the micro payment requested
by the user. Instead of receiving a micro-payment, the DID owner may
chose to make their DID available to entities free of charge for a
service, such as a job market placement. In such a system, an algorithm
could be constructed to parse all blockchains in search of a DID with
matching criteria. This would be done by identifying which addresses are
associated with DIDs and either following the public information or
beginning negotiation.
