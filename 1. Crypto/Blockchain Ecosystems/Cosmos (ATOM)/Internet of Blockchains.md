# Cosmos Breakdown
- Tendermint BFT Consensus: https://docs.tendermint.com/master/introduction/what-is-tendermint.html
	- Tendermint is software for securely and consistently replicating an application on many machines. By securely, we mean that Tendermint works even if up to 1/3 of machines fail in arbitrary ways. By consistently, we mean that every non-faulty machine sees the same transaction log and computes the same state. 
	- Secure and consistent replication is a fundamental problem in distributed systems; it plays a critical role in the fault tolerance of a broad range of applications, from currencies, to elections, to infrastructure orchestration, and beyond.

## Byzantine Fault Tolerance 
 The ability to tolerate machines failing in arbitrary ways, including becoming malicious, is known as Byzantine fault tolerance (BFT) <- (Tendermint docs above)

 "So this is basically referring to the tolerance that machines possess to protect against any potential failures (malicious attacks or other arbitrary methods)"


**Blockchain technology is just a reformalization of BFT in a more modern setting, with emphasis on peer-to-peer networking and cryptographic authentication**
The name derives from the way transactions are batched in blocks, where each block contains a cryptographic hash of the previous one, forming a chain. In practice, the blockchain data structure actually optimizes BFT design.

## Tendermint
Tendermint consists of two chief technical components: a blockchain consensus engine and a generic application interface. 

The consensus engine, called Tendermint Core, ensures that the same transactions are recorded on every machine in the same order. The application interface, called the Application BlockChain Interface (ABCI), enables the transactions to be processed in any programming language. 

Unlike other blockchain and consensus solutions, which come pre-packaged with built in state machines (like a fancy key-value store, or a quirky scripting language), developers can use Tendermint for BFT state machine replication of applications written in whatever programming language and development environment is right for them.
- Building a blockchain from scratch requires 3 layers: Networking, Consensus, and Application Layer. 
- Tendermint BFT packages the networking and consensus layers, reducing time taken to deploy sovereign blockchains.

`There's two classes of software for tendermint; one being distributed key-value stores, the other belonging to blockchain technology`

Tendermint is in essence similar software, but with two key differences:

-   It is Byzantine Fault Tolerant, meaning it can only tolerate up to a 1/3 of failures, but those failures can include arbitrary behaviour - including hacking and malicious attacks.
-   It does not specify a particular application, like a fancy key-value store. Instead, it focuses on arbitrary state machine replication, so developers can build the application logic that's right for them, from key-value store to cryptocurrency to e-voting platform and beyond.

can be used as a plug-and-play replacement for the consensus engines of other blockchain software
- this seems like a good point to focus on since it explains the underlying composability 

Cosmos network is built on Tendermint: https://cosmos.network/


