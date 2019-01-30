# Digital Trust Protocol
C. Keutmann & T. Pastoor  
DigitalTrustProtocol.org  
postmaster@digitaltrustprotocol.org

## Abstract

The Digital Trust Protocol (DTP) is a solution for the handling of trust in the digital space. The protocol is broadly designed to work with all aspects of trust; this includes identity, reputation, and security.

The protocol is designed to be independent of specific systems and is very minimalistic. The intention is to extend the protocol with layers above rather than direct implementations. The protocol claim message data is designed to be self-provable of authenticity, by use of private/public key algorithms and the blockchain timestamping feature. This enables the protocol to be decentralized without a need for central authority, as servers can use a peer-to-peer communication system and verify all the data it receives individually, without having to rely on the sender.

The Protocol allows anyone, including automated software, to issue their own cryptographic identities, for the use of trust and reputation and be able to verify those of others, without the need for a trusted third party. Users issue claims to other identities, and this way build a personal web of trust network.

Users can search for claims on subjects by use of the user's trust network. The search only include results from trusted sources, claims from untrusted sources are not returned. The system is resistant to attacks like Sybil and bot networks as they are usually not a part of the uses networks and therefore not considered when evaluating searches.

The system works on the incentive of the user’s reputation and established trust, to be a good actor within their networks, since no one will listen to them if no one trusts them.

It is possible to trust anything digitally, and therefore the protocol suitable to be used for anything that requires some degree of trust shared between systems related or unrelated. The DTP protocol is ideal for identity, reputation and security management that needs to be used in a broader sense without a central authority and furthermore it can augment existing systems already in place.

## Introduction

Trust in the digital world of today are mostly centralized and siloed. Many reputation systems only work on specific platforms. There are usually no sharing of trust and reputation between the platforms, and this makes it hard to keeping track of identities reputation across systems. Many platforms do even not have any form of reputation system in place, like many forums, news sites and so on. Therefore keeping a personal record of each identity on many different contents providing platforms becomes a time consuming and near impossible task, as the identity of the same person may differ from platform to platform.

Many existing solutions only offer a specific kind of trust, like reputation and have no possibility for diversity in expressing the kind of trust a user may have of an identity or item.

The Digital Trust Protocol (DTP) is designed to provide an open protocol for the handling of trust of any kind in the digital space, in a decentralized way. DTP is a decentralized web of trust protocol.

The DTP system works on the assumption that it is harder to gain trust than to losing trust. This is the basis for the system to function properly, as it creates an incentive for a user to act appropriately to maintain the reputation. Steadily losing trust will most likely result in loss of attention and influence.

A simple definition of trust is it is an expression of a belief or experience that a certain identity will act in a repeatable or predictable pattern. Simply DTP defines trust as proof of a predictable, repeatable pattern, and that is subjective to the observer. This simple pattern enables development of relatively simple rules that are easy to implement into autonomous programs, and by these rules, they can issue trust on their own.

Identity in DTP is based on trust. Identity is something that is internal and external. The internal identity is about self-realization and is not the subject of the DTP protocol. The external identity is properties like name, age, birthplace, citizenship, and other recognizable properties. They are all claims given by others. Usually, a state authority recognizes its citizens by name, address, identity number, and other credentials. Verifying the identity of a person is to use a trusted authority as a source for the claims, and not only to rely on the subject. In DTP external identity properties are provided by claims from others, not from oneself. Just like it is not possible to issue a valid driver license to yourself at home without any authority involvement. In DTP an authority can be any entity, like the government, companies, organizations, and friends. However, the authority still has to be recognized by others to have any relevance when asking for trust.

Security is claims given to an entity. Therefore the DTP can act as an access control system for identities across platforms. A claim can act as a simple ticket claim for specific an event, issued to a specific identity, thereby preventing reselling. Claims also include time properties to handle when the claims are active.

Rating is claims specifying a specific value for an entity. It is possible to issue rating claims to specific items like a car or printer. However, cars and printers are not able to issue a public identity for themselves. Therefore the name or a serial number of the item can be used to generate the identity address of the item. Because there was no private/public key generation involved in the process of generating the identity of the item, nobody can issue claims on behalf of an item.

