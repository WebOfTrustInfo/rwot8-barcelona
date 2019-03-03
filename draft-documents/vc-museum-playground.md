# Verifiable Credential playground-museum

In order to test our verifiable credential software, we need a playground-museum of claims that implementations can clearly succeed or fail against.  One of our main goals is to be neutral on all current candidates in use, and be able to show case some interopability.

We want this service to be a collection point, viewing point and playground for community VCs out there. So it is possible to understand how others have done their claim, get a better understanding of interopability, create guidelines for the community on how to build your VCs.

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

Data has to be collected from the community, so this draft initates the collecting of VCs from a simple form.

So please help us get up to speed on what types of VCs that exist out there, and how they are understood through this link: https://airtable.com/shr4ctJ5aJxkZEWkR

#### Examples we want to see
* Graph VC's
* Real usecase VC's
* User facing VC's
* VC's used between machines

#### Already existing examples
* Kim Hamiltons's examples: https://github.com/WebOfTrustInfo/btcr-did-tools-js/blob/master/claims/kimh-knows-christophera.jsonld
                   
* Test suite from W3C VC WG https://github.com/w3c/vc-test-suite

## The playground
For the playground to work intitially, and without any interopability protocol or library, we need to build a bridge between all VCs that has been collected, or is beeing inputed.
#### Existing libraries
##### General purpose bitcoin client
* bitcoinjs-lib (tested 3.3.2): https://github.com/bitcoinjs/bitcoinjs-lib
##### DID Method specific
* jsonld-signatures (tested 2.3.1): https://www.npmjs.com/package/jsonld-signatures
* txref-conversion-js     : https://github.com/WebOfTrustInfo/txref-conversion-js.git

# Execution phases
### Phase 1
#### Collection
* Collect versions of JSON-LD with LD-Proofs that conform with what the examples we want to see
* Collect versions of JSON-LD with LD-Signatures that conform with what the examples we want to see
* Collect versions of JSON with JWT that conform with what the examples we want to see
* Collect versions of JSON-LD with JWT that conform with what the examples we want to see

#### Playground initiation
* Start a code template for the playground so collaboration can grow.
* Get it hosted openly so it is easy to contribute

### Phase 2
#### Viewing VCs
* Create a flexible way to view the VCs in the museum part.
* Look at integrating with Satyrn for a better playground.

#### Understand the verifying of VCs
* Start mapping the libraries that people use to verify VCs
* Specing up first version of solution that can work as an interopability solution

#### Initiate a comparison table
* Write a joint statement on comparison tables for the different schemas that has come in, with inspiration from https://pr-preview.s3.amazonaws.com/w3c/vc-data-model/pull/384.html#syntax-and-proof-format-trade-offs

### Phase 3
####  Verifying the simplest VCs
* Start to verify the simples VC examples that is collected
* Built out the interopability solution for the simples examples

#### Build a feedback loop
* Develop a feedback view for the different simple VCs. This feedback loop includes:
    * Which VC-spec versions does this comply with
    * Deprecated?
    * Are these fields connected with an open-world model
    * Tested on libraries X,Y,Z
    * Decoding all text

### Phase 4
#### Spec up the next level of VCs
* Start specing up the interopability solution for next level of VCs, in terms of complexity.

#### Initiate interop transportation examples
* Proof of concept integration with SSI method with the playground to be able to experiment with transportation methods.

### Phase 5
#### Graphing out data collected
* Are there related claism


## Questions that is still not clear
* (BTCR specific) return SatoshiAuditTrail via CGI-script
        https://w3c-ccg.github.io/didm-btcr/
* (BTCR specific) return DIDdoc via CGI-script

* how do you encode a LD-Proof for transmission?  (pretty clear with JWT)