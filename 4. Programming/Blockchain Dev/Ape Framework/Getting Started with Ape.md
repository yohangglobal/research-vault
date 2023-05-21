---
date_created: 2023-05-21
tags: dev, python, guide
section: Programming
category: Blockchain Dev
subcategory: Ape Framework
topics: frameworks, code guides
---

# How to Use Ape Framework
#dev #Python #guide 

Working through this tutorial next, interestingly enough I can type `code` into the wsl terminal and this will open up a completely different VS Code that's made for WSL. Even has the "yohan@GG-Laptop:~$" that I always see for linux stuff!

Next is to create a virtual environment. Going to follow the same instructions that this guy has for this.

So now to go back to this, I'm going to make a new directory here, call it ape-demo, then create the venv for apeworx.

`python3 -m venv apeworx`

Then we can see the listed files that this environment has and activate the folder itself.

Very cool, now I have the apeworx environment set up and I can start coding at will:
`source apeworx/bin/activate`

You can easily deactivate to go back to the regular version, then type the above to activate.

Now we actually install Ape itself. Easiest way is to pip install ape. With python, we can copy and do both commands at the same time.

Eh doesn't seem to work for me, just going to do them separately. First is to simply install pip itself

$ pip install -U pip
$ pip install eth-ape

Then install `eth-ape`

Basically installs all necessary python files, libraries, multiple dependencies, then prespares ape itself with additional extensions. Sweet!

Now that this is installed, you can check the commands available by typing `ape` and seeing which version you have! This will pull up a console you can interact with! I'm currently on 0.6.9 version!

To exit the console itself, type `exit()`.

Next I'm going to try and combine the walkthrough that Kofi has to pull up these datapoints thru my terminal instead of google colab.

[Kofi's ApeWorX Starter Guide](obsidian://open?vault=Research%20Vault&file=4.%20Programming%2FBlockchain%20Dev%2FApe%20Framework%2FKofi's%20ApeWorx%20Starter%20Guide) begin here!

For example, after installing eth-ape, Kofi installs ape alchemy. Going to see if this works the same way.

By following the commands provided within the ape console, we can see that installing ape alchemy can be done by typing:
`ape plugins install ape-alchemy`

Now doing the same for etherscan:
`ape plugins install ape-etherscan`

You'll then have to import Ape libraries just like last time:
`from ape import chain, networks, Contract`

This doesn't work since the "from" command can't be found, will try with sudo apt instead.

Oh actually maybe i have to open the console first?

Yes this worked perfectly! So to refresh, you would open the console through `ape console` then type each of the following commands:

Then add the API key using this:
`%env WEB3_ALCHEMY_API_KEY= F_sInf_1m5Bk9gOtdxdB16LNYeIsUvRA`

```
network_choice = 'ethereum:mainnet:alchemy'
   ...: context = networks.parse_network_choice(network_choice)
   ...: 
   ...: with context:
   ...:   provider_config = context.provider.config
   ...:   context.__enter__()
   ...: 
```

`usdc = Contract("0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48")

`print(usdc.balanceOf('0x5777d92f208679db4b9778590fa3cab3ac9e2168'))
60785063528152

### Initial Test

So now that I printed the USDC token balances, I wanted to see if I could continue the same process for other tokens, then test out historical data.

Could've made the naming itself a bit easier but used the following code blocks to pull YFI token balance and previous token transfers between a range of blocks.

The YFI contract itself is: 0x0bc529c00C6401aEF6D220BE8C6Ea1667F6Ad93e
The largest holder and Yearn Treasury address used to pull balances is: 0xFEB4acf3df3cDEA7399794D0869ef76A6EfAff52
Next was the token transfers of YFI between blocks 15354270 and 15354350.

```
In [6]: yfi = Contract("0x0bc529c00C6401aEF6D220BE8C6Ea1667F6Ad93e")

In [7]: print(yfi.balanceOf('0xFEB4acf3df3cDEA7399794D0869ef76A6EfAff52'))
3667915140831411785413

In [8]: token_transfers = [log for log in yfi_token.Transfer.range(15354270,15354350)]
INFO: Cache database has not been initialized

In [9]: token_transfers
Out[10]: 
[<Transfer from=0xA9D1e08C7793af67e9d92fe308d5697FB81d3E43 to=0x6767526a362EC6c6b1DF185478e4F01506B73Ff3 value=1000000000000000000>,
 <Transfer from=0xe0F8C36Af7ce0C4076E6dB0ed5452edDadc2C61D to=0xa740025a271BBbC74F7586258f0e92943F627B77 value=639000000000000000>,
 <Transfer from=0xa740025a271BBbC74F7586258f0e92943F627B77 to=0x28C6c06298d514Db089934071355E5743bf21d60 value=639000000000000000>,
 <Transfer from=0x6767526a362EC6c6b1DF185478e4F01506B73Ff3 to=0x28C6c06298d514Db089934071355E5743bf21d60 value=2965240000000000000>,
 <Transfer from=0x007e4195A6C8F68801c0673ec561c38fED803021 to=0xf60c2Ea62EDBfE808163751DD0d8693DCb30019c value=878490000000000000>]
```

Next up will be using the ape-template plugin to clone and compile projects!

`ape plugins install ape-template`

With that installed, the guide says to sample a project and get testing so that's what I'll do. Will make a new file for [Create an ERC-20 Token](obsidian://open?vault=GG%20Research&file=777%20Devs%20Paradise%E2%8C%A8%EF%B8%8F%2FPython%2FApe%20Framework%2FCreate%20an%20ERC-20%20Token) and start there!


