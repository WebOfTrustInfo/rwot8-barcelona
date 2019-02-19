# Exploring adoptation of VC sharing to provide value today

### by Snorre Lothar von Gohren Edwin snorre@diwala.io

For the community to get faster adoptation of the standards we are working on now, it is important to explore the the possibilities that can work out of the box, which is also safe enough to be trustworthy and not leak any sensitive data.

With Verifiable Credentials it is important to ask the question what are we expecting the issuer, the holder, and / or the verifier to do? While still making it simple enough for all the users and keeping the needed level of trustworthiness.

Sharing is what provides the end value for both the verifying and the sharing party. If there is no sharing, the issuance of the VC has gone to waste. Hence if we are to provide value for the sharing party today, we have to ask the questions of where is this adopted, how can we make this adoption effortless? Can we put most of the work on the service providers? Is the user or another service expected to install software? If so, install software where? Is that software domain-specific or integrated with some existing software?

We have to explore methods of trustworthy sharing with all these aspects in mind and can we do it without too much intrusion on the verifier side? If so we can be able to showcase the value of VC's in a real live scalable example, very quickly.

# Situation
Diwala experienced during their users tests and pilots in East Africa, that sharing  approach taken by the community is not always feasible in these situations.

 * Many of the current sharing suggestions are based on that software has to be installed at every point of the process, from verifier, issuer and user. 
 * That the process is more pull based rather than push based. In this case it is expected of the verifier to have some sort of software installed to be able to pull the information from the sharing party, and not that the initial interaction can start from the sharing party, in one way or another.

During the user tests it was early agreed upon that the issuing party needed some kind of software, because they lacked any type of digital and efficient solution to be able to issue verifications to their students. They instantly saw the value a simple software could provide in the long run, and the value gained regarding efficiency and trustworthiness.

During tests for the receiving party it was early clarified that an identity application/wallet, such as uPort or Jolocom, could not provide enough services and information around once skill verifications and other metadata issued to the reciever. So it was concluded that the receiving party needed an app to be able better to understand and make sense of the data/VCs issued. It was also concluded that the current sharing solution in the identity application/wallet that was tested, was not sufficient enough to give instant value. The extra app had to take care of the sharing based on the data that was available from the identity application/wallet. Yet another software installation.

For the last party, the verifying party, it was early concluded that they could not be dependent on having a software if this was going to scale in any way. There was no clear technological path to solve this, then rather work on how this verification of a shared VC could be done without any special software installed, just dependent on web technologies.

In East Africa, Uganda to be specific, we found that even installing a couple of apps on a phone was problematic without enough incentivisation, or insight to what value this would provide the user. That was mainly because of the lack of space on the phone. Making the installation of software not very straightforward, on user facing phones. 

We also saw that the systems used, are not always as integrated as the western culture is used to, meaning it is quite difficult to figure out where in the pipeline a possible software installation would happen to generate the most value.

# A solution in experimentation

What Diwala tries to do is to provide value for the sharing of VCs, as the current technological situation is right now. Trying to figure out how to test out the value of VCs with the least possible friction. Diwala have taken the approach, how to do sharing through simple URLs and JWTs. To be able to build trustworthiness in the simplest form of sharing. This part still need a lot of work, but that is why I am raising the question for the community, to work together to build something that is as frictionless as possible, to be able to generate value here and now.

## How it works
Diwala works with uPort as an implementation for the identity solution, signing and initial issuance to the receivers of the VCs. Diwala builds a low weight certification solution for schools and course holders, that tries to remove the friction of decentralized identity onboarding, help creating VCs for skills and providing a view for the received VCs. This is done with a simple online web administration user interface for the issuing organization. 

The receiver has two apps, the uPort app for their identity, and the Diwala app for their view and sharing possibilities of the received VCs. Which we call their skill-identity. As mentioned earlier, uPort did not provide enough contextual services for these skill VCs, therefore this second app was created. 

The app allows for sharing through a simple URL, with the standard functionality for sharing on a phone. The VC, which is a JWT, coming from the uPort app/”your wallet” is appended to the URL that is being shared. This URL points to a service currently hosted by Diwala, which starts a verification process of the provided VC or VCs. This service verifies the signatures through a did resolver, loads any data that might be provided through the service URLs of the DIDs, and tries to showcase this to the verifier in a way that is trustworthy. This is all done without any communication to the Diwala database, which means this can be converted to a standalone SDK(Software development kit) provided to other services.

## Questions concering this solution
* How do can you confirm the VC is coming from the person that sent it?
* How can the verifier trust the validity of the data and that the signatures are acctually verified decentralized?

# Discussion

There are things to discuss and there might not be that the mentioned solution is viable at all. But it is something Diwala saw as a possibility and are currently testing out the value gain of this approach.

But in the end, the discussion is about adoption, how can we introduce this as frictionless as possible, and still keep the core values intact.

#### There are a few problem areas to tackle when sharing
* Replay attacks 

This can be mitigated with for example uPort’s challenge/response protocol, but then software is needed on all sides. If that protocol is not used, then you would need a an out-of-band method, e.g., ID card, that associates the VC with the individual
* Trust that it is coming from the person that shared it.

This is also mitigated with the same protocol mentioned above, but with bigger intrusion than neede. But again all this comes down to that the signatures are coming from the person who say they are sharing. And that  the sharing party owns the keys signed, are they on the users device?
* How much software needs to be installed?
* Who owns and shares the software?

