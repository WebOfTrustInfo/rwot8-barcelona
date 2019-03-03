# Use Cases and Research Directions for self-sovereign publication and journalism

RWOT8, March 2019, Barcelona

Lead author: Juan Caballero (juan@sourcecheck.org)

Contributors/Editors:  Nader Helmy, Juan Caballero, Alex Preukschat, Jack Poole, Carsten Keutmann

## **Abstract**

The intention of this paper is to begin elaborating and thinking through some use cases and impacts of integrating self-sovereign identity systems, as well as their claims systems and trust networks, into the data infrastructure of the publishing and journalism industries, particularly publication indexes and global-scale platforms and aggregators. The primary author, Juan Caballero, is involved with a technical cooperative (SourceCheck.org in Berlin) that is researching ways SSI could be integrated to existing data systems, platforms, and meta-platforms. Given the real-world urgency of the industry-scale funding crises in journalism and publishing, and given the consequential misinformation campaigns that are weaponizing social media and taking advantage of the anxiety that weaponization creates, there is a natural temptation to build something immediately that can start benefiting journalists, fact-checkers, and publics. But modeling the consequences and use cases of such systems (and beginning to sketch out some of the legal and ethical issues) is as urgent as building infrastructure.

## **Background**

This paper originates from a few separate working-groups with professional journalists to identify pain points and to sketch out a range of use-cases for SSI, drawing in particular from the experiences of developing-world journalists and editors battling misinformation, misattribution, and other identity issues in the press. The[ "first world bias"](https://motherboard.vice.com/en_us/article/pakxby/silicon-valley-is-inserting-its-biases-into-nearly-every-technology-we-use) of tech platforms and social media has been discussed at length, so we take it for granted, but would add that the journalistic pain points around misattribution, misinformation, and privacy are felt much more acutely in developing nations with potential regime-changes imminent and more fraught relations between journalists and government.  In many cases, the journalists working in these contexts prove themselves to be early-adopters of a wide range of privacy technologies and publishing tools compared to their developed-world analogues.

One basic problem exacerbated by social-media manipulation and other misinformation campaigns is misattribution-- from doctored twitter screengrabs, to altered soundbytes to citations invented wholesale, this is a growing nuisance in the election cycles of the developing world. Many journalists have expressed a desire to extend the "verification" scheme of a closed platform (Twitter being the most common example) to something more cross-platform, such that with some degree of certainty whole articles could be cryptographically signed by a keyholder who has also signed public profiles like a twitter page, a public-facing registry, a facebook page, etc. Given that many news platforms are currently upgrading and expanding the technical capabilities of their CMS systems and backends, especially in countries battling misinformation proactively like Brasil and India, the timing would seem to be urgent.

Shifting existing systems of publishing towards SSI could take many forms, but the difficulty is in thinking through the consequences through many stakeholders and systems at an appropriate scale.  For this reason, this paper is broken down into a tentative glossary for controversial or local terms, some detailed use-cases, and finally some general observations about system capabilities and design principles that might be useful going forward.

## **Glossary**

Todo: bibliography (i.e., [w3c documentation](https://www.w3.org/TR/verifiable-claims-use-cases/#professional-credentials), [DOI documentation](http://www.doi.org/10DEC99_presentation/faq.html#1.6), etc.)

## **Use-cases**

The following use-cases apply to different kinds of publication, and are sorted from most local/individual to most systemic in scale:



1. **Privacy/VC for journalistic sources:****Example:** Journalist gets an anonymous tip from a “whisteblower” (a vulnerable source testifying to malfeasance within an organization where they work) claiming to work in a branch of government with information about a war-crime. After an entirely anonymous communication over encrypted channels, the whisteblower is able to present a VC of the length of their employment there and another about their rank/clearance within the organization-- not enough information to compromise their confidentiality, but enough to substantiate their (journalistic, legal, or other) claims.  

   **Ramifications:** Traditional journalistic ethics and legal frameworks around the confidentiality or anonymity of sources would have to evolve rapidly given this new mechanism.

   

2. **Privacy/VC for Authorship:** **Example**: Authors publishing work anonymously could still attest to being the **same** anonymous authors who previously wrote other pieces.  Anonymous authors could be paid for their work or contacted discreetly/securely after publishing their work without compromising their anonymity vis-a-vis the publishers or editors of that work.  The classic/manual example of this is the anonymous author(s) who published influential writing under the pseudonym Satoshi Nakamoto, who has used cryptography to vouchsafe the integrity of their output over a decade.

   **Ramifications:** The liability for publishing anonymous writing with real-world consequences (say, libelous writing) would fall on a publisher in many cases, which would hopefully act as some brake on the wide adoption of this phenomenon.  The proliferation of these kinds of leaks would greatly empower whisteblowers but also all kinds of anonymous libel, misinformation, etc-- hopefully any system that unleashes this kind of chaos would simultaneously or previously buttress the trust and integrity of legitimate and non-anonymous outlets in equal measure!

   

3. **Attestations made (and potentially unmade!) by a source in a published piece:**

   **Example:** Sources quoted at length or about very consequential/touchy matters like national security might want the capacity to publicly endorse/approve an article, and might revoke/deactivate that endorsement at a later date.

   **Ramifications:** Considering an interview subject or the office of a politician quoted at length in an article to be “co-authors” or endorsers of a piece could lead to drastically different workflows and trust systems around publication in complex and unforeseeable ways.  Given the legal complexity of the boundary of the concept of authorship, it is important to create an alternate structure for endorsements than co-signing/co-authoring a given piece of writing-- perhaps the endorsements of specific claims, paragraphs, or ideas need to be differentiated (conceptually and technically) from endorsements of whole publications; in cases where non-authors to review/veto and thus endorse whole pieces of writing rather than specific ideas or statements, that endorsement might correspond more to a secondary category like **reviewer** or **contributor** than to that of **author** or **co-author**.

   

4. **VC for journalistic research/fieldwork:** **Example:** Professional journalists doing various kinds of reporting need many certifications, security clearances, press passes, and permissions to investigate places, people, and institutions.  For instance, embedded journalists often have to do security trainings or background checks, while politically-sensitive or military researchers often need to do extensive security clearances, usually issued by government agencies but sometimes also by professional agencies, insurance companies, guilds, freelancer’s unions, etc. 

   **Ramifications:** Being able to reuse these credentials, or have them inspected more quickly and conveniently, might be a useful agent of adoption, particularly if it were the **only** way to have them inspected in specific contexts.  Even the process of being certified via SSI systems could be seen as a kind of “SSI training” that could make professional journalists of a non-technical nature early adopters and/or evangelists of SSI systems.  The safety and legal concerns specific to journalists (for instance, exposure to retribution for having publications) should be considered in public-sector credential/badging schemes.

   

5. **Identity and freelancing, ghostwriting, “bylines”, etc:** **Examples:** For many kinds of authors, having authorship credit divorced from the afterlife/permanence of publication would be useful and important, particularly if an immutable Verifiable Claim was issued about the publication.  Publishers of journals, newspapers, or other outlets often go out of business, neglect to maintain an archive or resist being archived by others, or take down portions or subsets of their own archive due to economic, editorial, or political changes.  In these cases, an author might benefit from being able to prove they wrote a piece that is no longer publicly available for any number of legal or professional reasons.  There are also kinds of writing like “ghost writing”, publically-uncredited co-authorship, review or contribution-- these granularities of semi-anonymous or contextual credit could be systematized by VCs and SSI.  
   **Ramifications:** Increasingly, the journalistic labor market is splintered, freelance, insecure, and even “uberized.” At least in the short-term, and likely in the long-term barring major upheavals in the business model of professional writing, journalists and professional writers across many industries stripes could benefit in many ways.  As with anonymous publication, however, the liability ramifications are complex when anonymous contributors get registered. As elsewhere, the security concerns around persecution of journalists, censorship, and retribution make more complicated the mechanisms of revocation-- a system which tracks all of an author’s publications needs to be in the author’s complete control to such an extent that “disowning” or deactivating a claim to authorship of an individual piece is always possible and resistant to tracking, correlation, etc.

   

6. **Blind peer review and anonymous contributions in research:** **Examples:** Academic research traditions are largely founded on anonymous review by “peers,” whom are selected and defined by a very squishy but relatively international discipline-specific consensus about qualifications and authorities.  VCs could attest to membership in the latter and allow some amount of accounting/record-keeping of this important kind of intellectual work without compromising anonymity.  Many professional researchers outside of academic traditions also benefit from having anonymous but verifiable claims made about contribution or review.

   **Ramifications:** The administration/remuneration of blind review and other kinds of contribution and review in the academic labor system is currently very informal (and **very** unequally distributed/applied, which might motivate adoption in that particular use case). Similarly, the often nebulous, informal, and opaque criteria by which publication activity is “measured” by internal and administrative review boards for tenure and promotion purposes (particularly as regards the shifting and unspoken boundary or weighting system of reputation systems) could be improved by the systemic use-cases mentioned below. Transparency and auditability of publicly-funded or nonprofit research could have complex ramifications for law and accounting.

   

7. **Media rights, “photo credits,” and intellectual property waivers/permissions:** **Examples:** People who own/control the media rights of images (their own likeness as models or amateurs, paintings they own, the Eiffel Tower, etc) could publically “sign off” on their images being authorized for use in a given publication.

   **Ramifications:** Verified claims about the sources, licensing, and authorization to reproduce images and other media could conceivably simplify some of the “grey areas” around fair use, copyright, and licensing in the publishing industry and beyond. Rather than a “negative”/reactive system where owners of images bear the burden of enforcing their ownership or control of images (and where unscrupulous lawyers comb the internet for people to bully within the grey areas and legal illiteracies of the current global system of media rights), a “positive” system could instead evolve in which reproduction rights and licensing is registered or publicized along with publication content.

8. **Fact-checking and Policing of Misinformation in Media** **Examples:** Media end-users (i.e. 99% of humans) today who weigh their social network very highly in their trust of media sources are the primary target of misinformation campaigns that can now reach them cheaper than ever before; media literacy isn’t keeping pace with new channels and platforms that are too easy to manipulate.  End-users in a near future could have much more robust toolset for tracing the sources of important information and finding the data they want.  Anchoring a new trust system in identity and auditability of identity can build robust, granular, systems for reputation and information sourcing.  It goes well beyond whitelists and blacklists, or “better” opaque centralized algorithms with massive realworld impacts (i.e. social media).  **Ramifications:** It’s important to conceptually distinguish between infrastructure and reputation systems, but incorporating SSI into the infrastructure of publication has immense ramifications for systems of rating and sorting publications by reliability, objectivity, or standards.  Content moderation (or “safety and trust” departments) on individual platforms as well as info/source ranking/sorting systems specific to individual platforms (search engines, social media, etc) would all benefit from (and have huge financial incentive to distort or control) any cross-platform trust networks.

9. **SSI-backed indexes of authorship and ownership of ideas expressed in writing:** **Examples:** Authors of academic papers or research that generated intellectual property are heavily invested in a public ledger of (time-stamped) authorship to settle claims of plagiarism, originality, parallel development, etc.

   **Ramifications:** If an SSI backed system that registers the signatures of all individual authors (and the DID controlled by the publishing journal or venue), a more reliable and granularly-permissioned identity layer is grafted on existing indexes that are the foundation of library science (searching and organizing publication) and intellectual property (owning and controlling intellectual property). Since titles of publications operate as something like “roots of trust” for publications (particularly in the context of indexes), cosigning publications with DIDs might be as important as providing DID signatures of the author(s).

   

10. **System effects of incorporating SSI into publication indexes:** **Examples:** This is the hardest use case to speculate about, but in a world where SSI-backed reputation systems have evolved out of SSI-backed publishing systems and registries, all kinds of end-user tools are available to a consumer of any kind (or quantity) of media. **Ramifications:** The complex data science of reputation in library science operated by librarians and archivists worldwide is a massive and delicate apparatus the disruption of which is to be avoided at all costs to avoid creating openings (technical, algorithmic, or social) for disinformation efforts. That said, archivists and librarians are, in the aggregate, a **very** eager and self-motivated demographic for adopting new privacy and auditing technologies that may be incorporated into their systems. Archivists and database buildings/stewards would probably welcome an identity layer and audit trail for publications. Public-facing librarians and media-literacy educators could be a crucial resource in the safest and modest robust adoption of SSI by the general public.

## **Design Principles for integration to the ecosystems of publishing and journalism**

## 1.) *Interoperability*

There are many existing global, digital identity systems to “play nice with,” and perhaps the most important integration is bootstrapping/integrating with the DOI system, a global decentralized namespace for research publication that is the backbone of citation networks like [ResearchGate.com](http://researchgate.com), [Academia.edu](http://academia.edu), and [ScholarlyHub](https://www.insidehighered.com/news/2017/11/09/scholars-plan-nonprofit-alternative-researchgate).  Maximizing the number of true SSI platforms supported by any implementation of this is crucial.

## 2.) *Adoption and evangelism*

Journalists and librarians are two absolutely crucial vectors for adoption of any technology or media-- they are debatably more important for how the broader public understands, adopts, and thinks about a given technology or practice than any others.  Perhaps the ramifications of SSI for journalists and publishers should considered separately from the equally important role journalists and publishers can play in SSI.  Future work is definitely needed!

## 3.) *Public Relations and Messaging*

Much of adoption boils down to messaging and public relations, particularly since there are currently **very** powerful forces at play trying to tamp down public outrage over surveillance capitalism and the limitations of social media and “platform capitalism”.  One key strategy, which can be seen in [this very thoughtful article ](https://onezero.medium.com/your-speech-their-rules-meet-the-people-who-guard-the-internet-ab58fe6b9231)about content moderation and the liability/regulation crisis around “content moderation”, is injecting a vocabulary of **trust**, **control**, and **traceability** into the public debate around social media and tech politics. (For instance, the linked article refers to content moderation departments as “trust and safety” departments!)

## 4.) *Immutability and archives*

Debates around the design of data structures and data sovereignty issues are not unique to computer science-- on the contrary, much of the deep conceptual work and philosophy about data structures comes from the centuries-old library science tradition.  The use cases above make clear the real world consequences for many of the details around immutability and revocability of credentials.  Recent initiatives to commit text-only “carbon copies” of publications to public blockchains or other immutable ledgers (such as those by [popula.com](https://popula.com/2018/08/07/introducing-the-blockchain-part-of-this-thing/), [civil](https://www.coindesk.com/civil-backed-news-site-archives-article-on-ethereum-blockchain), etc) and the conversation around “immutable publishing” will be a valuable aspect of SSI-powered publication systems.

## 5.) *Attention to rapidly-changing legal frameworks*

Intellectual property law (particularly in the international context of global commerce) is changing as rapidly as identity law (GDPR and eiDAS are important to consider vis-a-vis SSI).  Both vary wildly from country to country and from continent to continent!  Rooting discussion the use-cases while incorporating interlocutors from other countries, disciplines, and experiences might help foreground and center what SSI technology means for authorship and publication moving forward.
