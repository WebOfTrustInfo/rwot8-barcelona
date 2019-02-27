
# Providing Decentralized Identity to the most vulnerable populations

## Draft: Rebooting Web of Trust VIII Topic Paper

## Authors

- Jeremi Joslin <jeremi@idpass.org>
- Greg Martel  - <greg@idpass.org>
- Hailey Park - <hailey@idpass.org>

## Problem

Decentralized identity solution has been mainly designed for the developed world and most implementation requires the need for expensive devices such as smartphones. However, by 2021, it is estimated that only 40% of the world’s population will own one. In contrast, there are one billion invisible people without an identity and a large majority still remains under the poverty line. Without a verifiable identity, one-seventh of the global population lacks the rights to access essential services such as Citizenship, Education, Justice, Health Care, Banking and Insurance.  

Moreover, in order to provide humanitarian aid to this population biometric is commonly captured to identify individuals. Although, from our experience, digital identity and biometric verification is often achieved by using a centralized identity management system which increases privacy concerns and requires an internet connection. 

## Idea

This is the reason why we are proposing a smart card based solution that leverages on W3C standards of Decentralized Identifiers and Verifiable Credentials. The card will be used to sign transaction and securely store the private keys and Verifiable Credentials.

### Access Management
One of the drawbacks of using a smart card is the lack of a user interface on the card, making it more difficult to selectively protect access to features and credentials stored on the card.
The following are authentication mechanism that could be used for our smart card:
- PIN code: one of the most common authentication methods in developed countries. However, based on our experiences, it was not considered as the preferred solutions due to low literacy and numeracy levels in some of the remote areas.
- Biometrics match-on-card: eliminates the need for a central database by both storing and matching fingerprint, iris and face biometrics data directly on a smartcard. 
- Cryptography: authenticate the Point of Services.
- Time Delay: can be used to differentiated between a simple tap, multi-tap or long-tap of the card.

Through the use and combination of these authentication processes, two possible solutions could be implemented:
Use of trusted devices like in the case of the credit card network where the user trust the terminal shows them the amount being deducted from the card and executes the action. This can be achieved by using cryptography and having the terminal authenticate to the card. The main advantage of this would be making it easier for the user to interact with the card, but to access their own data, they need to use a certified terminal. 
Use of a combination of authentication processes such as multiple PIN codes, fingerprint match or a delay to unlock access to different information. The advantage of this solution is that the user has increased control over their data as any device can be used to access it, but things such as keeping track of multiple PIN codes might be inconvenient for some.

These methods are not exclusive, and can actually be used in conjunction with others depending on how they are used. 











