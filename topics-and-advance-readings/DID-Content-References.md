# DID Content References
2019-03-02

Drummond Reed and Ken Ebert

## Motivation

A "naked DID" by itself identifies a DID subject. A naked DID is also is by itself a valid URL (Uniform Resource Locator), which is one type of URI (Uniform Resource Identifier) as defined by [RFC 3986](https://www.ietf.org/rfc/rfc3986.txt). As a URL, a naked DID resolves to a DID document that describes the DID subject. We can therefore call a naked DID a **DID document reference**.

By adding additional syntax elements as allowed under RFC 3986, a DID URL can also address other resources besides a DID document. For example:

1. By adding a fragment directly to a naked DID, a DID URL can address a specific component within a DID document (such as a specific public key). We will call this a **DID fragment reference**.
1. By adding a service ID directly after a naked DID, a DID URL can be dereferenced to a service endpoint and then pass on to it the optional path, query, and/or fragment components of a DID URL. In this way, a **DID service reference** can serve as a way to persistently address any service endpoint on the Web and to pass to that service endpoint the same components that a conventional URL can pass.

More recently a fourth general category of use cases for DIDs has arisen—the use of a DID to provide a persistent, decentralized references to **content** that is not hosted at a separate service endpoint but is stored at the verifiable data registry itself. A specific example of this use case is the [Sovrin community](https://sovrin.org/), which stores various persistent content types needed by Sovrin-based credentials on the Sovrin ledger, including schema definitions, credential definitions, and revocation registries.

While such persistent content references could be made using a Sovrin-specific content addressing syntax, it would be strongly preferable for these references to use a ledger-neutral DID syntax so they can be shared and reused across other ledgers or anywhere else that DID syntax is supported.

We will refer to this fourth category of DID-based references as **DID content references**. The balance of this document will propose DID ABNF syntax that supports all four types of DID references.

## Base ABNF Syntax

Following is a base ABNF syntax for DIDs and DID URLs that we propose to use as the starting point for this proposal. We note that this syntax is currently under discussion by the [W3C Credentials Community Group](https://www.w3.org/community/credentials/), so it may change, particularly during the upcoming discussions at Rebooting the Web of Trust #8. For the definitive DID and DID URL ABNF once it is solidified, see the DID spec at https://w3c-ccg.github.io/did-spec/. Any rules not defined in this ABNF are defined in RFC 3986 (for easy reference, a copy of that ABNF is included in the last section of this document).

**Note: this proposal changes the delimiter character for service references from a semicolon to a dollar sign.** While both semicolon and dollar sign are `sub-delims` characters under RFC 3986 and thus valid delimiters, the dollar sign character is: a) more visually distinguishable, and b) more suggestive of "service".

```
did                       = "did:" method ":" method-specific-idstring
method                    = 1*methodchar
methodchar                = %x61-7A / DIGIT
method-specific-idstring  = idstring *( ":" idstring )
idstring                  = 1*idchar
idchar                    = ALPHA / DIGIT / "." / "-"
did-url                   = did [ did-relative-ref ]
did-relative-ref          = did-fragment-ref / did-service-ref
did-fragment-ref          = "#" fragment
did-service-ref           = "$" service-id [ path-abempty ] [ "?" query ] [ "#" fragment ]
service-id                = service-idstring *( ":" service-idstring )
service-id                = 1*uri-safe-char
url-safe-char             = idchar / "_" / pct-encoded
did-reference             = did-url / did-relative-ref
```
## Proposed ABNF Syntax With Support for DID Content References

To add support for both types of content references, we only need to add syntax that is parallel to the delimiter syntax used for service references, but which allows for content references in various content referencing formats. The limited character set available for this syntax in a valid URI is defined the `sub-delims` rule from the URI syntax defined in [RFC 3986](https://www.ietf.org/rfc/rfc3986.txt). In this ABNF we propose the `!` as the delimiter for content references.

```
did                       = "did:" method ":" method-specific-idstring
method                    = 1*methodchar
methodchar                = %x61-7A / DIGIT
method-specific-idstring  = idstring *( ":" idstring )
idstring                  = 1*idchar
idchar                    = ALPHA / DIGIT / "." / "-"
did-url                   = did [ did-relative-ref ]
did-relative-ref          = did-fragment-ref / did-content-ref / did-service-ref             ;added did-content-ref
did-fragment-ref          = "#" fragment
did-content-ref           = "!" content-id                                                   ;new
content-id                = content-idstring *( ":" content-idstring )                       ;new
content-idstring          = 1*uri-safe-char                                                  ;new
url-safe-char             = idchar / "_" / pct-encoded
did-service-ref           = "$" service-id [ path-abempty ] [ "?" query ] [ "#" fragment ]
service-id                = service-idstring *( ":" service-idstring )
service-idstring          = 1*uri-safe-char
did-reference             = did-url / did-relative-ref
```

## Content Reference Formats

This syntax for content references can support emerging content addressing formats such as [Hashlink](https://tools.ietf.org/html/draft-sporny-hashlink-00). Following is an example of a DID URL containing a Hashlink as a content reference to a (fictitious) schema on the Sovrin ledger:
```
     did:sov:21tDAKCERh95uGgKbJNHYp!hl:zQmWvQxTqbG2Z9HPJgG57jjwR154cKhbtJenbyYTWkjgF3e
```

## Resolution of DID Content References

The intention of this extension to the DID specification is to enable verifiable data registries, such as distributed ledgers or decentralized file systems, to be able to store persistent content natively if they are able. In this case, a DID method specification can be extended to define how a DID resolver can resolve a DID content reference directly to the content object and thus return that as a result of resolution exactly like it would return a DID document as a result of naked DID resolution.

## RFC 3986 Appendix A (For Reference)

Any rules that are not defined in the ABNF above are defined in the ABNF for [RFC 3986](https://www.ietf.org/rfc/rfc3986.txt). That ABNF is included here for easy reference. Note that we have annotated the syntax path through this ABNF used by the DID and DID URL ABNF.

```
   URI           = scheme ":" hier-part [ "?" query ] [ "#" fragment ]

   hier-part     = "//" authority path-abempty
                 / path-absolute
                 / path-rootless                                 ; DID URLs use this rule
                 / path-empty

   URI-reference = URI / relative-ref

   absolute-URI  = scheme ":" hier-part [ "?" query ]

   relative-ref  = relative-part [ "?" query ] [ "#" fragment ]

   relative-part = "//" authority path-abempty
                 / path-absolute
                 / path-noscheme
                 / path-empty

   scheme        = ALPHA *( ALPHA / DIGIT / "+" / "-" / "." )

   authority     = [ userinfo "@" ] host [ ":" port ]
   userinfo      = *( unreserved / pct-encoded / sub-delims / ":" )
   host          = IP-literal / IPv4address / reg-name
   port          = *DIGIT

   IP-literal    = "[" ( IPv6address / IPvFuture  ) "]"

   IPvFuture     = "v" 1*HEXDIG "." 1*( unreserved / sub-delims / ":" )

   IPv6address   =                            6( h16 ":" ) ls32
                 /                       "::" 5( h16 ":" ) ls32
                 / [               h16 ] "::" 4( h16 ":" ) ls32
                 / [ *1( h16 ":" ) h16 ] "::" 3( h16 ":" ) ls32
                 / [ *2( h16 ":" ) h16 ] "::" 2( h16 ":" ) ls32
                 / [ *3( h16 ":" ) h16 ] "::"    h16 ":"   ls32
                 / [ *4( h16 ":" ) h16 ] "::"              ls32
                 / [ *5( h16 ":" ) h16 ] "::"              h16
                 / [ *6( h16 ":" ) h16 ] "::"

   h16           = 1*4HEXDIG
   ls32          = ( h16 ":" h16 ) / IPv4address
   IPv4address   = dec-octet "." dec-octet "." dec-octet "." dec-octet
   dec-octet     = DIGIT                 ; 0-9
                 / %x31-39 DIGIT         ; 10-99
                 / "1" 2DIGIT            ; 100-199
                 / "2" %x30-34 DIGIT     ; 200-249
                 / "25" %x30-35          ; 250-255

   reg-name      = *( unreserved / pct-encoded / sub-delims )

   path          = path-abempty    ; begins with "/" or is empty
                 / path-absolute   ; begins with "/" but not "//"
                 / path-noscheme   ; begins with a non-colon segment
                 / path-rootless   ; begins with a segment
                 / path-empty      ; zero characters

   path-abempty  = *( "/" segment )
   path-absolute = "/" [ segment-nz *( "/" segment ) ]
   path-noscheme = segment-nz-nc *( "/" segment )
   path-rootless = segment-nz *( "/" segment )                        ; DID URLs use this rule
   path-empty    = 0<pchar>

   segment       = *pchar
   segment-nz    = 1*pchar                                            ; DID URLs use this rule
   segment-nz-nc = 1*( unreserved / pct-encoded / sub-delims / "@" )
                 ; non-zero-length segment without any colon ":"

   pchar         = unreserved / pct-encoded / sub-delims / ":" / "@"  ; DID URLs use this rule

   query         = *( pchar / "/" / "?" )

   fragment      = *( pchar / "/" / "?" )

   pct-encoded   = "%" HEXDIG HEXDIG

   unreserved    = ALPHA / DIGIT / "-" / "." / "_" / "~"
   reserved      = gen-delims / sub-delims
   gen-delims    = ":" / "/" / "?" / "#" / "[" / "]" / "@"
   sub-delims    = "!" / "$" / "&" / "'" / "(" / ")"                 ; DID URLs use this rule
                 / "*" / "+" / "," / ";" / "="
```
