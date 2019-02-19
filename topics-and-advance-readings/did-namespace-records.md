# DID Namespace Records

--_Drummond Reed_, V1 2019-01-31

## Introduction & Motivation

DIDs are a unique new class of globally unique identifiers with four primary properties:
1. **Persistent**—assigned once and never change.
1. **Resolvable**—associated with standard metadata describing the identified entity
1. **Cryptographically-verifiable**—the DID controller can prove ownership using private keys
1. **Decentralized**—no centralized registration authority needed.

DIDs can be supported on any modern blockchain or distributed ledger by creating a **DID method** for that target system. Each DID method operates in its own **DID namespace**. DID method names can be nested within a namespace just like other hierarchical name systems, e.g., DNS. For example:
```
did:example:
did:example:foo:
did:example:bar:
did:example:bar:baz:
```
However the DID spec (as of 2019-01-31) does not yet include a mechanism to enable DID namespaces to "point" to one another—similar to how DNS nameservers point to one another—in a manner that can be discovered and cryptographically verified.

The lack of this feature is not surprising since every DID method name represents an entire decentralized network, and it was originally thought that the "flat" nature of DIDs meant nesting DID namespaces would have minimal value.

But as DID usage has grown, new motivations have emerged for linking DID namespaces. Besides discoverability of different decentralized networks, DID namespace linking also enables building bridges between different governance frameworks and trust assurance models—key building blocks of a global **web of trust**.

## DID Namespace Records

This gap can easily be filled with a simple addition to the DID specification: **DID namespace records**. The  vocabulary for DID namespace records could be defined either by:
1. Adding it to the base JSON-LD context for all DID documents, or
1. Specifying it in a separate JSON-LD context for DID namespace records.

Which approach is better is a judgement that can be made by the forthcoming DID Working Group. In this proposal, we will assume the former approach, i.e., that the vocabulary for DID namespace records have been included in the base JSON-LD context for DID documents.

A DID namespace record is very simple because its address is just **the fully qualified name of the DID method for that namespace**. In other words, to resolve a DID namespace record, a DID resolver simply makes a resolution request for the fully qualified DID method name using that DID method. For example, to request the DID namespace record for `did:example:foo:`, a resolver would resolve the DID method name `did:example:foo:` using the DID method `:did:example:`.

The DID document returned MAY contain one or more DID namespace records. Each DID namespace record is a JSON object in the following form:
```
{
	"children": ["did:example:foo:", "did:example:bar:"],
	"remote": ["did:abc:", "did:xyz:"]
}
```
* **Children** are child namespaces of the parent DID namespace.
* **Remote** are pointers to other associated DID namespaces that are not children of the parent. In this specification, no semantics are defined for this pointer. Such semantics MAY be specified by a DID method specification, by the governance framework for a DID namespace, or other mechanisms.

## Example DID Document for a DID Namespace Record

The following DID document could be maintained by the authority for the `did:example:` namespace.
```
{
	"@context": ["https://w3id.org/did/v1"],
	"id": "did:example:",
	"publicKey": [{
		"id": "did:example:123456789abcdefghi#keys-1",
		"type": "RsaVerificationKey2018",
		"controller": "did:example:123456789abcdefghi",
		"publicKeyPem": "-----BEGIN PUBLIC KEY...END PUBLIC KEY-----\r\n"
	}],
	"children": ["did:example:foo:", "did:example:bar:"],
	"remote": ["did:abc:", "did:xyz:"]
}
```
## Value Propositions for Linked DID Namespaces

Unlike DNS, where resolution of all domain names uses the same protocol, resolving a DID from a specific DID namespace requires a DID resolver to understand the associated DID method. If a resolver does not support that DID method, it will not be able to resolve that DID. 

However DIDs are a very different type of identifier than a domain name, so linking DID namespaces solve a different problems that delegating domain names. The two primary use cases as of this writing are:
1. **Discovery of child networks within a decentralized network of networks.** If a group of decentralized networks wanted to explicitly (and verifiably) express an affiliation, they can do it with DID namespace records. The children of the `:did:example:` namespace shown above are an example. There are two potential motivations:
   1. **Sharing the same parent DID method**—the networks could agree to all share the same DID method definition across all the namespaces while allowing each network to have its own governance.
   1. **Inheriting from the same parent governance framework**—the networks could all agree to the same base trust guarantees.
1. **Discovery of affiliated remote networks.** Although these remote networks do not share the same DID method, an explicit link could express some shared policies or trust guarantees—particularly if it was bilateral.

## Next Steps

After review and discussion at Rebooting the Web of Trust #8, the intent is to submit this proposal as a feature request for the main DID specification.
