(This is a backup of https://docs.google.com/document/d/1erTs0ybf02JbCznw25DYOEDfhIwP4TL53QAZydrzWmQ/edit#heading=h.kj7jvx553t23 but master will be officially moved here closer to final draft).

## Shamir Secret Sharing Best Practices

## Abstract

A number of companies and open source projects in the cryptocurrency and decentralized identity field make use of long-lived master secrets, stored in digital wallets, the loss of which can mean large losses of money or irrevocable lost of digital identity. Issues with management the master secrets, and the private keys deterministically generated from them, often pose barriers to the adoption of new decentralised technologies.

One of the most common practices is the use of Shamir Secret Sharing (SSS), a cryptographic technique of splitting key is considered information-theoretically secure. That is, any combination of shares less than the necessary threshold convey absolutely no information about the secret. Unfortunately, Shamir Secret Sharing has a history of being naively implemented which has in the past resulted in  a number of serious vulnerabilities.

To quote Bitcoin Core Developer Greg Maxwell:

```
_ "I think Shamir Secret Sharing (and a number of other things, RNGs for example), suffer from a property where they are just complex enough that people are excited to implement them often for little good reason, and then they are complex enough (or have few enough reasons to invest significant time) they implement them poorly."_
```

This document, and accompanying source code library and example code, are intended as a guide to best practices for implementing Shamir Secret Sharing for cryptographic secrets (as opposed to low-entropy secrets such as passwords).

### Why it is Hard!

(talk about why you should not do crypto, why humility is required, but if you really are going to do so, you better know about X, X, X)

### Choice of Finite Field

We currently recommend It is recommended that GF(256) be used as the underlying finite field for the coefficients of the polynomial used in Shamir's secret sharing scheme and that the scheme be applied separately to each byte of the shared secret. The advantage of using GF(256) is that the field arithmetic is easy to implement in any programming language and many implementations are already available since this field is used in the AES cipher. The fact that it is byte oriented makes it easy to work with.

The disadvantage of using a field of prime order GF(_p_), where log<sub>2</sub> _p_ is approximately the length of the secret in bits, is that it requires support for multi-precision arithmetic. Many programming languages, such as C/C++, do not support multi-precision arithmetic out of the box. Implementations would also need to store information about the prime number that should be used for each admissible length of the secret or they would need to generate the prime number deterministically on the fly.

The disadvantage of using GF(2<sup><em>m</em></sup>), where _m_ is the length of the secret in bits, is that it requires a more complicated implementation than GF(256). This is in part due to the multi-precision nature of the arithmetic and in part due to the fact that implementations would need to store an (e.g. lexicographically minimal) irreducible polynomial of degree _m_ for each admissible value of _m_ or they would need to be able to determine this polynomial on the fly.

We note that for sharing of cryptographic secrets, it is potentially valuable to use a prime field GF(p) where p is the group order of a secure elliptic curve. The curves secp256k1 and the prime-order Ristretto curve of curve25519-dalek are of particular interest due to the availability of Bulletproofs-based zero-knowledge proof systems which can be used to create an efficient verifiable Shamir secret sharing system. More research is required however to demonstrate this capability.

TODO:

Advantages of using the finite field from secp256k1 of order _p_ = 2<sup>256</sup> − 2<sup>32</sup> − 2<sup>9</sup> − 2<sup>8</sup> − 2<sup>7</sup> − 2<sup>6</sup> − 2<sup>4</sup> − 1.

Using bulletproofs:



- Describe use cases.
- Describe attack models.

### Multi-level Shamir secret sharing

Ideally an implementation of social key recovery should balancing numerous competing goals:



- Key recovery should require approval of many individuals so as to minimize potential for theft or deliberate key compromise by a small malicious subset of users.
- Key recovery should require the smallest acceptable threshold so as to prevent loss of funds from destroyed/lost/inaccessible shares.
- Key recovery requiring interaction with too many individuals is undesirable, as each interaction must involve re-authentication at the inconvenience of all involved.
- Social trust is not uniformly distributed among different social circles, such as friends, business acquaintances, and family. Individuals may be fungible within a certain circle of trust, but not more broadly. A "family member" is not the same as a "business partner."

For example, Alice might want a minimum of three people to sign off on a key recovery attempt, with individuals chosen among her friends, family, and close business partners. More than 3 would be inconvenient and risk loss of funds, while any combination of less than 3 individuals would not be trustworthy. However some combinations of 3 individuals drawn from this entire set would not be reliable: she wouldn't want her 3 business partners alone having control over her funds, as they may act maliciously in their shared business interests and not for her.

One solution for Alice is to require 3 individuals for social key recovery, but also require that these three individuals include _at least_ one friend and one family member.

This can be accomplished by constructing a three-way linear key split, or a 3-of-3 secret share to generate shares X, Y, and Z. X is given to family members, Y is given to friends, and Z is further split using 3-of-N Shamir secret sharing, with unique shares given to each family member, friend, and trusted business partner. Thus each family member knows X and one share of Z, each friend knows Y and one share of Z, and business partners only know their share of Z. As the original key is constructed as X+Y+Z, all three must be reconstructed, which requires the assistance of at least one family member, at least one friend, and a total of three individuals drawn from all three sets.

We suggest calling these separate groups of individuals "circles," and we suggest designing a social key recovery system where users are allowed to specify participation thresholds for the recovery of the key split associated with each circle (3 "friends" are required, 2 "business partners", etc.), and then also specify which circle thresholds are required in disjunctive normal form, e.g. "Friends AND Family" OR "Family AND Coworkers". internally this is translated into a set of linear key splits and/or Shamir secret shares that are encrypted and transmitted to each participant.

TODO:



- Advantages and disadvantages of using more than one level?
- Are two levels (aka "circles scheme") sufficient?
- Advantages and disadvantages of using Shamir secret sharing only at level two and plain addition of shares (_n_-of-_n_ scheme) at level one as opposed to using Shamir secret sharing at both levels.
- In judging the advantages and disadvantages consider the consequences for:
  - The format of the shares.
  - The user interface.
  - The complexity of the implementation.

### How to avoid a corrupted or malicious share on restoration

Sign shares with original key? Who is bad/malicious?

### X doesn't need to be private?

### Deterministic Nonce?

Bad random source, security breaks, but 

Ideally 2 sources

Uniform random secrets are easier to share, but be careful of low-entropy secrets (say bip38)

### Session secret

## Unsolved problems or Alternatives to Shamir

### All shares are equal

An interesting limitation of threshold schemes, like Shamir's scheme is the fact that "all shares are equal". That is, every share contains to a _t_'th of the information to reconstruct the secret. It is currently undecided whether there is an option for allowing scenarios like



- One share has 75% of reconstruction power; and
- Ten shares each have 5% of reconstruction power.

I.e. you would always need the "large" share, and at least 5 of the "small" shares.

The only method to implement these kinds of scenarios is by giving a shareholder multiple shares. For example, in the scenario described in the previous paragraph, we would generate 25 different shares, with a recombination threshold of 20. However, in this scenario one shareholder has to keep 15 different shares, which may be quite a lot of data; so much that it may be impractical to write them down.

### When should you be using multisig instead?

### You shouldn't use Shamir if you need to Verify shares

If you feel you need to verify your received share, you probably have a _multi-sig_ use case.

## Appendixes

### #1 Implementing on Constrained or Trusted Execution Environments

A commercial example with trusted execution environment (TEE) has been integrated on HTC EXODUS phone.

TEE is as an isolated execution environment inside a processor. Code, data, and UI in TEE is guaranteed confidentiality and integrity. HTC Exodus phone, keep your own key in the TEE. It breaks, encrypts and shares your recovery phrase to your trusted contacts, they can help you recover your key when your phone is lost.



- - User scenario:
    - Cryptocurrency wallet user on Exodus phone, can backup/restore seeds by highest security level. 
  - Support Social Key Recovery(SKR) to your private seeds.
  - Shamir Secret Sharing algorithm was implemented in TEE HW enclave(ZION) to support SKR with best security consideration.
  - Open source code plan:
    - Target 2nd quarter 2019.
  - ZION TEE HW enclave:

<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/RWOT8-Social0.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/RWOT8-Social0.png "image_tooltip")

