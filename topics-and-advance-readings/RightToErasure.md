

# GDPR: Right to erasure

_Authors: O.Burundukov <olegwb@gmail.com>, E. Moraes de Morais <eduardo.morais@gmail.com>_

_Company: ING Group, Netherlands_


## Abstract

In accordance to GDPR law ( see Appendix A ), once an owner of data has shared them with another party V, he/she has the right to withdraw the initial consent and to request the party V to erase the data. To execute the right the owner has to hold an evidence of the interaction with V. In the world of digital identities and anonymous credentials, the owner of data needs to obtain the digital proof of what and with whom the data have been disclosed.

## Introduction

This work is dedicated to the subject of sharing and withdrawing digital credentials in a self sovereign identity (**SSI**) system. We choose Hyperledger Indy SSI working system as the baseline, therefore the paper uses its architecture and vocabulary, e.g., three main Indy party roles in SSI process  are Issuer, Prover and Verifier.

### Facts about sharing digital data       

* Disclosing of the data presented in a digital format and shared by means of some network protocol is irreversible.

* Digital data cannot age and self-dispose ( physical media presumably can deteriorate, degenerate and decompose ).

* Once the credentials are delivered to the Verifier and are decrypted, there is no feasible method for the Prover for tracking of copies of the information enclosed in credentials, if such copies are made and/or shared by the Verifier.

* The prover has to obtain non-repudiated evidence of the finality of the process of sharing data with another party, the Verifier. Dishonest Verifier may just refuse to provide such evidence.

* Once data is being spotted by a human, it may be memorised.   


Having said that, it becomes obvious that pure technical measures do not facilitate the execution of the RTE. The legislation has to enforce the Verifier to put rules of GDPR into effect, and that is the legislation only, which can do that efficiently. As a consequence, the application of the law requires the circumstances of the interaction between Prover and Verifier documented in a form suitable for the legal case. In digital systems, the proof of interaction is usually a message digitally signed by all participants, where facts about the interaction are enlisted.

### Glossary

Hereafter the following abbreviations take place:

**P** - Prover  ,  **V** - Verifier

**PRQ** - proof requested

**pk**, **sk** - public key, secret key

**TTP** - trusted third party

**MSA** - multi-signature algorithm


## Implementation

Data sharing  in SSI system consists of the exchange of credentials between two parties. The applicability of RTE in this case necessitate the generation of bi-lateral non-repudiated evidence of transferring data.

### Naive solutions


* **P** sends the request to start protocol to **V**
* **V** responds with PRQ
* **P** constructs the proof and sends it to **V**
* **V** signs the proof plus original **PRQ** and sends it back as the receipt

One can see that dishonest **V** can repudiate that the **P** has sent the proof.

Slightly better version is where **P** can encrypt the proof beforehand:

* **P** sends the request to start protocol to **V**
* **V** responds with PRQ
* **P** generates temporary **sk**. **P** constructs the proof, encrypts it with **sk** and sends it to **V**
* **V** signs the encrypted proof plus original **PRQ** and sends it back as the receipt
* **P** saves the receipt along with **sk** and shares the **sk** with **V**


There are still problems here: dishonest **V** can repudiate that the **P** shared the **sk**. Besides that, the **V** has to sign encrypted proof without seeing its content.

Using Trusted Third Party

The protocol of non-repudiation may be built with only two parties interacting, however it has been argued that such protocol is inefficient.

The history of non-repudiating protocols starts from multiple works published by J. Zhou and D. Gollmann between 1996 and 2000. These papers  were summarised and reviewed by P.Louridas in 2000.  The papers propose using TTP and they cover dispute resolution, fairness, timeliness and the cases of protocol recovery and protocol abort. Each next version of the protocol adds an improvement over the previous version by addressing one of concerns. The first work where more than two parties exchange data was published some time later in the paper by Steve Kremer and Olivier Markowitch.

The non-repudiation is twofold. First, the non-repudiation of origin guards against the originator of a message falsely denying having sent the message. Second, non-repudiation of receipt defends the originator against the recipient of a message falsely denying having received the message.  In case of disclosing data in the SSI protocol , one can see that the Proof object is self-containing evidence of origin. Therefore we can safely state that bi-lateral evidence is formally uni-lateral in our case. 
All the protocols discussed above have one common property: the shared data is encrypted first, and then the key to it has to be shared at the very last step of  the protocol.

Main problem with sharing a key emerges with the requirement to maintain a public service for that.  Papers refer to such service as public FTP site  or Web server run by a party, either Prover or Notary, depending on the version of the protocol. Recall that SSI systems facilitate anonymity  of the Prover facing Verifier. There is high chance that a Prover operates the SSI application on a mobile device, where service access entries are not available for public in general way. We conclude that running key service on the side of a Prover becomes great challenge. We argue that the versions of  non-repudiation protocol where the key is generated by a Prover but shared by TTP ( Notary) remain the only realistic ones in the case of SSI.

We shall see that if the Notary shares the decryption key using publicly available service, such as Web server,  the Notary must be able to prove later that the key was obtained by Verifier. It can be achieved by the recording of the identity of  a reader during each reading operation, which ,in turn, requires the reader to prove his/her identity.  Once the chosen Verifier accomplishes the reading of the key, Notary considers the protocol finished and sends the confirmation to the Prover.

