# CRUD and multi-device for IPID

Authors: Alberto &lt;hi@albertoelias.me&gt;, André Cruz &lt;andre@moxy.studio&gt;, [jonnycrunch](https://github.com/jonnycrunch), João Santos &lt;jrmsantos15@gmail.com&gt;

Outline:

- [Introduction](#introduction)
- [Problems](#problems)
  - [Publishing the DID-Document concurrently](publishing-the-did-document-concurrently)
  - [Security of the Master Key](security-of-the-master-key)


## Introduction

IPID is an implementation of the DIDs specification over the IPFS (Interplanetary File System) network using the IPNS (Interplanetary Name Service) cryptographic namespace resolution service.

When you create your DID using IPNS, you create a key-pair - the Master Key - that is used to publish your DID-Document, where the hash of the public key becomes your did, like so: `<did>:ipid:<base58(sha2(publicKey))>`. The DID-Documents being published actually use IPLD to reference the previous version of the DID-Document, meaning you can traverse the IPLD DAG to retrieve the history of DID-Documents.

While simple, this technique has a few downsides that will be explained in this paper. Moreover, a few candidate solutions will be presented to solve these issues.

## Problems

### Publishing the DID-Document concurrently

In the real-world, you use different devices everyday, from your phone, to your laptop, to your smart-watch. It's likely that you may want perform changes to the DID-Document in any of these devices, such as revoking a public key.

Because IPFS is not a blockchain, you can't rely solely on it to order and timestamp actions made on the DID-Document. If two different devices try to perform changes to a IPID DID-Document concurrently, it's likely that one will overwrite the other one, which is far from ideal.

By leveraging Conflict-free Replicated Data-Types (CRDTs), each device will be able to independently and concurrently update and reconcile the DID-Document without coordination between them. A CRDT can be modelled in a variety of ways, but we will on Merkle-DAGs because IPLD already supports it natively. As a result, two Merkle-DAG based CRDT types will be presented as possible solutions: state-based and op-based.

#### State-based Merkle-DAG

TODO:

#### OP-based Merkle-DAG

TODO:

NOTE: Mention improvements on IPNS

### Security of the Master Key

IPID DIDs are based on the hash of the Master Key, which is necessary to update the DID-Document. This means that the Master Key is in complete control of the DID-Document and can never be rotated. For these reasons, you should never list the Master Key it in the DID-Document to avoid having to ever rotate it. Moreover, it should be stored super securely. This is usually made in a non-friendly way, usually as a Paper Key.

But when you end up needing to manipulate the DID-Document, such as adding the public key of a new device or revoking the public key of another device, you need the Master-Key. But because it's stored safely, it's likely that you don't have it close to you, and you won't be able to finish what you trying to do.

### Split the Master Key into two layers

One possible solution would be to split the Master Key into two: Master Key Layer 1 (L1) and Master Key Layer 2 (Layer ). In this technique, the Master Key Layer 1 is used to publish a IPNS record that points to another IPNS record owned by the Master Key Layer 2, which in turn points to the DID-Document. This allows us to share the Master Key Layer 2 amongst devices, meaning each one them would be able to update the DID-Document. From a user-experience perspective, this is much better as you don't rely on using our Paper Key or other less pratical methods.

The Master Key Layer 1 must still be kept being super secure and would only be necessary whenever you need to revoke one of public keys of a device. Whenever that happens, a new Master Key Layer 2 (L2) is issued and the Master Key Layer 1 is used to update the IPNS record to point to that new key.


NOTE: Explore another keys
NOTE: Mention that you need your master key to keep republishing it



