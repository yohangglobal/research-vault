# Passphrase and BIP 32 Code
#bitcoin #tools 

Source:
https://iancoleman.io/bip39/#english

I found this pretty interesting since each blockchain and its relevant phrases, public and private keys can be derived using the generator.

They explain that the mnemonic generator uses a [cryptographically secure random number generator](https://developer.mozilla.org/en-US/docs/Web/API/RandomSource/getRandomValues). Referring back to this reveals that each instance a key is created, the user is able to derive multiple public/private keys (wallet addresses as people normally recognize). 

From here, the page explains how to apply this same method to other chains. In this example, BIP 44 provides an expansion of BIP 32 and goes into depth about how to create the same cryptographic proofs for multi accounts and multiple tokens.
https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki

The main focus of this is based on BIP 32 and explains the system for deriving a tree of keypairs from a single seed phrase as well as how to build a wallet structure on top of this tree. This process can be applied to multiple clients and does not have to have the ability to make transactions or hold tokens.
https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki

What I found most interesting from this is the ability to define certain functions that derive child keys from a parent key. Each section of this explains key terms that users should be aware of, such as "bits" and "entropy". When creating this process, the function is used to extend the private and public keys with an extra 256 bits of entropy. From here, the chain code is identical for the creation of relative private/public keys.

One of the main things you can keep in mind during this is that the majority of these factors center around random number generators and how to securely generate said numbers. Beyond this, RNG acts as a foundation for the consequential BIPs that have become known as part of a crypto users daily interactions.