```
*   Social Key Recovery:
```

​        

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/RWOT8-Social1.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/RWOT8-Social1.png "image_tooltip")



## References

Shamir, Adi (1979). "How to share a secret". Communications of the ACM. 22 (11): 612–613. doi:10.1145/359168.359176. https://cs.jhu.edu/~sdoshi/crypto/papers/shamirturing.pdf

Beimel A. (2011) Secret-Sharing Schemes: A Survey. In: Chee Y.M. et al. (eds) Coding and Cryptology. IWCC 2011. Lecture Notes in Computer Science, vol 6639. Springer, Berlin, Heidelberg https://www.cs.bgu.ac.il/~beimel/Papers/Survey.pdf

Rait, Seth (2016). "Shamir Secret Sharing and Threshold Cryptography" https://sethrait.com/Shamir-Secret-Sharing-and-Threshold-Cryptography

Dautrich J.L., Ravishankar C.V. (2012) "Security Limitations of Using Secret Sharing for Data Outsourcing. In: Cuppens-Boulahia" N., Cuppens F., Garcia-Alfaro J. (eds) Data and Applications Security and Privacy XXVI. DBSec 2012. Lecture Notes in Computer Science, vol 7371. Springer, Berlin, Heidelberg http://www.cs.ucr.edu/~ravi/Papers/DBConf/secret_sharing.pdf)

