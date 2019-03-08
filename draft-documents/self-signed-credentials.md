# Enabling a Web of Trust with Self-Signed and Self-Issued Credentials
Lead: Nader Helmy (nader.helmy@danubetech.com)

Contributors (in alphabetical order): 
Juan Caballero (juan@sourcecheck.org)
Carsten Keutmann (carstenkeutmann@gmail.com)
Maciek Laskus (maciej.laskus@gmail.com)
Jack Poole (jack.w.poole@gmail.com)
Alex Preukschat (alex.preukschat@evernym.com)

## Abstract
The invention of Verifiable Credentials has provided the basis for a new web of trust, including an ecosystem of Issuers, Holders, and Verifiers interacting in a myriad of ways. Many of the use cases to date have primarily focused on the role of the Issuing Authority as a public root of trust. Examples of these credentials include passports, transcripts, financial documents, and digital certificates. While these kinds of Verifiable Credentials are valuable in a variety of business and consumer use cases, they do not address the broad role of the Issuer as outlined in the Verifiable Credentials data model (§1.2). As it describes, Issuers can be “corporations, non-profit organizations, trade associations, governments, and individuals.” The last item has not received significant coverage in current implementations and use cases. In addition, the spec details that “Issuers can issue Verifiable Credentials about any subject” (§1.3). If we consider the implications of a real Web of Trust which includes a variety of identities interacting in a variety of complex ways, we must examine the role of self-issued credentials and define a framework for interpreting their potential value. The Decentralized Identifier (DID) spec allows for self-sovereign identifiers which can be controlled by individuals. These identifiers, combined with Verifiable Credentials, provide the basis for new kinds of mutually shared consent. The basic question at hand is how do we evaluate whether to trust an unknown DID being used in a particular context? Phrased in another way, what can I prove about myself which is not known by an issuing authority? The answer is personal data, the mechanism is Verifiable Credentials, and for many use cases, these credentials will be self-issued.

## Mental Model
In the Verifiable Credentials spec, a credential is defined such that any identity holder can cryptographically verify “the authorship of the data can be trusted” (§2). What the specification does not cover is why you should trust the validity of the credential or the issuer. In fact, one of the first assumptions of the trust model states, “The subject and verifier trust the issuer to issue true (that is, not false) credentials about the subject, and to revoke them quickly when appropriate” (§5.2). This is the case for any Verifiable Credential, including the typical SSI examples such as a passport, a transcript, or a digital document. These types of credentials are issued by trusted authorities such as governments and universities, and the evaluation of what is considered to be “trusted” is outside the scope of the framework (and indeed, excluded from many implementations). In a similar manner, the Issuer of a self-issued credential should ultimately be evaluated by an individual with all the context they are given. As with any identity framework, including self-sovereign identity, the identity holder must make a determination about another entity based on all of the information they are provided. This paper provides a framework for evaluating these self-issued credentials as well as several examples describing how they might be used in a peer relationship or a peer network.

The most common uses for self-issued credentials appear to be mutual social networks which offer the ability to opt-in. In these scenarios, identity holders are agreeing to participate in the network for their own benefit, and their participation in the network may increase the value of the network itself. These networks offer a good prototype to demonstrate the value of self-issued credentials, which must be evaluated in a rigorous and reproducible way.



## Previous Work
There are a number of papers that have been written at Rebooting Web of Trust about decentralized reputation systems and frameworks. These proposals offer a way to frame the problem, and in some cases offer new architectures and metrics to evaluate the meaning of “trust” in particular contexts. The focus of this paper is to provide a method for building up a personal identity using nothing but existing open standards, e.g. self-asserted and self-issued credentials as they emerge from peer networks of self-sovereign identities.
    
In particular, the “Portable Reputation Toolkit” provides a ‘General Use Case’ framework which defines a basic interactive way to build up one’s “reputation” using the extensible data format of credentials to add context and information to one’s identity. To begin with, an identity owner controls some DID as well as the private key that they can use to sign credentials and claims. The identity owner wishes to make a statement about themselves, and to do so they create a claim or self-issued credential in a JSON-LD format. It is signed with their DID and timestamped. In this case, the DID owner is both the subject and the issuer of the credential. Others can evaluate or invalidate the assertion made in the credential. To do so, they publish Evidence in a JSON-LD format which they sign with their own DIDs. Evidence does not have to be related to any credential or claim initially, but it can also be attached or added to the original credential.

