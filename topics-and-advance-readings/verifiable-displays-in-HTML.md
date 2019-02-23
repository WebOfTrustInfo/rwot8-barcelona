# Verifiable Displays: secure presentation of Verifiable Credentials in HTML

Authors: Bohdan Andriyiv (bohdan.andriyiv@validbook.org)

Keywords: Verifiable Displays, Verifiable Credentials, Hashlinks, HTML

## Abstract
This paper describes a way to create tamper-proofed, future-proofed, "anywhere renderable" bundles of Verifiable Credentials and their Verifiable Displays, by embedding Verifiable Credentials and their Verifiable Displays into HTML files and linking them with Hashlinks. 

This paper is a continued exploration of the problem and proposals discussed in the paper - [Verifiable Displays](https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/topics-and-advance-readings/verifiable_displays.md). It uses understandings and developments from [Resource Integrity Proofs](https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/topics-and-advance-readings/resource-integrity-proofs.md) paper and  [Hashlinks - Cryptographic Hyperlinks](https://tools.ietf.org/html/draft-sporny-hashlink-02) specification.

## Problem Statement

The [Verifiable Credentials Data Model](https://w3c.github.io/vc-data-model/) is an emerging standard for expressing credentials such as driver's licenses, degrees, and passports on the Web in a secure, privacy respecting manner. The "Verifiable" part is because they are designed to be _cryptographically_ and _machine_ verifiable.

This emphasis on cryptogrphic machine verification is essential, but what’s not in scope of the VC Data Model is scenarios where a human participates in verification.

A human person is typically not looking at the content in a raw json format (this content is cryptographically signed/verifiable); instead they are looking at a styled representation of the content: PDF, HTML, SVG, etc.

The questions arise: 
 - How does the consumer of Verifiable Credential know that the friendly display they see is what the issuer signed/intended? 
 - How does the issuer know that the consumer will see the intened display, when it went through intermediary hands? 
 - In general, how to know that the display matches the content? 
 - Time-related concerns to credentials display: 
 -- How to ensure, everlasting longevity of the Verifiable Credential display? 
 -- In other words, how to make sure that display of the credential is going to be renderable and verifiable in the distant future? 


## HTML, Verifiable Displays, Verifiable Credentials, Hashlinks  - tying all together

[HTML](https://www.w3.org/TR/html52/) is a ubiquitous standard used to present data on the Internet. It can be rendered (opened) by all Internet related tools (most importantly by the Internet browsers). Therefore it is the best candidate to be used to display Verifiable Credentials.

[Verifiable Displays](https://hackmd.io/x9XKZZPvQ026YLuZUlcm7w?both#Embedding-Verifiable-Credential-and-Verifiable-Display-into-one-HTML-file) is a visual representation of Verifiable Credentials. It can be created by using any text or image format that can be embedded into HTML and rendered by typical Internet browser.

[Verifiable Credentials](https://w3c.github.io/vc-data-model/) is a JSON based specification to express cryptographically verifiable data.

[Hashlink](https://tools.ietf.org/html/draft-sporny-hashlink-02) is a newly proposed internet standard that provides a universal future-proofed way to reference data and ensure its integrity. 

### Using Hashlink to reference Verifiable Display from Verifiable Credential

   The example below demonstrates a simple hashlink that provides content integrity protection for the "http://example.org/hw.txt" file, which has a content type of "text/plain":

hl:zQmWvQxTqbG2Z9HPJgG57jjwR154cKhbtJenbyYTWkjgF3e:zuh8iaLobXC8g9tfma1CSTtYBakXeSTkHrYA5hmD4F7dCLw8XYwZ1GWyJ3zwF

Please, see in [Hashlink specification](https://tools.ietf.org/html/draft-sporny-hashlink-02) the detailed description of how this hashlink is created.

_TODO:_
 *- Provide description of standard metadata in hashlink that references Verifiable Display that is only locally available. For example - "BundledIntoHTML", "BundledIntoSVG", "local".*
_Maybe, better to use hashlink as parametrized URL? - http://BundledIntoHTML?hl=zQmWvQxTqbG2Z9HPJgG57jjwR154cKhbtJenbyYTWkjgF3e_

 *- Provide standard way to add into Verifiable Credential hashlink that references its Verifiable Display.* *Example:*
```
 "reference": {  
            "type":["VerifiableDisplay"],
            "hl":"http://BundledIntoHTML?hl=zQmWvQxTqbG2Z9HPJgG57jjwR154cKhbtJenbyYTWkjgF3e"
            }
```



### Embedding Verifiable Credential _and_ Verifiable Display into HTML file

Verifiable Display may be created by using any text or image format that can be embedded into HTML and rendered by typical Internet browser. 

Store Verifiable Display in first `<div>` element with attribute `data-type = "Verifiable Display"`, and attribute `hl = "_hash_value_of_hashlink"`

Store Verifiable Credential in  `<head>` block, within `<script type="application/ld+json">` element.

Embedding algorithm:
- Create Verifiable Display 
- Create Hashlink that references this Verifiable Display
- Add Hashlink into Verifiable Credential
- Create HTML file with Verifiable Credential embedded into `<head>` block, and Verifiable Display embedded into `<div>` element with attribute `data-type = "Verifiable Display"` 

Verification algorithm:
- Parse Verifiable Credential from the `<head>` block
- Parse hash value from Hashlink that references correct Verifiable Display
- Take content of the `div` element that is being presented to the user and calculate its hash using the same hash algorithm, that is used in Hashlink taken from Verifiable Credential 
- Compare calcualted hash value with hash value from Verfiaible Credential. If they are the same Verifiable Display is correct, if they are not the same Verifiable Display has been tempered with  

See here [HTML example](https://drive.google.com/uc?export=download&id=1a87-uNSPoBJdav5rP6Q1sAp5Dnp-sCNV) and [SVG example](https://drive.google.com/uc?export=download&id=1ePvJqpmFgrXcvdRxld104DMY129385gd) of HTML files with embedded Verifiable Credentials and their Verifiable Displays.

> Example implementation: You can see how verification of Verifiable Displays may look like at at: [Validbook Statements service](http://futurama1x.validbook.org/statements). To do this, login as the test user - “Jimbo Fry” using this [private key](https://drive.google.com/uc?export=download&id=1_ZDoXh4aBUQXR50PLRusZRF7XvEY3OQx) (password to private key file: “123456789”). After login go manually to the [Validbook Statements service](http://futurama1x.validbook.org/statements), use Chrome browser.) 


## Conclusion
In this paper we proposed the outline of the specification for tamper-proofed, future-proofed, "anywhere renderable", "truly portable" bundles of Verifiable Credentials and their Verifiable Displays, by embedding them into HTML files and linking them with Hashlinks.


## Questions

- How to use Hashlink to reference data that is part of HTML file? (describe hashlink metadata) 




















