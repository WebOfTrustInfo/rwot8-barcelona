# Where's the UX?

By Alberto Elias <hi@albertoelias.me>

[DIDs](https://w3c-ccg.github.io/did-spec/) provide a safer way to identify any entity (person, organization, software..) against any other entity in such a way that each one is the real controller of their identity. DIDs are a global identifier with no centralized authority involved. They are really powerful but they're still not usable. 

I've been doing some user testing with both developers and non-technical folks and every single one of them has complained about the authentication and registration flows. We all agree that **this work is for nothing if people don't end up using them**. This community is definitely human-focused, but initial DID implementations haven't nailed the user experience yet.

We're battling usernames and passwords. It's not a strong contender in neither user experience nor security. It's a pain to have a password for hundreds of sites/apps and having to remember them and writing them in all your devices, specially on smartphones and XR HMDs (VR/AR Head Mounted Displays). This also means that people use bad passwords, and use the same one for every service. We end up being hacked all the time.

DIDs are more secure and censorship resistant than passwords, specially thanks to some amazing work by the community: [key recovery](https://github.com/hyperledger/indy-sdk/blob/master/doc/design/005-dkms/DKMS%20Design%20and%20Architecture%20V3.md), [social recovery](https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/draft-documents/key_recovery_uport.md#recover-identity-social-recovery), [capability based system](https://w3c-ccg.github.io/ocap-ld/) etc. But even if the identity systems we created were just as (in)secure as passwords but **user-owned**, that would already be a substantial step in the right direction. The thing is that, even though privacy awareness is on the raise, people still won't care enough about security and data ownership if the UX isn't at least as good as what they're currently using.

There is a lot to gain if get the UX right. The good thing is that **DID UX can be way better than passwords**.

First things first. Users MUST never see DIDs or interact with DID Documents directly. I know the community is already completely on board on this one, but I still see several implementations exposing this data quite visibly.

The first impression people will get is during the *registration* flow. It should only require a button press which would generate the necessary keys and store them in an encrypted storage. As long as the code that generates the keys is open source and happens locally so it's provable that it wasn't shared, we're good. The key store needs to be encrypted so that, for example, on the Web other loaded scripts can't access the keys.

The most common flow is *authentication*. It should also consist of 1-2 button presses depending if the service requires more information from the person. We can even provide the option to auto-login when the application doesn't require any extra information. This would be specially useful with virtual worlds as you could navigate from world to world with a persistent avatar.

Many see [Verified Claims](https://w3c.github.io/vc-data-model/) as the API for DIDs. They are a very powerful API that allow our DID based identities to tie in very nicely into all aspect of our lives.  They should also only require a button press to read or write data. The UI could be something similar to OAuth where your identity app shows you the request and you can *Confirm* or *Reject*.

A crucial aspect for DIDs is that **they need to be universal and work everywhere**, including new devices. XR is a whole new platform which opens the door to change. We can use it as an opportunity to do things differently. The XR market is expected to grow significantly in 2019 due to the launch of standalone HMDs that reduce the friction to use them greatly. These headsets aren't connected to anything, neither a PC nor a phone. The computer is incorporated into the HMD, and the only interface available is the VR one. Current DID implementations just don't work in XR as they require scanning a QR code or accessing a private key in another device that doesn't connect nicely to the headset.

DIDs are a really powerful way to identify any kind of entity. We still have a lot of things to figure out and we haven't covered all the security holes, but the underlying technology is already in a good place. **I believe it is time to start getting users**. For that we need to prioritise UX and DIDs allow us to offer a better UX than passwords, with increased security and giving people back their data. Let's ship it.