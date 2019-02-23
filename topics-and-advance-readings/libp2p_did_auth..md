# libp2p for DID Authentication and the exchange of Verifiable Credentials

*Draft: Rebooting Web of Trust VIII Topic Paper by [jonnycrunch](https://github.com/jonnycrunch)

[Rebooting the Web of Trust, Spring 2019](https://github.com/WebOfTrustInfo/rwot8)

## Abstract

Peer to peer protocols in general have a distributed application architecture whereby each participant have an equal privilege to participant in the system [1].  The concept was popularized with the music file sharing application <a href="https://en.wikipedia.org/wiki/Napster">Napster</a> and more recently the <a href="https://ipfs.io">Interplanetary File System (IPFS)</a>. 

Since the emergence of the first draft of the [DID specificaiton](https://w3c-ccg.github.io/did-spec/) from the [Fall 2016 Rebooting the Web of Trust](https://github.com/WebOfTrustInfo/rwot3-sf) [[2]](#ref), numerous [DID method specifications](https://w3c-ccg.github.io/did-method-registry/) have appeared. Each DID method specification defines how to resolve a cryptographically-tied DID document given a method-specific identifier. In our [last paper](https:// ) we presented how IPLD could be used as a generalized framework to repesent and resolve the DID document.  In this paper, we will describe a way to perform [DID authenication](http://did.auth) and thereby proove ownership of the private key that is presented in the DID document utilizing the libp2p protocol.   

Operating within one particular DID method simply requires applying specific protocols dictated in it's DID method specification and typically under the constraints of it's distributed ledger or network. However, authentication between DID methods, where may have implemented disperse cryptographic suite of tools will proove to be more challenging.  In this paper, we would like to introduce the libp2p protocol to solve this problem. 

## Why libp2p

Libp2p is a modular networking framework that enables peer-to-peer applications.  Originally part of the Interplanetary File system (IPFS), it has since broke out into it's own separate project and supports a variety of applications including [Parity's Polkadot](https://polkadot.network/) and is being evaluated for [Ethereum 2.0](https://github.com/ethereum/eth2.0-specs/tree/v0.1). 

In traditional client/server model a stateless communication channel is iniated via an IP address and port combination. Libp2p uses the concept of a [multiaddress](https://github.com/multiformats/multiaddr) instead.  

Some examples:
- **/ip4/157.230.86.31/udp/9999** indicates the node with IP version 4 address of 157.230.86.31 and listening on UDP on port 9999
- **/ip6/ffe80::21f:5bff:fe38:6d91/udp/1567/quic** means that we should use the QUIC protocol on top of UDP port 1567 with an IPv6 address
- **/dns4/example.com/tcp/80/ws** means that we should use the WebSocket protocol on top of TCP port 80, using DNS to resolve the hostname example.com


## DID authentication 

The term DID authenctication is still not currently well defined [1].  From a white paper from the Rebooting web of Trust in 2018, DID authenication is defined as a ceremony where `the identity owner, with help of various components such as web browsers, mobile devices and other agent proves to a relying party that they are in control of a DID.`   This ceremony involves leveraging a number of pre-determined data formats, protocols and flows that transcend individual DID methods, but ultimately arrives at the end that the relaying party is sufficiently satified that the proving party is in control over the private key associated with the the public key published to the DID document specified as part of the DID method specific identifier. 

The [DID specification](https://github.com/w3c-ccg/did-spec) allows for attribute declaration of multiple services including for DID authentication. After DID authentication (and thereby prooving control over the private key associated with the DID method specific identifer as declaried in the DID document), a multitude of other service and workflows can be performed including Authorization, Access control lists, exchange of Verifiable Credentials and invoking an [Object Capability Systems](https://en.wikipedia.org/wiki/Object-capability_model).   

Example 1:  DID authentication declaration inside an example DID document [3]: 
```
{
	"@context": "https://w3id.org/did/v1",
	"id": "did:example:123456789abcdefghi",
	"service": {
		"type": "DidAuthService",
		"serviceEndpoint": "https://auth.example.com/did:example:123456789abcdefg"
	}
}
```

Example 2.  DID authentication declaration using libp2p as a service endpoint

```
{
    "@context": "https://w3id.org/did/v1",
	"id": "did:ipid:12D3KooWMHdrzcwpjbdrZs5GGqERAvcgqX3b5dpuPtPa9ot69yew",
    "service":  {
      "type": "DidAuthService",
      "serviceEndpoint": "/ip4/108.241.29.82/tcp/1265/ipfs/QmZTefe4V1KYwLUfhGVMMBbAkAa4E9vynzSNx5vPtrG4dv",
    }
}
```


This paper will review the mechanism and workflow specifically for DID authentication in the form of data formats, challenges and responses to facilitate proving ownership of a private key published to the DID docuemnt for a speficic DID method specific identifer followed by issuing a Verifiable Credential. 

DID authencication may involved one-way interactions or a bi-directional protocol over each respective DID authentication server endpoints.  We will explore both a unidirections DID authenications and bidirectional DID authentication over the libp2p protocol.  

DID authentication, at it's simplest interpretation, could be perceived as being the verification of a credential, and in this case the claim is control over the private key associated with the DID method specific identier ( or the prive key associated with the hash of the public key ). 


## libp2p 

- uses multiformats extensively 
- discoverablilty and connectivity of peers 
- process addressing ( when you connect that process you can authenicate )
- future proof stack 
- open source 
- encrypted connections by default 
- use in high latency scenarios
- work offline (offline first)
- protocol multiplexing 
- works in the browser 
- roaming ( independently coordinate the mobile edge client )
- works in the browser ( webRTC )
- used in Metamask for moving blocks of ethereum blockchain into the browser
- used by Parity networks Pokidot 
- used by Filecoin 
 

## Overview of circuit relay

The circuit relay is a means to establish connectivity between libp2p nodes that wouldn't otherwise be able to establish a direct connection to each other. [4]

Relays are generally used in situations where nodes are behind NAT, reverse proxies, firewalls and/or simply don't support the same transports (e.g. go-ipfs vs. browser-ipfs). Even though libp2p has modules for NAT traversal (go-libp2p-nat), piercing through NATs isn't always an option. The circuit relay protocol exists to overcome those scenarios.

In the context of DID authentication circuit relays could be used to prevent correlation based on IPV4 or IPV6 addresses.    

The relay node short-circuits streams between the two nodes, enabling them to reach each other and prevent correlation. 

```
+-----+    /ip4/.../tcp/.../ws/p2p/QmRelay    +-------+    /ip4/.../tcp/.../p2p/QmTwo       +-----+
|QmOne| <------------------------------------>|QmRelay|<----------------------------------->|QmTwo|
+-----+   (/libp2p/relay/circuit multistream) +-------+ (/libp2p/relay/circuit multistream) +-----+
     ^                                         +-----+                                         ^
     |           /p2p-circuit/QmTwo            |     |                                         |
     +-----------------------------------------+     +-----------------------------------------+
```

In the above example, the node labeled `QmOne` is connected to node `QmTwo` via a circuit relay `QmRelay`. `QmRelay` is configured to allow for relaying of connections between nodes and `QmOne` is configured to use `QmRelay` for relaying. All communication is encrypted between QmOne and QmTwo and the identity of the remote is verified, so the proxy QmRelay cannot act as a man-in-the-middle.  DID authentication using circuit relaying is shown in Example 3.  


Example 3.  DID authentication declaration using libp2p as a service endpoint with circuit relay. 

```
{
    "@context": "https://w3id.org/did/v1",
	"id": "did:ipid:12D3KooWMHdrzcwpjbdrZs5GGqERAvcgqX3b5dpuPtPa9ot69yew",
    "service":  {
      "type": "DidAuthService",
      "serviceEndpoint": "/p2p-circuit/QmTwo",
    }
}
```

## Problems with DNS 
- problem with location addressing 
- problem with root of trust 

## Example flow for DID Authentication

TBD

## Benefits

- Correlation can be prevented using circuit relays
- True peer-to-peer communication of 
- Ability to connect edge devices to operate without other connectivity to the rest of the internet 

## Drawbacks
- Unfortunately given the multiple levels of networking protocol, there are multiple layers of authenication and given the need for interoperability for other DID methods we need to add yet another on top of libp2p to allow for DID authentication. 
- In a simple world, the DID authenications would happen at the protocol layer. 
- QUIC implementation only supports RSA peer keys (Support for ed25519 and secp256k1 is pending )
- Multiaddress is not yet standardized thru IETF

## Conclusion

libp2p provides a robust framework for a lightweight protocol that faciliates cryptographic DID authentication over a variety of DID methods.  

## Discussion and Future Work

In this brief paper, we have introduced the application of libp2p as a general pattern for DID authentication and have highlighted its potential benefits and drawbacks and explained how it could be used across multiple DID method specifications. This technique enables a cost-effective and scalable solution for truly decentralized service endpoints to proove control over the private cryptographic key.    This framework could be used to accelerate the adoption of truly self-sovereign digital identities. 

In the future, we hope to formalize this approach with additional stakeholders and standard bodies. 


# Definitions

**Authentication**: The ceremony where an _identity owner_ proves to a _relying party_ that the _identity owner_ controls a DID, using a mechanism that is described in the DID's associated DID Document.

**Authorization**: A process of establishing the rights and privileges of an _identity owner_ to perform certain actions, including operations on a DID itself, or in another context.

**Decentralized Identifier (DID)**: A globally unique identifier that does not require a centralized registration authority because it is registered with distributed ledger technology or another form of decentralized network. (see [here](https://w3c-ccg.github.io/did-spec/#terminology))

**DID Document**: A structured document containing metadata that describes a DID, including authentication materials such as public keys and pseudonymous biometrics, that an entity can use to authenticate, i.e. to prove control of the DID. A DID Document may also contain other attributes or claims describing the entity. (see [here](https://w3c-ccg.github.io/did-spec/#terminology))

**DID Record**: The combination of a DID and its associated DID Document.

**Identity Owner**: The individual, organization or thing who created the DID, is identified by the DID that is the subject of the DID Document, and who has the ultimate authority to update or revoke the DID.

**Relying Party**: The individual, organization or thing that authenticates an _identity owner_ using a DID Auth protocol. Also called "Verifier" in other specifications.

**Verifiable Credentials**: A set of one or more claims that are statements made by an issuer about a subject that is tamper-resistant and whose authorship can be cryptographically verified (see [here](https://w3c.github.io/vc-data-model/#terminology)).


## References 
[1] [Peer-to-peer protocols](https://en.wikipedia.org/wiki/Peer-to-peer). 

[2] [DID (Decentralized Identifier) Data Model and Generic Syntax 1.0 Implementer's Draft 01 ](https://github.com/WebOfTrustInfo/rwot3-sf/blob/master/final-documents/did-implementer-draft-10.pdf)

[3] [Rebooting Web of Trust Spring 2018 - Introduction to DID Auth](https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/did-auth.md)