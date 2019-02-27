## Minimal implementation of verifiable credentials for a community of practice use case on an agent-centric distributed platform

### Authors
Jakub Lanc (jakub.lanc@gmail.com)

### Keywords
Verifiable Credentials; Communities of practice; Agent-centric systems

### Abstract
Organizing distributed peer communities of practice and their interfacing with official institutions comes with numerous challenges – tracking the education progress of the individuals and sub-communities, maintaining cohesion and coherence of the groups, ensuring the trustworthiness and credibility of the individuals as well as transient sub-groups etc. At the same time, decentralized agent-centric platforms are emerging, allowing for distributed data integrity and implementation of self-sovereignty-friendly models. This prompts us to experiment with implementing a minimal Verifiable Credentials-like system on a distributed agent-centric platform (Holochain), explore its suitability for distributed community of practice use cases, and discuss the specifics of such.

### Introduction
Our aim spans a technical and a conceptual level, which informs the technical experiments. The technical part consists of an experimental implementation of a minimal prototype of a Verifiable Credentials-like conception on an agent-centric distributed platform. The conceptual part is more of a methodological exploration. “In what ways and to what extent could VCs be used as a tool for facilitating different aspects of functioning of distributed communities of practice?”, we ask. We hope discussing this kind of use cases can also stimulate and enrich the broader discussions related to DID and VC standards and use cases. Since this is a longer term project, we will focus more on the elementary technical implementation issues in this paper, and we’ll describe some of the domain-specific conceptual issues in the appendix.

### Background context
Our prototyping context is a decentralized community of practice / peer network focused on low-barrier mental health support and support in fostering healthy interpersonal relationships and communication within youth.
The more obvious domain of VC use in this case is interfacing with official mental health institutions and other educational and professional bodies (and indeed an exemplary use case from this domain might serve as a basis for our initial minimal prototype implementation), but our interest lies in the more “esoteric” aspects of this territory:
Continuing long term peer education of this type entails methods from the fields of experiential-reflective learning and psychosocial development. 
An important part of such process is ensuring quality feedback and tracing individual participants’ learning progress, while assuring selective disclosure and overall autonomy and control over their data.
Another important aspect is the patterns of interaction and quality of interpersonal relationships within the community and between sub-groups. “Could VCs be suitable for capturing relevant interpersonal patterns and claims?”, we ask. For us the issue of translating such patterns and signals to a technological system in systemically beneficial ways (preventing undesirable externalities, side effects and unpredictable systems dynamics down the road) is very delicate and important. Further elaborations exceed the scope of this paper, but overall, we consider them essential.
We believe interpersonal learning accents of these use cases make for an intriguing borderline exploration - of the potential suitability (or non-suitability) of VCs, but also deeper conceptual (dare say even philosophical) questions.
 
### Technical part
#### Agent centric technology – Holochain

We’re still in an exploratory phase, but we believe an agent-centric system allows for a greater flexibility in implementing finer-grained and interpersonally oriented types of claims and credentials, while allowing for sufficient participant autonomy and control over their data. We have chosen the Holochain platform for prototyping, as it currently provides sufficient technological infrastructure and development ecosystem for experimental implementations and testing. We also find their “Autonomous Agent” license model as an important step towards promoting the autonomy and protecting privacy of the users.  

The Holochain protocol gives individuals high level of control of their actions, identity and data as well as upholding trustworthiness of other agents’ data and actions. Core components are peer validation, and intrinsic data integrity, which is assured by hared rules and tamper-evident journals. Each agent owns a hash-chain, recording his own interactions which are cryptographically signed (or counter-signed in case of multi-party interactions), serving as a proof of authorship. This mean that anyone can make reasonable determinations about data validity without relying on a central authority.
We want to start with a minimal, bare-bone implementation of the elementary VC components and then iterate between conceptual exploration and technical prototyping. 
Implementation on Holochain will be in the Rust language. We will need to define agent roles within the system, relevant data structures and proper validation rules. This presupposes choosing an elementary use case to implement.
 
