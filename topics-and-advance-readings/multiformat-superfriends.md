# The Multibase, Multihash, and Hashlink Specifications

By Manu Sporny and Ganesh Annan; Digital Bazaar

This document outlines three specifications that have recently become
work items of the W3C Credentials Community Group. The authors of these
specifications desire feedback from the Rebooting the Web of Trust community
to, if necessary, further expand the capabilities to address other use cases 
that are of importance to the individuals and organizations that attend RWoT8.

# Multibase

The Multibase specification was published a few weeks ago as an IETF
Internet-Draft. The specification is intended to be a joint work product
of Protocol Labs (IPFS and Filecoin), the W3C Digital Verification
Community Group, and the W3C Credentials Community Group.

So, what problem does Multibase solve and why do we care?

Our community encodes binary data in things like DID Documents and URLs.
For example, both the Veres One and Sovrin DIDs encode the public key in
the DID itself (these are legacy DIDs from past development versions,
and are provided for illustration purposes only):

did:v1:test:nym:z279ikfef3QbKRgnvTFmq5wEzZpe7s4fBiMb97hSEezXv3SL
did:sov:WRfXPg8dantKVubE3HX8pw

That bit at the end there is binary data (the public key) that is
"base-encoded" so that it's easy (for developers) to copy/paste that
stuff around and put it in emails when talking about technical things.
The problem is that we don't know what base-encoding format was used above 
(base64 with padding, base64url, base58btc)?

To solve this problem, we add a single byte to the beginning of the
encoded value, so this:

did:v1:test:nym:279ikfef3QbKRgnvTFmq5wEzZpe7s4fBiMb97hSEezXv3SL

turns into this (note the addition of 'z', which means "the data you are
about to read is encoded in Bitcoin's base-58 encoding"):

did:v1:test:nym:z279ikfef3QbKRgnvTFmq5wEzZpe7s4fBiMb97hSEezXv3SL

This is useful because this mechanism allows us to encode the same
information in a variety of different ways. For example, Ethereum folks
tend to use base16lower encoded values for their addresses while Bitcoin
folks use a Bitcoin flavor of base58. At some level, these are sort of
arbitrary decisions that developers fight over, but with Multibase, the
decision is translated into a simple matter of value conversion. You
don't have to fight over the base encoding format because Multibase
encodes it in the resulting value, making conversion simple and
deterministic and enabling future upgradability for your system (and
compatibility with other systems).

Multibase also allows developers to change the encoding format at a
later date because the software was written with upgradability in mind
from the beginning. The spec is a fairly short one, weighing in at 7
pages and can be found here:

https://tools.ietf.org/html/draft-multiformats-multibase-01

# Multihash

The Multihash specification was drafted before/during the last RWoT and
has been released as an IETF Internet-Draft. The specification is
intended to be a joint work product of Protocol Labs (IPFS and
Filecoin), the W3C Digital Verification Community Group, and the W3C
Credentials Community Group.

So, what problem does Multihash solve and why do we care?

Our community depends on cryptographic hashes to generate short
fingerprints for files and data. These fingerprints look like this as
binary data:

0x0a4ec6f1629e49262d7093e2f82a3278

While that may look like gobbledygook to a human reader, it's enough for
a computer to uniquely identify, for example, one picture among all of
the other trillions of pictures on the Web. We use these fingerprints
when working with Verifiable Credentials, DIDs, public keys, and
evidence data (images, PDFs, etc.) that are linked to Verifiable Credentials.

The problem is that we don't know what sort of cryptographic hash
function generated the hash above, so we need to put an identifier at
the front of that cryptographic hash. That's basically what Multihash
does: it provides a mechanism to identify how cryptographic hashes were
generated.

This is useful because if we have a cryptographic hash identifier, we
can design upgradability into the systems we're building today.
Cryptographic hashing systems are broken every 10 years or so -- they
have a shelf life and will eventually need to be upgraded. Building this
concept of upgradability into our systems, especially 
Decentralized Identifiers and Verifiable Credentials, is a good engineering 
practice and the Multihash spec enables us to do just that. It's a fairly 
short 10 page spec and can be found here:

https://tools.ietf.org/html/draft-multiformats-multihash-00

# Hashlink

The Hashlink specification is intended to be a way to enforce that the content 
at a given hyperlink has not changed since it was published.

The specification is a joint work product of the W3C Digital Verification 
Community Group, JSON-LD WG (unofficial), VCWG (unofficial), and the W3C 
Credentials Community Group.

Ok, so what's the problem and why do we care?

We do the following things in this community:

 * Link to JSON-LD Contexts
 * Link to ZKP Schemas
 * Link to evidence from Verifiable Credentials
 * Link to external data from DID Documents

... and we have no way to tell if the content at the end of that link
has changed since the Verifiable Credential was issued, or the DID
Document was created.

In the best case, verification of the cryptographic signature fails
(because the content at the end of the link changed). In the average
case, the signature doesn't fail, and we use data that may have been
modified. In the worst case, the data was modified by an attacker and
really bad things happen (like a developer being sloppy with how they
use JSON-LD Contexts in a financial system and the source/destination
fields being flipped in a financial transaction). There are mitigations
for all of these issues, but they require the developer to be aware of
the problem in the first place.

What would be great is if we could trust that when we use a hyperlink in
our systems (like a Verifiable Credential or a DID Document), and
digitally sign that hyperlink, that we're also signing the content at
the hyperlink. That's what the hashlink specification enables us to do.

Here's a simple example for the JSON-LD Context for the current DID
Spec. Here's the current link:

https://w3id.org/did/v0.11

You have no idea if the version you retrieved and the version I
retrieved are the same. Now, here's what it looks like when we secure it
with a "Legacy URL" Hashlink (blake2b 8 byte multihash + base58btc
multibase):

https://w3id.org/did/v0.11?hl=z3aq31uzgnZBuWNzUB

Now we both know that the version we download is the same (because of
the little bit at the end starting with "hl=", which stands for
Hashlink). Here's what it looks like as a (non-legacy) Hashlink URL:

hl:z3aq31uzgnZBuWNzUB:zpr1Xd34f3NYqfr1yMzb6TBCrWWrvJeGVRJGsUMMyVWXS8

Yes, that looks awful, but there are a number of redeeming
characteristics with the second form. The first is that the latter value
is optional -- you can discard everything after the second colon and
it's still a valid Hashlink URL. All you really need is
"hl:z3aq31uzgnZBuWNzUB" and you can get the data from anywhere else
(like different URLs, a local cache, etc.) and still thwart the attacks
listed above.

The other nice thing about Hashlink URLs, and this is the really
exciting bit, is that you can create multi-sourced hashlinks that span
completely different network architectures. Let's say that you had
information that you really wanted to make sure didn't disappear (like
the DID JSON-LD Context above), and you publish it at the following
locations:

