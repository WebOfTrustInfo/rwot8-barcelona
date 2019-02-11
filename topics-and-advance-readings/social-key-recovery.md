# A New Approach to Social Key Recovery

## by Christopher Allen & Mark Friedenbach

The goal of social key recovery is for the user to specify groups of
individuals that together possess the ability to recover the root
secret of a wallet. A good social key recovery protocol should not
just reflect what cryptographic primitives happen to be available for
use, but rather instead should be designed to correspond with the
structure of trust in the user’s social network while balancing the
technical tradeoffs involved under the hood.

The most popular social key recovery algorithm, Shamir Secret Sharing,
is considered information-theoretically secure. That is, any
combination of shares less than the necessary threshold convey
absolutely no information about the secret. However, all secrets have
equal weight and once a sufficient threshold is achieved the secret
can be reconstructed. In social contexts this can cause a number of
problems in common real-world scenarios. In addition, Shamir Secret
Sharing has a history of being naively implemented including a number
of serious vulnerabilities.

To quote Bitcoin Core Developer Greg Maxwell:

<blockquote>"I think Shamir Secret Sharing (and a number of other
things, RNGs for example), suffer from a property where they are just
complex enough that people are excited to implement them often for
little good reason, and then they are complex enough (or have few
enough reasons to invest significant time) they implement them
poorly.”</blockquote>

Ideally an implementation of social key recovery should balancing
numerous competing goals:

* Key recovery should require approval of many individuals so as to
minimize potential for theft or deliberate key compromise by a small
malicious subset of users.

* Key recovery should require the smallest acceptable threshold so as
to prevent loss of funds from destroyed/lost/inaccessible shares.

* Key recovery requiring interaction with too many individuals is
undesirable, as each interaction must involve re-authentication at
the inconvenience of all involved.

* Social trust is not uniformly distributed among different social
circles, such as friends, business acquaintances, and family.
Individuals may be fungible within a certain circle of trust, but
not more broadly.  A “family member” is not the same as a “business
partner.”

For example, Alice might want a minimum of three people to sign off on
a key recovery attempt, with individuals chosen among her friends,
family, and close business partners.  More than 3 would be
inconvenient and risk loss of funds, while any combination of less
than 3 individuals would not be trustworthy. However some combinations
of 3 individuals drawn from this entire set would not be reliable: she
wouldn’t want her 3 business partners alone having control over her
funds, as they may act maliciously in their shared business interests
and not for her.

One solution for Alice is to require 3 individuals for social key
recovery, but also require that these three individuals include AT
LEAST one friend and one family member.

This can be accomplished by constructing a three-way linear key split
with shares X, Y, and Z. X is given to family members, Y is given to
friends, and Z is further split using 3-of-N Shamir secret sharing,
with unique shares given to each family member, friend, and trusted
business partner. Thus each family member knows X and one share of Z,
each friend knows Y and one share of Z, and business partners only
know their share of Z. As the original key is constructed as X+Y+Z,
all three must be reconstructed, which requires the assistance of at
least one family member, at least one friend, and a total of three
individuals drawn from all three sets.

We suggest calling these separate groups of individuals “circles,” and
we suggest designing a social key recovery system where users are
allowed to specify participation thresholds for the recovery of the
key split associated with each circle (3 “friends” are required, 2
“business partners”, etc.), and then also specify which circle
thresholds are required in disjunctive normal form, e.g. “Friends AND
Family” OR “Family AND Coworkers”. Under the hood this is translated
into a set of linear key splits and Shamir secret shares that are
encrypted and transmitted to each participant.

Longer term on the hardware side, an HSM with secure I/O for user
authentication could be used to perform the social key recovery. A
potential early place to implement this is the HTC Exodus
cryptocurrency phone. When a user attempts key recovery, they present
a fresh set of identity keys to their friend/family/coworker/etc. and
authenticate themselves to the individual. If the individual is
convinced to participate, they authorize their device to reveal their
shares, which is done by decrypting on the HSM and then re-encrypting
to the temporary identity keys of the user’s new or wiped device. When
a user does this with enough shares to reconstruct the original key,
their device automatically does so and retires the temporary identity,
replacing with the recovered master key.

In terms of cryptographic implementation, this requires combining
Shamir secret sharing with linear key splits, and then building a
social key recovery API centered around the recovery protocol rather
than the cryptographic primitives. It will also require some work in
defining serialization formats and web-of-trust public key
infrastructure for encryption and authentication of the key splits
both at the time of distribution and recovery, as well as some
thoughts on best ways to store keyshares offline.

## Milestones

Stage 1 would be a review of newer academic papers on
improvements to Shamir Secret Sharing as well as linear key
splits. 

Stage 2 would be a specific proposal that we can submit to
arXiv and/or academic conferences regarding our specific new proposal.

The remaining stages are code. 

In Stage 3, a preliminary secure implementation of the underlying
cryptography for this proposal such that we can get code review by
various parties.

In Stage 4, we reqiest a formal independent review of the
code by an outside party. 

In Stage 5, we implement a UI version of
this for the iPhone. 

