# #SSI20XX - Model Use-Case Definitions and Implementation Commitment for higher Solution Interoperability and Robust Specifications.

Preface: Contribution by Martin Riedel / Identity.com as a Topic paper for the Rebooting of the Web-of-Trust workshop held in Barcelona, Spain from March 1st to 3rd.

## Summary
"The SSI community has developed several products around existing (draft) standards, like Decentralized Identifiers (DIDs) or Verifiable Credentials; however, there have been few interoperable implementations around SSI across different providers or companies even though there is often a high-level consensus within the community groups. This paper proposes that a vision statement (for example #SSI20XX) containing a very limited set of highly specified use-cases and UX descriptions will allow solution providers to commit to a common implementation goal that can greatly benefit solution interoperability and provide valuable feedback to existing specifications in the field of SSI."

## Introduction

The genesis block of Bitcoin just celebrated its 10 year anniversary on January, 3rd 2019, and since the genie of that new technology was let out of the bottle, the community has seen tremendous advancement in the adoption and the development around Distributed Ledger Technology (DLT).

The application of blockchain in the identity and access management (IAM) space quickly became apparent, especially since the existing centralized solutions were prone to hacks or implemented data management processes that allowed for easy identity fraud (e.g. social hacking).

Since then, numerous companies or organizations have developed solutions that utilize a DLT in some way or another to anchor identity information in a decentralized way. Their products and implementations have proven that the technology could practically be applied.

The introduction of Decentralized Identifiers (DIDs) was a significant milestone because it started to standardize the foundation layer around an interoperable self-sovereign identity ecosystem. Solution providers have greatly adopted the utilization of DIDs within their existing products, and as a foundational technology, it does not come with too many dependent technologies that need to be adopted due to a transitive relation.

However, within recent years, the community has built further upon that foundation and divergent patterns are starting to arise again. Within an emerging field, that is generally a beneficial trend because it allows for new innovation to arise quickly. The exploratory spikes become problematic as soon as new designs or specification are based on implementations that a whole part of the community has not developed consensus over yet. For example, it is very hard to standardize on a Proofing Request protocol if there is no high-level agreement over the underlying communication elements.

Solution providers within the decentralized identity space should strive for a high degree of interoperability in order to demonstrate the anti-monopoly patterns that arise from the use of that technology.

Therefore this paper proposes that a vision statement (for example #SSI20XX) containing a very limited set of highly specified use-cases and UX descriptions will allow solution providers to commit to a common implementation goal, which will greatly benefit solution interoperability and provide valuable feedback to existing specifications in the field of SSI.

## Status Quo

Most solution providers fill in the “gaps” that arise during the implementation of existing SSI specification on their own. Generally, these missing pieces would provide valuable input back to the original standard bodies, but often, the thought process and design around the custom implementation will not actively be shared externally.

Usually, this is not due to any ill intentions by the implementer, but rather due to the fact the changes are not deemed important enough, or, are highly linked to a dependent technology of the custom implementation that does not want to be shared publicly. 

An aligned vision statement around solving a predefined use-case in an interoperable way would allow solutions providers to fill in the “missing” pieces of implementation and specification in a collaborative way.

## Requirements for the (Implementation) Vision paper:
Solution providers within the SSI Community need to estimate and prioritize implementation demand that would arise of executing a common SSI vision use-case in competition with other internal development requirements. Therefore, the SSI vision paper should be a very detailed description of the use-case (or use-cases) that are planned to be achieved. This should include functional diagrams (e.g. sequence flows, UI/UX designs, data formats, and technology stacks) that allow for a better estimation around the expected complexity that may arise.

Furthermore, the described use-cases should not have a strong link to any specific functional domain, in order to not discourage providers that have business interests in other fields. Or, reversely, no single contributor should benefit in a disproportionate way. Most certainly this would lead towards asynchronous support of the project.

## Example Flow:
In order to initiate the discussion about well suited universal use-cases that can potentially be part of that implementation vision paper, an exemplary UX Flow for an  [Appointment and Access Management is attached.](./media/SSI20XX-Appointment-Access-Mgmt-UC.pdf)

## Challenges
There is an implicit trade-off when deciding on the specificity of a vision paper. On the one hand, it needs to be specific enough for companies to be able to commit towards it and provide an implementation within a predefined timeline. On the other hand, it should not take over the role of a priori specification, where low level technical and functional problems need to be solved. Readers need to be able to understand what the “destination” looks like, rather than knowing the path that leads there.

## Outlook
An Interoperability Project has been initialized within the DIF (Decentralized Identity Foundation) that aims at executing on that plan and designing the use-case scenario(s) in detail so that several implementation partners are able to commit towards it.



