# Using Immutable Data Objects to Define Verifiable Credential Data

Ken Ebert,
Sovrin Foundation,
ken@sovrin.org

## Abstract
Verifiable Credentials are strengthened by providing immutable data objects that
provide a full definition of the data being signed. 
This is particularly true for objects with ZKP style signatures,
where a more granular description of the data is required in order to support 
disclosure and predicate proofs on a per-property basis.

## Control Objects
Control objects, such as DIDs, revocation registries, and payment addresses, 
contain data required to establish control. 
It is expected that these objects need to change over time. 
Keys need to be rotated, credentials need to be revoked, 
and balances need to be updated.

## Data Objects
Data objects contain information that describes semantic meaning of 
verifiable credentials. 
In order to establish a cryptographic assurance of what is being signed in a 
verifiable credential, 
the definition of the meaning must not change after a credential is issued. 
Immutable data objects that provide this definition of meaning include:

### Verifiable Credential
A verifiable credential is a set of signed claims about a subject. 
The issuer and claims in the credential about the subject can be 
cryptographically verified to confirm that the issuer made those claims. 
The meaning of the claims is represented by other data objects.

Verifiable credentials are stored off-ledger to preserve privacy.

Verifiable credential definitions are specified in JSON-LD.

### Credential Definition
The credential definition identifies the issuer, an associated mapping, 
and public keys for this type of credential. 

Credential definitions are immutably stored on-ledger to provide access to the
materials used to verify any of the credentials issued using the definition.

Credential definitions are specified in JSON-LD.

### Mapping	
A mapping contains an ordered selection of properties from the source schema. 
For each property a corresponding encoding is specified to prepare the data for 
ZKP signatures. 
The primary objective of the mapping is to provide a sequence of numbers to sign 
in a ZKP style proof. 

Mappings are immutably stored on-ledger to provide the holder with the definition of 
each property and how that property was transformed into a number included in the 
ZKP proof.
Mappings can be shared between issuers to promote interoperability among trust 
frameworks established by communities of trust; multiple issuers can refer the same 
mapping from their respective credential definitions. Others outside the issuer’s 
trust framework may choose to trust credentials from the framework.

Mappings are specified in JSON-LD.

### Schema	
A schema defines the structure and type of data for claim data. 
Schemas can contain sub-schemas. Schemas can represent complex data objects. 
Schemas include properties such as type, label, and description. 
Standard schemas can be extended to incorporate definitions of properties not
previously included.
Many schemas already exist, such as those available at schema.org. 
Many schemas available on the internet do not have the property of immutability 
that can provide an unchanging definition of the properties signed in a 
verifiable credential.

Schemas are immutably stored on-ledger to provide the holder with the definition 
of each property. Mappings refer to the properties defined in the schema to select
properties for inclusion by an issuer in a verifiable credential. 
Schemas can be shared between mappings to promote interoperability. 
Verifiers’ presentation requests also refer to the schemas used in a 
verifiable credential to specify which properties from the verifiable
credential should be included in a derived presentation created by a holder. 
Multiple presentations can share schemas.  

Schemas are specified in JSON-LD.
	
### Context
A context is a collection of shortcut term definitions. 
Contexts establish definitions that promote efficiency while preserving accuracy. 

Contexts are immutably store on-ledger to provide the ecosystem with term 
definitions associated with verifiable credentials, credential definitions, 
mappings, encodings, presentation requests, presentations, etc. 
Changing a context could change the meaning of a signed verifiable credential.

Contexts are specified in JSON-LD.
	
### Encoding 
An encoding specifies the source data type and conversion algorithm used to 
transform a claim property to an attribute that can be signed using a 
ZKP style signature. ZKP signatures require an array of integer attributes. 
Some source data types can be converted to an integer in a way that does not support 
predicate proofs, such as “less than” or “greater than or equal”. 
For example, a source data type of string (stored as UTF-8) could be converted to 
an integer using a hashing algorithm, such as SHA-256. 
This converted attribute can be signed. 
However, in a presentation the value can only be disclosed or not disclosed; 
predicate proofs are not possible. 
Other encodings, such as dates, could be converted into seconds since 1970. 
This would allow the value to be disclosed or not disclosed; predicate proofs 
are also enabled. 
A proof such as “Age over 18” could be constructed to determine if an individual is 
an adult without revealing the individual’s age.

Encoding definitions are stored immutably on the ledger. 
Corresponding encoding algorithms are coded in approved and signed libraries.

Encoding definitions are specified in JSON-LD.

### Presentation Request
Presentation Requests describe to a holder the set of properties, types of proofs, 
and issuers that are acceptable to a verifier. 
Presentation requests can specify one or more sources for a presentation data element.
Graph paths are used to define the specific property from a source credential 
to be used in a derived credential, which will be included in the presentation. 
Proof types indicate whether the attribute value will be revealed or a predicate 
which must be satisfied. 
A list of acceptable issuers for a presentation data element is also specified.

Presentation requests can be stored immutably on the ledger in cases 
where reuse is important. 
However, a presentation request can be specific to a pair-wise relationship,
in which case, the presentation request can be stored off-ledger.

Presentation requests are specified in JSON-LD.

### Presentation
Presentations are a special case of a verifiable credential. 
Presentations contain derived claims from verifiable credentials. 
Presentations also contain cryptographic material for the proof of the derived claims.
In addition, where more than one verifiable credential was used 
to create the derived claims, 
the presentation must contain cryptographic material for 
proof that the source credentials are held by the same entity. 
In some instances a presentation may include self-asserted data 
not based on derived data from a verifiable credential. 
The verifier analyzes the presentation to substantiate claims using the 
cryptographic material.

Presentations are stored off the ledger by the verifier or deleted after use.

Presentations are specified in JSON-LD.

## Conclusion
Once a verifiable credential is issued it cannot be changed 
without breaking the cryptographic chain of trust. 
Similarly, once a verifiable credential is issued, 
the immutable data objects that provide 
a full definition of the data being signed cannot be changed 
without breaking the chain of trust.
