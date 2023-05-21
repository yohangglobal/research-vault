---
date_created: 2023-05-21
tags: dev, python
section: Programming
category: Blockchain Dev
subcategory: Ape Framework
topics: frameworks, code guides
---

# Getting Started with Ape Framework
#dev #Python #guide 

First we start with installing Ape into our terminal.

You can either download VS Code and install view apeworx's getting started guide:
https://academy.apeworx.io/getting-started

Or follow the google colab walkthrough that Kofi provides by running this command:
```
# This command installs Ape. 
!pip3 install eth-ape
```

This should now start installing and you can restart runtime to use the new version.

Kofi explains that Ape is modular and allows for installing various plugins. The first used is ape-alchemy:
```
# By installing plugins, you can expand the functionality of Ape.
# This plugin allows you to use the Alchemy API with Ape.
# Alchemy's API allows applications to connect to a blockchain node and thereby
# interact with on-chain data + send transactions.

!pip3 install ape-alchemy
```

Next is installing ape-eterscan for contract data.
```
# This plugin assists with fetching contract data.
!pip3 install ape-etherscan
```

The next part is to connect to Ethereum itself, which contains each of the Ape libraries that you can interact with.
```
# This command imports the Ape libraries you will need.
from ape import chain, networks, Contract
```

This is the API key that I used: 1m5Bk9gOtdxdB16LNYeIsUvRA

Then use the following codeblock to connect your API key with Ape to access each EVM chain.
```
# You can connect to any EVM chain using Ape, as long as there is a plugin for it.
# Ape supports Ethereum mainnet without the need for additional plugins.
# This code block connects you to Ethereum using the Alchemy API.

network_choice = 'ethereum:mainnet:alchemy'
context = networks.parse_network_choice(network_choice)

with context:
  provider_config = context.provider.config
  context.__enter__()
```

Make sure that you're following each step to make sure each function is inputted correctly. Don't skip around and install randomly.

Next you're going to create an instance of the USDC smart contract. Then you can query certain data points that you'd like to find. Just pull the contract address from etherscan.

```
# Using this command, you create an interactive instance of the USDC smart contract.
usdc = Contract("0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48")
```

To check token balances, you would call the `balanceOf()` function first and this is how users are presented with each relevant token balance on Etherscan.

```
# Using this command you call the balanceOf() function of the USDC smart contract
# to check the current balance of the Uniswap DAI/USDC 0.01% pool and
# print the result.

print(usdc.balanceOf('0x5777d92f208679db4b9778590fa3cab3ac9e2168'))
```

Kofi then explains that going through the contract itself will display all the functions that we can call. You will have to Read as Proxy to see all examples.

You can then state the different functions you want to print by typing `print(usdc._blank function_(input)`.

This would be a similar outcome to going to the uniswap v3 pool and typing in this address yourself.
https://etherscan.io/token/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48#readProxyContract

This worked pretty well actually, very impressed. This was the output: 61069035747218.

This is for viewing current datapoints, next is for historical data.

Kofi explains that whenever a smart contract emits an event, a log of that event is written to the blockchain and can be queried later on.

He pulls the historical data of the webaverse nft smart contract to display previous transfers within a range of blocks.

```
# Using this command, you create an interactive instance of the Webaverse
# NFT smart contract.

webaverse_nft = Contract("0x543D43F390b7d681513045e8a85707438c463d80")
```

Each query requires creating an instance of that smart contract within Ape, then you can make your desired queries.

This code allows for logging all transfer events within this list:
```
# Using this command you pull all the logs corresponding to the contract's
# Transfer events that occured between block 15354270 and block 15354350.

nft_transfers = [log for log in webaverse_nft.Transfer.range(15354270,15354350)]
```

Finally, you can call the `nft_transfers` function to then see all of the transfers that occurred within these blocks:
```
# Using this command you pull all the logs corresponding to the contract's
# Transfer events that occured between block 15354270 and block 15354350.

nft_transfers = [log for log in webaverse_nft.Transfer.range(15354270,15354350)]
```

Kofi then pulls up each of the contracts from the webaverse contract, the function is a transfer event emitted from the smart contract itself.

# Executing a Transaction
#dev #Python #guide 

>Not started yet!