https://w3id.org/did/v0.11

magnet:?xt=urn:btih:73C59D931B7E0C089C031D6CFE0D16AE

ipfs://ipfs/QmR7W4GQUFWDPMVrQfmNE8xJC6LoVAyaWeRnDp4gS9/did-v0.11

onion://pq6kufupl4mc43g2/didv0.11

The Hashlink URL would be really long, something like this:

hl:z3aq31uzgnZBuWNzUB:zeGVRWXS8TakFeJueF2bim3PaaDqbtqjkpxUc8ETS
WXe6dQLWXQWvqiUdw8TJrncx3uKhwfc88MtM5xZbR27FhVRUKv9ogekamVtdE3U
bXnXpMRT1AseCtoBUt1NE8x2SsnJxGfiZN45VVSCp6jh4dgcufL16tWrHREiSYE
SEGP1J75yXCvAdvKPr7nb5aY

... but the Hashlink URL above 1) ensures the integrity of the thing
you're linking to, and 2) still works if 3 out of the 4 networks listed
above failed. To put it another way, the link above could survive (for
example) the failure of the Web, BitTorrent, and Tor.

This approach also solves the following problems that other communities
in our orbit are having by:

* JSON-LD WG: Enabling backwards-compatible content integrity for JSON-
  LD Contexts.
* JSON-LD WG: Enabling non-Web-based, multi-sourced, compact, content
  integrity for JSON-LD Contexts.
* Sovrin: Enabling content integrity protected blockchain-based ZKP
  Schemas to be hosted on the Sovrin ledger (and Web-based
  locations) and referenced from Verifiable Credentials.
* IPFS: Enable organizations to dip their toes into IPFS as a "backup
  mechanism" w/o having to fully commit to jumping in with both
  feet.
* Verifiable Credentials WG: All the JSON-LD benefits above and the
  ability to digitally sign content integrity protected
  hyperlinks to evidence, terms of use, and any other information
  linked to from a Verifiable Credential.
* Credentials CG: Include links to data from DID Documents where the
  content at the links are secured by the cryptography of the
  ledger.

The specification is 9 pages long and can be found here:

https://tools.ietf.org/html/draft-sporny-hashlink-02

# Collaboration

A few of the authors and implementers of these specifications will be at 
RWoT8 and are very interested in educating the community about these 
specifications and getting feedback from the community about these 
specifications in order to improve them before large scale implementation
begins.
