# Applying the Principle of Least Authority to User Interaction
by Bill Tulloh

Object capabilities (ocaps) are increasingly recognized as an important tool for achieving the goals of self-sovereign identity. Many of the principles of self-sovereign identity, such as minimization and protection, can best be achieved through the disciplined pursuit of the principle of least authority that ocaps enable. This paper examines how POLA can be extended to better protect users when exercising their self-sovereign identity.

## Rich Sharing on the Web

Perhaps most visibly, ocaps minimize the degree to which systems must rely on identity for access control, by replacing frequent identity checks with bearer instruments representing authority. Ocaps replace [identity-based access with authorization-based access.](http://www.hpl.hp.com/techreports/2009/HPL-2009-30) 

As Marc Stiegler has argued, the choice of access control model has important implications for support for secure cooperation. He identifies six key features, enabled by ocaps, that support [rich sharing.](http://www.hpl.hp.com/techreports/2009/HPL-2009-169.pdf): dynnamic, attenuated, chained, cross domain, composable, and accountable. Together, these features ensure that people can share naturally with least authority. For example. chained, the ability to delegate authority, ensures that agents have enough authority, while attenuation, the ability to grant reduced authority, ensures that agents have least authority. 

Alan Karp illustrates this with the [following example:](https://alanhkarp.com/publications/Access-Control-for-IoT.pdf) “In an emergency, Marc asked me to park his car in my garage. I couldn’t do it, so I asked my neighbor to do it for me and told her to get the garage key from my son.”
1. Dynamic. It’s an emergency, so there’s no time to find an administrator to change permissions.
2. Attenuated. Marc did not have to give me all of his permissions, just the car keys.
3. Chained. I could pass Marc’s car keys to my neighbor, further attenuating with just the valet key. 
4. Composable. My neighbor combines one permission she got from me, the car key, with one she got from my son, the garage key, to complete the task.
5. Cross-domain. There are three families involved, each with its own policies, yet there is no need to communicate policies to another domain. In this example, I didn’t need to ask Marc to change his policy to grant my neighbor permission to drive his car.
6. Accountable. If Marc finds a new scratch on his car, he knows to ask me to pay for the repair, it’s up to me to collect from my neighbor.

Rich sharing demonstrates how the applyinng the principle of least authority enables us to cooperate with those with whom we have only limited trust. POLA enables secure cooperation across trust boundaries. 

## The Powerbox Pattern

Ocaps can also play an important role in the control, access, and protection of user identities. For example, ocaps, by providing confinement of authority, helps [stop exfiltration](https://www.youtube.com/watch?v=pig-sIS8_Wc) of users' data by malicious code. Moreover, as we build identity wallets and user agents, we must be ensure both a high level of security and usability. Ocaps help achieve high security by applying fine-grained POLA to [reduce the attack surface.](https://www.youtube.com/watch?v=wQHjITxQX0g&t=0s&index=20&list=PLKr-mvz8uvUgybLg53lgXSeLOp4BiwvB2) Such fine-grained division of authority may at first glance appear as a usability nightmare. Yet, much interesting work has been done showing that this need not be the case. Ocaps combine designation with authority, which enables user acts of designation - needed anyway - to also control the division of authority. 

The use of ocaps for secure interaction was pioneered during the early 2000sin the work of Mark Miller and Marc Stiegler on [CapDesk and the DarpaBrowser.](http://www.combex.com/papers/darpa-report/html/) A major design goal was to put the user, not their applications, in charge. An important step in this direction, was to the invention of [the PowerBox pattern.](http://www.hpl.hp.com/techreports/2006/HPL-2006-116.html) The CapDesk Powerbox was a software module that mediates the granting of authorities to a capability confined application from the user. Individuals necessarily hold many authorities, but there is no need for their applications to do so as well. The Powerbox manages the users authorities and safely allocates them as needed to applications, thus applying the prinicple of least authority. 

## Guidelines for Secure Interaction design

Ka-Ping Yee, building on the CapDesk work, identified a set of ten [guidelines for secure interaction design.](http://people.cs.vt.edu/~kafura/cs6204/Readings/Usability/AliigningSecurityUsability.pdf) Guidelines well supported by ocap architectures.

General principles
* Path of least resistance. The most natural way to do a task should also be the safest.
* Appropriate boundaries. The interface should draw distinctions among objects and actions along boundaries that matter to the user.

Maintaining the Actor-Ability State
* Explicit authorization. A User’s authority should only be granted to another actor through an explicit user action understood to imply granting.
* Visibility. The interface should let the user easily review any active authority relationships that could affect security decisions.
* Revocability. The interface should let users easily revoke authority that the user has granted, whenever revocation is possible.
* Expected ability. The interface should not give the user the impression of having authority that the user does not actually have.

Communicating with the users
* Trusted path. The user’s communication channel to any entity that manipulates authority on the user’s behalf must be unspoofable and free of corruption.
* Identifiability. The interface should ensure that identical objects or actions appear different.
* Expressiveness. The interface should provide enough expressive power to let users easily express security policies that fit their goals.
* Clarity. The effect of any authority-manipulating user action should be clearly apparent to the user before the action take effect.

While applying ocaps to secure interaction desgin remains a work in progress, we believe that much can be gained from exending the principle of least authority to the user.  
