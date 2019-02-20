# A Notebook Workbench for SSI

By Eric Welton (eric@korsimoro.com)

The technical cost of experimenting with and evaluating web-of-trust technology,
SSI and other, remains bewilderingly high.  This situation hinders broad
adoption.

Impacts of this complexity include:
- Biasing new projects towards build-from-scratch versus build-upon
- Forcing focus on infrastructure and edge tech, rather than VC-ecosystem flows
- Blocking effective cross-system evaluation and interoperability work
- Pushing UX into products and delaying UX development

I propose use of the Jupyterlab interactive computing environment as a means
of:
- facilitating broad adoption
- promoting interoperability
- supporting SSI UX development
- expanding the number of documented use-cases

## Kool Aid Syndrome

Spinning up a testnet for one of the SSI DLTs an evaluation framework for
DID resolution via the universal resolver is non-trivial.  When
factoring in the device-locked nature of some SSI-tech, spinning up an
evaluation environment may involve setting up iOS or Android simulation
environments.  Even setting up to develop UX components for DID, web-of-trust
constructs, proof-and-credential exploration, and verifiable displays requires
non-trivial setup.

To be certain, setting up these environments is not, in itself, a roadblock.
Many, if not most, of the technical participants at RWOT have done or routinely
do exactly this.  In fact, if you work primarily on a single platform you
probably have a stable and comfortable local environment, based on code with
which you are intimately familiar.  The combination of in-depth knowledge and
long term stability lets project developers focus on feature development and
core bug fixes rather than removing obstacles which plague first time users,
testers, and other evaluators.

This is what I call the Kool-Aid Syndrome - everything becomes clear after
the kool-aid kicks in, but the first step is drinking the project kool-aid.
In order to join the party, you must first integrate with the community,
explore the chat channels and forums (often in a foreign language), track down
the relevant technical documentation, (perhaps translate them into your
language), and begin working the kinks out of your local setup as you work
through the getting started guide.

This is reasonable for early stage development of new technology, but consider
someone kicking around the idea of how to solve a non-technical problem where
a strong SSI infrastructure would be a game changer.  During the build-out of
the business and product model, the project owners ask _“should we use one of
these existing systems, and if so which one, how would that work and how does
that change what we do?”._

During this formative exploratory time there is a rich interplay between
_“can system X do Y?”_ and _“system X supports Z, how can we leverage that?”_
The people involved are not starting from a position of years of identity-tech
immersion, rather, they are trying to understand identity-tech at the same time
as they are trying to solve their specific problem.  This is why it is critical
for developers to be able to do hands-on exploration of a system, in order to
bring value to the solution development discussions.

Unfortunately, the answer to _“can or how does X do Y?”_ is not often
_“let me get you an answer in an hour”_.  Instead, more often than not, the
answer is  _“I’ll work on that, I’m still trying to set up X, but the part that is supposed to go bing went bong.  I’ll check the chat channels, and I’ll check with Sally, maybe she had luck upgrading *irrelevant infrastructure part Z* over the weekend - that might get us a bing, i think my local firewall was blocking internode traffic, let me just…..”._

The result of Kool-Aid Syndrome are outcomes such as:
- Let’s just build our own system from scratch, I’m sure we can get it to do exactly what we want, i’ve got some really good ideas about key recovery from this bitcoin youtube video I watched last week…..
- Let’s pick one and put all of our eggs in that basket - we will be an X project, not an SSI project, and if we need features we can just fork the codebase.
- Let’s just use standard social auth, we’ll add SSI later, SSI is really just another version of a site-login and user-profile, right?  Let’s add a DID column to the database, would that work?
- The phone fingerprint is popular, let’s just protect all the data that way and tell Jerry to add “biometrically secured personal data” to the pitch decks, problem solved!

## Education and Use-Cases

The value proposition of SSI is not in the technical details of any specific
system, rather it is in the credentialing dance, where multiple SSI and non-SSI
systems exchange information and enable individuals to achieve something they
could not previously achieve.  There are some textually documented use-case
libraries, but while necessary, these are not sufficient when it comes to
educating the adopting community.

Specific cases in which I have had personal experience include
interbank-KYC-markets, education document verification, and
immigration-and-citizen systems.  In these cases, the stakeholders are quickly
confused in a sea of Alice, Bob, Example Bank, Example University, Example
Government, DIDs, Verifiable Credentials, Zero-Knowledge Proofs, and
Blockchains.  Sometimes the take-away is only
_“it uses blockchain, we need that, right?”_ or _“it uses blockchain, but we
can’t be a bitcoin system, let’s stick with [favorite enterprise vendor]”._

To mitigate this, substantial effort is required to build pitch decks and to
walk through explanations and logic that are already deeply familiar to much
of the RWOT cohort.  The challenge is to do this quickly, efficiently, and
respectfully - as the decision makers and stakeholders are not purposefully
resistant - rather they have 150 other high priority tasks and they are trying
to balance _making it happen_ with _doing it right_.

In cases where the presentations leave the decision makers intrigued, the next
step is inevitably setting up a “technical deep dive” with the engineers.  This
sort of session is where you sit down and really evaluate the technology in
action, perhaps collaboratively working through a getting started example and
hoping that the Kool-Aid  starts to kick in.

In one particularly telling case, evaluation of Verifiable Credentials was seen
as so far afield, that the decision was made to release a digital employment
credential in the form of a “smart-phone app” which displayed a PDF scan of the
paper document it replaced. No cryptography or security, of any kind, other
than the smart-phone device security was in play - not even HTTPS for REST calls.