It is possible to trust anything digitally and therefore the protocol suitable to be used for anything that requires some degree of trust shared between systems not related and without the need for any central authority.

DTP protocol defines a simple piece of data called a claim message. The claim message data is designed to be self-provable of authenticity by use of private/public key algorithms and the blockchain timestamping feature, and this ensures that nobody else will be able to issue the same claim message without the private key used to sign the message. The timestamp feature ensures that the claim can prove its existence at a specific time, thereby preventing backdating claim messages.

The self-provable authenticity feature of a claim message enables decentralization without the need for central authority, as servers can use peer-to-peer communication and still be able to verify all the data they receive, without having to trust the sender.

The DTP servers that host the DTP web of trust networks are based on the claim messages. They serve users requests to solve the queries on different subjects and targets. The servers can be public or private and still share data with anyone. The DTP servers can focus on specific claim types or host broader networks. The protocol for sharing of data between servers is not a part of the DTP protocol as this is considered a layer on top of the DTP protocol. Because the claim message is self-provable authentic, the servers can be sure that no matter how they got the data, it is verifiable against tampering. Per default the claim messages are not encrypted, only signed by the issuer, making the claim readable by anyone. When claim messages need to be private and secret, they do not need to be encrypted, as the claims are stored on closed servers and not publish however, others can still trust the public key of a closed network, enabling self-sovereign identity management, as it makes it possible to prove chain of trusts without exposing more details than needed.

## Architecture

The DTP protocol specifies generic data structure and a rule set for searching on these data in a specific way. The data structure does not specify the algorithms for calculating the private/public keys, signing scripts and hash values for ID’s, this is up for the implementation of the protocol.

The system consists of a client-server model, together with a clearly defined data structure. The generation of cryptographic key-pairs, and signing messages usually happens on the client. The messages are sent to a DTP server of choice, that timestamps each message and constructs a trust graph from all collected messages.

The DTP protocol focuses on defining a common data structure and how to search on the data, but does not limit the types of trust and algorithms used to sign the trust.

Event Sourcing is the base data pattern of the DTP protocol, where each claim defines a property change. The claim only defines a single atomic value for a single target from a single source, and are extended with a number of properties like scope and time. The principle of only changing of atomic values makes it easy to maintain the data in a decentralized way because it does not require previous knowledge of the state of an object. Bundling multiple claim values like Name, address, email into a single claim, introduces a higher complexity of implementation without any significant benefits. The claims are always bundled together into a package with the possibility of signing all the claims in one go before submitting it to the DTP server.

### Claim

A claim message is a relatively small piece of data with a flat data structure that is self-provable authentic and defines a single value issued to a subject. After a claim message is created, a hash ID is calculated and then signed by the issuer. Usually, the timestamp is added by the DTP server. A claim message needs to contain at least the issuer signature and a timestamp, for other DTP servers to verify that the received claim message is valid.

Claim messages can be of any type, and therefore the DTP protocol specifies a basic set of claim types for standardization purposes.

When issuing and signing claims, the signature can be base on a simple private/public key algorithm principle, or it is also possible to provide a script with multiple signatures for the claim. It is also possible to provide any custom non-standard script/type if needed, but then this has to be supported by any DTP server that serves the claim in its web of trust graph.

The value part of the claim defines a statement towards a subject. The value is what the issuer thinks of a subject. For simplifications, it is not possible to add more than one value per claim. Issuing multiple values to the same subject is done by issuing multiple claim messages. The single value per claim enables the system to update or replace individual claims with new ones as the need occurs. Updating or removing claims happens by issuing new claims messages to the same target with a new value or an empty value to simulate removal. The package that contains the claims, features techniques to enable single signing and templating for mitigating the bloat of having to issue multiple claims of the same type towards the same subject. It's possible to extract individual claims out of the package and add them into new updated packages and still keep the proof of authenticity with each claim. This way old replaced claims can be discarded and existing and new claims a combined into new packages before sharing.

It is possible to add a signature to the subject part of the claim message, proving that the issuer is also in control of the subject. This enables the DTP servers to change the behavior of the search algorithms used for finding trusts and enable features like tunneling for key management.
The claim message can have an activation and expiration date, enabling them only to be active at certain times. A use case would be that the trust is used as a ticket system or to provide secure access to systems for a limited time.
Claim messages contain a scope property for limiting the context of the claim, as the claim given to specific web platforms may not be relevant on other platforms. This is very beneficial to limit the amount of trust hosted on a DTP server. A claim message is hosted in a package when submitted or transported around.

