---
date_created: 2023-03-26
tags: guide, bitcoin, readings
category: Crypto
subcategory: Blockchain Ecosystems
topics: bitcoin resources
---
# Reading the Bitcoin Whitepaper
#guide #bitcoin #readings

Source: Bitcoin: A Peer-to-peer Electronic Cash System
https://bitcoin.org/bitcoin.pdf

Author: Satoshi Nakamoto
www.bitcoin.org

## Abstract

>A purely peer-to-peer version of electronic cash would allow online payments to be sent directly from one party to another without going through a financial institution.  Digital signatures provide part of the solution, but the main benefits are lost if a trusted third party is still required to prevent double-spending. We propose a solution to the double-spending problem using a peer-to-peer network. The network timestamps transactions by hashing them into an ongoing chain of hash-based proof-of-work, forming a record that cannot be changed without redoing the proof-of-work.  The longest chain not only serves as proof of the sequence of events witnessed, but proof that it came from the largest pool of CPU power.  As long as a majority of CPU power is controlled by nodes that are not cooperating to attack the network, they'll generate the longest chain and outpace attackers.  The network itself requires minimal structure.  Messages are broadcast on a best effort basis, and nodes can leave and rejoin the network at will, accepting the longest proof-of-work chain as proof of what happened while they were gone.

## Introduction

>We propose a solution to the double-spending problem using a peer-to-peer distributed timestamp server to generate computational proof of the chronological order of transactions.

## Transactions

![](Pasted%20image%2020230326113049.png)

>For our purposes, the earliest transaction is the one that counts, so we don't care about later attempts to double-spend.  The only way to confirm the absence of a transaction is to be aware of all transactions.  In the mint based model, the mint was aware of all transactions and decided which arrived first.  To accomplish this without a trusted party, transactions must be publicly announced [1], and we need a system for participants to agree on a single history of the order in which they were received.  The payee needs proof that at the time of each transaction, the majority of nodes agreed it was the first received. 

## Timestamp Server

![](Pasted%20image%2020230326113410.png)
## Proof-of-Work

>The proof-of-work involves scanning for a value that when hashed, such as with SHA-256, the hash begins with a number of zero bits.  The average work required is exponential in the number of zero bits required and can be verified by executing a single hash.

>We implement the proof-of-work by incrementing a nonce in the block until a value is found that gives the block's hash the required zero bits.  Once the CPU effort has been expended to make it satisfy the proof-of-work, the block cannot be changed without redoing the work.  As later blocks are chained after it, the work to change the block would include redoing all the blocks after it.

![](Pasted%20image%2020230326113547.png)
> If the majority were based on one-IP-address-one-vote, it could be subverted by anyone able to allocate many IPs.  Proof-of-work is essentially one-CPU-one-vote.  The majority decision is represented by the longest chain, which has the greatest proof-of-work effort invested in it.  If a majority of CPU power is controlled by honest nodes, the honest chain will grow the fastest and outpace any competing chains.  To modify a past block, an attacker would have to redo the proof-of-work of the block and all blocks after it and then catch up with and surpass the work of the honest nodes.  We will show later that the probability of a slower attacker catching up diminishes exponentially as subsequent blocks are added.


POW difficulty increases on a moving average that targets avg number of blocks per hour. This increases if blocks are produced too fast.

## Network

>1) New transactions are broadcast to all nodes. 
>2) Each node collects new transactions into a block.  
>3) Each node works on finding a difficult proof-of-work for its block. 
>4) When a node finds a proof-of-work, it broadcasts the block to all nodes. 
>5) Nodes accept the block only if all transactions in it are valid and not already spent. 
>6) Nodes express their acceptance of the block by working on creating the next block in the chain, using the hash of the accepted block as the previous hash.

>If two nodes broadcast different versions of the next block simultaneously, some nodes may receive one or the other first.  In that case, they work on the first one they received, but save the other branch in case it becomes longer.

## Incentive

>This adds an incentive for nodes to support the network, and provides a way to initially distribute coins into circulation, since there is no central authority to issue them. The steady addition of a constant of amount of new coins is analogous to gold miners expending resources to add gold to circulation.  In our case, it is CPU time and electricity that is expended.

> If the output value of a transaction is less than its input value, the difference is a transaction fee that is added to the incentive value of the block containing the transaction.  Once a predetermined number of coins have entered circulation, the incentive can transition entirely to transaction fees and be completely inflation free.

## Reclaiming Disk Space

![](Pasted%20image%2020230326114311.png)

>A block header with no transactions would be about 80 bytes.  If we suppose blocks are generated every 10 minutes, 80 bytes * 6 * 24 * 365 = 4.2MB per year.  With computer systems typically selling with 2GB of RAM as of 2008, and Moore's Law predicting current growth of 1.2GB per year, storage should not be a problem even if the block headers must be kept in memory.

This basically states that all you need to store within each Block header is the Hash of the previously combined transactions and then the incoming transactions with their hashes. Where the first and second transactions (Tx0 and Tx1) make up the first Hash (Hash01) and are used to confirm the second batch of transactions (Tx2 and Tx3) and their relative Hash (Hash23). This saves disk space and storage by providing block headers with minimal transactions required for the proof to work.

## Simplified Payment Verification

>A user only needs to keep a copy of the block headers of the longest proof-of-work chain, which he can get by querying network nodes until he's convinced he has the longest chain, and obtain the Merkle branch linking the transaction to the block it's timestamped in.  He can't check the transaction for himself, but by linking it to a place in the chain, he can see that a network node has accepted it, and blocks added after it further confirm the network has accepted it.

This is basically the role of the block explorer, where users can view that their transactions have been added to the block and that the network has accepted it. The tx hash itself can be searched on-chain to verify each transaction.

![](Pasted%20image%2020230326114916.png)
>As such, the verification is reliable as long as honest nodes control the network, but is more vulnerable if the network is overpowered by an attacker.  While network nodes can verify transactions for themselves, the simplified method can be fooled by an attacker's fabricated transactions for as long as the attacker can continue to overpower the network.

## Combining and Splitting Value

>To allow value to be split and combined, transactions contain multiple inputs and outputs.  Normally there will be either a single input from a larger previous transaction or multiple inputs combining smaller amounts, and at most two outputs: one for the payment, and one returning the change, if any, back to the sender. 

This relates to the more common bundle of transactions within one transaction that we see present within Ethereum imo.
![](Pasted%20image%2020230326115513.png)

