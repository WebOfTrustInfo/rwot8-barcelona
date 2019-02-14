# Bringing the Dependencies of a BTCR Wallet to the Swift Ecosystem

## [Wolf McNally](https://wolfmcnally.com/) for [Blockchain Commons](https://github.com/blockchaincommons/)

### The Swift Ecosystem

[Swift](https://en.wikipedia.org/wiki/Swift_%28programming_language%29) is a programming language introduced by Apple in 2014 as the new official programming language for writing iOS and macOS apps. In 2015 Apple released Swift under the [Apache open source license](https://en.wikipedia.org/wiki/Apache_License) and also seeded a build of Swift for Linux. A growing community of developers headquartered at [Swift.org](https://swift.org/) are extending the language in various ways, including Google's high-performance numerical computation library [Swift for TensorFlow](https://www.tensorflow.org/swift) and server-side application frameworks such as [Vapor](https://vapor.codes/). IBM has launched an [initiative](https://developer.ibm.com/blogs/2019/01/24/open-source-ibm-kitura-swift/) to promote server-side Swift, including [Kitura](https://www.kitura.io/), its own Swift server framework. Swift has a number of traits that make it attractive for use on the desktop, on mobile devices and cloud services. Swift is a modern, multi-paradigm language designed to be [safe, fast, and expressive](https://swift.org/about/). In this document, the phrase "Apple platforms" refers collectively to iOS, macOS, and tvOS. The use of Swift across Apple platforms and Linux is what this document refers to as the *Swift ecosystem*.

### Bridging BTCR Dependencies to Swift

While all the code to implement something as complex as a [DID resolver](https://w3c-ccg.github.io/did-resolution/) or [registrar](https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/topics-and-advance-readings/Universal-DID-Operations.md) could be written entirely in Swift, it makes sense to leverage code already written in other languages, and use Swift as a top-level language used to tie heterogenous modules into a unified application, whether it be a mobile application or server. This document surveys programing languages and technologies of interest, discusses issues of interoperating with Swift, and lists software packages of note. 

The author invites additions and clarifications from the reader.

---

### Programming Languages

#### C

[C](https://en.wikipedia.org/wiki/C_%28programming_language%29) is the grandfather of most modern programming languages, and is still valued for its simplicity, speed, and interoperability with other languages.

The whole Swift ecosystem can call C functions directly..

Packages of interest written in C include:

* [Libsecp256k1](https://github.com/bitcoin-core/secp256k1)— Optimized C library for EC operations on curve secp256k1.
	* Used by: Bitcoin Core and Libbitcoin
* [Nettle](https://git.lysator.liu.se/nettle/nettle)— A low-level cryptographic library that is designed to fit easily in more or less any context.
	* Used by: Bread Wallet
* [Breadwallet Core](https://github.com/breadwallet/breadwallet-core)— An implementation of SPV.
	* Used by: Bread Wallet

#### C++

[C++](https://en.wikipedia.org/wiki/C%2B%2B) is an object-oriented dialect of C, and is one of the main workhorse languages in use today.

Swift cannot call C++ directly, but we can get around this by writing a C-based shim— Swift calls the C API and the C API calls C++. This technique works under the entire Swift ecosystem.

Packages of interest written in C++ include:

* [Libbitcoin](https://github.com/libbitcoin/libbitcoin-system)— Libbitcoin is a multipurpose bitcoin library targeted towards high end use. An ideal backend to build fast implementations on top: mobile apps, desktop clients and server API's. The library places a heavy focus around asychronicity, speed and availability.
	* Blockchain Commons have already released a [framework for bridging from Libbitcoin to Swift](https://github.com/BlockchainCommons/iOS-Bitcoin) written by the author.
* [Bitcoin Core](https://bitcoincore.org/)— A free and open-source application that serves as a bitcoin node and provides a bitcoin wallet which fully verifies payments. It is considered to be bitcoin's reference implementation.
* [Boost](https://www.boost.org/)— A set of libraries that provide support for tasks and structures such as linear algebra, pseudorandom number generation, multithreading, image processing, regular expressions, and unit testing. It contains over eighty individual libraries.
	* Used by Libbitcoin.
* [V8](https://v8.dev/)— Google’s open source high-performance JavaScript and WebAssembly engine. It is used in Chrome and in Node.js, among others. There are already [available bridges](https://github.com/tris-foundation/javascript/tree/v8) from Swift to V8.

#### Javascript

[JavaScript](https://en.wikipedia.org/wiki/JavaScript) is a high-level, interpreted programming language. It is a language that is also characterized as dynamic, weakly typed, prototype-based and multi-paradigm. Alongside HTML and CSS, JavaScript is one of the three core technologies of the World Wide Web.

Apple platforms include [JavaScriptCore](https://developer.apple.com/documentation/javascriptcore), a built-in framework used by the WebKit engine in the Safari Browser, but also made available directly to Apple platforms developers for evaluating JavaScript programs. On Linux, Swift applications can integrate Javascript by using an execution engine like `V8`.

Packages of interest written in JavaScript include:

* [jsonld.js](https://github.com/tris-foundation/javascript/tree/v8)— An implementation of the JSON-LD specification in JavaScript.
* [jsonld-signatures](https://github.com/digitalbazaar/jsonld-signatures)— An implementation of the Linked Data Signatures specification for JSON-LD.
* [Webcoin](https://github.com/mappum/webcoin)— A Bitcoin SPV client that works in Node.js and the browser.

#### Go

[Go](https://golang.org/) (AKA Golang) is a statically typed, compiled programming language designed at Google.

Swift running under iOS can bridge to Go using [Go Mobile](https://github.com/golang/go/wiki/Mobile). Under Linux, Go modules can be [compiled to export C functions](https://medium.com/learning-the-go-programming-language/calling-go-functions-from-other-languages-4c7d8bcc69bf) that can be called by Swift.

Packages of interest written in Go include:

[btcd](https://github.com/btcsuite/btcd/blob/master/docs/README.md)— A full node bitcoin implementation. One key difference between btcd and Bitcoin Core is that btcd does *NOT* include wallet functionality and this was a very intentional design decision. That functionality is provided by the btcwallet project.
[btcwallet](https://github.com/btcsuite/btcwallet/blob/master/README.md)— A daemon handling bitcoin wallet functionality for a single user.
[spvwallet](https://github.com/OpenBazaar/spvwallet)— Lightweight p2p SPV wallet and library in Go. It connects directly to the bitcoin p2p network to fetch headers, merkle blocks, and transactions.

---

### Other Technologies

#### JSON

JSON, as specified in  [RFC7159](http://tools.ietf.org/html/rfc7159), is a simple data description language for representing objects on the Web.

The Swift [Foundation framework](https://developer.apple.com/documentation/foundation), available on Apple platforms and Linux, includes APIs for working with JSON:

* The [`Codable`](https://developer.apple.com/documentation/swift/codable) protocol, which works in concert with the `JSONEncoder` and `JSONDecoder` classes to serialize statically-typed data structures.
* The [`JSONSerialization`](https://developer.apple.com/documentation/foundation/jsonserialization) class, which can be used to structure and navigate dynamic JSON objects.

#### JSON-LD

[JSON-LD](https://json-ld.org/) is an extension of JSON designed as a light-weight syntax that can be used to express Linked Data, and is specifically used in the [Decentralized Identifiers (DID) specification](https://w3c-ccg.github.io/did-spec/#base-specifications) for constructing [DID Documents](https://w3c-ccg.github.io/did-spec/#terminology). A JSON-LD implementation will usually provide the functionality described in [JSON-LD 1.1 Processing Algorithms and API](https://json-ld.org/spec/ED/json-ld-api/20180215/).

Swift can integrate JSON-LD by bridging to the `jsonld.js` package listed above.

#### DID Document Hosting

The process of resolving, creating, updating, or revoking a DID implies that the target DID Document itself is stored somewhere under the control of its owner. A DID wallet will need to be able to store, retrieve, and update DID documents via a hosting service or protocol.

Services and protocols of note include:

* [GitHub](https://github.com/)— A web-based hosting service for version control using [Git](https://git-scm.com/). It is mostly used for computer code, but can host data of any type. It offers all of the distributed version control and source code management (SCM) functionality of Git as well as adding its own features. 
* [DropBox](https://en.wikipedia.org/wiki/Dropbox_%28service%29)— A file hosting service that offers cloud storage, file synchronization, personal cloud, and client software.
* [Amazon S3](https://aws.amazon.com/s3/)— A "simple storage service" offered by Amazon Web Services (AWS) that provides object storage through a web service interface.
* [IPFS](https://ipfs.io/)— A protocol and network designed to create a [content-addressable](https://en.wikipedia.org/wiki/Content-addressable_storage), peer-to-peer method of storing and sharing hypermedia in a distributed file system. Users typically run an IPFS node that stores their own files, which are replicated upon demand to other IPFS nodes. Data placed into IPFS is public by default, and must be encrypted by the user if it is to remain controlled. Notably, once data is placed into IPFS, it needs to be considered [indelible](https://github.com/ipfs/faq/issues/9).
* [Storj](https://storj.io/)— A decentralized, distributed, encrypted file system. Storj data is end-to-end encrypted and can only be accessed by its owners by default, but Storj can also be used to [host public buckets](https://docs.storj.io/discuss/591a0836a3c9ec0f00ff074d) as a [CDN](https://en.wikipedia.org/wiki/Content_delivery_network).

#### Linked Data Signatures

[Linked Data Signatures](https://w3c-dvcg.github.io/ld-signatures/) describes a mechanism for ensuring the authenticity and integrity of Linked Data documents using digital signatures. It can be applied to Linked Data formats such as JSON-LD or RDF. This is how DID documents are signed.

Swift can integrate Linked Data Signatures by bridging to the `jsonld-signatures` package listed above.

#### REST

[REST](https://en.wikipedia.org/wiki/Representational_state_transfer) is acronym for *REpresentational State Transfer*. RESTful web services (RWS), provide interoperability between computer systems on the Internet.

The Swift ecosystem uses the Foundation [`URLSession`](https://developer.apple.com/documentation/foundation/urlsession) API to perform HTTP REST requests. Packages like [Alamofire](https://github.com/Alamofire/Alamofire) build more elegant conveniences on top of this.

REST APIs of note include:

* [GitHub API](https://developer.github.com/v3/)— Used to manage GitHub repositories and commit data such as DID Documents.
* [Dropbox API](https://www.dropbox.com/developers/documentation/http/overview)— The Dropbox API allows developers to work with files in Dropbox, including advanced functionality like sharing.
* [Amazon S3 API](https://docs.aws.amazon.com/s3/index.html#lang/en_us)— You can use Amazon S3 to store and retrieve any amount of data at any time, from anywhere on the web.
* [IPFS API](https://docs.ipfs.io/reference/api/http/)— When an IPFS node is running as a daemon, it exposes an HTTP API that allows you to control the node and run the same commands you can from the command line.
* [Storj API](https://storj.io/api.html)— Access the Storj network using a simple REST API.

#### SPV

Simple Payment Verification (SPV) is a technique described in [Satoshi Nakamoto’s paper](https://bitcoin.org/bitcoin.pdf). SPV allows a lightweight client (like a mobile app) to verify that a transaction is included in the Bitcoin blockchain, without downloading the entire blockchain. The SPV client only needs download the block headers directly from the Bitcoin network, which are much smaller than the full blocks. To verify that a transaction is in a block, a SPV client requests a proof of inclusion, in the form of a [Merkle branch](https://bitcoin.org/en/glossary/merkle-tree). SPV clients offer more security than web wallets, because they do not need to trust the servers with the information they send.

Packages that provide SPV services that can be called from Swift include:

* Webcoin (see above)
* BreadWallet Core (see above)
* spvwallet (see above)

#### BreadWallet

[Bread Wallet](https://brd.com/) (AKA BreadWallet or BRD) is an open source SPV wallet for iOS and Android that supports a variety of cryptocurrencies, including Bitcoin-based altcoins and Ethereum tokens. Bread Wallet is under active development, [hosted on GitHub](https://github.com/breadwallet/breadwallet-ios) and released under the MIT open source license. The iOS version has been [forked 228 times](https://github.com/breadwallet/breadwallet-ios/network/members) as of this writing. The iOS and Android versions of Bread Wallet share the same C-based BreadWallet Core (see above) to provide SPV functionality. The current iOS version is written in Swift.

One potential path for bringing a BTCR wallet to iOS would be to fork Bread Wallet and then extend it to include BTCR DID capabilities. Benefits of this approach include leveraging a mature and well-tested SPV codebase and shipping app. Possible drawbacks include dealing with possible (TBD) mismatches between the assumptions and requirements of Bread Wallet and those of a BTCR wallet. In any case, incorporating any of the necessary technologies listed above (e.g., JSON-LD) should be possible via the bridging techniques described.
