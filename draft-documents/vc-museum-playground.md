# Verifiable Credential playground-museum

In order to test our verifiable credential software, we need a playground-museum of claims (a test suite of collected claims) that implementations can clearly succeed or fail against.  One of our main goals is to be neutral on all current candidates in use, and be able to showcase some interoperability.

We want this service to be a collection point, viewing point and playground for community VCs out there.  We aim to make it possible to understand how others have generated credentials, get a better understanding of interopability, and recommend libraries that are compliant with the specification.

This will be both an informative draft and a specification on what will be built over 5 phases, if time allows for it.

## Existing playgrounds

* Verifiable Claims playground
    * https://w3c-vc.github.io/playground/
* JSON-LD playground
    * https://json-ld.org/playground/
* JWT encode/decode
    * https://jwt.io

## Specs, Docs
* VC data model
    * https://w3c.github.io/vc-data-model/
* JSON-LD
    * https://json-ld.org/spec/latest/json-ld/
* JSON-LD documentation
    * https://json-ld.org/learn.html
* JWT
    * https://tools.ietf.org/html/rfc7519
        
## The museum

Data has to be collected from the community, so this draft initates the collecting of VCs in two ways:

* From **a simple webform**.  Please help us get up to speed on what types of VCs exist out there, and how they are understood, through this upload form: https://airtable.com/shr4ctJ5aJxkZEWkR

* Via **Github pull requests**.  You will find directions here: https://github.com/w3c-ccg/vc-examples/blob/master/via-pull-requests/HOWTO-contribute.md

#### Examples we are curious about
* Graph VC's
* Real usecase VC's
* User facing VC's
* VC's used between machines

#### Already existing examples
* Kim Hamiltons's examples: https://github.com/WebOfTrustInfo/btcr-did-tools-js/blob/master/claims/kimh-knows-christophera.jsonld
                   
* Test suite from W3C VC WG https://github.com/w3c/vc-test-suite

## The playground
For the playground to work intitially, and without any interopability protocol or library, we need to build a bridge between the VCs that we have been made aware of.
#### Existing libraries
##### General purpose bitcoin client
* bitcoinjs-lib (tested 3.3.2): https://github.com/bitcoinjs/bitcoinjs-lib
##### DID Method specific
* jsonld-signatures (tested 2.3.1): https://www.npmjs.com/package/jsonld-signatures
* txref-conversion-js     : https://github.com/WebOfTrustInfo/txref-conversion-js.git

# Execution phases
### Phase 1
#### Collection
* Collect VCs made as JSON-LD with LD-Proofs, that this community is curious about
* Collect VCs made as JSON-LD with LD-Signatures, that this community is curious about
* Collect VCs made as JSON with JWT, that this community is curious about
* Collect VCs made as JSON-LD with JWT, that this community is curious about

#### Playground initiation
* Start a code template for the playground so collaboration can grow.
* Get it hosted openly so it is easy for developers to improve the playground.

### Phase 2
#### Viewing VCs
* Create a flexible way to view the VCs in the museum.
* Look at integrating with Satyrn (an all-Javascript Jupyter-like single-page workspace) for a better playground.

#### Understand the verification processs of VCs
* Start mapping the libraries that are being used to verify VCs.
* Specify a version 1.0 playground that can show interopability progress.

#### Initiate a comparison table
* Write a joint statement on comparison tables for the different schemas that have come in, with inspiration from https://pr-preview.s3.amazonaws.com/w3c/vc-data-model/pull/384.html#syntax-and-proof-format-trade-offs

### Phase 3
####  Verifying the simplest VCs
* Programatically verify the VC examples that are collected.
* Build out the interopability solution for the examples.
    * (BTCR specific) return SatoshiAuditTrail via CGI-script https://w3c-ccg.github.io/didm-btcr/
    * (BTCR specific) return DIDdoc via CGI-script

#### Build a feedback loop
* Develop a feedback view for the different simple VCs. This feedback loop includes:
    * Which VC-spec versions does this comply with?
    * Deprecated?
    * Are these fields connected with an open-world model?
    * Tested on libraries [X,Y,Z]
    * Decoding all text
    * Signatures valid
* Add possibilities to tweak the VCs for different feedback.  This could mean trying a different context, or encoding differently, or siging with a different key available in the DIDdoc.

### Phase 4
#### Initiate interop transportation examples
* Proof of concept integration of an SSI method with the playground, to be able to experiment with transportation methods.

### Phase 5
#### Graphing out data collected
* Are there related claims so we can explore synergies?


# Questions that are still not clear
* What is the recommended encoding of an LD-Proof for transmission?  (pretty clear with JWT)
* What are the best transmission methods?