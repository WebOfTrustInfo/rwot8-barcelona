## Minimal implementation of verifiable credentials for communities of practice on an agent-centric distributed platform
### Authors
Jakub Lanc (jakub.lanc@gmail.com) 

### Keywords
Verifiable Credentials; Communities of practice; Agent-centric systems

### Abstract
Organizing distributed peer communities of practice and their interfacing with official institutions comes with numerous challenges – tracking the education progress of the individuals and sub-communities, maintaining cohesion and coherence of the groups, scaling the trustworthiness and credibility of the individuals as well as transient sub-groups, et cetera. At the same time, decentralized agent-centric platforms emerge, allowing for distributed data integrity and implementation of self-sovereignity-friendly models. This prompts us to explore suitability of agent-centric system implementations of Verifiable Credentials or Verifiable Credentials-like systems for use-cases from the community of practice contexts. We then discuss further methodological (and dare we say philosophical) questions, and hope these also enrich the broader discussions of the DID and VC models and use-case models.

### Introduction
Our aim can be differentiated to two levels: a technical level and a conceptual level, informing the technical experiments. The technical part consists of an experimental implemention of a minimal prototype of a Verifiable Claims or Verifiable Credentials-like conception on an agent-centric distributed platform. The conceptual part is more of a methodological exploration of the ways VCs could be used as a tool for facilitating different levels of functioning of decentralized communities of practice. Ideally we hope discussing this kind of use-cases can also stimulate and enrich the broader discussions related to DID and VC standard development. This is a longer term project, though, so in this paper we will focus more on the elementary technical implementation issues, and we’ll describe some of the methodological issues in the appendix.
 
### Background context
Our prototyping context is a decentralized community of practice / peer network focused on low-barrier mental health support and support in cultivating healthy interpersonal relationships and communication within youth.
Continuing peer education of this type entails specific methods of longer term experiential-reflective learning as well as methods of psychosocial development, and as such, it’s important to ensure not just quality feedback, tracking and communication of the individual trainees‘ progress and competences, but also the patterns and quality of the interpersonal relationships within the sub-communities. The interpersonal learning accent of such potential use-case makes for an interesting borderline case for exploring the suitability (or non-suitability) of VCs in our opinion.
In this case we believe VCs to be:
a) a suitable enabling tool for interfacing with official mental health institutions, as well as other educational and professional institutions, and  
b) a potentially suitable tool for facilitating patterns of organization and learning within and between such communities of practice – a metaphorical „social glue“.
 
We believe an agent-centric system allows greater flexibility in such cases that call for capturing interactions at a finer level of granularity and allows for experimenting with more interpersonally focused types of claims and credentials. We have chosen the Holochain platform for prototyping, as it currently already provides technological infrastructure for experimental implementations and testing.
 
### Technical part
#### Agent centric technology – Holochain
The Holochain protocol allows individuals high control of their actions, identity and data, as well as ensuring trustworthiness of data and actions of others. This is allowed by intrinsic data integrity and peer validation. There’s shared rules and tamper-evident journals - each agent owns a hash-chain of his own interactions, which are cryptographically signed (or counter-signed in case of multi-party interactions) as a proof of authorship. This mean that anyone can make reasonable determinations about data validity without relying on a central authority.
We would like to start with a minimal, bare-bone implementation of the essential VC components on the agent-centric system and then follow with further iterations of conceptual exploration and technical prototyping.
Implementation on Holochain will be done in the Rust language. It entails defining the actor roles within the system, defining and implementing the relevant data structures and validation rules. This presupposes defining an elementary-use case to implement.
 
### Appendix: Further background musings
The reason for using the “Verifiable Credentials-like” formulation compared to just “Verifiable Credentials” stems from our as-of-yet uncertainty about the extent to which the VC model is suitable for different parts of the use-case. Some of those might be seen as a fitting candidates for VCs, but there’s a few concerns that make us consider other possible angles. Here are rough descriptions of some of the partial intended functions:
 
