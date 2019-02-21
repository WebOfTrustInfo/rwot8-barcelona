# A Glossary of Terms for Rebooting the Web of Trust

### by Shannon Appelcline

__ACL:__ _Access Control List._ An authorization methodology where permissions are attached to an object as a list of who can access that object and in what way.

__Agent:__ A service or application that acts as a mediator between credential issuers, credential holders, and credential verifiers.

__Attestation:__ A statement of some fact (or some opinion) about some entity. Claim and Credential may be preferred synonyms due to [W3C's work on Verifiable Credentials](https://w3c.github.io/vc-data-model/).

__Attribute:__ Information about a digital identity.

__Authentication:__ The act of verifying an identity.

__Authorization:__ The act of verifying access permissions.

__Bitcoin:__ The cryptocurrency that invented blockchain technology and still the digital currency with the largest market cap. Focused on the purchase of goods and services.

__Blockcert:__ A blockchain-anchored credential that is decentralized and trustless.

__Blockchain:__ An immutable decentralized ledger maintained by consensus rules. In other words, a sort of online database that everyone can write to if they follow set guidelines.

__CA:__ _Certificate Authority._ An entity that issues certificates. Typically, a centralized authority/. 

__Capability:__ An authorization methodology where permissions are attached to an entity  as a list of what objects that entity can access and in what way. 

__Centralized Authority:__ A singular entity who has control over some system or process.

__Certificate:__ An identity credential. Typically, a public key bound to a name that is signed by some authority.

__Claim:__ An attestation about some entity.

__Credential:__ A set of one or more claims about the same entity, which might also include other information such as identifiers, proofs, or other metadata.

__Cryptocurrency:__ Digital currency protected by cryptographic algorithms. 

__Cryptography:__ Mathematical processes based on one-way functions that convert a message from a plain-text form to a coded form (and vice-versa).

__DAD:__ _Decentralized Autonomic Data._ Self-regulating or self-managing data that does not reside with a single party, supporting the identification, certification, and securing of streaming data that is processed in a distributed manner. See also ["Decentralized Autonomic Data (DAD) and the Three R's of Key Management"](https://nbviewer.jupyter.org/github/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/DecentralizedAutonomicData.pdf).

__Data Minimization:__ The act of limiting shared data to the minimum necessary.

__DID:__ _Decentralized Identifier._ A portable, globally unique identifier associated with some entity that does not require a centralized authority for registration. See also ["A Short Primer on Decentralized Identifiers"](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/did-primer.md).

__DID Document:__ A document that contains information related to a specific DID.

__DID Method:__ A regularized methodology for creating, reading, updating, and revoking a DID. BTCR, IPID, Sovrin, uPort, and Veres Ones are just a few DID methods.

__Decentralized:__ Distributed and not dependent upon any central authority.

__Digital Rights:__ The codification of authorization to use digital media.

__ECC:__ _Elliptic Curve Cryptography._ A method of public-key cryptography that depends on elliptic curves (y^2 = x^3 + ax + b) and how they behave in finite fields. They improve over classic RSA cryptography with their smaller key size.

__Entity:__ A person, organization, concept, or device.

__Ether:__ Currently, the third-most valuable cryptocurrency, the "fuel" for the ethereum platform. 

__Ethereum:__ A distributed computer blockchain focused on smart contracts that uses Ether.

__FIDO:__ An authentication method for secure two-factor authentication, managed by a hardware key.

__GDPR:__ _General Data Protection Regulation._ European laws that protect the data and privacy of individuals and that place restrictions on how others can use that data. 

__Holder:__ Someone who possesses credentials, usually (but not always) the subject of the credentials.

__Hub:__ A datastore where objects are signed by a digital identity and accessible through unique global identifiers. See also ["Hubs"](https://nbviewer.jupyter.org/github/WebOfTrustInfo/rebooting-the-web-of-trust-fall2016/blob/master/final-documents/hubs.pdf) and ["Identity Hub Attestation Flows and Components"](https://nbviewer.jupyter.org/github/WebOfTrustInfo/rebooting-the-web-of-trust-spring2018/blob/master/final-documents/identity-hub-attestations.pdf).

__Identifier:__ A proxy for identity that's used as a label to refer to the entity. For example, a name or UID.

__Identity:__ A somewhat nebulous term, defined in different ways by different people. Broadly, it's who or what an entity is.

__Identity, Digital:__ A digital representation of identity.

__Identity, Functional:__ A model for identity that says, "Identity is how we keep track of people and things and, in turn, how they keep track of us." See also ["A Primer on Functional Identity"](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/functional-identity-primer.md).

__Issuer:__ Someone who asserts claims and issues them in credentials.

__Key:__ A cryptographic secret used to encrypt or decrypt data. In traditional symmetric cryptography, the same key was used for encrypting and decrypting. In public-key cryptography, a private key is used for encrypting (and signing) while a mathematically related public key is used for decrypting (and verifying).

__PGP:__ _Pretty Good Privacy._ A classic program used for encrypting, decrypting, and signing data. The origin of the Web of Trust, which was designed as a method for determining the trust of public keys, as an alternative to a centralized public-key infrastructure.

__PKI:__ _Public-Key Infrastructure._ A methodology to ensure the creation, storage, distribution, and revocation of public keys.

__Private Key:__ Half of the keypair in public-key cryptography. A secret that's used to encrypt and to sign.

__Public Key:__ Half of the keypair in public-key cryptography. A publicly distributed key that's used to decrypt and to verify signatures.

__Public-key Cryptography:__ A cryptographic process that uses two mathematically related keys, one to encrypt a message and one to decrypt a message; one key (the public key) can be derived from the other key (the private key), but not vice-versa.

__Repository:__ A wallet (or other storage area) used to store personal credentials.

__Reputation:__ A system for measuring the behavior of entities.

__Revocation:__ The act of cancelling digital identity data such as a DID or private key.

__Ripple:__ A real-time payment and settlement system designed to bridge transfers between different sorts of money using the XRP cryptocurrency. Although it uses a distributed consensus ledger, it is not a blockchain.

__Selective Disclosure:__ A method of sharing information at a granular level, such as revealing some claims but not an entire credential. See also ["Engineering Privacy for Verified Credentials"](https://nbviewer.jupyter.org/github/WebOfTrustInfo/rebooting-the-web-of-trust-fall2017/blob/master/final-documents/data-minimization-sd.pdf).

__Signature:__ A means for verifying the authenticity of a message or transaction by signing it with a private key; the signature can then be verified with a public key.

__Smart Contract:__ A digital program, often associated with the transaction of cryptocurrency funds. Neither smart nor a contract.

__SSI:__ _Self-sovereign identity._ A decentralized, portable digital identity that does not depend on any centralized authority. See also ["The Path to Self-Sovereign Identity"](http://www.lifewithalacrity.com/2016/04/the-path-to-self-soverereign-identity.html).

__Subject:__ Someone who is the subject of claims.

__Trustless:__ Requiring no trust. A process that is designed such that its rules ensure that all of its participants must act fairly. Usually part of a decentralized design.

__Verifiable Claims:__ The original name for Verifiable Credentials.

__Verifiable Credentials:__ A tamper-evident credential, per the [W3C Data Model](https://w3c.github.io/vc-data-model/). See also ["A Verifiable Credentials Primer"](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/verifiable-credentials-primer.md).

__Verification:__ The act of proving the accuracy of something, often verifying a digital signature.

__Verifier:__ Someone who verifies credentials.

__Wallet:__ A digital means to store private keys and their associated public keys. The term comes from cryptocurrency wallets, which store the keys associated with cryptocurrency transactions, but there are also identity wallets, which store keys related to digital identities.

__Wallet, Hardware:__ A hardware gadget that acts as a wallet. Often, a Ledger or a Trezor.

__Web of Trust:__ A method for assessing trust based on peer-to-peer processes. More broadly, an area of digital development that focuses on decentralized identity.

__XRP:__ Currently, the second-most valuable cryptocurrency, owned by Ripple. Created as a high-speed bridge currency that eliminates exchange fees.

__Zero-knowledge Proof:__ A cryptographic method where someone can prove that they know some information without revealing the information.

_Some inspirations for terms and for the words used to describe them drawn from [Verifiable Claims Terminology](https://w3c.github.io/vc-data-model/#dfn-verifiable-presentations)._

_If you have any disagreements on definitions on which to include additional terms, please enter a PR._
