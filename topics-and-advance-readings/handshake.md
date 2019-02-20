## Handshake

by Boyma Fahnbulleh \<<boymanjor@protonmail.com>\>

### Introduction

Handshake is a decentralized, permission-less naming protocol compatible with
DNS. We seek to solve [Zooko's triangle][zooko] through the use of a utxo-based
blockchain, which manages the registration, renewal, and transfer of DNS
top-level domains (TLDs). The initial goal is not to replace the DNS protocol but
to replace the root zone file and the root servers with a decentralized, public
commons. By tying name ownership to a utxo, and embedding DNS records into its
metadata, a chain of trust can be created by a digital signature and verified
by querying blockchain data. A decentralized network of validating peers anchors
this chain of trust. The ultimate goal is to provide an alternative to existing
Certificate Authorities.

Our naming protocol differs from its predecessors in that it has no concept of
subdomains at the consensus layer. The protocol also provides secure name
resolutions via light client resolvers by committing to name data in the block
headers and using compact, merklelized proofs of inclusion and non-inclusion.

We believe this project could be used to add human readability to DIDs by
committing to them in the DNS records of names registered on the network.
Or the names themselves could exist as DIDs and DID documents could be
committed to in the DNS records.

### Name Auctions

Second-price, blind bid (Vickrey) auctions manage the issuance of names on-chain.
A consensus-level covenant system facilitates these auctions by encumbering utxos
with spending restrictions. A collection of these covenants model an auction
state machine.

For example, to bid on a name, one must spend a utxo in a transaction which creates
an output which carries a 'BID' covenant. This output will have a value which
is equal to (or higher) than the amount the user intends to bid on the name.
It will also include the name up for auction and a commitment to the actual
bid amount. The 'BID' covenant will restrict this output from being spent in
any transaction that does not create an output with a 'REVEAL' covenant.

The 'REVEAL' covenant essentially reveals the actual bid amount and allows the
excess value in the 'BID' covenant to be spent freely. The rest of the auction
process, as well as DNS record updates and name transfers, are modeled
in this covenant system.

### Network Bootstrapping

Consensus rules reserve all entries in ICANN's existing root zone file. Names in
the list of Alexa top 100,000 domains are also reserved. The latter names are
converted to TLDs by selecting their first domain name label. Name owners can
bypass the auction system and claim names through the use of DNSSEC ownership
proofs. We also have a sunrise period to allow trademark holders without domains
in the Alexa top 100,000 to reserve names.

The DNSSEC ownership proofs mentioned above are a stricter subset of
[DNSSEC proofs][dnssec]. They do not allow for CNAME glue or wildcards, and every
label must be separated by a zone cut using a typical DS-to-DNSKEY setup for
referrals. All zone referrals are retrieved and combined to produce the final proof.

These proofs must stem from ICANN's key-signing keys (KSKs) to the final ZSK in the
target zone. The ultimate zone-signing key (ZSK) must sign a TXT record which commits
to the name's desired address on the blockchain. The proof is broadcast to the
peer-to-peer network and included by miners in the coinbase transaction of a block.
The consensus rules dictate that the miner must create an output for the associated
proof, granting the name to the committed address.

### Software

[hsd][hsd] is a full node, Javascript implementation of the protocol and an
authoritative name resolver for the root zone. [hnsd][hnsd] is an SPV name resolver
written in C. It acts as a light client to the blockchain, as well as a recursive
name server. It can serve provable resource records without having the resource
requirements of a full node.

### Project Paper

This document is a high-level overview of the Handshake protocol. For a more detailed
description of the protocol, please read the
[project paper][paper].

[zooko]: https://web.archive.org/web/20011020191610/http://zooko.com/distnames.html
[dnssec]: https://tools.ietf.org/html/rfc4033
[hsd]: https://github.com/handshake-org/hsd
[hnsd]: https://github.com/handshake-org/hnsd
[paper]: https://handshake.org/files/handshake.txt