a)    A “micro credit” system for tracking and facilitating achieving specific learning goals -e.g.: Alice makes an agreement with Bob about her following through with her goal of being able to perform activity X as measured by Y in a time frame Z, and Bob supporting her through doing W, with Cyril and Dan attesting for how this has been carried out.  
 
b)    Staking related to a) - there can be an implicit stake in the form of an “learning integrity score” (see d)), but it might be desirable for the parties to stake other kinds of resources. How would those relate to the claims? (I.e.: “Alice has staked XY for her learning goal Z.”)  
 
c)    Motivational and learning feedback - related to a) and b), some claims may serve as more of transient signals for the actor or his close peers than to proving competence to outside actors and institutions, or, could serve as an intermediate signals, which could then be translated into “proper” VCs at some point.  
 
d)    Dynamic “gauges of integrity” - also related to a) and b) - e.g.: How consistent was Alice in performing specific learning activities or praxes over time? Alice might want or not want to disclose such partial micro-attestations to the “outside world”. She might as well want to be able to delineate the time frames to share or define a “thick red line” e.g. after a difficult life period, which might have been compromising her ability to function well at that time. She might as well want to record an attestation verified by relevant parties (i.e. mentor, peers, ...) related to such delineation (“lessons learnt”, “context has changed”, etc.). Those kinds of information might or might not be relevant for outside of the community or between specific communities and institutions.  
 
e)    Interpersonal and relational nature of the claims - the nature of some claims within such domain is often interpersonal and relational in nature - i.e. we want to be more explicit in capturing the fact that when making a claim about the subject, the issuer might be in some ways be also making a claim about the relationship and its quality within a given context, or his own mental models guiding the perceptions behind the attestation.  
 
f)    “Rupture-and-repair” model - an important model within psychology, capturing an important aspect of building trust and relational learning. E.g.: In some reputation systems associated with mental health support and services, clients and colleagues can issue attestations about the provider. So the provider can get “one star” or “red flag” for mis-steps perceived by the client for example. We don’t endorse such static approach to reputation in our context. Rather we believe in reframing such claims in terms of learning - as learning opportunity signals or “repair invitations”, inviting one or the other party to give or solicit feedback and process the event or conflict either together or with a third party, and then attest about that, towards mutual benefit.  

g)    Transient assemblies - temporary dyads, teams or working groups might want to identify themselves, as well as make attestations about their progress.  
 
Part of the theoretical background informing our endeavours and framing of the functions of the claims is Contextual Behavioral Science and Enactive Cognitive Science or “4E cognitive science”, literature related to Experiential-reflective learning as well as frameworks focused on cultivating communities of practice. These foreshadowed concerns could be also seen in terms of gamification patterns described in the academic literature, or even loosely associated with some prediction-market-like principles (staking on learning outcomes). We are aware that some of those functions might be outside the intended scope of VCs as currently defined and intended, but we believe exploration of such borderline causes might at least bring forth useful questions.  

### Resources
Elstad, T. A.; Eide, A. H.; Schumacher, U. (2017). „Social participation and recovery orientation in a “low threshold” community mental health service: An ethnographic study“. Cogent.  

Froese, T. & Gallagher, S. (2012). Getting interaction theory (IT) together: Integrating developmental, phenomenological, enactive, and dynamical approaches to social interaction. Interaction Studies, 13(3): 436-468.  

Zettle, R. D.; Hayes, S.; Barnes-Holmes D.; Biglan, A. (2016). „The Wiley Handbook of Contextual Behavioral Science“. Wiley-Blackwell.  

Kim S.; Song K.; Lockee B.; Burton, J. (2018). „Gamification in Learning and Education“. Springer.  

Brock, A.; Harris-Braun E.; Luck, N. (2017). „Holochain: Scalable agent-centric distributed computing“. https://github.com/holochain/holochain-proto/blob/whitepaper/holochain.pdf.
