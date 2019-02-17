Universal ID Framework
======================

By Dr. Shigeya Suzuki, Keio University

Submitted to Rebooting Web of Trust 8

January 31, 2019, Tokyo Japan

 
Problem
-------

Suppose we configure an access control list for a server software using some certificate-based client authentication over a secure connection. We need to configure a list of identity references such as the certificate's subjects or issuers. To describe the identity reference with PKI, we use X.500 Distinguished Name style strings.

Suppose we want to add support for DID in a client authentication server code like the above. We need to modify the access control code of the server to add support for DID resolution. If we have a DID resolver library to implement this, it is not a difficult task. However, if we want broader deployment of DID, we need to develop a better way to add support for DID to help application developers.

If we look at how to treat identity reference in an application, it is natural to develop a standard abstract data type which may store a different kind of identity references.


Key Idea
--------

One of the ways to support references for multiple ID scheme everywhere is developing a general Universal ID Reference scheme, which covers not only the references to DID but also Distinguish Name-based scheme or possibly others.

It is possible to develop a Universal ID framework consists of standard documents, open source libraries, and other necessary components to help using Universal ID-based system.


Possible outcomes
-----------------
If the Universal ID based framework is ready and the traditional single-framework component is replaced with  mutiple-framework capable component, it will be able to seamlessly support both DID and PKI based trust system.

This change effectively enables the use of DIDs in various places.


Relationship with URI
---------------------

Designing Universal ID reference syntax based on URI is natural. However, restrict the syntax of the Universal ID within the URI scheme or relaxing the syntax require detailed use case analysis.
