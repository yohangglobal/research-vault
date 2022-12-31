# Reviewing Yield Aggregators
#research #defi 

I had originally had an interest in finding new DeFi related papers that were either heavily cited or created new ideas for understanding yield strategies. When searching topics such as "Yearn finance" on Connected Papers, I was able to find a long list of references for both summary articles as well as in-depth workings behind similar protocols. My primary goal here is to see how this paper evolved since its publishing date in 2021 and whether their findings are still relevant to DeFi today

Search:
https://www.connectedpapers.com/search?q=yearn%20finance
https://arxiv.org/abs/2105.13891

## Pdf file 
![](2105.13891.pdf)


## Notes
This paper is from London College and represented at the 2022 IEEE International Conference on Blockchain and Cryptocurrency (ICBC) by the authors [Simon Cousaert](https://www.semanticscholar.org/author/Simon-Cousaert/2058152681), [Jiahua Xu](https://www.semanticscholar.org/author/Jiahua-Xu/46372373), [T. Matsu](https://www.semanticscholar.org/author/T.-Matsui/17911302) who have backgrounds in Computing & Blockchain Technologies.

My reminder to myself when referencing various academic papers is usually the terms used for both titling and describing the paper itself. In this case, the term Systemization of Knowledge or SoK can viewed as a compilation of acquired data and a summary of a defined concept. These focus on general frameworks and how to assess certain strategies or specific topics within a broader category. 

From this example, the paper applies this method of thinking to start with fundamentals of yield farming, continues into types of yield and strategies using said yield types, then creates their own simulations for yield farming performance through the following four aggregators:
- Idle finance
- Pickle finance 
- Harvest
- Yearn Finance (personal favorite and relative)

This xujiahuayz girl is actually pretty cool, her GitHub page has some great insights to projects she's helped analyze as well as key papers to read about AMMs and DeFi Protocols.
https://github.com/xujiahuayz

## Summary

### Introduction
Interesting standout here is that DeFi protocols held $600m in assets back in March 2020 (will use Defillama to fact check and then compare the current billion or so held now). Then continues to describe how these same protocols have reached $100b on just Eth during November 2021 (pico top). This article was written March 2022 so makes sense for this to be a lookback prior to the complete collapse of DeFi.

The team is familiar with common terms like defi stack and money legos for combine the different features of various protocols for greater yield. Plug and play mentality is still used often for lending, dexes and yield services. 

### Diagrams & Strategies

So catching up from the previous reading I've seen helpful diagrams that display yield farming processes and how to describe each of these functions from the perspective of a user deploying assets.

![](Pasted%20image%2020221202143906.png)

This example from Figure 2 on Page 3 will be a great reference to comprehend how to describe each moving part of a yield farm. 

Basically viewing that deposited assets will be tailored to collateral deposits onto platforms like Aave and then deployed to earn further yield (similar to leveraged borrows where an asset is looped from (deposit Usdc->borrow eth->sell for Usdc->deposit again->continued) and then profited on from the increased yield earned). All this occurs during Phase 2 which then allows for yields to be claimed and sent back to user or reinvested into the strategy. 

Best help for this would be learning from Yearn docs and understanding their many Vaults. Important note here is that when a user makes a large withdrawal, sometimes the farms/vaults will have to be rescinded and loans get repaid. This way there's enough liquid funds for the user to receive back for their LP tokens.

"A critical aspect in this stage is collateral management to avoid liquidation (see V-B1b) of deposited assets. The yield aggregator manages the collateral risk level by directing the f low of funds between smart contracts used in Phase 0 and Phase 1."

This explains the inherent risk, mostly that with leveraged borrows, a user is susceptible to increased risk the more loops that occur.

![](Pasted%20image%2020221202150937.png)

Another interesting standpoint on page 4 are the parameters that the researchers set in advance for how to create the simulation. Keynotes were 1% of protocol assets for funds, 0.01 gov tokens to users per day, 80% collateral factors and borrow apys at 10%, fixed exchange fee of 5% for AMMs.

These are vastly different from various protocols primarily in borrow APYs and exchange fees, but the collateral factor is relatively similar to the riskier platforms that allow high collateralization. From there, we can view each yield aggr example in Figure 4 and how these parameters would affect the protocol itself.

The above strategies work like so:
- deploy stables to either
	- lend/borrow/provide liquidity
- stables become interest-bearing assets or LP tokens
- user receives the interest earned from lending assets or borrowing against the previous token
- user earns trading fees from providing liquidity
- profit :)