Example of a claim package

    {
      "algorithm": "double256.merkle.dtp1",
      "id": "xSJLFeSNTYn4AHjvbz4rCh7AFz1ZJyFwZW1M8GJy3g4=",
      "created": 1548757308,
      "claims": [
        {
          "id": "Lp2+ebZ9U0LRv/Z/xnx8pPVhbkRdoyscsdcY+n+StaI=",
          "created": 1548757166,
          "issuer": {
            "type": "secp256k1-pkh",
            "id": "1LRNDp2HfVKc1FsCJwbJwMhtssXL8fdTx2",
            "signature": "H0+9PhNSxm6ySMShlkuC1ZCTuYdbxSHquP1KCmb/M4LxZwOSFoHUy+fHcZiiI/zjheVJvrQbM/1X4Eg6+wTx3N0="
          },
          "subject": {
            "type": "name",
            "id": "TrustProtocol"
          },
          "type": "binary.trust.dtp1",
          "value": "true",
          "scope": "twitter.com"
        },
        {
          "id": "3atbj7U7RMSfL8OQFaGDzYlpGRbpnm3kHItMzFXLjMk=",
          "created": 1548757166,
          "issuer": {
            "type": "secp256k1-pkh",
            "id": "1LRNDp2HfVKc1FsCJwbJwMhtssXL8fdTx2",
            "signature": "ICWN+jH6Gn8+c7FJ0rSk3SPRmRI97FiXVtEdnm2S0utJOpZaE+WqNDII1RhHwLDlgVxlyNFpkp7w3K+WCBJXhPg="
          },
          "subject": {
            "type": "id",
            "id": "1NKtqyDndSvQ87ANAHsWR5XGL66pXkZxc8"
          },
          "type": "binary.trust.dtp1",
          "value": "true",
          "scope": ""
        },
        {
          "id": "QlbmdW4R1Ctth4Ah4xIVNzcflhlyr4oFaZFtIASi9HA=",
          "created": 1548757169,
          "issuer": {
            "type": "secp256k1-pkh",
            "id": "1LRNDp2HfVKc1FsCJwbJwMhtssXL8fdTx2",
            "signature": "IPe6xOj4ofy1QWSB646AHvKPa7a7mk3ko6D/dKdk15jkVZ4wLt5ci1eCJrj2j4uWSM+JYFlVy+Z1Sa8LHMDNK8U="
          },
          "subject": {
            "type": "id",
            "id": "1NKtqyDndSvQ87ANAHsWR5XGL66pXkZxc8"
          },
          "type": "alias.identity.dtp1",
          "value": "Digital Trust Protocol",
          "scope": "twitter.com"
        }
      ],
      "timestamps": [
        {
          "blockchain": "btctest",
          "algorithm": "secp256k1-double256.merkle.dtp1",
          "source": "xSJLFeSNTYn4AHjvbz4rCh7AFz1ZJyFwZW1M8GJy3g4=",
          "registered": 1548757308
        }
      ],
      "server": {
        "type": "secp256k1-pkh",
        "id": "1LCGKp8zkmU3jBSdsRNfLzqsJH3qSzSxyk",
        "signature": "IBtutLOpiB5rcpgvSxdNbvB5OpVM5yp8t1dO3FVWvgPWdX+EvM3eQrfyBNeOQYil7K/xuzsgXYNYE7XjR/byhBo="
      }
    }

In the example above, three claims have been created and added to a package. The claims trust a subject named “TrustProtocol” and a subject with an ID “1NKtqyDndSvQ87ANAHsWR5XGL66pXkZxc8” and its alias of “Digital Trust Protocol”. These three claims are trusting the same entity on Twitter, where the entity has the public key “1NKtqyDndSvQ87ANAHsWR5XGL66pXkZxc8”, but also the twitter name “TrustProtocol” is trusted. Finally, an alias claim issued to the public key, connecting the key with an alias. Note that the scope property is empty for the claim that trusts the ID, this is because the trust is global and not limited to a scope. The server property in the package is created and signed by the DTP server receiving the claims from the client. This way other DTP servers can identify the source of the package. Lastly, the DTP server timestamps the claims by use of a publicly available blockchain to ensure that claims can prove their time of existence.

