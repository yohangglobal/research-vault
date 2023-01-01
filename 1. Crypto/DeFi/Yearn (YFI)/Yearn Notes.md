## yearn docerinos!
https://docs.yearn.finance/getting-started/intro

## Yearns rebrand:
https://medium.com/iearn/rebranding-yearn-consistency-from-chaos-32204f2a214d
![[Pasted image 20220821124220.png]]
these are their guided statements what a great way to view business and the purpose behind a company

love that they are expanding the logo even more by embracing the colorfulness of defi. going beyond blue white and black is perfect!![[Pasted image 20220821124638.png]]

going with new fote with purpose Aeonik Fono and MOno are dope
top tier post on creative background behind yearn, really explains opening up and creating a newfound reality for ppl to be a part of. also pretty pictures and cool merch

## Where does the on chain yield come from?
https://medium.com/iearn/where-does-on-chain-yield-come-from-ff9a931fad90

great points here being made that the best part of crypto yield is that which is paid for completing services. you pay btc for a permissionless money ledger. eth for creating secure services providing financial products. chainlink for using the largest oracle provider for accurate prices

![[Pasted image 20220821125440.png]]

curve and other tokens take this a step further by providing insurance and liquidity for example with other tokens thru derivative assets. example here was cvxCRV making veCRV tradeable for curve lockers

goes on to explain how the large majority of protocols that have liq mining programs without true service usability will eventually dry out. 

haha great questions everyone should be asking themselves when looking into a new protocol. be as skeptical as possible and question what is occuring with the tokens i receive. if my goal is to dump it tho i mean shit!

>Why do we need another Dex? What does this service does that other doesn’t? 
>Why would someone unstake liquidity from Uniswap/Sushiswap/Curve and put it in HentaiSwap? How much fees is this DEX generating? How close is it to 420%? 
>Take a look at all other swap protocols: how much they pay for the same pairs when they have a lot of liquidity to compare fees/returns? 
>Why should I stake $HENTAI? Why is someone paying me to hold this token? Seems like they want me to buy this token to make the price go up for previous bag holders to profit, but what can I do with it besides just selling back staking profits to the market? 
>And finally: How many $HENTAI tokens the team mint for themselves in order to sell when market speculation is making it worth something in the market? Who is gonna lose money when they do?

main example here is a user looking to swap his tokens for usd and the protocol charging .5% for swap fees. very understandable
yeah you ask for a service to be provided and you pay accordingly for that service to work correctly!

Yearn enters here by charging fees on top of yield profits, which is a positive sum scenario

i deposit my curve steth into yearn and get paid from the higher yields their strategy provides, then pay them from the yields received for providing said service.

this is key for providing transparent and accessible strategies!
love this breakdown and i think it explains very well what we can gather from yearn as a protocol.

## What are yearn's vaults and strategies
https://medium.com/iearn/yearn-finance-explained-what-are-vaults-and-strategies-96970560432

![[Pasted image 20220821130806.png]]

the open ended service allows for other protocols to be built on top of yearn, just like abracadabra!

-   **The token you deposit in a yVault is the token you’ll receive yield**, always automatically compounded into the yVault
-   **A yVault may have many active strategies at the same time**. A yVault may change its strategies capital allocation when it deems necessary
-   Unlike many other yield aggregators, **there are no deposit/withdrawal fees** charged to the user (BIG POINT)
-   **yVaults tokens implement the ERC20 standard**, this means that they can be easily moved between wallets and markets and can be used by any app that communicates with this standard (like decentralized exchanges).

you deposit your usdc into the usdc vault and receive yvUsdc that can be used to stake back into the protocol or use on other protocols as collateral

to add to strategies this is their vetting process
https://docs.yearn.finance/developers/v2/getting-started#overview-of-our-vetting-process
![[Pasted image 20220821131027.png]]
-   Up to 10% of the generated yield fees by a specific strategy (performance fee) goes to the strategist
-   10% of the generated yield fees by all strategies (performance fee) goes to the Yearn DAO treasury.
-   Over the year 2% of the vault’s total assets are taken as fees which go to Yearn to pay for expenses like gas, developer grants, and other services.

