# The Current Status of the DID Specification

By Amy Guy and Dmitri Zagidulin, Digital Bazaar

Work on the [Decentralized Identifier 1.0 specification](https://w3c-ccg.github.io/did-spec/) began at RWOT \#2 in May 2016, and a draft was published on 21 November 2016. Work continues under the custody of the [W3C Credentials Community Group](https://www.w3.org/community/credentials/), a group of 237 members, who contribute by taking part in [weekly teleconference calls](https://w3c-ccg.github.io/meetings/), engaging in discussions on the [mailing list](https://lists.w3.org/Archives/Public/public-credentials/), and [raising issues on the spec on GitHub](https://github.com/w3c-ccg/did-spec/issues/). 

This document serves as a summary of the current state of work. It includes a rough categorization of the current open issues, with the goal of identifying actions which can be taken quickly to move the spec forward, as well as topics which need extended discussion amongst the community. Issues (and sometimes PRs) are categorized as follows:

* **clarity**: Clarification or disambiguation of concepts the community already has consensus on.
* **discuss**: Topics which need more discussion to reach consensus about. 
* **editorial**: Updates to informative language, without changes to meaning or conformance criteria.
* **elsewhere**: Issues relating to other documents (specs, namespaces, etc).
* ..

If you're new to DIDs, or want a refresher on the background and core concepts of the DID spec, you will find it useful to read the [DID Primer](did-primer.md) (or [extended DID Primer](did-primer-extended.md)) first.

This document will be updated as work on the DID specification progresses, so information will be current at the time of RWOT8.

## Clarification needed

Some topics have consensus amongst members of the Community Group, or are intuitively understood by people who have been deeply embedded in the work for a while, but remain unclear with regards to text in the specification. For these, the spec needs new text, or reworking of existing text, to make sure concepts are communicated clearly and unambiguously to new readers.

Issues are labeled '[clarity](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Aclarity)' and include:

* The scope and purpose of the DID specification ([#158](https://github.com/w3c-ccg/did-spec/issues/158), [#157](https://github.com/w3c-ccg/did-spec/issues/157), [#121](https://github.com/w3c-ccg/did-spec/issues/121), [#138](https://github.com/w3c-ccg/did-spec/issues/138)).
* What is a DID? ([#130](https://github.com/w3c-ccg/did-spec/issues/130), [#156](https://github.com/w3c-ccg/did-spec/issues/156), [#155](https://github.com/w3c-ccg/did-spec/issues/155), [#141](https://github.com/w3c-ccg/did-spec/issues/141), [#140](https://github.com/w3c-ccg/did-spec/issues/140), [#125](https://github.com/w3c-ccg/did-spec/issues/125), [#124](https://github.com/w3c-ccg/did-spec/issues/124), [#123](https://github.com/w3c-ccg/did-spec/issues/123), [#122](https://github.com/w3c-ccg/did-spec/issues/122), [#115](https://github.com/w3c-ccg/did-spec/issues/115)).
* Which parts of the spec comprise the data model ([#151](https://github.com/w3c-ccg/did-spec/issues/151))
* Use of '[distributed] ledger'. ([#150](https://github.com/w3c-ccg/did-spec/issues/150), [#149](https://github.com/w3c-ccg/did-spec/issues/149)).
* Questions about keys ([#147](https://github.com/w3c-ccg/did-spec/issues/147), [#143](https://github.com/w3c-ccg/did-spec/issues/143), [#105](https://github.com/w3c-ccg/did-spec/issues/105)).
* ABNF rules ([#136](https://github.com/w3c-ccg/did-spec/issues/136), [#135](https://github.com/w3c-ccg/did-spec/issues/135), [#131](https://github.com/w3c-ccg/did-spec/issues/131)).
* Decentralization and practicality. ([#133](https://github.com/w3c-ccg/did-spec/issues/133), [#120](https://github.com/w3c-ccg/did-spec/issues/120)).
* Service endpoints [#104](https://github.com/w3c-ccg/did-spec/issues/104).
* Content types [#84](https://github.com/w3c-ccg/did-spec/issues/84).

Action: The CG should agree definitive definitions or statements for each of these, and then work to integrate them into the spec text.

## Bigger discussion points

Some topics need deeper discussion to ensure common understanding amongst the CG and the wider community, or more technical work to make sure the are resolved properly.

Issues are labeled '[discuss](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Adiscuss)' and include:

* Do we need to explicitly name the thing that the DID identifies? (Or, consolidate casual references to the thing the DID identifies?) Eg. 'referent', 'entity', 'subject', .. ([#154](https://github.com/w3c-ccg/did-spec/issues/154), [#148](https://github.com/w3c-ccg/did-spec/issues/148), [#145](https://github.com/w3c-ccg/did-spec/issues/145), [#130](https://github.com/w3c-ccg/did-spec/issues/130), [#139](https://github.com/w3c-ccg/did-spec/issues/139)).
* Resolving URIs in DID Documents ([#97](https://github.com/w3c-ccg/did-spec/issues/97), [#90](https://github.com/w3c-ccg/did-spec/issues/90), [#85](https://github.com/w3c-ccg/did-spec/issues/85), [#80](https://github.com/w3c-ccg/did-spec/issues/80)).
* Key revocation ([#96](https://github.com/w3c-ccg/did-spec/issues/96)).
* DID method discovery ([#83](https://github.com/w3c-ccg/did-spec/issues/83)).

Action: ...discuss.. at RWOT?

## Smaller todos

Editorial issues, such as grammatical fixes or reworking sentences without changing the meaning, and perhaps structural changes like section naming or ordering, are labeled '[editorial](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Aeditorial)' and include:

* s/Description/Document: [#144](https://github.com/w3c-ccg/did-spec/issues/144)
* Clearer language / small correction requested: [#137](https://github.com/w3c-ccg/did-spec/issues/137), [#129](https://github.com/w3c-ccg/did-spec/issues/129), [#128](https://github.com/w3c-ccg/did-spec/issues/128), [#127](https://github.com/w3c-ccg/did-spec/issues/127), [#126](https://github.com/w3c-ccg/did-spec/issues/126), [#119](https://github.com/w3c-ccg/did-spec/issues/119), [#118](https://github.com/w3c-ccg/did-spec/issues/118), [#117](https://github.com/w3c-ccg/did-spec/issues/117), [#116](https://github.com/w3c-ccg/did-spec/issues/116), [#112](https://github.com/w3c-ccg/did-spec/issues/112), [#81](https://github.com/w3c-ccg/did-spec/issues/81)
* Additional explanation requested: [#134](https://github.com/w3c-ccg/did-spec/issues/134)
* Fixing references: [#132](https://github.com/w3c-ccg/did-spec/issues/132).
* Json pointer: [#86](https://github.com/w3c-ccg/did-spec/issues/86), [PR #107](https://github.com/w3c-ccg/did-spec/pull/107).
* MIME type: [#82](https://github.com/w3c-ccg/did-spec/issues/82).

Action: PRs please!

## External documents

Some aspects of the DID work are eventually extracted into separate specifications. There are other external documents which are connected to the spec. Issues relating to these are labeled '[elsewhere](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Aelsewhere)' and include:

* JSON-LD context(s): [#152](https://github.com/w3c-ccg/did-spec/issues/152).
* Related to DID Resolution: [#114](https://github.com/w3c-ccg/did-spec/issues/114), [#97](https://github.com/w3c-ccg/did-spec/issues/97), [#64](https://github.com/w3c-ccg/did-spec/issues/64), [#17](https://github.com/w3c-ccg/did-spec/issues/17).
* Signatures: [#60](https://github.com/w3c-ccg/did-spec/issues/60), [#56](https://github.com/w3c-ccg/did-spec/issues/56), [#39](https://github.com/w3c-ccg/did-spec/issues/39), [#38](https://github.com/w3c-ccg/did-spec/issues/38), [#37](https://github.com/w3c-ccg/did-spec/issues/37), [#29](https://github.com/w3c-ccg/did-spec/issues/29).

## Questions, implementation guidance

Some issues are opened by people with questions about the spec (which don't need spec changes to answer) or requests for guidance about implementations or technical details. These are labelled '[question](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Aquestion)' and include:

* Non-blockchain DIDs? [#113](https://github.com/w3c-ccg/did-spec/issues/113)
* DIDs for devices? [#100](https://github.com/w3c-ccg/did-spec/issues/100)
* Inviting CCG participants [#92](https://github.com/w3c-ccg/did-spec/issues/92).

Action: answer the commenter's question(s), check they are happy, and close the issue.

## Next steps

------------------

# Notes

## Unsorted

* [#101](https://github.com/w3c-ccg/did-spec/issues/101) - resolved! 
* [#142](https://github.com/w3c-ccg/did-spec/issues/142) - I think this is resolved by removal of 'ownership' language?
* [#153](https://github.com/w3c-ccg/did-spec/issues/153) - ?
* [#160](https://github.com/w3c-ccg/did-spec/issues/160) - elsewhere?

