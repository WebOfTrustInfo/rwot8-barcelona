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

## Clarification needed

Some topics have consensus amongst members of the Community Group, or are intuitively understood by people who have been deeply embedded in the work for a while, but remain unclear with regards to text in the specification. For these, the spec needs new text, or reworking of existing text, to make sure concepts are communicated clearly and unambiguously to new readers.

Issues are labeled '[clarity]()' and include:

* The scope and purpose of the DID specification. ([#158](https://github.com/w3c-ccg/did-spec/issues/158), [#157](https://github.com/w3c-ccg/did-spec/issues/157), [#121](https://github.com/w3c-ccg/did-spec/issues/121), [#138](https://github.com/w3c-ccg/did-spec/issues/138))
* What is a DID? ([#130](https://github.com/w3c-ccg/did-spec/issues/130), [#156](https://github.com/w3c-ccg/did-spec/issues/156), [#155](https://github.com/w3c-ccg/did-spec/issues/155), [#141](https://github.com/w3c-ccg/did-spec/issues/141), [#140](https://github.com/w3c-ccg/did-spec/issues/140))
* Which parts of the spec comprise the data model. ([#151](https://github.com/w3c-ccg/did-spec/issues/151))
* Use of '[distributed] ledger'. ([#150](https://github.com/w3c-ccg/did-spec/issues/150), [#149](https://github.com/w3c-ccg/did-spec/issues/149))
* DID operations and CKMS. ([#147](https://github.com/w3c-ccg/did-spec/issues/147))
* Embedding public keys. ([#143](https://github.com/w3c-ccg/did-spec/issues/143))
* Registries. ([#133](https://github.com/w3c-ccg/did-spec/issues/133))
* ABNF rules. ([#136](https://github.com/w3c-ccg/did-spec/issues/136), [#135](https://github.com/w3c-ccg/did-spec/issues/135))

Action: The CG should agree definitive definitions or statements for each of these, and then work to integrate them into the spec text.

## Bigger discussion points

Some topics need deeper discussion to ensure common understanding amongst the CG, and the wider community.

Issues are labeled '[discuss]()' and include:

* Do we need to explicitly name the thing that the DID identifies? (Or, consolidate casual references to the thing the DID identifies?) Eg. 'referent', 'entity', 'subject', .. ([#154](https://github.com/w3c-ccg/did-spec/issues/154), [#148](https://github.com/w3c-ccg/did-spec/issues/148), [#145](https://github.com/w3c-ccg/did-spec/issues/145), [#130](https://github.com/w3c-ccg/did-spec/issues/130), [#139](https://github.com/w3c-ccg/did-spec/issues/139))

Action: ...discuss.. at RWOT?

## Smaller todos

Editorial issues, such as grammatical fixes or reworking sentences without changing the meaning, and perhaps structural changes like section naming or ordering, are labeled '[editorial]()' and include:

* s/Description/Document: [#144](https://github.com/w3c-ccg/did-spec/issues/144)
* Clearer language requested: [#137](https://github.com/w3c-ccg/did-spec/issues/137)
* Additional explanation requested: [#134](https://github.com/w3c-ccg/did-spec/issues/134)

Action: PRs please!

## External documents

Some aspects of the DID work are eventually extracted into separate specifications. There are other external documents which are connected to the spec. Issues relating to these are labeled '[elsewhere]()' and include:

* Update (or note stability of) JSON-LD context(s). ([#152](https://github.com/w3c-ccg/did-spec/issues/152))

## Next steps

------------------

# Notes

## Unsorted

* [#101](https://github.com/w3c-ccg/did-spec/issues/101) - resolved! 
* [#142](https://github.com/w3c-ccg/did-spec/issues/142) - I think this is resolved by removal of 'ownership' language?
* [#153](https://github.com/w3c-ccg/did-spec/issues/153) - ?
