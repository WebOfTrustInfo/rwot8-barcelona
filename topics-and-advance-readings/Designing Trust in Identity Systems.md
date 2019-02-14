# RWoT 8 Topic Paper

## Authors
Bentley Farrington and Bart Suichies

## Introduction
An often misunderstood element of the next generation of credential based digital identity systems is that they are no longer reliant on any single issuer being trustworthy. Rather, they rely the combination of many issuers, and many verifiable claims in order to create a reliable web of trust. As with any network, this ability to establish trust between peers scales exponentially with the relationships inside it.

This network effect fundamentally shifts the power balance from centralized issuers, or federated identity managers, towards individual ID holders. The trade-off here is 1) the ease of compliance and 2) automation of services across contexts in an ever expanding ecosystem. Bonus-points for systems that cater to (zero knowledge) proofs over the exchange of credentials, which further simplifies the compliance part (and not unimportant - a fundamental human right as privacy), while allowing for next generation services.

This also fundamentally changes the need for correlation. It's still there, but at the level of individual claims and issuers of those claims, NOT at the level of individuals. In short: I will be able to prove that I am over 18 by sharing proofs of x different issuers. Even if one of these issuers turns out to be not trustworthy, a verifier can still rely on the others that claim the same thing. All without having to have a single identifier cross-linking information across different systems, but merely by combining claims and proofs from different issuers. 

This also changes how we should think about regulation and levels of assurance, which will no longer be tied to single issuance processes, but also to a multi-source verification processes. As verifiers are almost always also issuers, there is a common interest in keeping costs of such systems down, driving the development of open standards to cater to interoperability rather than differentiating on individual levels of assurance. (On a side-note this is similar to the combinatorial power of biometrics - many individual biometrics can have poor performance, but the combination can get you some pretty accurate results.)

Combined, this leads to systems that are 10x more trustworthy, offer 10x the value, and are likely to be 10x cheaper. As such, it is almost an inevitability they will be the prevailing model for digital society.

## The need for a human centered design exploration
Putting the ID holder at the center of an identity system comes with great opportunity, but also introduces new risks and barriers to adoption. Many of these are non-technical and such, should be explored in multi-disciplanary way. We propose a human centered design approach to tackle some of these issues and help shift the focus to not just the technical feasibility, but also inclusive usability. This is a prerequisite to creating an identity system which combines technical and human trust elements. 

Typical questions to explore play at different abstraction levels:

- How to design a self-sovereign identity system that can be adopted by key players in the identity ecosystem? Should it complement or replace existing systems?
- Does it make sense to have core metaphors for technical concepts to help build trust in these systems?
- How to design a credential exchange for people without ability to access the required technology?
- How will the new artefacts and control-levers of self-sovereign identity manifest themselves?
- How to prevent the unwanted sharing of credentials in a case where there is a power difference between a service provider and a citizen that would like to have access to a service? Is there such a thing as freely given, informed consent?
