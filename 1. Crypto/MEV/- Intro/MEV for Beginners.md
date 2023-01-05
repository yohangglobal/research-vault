# Venturing into the Dark Forest
#mev #dev #strategies 
![[Pasted image 20220202143300.png]]
## Foundation
### Definition
**MEV was initially termed as Miner Extractable Value because the process entails measuring a miner's profit from including, excluding or re-ordering the many transactions within a block's production.**

**MEV, Maximal Extractable Value/Miner Extractable Value should now be observed as any automated interaction you can or will do on the blockchain that has positive expected value.** 
https://research.paradigm.xyz/MEV

Importantly, it is **not** speculating on the prices of assets, YOLOing into a ponzi-esque yield farming protocol or any sort of traditional investment strategy. One kind of accurate way to think about it: MEV is to DeFi what HFT is to the stock market.

### Introduction to MEV
**MEV was initially termed as Miner Extractable Value because the process entails measuring a miner's profit from including, excluding or re-ordering the many transactions within a block's production.**

*Example*
So let's consider arbitrages, since they're the most commonly known foundation for applying MEV.

Let's say there's a large trade that just occurred on uniswap (which is a decentralized exchange on the Ethereum network), and it creates a $10,000 arbitrage opportunity. An arbitrage bot notices the opportunity and submits a transaction to capture it, offering a $10 txfee to the miner. One of two things may happen:

1.  A miner will copy and censor the arbitrageur’s transaction in order to capture the opportunity themselves.
2.  Other bots will notice and bid a higher txfee, starting a bidding war for the right to capture the arbitrage. The auction is called a “Priority Gas Auction” (PGA).

The $10,000 potential profit is MEV. If a miner does not capture it, and a PGA is kicked off, the difference between the price at which the auction settles and the total MEV available is the winning trader’s profit (e.g., if a $7,000 fee is paid to a miner, the remaining $3,000 is left to the trader).

