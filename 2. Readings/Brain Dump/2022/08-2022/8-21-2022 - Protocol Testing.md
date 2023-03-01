# Learnings for Today
#readings #resources

## Protocols
### Vesta finance background
https://twitter.com/thedefinvestor/status/1559525451076362242?s=21&t=TPkiR7_obwDfEz9Kl4Hw_A
Users can lock up collateral and issue Vesta's stablecoin [$VST](https://twitter.com/search?q=%24VST&src=cashtag_click), paying only a one-time mint fee. In order to ensure that the protocol will not accrue bad debt, the team implemented a Stability Pool.

However, unlike Liquity, Vesta also allows: -$VST stablecoin minting against multiple collaterals -yield-bearing assets as collateral yield-bearing assets - assets that accrue rewards

Vesta stakes [$GMX](https://twitter.com/search?q=%24GMX&src=cashtag_click) on your behalf and gives you back 80% of the [$GMX](https://twitter.com/search?q=%24GMX&src=cashtag_click) staking rewards in [$ETH](https://twitter.com/search?q=%24ETH&src=cashtag_click).
![[Pasted image 20220821133601.png]]

damn 20% performance fee?
![[Pasted image 20220821133632.png]]

that seems excessive tbh
-a leverage trading interface -an internal DEX aggregator -flexible liquidation -a collateral locking system -$VSTA staking module -more collateral types -multichain expansion

eh seems like they're aiming too high tbh

currently adding things like glp vault and other vaults as well
GLP vault that will allow users to borrow [$VST](https://twitter.com/search?q=%24VST&src=cashtag_click) while earning GLP rewards will be launched soon.

No revenue sharing. Its a governance token, but governance is not yet implemented. Small amounts of it is required to issue new debt, but the team plans to remove this feature and pay the fee through the collateral

honestly doesnt seem like worthwhile protocol to use unless you're alredy earning off gmx/glp fees

### trm labs sanctioning eth wallets
https://twitter.com/bantg/status/1560004104189104129
https://depression2022.substack.com/p/8172022-my-eth-wallet-is-wrongly

 [The Furucombo Hacker](https://etherscan.io/address/0xb624e2b10b84a41687caec94bdd484e48d76b212) transferred ~40K PERP tokens from my address (0x660939b21C0ac3339A98dB9FFBdA74Cd59E07685) with this [transaction](https://etherscan.io/tx/0x7d9405670658222359ea8d1c3398e2736dc406632b24d9b651d3d70fbcc5f806) , swapped all the tokens to ETH and used Tornado Cash to launder the money. I suspect the fact that there’s a direct transfer from my wallet to the hacker’s wallet resulted in the sanction. **But that transfer is the hack itself.**

damn this shit is just fucking sad, going above and beyond like this is pitiful
So basically the web UI is blocked but people can still use AAVE by sending transactions to the blockchains directly. I am not sure how useful blocking the web UI is for sanctioning a wallet. I believe most hackers are able to make direct contract calls since that’s usually how they carry out the hacks. It is true though that for [upgradable proxy contracts](https://docs.openzeppelin.com/upgrades-plugins/1.x/proxies#:~:text=Upgrading%20via%20the%20Proxy%20Pattern&text=The%20key%20concept%20to%20understand,be%20swapped%20by%20another%20contract.) , the DeFi protocols will be able to carry out the sanctions at the smart contract level in the future.

wow so these ppl are just idiots that blocked off the web ui. better option is simply speaking to the blockchains directly

### A deep dive on zk rollups
https://twitter.com/RiftFinance/status/1559914291230384131
https://blog.rift.finance/the-state-of-zk-rollups/

![[Pasted image 20220821134500.png]]

### Starting out with Arbitrum
https://twitter.com/DeFiSurfer808/status/1559888207067635714

okay here bro is explaining arbitrum nitro and odyssey making a return, idk what that is
this article dives into arbitrum and what it is 
https://defisurfer808.substack.com/p/optimistic-arbitrum?sd=pf

this is a how to guide for arbi
https://twitter.com/ethersole/status/1559584539642458112?s=20&t=sP469lSR043rCwSNvlo17A

tokens to watch
[$GMX](https://twitter.com/search?q=%24GMX&src=cashtag_click): 83% · [$DPX](https://twitter.com/search?q=%24DPX&src=cashtag_click): 326% · [$rDPX](https://twitter.com/search?q=%24rDPX&src=cashtag_click): 258% · [$MAGIC](https://twitter.com/search?q=%24MAGIC&src=cashtag_click): 242% · [$TCR](https://twitter.com/search?q=%24TCR&src=cashtag_click): 351% · [$JONES](https://twitter.com/search?q=%24JONES&src=cashtag_click): 302% · [$VSTA](https://twitter.com/search?q=%24VSTA&src=cashtag_click): 491% · [$PLS](https://twitter.com/search?q=%24PLS&src=cashtag_click): 194% · [$UMAMI](https://twitter.com/search?q=%24UMAMI&src=cashtag_click): 158%
https://twitter.com/dLuxGMI/status/1558188471143079936?s=20&t=sP469lSR043rCwSNvlo17A

this is current chain growth
![[Pasted image 20220821135903.png]]


this is an interesting way to map out value here
![[Pasted image 20220821135936.png]]

Here is described as the convex of arbitrum primarily speaking for using tokens as governance on other protocols

[@PlutusDAO_io](https://twitter.com/PlutusDAO_io)
($PLS) has free rein over the
[@arbitrum](https://twitter.com/arbitrum)
eco, being the yield-aggregator of choice fo
[@dopex_io](https://twitter.com/dopex_io)
[@DAOJonesOptions](https://twitter.com/DAOJonesOptions)
and
[@SperaxUSD](https://twitter.com/SperaxUSD)
and working on partnerships w
[@GMX_IO](https://twitter.com/GMX_IO)

![[Pasted image 20220821140116.png]]

umami and jones acts as the yearn finance for arbitrum protocols

## Testnets and Airdrops
### Sei network and their incentivized testnet!
#testnet

https://twitter.com/0xbezzub/status/1561408003777208320?s=20&t=sP469lSR043rCwSNvlo17A

![[Pasted image 20220821140237.png]]
interesting they have an ambassador program too?
https://twitter.com/0xbezzub/status/1558814601583755265?s=20&t=sP469lSR043rCwSNvlo17A

hm what do we have here?
https://trade.vortexprotocol.io/

join sei discord here
https://discord.com/invite/CB89BJNMVE

Go to [https://faucet.egorfine.com](https://t.co/BswqcLdb0C)
for ropsten testnet eth

Next step, go to [https://trade.vortexprotocol.io/bridge](https://t.co/wvZSeyaBZG) Enter quantity of token and enter your Sei address. Confirm all transactions in your wallet and wait 15-20 minutes for approval.

best method for me here is to go thru the vortex steps on a bunch of wallets!!!!
![[Pasted image 20220821140532.png]]

bridge and they make test transactions using the trading platform

### Looking into the zksync ecosystem
#testnet 

https://twitter.com/thedefisaint/status/1560606597792931843?s=21&t=i0fpZygEQOKaj_x7LtI8lw

first up is 1kx protocol
lot of protocols here tbh, not even sure if its worth going thru all of em but might as well check out!

>LPs can deposit only one token on 1kx liquidity pool & can benefit from that by 
>• Earning fees from Spot swap • Fees from margin trading • Interest from borrowers 
>• Fees from Perp trading 
>• Earning 1kx token through revenue distribution

The protocol is still on Testnet • Strategy: Use the protocol & the entire features by being an active user • Airdrop confirmation: Confirmed

LMAOOOO nvm lets get that testnet baggerinoooooo more airdrops pls!

next is MES protocol as well
https://www.mesprotocol.com/

An Order Book DEX on zkSync that offers slick trading experience just like that of CEX The Protocol is still on Testnet & no token yet • Strategy: Trade across the DEX • Airdrop confirmation: Possible Airdrop

then we do mystiko network
The Protocol is still on Testnet Below is a guide on how to use it [https://docs.mystiko.network/mystiko-zk-2-tutorial-effective-since-june-2022…](https://t.co/q2ghBuvDwc) • Strategy: Use Testnet Wallet • Airdrop Confirmation: Possible Airdrop

orbiter finance for briding assets
5/ Orbiter finance

[@Orbiter_Finance](https://twitter.com/Orbiter_Finance)

A Cross Rollup bridge across all L2s, which is among the cheapest bridge No token yet • Strategy: Bridge across various chains including zkSync. • Airdrop Confirmation: Possible Airdrop

haha phezzan protocol as well for trading and adding liquidity
Phezzan Protocol

[@PhezzanProtocol](https://twitter.com/PhezzanProtocol)

An Order Book Perp Derivative Dex that features multi-collateral support & yield earning while trading or providing liquidity. The Protocol is still on Testnet • Strategy: Trade & add liquidity • Airdrop Confirmation: Airdrop Confirmed

for primex, you need to fill out early user form first and then trade on the dex
• Strategy: Trade across the Dex & add liquidity Fill the Early user form provided below to be able to access the Testnet [https://primexfinance.typeform.com/to/UDnZxL8x?typeform-source=primex.finance…](https://t.co/B14n2RUe7W) • Airdrop Confirmation: Airdrop Confirmed
![[Pasted image 20220821141147.png]]


on rubicon finance just swap stables or sum and use the bridge
Rubicon

[@rubicondefi](https://twitter.com/rubicondefi)

An Order Book DEX for L2s which its feature includes: Swap function, Pool and a Bridge (Powered by

[@SocketDotTech](https://twitter.com/SocketDotTech)

) • Strategies: I. Trade, Swap & use the bridge ( Be an active user) II. Add liquidity

nothing too crazy on satis, main point is to just trade on the dex
[http://Sat.is](https://t.co/Ulzy2suDIL)

[@SatisDEX](https://twitter.com/SatisDEX)

A multichain trading DEX The Protocol is still on Testnet, it's already on Arbitrum, Boba, polygon & zkSync • Strategy: Trade across different chains • Airdrop confirmation: Possible Airdrop

Tally Ho

[@tallycash](https://twitter.com/TallyCash)

A Decentralized free, community owned & open-source web3 wallet just like metamask. • Strategy: Be an active wallet user & also use the swap feature. • Airdrop confirmation: Airdrop Confirmed, As the criteria will be based on fair launch.

there's also tally wallet, hmmm do i want to use this or not? maybe use this primarily for zk shit?
https://tally.cash/

biggest one to watch is trustless!
Censorship resistant • Community Owned • Governance minimized The Protocol is still on Testnet • Strategy: I. Get into the discord on "curriculum" & complete the whole assessment starting from Demo - Demo submission

https://twitter.com/TheDeFISaint/status/1560614254532628480?s=20&t=svFIPpjaupQjyIhQnmpYxA

seems to be that they're building a whole lot of the same focuses that i want to see in a protocol's principles
Airdrop Confirmation: Airdrop Confirmed Incentivzing Testnet users, LPs & Long term community supporters TCP will allocate 100M tokens, 65M to the community & 35M to the foundation. This is why it's truly community owned protoco

![[Pasted image 20220821141414.png]]


ZKEX is a dex with low fees, goal here is simply to trade on the dex
ZKEX A multichain order book DEX with low trading fees Testnet Coming Soon • Strategy: Trade across the Dex • Airdrop Confirmation: Airdrop Confirmed Incentivzed Testnet for users

### Canto airdrop and guides
#testnet 
https://twitter.com/ahboyash/status/1560861315178016768
https://twitter.com/0xAndy_Gamer/status/1548287117201010694?s=20&t=QR38kFbLBAmGGsDviLFQDg

a fork of[@Evmosorg](https://twitter.com/EvmosOrg)Canto is built using Tendermint Consensus with an EVM execution layer in via Cosmos SDK. It claims to be a full decentralised chain with no presale, no foundation and no VCs. Read more here: [https://docs.canto.io/overview/about-canto](https://t.co/eVD8o5STv1)

To set up your Metamask: • Network: CANTO • RPC URL: https://canto.evm.chandrastation.com • Chain ID: 7700 • Currency Symbol: CANTO • Block Explorer URL: [https://evm.explorer.canto.io](https://t.co/t0x1yJdueg)
most important setup here^^

![[Pasted image 20220821142028.png]]
okay the bridging process seems like a bit much cant even lie to ya but the site wrecks here in there. 

On your Kelpr wallet, select "IBC Transfer - Send tokens over IBC" • Select New IBC Transfer > Canto Mainnet > Bridge assets • Head to [https://convert.canto.io](https://t.co/07CF5FQUzm) and convert the Cosmos assets to the Canto EVM Chain

 could also just bridge directly form the keplr wallet instead
 ![[Pasted image 20220821142111.png]]

to bridge off of canto
• Convert Canto EVM assets to Canto • Connect to [https://spacestation.zone](https://t.co/Ich3gbZ7Fj) to get the Gravity wallet address • Bridge from Canto > Gravity • Transfer from Gravity to Osmosis
https://twitter.com/Meez_Tweets/status/1558559878389678084?s=20&t=QR38kFbLBAmGGsDviLFQDg

current tools
Tools a) Chain explorer: [https://evm.explorer.canto.io](https://t.co/t0x1yJdueg) ![🔍]( b) Guides: [https://docs.canto.io/overview/about-canto…](https://t.co/eVD8o5STv1) ![📚]( c) Account: [https://account.canto.io](https://t.co/A3nFogdPmc) 

current dapps are as follows
Dapps 
a) DEXs/ Farms • [https://convert.canto.io](https://t.co/07CF5FQUzm) •
[@SlingshotCrypto](https://twitter.com/SlingshotCrypto)
[@forteswap](https://twitter.com/forteswap)
b) Lending • [https://lending.canto.io](https://t.co/9SSBSFDIlb) 
c) Memes/ misc •
[@CantoInu](https://twitter.com/CantoInu)
[@CantoPunks_](https://twitter.com/CantoPunks_)
[@CantoReserve](https://twitter.com/CantoReserve)
[@CantoPepeCoin](https://twitter.com/CantoPepeCoin)
d) Staking • [https://staking.canto.io](https://t.co/mo8qEceMP7) 3) LP • [https://lp.canto.io](https://t.co/9d1RAxzTFm)

TG groups • Canto apes: [https://t.me/cantoapesecosystem…](https://t.co/33G3wFjx6l) • Canto Cult:
https://t.me/cantocult

### Future of Optimism

https://twitter.com/kelvinfichter/status/1553323106030260224?s=20&t=QR38kFbLBAmGGsDviLFQDg

and an overview of op bedrock!!!
https://dev.optimism.io/introducing-optimism-bedrock/

hahahah this is all i needed to do for airdrop wtf!!!
https://canto.mirror.xyz/kSrSQcHROw41HlS0M3YU_Yj1ljRarGXChrKbE0Z7BJc
![[Pasted image 20220821141910.png]]


# Things that happened
## things that happened
benddao got mf rugged
https://twitter.com/CirrusNFT/status/1561383476137365504?s=20&t=utbPix6W3nAZGdVDR4v6IA

![[Pasted image 20220821134647.png]]

https://twitter.com/CoinDesk/status/1561367462846894089?s=20&t=utbPix6W3nAZGdVDR4v6IA
the protest in netherlands occurred, great thing to happen in the community

breaking down current decentralization
https://twitter.com/bantg/status/1561385167868010498?s=20&t=utbPix6W3nAZGdVDR4v6IA

![[Pasted image 20220821135006.png]]
