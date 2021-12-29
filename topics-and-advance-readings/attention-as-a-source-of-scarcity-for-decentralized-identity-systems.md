# Attention as a Source of Scarcity for Decentralized Identity Systems

## Author

Maciek Laskus ([maciek@hive.one](mailto:maciek@hive.one), [​maciek.blog](http://maciek.blog/)​, ​[@macieklaskus](https://twitter.com/maciekLaskus)​)

[Source blog post](http://maciek.blog/attention-as-a-source-of-scarcity-for-decentralized-identity-systems/)

## Abstract

This paper proposes a new approach to introducing scarcity into identity systems without sacrificing privacy and self-sovereignty.

The method relies on quantifying attention flows between identities. It is predicated on the fact that attention is a basic element of all cognitive processes. It is also limited and therefore is a natural source of scarcity.  

## Problem

None of the designs for decentralized identity systems has been able to deliver on all three of the following features:  

-   Privacy-preserving
-   Self-sovereignty
-   Sybil-resistant

![Decentralized-Identity-Trilemma](https://user-images.githubusercontent.com/9806858/147667320-da6233aa-16ed-4953-8f3d-f682696c0a07.jpg)


I previously proposed to refer to this problem as Decentralized Identity Trilemma ([Laskus  2018a](http://maciek.blog/dit/))



## Requirements for a Solution

In order to address DIT one needs to provide Sybil-resistance without sacrificing privacy and self-sovereignty:

1.  No requirement of providing any ‘real name’<sup>1</sup>  documentation or credentials
2.  No hindering users ability to create and control identifiers including any limitation in terms of how many can be created.

## Solution

Identity is a collection of ideas that others have about a subject<sup>2</sup>. Creation of an idea requires paying attention.  

Attention is a basic component of all cognitive processes (Anderson, J.R. 2014) . In that sense, it plays a similar role in the brain that electricity plays in a computer.  

Both the computer and the brain can perform various types of computations. However, all of them require electricity and attention respectively.

![Screen Shot 2019-02-14 at 10 35 59 PM](https://user-images.githubusercontent.com/9806858/147667340-e83c438a-50b1-4f3f-bb63-3a04c2902ad4.png)


I can walk on a slackline, try to find a pattern in a string of numbers or plan what to cook for dinner. My brain is flexible enough to perform each one of these tasks, even though they require different forms of intelligence<sup>3</sup>.

However, what they all have in common is that require attention. I can switch between these different forms of intelligence, but I cannot use them all at the same time.  

Attention is scarce. We can hold only a handful of objects in our attention at a given point in time ([Byrne and Anderson  2001](https://docs.google.com/document/d/1-ltn85_RcU68Db6KBVM_LtlbXlVcWnqAdYk-DOq0_sI/edit#heading=h.uh3l6jrue5w6))   .  

Making up an idea about somebody is another type of computation that our brain performs and is subject to the same limitation as other cognitive processes.  

Not only making up an idea about somebody requires paying attention to that person. Additionally, we dedicate different amounts of attention to different people depending on how important we perceive them to be in a group.  

This claim is axiomatic. You can observe it in your own experience.  

A person with the highest status in a group is going to receive a lot of attention from the members of the group. A person with a low status is going to receive little attention.  

This is true in a boardroom, in a bar, at a conference or on Twitter.  

This last claim has been verified empirically by my team. We have designed an algorithm that has mapped and ranked members of the “crypto Twitter”. It is based exclusively on tracking attention flows between members of this group.  

The hypothesis that the results are accurate has been supported through an experiment of exposing the results to a large number of members of this group and observing their reactions ([Laskus  2018b]((http://maciek.blog/influence/))).  

It seems feasible that this approach can be applied to a variety of other data sets<sup>4</sup>.

## Conclusion

The proposed solution fulfills both requirements:  

1.  It does not require sacrificing privacy. One can create a pseudonymous account and attract the attention of other users. However, in order to do so, they must compete with others and provide something of interest. Not only this process takes a lot of time and effort, but also seems to be an effective way of filtering between products of organic and machine intelligence. We have seen hardly any bots receiving meaningful scores in our system.
2.  It does not limit one’s ability to issue and control its own identifiers. One is free to create as many as they wish, but this process alone does not provide them with any “voting power”. In order for these identifiers to form identities, they need to become recognized by intelligence behind other identities. Attracting their attention requires products of organic intelligence delivered over an extended period of time. Therefore, one can choose to create multiple identities but their total weight/voting power is going to be predicated on the amount of attention that the organic intelligence behind them can attract.

#### References

1.  Laskus, M. (2018, August 13). 2018a. Decentralized Identity Trilemma. Retrieved February 22, 2019, from  [http://maciek.blog/dit](http://maciek.blog/dit).
2.  Anderson, J.R. (2014). Cognitive Psychology and Its Implications. Worth Publishers, 53–78.
3.  Byrne, M. D., & Anderson, J. R. (2001). Serial modules in parallel: The psychological refractory period and perfect time-sharing. Psychological Review, 108, 847–869.
4.  Laskus, M. (2018, March 8). 2018b. What is Influence. Retrieved February 22, 2019, from  [http://maciek.blog/influence](http://maciek.blog/influence/).

#### Footnotes

1.  I.e. issued and recognized by centralized institutions and organizations, such as nation-states or banks.
2.  I am drawing upon the conclusions from  [Identity Crises white paper](https://github.com/WebOfTrustInfo/rwot2-id2020/blob/master/draft-documents/identity-crisis.md), however, I am intentionally using the term “ideas” instead of “correlations”. The reason is that the “idea” is more intuitive in this context since it indicates it is a product of a cognitive process.
3.  Various forms of intelligence can be also thought of as types of computation. Therefore, I am using these terms interchangeably throughout this document.
4.  Podcasts, conferences, Github, Reddit etc.