There comes a wide and ranging chain of cause and effect that ends up impacting nearly everyone in the market. 
![alt_text](https://research.paradigm.xyz/assets/images/mev/testgraph.PNG)

MEV can be created any time a user interacts with a blockchain, and smart contracts enable a functionally infinite number of potential interactions. Thus, it is computationally infeasible to calculate a blockchain’s total potential MEV by brute force.

**some MEV can only be captured by miners,** because they have the authority to arbitrarily order (or exclude) transactions. Non-mining traders can access a strictly smaller subset of “simple” MEV; “complex” preferences cannot be efficiently expressed through PGA’s.

Another type of MEV seen often in practice is theft from vulnerable smart contracts. One example is described in the “Dark Forest” post by Dan and co. They found a smart contract with a vulnerability that would allow anyone to steal the funds inside; Dan planned to recover the funds by exploiting it before a thief could. However, an arbitrage bot automatically recognized and copied their transaction, replacing their address with its own, and bid a higher transaction fee. The bot’s transaction executed before theirs and made off with the funds.

Feverish non-mining trader activity highlights opportunities that miners can capture more efficiently and profitably. Additionally, the types of MEV that non-mining traders _can’t_ access are a pot of totally untouched miner revenue; that pot may be far larger than the MEV realized to date. At some level, it is more surprising that it took miners this long to become involved.

In our earlier Uniswap example, a large trade caused price slippage, creating a $10,000 profit opportunity (MEV). The bot which arbitrages the market back to parity with the true price is making the Uniswap market more efficient without harming the original trader in the process. This is an example of a **benign MEV transaction**.

in a different version of the same trade, an arbitrage bot would recognize the user’s trade _before_ it’s executed and “sandwich” their transaction between a buy and sell order of its own. The net effect is that **MEV levies an invisible tax on the user**: their order is manipulated into executing at an artificially inflated price, which the bot then sells into for an instant profit. Of course, a miner could do this at no cost to themselves. This is what one might call a **malignant MEV transaction**.

**Any attempt to prevent miners from accessing the revenue stream is liable to incentivize the creation of off-protocol markets.** For example, if all transactions were only allowed to pay a flat rate, we would expect miners to collude with traders to accept payment for transaction priority out-of-band. Similarly, if all transaction fees were burned or paid to a communal pot, miners would simply accept fees separately.

This is why we say that MEV cannot be _easily_ counteracted. Potential mitigations exist, but they require structural changes to the way Ethereum applications are architected and users interact with them.

Ethereum’s application-layer complexity and MEV are continuing to grow exponentially. The known lower-bound on MEV revenues could be larger than the value of ETH miner security incentives within the year.

**Large-scale, efficient MEV extraction may make the “tax” on Ethereum users untenable. Ethereum could become congested and more costly for all applications. The platform UX would be impaired, and that could stall Ethereum’s network effects and momentum.**

There is also the possibility of time-bandits, although it feels unlikely that miners would damage their long-term interest in Ethereum with major re-orgs. A lite version, in which miners intentionally uncle or re-org only small handfuls of lucrative blocks, could still be harmful.
*add in edgar story from zk proofs*

In any case, it’s time to seriously consider what measures we can take if the situation deteriorates.

### Ethereum on MEV
https://ethereum.org/en/developers/docs/mev/
#### Summary
Maximal (formerly "miner") extractable value (MEV) refers to the maximum value that can be extracted from block production in excess of the standard block reward and gas fees by including, excluding, and changing the order of transactions in a block.

In a [proof-of-work](https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/) context, maximal extractable value is also called "miner extractable value." This is because in proof-of-work, miners control transaction inclusion, exclusion, and ordering

- Searchers run complex algorithms on blockchain data to detect profitable MEV opportunities and have bots to automatically submit those profitable transactions to the network.
- for some highly competitive MEV opportunities, such as [DEX arbitrage](https://ethereum.org/en/developers/docs/mev/#mev-examples-dex-arbitrage), searchers may have to pay 90% or even more of their total MEV revenue in gas fees to the miner because so many people want to run the same profitable arbitrage trade
- Finding more techniques to reduce gas usage is an active area of research among searchers.

##### Generalized frontrunners
Rather than programming complex algorithms to detect profitable MEV opportunities, some searchers run generalized frontrunners. 
- Generalized frontrunners are bots that watch the mempool to detect profitable transactions. 
- The frontrunner will copy the potentially profitable transaction's code, replace addresses with the frontrunner's address, and run the transaction locally to double-check that the modified transaction results in a profit to the frontrunner's address. 
- If the transaction is indeed profitable, the frontrunner will submit the modified transaction with the replaced address and a higher gas price, "frontrunning" the original transaction and getting the original searcher's MEV

##### DEX Arbs
It works like this: if two DEXes are offering a token at two different prices, someone can buy the token on the lower-priced DEX and sell it on the higher-priced DEX in a single, atomic transaction. Thanks to the mechanics of the blockchain, this is true, riskless arbitrage.

[Here's an example](https://etherscan.io/tx/0x5e1657ef0e9be9bc72efefe59a2528d0d730d478cfc9e6cdd09af9f997bb3ef4) of a profitable arbitrage transaction where a searcher turned 1,000 ETH into 1,045 ETH by taking advantage of different pricing of the ETH/DAI pair on Uniswap vs. Sushiswap.
![[Pasted image 20220202212552.png]]

##### Liquidations
Searchers compete to parse blockchain data as fast as possible to determine which borrowers can be liquidated and be the first to submit a liquidation transaction and collect the liquidation fee for themselves

##### Sandwich trading
Sandwich trading is another common method of MEV extraction.

To sandwich, a searcher will watch the mempool for large DEX trades. For instance, suppose someone wants to buy 10,000 UNI with DAI on Uniswap. A trade of this magnitude will have a meaningful impact the UNI/DAI pair, potentially significantly raising the price of UNI relative to DAI.

A searcher can calculate the approximate price impact of this large trade on the UNI/DAI pair and execute an optimal buy order immediately _before_ the large trade, buying UNI cheaply, then execute a sell order immediately _after_ the large trade, selling it for the higher price caused by the large order.

Sandwiching, however, is riskier as it isn't atomic (unlike DEX arbitrage, as described above) and is prone to a [salmonella attack](https://github.com/Defi-Cartel/salmonella)

##### NFT MEV
if there's a popular NFT drop and a searcher wants a certain NFT or set of NFTs, they can program a transaction such that they are the first in line to buy the NFT, or they can buy the entire set of NFTs in a single transaction. Or if an NFT is [mistakenly listed at a low price](https://www.theblockcrypto.com/post/113546/mistake-sees-69000-cryptopunk-sold-for-less-than-a-cent), a searcher can frontrun other purchasers and snap it up for cheap.

One prominent example of NFT MEV occurred when a searcher spent $7 million to [buy](https://etherscan.io/address/0x650dCdEB6ecF05aE3CAF30A70966E2F395d5E9E5) every single Cryptopunk at the price floor. A blockchain researcher [explained on Twitter](https://twitter.com/IvanBogatyy/status/1422232184493121538) how the buyer worked with an MEV provider to keep their purchase secret

##### The long tail
DEX arbitrage, liquidations, and sandwich trading are all very well-known MEV opportunities and are unlikely to be profitable for new searchers. However, there is a long tail of lesser known MEV opportunities (NFT MEV is arguably one such opportunity).

Searchers who are just getting started may be able to find more success by searching for MEV in this longer tail. Flashbot's [MEV job board](https://github.com/flashbots/mev-job-board) lists some emerging opportunities

#### On gas

As mentioned, transactions cost [gas](https://ethereum.org/en/developers/docs/gas/) to execute. Simple transfer transactions require 21000 units of Gas.

So for Bob to send Alice 1 ETH at a `baseFeePerGas` of 190 gwei and `maxPriorityFeePerGas` of 10 gwei, Bob will need to pay the following fee:

(190 + 10) * 21000 = 4,200,000 gwei

--or--

0.0042 ETH

Bob's account will be debited **-1.0042 ETH**

Alice's account will be credited **+1.0 ETH**

The base fee will be burned **-0.00399 ETH**

Miner keeps the tip **+0.000210 ETH**

Gas is required for any smart contract interaction too.

![Diagram showing how unused gas is refunded](https://ethereum.org/static/c3638b26a1210d2c73a7ec2335c57351/302a4/gas-tx.png "Diagram showing how unused gas is refunded")
### 0 to Hero
Compilation Thread by Korogaya
[https://twitter.com/0xkorogaya/status/1468994152390176770?s=21](https://twitter.com/0xkorogaya/status/1468994152390176770?s=21 "https://twitter.com/0xkorogaya/status/1468994152390176770?s=21") 

0xmebius MEV 101
[https://github.com/0xmebius/mev/blob/main/MEV101.pdf](https://github.com/0xmebius/mev/blob/main/MEV101.pdf "https://github.com/0xmebius/mev/blob/main/MEV101.pdf")
https://calblockchain.mirror.xyz/c56CHOu-Wow_50qPp2Wlg0rhUvdz1HLbGSUWlB_KX9o

### Youtubes
"Frontrunning in Ethereum"
[https://www.youtube.com/watch?v=UZ-NNd6yjFM&feature=youtu.be](https://www.youtube.com/watch?v=UZ-NNd6yjFM&feature=youtu.be "https://www.youtube.com/watch?v=UZ-NNd6yjFM&feature=youtu.be") 

"Miner Extractable Value with Phil & Georgios" - Georgios Konstantopoulos & Phil Daian
[https://www.youtube.com/watch?v=tv0CkmcoGkM&feature=youtu.be](https://www.youtube.com/watch?v=tv0CkmcoGkM&feature=youtu.be "https://www.youtube.com/watch?v=tv0CkmcoGkM&feature=youtu.be") 

"Frontrunning in Decentralized Exchanges, Miner Extractable Value, and Consensus Instability"
[https://www.youtube.com/watch?v=vR1v7AQ8i3k&feature=youtu.be](https://www.youtube.com/watch?v=vR1v7AQ8i3k&feature=youtu.be "https://www.youtube.com/watch?v=vR1v7AQ8i3k&feature=youtu.be")

"FlashBots: How to make $1m per month"
https://www.youtube.com/watch?v=lXq0eU8viFQ

## Resources
### Arxiv readings
First step to understand Flash Loans
https://arxiv.org/pdf/2010.12252

Galaxy Digital Summary
https://docsend.com/view/vr6seimd2bfx8iei

Pdaian Blog
https://pdaian.com/blog/
https://pdaian.com/blog/mev-wat-do/

### Tutorials
#### Build a Flash Loan bot on Infura
https://blog.infura.io/build-a-flash-loan-arbitrage-bot-on-infura-part-i/

https://blog.infura.io/build-a-flash-loan-arbitrage-bot-on-infura-part-ii/?&utm_source=infurablog&utm_medium=referral&utm_campaign=Tutorials&utm_content=flashbot1

**Infura endgoal**

![[Pasted image 20220314194455.png]]


#### Using Furucombo for Flashloans
https://furucombo.app/combo
https://medium.com/furucombo/create-flashloan-combo-on-furucombo-c7c3b23267f0

![](https://miro.medium.com/max/1400/0*TL8j_UTbbMcQQiNs)

##### **What is Flashloan?**

Flash Loans are introduced by the [Aave](https://app.aave.com/home), an open-source lending protocol for anyone to deposit and borrow cryptographic assets. Essentially, flashloans let users borrow any amount up to the total liquidity available without any collateral, so long as the loan is repaid in the same transaction. If the loan is not repaid, the whole transaction will be reverted. With flashloan anyone can access a massive amount of liquidity, and use the loan with other protocols however they want. You can become a ‘whale’ without any capital.

At the time of writing, there are three pools providing flashloans:

-   **Aave:** 17 tokens available with 0.09% fee
-   **dYdX:** 3 tokens available zero fee *
-   **Uniswap V2:** 100+ tokens available with 0.3% fee

_* Note that flashloan on dydx is not a consumer feature. It is achieved by developers chaining Withdraw, Call and Deposit actions._

So, flashloan sounds like a very good deal. What exactly can you use it for? [Marc Zeller](https://twitter.com/lemiscate) from Aave has written a very nice piece demonstrating some of the top use cases for flashloan.

[

##### Sneak peek at Flash Loans
We summarize the use cases:

-   Arbitrage trades
-   [Collateral swap](https://deflast.finance/)
-   Self-hedging
-   Self-liquidation
-   (Debt) Interest rate swap
-   (Debt) Curreny swap

The most popular use case by far is **_Arbitrage trades_**. For those unfamiliar, arbitrage is the strategy of making a profit from price differences between different markets. To make a significant amount of profit, you will need substantial capital to get started. And this, is where the magic happens — We use flashloan to generate free money with no upfront cost.

##### Before we get started

There are some important things to understand:

> For arbitrage traders, Furucombo lowers the barriers-to-entry for building money legos, providing all the necessary elements to create arbitrage strategies including the so far coder-only flashloans. But, please keep in mind that Furucombo does **_NOT_** find arbitrage opportunities for you. You will have to find it yourself. ✊🏻

Enough with the disclaimer, let’s get to the checklist. 👇🏻

1️⃣ Find an arbitrage opportunity >0.09% to cover flashloan's fee  
2️⃣ Have some ETH in your wallet enough to pay for gas

On Furucombo, there are two pools supported, Uniswap (V1) and Kyberswap. The example we use in the following is an arbitrage opportunity found between KyberSwap and Uniswap V1 a few months ago.

![](https://miro.medium.com/max/1200/1*Y1JOUlV7boLecbi9YRmpBA.png)

Rate difference: 20+%  
1 DAI = 0.9927 sUSD on Kyberswap  
1 DAI = 0.8057 sUSD on Uniswap  
👉🏻 **_Buy low sell high: Buy sUSD on Uniswap and sell it on Kyberswap_**

Now you found the rate difference, let’s start creating the combo. The complete combo should look like this:

1️⃣ Borrow 100DAI from Flashloan  
2️⃣ Swap 100DAI to 122.83649sUSD on Uniswap  
3️⃣ Swap 122.83649sUSD to 122.83429DAI on Kyberswap  
4️⃣ Repay 100.09DAI to Flashloan  
5️⃣ You keep 22.74429DAI profit.

##### Step by step

##### 1. Go to [Furucombo](https://furucombo.app/)

##### 2. Add a Uniswap cube

![](https://miro.medium.com/max/1052/1*8l3EqTp3Tk4D9v8OS4ceuA.png)

1️⃣ Click the cube with '+' symbol   
2️⃣ Choose 'Swap Token' under Uniswap section  
3️⃣ Enter Input: 100DAI  
4️⃣ Output generated from Uniswap: 122.83649sUSD  
5️⃣ Click 'Set'

##### 3. Add a Kyberswap cube

![](https://miro.medium.com/max/1068/1*e-v-jWbGEs_-znXgxybVKA.png)

1️⃣ Click the cube with '+' symbol   
2️⃣ Choose 'Swap Token' under Kyberswap section  
3️⃣ Enter Input: 122.83649 sUSD  
4️⃣ Output generated from Kyberswap: 122.83429 DAI  
5️⃣ Click 'Set'**💡 Tips:** If your input is according to the previous cube's output, enter slightly lower amount instead of the exact amount. This way, you can avoid combo failure due to rate difference. 

##### 4. Add Flashloan cube

![](https://miro.medium.com/max/1068/1*F_b0egiieYC7ddH68hiDJw.png)

1️⃣ Click the cube with '+' symbol   
2️⃣ Choose 'flashloan' under Aave section  
3️⃣ Enter amount: 100DAI  
4️⃣ Click 'Set'  
5️⃣ Two cubes appear. 1st cube is borrow 100DAI and 2nd cube is payback 100.09DAI.

##### 5. Drag flashloan’s 1st cube to the top

This is simply adjusting the execution order. You want to borrow from flashloan at the very beginning to have the upfront capital. So, just click and drag the borrow cube to the top and keep the payback cube at the bottom.The final combo would look like...

![](https://miro.medium.com/max/1400/1*xJR5X5GnVNelOFB6GlKBvA.png)



#### UniSwap FlashSwaps: Make Millions of Dollars With Your Code
Uniswap Flashswaps: Millions with ya code
https://thecitadelpub.com/uniswap-flashswaps-make-millions-of-dollars-with-your-code-14d7d5f017dd

##### An A-Z guide on how to program a smart contract that executes an arbitrage strategy using a UniSwap flash loan.

![](https://miro.medium.com/max/1400/1*Fism3Om51FutwhX0EtlVDQ.jpeg)

> “… I will be showing you how to get a $2,000,000 Flash Loan and then execute an arbitrage strategy between the exchanges SushiSwap and UniSwap…”

With DeFi making the news almost daily, it would be an understatement to say that people are fascinated with the projects and technologies that are emerging in the Decentralized Finance scene. One such technology is **_Flash Loans_**.

Although a detailed analysis of Flash Loans can be found [here](https://medium.datadriveninvestor.com/defi-flashloans-borrow-millions-and-pay-nothing-in-advance-183145e3ac17), they can be described as a new form of uncollateralized **lending,** where the borrower must borrow and repay the funds within the same transaction.

With Flash Loans now having been defined (I would highly recommend you read the article I cited above first), it is time to define Flash Swaps — the Flash Loan alternative of the UniSwap protocol. According to the documentation:

> Uniswap flash swaps allow you to withdraw up to the full reserves of any ERC20 token on Uniswap and execute arbitrary logic at no upfront cost, provided that by the end of the transaction you either:
> 
> - pay for the withdrawn ERC20 tokens with the corresponding pair tokens
> 
> - return the withdrawn ERC20 tokens along with a small fee

**Now that all the important definitions are out of the way, it is time to dive into the gist of this article — how to program a profitable Flash Loan.**

##### Plan of Attack

_I just published the only A-Z guide I have seen on the internet on how to deploy a Flash Loan on the Binance Smart Chain (code included!). You can find it_ [_here_](https://www.patreon.com/posts/bsc-flash-loans-50479380)_._

Let’s assume for a second that we receive a Flash Loan of **$2,000,000** — liquidity that we can employ in any way we want. Although there are multiple different techniques that can be used to profit from Flash Loans, **arbitrage** is the most straight forward and rewarding _(more information on Flash Loan-powered arbitrage can be found_ [_here_](https://medium.datadriveninvestor.com/defi-flashloans-borrow-millions-and-pay-nothing-in-advance-183145e3ac17)_.)_

For the purpose of this article, I will be showing you how to get a **$2,000,000 Flash Loan** and then execute an arbitrage strategy between the exchanges **SushiSwap** and **UniSwap**, profiting from the price discrepancies of the ETH/DAI pair.

A theoretical pipeline outlining the logic of my approach is shown below:

-   Borrow 2M DAI ($2,000,000)
-   Buy 1000 ETH on Exchange A for 2000 DAI/ETH
-   Sell 1000 ETH on Exchange B for 2005 DAI/ETH
-   Reimburse 2M DAI + 0.3% Fee
-   Keep the difference

##### Writing the Smart Contract

![](https://miro.medium.com/max/1400/0*AYm1W_sqy-nzdVfJ)

Photo by [Florian Olivo](https://unsplash.com/@florianolv?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

_With SushiSwap being a fork of UniSwap, the different functionalities of the contract all relate back to UniSwap V2 (The different UniSwap V2 contracts can be found in_ [_this Github repo_](https://github.com/Uniswap/uniswap-v2-core)_)._

After defining the version of solidity we will be using (UniSwap V2 is built on 0.6.6), we must import a number of interfaces needed to interact with UniSwap V2.

With that out of the way, it is time to start writing the contract itself. One of the first steps is to define a number of crucial variables, such as:

-   **factory**: A central hub within the UniSwap ecosystem that provides information about the liquidity pools.
-   **deadline**: The date the trade is due.
-   **sushiRouter**: A central smart contract in the SushiSwap ecosystem that is used to trade in its liquidity pools.

We can now create the constructor, initializing the value of the UniSwap Factory and sushiRouter:

##### The Arbitrage Function

With the basics now being out of the way, we can create the most important part of the contract which is the “_startArbitrage_” function, outlining the logic for the arbitrage.

Within the function, it is important to define the:

-   **token0**: The token we are going to borrow (eg. DAI).
-   **token1**: The token we are going to trade token0 for (eg. ETH).
-   **amount0**: The amount we are going to borrow.
-   **amount1**: This will be 0 for now.
-   **pairAddress**: The address of the pair smart contract of UniSwap for the two tokens (the address of the liquidity pool).

_*When the swap method is called, “address(this)” is entered as a parameter. By doing this, we provide the address we want to receive the borrowed tokens (“this” automatically routes to your address)._

###### Calling the Flash Loan

Having written the method in charge of the arbitrage logic, it is important to outline the logic for the FlashSwap itself.

To do so, the following arguments must be defined:

-   **_sender**: The address that triggered the Flash Loan
-   **_amount0**: The amount borrowed
-   **_amount1**: 0
-   **address**: An array of addresses used to complete the trade.
-   **amountToken**: This will be equal to “_amount0”.
-   **token0**: The address of the first token in Uniswap’s liquidity pool.
-   **token1**: The address of the second token in Uniswap’s liquidity pool.
-   **IERC20 token**: A pointer to the token that we are going to sell on SushiSwap.
-   **amountRequired**: The amount of the initial token that must be reimburshed for the Flash Loan to UniSwap.

The only thing now remaining is to pay back the amount due to the lender and send the profit to our wallet.

_The complete code needed for the deployment of your smart contract on both the Ethereum mainnet and testnet + how to deploy it on the Binance Smart Chain can be found_ [_here_](https://www.patreon.com/posts/flashswaps-code-49927919?utm_medium=clipboard_copy&utm_source=copy_to_clipboard&utm_campaign=postshare) _&_ [_here_](https://www.patreon.com/posts/bsc-flash-loans-50479380)_._

##### Conclusion & Next Steps

Having understood and replicated the smart contract outlined and explained above, you now possess the power to borrow millions of dollars, and just as the perpetrators of the [bZx attack make millions](https://medium.datadriveninvestor.com/defi-flashloans-borrow-millions-and-pay-nothing-in-advance-183145e3ac17).

Obviously, in order to deploy the contact, you will need to take care of the migrations contract and use a platform such as truffle (You can download the files [here](https://www.patreon.com/posts/flashswaps-code-49927919?utm_medium=clipboard_copy&utm_source=copy_to_clipboard&utm_campaign=postshare)).

The one thing required on your part would be to develop a script (in either JS or Python) that would monitor the prices of specified pairs across different exchanges and would execute the contract once a profitable opportunity arises (stay tuned for the related article).

##### DeFi Flashloans: Borrow Millions and Pay Nothing in Advance
https://medium.datadriveninvestor.com/defi-flashloans-borrow-millions-and-pay-nothing-in-advance-183145e3ac17

#### How to make a Flash loan using Aave
https://www.quicknode.com/guides/defi/how-to-make-a-flash-loan-using-aave

##### Overview

Aave, previously known as ETHLender, has catapulted to the forefront of the DeFi space. Aave was the first in the space to come up with the idea of a [Flash Loan](https://aave.com/flash-loans/). Before flash loans, you would have to stake an over-collateralized asset to loan another asset. For example, if I wanted to borrow one [DAI](https://en.wikipedia.org/wiki/Dai_(cryptocurrency)) I would have to deposit another cryptocurrency that exceeded that value. In other words, you had to have money to borrow money. Flash Loans demolished this idea. And they opened up doors for a new loaning system. They did this by allowing users to borrow without putting up anything as collateral. In this tutorial you will learn how this is possible and how you can do it yourself!

##### About Aave

Taken from the [Aave website](https://aave.com/).  
  

> Aave is a decentralised non-custodial liquidity market protocol where users can participate as depositors or borrowers. Depositors provide liquidity to the market to earn a passive income, while borrowers are able to borrow in an over collateralized (perpetually) or undercollateralized (one-block liquidity) fashion.

  

While that is entirely correct, it may not make much sense to you if you aren’t already familiar with all of the DeFi industry jargon. You could think of Aave as being a decentralized pseudo-bank. Instead of a central bank that validates all of the transactions, Aave has smart contracts that do all of this work in an automated fashion. Depositors put their tokens into Aave, and begin earning interest on their deposit. Borrowers on the other hand will do the opposite. They will take money out of Aave and will begin accruing interest on the amount borrowed. In order to do this, they must be [overcollateralized](https://www.oxfordreference.com/view/10.1093/oi/authority.20110803100257900).

  

There is another method for those that don’t want to deposit money into Aave, and just want to borrow. This is the Flash Loan we mentioned earlier.

  

##### About Flash Loans

The previously mentioned Flash Loan is a new way of borrowing assets on the blockchain. Initially implemented by Aave, other trending DeFi protocols such as [dYdX](https://dydx.exchange/) quickly followed suit in adding this new feature. There is a property that all Ethereum transactions share that enable Flash Loans to be possible. And this key feature is [atomicity](https://en.wikipedia.org/wiki/Atomicity_(database_systems)#:~:text=An%20atomic%20transaction%20is%20an,rejecting%20the%20whole%20series%20outright.).

  

A transaction is atomic whenever the series of its operations are indivisible and irreducible. Or in plain english— either _all_ or _none_ of the transaction occurs. No halfsies! The Flash Loan leverages atomicity to allow a user to borrow without posting collateral.There are two caveats to mention. First of all, whenever you borrow an asset in a Flash Loan you have to pay a fee of 0.09% of the amount loaned. Secondly, you must pay back the loan in the same transaction in which you borrowed. While this ability is great, it is somewhat limited in its use. Flash Loans are primarily used for [arbitrage between assets](https://en.wikipedia.org/wiki/Arbitrage).

  

##### Remix Setup

For the sake of simplicity, we will be using the [Remix IDE](https://remix.ethereum.org/).

  

This is a browser-based IDE. Also known as an Integrated Development Environment.

Remix comes with the ability to write, debug, deploy, and otherwise manipulate [Ethereum Smart Contracts](https://ethereum.org/en/developers/docs/smart-contracts/).

  

When you load up Remix in your browser, you will be greeted by this menu.

![](https://lh6.googleusercontent.com/ddjSTmRa2bEMUoYYdubmBmmlQ68f_eg1o1tNfSqt5jr2HOwUwE4YB4rh67iSAJdzhVH9k9SbxAJNNz5zDLT7C7FNmAaI9TialimBRkerRB9EihbV7pQMTOWqkPE4f6WmyrwTR1r6)

  

We won’t be doing a deep dive on the IDE, as the focus of this tutorial is on the Flash Loan. However, you will want to become familiar with the four sections highlighted: main panel, side panel, icon panel, and terminal.

  
Before we start writing our smart contracts we will want to download a browser extension that allows us to interface with the Ethereum blockchain. There are several tools out there that unlock such functionality, but the most popular one is [MetaMask](https://metamask.io/).

##### MetaMask Setup

A step-by-step breakdown of how to install MetaMask.

  

1.  You will start by downloading the extension off of the website above.
2.  Click on your newly installed extension and agree to the terms and conditions.
3.  Create a secure password!
4.  Write down the mnemonic seed phrase. This should be in the physical world, and shouldn’t be kept anywhere on your computer.

  

If the four steps outlined above are completed you are all ready to start writing your first smart contracts!

##### The Smart Contract

Smart contracts allow us to read and write data to the blockchain by executing deterministic programs. When coding a smart contract for use on Ethereum, we use a programming language called [Solidity.](https://docs.soliditylang.org/en/v0.8.5/) Solidity files end in the .sol extension.

  

> You can delete any files that may be in your workspace when you first boot up Remix.

  

You will want to create several files:

1.  **FlashLoan.sol**
2.  **FlashLoanReceiverBase.sol**
3.  **ILendingPoolAddressesProvider.sol**
4.  **IFlashLoanReceiver.sol**
5.  **ILendingPool.sol**
6.  **Withdrawable.sol**

  

The following code snippet is the implementation of **FlashLoan.sol.**

  
This Flash Loan will be borrowing 1 [DAI](https://en.wikipedia.org/wiki/Dai_(cryptocurrency)).

pragma solidity ^0.6.6;

import "./FlashLoanReceiverBase.sol";

import "./ILendingPoolAddressesProvider.sol";

import "./ILendingPool.sol";

contract FlashloanV1 is FlashLoanReceiverBaseV1 {

    constructor(address _addressProvider) FlashLoanReceiverBaseV1(_addressProvider) public{}

 /**

     Flash loan 1000000000000000000 wei (1 ether) worth of `_asset`

  */

 function flashloan(address _asset) public onlyOwner {

     bytes memory data = "";

  
To summarize, we start by importing the dependencies required to execute our Flash Loan. Some of these dependencies are called [abstract contracts](https://docs.soliditylang.org/en/v0.6.2/contracts.html#abstract-contracts). An abstract contract has at _least_ one function that isn’t implemented. You can think of it as a blueprint of a house. A builder uses this blueprint to make a house. However, in our analogy the blueprint is an abstract contract, you are the builder, and the house is the derived contract.  
  
In our case the Flash Loan contract is using an abstract contract called **FlashLoanReceiverBaseV1**. It provides necessary implementation details such as repayment of the Flash Loan.

Now to break down the code line by line.

1.  First, we have to define the solidity compiler version. In this case, it's 0.6.6.

     2-4. Importing dependencies for the smart contract

      6. The FlashLoanV1 contract is inheriting from the FlashLoanReceiverBaseV1 contract.

      8. We passed the address of one of the Lending Pool Providers of Aave. In this case, we are providing the address of DAI Lending Pool. 

     13. We have defined a function called flashLoan. It takes the address of the asset we want to flash loan. In this case the asset is DAI.

14. We don't have any need of data for the flash loan, so we are passing an empty string.

15. We are defining the number of DAI(in terms of wei which is 10^18) we want to loan.

16. We initialize the LendingPool interface which is ILendingPoolV1 provided by Aave so that we can call the flashLoan function.

17. Finally, we call our flashLoan function. The function takes 4 main parameters. First we pass the address which will receive the loan. In our case, it's our own contract. Second, we pass the address of the asset. In our case, it's the address of DAI in the Kovan network. Third, we pass the amount of assets, and in our case it's 1 “ether” amount of units(or 10^18 in “wei” units). Last but not least, we pass the data value which in our case is an empty string.

24-31 Next, we define the second function which is executeOperation. It’s where we utilize the flash loan. It’s called internally after the flashLoan function is successfully executed. It takes 4 main parameter which are -  
        1. The address of reserve to which we will have to pay back the loan.  
        2. The amount of asset  
        3. The fee that is charged by the protocol  
        4. Additional parameter which is used internally by the function.

33. It checks if we received the appropriate amount of loan or else it will throw an error message.

34. At this point, this is where you would implement logic for any arbitrary use case.

40. We add the fee along with the loan amount by using add function provided by SafeMaths library.

41.At last we pay back the total debt or loan amount back to the lending pool
  

##### Deploying The Contract

1.  First, open your MetaMask and set your network to "Kovan Test Network".

  

![](https://lh6.googleusercontent.com/WgrXeVhsLdpVkGkrgYOUe5RPKgr1KiNvEG2ryRjFENy9N8Q7CIFjlAADsvPORFmcA36Szu0ANj3rcKyfTAEjlgtkPZznwGYdkSyupmpjl4rCXPHj4n8s16S_wrah72JKQW7mkwoR)

  
2. Use this gist for defining the dependencies for flashloan smart contracts. Click each of the links and paste the code into the corresponding Solidity file you made earlier.  
        a.[ILendingPool](https://gist.github.com/akp111/e254b2b5b98aa5a79f3f8dc501dfaedb#file-ilendingpool-sol)  
        b.[IFlashLoanReceiver](https://gist.github.com/akp111/e254b2b5b98aa5a79f3f8dc501dfaedb#file-iflashloanreceiver-sol)  
        c. [ILendingPoolAddressesProvider](https://gist.github.com/akp111/e254b2b5b98aa5a79f3f8dc501dfaedb#file-ilendingpooladdressesprovider-sol)  
        d. [FlashLoanReceiverBase](https://gist.github.com/akp111/e254b2b5b98aa5a79f3f8dc501dfaedb#file-flashloanreceiverbase-sol)  
        e. [Withdrawable](https://gist.github.com/akp111/e254b2b5b98aa5a79f3f8dc501dfaedb#file-withdrawable-sol)  
  

![](https://lh4.googleusercontent.com/0VlsOWyZlAHptEOYVO1mCXHuhFntB9leat-QdbswD2Z418sNEsWCwFXR6FGbVI5y7SqlDPQwf7JLCF5ZIE7Sa4XhJzbaMDmFDphP3XuRUeZ3S_0pbOK1AEsdMM5UrR3yggIf30Ec)

  
3. Switch to the "Solidity Compiler" tab. Set the compiler to 0.6.6 and click on "Compile FlashLoan.sol".  
  

![](https://lh3.googleusercontent.com/GXQB4LGOKknLLWi_5BZl72azN7ykRAC5vBBKb7RYypsrEPhBIvp1vi6BvicDMvuIMK3ymOZQYCpLYlB5oQsy0FqsoW9rQMhHmoWkXYCtQzmKg3ii-ZLtC4TbDcVY67Bly-h4Op5d)
4. You should see some warnings but no error message.  
  
5. Now, we are all set to deploy the contract to the Kovan network. Switch to "Deploy & Run Transactions" tab. Under the environment field, change it from JavaScript VM to Injected Web3. This should open MetaMask asking for your permission.  
![](https://lh5.googleusercontent.com/YwdvqJnXD9NGQXSFzI9hd3r8d-Upiu8UqqXc9gEZak2NqSHiX3L-x1t-qSlum6wZMCyfIXbj-D4xOmArDOso6yISNwXxk-3HY26xmVdGWsmtkx6MdJ-JML9z3ohtEQCavKPf7piZ)

6. Make sure the “CONTRACT” field is set to FlashLoan.sol. Provide the address of LendingPool in the text field that is next to the deploy button. In our case, it will be **0x506B0B2CF20FAA8f38a4E2B524EE43e1f4458Cc5**. Then click “Deploy”. It should open up MetaMask.   
  

> **Note**: A list of all deployed contract addresses can be found [here](https://docs.aave.com/developers/v/1.0/deployed-contracts/deployed-contract-instances). There, you can find the addresses of various Lending Pools supported by Aave. Though the addresses are different for every token, the procedure remains the same.

  

![](https://lh6.googleusercontent.com/qis_4Nr7FcYEMDvp-y22E1IegEQc-Epyno_HMwb_ioHOKOlb-cN7UbeMlYrueVZeplaY1EdhfsDwV2EOEuVtb4iBfuXC07Qef4NUtQWbXAzV3diagaFzcUouP8_glzR0C_9xGelv)

7. Click on “Confirm”. Upon doing so, you should see a success notification from MetaMask. There should now be a “Deployed Contracts” in the side panel.

##### Funding The Flash Loan
![](https://lh6.googleusercontent.com/XDusVPCOGW5TzqcXwLrbZGCFwhNt6Z6m2y_GLy4S9FpOYuiZKezNdFJNr_rNncXBYkcxaViaONeS4czvHfkLIpKfe7Z-0SZW4ON-tFJNcY2BMFb7QQnQzh2M62U9ykpLslTmnc4i)

Under the new “Deployed Contracts” tab, you will be able to copy the deployed contract's address. We will come back to this step later; in the meantime we need to add some DAI to our Flash Loan contract. This is because Flash Loans need funds in the contract to successfully execute. For that, you can jump to [this](https://testnet.aave.com/faucet/DAI) link to get some DAI tokens (be sure to connect to the “Aave v2 Market” with a little “K” in the top right corner). Click on the faucet, paste in your MetaMask wallet address, and wait for confirmation.  
  

![](https://lh5.googleusercontent.com/Ajj4UPZAeG3qe8trgnMVgaXAdK2Sh7EpfX0jU8V-NOIqq2cSgIzGUQMNtX76r1dqJFNu0eEfwVBxPJfBGZ86c_40bgdUM8komE4Shkhdoti9KxYRTswf_sHjk-edmDZQNKIdnevs)

  

After obtaining confirmation, we are going to add the DAI token to MetaMask. For that, open your MetaMask. Click on “Add Token” at the bottom. In the “Token Contract Address” field enter 0xFf795577d9AC8bD7D90Ee22b6C1703490b6512FD. This is the contract address for DAI in Kovan. After clicking “Next”, It should display the DAI you got from the faucet earlier.  
  

![](https://lh4.googleusercontent.com/0mv-l7oo6womMIHj1gwc_ZgMLkmrQdFXz71Dsx9Q1IWGQcrSmAqdy7yblr3r5OlJrYwTxCwjXBEEGX5K6xP-FogmaZHxXGaySAtiCHh7_7Xp_VXgrmC82ud0mNOsAyFhDgYRBMJ5)

  

Next up, click on the DAI token. Click on “Send” and it should open a window similar to the picture below.  
  

![](https://lh3.googleusercontent.com/4Gzc_OOpAU1G69SATQwY9iGL34wBFkV0Bm73RiYy2-bySGK7wJ4wZeDVNRlSlwm9IGIVr7OnPhDnmz2MN64cYyk2d6rXk2moXZhVMiaqWLWCWKadVeOttAP7LaUDEHGQqFSIh013)

  
  
Enter our Flash Loan’s contract address, which we found out where to obtain earlier. Enter the amount which we want to send. In our case, we will send 10 DAI. Then click on "Next". Click on "Confirm"! You have now successfully given your Flash Loan contract 10 DAI.

##### Executing The Flash Loan

Head back to Remix. Under the deployed Flash Loan contract, there’s another “flashloan” text field. This field takes a contract address of the asset we want to use. In our case it’s the Kovan Testnet’s DAI contract, which is 0xFf795577d9AC8bD7D90Ee22b6C1703490b6512FD. With that field correctly filled in, you can now hit the “transact” button as shown below.  
  

![](https://lh3.googleusercontent.com/PLQXilUZZXfGFiaE5aveUuXTuQavlXdlGvi4NKGNPj2Z5qOwvM_Zv3LWsZIPkNgAd1wyS2WAE0o4khUSf96ZMxaXWNXTUZaQPyKNwSP6XcFfmFbcr8ThzANOc3HMTgddY8XEEqJf)

  

Upon clicking the button, MetaMask should pop up asking for approval of the transaction. Confirm the transaction and you should be greeted by a success message. In Remix’s terminal you should see an URL. Click on that and you should be redirected to Etherscan.

  

![](https://lh4.googleusercontent.com/yo-7JzxNyoIb1PTeT2CsFkaIUiWM5M1bbji6YKBWhLUTEFBIpzLIS-cWOGd3mIBYV15ihHJjqTQ3mHvC41sDas5CLajBGLVWTTjlrQDTgFiGXQnffEg24UDpPnNh39auETP5bJ1-)

  

Under “Tokens Transferred”, you should see three different transactions.

![](https://lh6.googleusercontent.com/IVZDXrKdh1NYdXuC63vng1OblAvKdmG9dl7CSR1dkH1pX52osPp-uPYwd0Ymi2L3PKmirplj8G4GgQXJkAdL6c0RNKZ9JpUJ52B7vE_OYQ5NZQfXDbM2JQybCyk-D7WSJZLj5Ltx)

1.  The red arrow highlights the transfer of 1 DAI from LendingPool to our contract.
2.  The orange arrow indicates the payback of 1 DAI along with the fees back to the Landing pool.
3.  The blue arrow shows the interest generated DAI which has its separate utility.

## Flashbots
`Flashbots is a research and development organization working on mitigating the negative externalities of current MEV extraction techniques and avoiding the existential risks MEV could cause to state-rich blockchains like Ethereum.`

`Our primary focus is to enable a permissionless, transparent, and fair ecosystem for MEV extraction. It falls under three goals: Bringing Transparency to MEV Activity, Democratizing Access to MEV Revenue and Enabling Fair Redistribution of MEV Revenue`

### Starting point
-   [Ethereum is a Dark Forest](https://www.paradigm.xyz/2020/08/ethereum-is-a-dark-forest/) by Dan Robinson & Georgios Konstantopoulos
-   [How to get Front-Run on Ethereum mainnet](https://youtu.be/UZ-NNd6yjFM) by Scott Bigelow
-   [Escaping the Dark Forest](https://samczsun.com/escaping-the-dark-forest/) by samczsun
-   [Frontrunning in DEXs, Miner Extractable Value, and Consensus Instability](https://youtu.be/vR1v7AQ8i3k) by Phil Daian at IEEE Symposium on Security and Privacy
-   [Flashbots: Frontrunning the MEV Crisis](https://medium.com/flashbots/frontrunning-the-mev-crisis-40629a613752) by Flashbots
-   [ETHOnline - Phil & Georgios Talk Miner Extractable Value](https://youtu.be/tv0CkmcoGkM)
-   [Quantifying MEV: Introducing MEV-Explore v0](https://medium.com/flashbots/quantifying-mev-introducing-mev-explore-v0-5ccbee0f6d02) by Flashbots
- [On the Formalization of MEV](https://writings.flashbots.net/research/formalization-mev/) by Flashbots

You can check out a full list of MEV resources in our [Research Vault](https://github.com/flashbots/mev-research/blob/main/resources.md)

### Websites
https://docs.flashbots.net/
#### MEV Explore
https://explore.flashbots.net/
https://explore.flashbots.net/data-metrics
![[Pasted image 20220202132734.png]]

**Arbitrage Example**
https://etherscan.io/tx/0xb72689042f313adbffbe4d192b0febc4c8a8346b75a549d5b4d4795b37180488

### Github
https://github.com/flashbots/pm

#### MEV Job Board
https://github.com/flashbots/mev-job-board

https://github.com/flashbots/mev-job-board/blob/main/specs/maker-wsteth-liquidations.md

##### Steps to capture MEV^^^
1.  Flashmint the required DAI amount
2.  Liquidate the bad debt position with flashminted DAI
3.  Swap part (or all if you want profit in debt asset) of collateral asset to repay flashmint: wstETH straight on balancer and wstETH-DAI pair on Sushi; unwrap and liquidate steth->eth on curve and eth->dai on DEXes.
4.  The remaining asset is your profit

#### Simple Arbitrage
[https://github.com/flashbots/simple-arbitrage](https://github.com/flashbots/simple-arbitrage "https://github.com/flashbots/simple-arbitrage") 

Walkthrough by Bert
[https://www.youtube.com/watch?v=wn8r674U1B4](https://www.youtube.com/watch?v=wn8r674U1B4 "https://www.youtube.com/watch?v=wn8r674U1B4")

##### Notes
Using discord and the searchers channel to find alpha and leanr more about the group and different opportunities available
- hella alpha

#### MEV Inspect
https://github.com/flashbots/mev-inspect-py
https://docs.flashbots.net/flashbots-data/mev-inspect-py/overview/

**Notes**
point of mev inspect is to pull data from the chain to then allow to search blocks for all transactions and corresponding info -> display each pool of data and then pull the 
- pool addresses
- token addresses
- trace addresses

all of this pulled from just the block number
![[Pasted image 20220206100615.png]]

breakdown:

taking this arbitrage from the tweet that mev alpha leak gave out and then looking at the swaps that compose it

pulling the raw traces from the block itself
from decord inputs to transfers 
transfers to swaps 
swaps to arbitrages 
arbs to the entire database that we're looking at now

trace address: 0020 (where in the trace tree this swap was called)
- after this trace address, it called another function, then called another one, which pulled up the record 1 swap
- this trace is at depth 4 here -> within the call is the overall tree of functions itself

SELECT * from miner_payments WHERE transaction_hash =
^ this displays how the miner got paid

you can either do this thru gas or pay it directly to the miner
- debating whether this is even worth it lol
- 48 eth sent to miner
- net profit of 5 eth for the searcher
![[Pasted image 20220206102106.png]]



#### MEV Research
https://github.com/flashbots/mev-research
https://github.com/flashbots/mev-research/blob/main/topics.md

### MEV in Review
[[Longing feb 2-4 bottom]]
https://www.youtube.com/watch?v=V_wlCeVWMgk

#### Highlights
seems as if this space is insanely competitive, which ruins the oveall good natured philosophy that i always feel like crypto pushes forward. if my end goal is to arb an incoming nft launch, but someone else sees my bot allocating capital already for said purpose, to what lengths will others disclaim and/or hate/shame the bot owner to get their profit

point is that im really curious as to what area of game theory takes place here and what new person in mev could even accomplish at this point
## Ideas
### Flashloan Swaps
**The LION Method**  
  
The LION method breaks down the whole process of creating Flashloans:

1.  PLAN: Pick your arbitrage strategy
2.  OBSERVE: Monitor the Blockchain for arbitrage opportunities
3.  ATTACK: Execute you arbitrage strategy as soon as you spot an opportunity

  
And to do this, you need to automate the whole process with a script. This will require some basic skills:

-   Basic understanding of the Blockchain
-   Basic skills in web programming (backend)
-   Basic skills in Solidity

  
If you don't have some of these skills, and or are not a technical person, I have a training to quickly get you up to speed.
Creating a protocol that offers instant flashloans to users that need to swap large amounts on exchanges that have increased slippage. This would act as a way to create seamless and efficient transactions for anyone trading on independent exchanges.

Use cases:
User wants to swap $5m YFI for ETH on SushiSwap, but there's not enough liquidity in their yfi/eth pool. Slippage is +10%, you're down bad. So, you want to add more liquidity to the pool, but just for you're transaction

Flashbots RPC as well

![[Pasted image 20220310181726.png]]
#### Zaki podcast for DeFi
https://podcasts.apple.com/us/podcast/zero-knowledge/id1326503043?i=1000538456351
