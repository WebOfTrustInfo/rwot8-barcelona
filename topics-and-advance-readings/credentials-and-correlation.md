# **Credentials and Correlation**

*A submission to Rebooting the Web of Trust #8*

Jack Poole, jack.w.poole@gmail.com 

## **Background**

Within SSI frameworks, selective disclosure using zero-knowledge proofs and verifiable credentials enables users to prove specific attributes about themselves, while keeping other attributes private. This could allow a user to prove that that are a graduate of University X or are a current employee of Company Y without revealing their name or other aspects of their identity. 

In scenarios where a user wishes to disclose multiple attributes about their identity, whether from a single credential or from a combination of multiple credentials, it’s important for users to understand that disclosing multiple attributes about one’s identity could expose them to unwanted correlation. 

## **Problem**

While data can be anonymized or de-identified to protect user privacy, de-anonymization attacks are possible when different data sets can be linked together. For instance, when multiple de-identified datasets are analyzed together, such as mobile phone logs and transit trips [1], correlation can expose individual identities. Selective disclosure workflows allow SSI users to share attributes about their identity in a privacy-respecting way, but only if they share attributes that can’t be correlated. How can users be educated of the privacy implications of such behaviors, and what role can software agents have?


## **Goal**

It should be clear to SSI users that utilizing selective disclosure technologies can expose them to correlation attacks. Similar to SSL warnings, users should be guided away from vulnerable situations with explanations and clear guidance of safe practices.   

I would like to explore the potential and limitations that software agents can have in protecting user privacy. How can agents assess a user’s degree of anonymity when sharing multiple attributes? What anonymity set is considered safe for certain applications? 

*References:*

[1] http://news.mit.edu/2018/privacy-risks-mobility-data-1207