SHEESH 10% goes back to em??? then 10% of all yield fees by all strategies goes back to yearn treasury. 2% of vaults total assets are taken as fees for gas, grants and other services

diving into strategies now, love this image from finematics!
![[Pasted image 20220821131155.png]]

oh wow im getting a bit confused here LMAO this is actually very interesting and i clearly need to watch this video 
https://finematics.com/yearn-vaults-eth-vault-explained/

basically breaks down as:
-   When a user deposits ETH the ETH is then lent at MakerDAO as collateral
-   The collateral is used to borrow DAI
-   The borrowed DAI is deposited into the DAI yVault

from here, main questions are what happens within the vaults and how does yearn guarantee the safety of strategies
- for one, the fees come from the harvest function that is called when a user wants to rebalance a strategy and take profits
- they look at yearn watch for safety metrics
https://yearn.watch/

#### Healthchecks
The healthchecks have been added since v0.4.2 for the Yearn's strategies in order to ensure that they are working properly. The healthchecks are automatically triggered on harvest if the doHealthCheck parameter is enabled, and if a valid address for this check is set. The strategies missing one of theses parameters will be displayed bellow.

Based on the Total Value Locked (TVL) in the strategy, a Risk score, from 5 (most risky) to 1 (least risky), is computed.

one example strategy here being that the Curve sUSD yvault supplies yvcurve-susd to convex to earn crv and cvx. then these tokens are harvested and sold for more yvCurve-sUSD. this is then deposited back into the strategy

![[Pasted image 20220821131820.png]]

here they're expecting a 87k return on a vault with 994k in it. from here they would get 10% of fees sent back to strategist!

here are their current restraints:
-   Vault funds should go “up only” and not down
-   Avoid Impermanent Loss (e.g. don’t provide YFI/ETH liquidity in a liquidity pool)
-   Users should be able to withdraw at any time (so the strategy can’t timelock all vault funds, only a small fraction)
-   Use only protocols with a proven track record and well-understood, immutable contracts

they are programmed in the following:
#### Building Strategies
-   **yVaults** are programmed in [**Vyper**](https://vyper.readthedocs.io/en/stable/)
-   **Strategies** are programmed in [**Solidity**](https://docs.soliditylang.org/en/v0.8.11/)

-   Knowledge about the blockchain ecosystem you’ll deploy in, which can be acquired by doing in-depth research of tokenomics and documentation for all tokens used in the strategy itself.
-   Solidity programming knowledge similar to [completing Level 4 on CryptoZombies](https://cryptozombies.io/)
-   Know how to get around [git](https://git-scm.com/), [eth-brownie](https://eth-brownie.readthedocs.io/en/stable/), and [ganache](https://trufflesuite.com/ganache/).
-   After understanding the basics of the above tools you are ready to [copy our strategy template](https://github.com/yearn/brownie-strategy-mix)! The functions you should start changing in this template in order to build with your own first strategy are _prepareReturn_, _adjustPosition_, and _liquidatePositon._

oh damn this is really all it takes to create a strategy? would basically be tasked with learning about the above programs and strategy templates, then applying them to another protocol

-   [yVaults descriptions](https://vaults.yearn.finance/)
-   [yVault/ Docs](https://docs.yearn.finance/getting-started/products/yvaults/overview)
-   [Become a mighty strategist](https://www.youtube.com/watch?v=NVR3teJw0Y0)
-   [External video/article from Finematics about yVaults](https://finematics.com/yearn-vaults-eth-vault-explained/)
-   [Partners building with yVaults](https://medium.com/iearn/yearn-partners-building-with-yvaults-4cd042ea092)
-   [Hacking with Yearn](https://docs.yearn.finance/developers/v2/hacking-with-yearn)
-   [Additional Resources from Yearn](https://docs.yearn.finance/developers/v2/additional-resources)

best resources for this!