### Package

When DTP server shares claim messages with other DTP servers, they use a package to contain the claim messages; this enables them to create an array of claim they have received from users and timestamp them all at once by using a Merkle tree algorithm. DTP servers also sign the package with their own identity, enabling other DTP servers to be able to verify the origin of the package. By having DTP packaging and signing claims, it helps to confirm the existence of the claims, further enhancing the proof of the existence of the claims, because the claim message has now been seen by at least one DTP server and shared in a package signed by the server. The package includes a template property to reduce storage needed by providing shared templates for claims to use. Even key signing is supported within the template. It is possible to add multiple claims to a single package and sign the package once. The signature is based on the id calculated from a Merkle tree of all the id’s from the claims, and the timestamp works in the same way. This enables claims to be separated from their original package and added to other newer packages, but still be able to be self-provable authentic. The Merkle tree id feature enables repackaging of the claims into new packages as individual claims to get replaced, avoiding having to keep old replaced claims data with still active claims.

### DTP server

The DTP can have multiple roles in the DTP protocol, as they can act as a timestamp server and as a search engine for the DTP web of trust graph.

The timestamp role is to ensure that claim messages can prove their existence at a specific time. Furthermore, the server can package up the claim messages into packages that the server signs on its own, then sharing the package with other DTP servers, improving the claims proof of existence.

The DTP server stores the claim messages in a regular database and not on a blockchain. No blockchain is needed for storage as there is no need for a consensus of the state of the ledger because it is not possible to re-spent the same claim given to a subject on to other subjects; therefore the amount of trust that can be issued are endless. Only the timestamp feature uses a blockchain, and by use of the Merkle tree algorithm, it is possible to timestamp a large number of claim messages in one single transaction on a blockchain.

#### Web of Trust

The DTP web of trust graph role of the DTP server is to serve user requests on the user personal trust network. The claim message in itself is a plain value carrier, and therefore a graph structure is needed to be able to search through relevant trust based on a users perspective. A DTP server collects claim messages that are relevant for its users and build up a graph structure that is searchable.

The DTP protocol defines a standard search and result structure for search and result, and it also defines a standard set of rules on how to search through the web of trust graph regarding the perspective of the user.

A tunneling claim is where the issuer of a claim have signed both the issuer key and the subject key, thereby proving control of both keys. A tunneling claim do not enforce an incremental count of degree when calculating the search, but just follow through. It enables a deeper level of search beyond three degrees, and as the issuer usually only creates a few tunneling claims, it will limiting the number of claims to search through. A tunneling claim is suited for key management as a public identity with a private key highly secured and rarely used, can delegate trust to a daily key, by the tunneling claim. It makes it easy to have high security with convenient key management; this enables organizations to have a hierarchy of keys for divisions, departments, and employees. Trust issued by an employee can be linked all the way back to the organization's public key by a chain of claims, and therefore only the organizations public key has to be trusted when validating the proof of credentials, even that is was an employee that issued the credentials. This also makes it easy to replace keys when employees change positions or keys gets compromised.

