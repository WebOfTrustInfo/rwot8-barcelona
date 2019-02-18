

# GDPR: Right to erasure

_Authors: O.Burundukov <olegwb@gmail.com>, E. Moraes de Morais <eduardo.morais@gmail.com>_

_Company: ING Group, Netherlands_

## Abstract

In accordance to GDPR law ( see Appendix A ), once an owner of data has shared them with another party V, he/she has the right to withdraw the initial consent and to request the party V to erase the data. To execute the right the owner has to hold an evidence of the interaction with V. In the world of digital identities and anonymous credentials, the owner of data needs to obtain the digital proof of what and with whom the data have been disclosed.

## Introduction

This work is dedicated to the subject of sharing and withdrawing digital credentials in a self sovereign identity (**SSI**) system. We choose Hyperledger Indy SSI working system as the baseline, therefore the paper uses its architecture and vocabulary, e.g. three main Indy party roles in SSI process  are Issuer, Prover and Verifier.

### Facts about sharing digital data       

* Disclosing of the data presented in a digital format and shared by means of some network protocol is irreversible.

* Digital data cannot age and self-dispose ( physical media presumably can deteriorate, degenerate and decompose ).

* Once the credentials are delivered to the Verifier and are decrypted, there is no feasible method for the Prover for tracking of copies of the information enclosed in credentials, if such copies are made and/or shared by the Verifier.

* The prover has to obtain non-repudiated evidence of the finality of the process of sharing data with another party, the Verifier. Dishonest Verifier may just refuse to provide such evidence.

* Once data is being spotted by a human, it may be memorised.   


Having said that, it becomes obvious that pure technical measures do not facilitate the execution of the RTE. The legislation has to enforce the Verifier to put rules of GDPR into effect, and that is the legislation only, which can do that efficiently. As a consequence, the application of the law requires the circumstances of the interaction between Prover and Verifier documented in a form suitable for the legal case. In digital systems, the proof of interaction is usually a message digitally signed by all participants, where facts about the interaction are enlisted.

## Implementation

Indy verification ( data disclose ) process consists of the exchange of credentials between two parties. The applicability of RTE in this case necessitate the generation of bi-lateral non-repudiated evidence of transferring data. One can see that the Proof object is self-containing evidence of the data disclose for the Verifier. On the other hand the evidence required by Prover is merely the confirmation that the Proof has arrived to the Verifier. We assume that dishonest Verifier can deny it.


### Glossary

Hereafter the following abbreviations take place:

**P** - Prover  ,  **V** - Verifier

**PRQ** - proof requested

**pk**, **sk** - public key, secret key

**TTP** - trusted third party

**MSA** - multi-signature algorithm

### Simple solution


We use Indy verification algorithm  as the baseline:

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

## Proposal

The verification process requires additional participant, notary, a **TTP**. Other aspects, anonymity and confidentiality of data exchange between parties, still have to be facilitated, for example by the secure  verification protocol implemented in target SSI system.  

The notary plays a role of communicator between P and V:
* the notary initialises the context of the process;
* the notary collects signatures produced by both P and V at different stages of the protocols into the context using **MSA**, and signs the context at several checkpoints too.

The details of the proposal are to be discussed in the workshop.

## Other aspects

### Policy of the Verifier

The legislation of the process may require the **P** to be informed of the policy of the data holder ( verifier ) with respect to GDPR and RTE. The **P** may decide not to continue with the process in the circumstances where the policy of the receiver disregards GDPR with respect to RTE.
The protocol has to allow the policy to be observable for **P** beforehand. From this point, it makes sense to sign and to publish the policy on the ledger, and to include the reference to the record in the ledger into the protocol. The protocol continues in case presented reference is accepted by the **P**.

### Anonymity

In case of anonymous identities, when the **P** executes the right to erasure, he/she needs to disclose real identity to supply the legislation process. Hyperledger Indy designates special role for that,  the Inspector.

### MITM-attacks   

The **P** and **V** have to communicate safely and securely to eliminate the threat of man-in-the-middle attacks. This inevitably leads to the requirement for strong public key infrastructure. Hyperledger INDY already facilitates decentralised PKI.


### ZK proofs
Anonymous credentials involve partial disclose of data and employ zero knowledge proofs.  Sometimes the **P** discloses so little about him/herself so that the need of the regulation of the  privacy seems to be negligible. Is is also hard to link ZK proofs to real identity.


## Conclusion

* Executing the right to be forgotten is not feasible by means of crypto techniques only.

* The provisioning of the evidence of the actions performed by parties in the protocol is feasible by means of multi-signatures and trusted third party.

* While the notion of trusted third party is opposed to the nature of public permissionless ledgers, the Indy ledger is merely the chain of trust, where TTP fits with the role of attested observer, similar to the role of Inspector.   

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