### Appendix: Further background musings
We used the phrase “Verifiable Credentials-like” instead of just “Verifiable Credentials”. This stems from our as-of-yet uncertainty about the extent, to which the VC model will be suitable or practical. Here are perfunctory outlines of some of the intended VC functions to provide at least a cursory insight:  
 
a)    A “micro credit” system for tracking and facilitating achieving specific learning goals - e.g.: Alice makes an agreement with Bob: she will follow through with a learning goal X as measured by Y in a time frame Z, and Bob will support her through doing W. Cyril and Dan will attest for how this will have been carried out.  
 
b)    “Staking” - there can be an implicit stake in the form of a “learning integrity score” (see d)), but it might be desirable for the parties to be able to stake also other kinds of resources (e.g.: “Alice has staked XY on following through with her learning goal X.”). How could those kinds of claims be implemented as VCs?  
 
c)    Motivational and learning feedback - related to a) and b). Some claims may serve more as transient signals for the actor or his close peers themselves than as proofs of competence to outside actors. Alternatively, they could serve as a sort of “intermediate” signals, which could be translated or bridged to “proper” VCs at some point.  
 
d)    Dynamic “gauges of integrity” - also related to a) and b). E.g.: “How consistent was Alice in performing specific learning activities or praxes over time?” Furthermore, Alice might or might not want to disclose such partial micro-attestations to different parts of the “outside world”. She might want to be able to delineate time frames to share, or define a “thick black line”, marking a blank slate, new stage. An simplistic example to illustrate the idea: after a difficult life period marked by compromised ability to function well, Alice wants to attest for this divide (“lessons learnt”, “context has changed”, etc.) together with relevant parties (i.e. a mentor, peers). She might or might not want to make this information visible outside of the community, or even outside their sub-group.  
 
e)    Interpersonal and relational nature of the claims - we want to be more open to and explicit about the possibility, that in making a claim about a subject, the issuer is also, in a way, making a claim about his own mental models behind the attestation, or the relationship between him and the subject. What could be some specific examples?  
 
f)    “Rupture-and-repair” model - an important model of building trust and relational learning in psychology. To illustrate: In reputation systems associated with mental health services, clients and peers can issue attestations (ratings, reviews, stars etc.) about the provider. So the provider can get “one star” or a “red flag” from the client for his “mis-steps” for example. We don’t endorse such static approach to reputation. Rather we believe in reframing such claims in terms of learning - learning opportunity signals or “repair invitations” for example, inviting one or the other party to initiate and engage in a more receptive interaction, processing the event or conflict either together or with a third party, and then attest about the resolution towards mutual benefit.  

g)    Transient assemblies - temporary dyads, teams or working groups might want to identify themselves, as well as make attestations about their progress.  
 
Theoretical background informing our endeavours and framings includes Contextual Behavioral Science, enactive cognitive science or “4E cognitive science”, theories and practices related to experiential-reflective learning as well as frameworks focused on fostering communities of practice. The foreshadowed concerns can also be considered in terms of gamification patterns in education, or even prediction-market-like principles (i.e. staking on learning outcomes). We are aware that some of those functions might be outside the intended scope of VCs as currently defined and intended, but we believe exploration of such borderline causes might stimulate a fertile discussion.  

### Resources
Elstad, T. A.; Eide, A. H.; Schumacher, U. (2017). „Social participation and recovery orientation in a “low threshold” community mental health service: An ethnographic study“. Cogent.  

Froese, T. & Gallagher, S. (2012). Getting interaction theory (IT) together: Integrating developmental, phenomenological, enactive, and dynamical approaches to social interaction. Interaction Studies, 13(3): 436-468.  

Zettle, R. D.; Hayes, S.; Barnes-Holmes D.; Biglan, A. (2016). „The Wiley Handbook of Contextual Behavioral Science“. Wiley-Blackwell.  

Kim S.; Song K.; Lockee B.; Burton, J. (2018). „Gamification in Learning and Education“. Springer.  

Brock, A.; Harris-Braun E.; Luck, N. (2017). „Holochain: Scalable agent-centric distributed computing“. https://github.com/holochain/holochain-proto/blob/whitepaper/holochain.pdf.
