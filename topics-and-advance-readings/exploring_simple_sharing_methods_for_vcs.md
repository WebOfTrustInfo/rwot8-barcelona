# Exploring adoptation of VC sharing to provide value today

### by Snorre Lothar von Gohren Edwin snorre@diwala.io

For the community to get faster adoptation of the standards we are working on now it is important to explore the the possibilities that can work out of the box, which is also safe enough to be trustworthy and not loose any sensitive data. 

With Verifiable Credentials it is important to ask the questiont what are we expecting the issuer, the holder, and / or the verifier to do? While still making it easily enough for all the users and keeping trustworthiness.

Sharing is what provides the end value for both the verifying and the sharing party. Hence if we are to provide value for the sharing party today, we have to ask the questions of where is this adopted, how can we make this adoption effortless by putting the work on the service providers? Is the user or another service expected to install software? If so install software where? Is that software domain-specific or integrated with some existing software?

We have to explore methods of trustworthy sharing with all these aspects in mind, can we do it without too much intrusion in the verifier side? If so we can be able to showcase the value of VC's in a real live example, very quickly.

# Situation
Diwala experienced with their users tests and pilots in East Africa that the same approach beeing taken by the community is not always feasible in these situations.

Many of the current sharing suggestions I feel are based on software having to be installed at every point of the process, from verifier, issuer and user.

In East Africa, Uganda to be specific, we found that even installing a couple of apps on your phone was problematic without enough insentivisation, or insight to what value this would provide the user. That was mainly because of the lack of space on once phone. We also have seen that the systems beeing worked with are not always as integrated as the western culture is used to, meaning it is quite difficult to figure out where this software installation would be put to generate the most value.

# A solution in experimentation

What Diwala tries to do is to provide value for sharing, as the current situation is right now. Trying to figure out how to test out the value of VCs with the least possible friction. Diwala have taken the approach to look at how to do sharing through simple URLs and JWTs. To be able to build a trustworthiness in the simplest form of sharing. This part still need a lot of work, but that is why I am raising the question for the community, to work together to build something that is as frictionless as possible, to be able to generate value here and now.

## How it works
Right now Diwala works with uPort as an implementation for the identity solution and issuance of the VCs. Diwala builds a certification solution for schools and course holders, that tries to remove the friction of decentralized identity onboarding, and creating value around skill VCs. This is done with a simple administration user interface for the issuing organization. The reciever has two apps, the uPort app for their identity, and the Diwala app for their skill-identity. This app provides more services on top of the current identity and skill VCs. Through the Diwala app, it allows for sharing throug a simple URL, where the VC, a JWT, is appended to the URL to enable sharing of the data. A SDK is then loaded on the URL landing page, to read out the data and verify the signatures decentralized.

## Questions concering this solution
* How do can you confirm the VC is coming from the person that sent it?
* How can the verifier trust the validity of the data and that the signatures are acctually verified decentralized?

# Discussion

There are things to discuss and there might not be that the mentioned solution is viable at all. But it is something Diwala saw as a possibility and are currently testing out the value of this approach.

But in the end, the discussion is about adoption, how can we introduce this as frictionless as possible, and still keep the core values intact.

There are a few problem areas to tackle when sharing
* Replay attacks
* Trust it is coming from the person that shared it
* How much software needs to be installed?
* Who holds the software?
