# Staying Anonymous With DIDs
## Author

David Stark david.stark@securekey.com

## Abstract

This paper looks at the ways the different parties in a sharing transaction may wish to stay anonymous.
In a simple sharing transaction there are three parties involved:
- Requestor - The party who is asking for some information
- User - The party who the information is being requested from
- Trusted Data Provider - A party who the requestor will trust to provide data for the user

If the user is providing non identifiable information (such as age) they may not want to be tracked by the requestor, for example they do not want the requestor to be able to see they visited them on previous occasions.

## The Problem

If a user provides the same DID (associated to a verifiable claim, for example) to multiple parties  – or even the same party multiple times  – those parties, if colluding, could track an individual user's activity. For instance if a user needs to prove they live in a particular country (the claim) to qualify for services at two different companies and provides the same DID associated to the "country of residence" claim to prove their eligibility, those parties requesting the information then (if colluding)  could confirm that it is in fact the same user/individual. The problem is compounded when multiple anonymous claims (from different sources) need to be combined in the same exchange.

## How can this be solved

If a user needs to issue a claim where they wish to remain anonymous then they can only issue that specific claim once. This would mean that to satisfy a request where the user wishes to stay anonymous then they would need to create a new DID for the purpose of this transaction only and contact thier data provider to provide a new claim for this DID that is not linked in anyway (at least visible to anyone except the data provider and the user) to the users existing DID or claims. Associated issuers, holders and verifiers would need to treat the 'transaction specific' DIDs and claims appropriately by enforcing audience, permissions, and expiry.
