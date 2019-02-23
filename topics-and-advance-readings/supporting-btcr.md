# Querying Bitcoin blockchain for BTCR support

Kulpreet Singh, [kulpreet@opdup.com](mailto:kupreet@opdup.com)

## Abstract

I describe the progress made during the
[BTCR hackathon](https://github.com/w3c-ccg/did-hackathon-2018/blob/master/README.md)
towards providing a community service for querying the bitcoin
blockchain as a means to support clients building BTCR DID resolvers
using the BTCR DID method.

BTCR DID method enables bitcoin users to generate DIDs corresponding
to their bitcoin key pairs. By generating DIDs using bitcoin key pairs
we can leverage the high level of guarantees provided by the bitcoin
blockchain against manipulation of published data.

I provide a brief overview of the BTCR DID resolution method, point to
the problem of querying third party services and how we provided our
own community service as part of a hackathon in 2018.

## BTCR Overview 

[Decentralized Identifiers (DIDs)](https://w3c-ccg.github.io/did-spec/)
are a new type of identifier for verifiable, "self-sovereign" digital
identity. DIDs are fully under the control of the DID subject,
independent from any centralized registry, identity provider, or
certificate authority. The
[BTCR DID method](https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/btcr-resolver.md)
specifies how the transaction output identified above can be used to
generate a DID Document matching the key pair used to sign that
transaction.

BTCR DID method uses a reference to a transaction provided by a user
who wants to generate a BTCR DID. This reference to a transaction
includes the type of the network (testnet or mainnet), the height of
the block that contains the transaction, the index of the transaction
in the block and finally the index of the output. See
[Extended TxRef](https://github.com/veleslavs/bips/blob/c83837536d6629f754ce5a88bbe245e0a615e76e/bip-XXXX-Bech32_Encoded_Transaction_Position_References.mediawiki)
for details on how the reference to a transaction can be encoded and
easily exchanged between humans.

The BTCR DID method requires that we check if the transaction output
specified has been spent or not. Depending on the spend status the DID
method generates a DID pointing to the public key found in the
transaction output or follows the spends to see if a future
transaction output can be be found that has not been spent - this
enables key rotation in the BTCR DID method.

The challenge facing BTCR DID resolution is the ability to query the
bitcoin blockchain for any transactions referencing a given
address. In our case, it is the address in the P2PKH script referenced
by the user transaction. The bitcoin reference client, bitcoind, does
not maintain an address history and therefore as a community the BTCR
developers were dependent on third party block explorers.

## Using Block Explorers

Third party block explorers run their own databases indexing
transactions by addresses referenced in those transactions. This
allowed the BTCR developer community to quickly develop some MVPs and
demo them to the larger community. However, third party block
explorers are not a long term solution because of concerns about
privacy leaks and more immediately the rate limits imposed by them.

## Community Run Query Endpoint

To get past the problems of of using third part block explorers and
also to validate potential implementation solutions we deployed a
[BTCD](https://github.com/btcsuite/btcd) instance that provides an
endpoint to query all transactions referencing and address. We also
provided a very simple API to query all transactions referencing an
address.

The service is built in Go and invokes the BTCD API endpoints. It
accept TxRefs as inputs and responds with a JSON array of transactions
referencing the address. For example, the URL
[https://btcr-service.opdup.com/txref/txtest1:xz35-jzv2-qqs2-9wjt/resolve?spendsOnly=false](https://btcr-service.opdup.com/txref/txtest1:xz35-jzv2-qqs2-9wjt/resolve?spendsOnly=false)
queries the service for TxRef xz35-jzv2-qqs2-9wjt on the testnet
network and responds with all transactions referencing that address.

With access to the list of transactions, BTCR developers can continue
to experiment and further develop the BTCR DID method
specification. The source code for the service is available on the
GitHub repo
[https://github.com/kulpreet/btcr-service](https://github.com/kulpreet/btcr-service). The
README on the repo describes the various API endpoints and how to
deploy the service.

## Current and Future Work

As a proof of concept we are using BTCR Service to build a BTCR
Android Wallet. The BTCR Android Wallet includes a Java client library
for the BTCR Service API endpoints. For now, the wallet accepts a
TxRef and shows the public key that can be used to generate an
implicit DID. Our plan is to support DID generation using key pairs
managed by the Android wallet. The wallet source code is available at
[https://github.com/opdup/btcr-android-wallet](https://github.com/opdup/btcr-android-wallet).

As the BTCR DID method spec evolves, we also plan to continue adding
API endpoints that will be helpful to the community.


