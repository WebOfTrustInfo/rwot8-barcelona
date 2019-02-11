# Aligning SSI with European Union identity legislation (aka eIDAS Regulation)

## Authors

Nacho Alamillo & Santi Casas

## Abstract

This paper aims to advance the alignment of SSI solutions with the eIDAS Regulation regarding electronic identification.

## Background

Regulation (EU) No 910/2014 of the European Parliament and of the Council of 23 July 2014 on electronic identification and trust services for electronic transactions in the internal market and repealing Directive 1999/93/EC (eIDAS Regulation, avaliable at http://data.europa.eu/eli/reg/2014/910/oj) aims, among other objectives, to facilitate the legal recognition of electronic identification means - used in Member States to access public services - by other Member States.

The eIDAS Regulation has been developed, regarding electronic identification, by different implementing acts, notably: 

- Commission Implementing Regulation (EU) 2015/1501 of 8 September 2015 on the interoperability framework pursuant to Article 12(8) of Regulation (EU) No 910/2014 of the European Parliament and of the Council on electronic identification and trust services for electronic transactions in the internal market (eIDAS Interoperability regulation, available at http://data.europa.eu/eli/reg_impl/2015/1501/2015-09-09).
- Commission Implementing Regulation (EU) 2015/1502 of 8 September 2015 on setting out minimum technical specifications and procedures for assurance levels for electronic identification means pursuant to Article 8(3) of Regulation (EU) No 910/2014 of the European Parliament and of the Council on electronic identification and trust services for electronic transactions in the internal market (eIDAS Assurance Levels regulation, available at http://data.europa.eu/eli/reg_impl/2015/1502/oj).

According to eIDAS Regulation Whereas (27), the eIDAS Regulation should be technology-neutral, meaning that the legal effects it grants should be achievable by any technical means provided that the requirements of the Regulation are met. Thus, it should be legally possible to recognise an particular setup of an SSI system under eIDAS, allowing its usage for public services transactions, which are a relevant part of the market.

It is also interesting to note that, according to eIDAS Regulation Whereas (17), Member States should encourage the private sector to voluntarily use electronic identification means under a notified scheme for identification purposes when needed for online services or electronic transactions. The possibility to use such electronic identification means would enable the private sector to rely on electronic identification and authentication already largely used in many Member States at least for public services and to make it easier for businesses and citizens to access their online services across borders. 

One interesting reason to foster the legal acceptance of eIDAS eIDs in the private sector is identification in AML/CFT procedures under Directive (EU) 2015/849 of the European Parliament and of the Council of 20 May 2015 on the prevention of the use of the financial system for the purposes of money laundering or terrorist financing, amending Regulation (EU) No 648/2012 of the European Parliament and of the Council, and repealing Directive 2005/60/EC of the European Parliament and of the Council and Commission Directive 2006/70/EC, amended by Directive (EU) 2018/843 of the European Parliament and of the Council of 30 May 2018 (consolidated text available at http://data.europa.eu/eli/dir/2015/849/2018-07-09). 

If case one or more Member States of eIDAS Regulation make use of the possibility mentioned in eIDAS Regulation Whereas (17), that would facilitate the full expansion of a SSI system, inheriting the legal value of the eIDAS Regulation recognized identification means.

## Use cases 

When analysing the interplay between the eIDAS Regulation and the SSI systems, at least two use cases must be considered.

### Using eIDAS identification means when creating verifiable claims

The first use case considers the utilization of an electronic identification system for the validation of the identity attributes that are to be included in any assertion contained in the DID document. This would be a scenario in which a means of identification recognized in accordance with the eIDAS Regulation is used to verify the information that will be included in a DID document (i.e., using a special kind of oracle that verifies the eIDAS eID to pass the information to the DID creator).

eIDAS Interoperability regulation defines minimum data sets for natural persons and for legal persons.

For natural persons, the data set includes:current family name(s), current first name(s), date of birth, a unique identifier constructed by the sending Member State in accordance with the technical specifications for the purposes of cross-border identification and which is as persistent as possible in time, first name(s) and family name(s) at birth (optional), place of birth (optional), current address (optional) and gender (optional).

For legal persons, the data set includes:current legal name; a unique identifier constructed by the sending Member State in accordance with the technical specifications for the purposes of cross-border identification and which is as persistent as possible in time, current address (optional), VAT registration number (optional), tax reference number (optional), the identifier related to Article 3(1) of Directive 2009/101/EC of the European Parliament and of the Council (optional), Legal Entity Identifier (LEI) referred to in Commission Implementing Regulation (EU) No 1247/2012 (optional), Economic Operator Registration and Identification (EORI) referred to in Commission Implementing Regulation (EU) No 1352/2013 (optional), and excise number provided in Article 2(12) of Council Regulation (EC) No 389/2012 (optional).

The main advantage of using this approach is that the DID inherits the level of assurance of the eIDAS electronic identification means, allowing a person with this kind of eID, which is centralized, to get DIDs and leveraging their use in the space of decentralized transactions, gaining real privacy.

### Using SSI as an eIDAS identification means

Although electronic identification under eIDAS Regulation is today clearly aligned with SAML-based infraestructures (see Opinion No. 2/2016 of the Cooperation Network on version 1.1 of the eIDAS Technical specifications, available at https://ec.europa.eu/cefdigital/wiki/pages/viewpage.action?pageId=37750723 and eIDAS eID Profile, available   https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/eIDAS+Profile), nothing in the eIDAS or its implementing acts should prevent the usage of a SSI system as an electronic identification means.

Thus, the second use case considers a DID as an eIDAS compliant electronic identification means, enabling - at least - transactions with Public Sector authorities and Public Administrations and, if so decided by the DID creator, also with private sector entities. 

For this purpose, the following challenges are considered:

- The alignment of the SSI/DID/VC vocabulary with the eIDAS legal concepts.
- Consideration of some specific DID creators as eIDAS issuers and nodes.
- Drafting of a SSI eIDAS profile, which could be approved by the eIDAS Cooperation Network.