The above process is a standard interpretation of the Verifiable Credentials format and the key-signing properties of DIDs. The new construct introduced by the paper is a way to process evidence and self-issued credentials called an Evaluation. Any user can refute, challenge, or support an earlier credential with an evaluation. These evaluations always point to a credential or claim and include a true/false or 0-1 float value. They are again signed by the creator’s DID and timestamped. 

Finally, a potential Verifier can use all of the above to inform their decision regarding whether or not to trust an Issuer. To do so they may wish to use a Filter. A filter is an algorithm which factors in the evidence, the evaluations, and the claims in the credential as well as the trust in the DIDs signing each of these objects to determine the validity of the credential. The user can apply any number of these filters to a credential (or set of credentials) to gain numerous perspectives on the truthfulness of the claims included. A user may even develop a list of trusted filters or import filters from another party.  Presumably this would happen in a competitive marketplace for agents, rather than at the layer of individual user experience or identity layer. 

These constructs become particularly useful when discussing the mechanics of self-issued credentials and how they can be built up over time. When a DID is initially created it does not necessarily have any reputation or trust associated with it. The current assumption has been that the DID begins to collect credentials which are issued to it by 3rd party authorities. In the case where this is not available, we can use self-issued credentials utilizing these constructs as building blocks for a basis of trust. This represents a shift in thinking about Verifiable Credentials as continuous, long-term representations of identity data instead of discrete, authoritative documents.

In addition, “Design Considerations for Decentralized Reputation Systems” covers the issue of privacy and confidentiality as it relates to social sharing. It’s desirable to have some granular control of which attributes are shared in which contexts in order to manage our relationships, however there are several different ways to identify a user that are outside of their control. In the case of self-issued credentials and attestations based on social graphs, users should consider the privacy implications specifically surrounding correlation. Identity owners need to be aware that sharing multiple credentials can lead to correlating an entity across multiple identifiers, and end-users should be encouraged and educated to practice minimal disclosure when creating credentials to protect themselves from unintended correlation.

## Properties of good self-issued SSI credentials
It is useful to discuss the properties of good self-issued credentials as a framework to identify self-issued credentials that can be semantically meaningful in a peer relationship or a peer network. These are listed in order of increasing importance to establish trust for a self-issued credential.

### Pairwise or Mutual
In many cases, for self-issued credentials to have value, they need to be confirmed by other parties, at least “passively” (by prior opt-in). Depending on my relationship with the Issuer, a self-issued credential asserted by a single party may have some semantic value on its own. However as it is individually endorsed by one or many different peers (in the form of claims, evidence, or evaluations) this credential may become more relevant to my network.
### Recurring
What makes a pairwise or mutual self-issued credential even more valuable is if it is repeated over time. A self-issued credential with one peer endorsement once may be deemed unreliable or low-trust, but if it is recurrent over time it becomes more trustworthy to my network. These claims, evidence and evaluations can be embedded within the original credential.
### Recent
The value of certain self-issued credentials depends on the timeframe that the credential was issued. Particularly with self-issued credentials, there is the risk of “stale” data. For instance, a self-issued credential that has recently been issued may be more valuable than one that was issued 2 years ago. Self-issued credentials may come with an optional “expirationDate” (§4.6) property.
### Invested
Self-issued credentials are even more valuable for my network when they are repeatedly evaluated over time by parties who have proved some kind of “investment” in the credential’s claims. An “investment” necessitates expensing a scarce and valuable resource e.g. attention, money, and individual reputation. These investments may be on behalf of the self-issuer themselves as well as any number of other peers. These investments can be added as additional evidence to the credential and can take the form of smart contracts or proofs, or be evaluated/qualified on other layers of the identity stack. 
### Localized
Each self-sovereign identity owns their own social graph describing their connections and relationships with others. When considering the claims, evidence and evaluations associated with a particular self-issued credential, it is useful to make an assessment about the location of the source of info in the social graph. Groups of peers or communities which include the self-issuer can be considered “local” or native and should be taken into account as part of assessing a credential.