A simple scenario of issuing trust and searching for it.  
![Issue of Trust](https://github.com/DigitalTrustProtocol/Whitepaper/blob/master/Images/DTP_image1.png)  
Client A issue trust to B and B issue trust to Client C  
  
![Search on Trust](https://github.com/DigitalTrustProtocol/Whitepaper/blob/master/Images/DTP_image2.png)  
Client A searches on Client C and gets the result from the DTP search server. The result contains the trust from A to B and the trust from B to C.

It is up to the client to decide how to interpret the search result as the may be multiple results on from different identities having different opinions. Therefore the server presents the data, and the client handles it from there on.

Some basic rules of the search engine are that searches never go further than 3 degrees away from the user, as this quickly become irrelevant the further out in the network the search goes. Another rule is that the only result from the same degree is returned and the search does not continue further onto the next degree when a match is found. Only trusted identities on the network are followed and distrusted identities are ignored.

The chains of trust are the basics of the system, as they enable for verification of proof of identity credentials by following the trust chains generated by authorities.

**The network of DTP servers and scalability**

The usability and value of a web of trust network increase with more users join the system. The DTP system is designed to scale up to a very high number of identities and claim messages supporting a global implementation. The nature of the claim message is that they are self-provable authentic and therefore the DTP servers do not need to rely on a central authority but can share the data directly in a peer to peer network. The DTP protocol does not specify the communications between servers as this is regarded as a layer on top of the DTP protocol.

The DTP server may offer different scopes for trust services; therefore the trust messages include a type and scope properties to help to filter and limiting the trust before it is verified and included in a servers DTP web of trust graph.

A claim message is designed to be very small usually under one kilobyte; therefore the properties of the claim naturally have a limited size. The small size helps claim messages propagate quickly through the system and limit attack surfaces.

It is estimated that it is possible to have DTP search servers with reasonably low cost that can handle web of trust graphs containing millions of identities and trusts with effective memory management. Servers can become more specialized and limiting the type and scope of trusts as the networks get larger. It is possible that the clients will have a list of dedicated DTP search server for different scopes of trust and choose the right server in the right context.

### The client
The client issues trust and interpret the search results from the DTP server. It is up to each client to decide how to read the search result as this may have a different meaning in different scenarios.

When using the DTP protocol, the client does not need to provide an identity to be able to use the web of trust graph. Anonymous users can rely on other established identities and use their networks, this could be friends or well-known entities like online search engines, and security firms specialized in web security.

However, without a personal DTP identity, it is not possible for others to trust the identity and establish a personal web of trust network.

**Key management**
The issuer of trust uses a private/public key algorithms to generate an identity in the form of a public key and to sign the claim messages. However, it is also possible to use a script like languages for multi signatures for proving ownership. After a daily session of issuing claims, they would be bundled into a package and signed by a possible hardware device before submitting to a DTP server. This gives a very high degree of security of the private key and avoids having to sign every claim individually. The subject of a claim message can be signed as well, enabling optimization of the DTP search engine.

For strong key management, a subject signing technique is used for replaceable identities. A person can create a highly secure key and publish the public key for others to trust. Then create a less secure private key for daily use, that is trusted by the highly secure key. The claim message contains a signature for both the issuer (high secure key) and subject (daily key). A DTP search server regards this as a tunneling claim and channel through it without increasing the degree. This way if the daily key is compromised, it can be replaced by a new daily key and trust network copied. This happens by distrusting the old daily key and trusting the new daily key. After propagation, all DTP search servers ignore the old daily key and use the new daily key. From others perspective, it looks that the web of trust network is unchanged as they use the highly secure public key, that routes through to the new daily key.

## Identity
The identities on the DTP system is based on private/public key algorithms, creating a pseudonymous identity. Connecting a users personal information to that identity is done by others issuing claim message to the identity. One can claim information about oneself, but this may not be considered in the DTP search rules and therefore not show up in search results. Because claims about one's identity are given by others, like the government, company or friends, it is possible to present proof of identity without revealing more information than needed. A government issues trust to an identity with the claims like name and birthday. This trust is however not shared publicly but kept securely private on government servers. However, the government can issue proofs of the trust, like over a certain age and so on. The government has published a general public key, that others can trust in their networks. So now when for example proof of age has to be presented, then a search on the identity with the query for a certain age can be issued. The result is a chain of proof from the government to the identity, proving that the chain is valid. Anyone that trusts the government public key can now verify and accept the proof of a certain age because the chain of claims is valid all the way from the verifier to the subject, though the government. A subject can choose to store the chain of proof locally and present this whenever needed, avoiding any search on a government server in the case of verification. Multiple different proofs can be stored locally and only present the necessary ones without exposing more data than needed. As the proofs only state a fact and not the value itself, then the concerns for storing the data securely can be more relaxed.

Searches on information on identities held by the government can be limited to only allowing the identities to make queries about them self, prevent information phishing.

Items do not have an identity and therefore cannot issue trust by themselves. Trusting items can be done by using a unique value of the item, as a source of identity. As the identity is generated from a hash value of the unique value source, it is not possible to issue trust on behalf of that item, only receiving trust is possible.

## Incentive

The system assumes it is generally harder to gain trust than to lose trust, both for humans and machines. This gives the users an incentive to guard their trust highly, as they otherwise may lose attention, influence, and opportunities. The trust network is based on a subjective viewpoint, as each subject has individual preferences of trust in others and items.

By assigning trust to everything that is possible to represent digitally; it becomes possible to leverage on the viewpoints and opinions on everything from trusted sources, this enables users to get information about entities that will help to make decisions about that entity. Imagine news articles flagged for their trustworthiness, products in a supermarket trusted for their quality, and the car mechanic rated for services, all within a single users personal trust network.

For an entity to keep trust already gained, creates an incentive to avoid bad behavior and keep up its predictability, this also applies to DTP servers to avoid being selective in hosting and sharing trust for uses, as this otherwise leads to distrust of the server and ultimate losing its customer base. Therefore the distribution, sharing, and searching for trust, rely on this incentive.

**Potential Attacks**

The strength of the system is that it is subjective and the trust is self-provable authentic. This makes it hard to perform attacks where a massive number of claim messages are issued from a bot network, trying to influence a specific subject. Because it only has a minimal effect for the users of the system besides taking up resources, as nobody trusts the spam in the first place and therefore the spam will no influence the user's networks of trust. Entities trusting the spam can quickly be identified and distrusted if necessary to close of the spam from the personal network.

The prediction attack is from users trying to make predictions by creating a million ‘guessing’ messages and not / barely share them, to make it seems that the issuer has created a correct trust when presented in the future scenarios. This can be countered by looking at packages containing the trust when trusts are published on a DTP server, they are time stamped and package into a Trust packages that in return are signed by the server and then shared with other servers. If no packages with the trust in it, can be found on any servers, then the trust may seem not to be shared publicly and therefore may have limited historical value. Furthermore, if the identity behind the prediction has a minimal history one may assume that it has been fabricated to this scenario.

The excluding trust attack is when a DTP search server selectively chooses not to include a specific trust for some reason, and therefore the search result still returns old or no claims on purpose. In this case, because of openly sharing of claims, enables them to be stored by multiple servers, and therefore reasonably easy to detect if a server has not included the latest claims by comparing data from different servers. When a server does not in a reasonably timely manner demonstrate a willingness to include specific claims, it can be distrusted by other servers and users, effectively render the server useless in a broader sense as nobody trust it anymore.

## Conclusion

With the rise of the Internet, the possibility to efficiently extend the contact surface with the rest of the world was a reality. However, this presented some problems as there is no general way to transform the trust from a near physical environment onto the digital space in a broader digital form. Merely keeping track of the trust of everybody is an overwhelming task. The solution is to leverage the trust of others trusted parties subjectively chosen and stored digitally. The DTP system aims to solve this problem by defining a protocol for sharing and searching on trust within subjects own space. The DTP system is designed to be very simple, lightweight, decentralized and open source. It is possible to extend already established systems without changing them because the DTP protocol is fundamentally a metadata system. The DTP system is intended to be used as the foundation for trust, identity, and security. The DTP system is a tool for the users to navigate in the sea of information and be able to selectively choose information relevant based the users own trusted networks and for users to do self-sovereign identity management without the need to store credential documentation privately.
  
  

**References**

\[1\] Verifiable Claims Data Model and Representations https://www.w3.org/TR/verifiable-claims-data-model/

\[2\] Trust (emotion). https://en.wikipedia.org/wiki/Trust_(emotion)

\[3\] Trust. https://ldapwiki.com/wiki/Trust

\[4\] Identity is an Edge Protocol. https://static1.squarespace.com/static/55f73743e4b051cfcc0b02cf/t/59009d56f5e23188266086e0/1493212506000/Identity%2Bis%2Ban%2BEdge%2BProtocol+2.pdf

\[5\] SPKI/SDSI Certificates. http://theworld.com/~cme/spki.txt

\[6\] Decentralized Public Key Infrastructure. https://danubetech.com/download/dpki.pdf

\[7\] Bitcoin: A Peer-to-Peer Electronic Cash System. https://bitcoin.org/bitcoin.pdf

\[8\] Event Sourcing. https://martinfowler.com/eaaDev/EventSourcing.html

Copyright © 2019 Digital Trust Protocol Developers

Permission is hereby granted, free of charge, to any person obtaining a copy of this document and software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
