# DID Data Object References
2019-02-29

Drummond Reed and Ken Ebert

## Motivation

A "naked DID" by itself identifies a DID subject. A naked DID is also is by itself a valid URL (Uniform Resource Locator), which is one type of URI (Uniform Resource Identifier) as defined by [RFC 3986](https://www.ietf.org/rfc/rfc3986.txt). 

By adding additional syntax elements as allowed under RFC 3986, a DID URL can also address other resources besides a DID subject. For example, by adding a service ID using semicolon syntax, a DID URL can dereference to a service endpoint and pass on to it the path, query, and/or fragment component of a DID URL. In this way services represent the ability for a DID URL to address a "predicate"—the predicate being a service.

To complete the ability of a DID URL to address all three basic types of semantic objects (subjects, predicates, and objects), we also need the ability for DID URLs to serve as persistent, cryptographically verifiable identifiers for **data objects** of two types:
1. **Immutable Data Objects (IDOs)**—data objects whose state MUST NOT change. Examples include schema definitions, credential definitions, and state anchors.
1. **Mutable Data Objects (MDOs)**—data objects whose state MAY change over time. Examples include payment addresses, revocation registries, and other forms of control objects that need fixed addresses but can have mutable state. A DID document is also an MDO, however it the default MDO returned by a naked DID.

## Base ABNF Syntax

Following is the base ABNF syntax for DIDs and DID URLs that we will use as the starting point for this proposal. We note that this syntax is currently under discussion by the [W3C Credentials Community Group](https://www.w3.org/community/credentials/), so it may change, particularly during the upcoming discussions at Rebooting the Web of Trust #8. For the definitive DID and DID URL ABNF once it is solidified, see the DID spec at https://w3c-ccg.github.io/did-spec/. Any rules not defined in this ABNF are defined in RFC 3986. For easy reference, a copy of that ABNF is included in the last section of this document.

```
did                = "did:" method ":" method-specific-idstring
method             = 1*methodchar
methodchar         = %x61-7A / DIGIT
method-specific-idstring  = idstring *( ":" idstring )
idstring           = 1*idchar
idchar             = ALPHA / DIGIT / "." / "-"
did-url            = did [ did-relative-ref ]
did-relative-ref   = did-fragment-ref / did-service-ref
did-fragment-ref   = "#" fragment
did-service-ref    = *( ";" service-id ) [ path-abempty ] [ "?"    
                     query ] [ "#" fragment ]
service-id         = 1*( ALPHA / DIGIT / "." / "-" / "_" / 
                     pct-encoded )
did-reference      = did-url / did-relative-ref
```
## Proposed ABNF Syntax With Support for Data Object References

To add support for both types of data object references, we only need to add syntax that is parallel to the semicolon syntax used for service references. The limited character set available for this syntax in a valid URI is defined the `sub-delims` rule from the URI syntax defined in [RFC 3986](https://www.ietf.org/rfc/rfc3986.txt). In this ABNF we chose `!` for IDOs and `$` doe MDOs.

```
did                = "did:" method ":" method-specific-idstring
method             = 1*methodchar
methodchar         = %x61-7A / DIGIT
method-specific-idstring  = idstring *( ":" idstring )
idstring           = 1*idchar
idchar             = ALPHA / DIGIT / "." / "-"
did-url            = did [ did-relative-ref ]
did-relative-ref   = did-fragment-ref / did-service-ref /
                     did-ido-ref / did-mdo-ref                    ; These two rules added
did-fragment-ref   = "#" fragment
did-ido-ref        = 1*( "!" type-id )                            ; Syntax for immutable data object references
did-mdo-ref        = 1*( "$" type-id )                            ; Syntax for mutable data object references
type-id            = 1*( ALPHA / DIGIT / "." / "-" / "_" /        ; Syntax for type-ids
                     pct-encoded )
did-service-ref    = *( ";" service-id ) [ path-abempty ] 
                     [ "?" query ] [ "#" fragment ]
service-id         = 1*( ALPHA / DIGIT / "." / "-" / "_" / 
                     pct-encoded )
did-reference      = did-url / did-relative-ref
```

## Resolution of DID Data Object References

The intention of this extension to the DID specification is to enable DID target systems (also called DID registries), such as distributed ledgers or decentralized file systems, to be able to store IDOs and MDOs natively if they are able. In this case, a DID method specification can be extended to define how a DID resolver can resolve a DID Object Reference directly to the IDO or MDO and thus return that as a result of resolution exactly like it would return a DID document as a result of naked DID resolution.

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
