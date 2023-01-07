# Case Studies for Yearn's Vaults
#defi #readings #notion 

## Background

Primary article for measuring risk: https://medium.com/iearn/measuring-risk-for-defi-yield-strategies-b53f62b83b92

Recent case study on Lido stETH: https://medium.com/iearn/yearn-strategies-case-study-lido-staked-eth-d21b2a57f79c

## Measuring risk for DeFi yield strategies

Article link: https://medium.com/iearn/measuring-risk-for-defi-yield-strategies-b53f62b83b92

This article covers key areas of how DeFi natives have dealt with risks in farming pools and how new degens can learn from their survival. Marco displays how retail investors can learn from Yearn specifically with their [Risk Score Framework](https://docs.yearn.finance/resources/risks/risk-score). 
The below screenshot explains the dimensions they include for securing each of their vaults. Highlights that I view as important include Team Knowledge and TVL Impact. 

The former because of how necessary it can be to have multiple eyes on a specific strategy, especially in the off-chance that lead developers aren't available for when an issue arises. This can also translate to non-technical parties explaining what a vault is doing to the community, therefore benefitting from the overall increase of attention a vault receives.

The latter is more so from a financial risk standpoint and demonstrates how they can alleviate extensive risk by not relying too much on a single strategy. Yield can only do so much for a massive portfolio like theirs and by decreasing TVL impact, Yearn would be able to survive further windfalls that might occur.
![](Pasted%20image%2020230107165931.png)

Prior to examining the strategy itself, the author explains the key risks in DeFi that every user should be aware of. Main ones for us as the reader to understand are Technological (smart contract bugs/exploits) & Oracles (relying on fault price oracle feeds) since these are the most common areas of risk that negatively impacts a large amount of DeFi pools.

### Compound Flashmint Folding

For this case study, the author views "GenLevCompV3" which holds $30m in a Yearn DAI vault (the user would deposit the stablecoin DAI into this vault to earn yield through this strategy). 

The analytics for this strategy can be viewed on Yearn Watch, which places all relevant information on each vault for users to check. The below displays stats such as previous Harvests (when yield rewards are claimed), Assets within the strategy, and total gains & losses.
https://yearn.watch/vault/0xdA816459F1AB5631232FE5e97a05BBBb94970c95/0x1676055fE954EE6fc388F9096210E5EbE0A9070c
![](Pasted%20image%2020230107174640.png)

The basic understanding for this strategy can be understood as:
1. Supply DAI into Compound
2. Borrow DAI back from Compound using your deposit as collateral
3. Continue this process until you've leveraged up your final position to your desired limit
4. Sell rewards as they accrue for more DAI and run the same strategy again

Where Yearn innovates here is through their Flashloan & Flashmint optimization. To better understand the concept of Flash Minting, the following resources are good places to start:
- the initial flashmint docs from MakerDAO provides a first principles explanation on how this module works - https://docs.makerdao.com/smart-contract-modules/flash-mint-module
- this repository by Fifikobayashi provided an interesting background on how flashloans can interact with multiple protocols - https://github.com/fifikobayashi/FlashMintArbitrage
	- in this case by arbitraging ETH prices between Kyber and Uniswap (two standalone Decentralized Exchanges (DEXs) on Ethereum).
	- an example tx of how this arbitrage would look can be found here: https://ropsten.etherscan.io/tx/0xcd7df11739852523b70419f6868d2c43fd57e984c160911d5da962d3d2e2db14

Marco explains this strategy as the following:
1. Flashmint DAI from MakerDAO
2. Supply deposited DAI and the newly flashminted DAI to Compound
3. Borrow DAI using the deposited DAI as collateral (no looping these steps here)
4. Repay the overall Flashmint used for the DAI; explained as a combination of the mint and a flashloan to repay the mint
5. Sell all COMP rewards for DAI and reinvest back into Flashminting DAI

What's revealed here is that both of these results have the same result but allow for decreasing risk instead of 