Komargodski I., Naor M., Yogev E. (2016) How to Share a Secret, Infinitely. In: Hirt M., Smith A. (eds) Theory of Cryptography. TCC 2016. Lecture Notes in Computer Science, vol 9986. Springer, Berlin, Heidelberg https://eprint.iacr.org/2016/194.pdf

Coron JS., Prouff E., Roche T. (2013) On the Use of Shamir's Secret Sharing against Side-Channel Analysis. In: Mangard S. (eds) Smart Card Research and Advanced Applications. CARDIS 2012. Lecture Notes in Computer Science, vol 7771. Springer, Berlin, Heidelberg https://www.ssi.gouv.fr/uploads/IMG/pdf/aesshamir_Coron_Prouff_Roche.pdf

Blakley, G.R. (1979). "Safeguarding Cryptographic Keys". Managing Requirements Knowledge, International Workshop on (AFIPS). 48: 313–317. doi:10.1109-/AFIPS.1979.98. https://pdfs.semanticscholar.org/32d2/1ccc21a807627fcb21ea829d1acdab23be12.pdf

Feldman, Paul (1987) "A practical scheme for non-interactive Verifiable Secret Sharing" Proceedings of the 28th Annual Symposium on Foundations of Computer Science https://www.cs.umd.edu/~gasarch/TOPICS/secretsharing/feldmanVSS.pdf

Harn, e, Changlu L (2009). "Detection and identification of cheaters in (t, n) secret sharing scheme" Des. Codes Cryptography 52, 1 (July 2009), 15-24. DOI=10.1007/s10623-008-9265-8 http://dx.doi.org/10.1007/s10623-008-9265-8

Schoenmakers, Berry (1999) "A Simple Publicly Verifiable Secret Sharing Scheme and its Application to Electronic Voting" Advances in Cryptology-CRYPTO'99, volume 1666 of Lecture Notes in Computer Science, pages 148-164, Berlin, 1999. Springer-Verlag. https://www.win.tue.nl/~berry/papers/crypto99.pdf

Rusnak, P, et. al (2018) "SLIP-0039 : Shamir's Secret-Sharing for Mnemonic Codes" Satoshi Labs Github. https://github.com/satoshilabs/slips/blob/master/slip-0039.md

Stack Exchange (2016) "Why is Shamir Secret Sharing not secure against active adversaries out-of-the-box?" Stack Exchange https://crypto.stackexchange.com/questions/41994/why-is-shamir-secret-sharing-not-secure-against-active-adversaries-out-of-the-bo

------

Beimel, Amos (2011). "Secret-Sharing Schemes: A Survey" [http://www.cs.bgu.ac.il/~beimel/Papers/Survey.pdf](http://www.cs.bgu.ac.il/~beimel/Papers/Survey.pdf)

Blakley, G.R. (1979). "Safeguarding Cryptographic Keys". Managing Requirements Knowledge, International Workshop on (AFIPS). 48: 313–317. doi:10.1109-/AFIPS.1979.98.

Feldman, Paul (1987) "A practical scheme for non-interactive Verifiable Secret Sharing" Proceedings of the 28th Annual Symposium on Foundations of Computer Science

Harn, L. & Lin, C. Detection and identification of cheaters in (t, n) secret sharing scheme, Des. Codes Cryptogr. (2009) 52: 15. [https://link.springer.com/article/10.1007/s10623-008-9265-8](https://link.springer.com/article/10.1007/s10623-008-9265-8)

Schneier, Bruce (2010) - DNSSEC Root Key held by 7 parties worldwide [https://www.schneier.com/blog/archives/2010/07/dnssec_root_key.html](https://www.schneier.com/blog/archives/2010/07/dnssec_root_key.html)

Schoenmakers, Berry (1999) "A Simple Publicly Verifiable Secret Sharing Scheme and its Application to Electronic Voting" Advances in Cryptology-CRYPTO'99, volume 1666 of Lecture Notes in Computer Science, pages 148-164, Berlin, 1999. Springer-Verlag.

Zenroom, a virtual machine for fast cryptographic operations on elliptic curves, [https://zenroom.dyne.org/](https://zenroom.dyne.org/)

HTC EXODUS SKR, a smartphone device with build-in Shamir Secret Sharing into Trusted Execution Environment. Which support the web 3.0 to turn that around by empowering users to own their own data. The EXODUS 1 is the first native web 3.0 mobile device. This same architecture also secures your crypto assets. [https://www.htcexodus.com/eu/zion/](https://www.htcexodus.com/eu/zion/)

https://tools.ietf.org/html/draft-mcgrew-tss-03

