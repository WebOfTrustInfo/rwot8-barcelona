# Peer-Star Identity Manager

*Authors*: André Cruz, João Santos, Pedro Teixeira

*Keywords*: [DIDs](https://w3c-ccg.github.io/did-spec/), [Verifiable Credentials](https://www.w3.org/TR/verifiable-claims-data-model), [DID Delegates & Devices](https://w3c-ccg.github.io/did-spec/#authentication)

## Introduction

The benefits of using emerging p2p technologies, which enable truly decentralized applications to existing, are obvious to those well versed in the topic. However, in order to attain massive user adoption, these decentralized applications need to be better than the incumbents in almost every aspect -- usability being the one where they usually lack the most.
The Peer Start Identity Manager is a decentralized identity and authentication application, built on top of the Peer Star stack, with a strong emphasis on user experience.
On one hand, the experience for end-users should be intuitive, simple and familiar. Ideally, users should have little contact with private keys and most of the cryptographic operations should happen behind the scenes. On the other hand, developers building DApps should have an easy way to authenticate users.

## The Identity Manager

The IdentityManager is a web-page hosted on IPFS and reachable via a specific URL, e.g.: https://peer-identity.io. The application will work completely offline thanks to the installation of a ServiceWorker. It packages emerging [Standards & foundations](#standards--foundations) into an intuitive and easy to use interface for end-users. By using the application, users will be able to create identities on several DID methods, import identities created on other devices, manage Verifiable Claims of identities, authenticate to dApps (sessions).

Because it runs on its own domain, it provides a sandboxed environment, where access to functionality and data is completely controlled. More specifically, all interactions made with the IdentityManager will be made via [`postMessage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) where control and data segmentation is made via the messages' origin.

All private keys, such as Device Private Keys and Session Private Keys, will be safely stored in the IdentityManager local storage. Applications must interact with the IdentityManager to sign or decypher payload that uses such keys.

Moreover, any meaningful event on the IdentityManager, such as the removal of an Identity, will be broadcasted to interested parties. This allows applications to immediately react to certain events by subscribing to them on the IdentityManager.

Among others, the most important advantages of this solution are:

- Embraces several DID methods instead of being tied to a specific method.
- Uses DID best practices, such as using delegate keys to associated devices.
- Doesn't require any extensions, scanning of QR codes, or any other unfriendly processes for daily use.
- Acts like a "server" in the sense that sensitive information may be safely stored in it. Many DID methods require a secret for certain actions, e.g.: uPort requires an app secret to request normal and verified credentials.
- Has wide support among devices. If we make it a Progressive Web App (PWA), users may install the application in the OS itself, further enhancing the user experience. Later on, we can develop native mobile apps to support OS's that don't yet allow PWAs to be installed natively.
- Allows the user to choose between several identities when authenticating, useful for people that manage companies, organizations or similar.

### Managing identities

Users will be able to create identities using their preferred DID method or associate existing ones, thus creating Device Keys. All the Device Private Keys will be locked to improve security.  Even if a device gets stolen, the robber won't be able to use most features without unlocking the Device Private Key as all the information stored locally will be encrypted with the Device Public Key. This gives time for the owner of the Identity to revoke the compromised device in the IdentityManager of another device. Because the identity was linked to this device at setup time, and depending on the DID method, profile information and verifiable claims might become stale. For this reason, users will be able to sync up with their identity to update any stale data.

### Managing Verifiable Claims

Users will be able to add claims to their identities. Initially, we will focus on adding self-signed claims linked to some of the most popular social networks. The process of adding those claims (and proofs) will work similarly to [Keybase](https://keybase.io/) in the sense that users will be guided throughout the process. The exact way in how the claims will be stored is dependent on the DID method. For instance, uPort already provides a way to store these claims via attestations.

### Authentication on applications

Peer-Star applications will use the IdentityManagerClient to manage the user's session by tapping into the app's local storage to access the session keys.

When the application requests the IdentityManagerClient to authenticate the user, a popup pointing to the IdentityManager authenticate screen is open. In this screen, the user is asked to choose an identity and to disclose some information, such as its name, its photo and a set of claims & proofs. If the user consented to the disclosure of this information and entered the Device Private Key passphrase correctly, a new session for this application will be created and stored. The session data, including the Session Public Key and its signature signed by the Device Private Key, is sent back to the application.  Applications might choose the TTL of a session depending on the degree of security they want to have.

### Signing artifacts and verifying signatures on applications

Applications may want to sign artifacts, such as regular data or Ephemeral Keys. This will be possible in two different ways. Sign with the Session Private Key or sign with the Device Private Key.

The first method is less intrusive and happens transparently to the user, but is less secure. More specifically, a robber who stole a device may still sign Ephemeral Keys with the Session Private Key as long as a session is valid (not expired). Relying parties will still see those signatures as valid until the DID owner revokes the stolen device. The second method provides more security as the user is prompted for the Device Private Key passphrase, but it's more intrusive. The interaction is similar to the Authentication process, where a popup pointing to the sign screen gets open. The user either allows or denies the signing and the result gets back into the application. Please note that the passphrase might be stored in memory in the IdentityManager during a certain amount of time, which in turn makes this process less intrusive for subsequent signings.

Any party might verify the authenticity and authorship of artifacts signed by other parties' session or device public keys. There will be functions offered by the IdentityManagerClient to verify signatures using the processes described above.

### Managing application sessions

Users will be able to revoke any session listed on the identity's Authenticated Session list at any time. Revoking a session will essentially delete the application session from the IdentityManager local storage.
Additionally, each session has a TTL that limits its lifespan and states when they expire. Expired sessions are automatically revoked. Applications will be unable to sign artifacts or decypher payload if their sessions are revoked or non-existent. This is guaranteed by declining such requests made by applications to the IdentityManager.

### Revoking a device

Users must be able to revoke a device associated with an identity. To do so, users may see the list of devices associated with an identity and revoke any device of that list, including the device from which they are interacting. This will require interacting with the DID method (Master Private Key) to publish the device being revoked. If a device becomes aware that it was revoked, it will trigger a wipe-out process where all the identity data stored locally will be deleted, including the Device Key and Authenticated Sessions.