Important to recognize here that t=0 is initial starting time of simulation and as time passes on, interest will accrue at a steady rate (10% APY).

#### Strategies
These are defined as simplified strategies based on deploying capital and earning yield on deposited assets.

**Strategy 1**
Deposit into lending protocol -> earn supply interest in native tokens -> withdraw deposits with token rewards

**Strategy 2**
Deposit into lending protocol -> loop the deposited assets by borrowing against them and then depositing the newly borrowed assets -> native/governance token rewards are used to swap back into the borrowed assets to repay the loan

**Strategy 3**
Deposit assets into liquidity pools for DEXs/AMMs and receive Liquidity Provider (LP) tokens in return -> acquire rewards to these LP tokens for supplying liquidity and withdraw when necessary

### Assumptions, Mechanisms, & Volume Changes

#### Assumptions
Once listing these Strategies throughout page 3-4, the writers explain what requirements must be set in place prior to demonstrating their solutions. They take various routes in their model to avoid any additional restrictions, including the following:
1. No transaction costs
2. Yield aggregator value is measured in DAI (stablecoin) and each value is set at W0 = 1.
3. This aggregator supplies all funds to either lending platforms or AMMs, making up only 1% of the platform's TVL.
4. This platform distributes yield paid out in 0.01 governance token/day
	1. Half of the lending platform's tokens go to lenders, other half goes to borrowers.
	2. AMMs will have proportionate rewards to their deposits.