None of these stages would be for secure hardware such as for
TrustZone (HTC) or TinyPython for Ledger, or other secure hardware,
but would include architectural considerations for such in the future.

## References

Shamir, Adi (1979). “How to share a secret”. Communications of the ACM. 22 (11): 612–613. doi:10.1145/359168.359176. [https://cs.jhu.edu/~sdoshi/crypto/papers/shamirturing.pdf](https://cs.jhu.edu/~sdoshi/crypto/papers/shamirturing.pdf)

Beimel A. (2011) Secret-Sharing Schemes: A Survey. In: Chee Y.M. et
al. (eds) Coding and Cryptology. IWCC 2011. Lecture Notes in Computer
Science, vol 6639. Springer, Berlin, Heidelberg
[https://www.cs.bgu.ac.il/~beimel/Papers/Survey.pdf](https://www.cs.bgu.ac.il/~beimel/Papers/Survey.pdf)

Rait, Seth (2016). “Shamir Secret Sharing and Threshold Cryptography”
[https://sethrait.com/Shamir-Secret-Sharing-and-Threshold-Cryptography](https://sethrait.com/Shamir-Secret-Sharing-and-Threshold-Cryptography)

Dautrich J.L., Ravishankar C.V. (2012) “Security Limitations of Using
Secret Sharing for Data Outsourcing. In: Cuppens-Boulahia” N., Cuppens
F., Garcia-Alfaro J. (eds) Data and Applications Security and Privacy
XXVI. DBSec 2012. Lecture Notes in Computer Science, vol
7371. Springer, Berlin, Heidelberg
[http://www.cs.ucr.edu/~ravi/Papers/DBConf/secret_sharing.pdf](http://www.cs.ucr.edu/~ravi/Papers/DBConf/secret_sharing.pdf))

Komargodski I., Naor M., Yogev E. (2016) How to Share a Secret,
Infinitely. In: Hirt M., Smith A. (eds) Theory of Cryptography. TCC
2016. Lecture Notes in Computer Science, vol 9986. Springer, Berlin,
Heidelberg [https://eprint.iacr.org/2016/194.pdf](https://eprint.iacr.org/2016/194.pdf)

Coron JS., Prouff E., Roche T. (2013) On the Use of Shamir’s Secret
Sharing against Side-Channel Analysis. In: Mangard S. (eds) Smart Card
Research and Advanced Applications. CARDIS 2012. Lecture Notes in
Computer Science, vol 7771. Springer, Berlin, Heidelberg
[https://www.ssi.gouv.fr/uploads/IMG/pdf/aesshamir_Coron_Prouff_Roche.pdf](https://www.ssi.gouv.fr/uploads/IMG/pdf/aesshamir_Coron_Prouff_Roche.pdf)

Blakley, G.R. (1979). “Safeguarding Cryptographic Keys”. Managing Requirements Knowledge, International Workshop on (AFIPS). 48: 313–317. doi:10.1109-/AFIPS.1979.98. https://pdfs.semanticscholar.org/32d2/1ccc21a807627fcb21ea829d1acdab23be12.pdf

Feldman, Paul (1987) “A practical scheme for non-interactive
Verifiable Secret Sharing” Proceedings of the 28th Annual Symposium on
Foundations of Computer Science
[https://www.cs.umd.edu/~gasarch/TOPICS/secretsharing/feldmanVSS.pdf](https://www.cs.umd.edu/~gasarch/TOPICS/secretsharing/feldmanVSS.pdf)

Harn, e, Changlu L (2009). “Detection and identification of cheaters
in (t, n) secret sharing scheme” Des. Codes Cryptography 52, 1 (July
2009), 15-24. DOI=10.1007/s10623-008-9265-8
[http://dx.doi.org/10.1007/s10623-008-9265-8](http://dx.doi.org/10.1007/s10623-008-9265-8)

Schoenmakers, Berry (1999) “A Simple Publicly Verifiable Secret
Sharing Scheme and its Application to Electronic Voting” Advances in
Cryptology-CRYPTO’99, volume 1666 of Lecture Notes in Computer
Science, pages 148-164, Berlin,
1999. Springer-Verlag. [https://www.win.tue.nl/~berry/papers/crypto99.pdf](https://www.win.tue.nl/~berry/papers/crypto99.pdf)

Rusnak, P, et. al (2018) “SLIP-0039 : Shamir’s Secret-Sharing for
Mnemonic Codes” Satoshi Labs
Github. [https://github.com/satoshilabs/slips/blob/master/slip-0039.md](https://github.com/satoshilabs/slips/blob/master/slip-0039.md)

Stack Exchange (2016) “Why is Shamir Secret Sharing not secure against
active adversaries out-of-the-box?” Stack Exchange
[https://crypto.stackexchange.com/questions/41994/why-is-shamir-secret-sharing-not-secure-against-active-adversaries-out-of-the-bo](https://crypto.stackexchange.com/questions/41994/why-is-shamir-secret-sharing-not-secure-against-active-adversaries-out-of-the-bo)
