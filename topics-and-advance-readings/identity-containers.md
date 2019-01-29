# Sikaris - Decentralized Identity with Identity Containers (SSI)

Let's make DIDs and ERC725 work together.

Full proposal : [Sikaris](https://gitlab.com/caelumlabs/sikaris)

## Description

An implementation proposal for a Self Sovereign Identity (SSI) network using Blockchain as a DKPI

Long story short, We suggest to store just a Merkle Root of the keys and claims being holded by an entity (user, organization..,) and set a list standard endpoints to query and interact between entities. This way most of the information is transferred off-chain and the whole system should be GDPR compliant.

## Digital ID - SSI Nodes
Schema :

![Schema](https://github.com/WebOfTrustInfo/rwot8-barcelona/tree/master/topics-and-advance-readings/media/diagram.png)

A Digital ID is composed by :

1. **DID**. A unique Decentralized Identifier. This identifier includes information about the plaform (network) the identity is deployed to.
2. **DID Document**. For every DID We will have a DID Document containinng the basic information the entity needs to A&A.
3. **ID Container**. Every entity will have a container holding all its data.
4. **Smart Contract**. This SC will become our Digital Twin in the Blockchain Platform. Once deployed, the resulting address of the SC will be part of the DID. 
5. **Keys** . List of Keys owned by the entity.
6. **Verifiable Claims** . List of Verifiable Claims.

So far nothing new :)

# 1. Architecture
Every entity will be linked to a SSI Node where her/his/its ID will reside inside one ID Container. It can be in a single user node, a pool of Ids (many ID containers in a node) or maybe a professional SSI Node with extra services (recovery, safe storage...).

This means that some nodes in the Blockchain network will be acting as Identity SSI Nodes, will store information and will be able to do some basic actions for the entity/ies, meaning these nodes will have an API to resolve some basic ID endpoints. All these SSI Nodes will be connected to each other.

![Schema](https://github.com/WebOfTrustInfo/rwot8-barcelona/tree/master/topics-and-advance-readings/media/architecture.png)


## 1.1. ID Container
Each Entity (one or many) in the Identity node will have an encrypted (and portable) sqlite file, the name of the database will be the DID itself and inside we are going to store (encrypted with the Public Encryption Key of the user) :

1. Wallet : Management Key for the Entity to update the Smart Contract holding Identity information. 
2. DID Document : Modified version of the DID Doc.
3. Keys : Public keys owned by the entity
3. Claims : Verifiable Claims.
5. Documents : docs sent by other entities and accepted by the user.
6. Dapps Info : extra information regarding other dapps.

> ID Containers inside SSI Nodes become the Inbox for contacts, documents, keys and claims for the entity

## 1.2. Portability

ID Containers will be easy to backup and/or move between SSI Nodes. Also with light nodes, Container IDs could even live in a Mobile Device. Any user could run a SSI Node with their container inside and at any tinme move it to a professional service.

## 1.3. Version 0.1 : Storing a JSON File as a Merkle Tree

Instead of having a list of Keys in one Smart Contract in the Blockchain (ERC725) or a list of claims (ERC735) I propose to store only the Merkle Root of the lists, and provide with the necessary endpoints to show keys and verify claims. **Most of the actions will happen off-chain**.

This way when asked about a particular leaf of the tree we can show specific information and prove its validity without compromising the hash of any other field.

## 1.4. Version 0.2.

In a next stage, instead of storing Merkle Trees, we will use Zero Knowlege Proofs (zk-Snarks): The basic idea is to assign a Prime number to each Hash and then create a ZKP circiut with the multiplication of all these numbers (See more info here).

In both versions, v0.1 and v0.2 we will refer to the value resulting as Root : Keys Root and Claims Root.


## 1.5. Identity Smart Contract (IDSC)

For each ID Container (entity) we will deploy one ERC725 Smart Contract and one DID Document on IPFS.

We are following the new [ERC725 alliance specs](https://github.com/ERC725Alliance/erc725) where:
1. ERC725 is a Proxy contract holding d arbitrary data through a generic key/value store. Owner is stored at at key 0x000...
2. ERC734 is a list of Keys.
3. ERC735 is a list of Claims.

For our Identity we need:

1. Identity Management. How to update the SCID, who can do it. There's a Management Key that could be an account or another Smart Contract, so  we could easily change to a more sophisticated Base Contract (RBAC) with roles and permissions (we could separate DIDs Management and Claims Management). We will store the owner at key 0x0000.

2. DIDs management. IPFS address of the Did Doc where the Public-Public Keys are. We will use hash('did') as key.

3. Private-Public Keys. a Merkle Root or a zk-Snark contract. No Private information is ever shared in the Blockchain. We are not sharing any information about our keys but we can prove at any time that we own them. This way we can also group Keys by using a diferent key to store it :hash('keys1'), hash('login-keys')...

4. Claims Management. List of Claims isued by the entity. For the same reasons, instead of storing a list of claims (like in the ERC735 proposal), we will save in the contract the Claims Merkle Root (or kz-Snark). This way we can also group Keys by using a diferent key to store it :hash('claims1'), hash('personal-claims')...

# 2. Personal Information

## DIDs, Keys, Claims, Contacts, Documents and Dapps.

On this first version we will allow Identity Nodes to act as APIs, so they will be able to answer questions about the identity (claims, docs...). But then I need to link an IP address to a particular ID (less privacy).

We could will build a P2P network based on Libp2p to be able to send and receive messages to a particular DID without knowing where the DID is located (its IP address), but that would flood the netork with too many messages. Also Whisper looked like a good idea (We still think it is) using a topic just for Identity.

All communications with another DID will be sent with its ID container and encrypted with the public key of the destiny entity.

Before any information oculd be shared a Contact Handshake must be done. During this process, both entities agree on stablishing a Secure Id Channel between both.

For each channel (entity we are connected to), the Container ID will store the permission allowed for each claim, document and key.

## 2.1 DID Document.
We will start with a basic implementation of DIDs.

```json
{
  "@context": "https://w3id.org/did/v1",
  "id": "did:ala:123456789abcdefghi",
  "publicKey": [{
		"id": "did:example:123456789abcdefghi#login",
		"type": "RsaVerificationKey2018",
		"owner": "did:example:123456789abcdefghi",
		"publicKeyPem": "-----BEGIN PUBLIC KEY...END PUBLIC KEY-----\r\n"
	},
  {
		"id": "did:example:123456789abcdefghi#encryption",
		"type": "RsaVerificationKey2018",
		"owner": "did:example:123456789abcdefghi",
		"publicKeyPem": "-----BEGIN PUBLIC KEY...END PUBLIC KEY-----\r\n"
	}],
  "authentication": [{
    "publicKey": "did:ala:123456789abcdefghi#login"
  }],
  "service": [{
    "id": "did:ala:123456789abcdefghi;did",
    "type": "IdContainerService",
    "serviceEndpoint": "/ip4/caelumlabs.com/user/1223"
  }],
  "created": "2018-10-10T17:00:00Z",
  "updated": "2018-10-12T17:00:00Z"
}
```
There are a few differences with the Original DIDs specs. The idea came after speaking with [Victor Bjelkholm](https://github.com/VictorBjelkholm) about the LibP2P (IPFS) proposal for [multiformats](https://multiformats.io/).

- [Multiaddr](https://multiformats.io/multiaddr/) is a format for encoding addresses from various well-established network protocols. It is useful to write applications that future-proof their use of addresses, and allow multiple transport protocols and addresses to coexist.

This file will be stored on IPFS. The address will be stored on the Identity Contract (ERC725)

## 2.2. Private Public Keys

At the Identity Node we will store a list of all the keys belonging to the entity (as a Merkle Tree or as a zk-Snark).  **Keys Root**.

At the Container ID, these keys will be stored (and shared when necessary) using this format. It can be used for Wallets where we don't want anyone to relate the balance in an ERC20 contract and our DID.

```json
"publicKey": {
    "type": "Ed25519VerificationKey2018",
    "id": "did:ala:123456789abcdefghi#keys-1",
    "owner": "did:ala:123456789abcdefghi",
    "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
  }
```

## 2.3.  Verifiable Claims

We'll use the [W3C Verifiable Claims Data Model and Representations](https://www.w3.org/TR/verifiable-claims-data-model/) Spec
- **entity**: A thing with distinct and independent existence such as a person, organization, concept, or device. 
- **subject**: An entity about which claims may be made. 
- **claim** : A statement made by an entity about a subject. A verifiable claim is a claim that is effectively tamper-proof and whose authorship can be cryptographically verified. Multiple claims may be bundled together into a set of claims.

We will start with self signed Verified Claims.

```json
{
  "@context": "https://w3id.org/security/v1",
  "id": "did:ala:1234...#claim-1",
  "type": ["Credential", "ProofOfAgeCredential"],
  "issuer": "did:ala:8881111...",
  "issued": "2018-10-01",
  "claim": {
    "id": "did:example:1234...",
    "ageOver": 21
  },
  "signature": {
    "type": "LinkedDataSignature2015",
    "created": "2016-06-18T21:19:10Z",
    "creator": "did:ala:8881111...#key-1",
    "domain": "json-ld.org",
    "nonce": "598c63d6",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+
    MCRVpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wps
    PRdW+gGsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed
    +W3JT24="
  }
}
```

Here an issuer (did:ala:8881111...) is verifying with a public key owned by the entity (did:ala:8881111...#key-1) available at the DDOC, that one persona (did:ala:1234...) is over 21. The Id of the claim is did:ala:1234...#claim-1

All the claims will be used to build the Claims Merkle Root or the zk-snark : ** Claims Root**

In this proposal Claims work in one direction only. Issuer is the responsible to create a Claim, send the claim to the entity he's claiming something about and then updating the Claims Root in its own Smart Contract.

Revocation is as easy as deleting the hash of the claim from its own Claim Root.

## 2.4. Contacts

Before asking for any information about another entity we need to stablish a Secure Id Channel netween both entites. Any communication in this channel will be encrypted using the Encryption Key avaliable at the DID Document. 

To stablish a contact both entites must verify their own identities first and agree on the creation of the channel. Once the Channel is ready I can ask for a Claim, a Document and/or a Key : Shares.

Information will be shared when:
1. Entity (verified) asks for a Key, a Claim or a Document.
2. Which Information is required : Name, Proof, Document....
3. How the data is going to be used (how and what for)
4. For how long

The contacts will be stored on each Id Container.

## 2.5. Documents

The Id Container will act as an Inbox for certified documents.

First we need to stablish a Secure Id Channel, and after that I can request to put or get a document. All the documents will be stored in the Id Container.

Example : I make a payment to an ERC725, and the entity sends me an Invoice for that payment to my Id Inbox for documents. 

## 2.6. Dapps

Any Dap can use the Id Container to store personal information of the user.

# 3. Recommended readings

- [SSI by Christpher Allen](http://www.lifewithalacrity.com/2016/04/the-path-to-self-soverereign-identity.html)
- [Decentralized Identifiers (DIDs)](https://w3c-ccg.github.io/did-spec/)
- [Verifiable Claims](https://www.w3.org/TR/verifiable-claims-data-model/)
- [DID Auth](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-spring2018/blob/master/final-documents/did-auth.md)
- [IPFS](https://ipfs.io/) & [LibP2P](https://libp2p.io/)
- [Multiformats](https://multiformats.io/)
- ERC proposals : [ERC725](https://github.com/ethereum/EIPs/issues/725), [ERC735](https://github.com/ethereum/EIPs/issues/735), [ERC780](https://github.com/ethereum/EIPs/issues/780), [ERC1056](https://github.com/ethereum/EIPs/issues/1056) , [ERC1484](https://github.com/ethereum/EIPs/issues/1495)
