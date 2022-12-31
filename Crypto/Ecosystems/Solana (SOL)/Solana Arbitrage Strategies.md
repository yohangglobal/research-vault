# Jupiter Arbitrages
#strategies #ggportfolio #gg-trades 

## initial plan
going to look to adapt these simple strategies to the types of arbs presented on Jupiter

**USDC/DAI on ForDeX and DAI/USDC on Coinbase Pro**

DAI/USDC price on Coinbase Pro - 0.98

USDC/DAI price on ForDeX - 0.9998  

Arbitrage trade flow: a) Buy 1.02 DAI for 1 USDC on Coinbase Pro

b) Move DAI from Coinbase Pro to ForDeX

c) Buy 1.02 USDC for 1.02 DAI on ForDeX

1 USDC = 0.999986 (Mercurial x Lifinity)
1 UST = 1.0000028

Basically i buy 49.998362 UST with 50 USDC


`So on Jupiter i can swap 50 USDC for either 49.99 UST at max 
`or swap 50 USDC for 44.26 UST thru Sencha x Mercurial

`I can swap 50 UST for 48.14 USDC thru Orca x Saros
`or swap 50 UST for 50.001431 USDC on Saber

![[Pasted image 20220405225109.png]]

By the following the above path of trades, an arbitrageur started with 1 USDC and ended up with 1.02 USDC at the end of two trades, capturing a price spread of  2% with zero risk.

These are just a couple of examples of possible arbitrage. It is probably safe to assume that such arbitrage opportunities will disappear at scale, but for the near future, there is definitely profits to be made for the enterprising trader, in a fairly capital efficient manner.