Note that  disclosing  keys with arbitrary users can result in revealing the weaknesses in underlying cryptographic schemas, therefore Notary has to restrict the access to the key before publishing by encrypting it with trusted public key of the Verifier.

Two other important properties of non-repudiation protocol are unique labelling for each message and time limits for waiting for next message. The former is required to identify each step in the protocol, and the latter makes provision for the eventual termination.

## Smart contracts as key storage

Recall that the Notary has to register the event of sharing the key with chosen Verifier, and this requires checking the identity of each client which performs read operation. This process can be cumbersome.

We shall consider using a notion of smart contract on the distributed ledger for holding keys and for capturing the event. Smart contract  is able to check its caller’s identity, therefore the contract should be able to write yet another change into the ledger, namely the receipt of reading the key by designated Verifier. This evidence is very strong for the purpose of RTE, and it remains publicly available and verifiable. We should analyse whether the receipt has to hold the details of the protocol interaction too.

It is technically feasible to map the entire protocol between P, V and N into the sequence of transactions in the ledger. However,  this would lead to the pollution of the ledger.


## Proposal

The protocol description is given in the second document, RightToErasure-protocol.pdf


## Other aspects

### Policy of the Verifier

The legislation of the process may require the **P** to be informed of the policy of the data holder ( verifier ) with respect to GDPR and RTE. The **P** may decide not to continue with the process in the circumstances where the policy of the receiver disregards GDPR with respect to RTE.
The protocol has to allow the policy to be observable for **P** beforehand. From this point, it makes sense to sign and to publish the policy on the ledger, and to include the reference to the record in the ledger into the protocol. The protocol continues in case presented reference is accepted by the **P**.

### Anonymity

In case of anonymous identities, when the **P** executes the right to erasure, he/she needs to disclose real identity to supply the legislation process. Hyperledger Indy designates special role for that,  the Inspector.

### MITM-attacks   

The **P** and **V** have to communicate safely and securely to eliminate the threat of man-in-the-middle attacks. This inevitably leads to the requirement for strong public key infrastructure. Hyperledger INDY already facilitates decentralised PKI.


### ZK proofs
Anonymous credentials involve partial disclose of data and employ zero knowledge proofs.  Sometimes the **P** discloses so little about him/herself so that the demand of the privacy keeping seems to be negligible. It is also hard to link ZK proofs to real identity.


## Conclusion

* Executing the right to be forgotten is not feasible by means of crypto techniques only.

* The provisioning of the evidence of the actions performed by parties in the protocol is feasible by means of multi-signatures and trusted third party.

* While the notion of trusted third party is opposed to the nature of public permissionless ledgers, the Hyperledger Indy is merely the chain of trust, where TTP fits with the role of attested observer, similar to the role of Inspector.   

* The usage of ZK proofs together with anonymity almost solves entire problem. However, stored ZK proofs have to be qualified first by the law as objects not falling into the data categories protected by the GDPR.

* It is easy to see that ZK cannot be always used for personal credentials in real scenarios.   



## Appendix A : GDPR: Right to erasure

### Glossary

_Controller_ means the natural or legal person, public authority, agency or other body which, alone or jointly with others, determines the purposes and means of the processing of personal data; where the purposes and means of such processing are determined by Union or Member State law, the controller or the specific criteria for its nomination may be provided for by Union or Member State law;


### Right to erasure, art 17, GDPR

1. The data subject shall have the right to obtain from the _controller_ the erasure of personal data concerning him or her without undue delay and the controller shall have the obligation to erase personal data without undue delay where one of the following grounds applies:

  1. the personal data are no longer necessary in relation to the purposes for which they were collected or otherwise processed;
  2. the data subject withdraws consent on which the processing is based according to point (a) of Article 6(1), or point (a) of Article 9(2), and where there is no other legal ground for the processing;
  3. the data subject objects to the processing pursuant to Article 21(1) and there are no overriding legitimate grounds for the processing, or the data subject objects to the processing pursuant to Article 21(2);
  4. the personal data have been unlawfully processed;
  5. the personal data have to be erased for compliance with a legal obligation in Union or Member State law to which the controller is subject;
  6. the personal data have been collected in relation to the offer of information society services referred to in Article 8(1).

2. Where the controller has made the personal data public and is obliged pursuant to paragraph 1 to erase the personal data, the controller, taking account of available technology and the cost of implementation, shall take reasonable steps, including technical measures, to inform controllers which are processing the personal data that the data subject has requested the erasure by such controllers of any links to, or copy or replication of, those personal data.


3. Paragraphs 1 and 2 shall not apply to the extent that processing is necessary:
  1. for exercising the right of freedom of expression and information;
  2. for compliance with a legal obligation which requires processing by Union or Member State law to which the controller is subject or for the performance of a task carried out in the public interest or in the exercise of official authority vested in the controller;
  3. for reasons of public interest in the area of public health in accordance with points (h) and (i) of Article 9(2) as well as Article 9(3);
  4. for archiving purposes in the public interest, scientific or historical research purposes or statistical purposes in accordance with Article 89(1) in so far as the right referred to in paragraph 1 is likely to render impossible or seriously impair the achievement of the objectives of that processing; or
  5. for the establishment, exercise or defence of legal claims.
