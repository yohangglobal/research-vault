# Katana Asset management
#solana #defi #notion 
## What is Katana?
# Katana Solana DeFi Katana 
- The Yield Generation Protocol for Solana - Winner of the 2021 Ignition Hackaton. 

[Katana]([https://app.katana.so/](https://app.katana.so/ "https://app.katana.so/")) 
Katana is a DeFi dApp on the solana blockchain that enables users to generate yield though programatic strategies. The strategies currently employed by Katana vaults are “Covered Calls”, which are common in the options world of traditional trading. Funds are locked up for a week (?) and used to purchase covered call options on PsyOptions at strike prices Katana doesn’t expect will happen. From the docs.

```
VAULT STRATEGY
This vault accepts ETH deposits and earns yield via an automated ETH covered call strategy. The strategy works by first depositing the underlying ETH on PsyOptions and minting out-of-the-money ETH calls in return. The vault then sells these call options on the corresponding Serum market, earning the option premium as initial yield. If the price of ETH is below the strike price at the time of expiry, the vault earns the full value of the options it sold and can repeat the strategy, compounding its ETH over time
```

What are the risks? [Covered Calls]([https://www.investopedia.com/terms/c/coveredcall.asp](https://www.investopedia.com/terms/c/coveredcall.asp "https://www.investopedia.com/terms/c/coveredcall.asp")) are generally a low risk way of getting passive income on assets you already own. The biggest risk is that an option you sell will be exercised and your asset will be sold at the strike price; you will lose any difference between strike and new higher price. From the docs:

```
RISK
The vault may incur a loss if the price of ETH is above the strike price of the call options at the time of expiry. If so, the options are deemed to have expired in the money and can be exercised for the ETH locked by the vault, resulting in a potential loss in ETH terms for the period. Strike prices are chosen such that these events are exceedingly rare.
```

Vaults will show the type of asset, the TVL, APY, and any current position you are holding. 
[image:049351F3-9BA2-4898-AC34-559FE838AE94-9593-0001125285336A7E/78AD3FD8-5D0C-4A99-A423-7969FDDBCDE2.png] 

New vaults will not have a APY as there is no data to draw conclusions from.  
[image:6253DB49-8A35-4B9E-9BF7-EDA89CFE813D-9593-000112548E54688D/ED99ADBD-6DB1-41E2-AFB1-586F77FAE4CE.png] 

At the time of this writing the ETH Covered calls vault is returning 33% APY weekly, compounding. To take advantage of ETH vault, you’ll need to get ETH on Solana.

There are two ways to get it, buying it with USDC (or any other swap route), or bridging it through the Solana wormhole. [

Wormhole Token Bridge]([https://wormholebridge.com/#/transfer](https://wormholebridge.com/#/transfer "https://wormholebridge.com/#/transfer")) 

Once bridged, you’ll have `Wrapped ETH` and then you’ll need to swap that to get `ETH`, I’m not sure how `ETH` via the bridge, or how anyone else is getting it but the Katana docs suggest using a choice of DEX’s. I used Orca to swap from `whETH` to `ETH` [image:449494B9-6DF1-41F5-A327-A3C4AE9E7283-9593-000112A3EB8648ED/02BD5A64-5D25-4209-AF5B-D75326C2A158.png] 

Once traded, you’ll have ETH in your Solana wallet and will be able to deposit that into Katana.