# DID Namespace Records

--_Drummond Reed_, V1 2019-01-31

## Introduction & Motivation

DIDs are a unique new class of globally unique identifiers with four primary properties:
1. **Persistent**—assigned once and never change.
1. **Resolvable**—they are associated with standard metadata describing the identified entity
1. **Cryptographically-verifiable**—the DID controller can prove ownership using private keys
1. **Decentralized**—No centralized registration authority is required.

DIDs can be supported on any modern blockchain or distributed ledger by creating a **DID method** for that target system. Each DID method operates in its own **DID namespace**. DID method names can be nested within a namespace just like other hierarchical name systems, e.g., DNS. For example:
```
did:example:
did:example:foo:
did:example:bar:
did:example:bar:baz:
```
However the DID spec (as of 2019-01-31) does not include a mechanism to enable DID namespaces to "point" to one another—similar to how DNS nameservers point to one another—in a manner that can be discovered and cryptographically verified.

The lack of this feature is not surprising since every DID method name represents an entire decentralized network, and it was originally thought that the "flat" nature of DIDs meant nesting DID namespaces would have minimal value.

But as DID usage has grown, new motivations have emerged for linking DID namespaces. Besides discoverability of different decentralized networks, DID namespace linking also enables building bridges between different governance frameworks and trust assurance models—key building blocks for **web of trust**.

## Specification

[TODO—simple definition of a DID namespace record]

## Example

[TODO—simple example of a DID document containing a set of DID namespace records]

## Next Steps

[TODO—recommendations to the W3C Credentials Community Group]