## UX & Playtime

The call for a robust UX for web of trust components, like DIDs, VCs, proofs,
trust web navigation, and assurance visualization continues to gain steam.
Given the scope of identity-tech, the development of a strong visual language
which can engage the world’s population is critical.  Imagine how much less
Kool-Aid one has to drink if the above presentations and pitches could draw
from a common UX language.

Typical UX development is product and project driven.  It only emerges as a
common lexicon after sufficient adoption.  In terms of identity-tech, we may
be able to invert this pattern and spur adoption by developing a UX lexicon
first.  But how does one build UX components for identity-tech outside of the
scope of a specific project?

I think that what is needed is the ability to play with credential flows and
to both explore and generate a wider range of richly documented use-cases.
If the Kool-Aid can be removed then people who are interested in issues of
usability and credential flow can work directly on the shared UX lexicon and
can expand the documented use-case library to the point where that library
itself becomes less of a ‘for example’ and more of a ‘let’s see how this is
done elsewhere’.

## Let's fly to Jupyter

I have been working on an SSI tech workbench based on the Jupyter notebook
environment popular in data science communities.  Jupyter is an interactive
computing environment which separates the UI from the background compute, and
which can be frozen and re-distributed in the form of educational notebooks.

In an interactive computing environment, commands can generate rich output.
It is not a simple terminal session.  This is why such notebooks have become
a mainstay in the data-science world - where many projects are ad-hoc
and every data set needs a little bit of programmatic massaging before it
is useful.  With a user base of over 5M, a notebook presence of over 10M, and
support from major vendors like Azure, this sort of interactive computing is
neither a passing fad nor a far flung future vision - it is now, and it is
mature - it is just not yet a part of the SSI world.

The sort of interaction that interests me, and I think is of interest to the
identity-tech development community, looks something like this:

```
# start up a local blockchain
launch veres.one on v1.local
# start up another local blockchain
launch sovrin on sovrin.local
# create test users
alice = create_actor(‘alice’,{... payment definition })
bob = create_actor(‘bob’,{... payment definition})
# grab some did information
(did_x,ddo_x) = grab_new_did(‘v1.local’,alice.payment_info)
# run evaluation/verification tests on a DID Document
validate(ddo_x)
assign(alice,did_x)
# grab bob’s did information
(did_y,ddo_y) = grab_new_did(‘sovrin.local’,bob.payment_info)
assign(bob,did_y)
# and so on, until we can get to something really sexy like
run_w3c_vcwg_use_case_suite({student:bob,mortgage:a1Mortgage….})
```

The W3C VC working group, for example, provides a set of use-cases in the
form of text in a github repository.  Wouldn’t it be great if we could provide
a ‘live’ notebook which allows someone to quickly execute the actual use case?
In so doing:
- Use-Case Notebooks can be distributed to demonstrate, not as theory, but as running code, the applicability of SSI technology - it can be handed to anyone, anywhere, who can actually “use” SSI technology, instead of reading “about” the technology
- Use-Cases can be explored, actively, in the context of interoperability and edge-case investigation - the ability to start with a reproducible, active baseline, and then tweak the environment slightly and re-run the scripts, promotes interoperability.

Such notebooks can be easily redistributed, perhaps as documents in the same
repository as the current text-based use cases.

When it comes to the UX - if it is easy to “spin up some actors, holders,
issuers, verifiers, etc”, then we can focus on the UX.  Consider a
```
# issue a digital driving license
DL = issue({...},alice,landTransportOffice)
present(DL)
<output is a React Widget, or a Verifiable HTML widget, etc.>
```

The output produced *is* a re-usable UX component, placed in a wrapper which
adapts the component to the ZMQ based Jupyter notebook/kernel environment.

This allows a UX developer to focus on the UX itself, and on the UX
relationship to the VC environment, without being bogged down in the technical
details of setting up the development harness, or even in product details.
The product, in this case, is the interactive library of use-cases.

## There is no Kool-Aid on Jupyter

The workbench, as it is envisioned, is distributed as an electron app
(e.g. jupyterlab_app), so that it can be “downloaded and run” as any other
desktop application.  Dependencies are limited to external language
installations (python, rust, go, etc.) and docker.  This is part of the
existing jupyterlab framework, and would need to be expanded slightly to
accommodate common SSI elements.

In Jupyter terms, the SSI specific runtimes are known as Kernels, and with a
current coverage of over 100 languages, adding a few SSI specific systems
means following a well-traveled pathway and is not prohibitive.

Once downloaded, the ability to open up “notebooks” which contain reproducible investigations of specific use-cases is as simple as “clicking on the file”.

In terms of presenting to stakeholders and decision makers, and in terms of
exploring “how can we leverage SSI to solve our problem”, the requirement of
deep investment within a specific system and the requirement of strong
prior-knowledge of the last years of SSI technology is replaced by a focus
on “download, explore, and engage”

The ability to connect this sort of easily accessible workbench to
engineering teams, both before and after engaging decision makers and
product teams, substantially reduces the need for long, Kool-Aid fueled
technical deep dives involving specific systems.

Using this approach, fostering SSI adoption can focus on the dance of
credentials, issuers, holders, verifiers, relying parties, assurance mavens,
compliance officers, audit specialists, governance authorities, and end
user abilities - rather than on the technical details of making sure the
right version of node or libsodium is installed or that the docker environment
is correctly configured to connect with the local test ipads and androids.

Furthermore, the development of appropriate UX technology can be combined
with the expansion of the use case library, in the form of redistributable
educational notebooks.
