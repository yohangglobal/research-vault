# Simple Arbitrage
#dev #mev 

Source: https://github.com/flashbots/simple-arbitrage

This repository contains a simple, mechanical system for discovering, evaluating, rating, and submitting arbitrage opportunities to the Flashbots bundle endpoint. This script is very unlikely to be profitable, as many users have access to it, and it is targeting well-known Ethereum opportunities.

We hope you will use this repository as an example of how to integrate Flashbots into your own Flashbot searcher (bot). For more information, see the [Flashbots Searcher FAQ](https://docs.flashbots.net/flashbots-auction/searchers/faq)

Environment Variables
=====================
- **ETHEREUM_RPC_URL** - Ethereum RPC endpoint. Can not be the same as FLASHBOTS_RPC_URL
- **PRIVATE_KEY** - Private key for the Ethereum EOA that will be submitting Flashbots Ethereum transactions
- **FLASHBOTS_RELAY_SIGNING_KEY** _[Optional, default: random]_ - Flashbots submissions require an Ethereum private key to sign transaction payloads. This newly-created account does not need to hold any funds or correlate to any on-chain activity, it just needs to be used across multiple Flashbots RPC requests to identify requests related to same searcher. Please see https://docs.flashbots.net/flashbots-auction/searchers/faq#do-i-need-authentication-to-access-the-flashbots-relay
- **HEALTHCHECK_URL** _[Optional]_ - Health check URL, hit only after successfully submitting a bundle.
- **MINER_REWARD_PERCENTAGE** _[Optional, default 80]_ - 0 -> 100, what percentage of overall profitability to send to miner.

Usage
======================
1. Generate a new bot wallet address and extract the private key into a raw 32-byte format.
2. Deploy the included BundleExecutor.sol to Ethereum, from a secured account, with the address of the newly created wallet as the constructor argument
3. Transfer WETH to the newly deployed BundleExecutor

_It is important to keep both the bot wallet private key and bundleExecutor owner private key secure. The bot wallet attempts to not lose WETH inside an arbitrage, but a malicious user would be able to drain the contract._

```
$ npm install
$ PRIVATE_KEY=__PRIVATE_KEY_FROM_ABOVE__ \
    BUNDLE_EXECUTOR_ADDRESS=__DEPLOYED_ADDRESS_FROM_ABOVE__ \
    FLASHBOTS_RELAY_SIGNING_KEY=__RANDOM_ETHEREUM_PRIVATE_KEY__ \
      npm run start
```

## Arbitrage.ts
```
```import * as _ from "lodash";

import { BigNumber, Contract, Wallet } from "ethers";

import { FlashbotsBundleProvider } from "@flashbots/ethers-provider-bundle";

import { WETH_ADDRESS } from "./addresses";

import { EthMarket } from "./EthMarket";

import { ETHER, bigNumberToDecimal } from "./utils";

export interface CrossedMarketDetails {

profit: BigNumber,

volume: BigNumber,

tokenAddress: string,

buyFromMarket: EthMarket,

sellToMarket: EthMarket,

}

export type MarketsByToken = { [tokenAddress: string]: Array<EthMarket> }

// TODO: implement binary search (assuming linear/exponential global maximum profitability)

const TEST_VOLUMES = [

ETHER.div(100),

ETHER.div(10),

ETHER.div(6),

ETHER.div(4),

ETHER.div(2),

ETHER.div(1),

ETHER.mul(2),

ETHER.mul(5),

ETHER.mul(10),

]

export function getBestCrossedMarket(crossedMarkets: Array<EthMarket>[], tokenAddress: string): CrossedMarketDetails | undefined {

let bestCrossedMarket: CrossedMarketDetails | undefined = undefined;

for (const crossedMarket of crossedMarkets) {

const sellToMarket = crossedMarket[0]

const buyFromMarket = crossedMarket[1]

for (const size of TEST_VOLUMES) {

const tokensOutFromBuyingSize = buyFromMarket.getTokensOut(WETH_ADDRESS, tokenAddress, size);

const proceedsFromSellingTokens = sellToMarket.getTokensOut(tokenAddress, WETH_ADDRESS, tokensOutFromBuyingSize)

const profit = proceedsFromSellingTokens.sub(size);

if (bestCrossedMarket !== undefined && profit.lt(bestCrossedMarket.profit)) {

// If the next size up lost value, meet halfway. TODO: replace with real binary search

const trySize = size.add(bestCrossedMarket.volume).div(2)

const tryTokensOutFromBuyingSize = buyFromMarket.getTokensOut(WETH_ADDRESS, tokenAddress, trySize);

const tryProceedsFromSellingTokens = sellToMarket.getTokensOut(tokenAddress, WETH_ADDRESS, tryTokensOutFromBuyingSize)

const tryProfit = tryProceedsFromSellingTokens.sub(trySize);

if (tryProfit.gt(bestCrossedMarket.profit)) {

bestCrossedMarket = {

volume: trySize,

profit: tryProfit,

tokenAddress,

sellToMarket,

buyFromMarket

}

}

break;

}

bestCrossedMarket = {

volume: size,

profit: profit,

tokenAddress,

sellToMarket,

buyFromMarket

}

}

}

return bestCrossedMarket;

}

export class Arbitrage {

private flashbotsProvider: FlashbotsBundleProvider;

private bundleExecutorContract: Contract;

private executorWallet: Wallet;

constructor(executorWallet: Wallet, flashbotsProvider: FlashbotsBundleProvider, bundleExecutorContract: Contract) {

this.executorWallet = executorWallet;

this.flashbotsProvider = flashbotsProvider;

this.bundleExecutorContract = bundleExecutorContract;

}

static printCrossedMarket(crossedMarket: CrossedMarketDetails): void {

const buyTokens = crossedMarket.buyFromMarket.tokens

const sellTokens = crossedMarket.sellToMarket.tokens

console.log(

`Profit: ${bigNumberToDecimal(crossedMarket.profit)} Volume: ${bigNumberToDecimal(crossedMarket.volume)}\n` +

`${crossedMarket.buyFromMarket.protocol} (${crossedMarket.buyFromMarket.marketAddress})\n` +

` ${buyTokens[0]} => ${buyTokens[1]}\n` +

`${crossedMarket.sellToMarket.protocol} (${crossedMarket.sellToMarket.marketAddress})\n` +

` ${sellTokens[0]} => ${sellTokens[1]}\n` +

`\n`

)

}

async evaluateMarkets(marketsByToken: MarketsByToken): Promise<Array<CrossedMarketDetails>> {

const bestCrossedMarkets = new Array<CrossedMarketDetails>()

for (const tokenAddress in marketsByToken) {

const markets = marketsByToken[tokenAddress]

const pricedMarkets = _.map(markets, (ethMarket: EthMarket) => {

return {

ethMarket: ethMarket,

buyTokenPrice: ethMarket.getTokensIn(tokenAddress, WETH_ADDRESS, ETHER.div(100)),

sellTokenPrice: ethMarket.getTokensOut(WETH_ADDRESS, tokenAddress, ETHER.div(100)),

}

});

const crossedMarkets = new Array<Array<EthMarket>>()

for (const pricedMarket of pricedMarkets) {

_.forEach(pricedMarkets, pm => {

if (pm.sellTokenPrice.gt(pricedMarket.buyTokenPrice)) {

crossedMarkets.push([pricedMarket.ethMarket, pm.ethMarket])

}

})

}

const bestCrossedMarket = getBestCrossedMarket(crossedMarkets, tokenAddress);

if (bestCrossedMarket !== undefined && bestCrossedMarket.profit.gt(ETHER.div(1000))) {

bestCrossedMarkets.push(bestCrossedMarket)

}

}

bestCrossedMarkets.sort((a, b) => a.profit.lt(b.profit) ? 1 : a.profit.gt(b.profit) ? -1 : 0)

return bestCrossedMarkets

}

// TODO: take more than 1

async takeCrossedMarkets(bestCrossedMarkets: CrossedMarketDetails[], blockNumber: number, minerRewardPercentage: number): Promise<void> {

for (const bestCrossedMarket of bestCrossedMarkets) {

console.log("Send this much WETH", bestCrossedMarket.volume.toString(), "get this much profit", bestCrossedMarket.profit.toString())

const buyCalls = await bestCrossedMarket.buyFromMarket.sellTokensToNextMarket(WETH_ADDRESS, bestCrossedMarket.volume, bestCrossedMarket.sellToMarket);

const inter = bestCrossedMarket.buyFromMarket.getTokensOut(WETH_ADDRESS, bestCrossedMarket.tokenAddress, bestCrossedMarket.volume)

const sellCallData = await bestCrossedMarket.sellToMarket.sellTokens(bestCrossedMarket.tokenAddress, inter, this.bundleExecutorContract.address);

const targets: Array<string> = [...buyCalls.targets, bestCrossedMarket.sellToMarket.marketAddress]

const payloads: Array<string> = [...buyCalls.data, sellCallData]

console.log({targets, payloads})

const minerReward = bestCrossedMarket.profit.mul(minerRewardPercentage).div(100);

const transaction = await this.bundleExecutorContract.populateTransaction.uniswapWeth(bestCrossedMarket.volume, minerReward, targets, payloads, {

gasPrice: BigNumber.from(0),

gasLimit: BigNumber.from(1000000),

});

try {

const estimateGas = await this.bundleExecutorContract.provider.estimateGas(

{

...transaction,

from: this.executorWallet.address

})

if (estimateGas.gt(1400000)) {

console.log("EstimateGas succeeded, but suspiciously large: " + estimateGas.toString())

continue

}

transaction.gasLimit = estimateGas.mul(2)

} catch (e) {

console.warn(`Estimate gas failure for ${JSON.stringify(bestCrossedMarket)}`)

continue

}

const bundledTransactions = [

{

signer: this.executorWallet,

transaction: transaction

}

];

console.log(bundledTransactions)

const signedBundle = await this.flashbotsProvider.signBundle(bundledTransactions)

//

const simulation = await this.flashbotsProvider.simulate(signedBundle, blockNumber + 1 )

if ("error" in simulation || simulation.firstRevert !== undefined) {

console.log(`Simulation Error on token ${bestCrossedMarket.tokenAddress}, skipping`)

continue

}

console.log(`Submitting bundle, profit sent to miner: ${bigNumberToDecimal(simulation.coinbaseDiff)}, effective gas price: ${bigNumberToDecimal(simulation.coinbaseDiff.div(simulation.totalGasUsed), 9)} GWEI`)

const bundlePromises = _.map([blockNumber + 1, blockNumber + 2], targetBlockNumber =>

this.flashbotsProvider.sendRawBundle(

signedBundle,

targetBlockNumber

))

await Promise.all(bundlePromises)

return

}

throw new Error("No arbitrage submitted to relay")

}

}