## Use Cases
In many social contracts, there is a mutual interest amongst the participants and an option to opt-in to certain requirements and agreements. As we establish a new Web of Trust, there will be a variety of social contracts that can be facilitated digitally. These exchanges are characterized by the properties above and can take a variety of different forms suited to their particular use cases
### Social circles
To participate in social circles or networks, individuals can opt-in to be known to a network of their peers. In a self-sovereign identity model, identity owners are able to generate a DID for the sole purpose of interacting with this network. They may reveal elements of their identity selectively to different members of the circle, or all members. This applies the principle of minimal disclosure and allows the participants to have control over how they wish to be known in their particular communities.
The analogue for this in the real world is when we sign up for a newsletter or social media site. When we seek to be members of a group, we often provide our identifiers (like our name and contact info) as well as some information about ourselves (what we like, what we know, what we are interested in). The communications platforms these take place on (snail mail, email, and social media messaging) often have a lot of filtering built in that heavily weigh familiarity and/or institutional root of trust in the namespace.  The same framework can be extended to include DIDs as identifiers and credentials representing identity attributes.  A social graph built on SSI principles would allows a higher degree of end-user control over and awareness of filtering mechanisms and contact permissions.
Specifically, let’s say that I am a part of a Meetup.com group for hackers and developers in my city and I want to reveal the same level of detail about me to the whole group participating in that meetup. By opting in to this DID-based social circle, I can query the network to find others who may share attributes I am looking for, or to discover new resources and people who I may wish to connect with.
### Respected peer endorsements
There are many cases in which we can learn more about an unknown identity by leveraging peer networks. 
For example, during a discussion somebody claims deep knowledge of theoretical physics. Other participants of the discussion have no ability to verify that claim - they themselves have no expertise in this domain. However, in order for the discussion to progress, they need to be able to establish whether this claim is believable. The way this is currently established is through ‘reputation 3rd parties’ - such as university degrees, job titles, awards etc. Alternatively, one could support their claim by proving that other people with that kind of expertise recognized it, e.g. spent time & effort on reading their works on physics. 
Unlike traditional organizations, there is nobody who can formally speak on behalf of bitcoin. One could prove their membership in this community by creating a Twitter account and showing that other members of the community pay attention to them -- as verified by other accounts belonging to this cluster following them, responding to their messages, interacting with their tweets. 
ex.
{
  "id": "http://example.edu/credentials/1870",
  "type": ["VerifiableCredential", "Peer-Endorsement"],
  "Issuer": "did:example:98765zyxwvu",
  "issuanceDate": "2010-01-01T19:23:24Z",
  "credentialSubject": {
    "id": "did:example:123456abcdef",
  },
  "proof": { ... }
}
### Identity Proofs
The self-sovereign identity model asserts that an individual owns all of their data, including all of their relationships and their attributes over all of time. Some of these relationships represent connections with services and businesses, but many of these connections are peer to peer or shared between individuals. The aggregate of this data is incredibly unique to that individual; there is virtually no way to replicate this data chain and provenance without being the owner of this identity. This aggregated identity is itself a valuable identifier. If someone is able to hash this “hardened” identity in some way, they can include it in a self-issued credential along with a timestamp and metadata. This becomes more valuable as it is continually confirmed by others in their network.
{
  "id": "http://example.edu/credentials/1872",
  "type": ["VerifiableCredential", "Proof-of-Self"],
  "Issuer": "did:example:123456abcdef",
  "issuanceDate": "2010-01-01T19:23:24Z",
  "credentialSubject": {
    "id": "did:example:123456abcdef",
  },
  "proof": { ... }
}

## Implementation Considerations
In order to build a peer relationship or a peer network where self-issued credentials can be used to transfer and communicate value, there are a few software architecture considerations that should be taken into account. Primarily, this is an issue to be dealt with by implementations of identity agents and additionally on the application layer. Any agent which adopts some DID usage and can receive verifiable credentials can receive the kinds of self-issued credentials described in this paper. Whether or not this agent can interpret and apply the principles described here 

### Questions for implementation

How is data shared?
Is it fine that everyone keeps a local/cloud database and share data on request?
Or should data be shared automatically and how would that be done?
How much data can a system handle, does it need to store everything or is there filters?
How does a system evaluate the information (claims/credentials) in a aggregated way, what rules are needed?

DID is a pull request system, where when a verifier needs to know about a subject asks the subjects DID for information on how to get additional credentials.

The data structure is rich and is on a higher level on the information stack. The DID system scale very easy and still works perfectly in a decentralized way. However, aggregating credentials from many different DID’s is relatively slow and time-consuming. DID is an identity, security system, but not a reputation system.

An alternative system for comparison.
Digital Trust Protocol (DTP) is a push request system where claims are pushed out constantly. The data structure is very simple and generic, it sits on a lower level on the information stack. The DTP system is built for scale and decentralization but is harder to implement than DID. The DTP system offers instant availability of information on peers, their credentials and claims from in-memory graph structures. DTP is designed to be a identity, security and a reputation system.

## Conclusion
Both systems offer the needed functionality, however, the DID system is more mature, well defined and may be easier to implement. In perspective of being able to self-issue credentials, the DID system will suit this purpose perfectly, as it offers better control of one’s own credentials.
