# Proof of Key Ownership with OpenID Connect Self-Issued Identities

Proving ownership of a DID requires proving ownership of a private key corresponding to a public key for the DID.  Of course, this could be done with a new DID-specific protocol.  However, there already exist standard protocols for proving ownership of a public/private key pair.

The [OpenID Connect](https://openid.net/specs/openid-connect-core-1_0.html) specification defines [Self-Issued Identities](https://openid.net/specs/openid-connect-core-1_0.html#SelfIssued) in Section 7.  A self-issued identity is represented by a public/private key pair.  Logging in with the self-issued identity proves control of the private key.

Microsoft is experimenting with using self-issued identities to prove ownership of DIDs.  This is straightforward.  The DID key is used as the key for the self-issued identity.  The self-issued identity is validated in the standard way.  In addition, a "did" claim containing the DID identifier is added to the self-issued ID Token.  This enables relying parties that understand that the self-issued identity is also a DID to perform DID operations after control of the key has been verified using OpenID Connect.

I look forward to discussing this potential DID validation approach with the workshop participants.

**Author:** Michael B. Jones [https://self-issued.info/](https://self-issued.info/), [@selfissued](https://twitter.com/selfissued)
