# Identity Manager Specification

*NOTE: This is a draft, we will be updating the document during the next days*

By Adin Schmahmann &lt;adin@protocol.ai&gt;, Protocol Labs; André Cruz &lt;andre@moxy.studio&gt;, MOXY; and Pedro Teixeira, Protocol Labs &lt;pedro@protocol.ai&gt;, Protocol Labs.

The IDM (Identity Manager) project itself is open-source, meaning that anyone should be able to look at the specification and implement it in their language of choice. This also enables implementing different user-interfaces. There will be a reference implementation of this spec written in JavaScript as well as a web based user-interface.

The goals of the workshop are to present the spec, gather feedback and discuss some unresolved topics.

Index:

- [IDM Client](#idm-client)
- [IDM Wallet](#idm-wallet)
- [IDM Bridge](#idm-bridge)
- [Data Types](#data-types)
- [To Discuss](#to-discuss)


## IDM Client

```js
// authenticate, unauthenticate & obtain current session
.authenticate({ Array<CredentialScope> scopes } options): Promise<Session>
.unauthenticate(): Promise
.getSession(): Promise<Session>
.onSessionChange((Session session) => {}): Function (to remove the listener)

// signing and verifying
.sign(ArrayBuffer data, { IdentifiedSignatureKeyType keyType = session, String previewUrl } options): Promise<IdentifiedSignature>
.verifySignature(ArrayBuffer data, IdentifiedSignature signature): Promise<Boolean>
```

--------------------------

## IDM Wallet

Main scopes:

```js
.locker
.storage
.did
.identities
.session
```

### .locker

```js
.locker.unlock(LockerType type, (Any challenge) => Any solution): Promise
.locker.lock()
.locker.isLocked(): Boolean
.locker.onLockedChange((Boolean locked) => {}): Function (to remove the listener)
.locker.getPublicKey(): PublicKey
.locker.getPrivateKey(): PrivateKey
.locker.locks.list(): Promise<Array<LockerType>>
.locker.locks.set(LockerType type, Any solutions)
.locker.locks.unset(LockerType type)

```

TODO:
- refreshLock to keep unlocked because we did a op
- where the unlocking time is defined


### .storage

```js
.storage.get(String<String>|String key, { PrivateKey decryptKey } options): Promise<Object<String,Any>>
.storage.set(Object<String, Any>, { Number maxAge, PublicKey encryptKey } options): Promise
.storage.remove(String<String>|String key): Promise
.storage.clear(): Promise
.storage.getBytesInUse([String<String>|String key]): Promise<Number>
```

### .did

```js
.did.resolve(String did): Pending<DidDocument>
.did.create(String didMethod, Object parameters): Promise<{ String did, KeyPair deviceKeyPair, [KeyPair masterKeyPair] }>
.did.import(String did, Object parameters): Promise<{ String did, KeyPair deviceKeyPair> }>
.did.verifySignature(IdentifiedSignature signature): Pending<Boolean>
.did.methods.list(DIDMethodPurpose purpose)
.did.methods.isSupported(String didMethod, DIDMethodPurpose purpose)
```

TODO: add did auth


### .identities

```
.identities.list(): Promise<Array<Identity>>
.identities.add(String did, KeyPair deviceKeyPair, [KeyPair masterKeyPair]): Promise<Identity>
.identities.get(String did): Identity
.identities.remove(String did): Promise

```

Note: Identity is actually a instance of a "class" and not a data-structure


#### identity


##### identity.credentials

```js
identity.credentials.list(): Array<Credential>
identity.credentials.listByScope(CredentialScope scope): Array<Credential>
identity.credentials.add(Credential credential, [CredentialScope scope])
identity.credentials.remove(String credentialId)
identity.credentials.onChange((Array<Credentials> credentials) => {}) : Function (to remove the listener)
```

##### identity.devices

```js
identity.devices.list(): Array<Device>
identity.devices.add(Device device, PrivateKey masterKey)
identity.devices.revoke(PublicKey deviceKey, PrivateKey masterKey)
identity.devices.update(PublicKey deviceKey, Device device)
identity.devices.onChange((Array<Device> devices) => {}) : Function (to remove the listener)
```

##### identity.applications

```js
identity.apps.list(): Array<App>
identity.apps.add(App app)
identity.apps.revoke(String appId)
identity.apps.getUsage(String appId): AppUsage
identity.apps.onChange((Array<App>) => {}) : Function (to remove the listener)
```

##### identity.replication

```
identity.replication.getStatus(): ReplicationStatus
identity.replication.start(): Promise
identity.replication.stop(): Promise
```

The IDM reference implementation will use [peer-base](https://github.com/peer-base/peer-base). The replication protocol will later be defined as part of the peer-base project itself.



### .session

```js
.session.create(App app, String did, { Array<CredentialScope> scopes, Number maxAge } options): Promise<Session>
.session.destroy(String sessionId): Promise
.session.isValid(String sessionId): Session
.session.getById(String sessionId): Session
.session.sign(sessionId, ArrayBuffer data, { SignatureKeyType keyType = 'session', String previewUrl } options): Promise<IdentifiedSignature>
```

--------------------------

## IDM Bridge

The way the IDM Client and the IDM Wallet communicate depends on the environment they are running. Also, they should be interoperable even if they are implemented in different languages. The IDM Bridge ensures these two requirements.

Here's a few environment scenarios:

- The DApp and the IDM Wallet are running in the same browser
- The DApp is a web app running on Chrome and IDM Wallet is an electron app on the same computer
- The DApp is a mobile app and IDM wallet is an electron app on a computer

TODO: This is complex, discuss this

--------------------------

## Data Types

```js
App { String id, String name, String homepageUrl, Array<Icon> icons }
AppUsage { Number interactionsCount, String addedAt, String lastUsedAt }
ChainedKey { PublicKey key, ChainedKey parent, String (multisig?) parentSignature }
Credential (https://github.com/w3c/vc-data-model)
CredentialScope enum(details, social)
DIDMethodPurpose enum(resolve, create, import)
DIDDocument (https://w3c-ccg.github.io/did-spec/#simple-examples)
DIDMethodInfo { String name, String homepageUrl, String description, Array<Icon> icons }
Device { PublicKey key, String name, DeviceType type }
DeviceType enum(laptop, desktop, phone, tablet)
KeyPair { PublicKey publicKey, PrivateKey privateKey }
Icon { Number width, Number height, String type, String url }
IdentifiedSignature { String did, String date, ChainedKey chainedKey, String (multisig?) signature }
IdentifiedSignatureKeyType enum(device, session)
Identity { String did, IdentityType type, Schema.org details }
IdentityType enum(person, organization, other)
LockerType enum(passphrase, fingerprint, faceid)
PrivateKey String (multikey?)
PublicKey String (multikey?)
ReplicationConsistency { incoming: Array<String>, outgoing: Array<String> }
ReplicationStage enum(inactive, starting, active, stopping)
ReplicationStatus { ReplicationStage stage, ReplicationConsistency consistency }
Session { String id, String appId, String createdAt, String expiresAt, Identity identity, Object<CredentialScope, Array<Credential>> credentials }
```

--------------------------

## To Discuss

- IDM Bridge
- multikey
- multisignature
