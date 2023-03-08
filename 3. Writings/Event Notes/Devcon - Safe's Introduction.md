# Stefan explains the benefits of the Gnosis Safe
#event #notion 

## Purpose

-   Learning more about Safe’s origin and where its inspiration came from.
-   Gnosis and the initial outlook of creating an easier to use method for token accounts.
-   The benefits of contract accounts.

## Important Docs & Links

Youtube:

[](https://www.youtube.com/watch?v=9gyZRq162A8)[https://www.youtube.com/watch?v=9gyZRq162A8](https://www.youtube.com/watch?v=9gyZRq162A8)

Gnosis Safe Beta: [](https://blog.gnosis.pm/announcing-the-gnosis-safe-beta-personal-edition-19a69a4453e8?gi=b002ef47f458)[https://blog.gnosis.pm/announcing-the-gnosis-safe-beta-personal-edition-19a69a4453e8?gi=b002ef47f458](https://blog.gnosis.pm/announcing-the-gnosis-safe-beta-personal-edition-19a69a4453e8?gi=b002ef47f458)

DevCon Archive: [](https://archive.devcon.org/archive/)[https://archive.devcon.org/archive/](https://archive.devcon.org/archive/)

---

# Event Notes

🙇🏾‍♂️ This talk opens up by presenting how the Gnosis Safe and Smart Contract Accounts can be beneficial to the current crypto ecosystem.

### Terms

[EOA](https://ethereum.org/en/glossary/#:~:text=of%20execution%20clients.-,externally%20owned%20account%20(EOA),any%20code%20associated%20with%20them.): Externally Owned Account or an account that is controlled by a private key.
[Contract Accounts](https://ethereum.stackexchange.com/questions/114809/what-exactly-is-a-proxy-contract-and-why-is-there-a-security-vulnerability-invol): accounts controlled by code that is executed on the Ethereum Virtual Machine (EVM).
[Proxy](https://ethereum.stackexchange.com/questions/114809/what-exactly-is-a-proxy-contract-and-why-is-there-a-security-vulnerability-invol): an intermediary contract that delegates its contained functions to another contract.
[Multisig](https://ethereum.stackexchange.com/questions/114809/what-exactly-is-a-proxy-contract-and-why-is-there-a-security-vulnerability-invol): a Contract Account that requires multiple signatures to occur before a transaction can be confirmed.

## EOA vs Contract Accounts

The most commonly known wallet interface is an [EOA or an Externally Owned Account](https://ethereum.org/en/glossary/#:~:text=of%20execution%20clients.-,externally%20owned%20account%20(EOA),any%20code%20associated%20with%20them.). This means that accounts are controlled by private keys and/or made accessible through seed phrases.

This is currently how the majority of users interact with protocols, yet this places a large risk on any potential losses of this seed phrase. Your EOA is all that you have access to, which means the private key is all you have available for accessing this account.

### Backups

Stefan explains that passwords and backups being lost should not be final outcome for users as they participate in this ecosystem.

This occurs often with wallet users that lose access to their accounts and try to recover their assets. The companies building these tools will not be able to help you, which is where smart contract accounts can offer a solution to this problem

### Access Control

Private keys can access everything within that wallet but what if you want to remove access to other financial transactions. As we see today, our wallet accounts can become our entire identity. It has become our representation within various ecosystems, it can be how you apply to positions, and people have used their addresses to build a recognizable persona.

However, this private key has access to all of this and does not provide the option for including restrictions or reducing controls, such as placing limits on spending.

One solution to these issues is [Contract Accounts (CA)](https://ethereum.org/en/glossary/#contract-account). A CA has the same interactions available as EOAs, however, they provide a wider range of optionality for what is possible within a CA.

Contract accounts can be made to sign a “meta-transaction”, instead of having to sign the actual transaction with your actual private/public key.

By abstracting away from the previously accustomed process, Contract Accounts allow for a greater variety of use cases for the user.

![](Pasted%20image%2020230308111449.png)

### Meta-transactions

[Meta-transactions](https://www.biconomy.io/post/how-do-meta-transactions-reduce-the-barriers-to-web3#:~:text=A%20meta%20transaction%20is%20an,blockchain%2C%20and%20handles%20the%20fee.) can be viewed as Ethereum transactions that place an additional transaction within the original transaction. As shown above, the user will sign the Ethereum transaction provided by the CA, instead of signing the actual transaction.

The overarching Ethereum transaction will trigger a signature on the proxy transaction. This "proxy" transaction can be viewed as an intermediary between the overarching Ethereum transaction and the underlying meta-transaction. This includes a "validate signature" transaction that confirms with `require(checkSignatures)`.

For execution to occur with this Meta-transactions, Gnosis Safe implements an “n out of m” function that specifies that only owners can validate this signature. This means that there is a set threshold that needs to be reached before any transaction can be confirmed.

![](Pasted%20image%2020230308113147.png)

The opportunity here allows for different types of signatures. One example is through Contract Signatures: this function will call an external contract, where you can have different Safe contracts be owners of other Safes.

The benefit of this can be for larger organizations that are managing funds or protocols that need to create overarching accounts (similar to a parent company and its underlying organizations).

### Execute Calls

There are similar options for EOAs that people can sign for. The Gnosis Safe can do all of the same processes that EOAs can do, such as `executeCalls` and Execute Delegate Calls.

A Delegate Call allows for increased functionality of the Safe just for the duration of that transaction. This allows the user to include different parameters for the transaction.

These CAs also have the ability to produce a "Refund Sender" transaction to the party that was submitting the transaction. Previously, multisig owners would have to hold ETH to sign and execute a transaction.

![](Pasted%20image%2020230308113837.png)

Now, they can refund the person that is trying to sign the transaction. This can occur with a refund in ETH or in any [ERC20 token](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/#:~:text=The%20ERC%2D20%20(Ethereum%20Request,token%20balance%20of%20an%20account).

In this example, the person completing the transaction will have to actually send the meta-transactions after the owners sign for it. Since the account signing has to sign with ETH, this can potentially reduce any barriers that a user might deal with when signing transactions.

### Meta-transaction Relay

The next explains point covers a meta-transaction relayer that would sign these transactions. Stefan explains that this relayer is currently acting as an intermediary between the miner and the user signing the transaction.

In the future, the miner could simply execute the meta-transactions themselves without needing the user to supply ETH. The main concept behind ETH is to simply incentivize miners to accept their transactions. 

These CAs could potentially remove a use case for ETH, since there would be less instances where users need to bribe miners. 

### Batch-Transactions

An additional use case to CAs is the ability to create a "Batch-Transaction". This means combining different transactions together and sending them as a single transaction to the network. A common example of this are [Batch Transfers](https://ethereum.org/en/developers/docs/standards/tokens/erc-1155/#batch-transfers), which allows for transferring multiple assets within a single contract.

For example, in this `multiSend` function, the contract can create a transaction combination that reduces fees needed and allows all transactions to be executed/unconfirmed at once.

![](Pasted%20image%2020230308124730.png)

We can consider an arbitrage trader that is looking to buy an asset on one exchange and sell it for a profit on another exchange as a potential benefactor of this feature. In this circumstance, the trader would want to have all of his transactions be confirmed and executed, instead of only the buy or sell-side.

## Modules

Another advantage to CAs is the ability to extend access using a [Module](https://docs.gnosis-safe.io/learn/safe-core-protocol/modules-1). You can view these as additional apps or contracts that can be built within the Gnosis Safe to satisfy certain requirements. Each Module has to be whitelisted by the Safe owner.

There are two primary locations to learn about available Modules:
1. Safe's Implemented Modules: https://docs.gnosis-safe.io/learn/safe-core-protocol/modules-1
2. Zodiac's Collaborative Modules: https://zodiac.wiki/index.php/Introduction:_Zodiac_Standard#Modules

These can be added or removed at your discretion and include benefits such as daily spending allowances, recurring transactions, and the option for social recovery.

### Recovery Module

As discussed earlier, recovering your private key or account can be a nearly impossible process if you have lost access. With an integrated Recovery Module, Gnosis Safe allows for the other multisig owners to confirm that the account has been lost. 

This then offers the chance to change the owner of the account so that you can recover access. The process follows a `swapOwner` transaction that needs to be confirmed by the other Owners of the account. After execution, the user will be able to recover the account from a different wallet address.

![](Pasted%20image%2020230308130039.png)

## Proxy Contracts

A "Proxy Contract" is a solution for reducing costs of each contract creation. This implements one function that would combine and send all of the underlying contracts within a single bundle, thus decreasing the necessary fees for each function.

You can think of this as a single contract that contains various functions and can be confirmed all within signing one transaction.

In this example, this allows for building new Safes very quickly and cheaply. Users do not have to waste gas on creating multisigs and can let anyone use these contracts without worrying about costs.

## Advantages of Gnosis Safe

As Stefan has explained so far, there are multiple benefits to using CAs, especially with how the Gnosis Safe has been created.

These include:
-   Granular access schemes
    -   Multisig setup: think of multiple owners or 2FA Authentication (what people are usually accustomed to).
    -   Recovery options: allowing for social recovery in case of a lost private key.
    -   Daily limit transactions.
-   Users can pay for transactions in ETH or other ERC20 tokens.
-   The ability implement Batch Transactions.
    -   This improves on-chain experience for the user.
    -   There is now less friction for complex transactions.

### Disadvantages

Execution costs are slightly increased now that your transactions will have to occur through meta-transactions. Time-to-execution will be increased as well since each owner will have to sign a transaction before it can be confirmed.

An additional disadvantage is that using a CA can be viewed as another attack vector, which is now even more important to secure these contracts.

## Contract Security

To confirm the security of their contracts, the Gnosis Safe team completed formal verification. This included verifying the EVM bytecode used within each contract as well as confirming that each smart contract does what it is supposed to do. 

![](Pasted%20image%2020230308132137.png)

**Funding**  
- This was funded by the ECF and GEF, then executed by Runtime Verification.
    -   In the future, they will go forward simplifying the contract and removing any potential bugs.

This is the highest standard of security for smart contracts, which they view this as very important for securing their platform. Although it is time-consuming and costly, it is a necessary step for their continued development.

## Conclusions and Q&A

### Mobile Safe

There is the Safe Mobile App and the browser extension available. This can be found on the App Store or the Google Play Store for download. As of now, the Safe App is fully interactive on each network and can be used as a form of 2-Factor Authentication (similar to a Google Authenticator app).

Safe Mobile App: https://apps.apple.com/app/id1515759131
Safe Website: https://safe.global/

### Bounties

The team had also put together bounties for extending Safe contracts functionality. 
These included:
- Daily Limit Modules for ERC20 tokens and ETH (fully built out and can be found on [Safe Modules](https://docs.gnosis-safe.io/learn/safe-core-protocol/modules-1)).
- Recurring Transfers Module (fully built out and can be found on [Safe Modules](https://docs.gnosis-safe.io/learn/safe-core-protocol/modules-1)).

What is most interesting here is that as each of these Modules have been built out, people have become more creative and developed new use cases for Modules. Over time these have included Bridge Modules for using one Safe to interact with Safes on other networks and other governance related Modules.

### Questions

**What if people will end up colluding or if multisigs end up colluding in recovery module?**

> They haven’t figured this out fully yet. Proper solution will be a proof and authentication requirement. Prove that you don’t have access to wallet anymore and send tx with a bond, basically if no one can send the bond within a month and displays that you don’t have access to the module.

Goal is to create multiple types of security measures. Friends should first agree on this to occur, and they would plan on working around potential ideas for removing attack vectors from other multisig owners.