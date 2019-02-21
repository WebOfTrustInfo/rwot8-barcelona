# Structures of Identity: Namespace 
Ethan Brown | ethn@ethn.co 



<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/1.png">
---

With the development of new digital networks, especially in recent years, the scope of identity has expanded significantly. On one hand, our trajectory points toward a future of sustainable solutions built in the context of collaborative networks based on communication between these identities. On the other hand, it appears that rather than "owning" our identities, we are increasingly owned by them -- aggregated and dependent. This limits the range of possibilities for emergent conversations and solutions. In light of this, I hope to present some work that involves exploring the features of this terrain, with an eye to seeing how we might move toward greater freedom from the limitations of current models of identity. 

Note: If you're reading this as a markdown, the image alignment is a bit broken. Try downloading the PDF in the same directory.

###  Two Approaches: - 

- Exploring some current limitations of current digital identity systems 

- Exploring the possibilities of shifting the emphasis from individuals and addresses to transactions and relationships in a shared namespace where it is easy to exercise control of the constituent elements of our identities 

Afterward, I discuss some philosophical assumptions that underly this exploration and pose further questions. 

### Current Limitations 

I’d like to focus on two characteristics of the way we approach identity that appear to be limiting our ability to exercise our freedom: 

#### 1) The dependence on memorable addresses 

Here I consider email, but any network handle which is difficult to change can be considered in this way. An average person has one or two email addresses, and can’t easily change their addresses without considerable effort. So, people don’t change their email addresses. The effect of this is essentially a tight coupling between a real person and their address. If you have someone’s address, you have access to them, because that connection is not generally ephemeral. Sometimes, this is not a desirable feature.


<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/2.png" width="300">
<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/3.png" width="300">
<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/4.png" width="300">
---

This is a concept I represent by showing that, at some level, because of this tight coupling, the person (circle) and the email (dotted circle) may be in some way considered one-and-the-same, because it is a relatively persistent relationship. 

#### 2) The closeness of the Device and Body 

Beyond the dependence on memorable addresses is the fact that we increasingly cannot expect the devices that allow us to connect to the Internet to be transparent to our identities. 


<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/5.png" width="300">
<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/6.png" width="300">
---

Here we see a rough approximation of the layers of abstraction through which information passes over time with respect to ALICE. In much the same way we looked at her IDENTITY-EMAIL, here we see her DEVICE-BODY, which arises from that fact that she usually has the device with her that enables her access to her digital identity. This results in a sort of inextricability from her digital identity, which is not always desirable. 

The important point for me here is the ubiquitous closeness of the BODY, DEVICE and INTERNET, and the fact that the DEVICE can generally assumed to leak information about ALICE she is not aware of, which is sufficient to circumvent her attempt at establishing a digital identity she controls. 

I’m not immediately interested in making the argument that there’s something inherently wrong with this situation. In many cases it is benign, and sometimes useful. Ultimately I think it is better to focus on whether there may be emergent properties of a network that has a layer for identity that make it more successful than what we have now. Where identity can be smaller than currently possible (more anonymous), more connected (greater representation of complexity), and enable greater trust (more certainty in engaging with others). 

### Infinite Namespace 

In light of these issues, it ought to be easy and quick to create a new address whenever you want, to alleviate these tight couplings and regain control over our access to our identities.

Instead of having a single address you have the ability to create addresses, in infinite NAMESPACE:


<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/7.png" width="300"><img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/8.png" width="300">
---

These nodes can have hierarchical relationships. I.e., a node can generate a child node every time it wants to initiate a new conversation with another node: 

<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/9.png" width="300">
---

This means instead of ALICE being one-and-the-same with her rented digital identity (left), there is a layer which serves to separate her from her digital identity (right): 


<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/10.png" width="300"><img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/11.png" width="300">
---

In this model there is a clearer separation between elements. ALICE has a mind and body, ALICE has a computer, and her computer enables her to create ALICE’S ALICES, nodal representations of her identity that hierarchically descend from her root representations to create micro identities that may or may not be associated with her directly. The ensuing hierarchical and historical graphs encode more complex and subtle representations of her relationships with others.

<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/12.png" width="300">
<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/13.png" width="300">
---

Especially if ALICE creates a new node every time she makes a new connection, she gains the ability to grant and revoke access to her identity. If this node begins to be misused, it can be revoked without affecting other relationships.

In the above instance, if DAN decides to start sending ALICE unwanted communication, she can delete the nodes that encoded and enabled their communication, and subsequent messages from DAN become undeliverable. And because DAN only ever knew the information about ALICE that was deducible from or represented by the graph of nodes he was granted, he has lost touch with ALICE. 

Furthermore, by clearly establishing the scope of a digital identity graph, we can create new identities which are outside of this domain, and explore what attributes should be associated with this identity. 

<img src="https://raw.githubusercontent.com/ethan3523/rwot8-barcelona/master/topics-and-advance-readings/media/soi_images/14.png">
---


## Guiding Principles 

### Functional Identity  

To a reasonable extent I have been approaching digital identity in a similar way to the Functional Identity definition Joe Andrieu lays out in "A Primer on Functional Identity", i.e. that identity is an abstraction that consists of correlations between subjects, identifiers, attributes, etc. 

If an individual is to have control of their identity, they must become aware of their "identity surface" i.e. the graph of attributes and identifiers that are correlated to them and their digital selves. From this vantage, we can be realistic about the identities we create in digital space, and have the opportunity to enter truly new digital spaces, without hidden assumptions conditioning or limiting our experience and action. 

## Identity is an Abstraction

Identity is an abstraction that has no smallest nor largest element, and as such the tooling around identity should permit a sensitivity to this fact. Ultimately, whoever is considered to be an individual cannot ultimately be isolated from the whole, because their body, language, thinking, etc. arise from the whole. Thus, I’ve found it also useful to talk about micro-identities as constituent elements of personal identities. Identity systems should reflect this by providing sufficient resolution and isolation to enable the coexistence of contradictory elements by loosening the expectation that identity-bearers should always be consistent.  

### Identity Linked to Bodies is Persistent

There is a special type of identity which results from the persistent association of an identity graph to a (human) body. One primary example of this is the consensual membership in institutions which explicitly require association of identities to individual bodies (such as states, countries, businesses, etc.). This is a necessary social construct which enables us to enforce responsibility for actions in traditional sociopolitical systems. But we also stand to gain from preserving systems of identity that do not connect to this body-connected identity, and improve on these systems’ ability to enable trust. When new identity information is linked to a body-associated persistent identity graph, it becomes difficult for the individual to whom it is linked to access the freedom of unconditioned space. Consequently, it should not generally be expected that online services or entities require information which links to this body-connected identity if there is a satisfactory alternative. 

### The Value of Access to New Identities 

I assume a priori that speech between two or more parties which is currently or will be observed by external parties and tied to identity (whether or not this is known) has inherently different qualities and capacities to speech that is known to be private. Both environments for speech are inherently valuable, and certain ideas can only emerge from one or the other environment. I feel that society stands to gain from developing a higher degree of sensitivity for ideas and concepts that could not arise in the presence of this type of observation. And because global society relies on the Internet, the Internet should provide robust means to engage in all levels and degrees of conversation, from public fora, to networks of complex inter-relational anonymous speech. 

### Decoupling Trust and Identity

If we see identity as existing as a set of nodes and connections, is it possible to communicate "on the strength of" attributes of identity without revealing personal information?