Can Name Services provide Persistent Human-meaningful Names Linked To A Self Sovereign Identity DID Without Compromising SSI?
======================
A Topic Paper submitted to Rebooting The Web of Trust 8

by Toby Tremayne & Ryan Gill

February 26, 2019, Melbourne Australia

## Overview
The Zooko’s Triangle Trilemma  posits that only two of the desired three components of a modern digital identity system can successfully be implemented within a single system. Like “Good, cheap fast; pick two”, such a system can achieve security and decentralization, but without the third element of desirability – human meaningful names.

The Topic for discussion is whether an externally managed name service can safely be used for deliberate identity persistence, allowing users to retain a name or handle and accrue reputation against it.

## Concept
![Diagram of conceptual authentication process using Idents](/name-services-and-ssi-filies/figure1.png)
Figure 1: Diagram of conceptual authentication process using Idents

### Name Service
A decentralized database or distributed ledger allows registration of “Aliases”, a human readable arbitrary string, which can be attached to a a user specified sovereign identity DID (IE a Sovrin DID), creating an “Ident”.

Behavioural or network contribution reputation within a moderation network or a consensus group can be assigned against the DID. This lets the user carry around their own “handle” or persona online much like a twitter handle, while still retaining the protections of SSI.

### Zero Knowledge Proof of Humanity (PoH)
A proposed standard for proving a human controlled, legally liable yet publicly anonymous identity online. Simply, an agreed level of service based or in-person verification that is linked to verification of a government accepted form of identification, or sufficient equivalent proof.

Proof of Humanity is a credential that could be offered at the time of verification with a Steward or Verifier on an SSI blockchain, or a recognised credential for any form of id that passes the requirement. This proof is used to assert that the user is a real human, identifiable from the rest of humanity. While the Steward or Verifier would retain knowledge of Personal Identity from the original verification, that knowledge is not passed on with credentials or in any other way to service providers.

A Channel or service requiring PoH can allow anonymous or pseudonymous posting and transactions, while retaining the ability to action a behaviour on the account if there are valid applicable legal reasons to do so – IE providing a warrant or subpoena to a Steward or Verifier.

Using PoH is consent to be legally liable for your interactions and transactions under that account, with the knowledge that Services do not record your real identity, but law enforcement can connect you to your activity should they have grounds.

Details such as SLAs, security requirements and regulation are all important requirements for a successful PoH implementation, however we believe even a tacit agreement of currently available verification standards and a well drafted consent / usage form are enough to implement a proof of concept on existing implementations like Sovrin. Over time as the protocol is refined, proof requirements for a PoH credential could become more stringent.

The ultimate aim of Poh is not to solve all online abuse and bad faith acts, but to provide a baseline to develop the ability for users to interact anonymously online while still being accountable to legal and community rules.

## Reputation
Given an arbitrary reputational system, points could be accrued against the DID. Additionally, the use of the Alias in online social settings like games or social media accrue social reputation against the name.

### Concealed DID
Instead of using the original SSI ID the user registered the Alias against on the Name Service, a new DID could be provided with a custom Ident method. “did:ident:2345” might proxy a lookup to the original SSI DID, and pass the key detail accordingly, allowing for a step further obfuscation from data miners, while still being legally actionable.

### Collisions
If a shared standard were to be developed, a game or social media site might use a list of name services, or allow you to sign up with any. Colliding names could be given automatically assigned modifiers for differentiation, based on locality and time of arrival. Subsequent users with the same alias registered on a different service might receive an appendix denoting their service and a number.

## Questions

### Standard
How could a minimal standard for the use of names together with an SSI DID be developed to allow all such services to participate?

How else might multiple name services co-exist and manage collisions for usernames for example, when everyone joins the latest VR world?

### Identity Cycling
If not using the Concealed DID method, users could simply change the SSI ID attached to an Ident, thus “rinsing” online reputation. Would the (globally speaking) limited number of Stewards, limit the feasibility of this action on a large scale?

How can identity cycling be prevented without locking an Alias to a one time DID?

If the user loses control of the Ident’s SSI ID, how can they regain control of their online reputation without allowing the bad actor use of identity cycling?

### Proof of Humanity
How could Proof of Humanity be developed as a standard among existing Stewards with current technology? How could a living standard be developed to grow and refine a list of acceptable forms of personal verification?

Would PoH require legislation, IE criminalizing network accounts operating bots under false PoH?

To what level would PoH need to be developed to be useful for anything from basic social media permissions to virtual environment and app authentication?

Does the idea of layering names on top of SSI or providing the ability to create one portion of your Digital Identity to be your “presence” in the online world work at odds to the intent of SSI?
