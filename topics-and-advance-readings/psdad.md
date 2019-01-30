
# PSDAD - A new data format with secure semantics

Submission to: [Rebooting the Web of Trust #8](https://github.com/WebOfTrustInfo/rwot8-barcelona) (March 2019, Barcelona)

Author: [Sandro Hawke](https://www.w3.org/People/Sandro) < sandro@w3.org >

## Abstract

Existing data serialization formats like JSON, JSON-LD, XML, and even
ASN.1 (with its various encoding rules) work well enough for
conventional computing environments, but they fall short when high
levels of both trust and decentralization are required. PSDAD
(plaintext self-describing assertional data) is a proposed new
approach which uses natural language strings simultaneously as
identifiers, delimiters, and documentation, resulting in a
surprisingly simple and robust system with distinct advantages over
known approaches in certain environments.  PSDAD has a [partial
spec](https://sandhawke.github.io/psdad/spec.html) and [partial
implementation](https://github.com/sandhawke/psdad.js) available.

## Motivation

Consider the scenario where Alice wants to send Bob a machine-readable
message saying that some thermal probe (probe number 6) is currently
reading 34°C.  With **JSON**, she might encode it like this:

```json
{ 
  "probe": 6, 
  "temp": 34 
}
```

To properly understand this message, Bob needs to know its syntax and
semantics. In particular, in this example, how can he tell whether the
temperature is in Celsius, Fahrenheit, Kelvin, or some
application-specific scale?

This has to be communicated out-of-band, via external means.  Perhaps
Alice and Bob were at a hackathon together while building this system.
Or maybe Alice wrote a blog post about it, which Bob found via search
engine. Or maybe it's part of some formal standard, or this is some
proprietary software talking to another instance of itself.

In any case, for Bob to be confident he is correctly understanding
Alice's message, there has to be some clear external signaling of how
Alice intends each of the data fields in her message to be understood,
in the context of the message.

With **JSON-LD**, Alice might encode her message like this:
```json
{
  "@context": {
    "probe": "https://thermals.example/schema#probe",
    "temp": "https://thermals.example/schema#temp"
  },
  "probe": 6, 
  "temp": 34 
}
```

Now, there is some in-band signaling of the semantics. The URIs act as
global identifier (in a way "probe" and "temp" do not). And now Bob
has the additional option of visiting https://thermals.example/schema
in a browser and perhaps finding some useful information about the
semantics of the data.  That sounds pretty good.

These familiar techniques fall short, however, if there is confusion
about which definitions to use. That confusion might come from an
innocent mistake (such as poor coordination during evolution of the
system), or it might come from a disinformation attack, with someone
deliberately spreading misleading information about the semantics of
Alice's data.

As long as Alice and Bob know each other, are using the same software,
or are using data formats defined by large standards organizations,
the risk is probably small.  The risk becomes significant, however, in
a dynamic market around an open data bus (such as the web), with many
different components and systems passing data around, with
increasingly complexity, and new formats or extensions appearing over
time.

Some people suggest the RDF (and XML) namespace architectures, as
shown above in JSON-LD, solve this problem because one can use the
namespace URL content as the master definition source. In theory this
could work, but in practice it has three serious problems:

1. The W3C RDF specifications and current practice do not actually
give the namespace content any special privileged status. If the
content disagrees with search engine results or word-of-mouth, it's
unclear which should be taken as correct. It is also unclear whether
there is any way to add such special status now, long after the specs
have been published.

2. This makes the namespace host a part of the critical security
infrastructure, since it gets to say what the terms mean. Now, when
Alice and Bob communicate, they must also trust the namespace host
(thermal.example, in the above example). This could make it
significantly harder to build secure data communication channels, and
it increases the cost and liability for running a namespace
host. Arguably, it increases centralization around major namespaces.

3. Not everybody is willing to use RDF, even in the form of JSON-LD.

These concerns are becoming more pressing as the [Credible Web
Community Group](https://credweb.org) moves toward creating a data
ecosystem to help combat online misinformation. There may be others in
the larger community with similar concerns.

## Alternatives

I am not aware of anyone else having done work on this problem. I have
developed another solution which applies only to the RDF space,
[Movable Schemas](https://sandhawke.github.io/mov/), possibly with
[version-integrity](https://github.com/sandhawke/version-integrity). PSDAD
is the extension of Movable Schemas idea to the larger field beyond
RDF.

## Proposal

PSDAD starts with the observation that the semantics of each field in
a data format are in practice defined by a short paragraph in some
specification. In the example above, Alice and Bob might be using a
spec which contains this text:

> ...
>
> **probe**: The "probe" field specifies the integer index of the probe whose temperature is specified in the "temp" field.
>
> **temp**: The "temp" field specifies the temperature measured at the given probe, rounded off to the nearest integer, in degrees Celsius.
>
> ...

We want that spec text to be connected to the bits on the wire, in a
way that is secure, scalable, and maintainable. Operationally, we want
the people writing any software which might be working with the data
in those fields to be looking at the same spec text, with minimal
chance for error or disinformation.

The PSDAD approach is to send that spec text on the wire wrapped
around the data fields.  For example, Alice might transmit:

```text
The temperature at probe number 6 is 34°C.
```

To a human who knows English, this is fairly meaningful.  To the
software at either end, this looks pretty much the same as the JSON
expression given above, `{"probe":6,"temp": 34}`.  It's a few bytes
longer, but it's still "stuff 6 stuff 34 stuff".

The PSDAD trick is to make the delimiters be the documentation by
writing the documentation as template assertions, then filling in the
templates with the field data values.

The template in use here is `The temperature at probe number [] is
[]°C.` Given that template, software at either end can easily
serialize and deserialize probe temperature data.

## Applicability

The primary use case here is to have decentralized extensibility be
robust against disinformation attacks, but this technique also has
potential to address schema and documentation management issues in
conventional deployment environments. In particular, PSDAD allows
developers to publish and/or consume machine-readable data with semantic
clarity and minimal procedural work or need for prior agreement.

If you want to publish some data, just think about how you would
express each item in that data clearly, pedantically, as a statement
in your preferred natural language.  If you want to consume some data,
look at some examples and deduce the template.  If it's not obvious,
there's probably an issue.

Here's another example.  Alice wants to help build a web of trust, so
she publish this text at https://alice.example/endorsements :

```text
I have met and know the person "Susan X. Lastname".
Susan X. Lastname controls and is the sole user of the website https://susan.example.
Susan X. Lastname has the ssh key with public part ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDQnL/9t1t+w8U9bBOn3OeM568BkiejgK37ITAgaRHyGw0+vYCqinMKeswzv0YFar8n9M+Rwi78Evk72RuOlQldcw5cmVfrgwey3U7k/0cJE5ecnO2CEBU4zqfBiKlGnlRsjQ1UcsY2e396ScBGrzm02UYBmtRa09fA+vbSxN4O6nHVDdR1cscbOa3TXhfPpp009LdDzUIt5AgiwXPdBYOBBrvRnzULhGMWiTy8HEXpueRpBOa90Q7yEhL/zZluZQo8tMRUYkk6EwTvJUmz3TjrYKI5DO5p5q1mPR1/wMjVRUEwYG7HET6PgQuJj4aQiIrPQZbVftd+AVOjJyvenkW9 susan@susan.example.

I have met and know the person Tommy Lastname.
Tommy Lastname controls and is the sole user of the website https://tommy.example.
```

These strings can be serialized and/or deserialized easily, given these templates:
* `I have met and know the person [name].`
* `[name] controls and is the sole user of the website [url].`
* `[name] has the ssh key with the public part [ssh_pub].`

## Details

As with any data format, there are many details.  They are being
addressed in the [PSDAD
spec](https://sandhawke.github.io/psdad/spec.html)

A few specific points:

* PSDAD text SHOULD be compressed using the standard compression features of the underlying layer(s). After compression, the size is likely to converge on the same size as JSON serialized data.
* Field value serializations MAY be quoted (JSON-style) and MUST be quoted if the value happens to include a substring matching the ending delimiter of that field in that template.  (We had to quote "Susan X. Lastname" above because the string contained period+whitespace, which was also the ending delimiter.
* Unknown text in input MUST be ignored, to allow for extensibility.
* If there are multiple different templates for the same data (perhaps because of schema evolution), and you don't have a negotiation mechanism to narrow down which ones the other end might be using, you MUST use them all.  Writers must write them all, readers must attempt to recognize them all. This provides backward and forward compatibility.
* The semantics of transmitted data are assertional (like RDF), so duplicate data/statements are ignored
* Writing good template statements is hard, as is writing a good spec. If you err on the long side, it will at least serve to identify and delimit, and then you can iteratively improve the wording as issues arise.

## Conclusion

PSDAD is a new data serialization technique, which appears to have
significant advantages in dynamic, decentralized, trust-sensitive
environments.  Feedback and improvements are [welcome via
github](https://github.com/sandhawke/psdad/issues/).