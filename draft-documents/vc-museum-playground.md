# Verifiable Credential playground-museum

In order to test our verifiable credential software, we need a corpus of claims that implementations can clearly succeed or fail against.  One of our main goals is to be neutral on all current candidates in use, and be able to show case some interopability.

We aim to first collect instances of Verifiable Credentials in a static database.

* Collect versions of JSON-LD with LD-Proofs
* Collect versions of JSON-LD with LD-Signatures
* Collect versions of JSON with JWT
* Collect versions of JSON-LD with JWT

We have some examples from 2017, but small changes have occurred in the DID formatting so the examples will need small updates.

We aim to second be able to make an initial specification what a site like this would need and initate the project as far as we come.

The goal is to have a developer-friendly playgrounds that shows the use of these credentials that will be open source and templated for easy expansion by the community.

## Existing playgrounds

* https://jwt.io
* https://w3c-vc.github.io/playground/
* https://json-ld.org/playground/

## Specs
* https://tools.ietf.org/html/rfc7519
* https://json-ld.org/spec/latest/json-ld/#dfn-graph
* https://json-ld.org/learn.html
* https://w3c.github.io/vc-data-model/
        
## Corpus
  
* collect a few 2017 examples
  * Kim's work
            https://github.com/WebOfTrustInfo/btcr-did-tools-js/blob/master/claims/kimh-knows-christophera.jsonld

  * https://w3c-vc.github.io/playground/

  * try to verify them using current libraries
            https://github.com/WebOfTrustInfo/btcr-did-tools-js/blob/master/claims/kimh-knows-christophera.jsonld
          
* JWT from uPort (node architecture) will generate VC from test example

* Will follow and look how the DIF interop project driven by Rouven Heck (Consensys), where Rouven and Martin Riedel's has come with simple suggestions that project will work on.

* Get a useful complicated graph of verifiable credentials

## Roadmap

* add usage notes to corpus (how should the fields be interprested)
  * which VC-spec versions is this VC believed to comply with?
  * how to interpret fields (local, or open-world model with @context?)
  * contributor
  * help contact
  * encoded text
  * decoded text
  * necessary DIDs
  * tested on libraries X,Y,Z  (VCs!)
  * deprecated?
  * git metadata...
  * related claims... / tags
  * intended result (verifies/fails)

* fork from existing javscript playground
* (BTCR specific) return SatoshiAuditTrail via CGI-script
        https://w3c-ccg.github.io/didm-btcr/
* (BTCR specific) return DIDdoc via CGI-script
* validate non-graph verifiable credential, encoded as JWT
* validate non-graph verifiable credential, encoded as JSON-LD
* try a verifiable credential with a graph, for JWT
* try a verifiable credential with a graph, for JSON-LD 
* validate Verifiable Credential (in a low-friction way)
* launch online (no requirements) playground for users
* write a joint statement on comparison tables for signature schemes JWT and LD-Proofs
        https://pr-preview.s3.amazonaws.com/w3c/vc-data-model/pull/384.html#syntax-and-proof-format-trade-offs
  * how do you encode a LD-Proof for transmission?  (pretty clear with JWT)
* review JSON-LD playground features to try to understand graph
        https://json-ld.org/playground/
        