5. Governance token price remains constant.
6. Lending platforms have fixed borrow APY of 10% with collateralization limits at 80%  (depositors can take 0.8 DAI's worth of their loan). This is common for a few protocols however more of them have begun reducing their collateral factors to decrease risk.
7. AMMs have exchange fee of 5%, charged by retaining 5% of each pool similar to a Uniswap pool.

#### Mechanisms
One interesting standpoint the writers focus on is developing their simulated environment with interest-DAI increasing in value relative to how much time has passed. They explain that losses only occur under extreme market conditions regarding undercollateralization of assets. The Wt variable for the value of the yield aggregator itself increases with the lending APY and whether the governance token price increases.

When explaining their outlook on Leveraged Borrows (pg. 5) we start to see a wider exploration of the inner workings/strategies of DeFi protocols and how users create loops/spirals to increase their potential rewards. For their example, at t=0 the aggregator will deposit 1 DAI and borrow against the deposit at 70% (1 DAI -> 0.7 DAI), then re-deposit these borrowed funds as collateral to borrow again. This same process has led to both the rise and fall of many protocols, primarily due to governance tokens decreasing in value which we have seen more often than not within the DeFi industry.

For Liquidity Pools, the authors describe the aggregator as depositing 1 DAI into a DAI-ETH pool, which then sends a DAI-ETH LP token back to the aggregator. They now own 1% of the supply for this LP token which will remain at 1% according to liquidity provision and withdrawals canceling out. This is subject to relatively no risk since the previous Assumptions (2 and 7) clarify that DAI and ETH have equal value within the pool (exactly 50% DAI and 50% ETH). 

#### Trading Volumes
Volumes for the AMM are measured in DAI and follow these Scenarios:
- Scenario i
	- Buy, Sell ETH - 0, 0 trading volume
	- No volume, only governance token reward
- Scenario ii
	- Buy, Sell ETH - 45, 55 trading volume
	- Larger amount of sells and lower ETH price which leads to less yield
- Scenario iii
	- Buy, Sell ETH - 50, 50 trading volume
	- Equal volume as (i) but with added trading fee for more yield
- Scenario iv
	- Buy, Sell ETH - 55, 45 trading volume
	- Higher demand in ETH drives up price, more yield

Following this they also explain how trading volume is spread out evenly across each simulation. Each Scenario (the various simulation periods) is used to determine what yield the aggregator receives depending on trading volumes. At Scenario i or the blue line (0, 0), they only receive the governance token reward. With added trading volume for Scenario (iii) this displays that the higher yield comes from the 5% trading fee.

![](Pasted%20image%2020221221131251.png)

They go on to explain each of these Scenarios as various market movements that can occur when interacting with AMMs, for instance when the liquidity for a specific asset in a pool dries up, making it more difficult for users to withdraw their funds in the desired asset. Their reasoning for the decreased yield is that users would have to offset the value loss of the asset since the fee revenue and governance token reward would not be enough. The opposite Scenario iv applies in the same manner with a rise in the pool's value as more people are buying ETH versus selling.

The risks within this method include common factors such as high volatility and random bouts of trading activity.

### DeFi Yield Aggregators

When understanding the purpose and use cases of yield aggregators, we can view their current TVL according to the past couple years of data and how users have been deploying capital on Ethereum. 

To truly understand the outlook of this paper, we should first consider that the data acquired comes from the peak/end of the previous bull run. Prices and TVL had reached enormous heights, which is viewable here as Yearn Finance held nearly $6bn in assets by the end of 2021. Compare this data to now, Yearn only manages $333m in assets on Ethereum (https://defillama.com/protocol/yearn-finance).
![](Pasted%20image%2020221222092258.png)

The next diagram they use is Table 1. This represents the current strategies available on each platform. Key areas to observe are that Harvest & Yearn Finance have the largest amount of Pools, at 53 and 50 respectively. Yearn has the most token holders (44,484), the largest TVL (5.548bn) and the highest Market Cap (MCap) (1.156bn). 

Most interesting of these combinations is that there seems to be a direct correlation between TVL, # of pools, and expansion of strategies since Yearn covers all baskets except for pools with multiple assets. Combine this with their ability to perform leveraged borrows and the large difference between other platforms becomes more evident.
![](Pasted%20image%2020221222093036.png)

The remainder of this section elaborates on the above Table with an explanation of each protocol's Strategies, Return for Users, & Protocol Fees.

#### Idle Finance
Background: Idle launched in August 2019 and allocates interest-bearing tokens, very similar to the Abracadabra model of putting interest-bearing tokens like yvUSDC to use as collateral.
1) Focus is on single-asset pools sent to different lending protocols
	1) Uses Compound, Fulcrum, Aave, DyDx, & Maker.
	2) Best Yield allocations searches for the best interest rates.
	3) Risk Adjusted allocations change according to the highest risk-return score, based on the level of risk for each lending platform.
2) Return is currently determined by IdleTokens being used as LP tokens to pay out ownership of the asset pool, and IDLE governance tokens.
3) There's a 10% performance fee per generated yield.

#### Pickle Finance
Background: Pickle launched in September 2020 and offers Pickle Jars (pJar) and Pickle Farms. Jars are yield farms represented by pTokens that earn returns on users' funds, Farms are where users earn PICKLE governance tokens through liquidity mining pools.
1) Two different types of yield strategies are used, where pJar 0.00 operates around Curve Finance using CRV rewards and pJar 0.99 operates around LP tokens from Uniswap and Sushiswap and generating yield from trading fees.
2) Returns are determined by liquidity in AMM pools, other liquidity mining programs, and the additional yield from earned PICKLE tokens.
3) There's a 20% performance fee on generated yield.

#### Harvest Finance

### Author's Findings
