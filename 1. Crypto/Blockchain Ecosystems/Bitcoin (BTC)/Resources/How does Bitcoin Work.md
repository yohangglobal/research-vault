---
date_created: 2023-04-05
tags: guide, bitcoin, videos
category: summary
topics: bitcoin
---
# Explanation on how Bitcoin works
#guide #bitcoin #videos 

Source: https://www.youtube.com/watch?v=bBC-nXj3Ng4

Questions to ask for speculators:
What does it mean to *have* a bitcoin?

This video walks through why crypto is invented, the purpose of ledgers, and why Bitcoin was created.
Explained as Ledger - Trust + Cryptography = Cryptocurrency

This provides a direct description of what the computers are doing when sending transactions and their digital signatures.

The comparison here is that Bitcoin and $ has their own user facing and underlying systems.

|                   | Bitcoin          | Fiat System    |
| ----------------- | ---------------- | -------------- |
| User-facing       | Mobile/Internet  | Credit Cards   |
| Underlying system | Bitcoin protocol | Banking system |

The backbone of Bitcoin is not a centralized party like a bank but a network of trustless verification using the math behind cryptography. 

## Ledgers

The important foundation to understand is the concept of sending money to your friends and how to verify what has or hasn't been sent or received.

This is where a ledger, or an identifiable record of transactions, can store what payments have been made or will be made in the future.

This ledger would be public to your friends and can be accessed by any party.

Protocol:
- anyone can add lines to the ledger
- end of month will have everyone settle up.

The issue here is that approving transactions would be a necessity since other people could falsify data on the ledger.

The initial part of cryptography here consists of digital signatures. These signatures allow for full verification and approval of a transaction without letting a bad actor copy the signature.

This should be infeasible for anyone to forge this signature.

The way this works is by creating a Private Key and Public Key pair. These are an identifiable set of digits that the user will 

### Secret key and Public key

A digital signature is much stronger, producing a signature will have its own message and sign to have.

This is explained as two separate functions:
Sign(Message, sk) = Signature
Verify(Message, Signature, pk) = T/F

The signature is a 256 bit Signature, which will take an insane amount of computing power to break.

Only way someone could produce signatures is with the secret key and public key pair.

Each line on the ledger will need their own identifiers, think of tx hashes.

Protocol now looks like:
- Only signed transactions are valid

## Ledger is the currency

This is still using an honor system for ppl to follow thru with the settlement.

The real reason for settling is to honor this system.

The goal is to make sure that people are not overspending.

Verifying transactions means you must know what previous transactions were prior to confirming them.

The ledger is supposed to be something different from this system.

The video then dives into Ledger Dollars, as this is their own currency maintained by the Ledger.

There would still be exchange rates for this currency, however the point is that the currency can stand on its own.

The currency is the transaction history.

## Decentralization

Right now the Ledger Dollars are centralized, while bitcoin, ethereum is decentralized.

So far, Ledger Dollars are in a central place.
The point is that these should not be controlled by one person, and instead represented by people on the network itself.

To remove this layer of trust, a blockchain allows for each individual to own and keep track of their own ledger.

The speaker explains that the system for agreeing on the right ledger needs to make sure/verify that each transaction is confirmed and verified by everyone else.

> Can you come up with a protocol to accept or reject transactions and in what order so that you can feel confident that other ledger owners have the same ledger.

A blockchain chooses to trust the ledger that has the most computational work within it. It does so through cryptographic hash functions, or a mathematical process for scrambling and compressing data into a shortened hash.

The point being that if you use computational work to verify these transactions, this means that it becomes computationally infeasible to exploit these functions.

## Hash functions

This is a cool idea and is important for understanding the foundations of bitcoin and other blockchains.

The hash function itself is called SHA256 and the function would look like this:
- SHA256("Hello, World") = 10101001011000110101 (This is the actual hash)
- If you change the input (file message), this changes the entire hash itself.
- The benefit here is that this hash is infeasible to reverse.
	- Downside for this is 2^256 takes a lot of computational power to reverse engineer.

Modern security depends on SHA-256 with RSA Encryption.

## Proof of Work and Blockchains

This example takes a list of transactions and then assigns it a certain number. SHA256 will force the person to verify

4

### Distributed ledger

Everyone is broadcasting transactions but they need to be able to trust the ledger with the most work put into it.

Bitcoin splits these into blocks with their own specific hash. Transactions are only valid when they are signed by the user.

(16:47) In the same way, a block is only valid when it has a Proof of Work. This is comprised of the hash from the SHA256 bit encryption.

So your hash u32fd748fd8e332gd will be encrypted via SHA256 and spit out 00000001010101010101

A block has to have the hash of a previous block in its header. If you swap order of two blocks, this changes the block that comes after it and their respective hashes. 

This means that you would have to redo all of the work to get to the right 256 bit hash. The point is that each block must start with the correct hash and if this isn't the case, then each block will need a new proof of work to verify them.

Instead of ledgers, we call this Block Chains.

Now anyone can become a block creator. They listen for transactions, collect them into a block, and then do proof of work to find a special number that provides the correct hash for that block.

The next step here is the reward for these block creators (or miners), which is paid out as the miner completes the proof of work.

This isn't paid by anyone and does not need to be signed. Each block will introduce new bitcoins into the economy.

**Miner Roles:**
Listen for txs
Create blocks
Broadcast blocks
Rewarded with new money

This is a race for the block reward, who can complete the proof of work the fastest.

### Block length

Each of these instances will depend on the blockchain that has the most computational work. The purpose of this is to fully remove the trust of a central authority and instead rely on this level of computational work. 

## Double Spending

This is an explanation of how to fool someone on the blockchain. 












