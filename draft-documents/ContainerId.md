# Identity Containers

-----------------------------------------------------------------------------------------------------

Alex Puig - Caelum Labs - alex@caelumlabs.com

Oleg Burundukov,  ING bank, blockchain team   - [olegwb@gmail.com](mailto:olegwb@gmail.com)

Miguel Fernando Jimenez Sola - Yoti - blockchain team - [miguel.jimenez@yoti.com](mailto:miguel.jimenez@yoti.com)


## Abstract

We propose the implementation of self sovereign identity system based on public blockchain. The functional scope of the system includes credential issuance and verification where different algorithms can be employed for this purpose. The system does not follow a particular standard for verifiable claims. Instead, it  accommodates non-interoperable credentials into the identity container. The system is designed to be eIDAS and GDPR compliant, providing the confidentiality for personal data as well as the non-repudiation for the execution of the right to erase. We propose using only zero knowledge proofs for the validations. We also argue that the interactions where data are shared may require the new role of a notary added.  While the prototype is built on IPFS and Ethereum blockchain using ERC725 v2 standards, the architecture is seen to be ledger agnostic.


## Summary 

We propose to store just a Merkle Root of the keys and claims being holded by an entity (user, organization, etc.) and set a list standard endpoints to query and interact between entities. This way most of the information is transferred off-chain and the whole system should be GDPR compliant. We use ZKP to validate things.


## Introduction

We propose open-source platform for Self Sovereign Identity featuring properties of decentralized public identity network. The platform facilitates the creation of verifiable credentials in the portable format. The platform uses the blockchain technology as the decentralized public data infrastructure. We introduce the notion of identity container where the portable artefacts of SSI are stored. The identity container comprises  



*   DID documents
*   Keys
*   Verifiable credentials
*   Trusted Contact

The platform employs zero-knowledge proof techniques  for:



*   The validation of the possession of a key
*   The validation of the issuer's signature in the verifiable credential 
*   The validation of the relation between keys and DIDs


## Use cases



*   Building your own identity as a person or organisation
*   Creating new Identities controlled (owned) by yours
*   Creating secure P2P channels between Id Containers.
*   Creating verifiable credentials (Proofs)
*   Using the credentials to authorize against web services.
*   Share the verifiable credential with a third party
*   Issue the receipt of the successful transmission
*   Revoke the verifiable credential



Architecture


### 

![alt_text](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/draft-documents/ContainerId/schema1.png "image_tooltip")


Identity Smart Contract

Each ID Container is represented in a ledger by the ERC725 Proxy contract. According to latest [ERC725 alliance specs](https://github.com/ERC725Alliance/erc725), ERC725 can hold arbitrary data through a generic key/value store. The owner of the contract is stored at key 0x0000.

A list of ZKP keys is held in ERC734 format, and the list of credentials is held in ERC735.

No private information is ever shared in the Blockchain, but the proof can be made  at any time that the owner of DID owns other items. Keys in ERC725 can also be grouped.

Verifiable credentials are managed in similar way , so that list of them issued by the other entities is stored in the private part of the container, while the  Merkle root is stored in the keys ERC725 grouped in convenient way. For example keys can be grouped by the purpose:   :hash('claims1'), hash('personal-claims') etc.

The proxy contract is supposed to hold ZK proofs of possession of keys or DIDs other than master key and DID of the user too.


## Create and Share Claims


![alt_text](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/draft-documents/ContainerId/schema2.png "image_tooltip")



## Non-repudiable interactions

The protocol of the interaction of two parties where both parties issue the receipts of successful termination is rather challenging to design. It has been argued that such protocol is inefficient end error-prone in absence of trusted third party. We propose the addition of the notary actor into the proof verification scenario.  The Notary should not be involved in every interaction  due to the optionality of  the receipts exchanged.

The non-repudiable protocols designed so far use common technique where the data are shared in encrypted format first. The decryption key is shared after designated receiver of data issues the receipt confirming the sharing. 

Main problem with sharing a key emerges with the requirement to maintain a public service entry point  by  the party, either Prover or Notary, depending on the version of the protocol. Having in mind the anonymity of the Prover, and the fact  that a Prover likely operates the SSI application on a mobile device, we conclude that running key service on the side of a Prover becomes great challenge. We argue that the versions of  non-repudiation protocol where the key is generated by a Prover but shared by TTP ( Notary) remain the only realistic ones.

We shall see that if the Notary shares the decryption key using publicly available service, such as Web server,  the Notary must be able to prove  that the key was obtained by Verifier. It can be achieved by few techniques, for example, the recording of the identity of  a reader during each reading operation, which ,in turn, requires the reader to use his/her identity when transacting with key storage.

 Once the chosen Verifier accomplishes the reading of the key, Notary considers the protocol finished and sends the confirmation to the Prover.

Note that  hosting keys in public storage can result in revealing the weaknesses in underlying cryptographic schemas, therefore we argue that Notary has to restrict the access to the key before publishing by encrypting it with trusted public key of the Verifier.

We can see that  using a notion of smart contract on the distributed ledger for holding keys and for capturing the event may resolve  aforementioned problems. Smart contract  is able to check its caller's identity, therefore the contract should be able to write yet another change into the ledger, namely the receipt of reading the key by designated Verifier. This evidence is very strong for the purpose of RTE, and it remains publicly available and verifiable. However we also see that the desired functionality is not supported by Ethereum smart contracts. 

Another option for the storage of temporary key can be HSM as a service. HSMs support holding cryptographic artefacts and facilitate selective disclose of them on the base of the identity of a reader.

  

Two other important properties of non-repudiation protocol are unique labelling for each message and time limits for waiting for next message. The former is required to identify each step in the protocol, and the latter makes provision for the eventual termination.

Note that using  ZK proofs for partial disclose solves entire problem in case the data  disclosed in clear text is not qualified as personal. We also argue that stored ZK proofs have to be qualified first by the law as objects not falling into the data categories protected by the GDPR. 

We conclude that the responsibility and the choice  to opt for full non-repudiation protocol or to restrict shared data is up to the Prover,  according to the the interpretation of what personal data are.  

  


## To be added



*   _Add Secret Storage_
*   _Add HSM (Hardware Security Module)_
*   _Proofs (acknowledges) with lifetime_
*   _eiDas & GDPR compliance_


## Conclusions

No easy solution for non-repudiation protocol without the interaction with a Notary,  a trusted third party. 


## Further readings



*   [SSI by Christpher Allen](http://www.lifewithalacrity.com/2016/04/the-path-to-self-soverereign-identity.html)
*   [Decentralized Identifiers (DIDs)](https://w3c-ccg.github.io/did-spec/)
*   [Verifiable Claims](https://www.w3.org/TR/verifiable-claims-data-model/)
*   [DID Auth](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-spring2018/blob/master/final-documents/did-auth.md)
*   [IPFS](https://ipfs.io/) & [LibP2P](https://libp2p.io/)
*   [Multiformats](https://multiformats.io/)
*   ERC proposals : [ERC725](https://github.com/ethereum/EIPs/issues/725), [ERC735](https://github.com/ethereum/EIPs/issues/735), [ERC780](https://github.com/ethereum/EIPs/issues/780), [ERC1056](https://github.com/ethereum/EIPs/issues/1056) , [ERC1484](https://github.com/ethereum/EIPs/issues/1495)

<!-- Docs to Markdown version 1.0β16 -->
