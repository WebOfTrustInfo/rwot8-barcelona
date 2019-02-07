# Multi-Factor Attribute Trust

I am interested in the problem surrounding the question of how do I trust an attribute presentation? I know Sovrin have the concept of [Governance Frameworks](https://sovrin.org/library/sovrin-governance-framework/), which define the rules for actors within a certain ecosystem although I am less aware of the technical implementation of these frameworks. I accept this is a good solution, but wonder about its ability to provide trust when credentials are used across ecosystems. For Verifiable Credentials to succeed they must be usable in as many contexts by as many verifiers as possible, this will help build network effects enabling applications, outside of the scope of the original ecosystem that the credentials were defined for, to be designed to accept certain credentials.

Within a credential ecosystem it is easy to envision this working through shared knowledge of the trusted issuers' public decentralised identifiers, but how does a verifier from outside this ecosystem without this knowledge trust attributes from these credentials? 

Defining robust methods for gauging the trustworthiness of an attribute presentation will be essential for ensuring these credentials can be used as extensively as we would like. Throughout the rest of this article, I outline potential mechanisms for achieving this trust and content that a combination of these could be used to provide multi-factor trust in attribute presentations from unknown issuers.

## Mechanisms for Judging Trust

### Open Access to an Ecosystems Trusted Issuer DIDs

This option would seem to be the most obvious. Suppose within an identity network an ecosystem forms for Healthcare in the UK. As part of that formation, they define a framework outlining the types of credentials needed within the ecosystem and the public DIDs trusted to issue them. These DIDs are shared with all members of the ecosystem. For example, all hospitals are trusted issuers of doctor employment credentials and know all the other trusted DIDs able to issue these employment credentials.

This works within an ecosystem where dissemination of trusted DIDs is easy and could be built into the services used by this ecosystem, but how does a verifier outside this ecosystem check a doctor employment credential was issued by a DID trusted within this health framework? How can they do it in real time? How can they do it without compromising the privacy of the individual?

One option might be for that ecosystem to host an endpoint for anyone to query to verify the authenticity of the issuing identifier, but this has its problems. Who would be in charge of running it? How can you be sure the endpoint has not been compromised? What happens if the endpoint is down? Is this a privacy concern - if every time a credential is verified, the verifier has to hit someone's endpoint?

A solution to this could be to store these registries on the ledger must the same as revocation registries. These use dynamic accumulators to combine the hashes of all trusted DID's for a certain credential definition. This would provide an open, highly available, immutable registry to query without the same privacy concerns as an endpoint. The only problem I can see is which entities are capable of dynamically updating the registry. This could be managed through threshold signatures with key sharing defined as part of the Governance Framework.

### Public Credentials/Attestations

A different approach could be to issue credentials on chain to the trusted issuers in a certain ecosystem. Then when verifying a credential presentation by resolving the DID on chain the verifier would also check for a credential to support the DID as a trusted issuer.

The obvious problem with this is who issued that credential and how can you trust them. Trust could be improved with public credentials issued from top to bottom of a governance framework. These credentials are basically attestations to the trust of a public DID. If all members of an ecosystem attest to the trust of all other members on chain creating a verifiable web of trust for that ecosystem. This would make it much harder for a bad actor to imitate a trusted issuer.

### Context

Providing context could be another mechanism for gauging the trust of an attribute. For example, a verifier receives a credential presentation of an attribute by an issuer have low trust in. The verifier could ask for further corroborating proof of that attribute.  The challenge here would be to enable a prover to provide this proof without giving away any more information about themselves than necessary, following the data minimisation principle.

An example could be when attesting to work experience in a foreign country, the verifier requests proof that you indeed were in that country for the stated amount of time which the prover can present through proofs of digital passport stamps from that country.

### Quantity

The number of different issuers a prover can show attest to the same attribute they are presenting the greater the trust a verifier can place in that attribute. A simple example of this might be attendance at an event. Attestation from 10 different low trust DID's could be as trustworthy as a single attestation from a trusted DID.

### Time

Time is an interesting one. I think there are multiple ways to include time into a trustworthiness calculation. The most obvious is how long has the issuing DID been registered on the public ledger. However, I think particularly in low trust environments, if there was some way to leverage the length of time the prover has had a private connection with an issuer or an entity attesting to the credibility of a claim in such a way that the prover could combine this into the presentation then time could be a really useful measure of trust.

I am not sure exactly how this would work, but it mirrors how we act in the physical world. The longer I know someone the abler I am to confidently attest to their trustworthiness. I believe there must be some way to translate this into the anonymous credential world. 

## Closing Thoughts

For a verifier, making the decision to trust or reject the attributes presented to them will be critical to their organisation. At the same time, the amount of trust required and the initial trust conditions can vary widely depending on the context of the identity interaction. Mechanisms to allow verifiers to make real-time decisions on whether or not to trust the presentation of attributes presented to them will be important to the development of Self-Sovereign Identity and the network effects that will make it the default approach for digital identity.

This is an initial attempt to outline ways to judge the trustworthiness of an attestation. I believe a combination of these methods could provide multi-factor trust needed, particularly for individuals from areas of the world without trusted entities capable of bootstrapping a decentralised trusted credential network.

Finally, these are some questions I am thinking about:

- Are there any other approaches that could be used to assess the trust of an attribute?
- How might these methods be implemented & combined in such a way to provide a trust score for an attribute?
- How can the initial trust conditions of a verifier be included in these methods, to provide an interoperable solution any verifier could use?
- How might we combine trust assumptions gained from context, quantity and time be used to provide high trust credentials to people from areas of the world with low trust organisations?

## Next Steps

I would like to discuss ongoing work within the community to solve this trust problem. How do people see it working? Other than hard coding in trusted DID issuers how can a developer build applications that verify credential presentations meet the trust requirements of the application in as flexible a way as possible?