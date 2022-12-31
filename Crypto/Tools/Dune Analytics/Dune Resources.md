
# Getting Started with Dune
#guide #dev #dataanalysis 

## Groups
This TG group is for Dune Ninja, an easy way to pull up queries for different things on Dune
https://t.me/+uOMEYuVpMoRiOWUx

## Threads
### Hoeem Top Tips
This first thread gives top tips to follow when starting out on Dune
https://twitter.com/crypthoem/status/1580580068773965824?s=20&t=Yn4QoFU9qIaec6PVCT0dzw

He describes Dune as a way to view any dataset of blockchains in a simple way and shows the most popular dashboards over time.

rchen8 has a dashboard of all defi users over time
![](Pasted%20image%2020221223173717.png)

For viewing ETH staking there's this dashboard from hildobby
![](Pasted%20image%2020221223173802.png)

The classic DEX metrics from hagaetc, then one more about NFT marketplaces. Best outlook for me would be figuring out how to recreate the DEX metrics and understanding defi usage over time.

#### Dune Analysis Tutorials
From here he delves into useful tutorials, primarily the Episode 3 of Dune Analytics Tutorial Series for tracking wallets and showing ecosystem strength.

About an hour long and I should definitely watch this series first:
https://www.youtube.com/watch?v=ez3VfcfNwvc&feature=youtu.be

### DeFi Mochi Dune Thread
So this was a pretty big thread that got some attention on how to become a crypto data analyst:
https://twitter.com/defi_mochi/status/1598478592329252864?s=20&t=xDg0JElgnrYTOeTPhpVxmg

Begins with an SQL for beginners tutorial which should be a good place to start out (looks like it was taken down but I can find some other SQL Beginners guide)

#### OurNetwork Guide
The next resource is the Our Network guide and their first episode on how to learn about Dune and their syllabus. The youtube page has about 19 episodes uploaded and this initial video is roughly 19 minutes long. This will be a pretty good intro course to follow up with for direct education.
https://www.youtube.com/watch?v=yDSmTUrpdoQ

Mochi's next suggestion is to simply go thru etherscan txs, that's relatively simple for me as I can work around the # block-explorer channels to plug and play with different transactions I've watched over time.

#### Using Etherscan
From here they reference an etherscan tutorial as more of a 101 guide to follow, seems like it gives good start to finish but not as advanced as I would expect. Roughly 19min and will cover different tokens and transactions.

**How to Use Etherscan:**
https://www.youtube.com/watch?v=spnwIsE5ziQ

Adding coins to wallet, learning about how to do it within etherscan. This is showing interactions with coins and what is showing within the wallet itself. They then go into loans and their balances on each of these pools.

Goes thru analytics dash and past tx fees, can look at stuff from every account. Main addresses can view comments and seeing what is on the main account page for each wallet. Talks about ENS names and buying nfts, dont care about that.

Focuses on how to speed up a tx as well thru etherscan. This shows what is in the queue and how long it'll be until this tx is included in the block.

Next is how to revoke token accesses, basically doing revoke.cash but thru etherscan instead. Pretty interesting but there's already a website for this now.

Next section is on reading/writing smart contracts. Very basic understanding, mostly just how to go thru the same process as other projects and reading each part of the contract. Pretty cool that you can go thru each one and see balances thru etherscan vs relying on wallets. You can also write full parts of the contract, connecting your wallet and then going to the transfer/mint/burn part of the smart contract. 

Very cool example he gave is transferring his uniswap v3 position from one wallet to another? I can do this with sushiswap then right? That would be a pretty interesting test to try out as well instead of letting it sit there without harvesting.

#### More info on Dune & Wizards
Mochi explains that Dune analytics is roughly 30% etherscan and 70% SQL and should be understood as a whole.

Next is to join the discord to talk with other wizards
https://discord.com/invite/ErrzwBz

From here the goal is to start on a personal project, find something you like interesting and then build it out. Mochi's example is that Fraximalist dashboard: https://dune.com/defimochi/fraxboard
They also recommend starting out on Ethereum and then building out to other chains once you've gotten started.

List of wizards to follow:
[@superamscom](https://twitter.com/superamscom)
[@0xBoxer](https://twitter.com/0xBoxer)
[@crypto_DIPsy](https://twitter.com/crypto_DIPsy)
[@chuxin_h](https://twitter.com/chuxin_h)
[@hildobby_](https://twitter.com/hildobby_)
[@sui414](https://twitter.com/sui414)
[@andrewhong5297](https://twitter.com/andrewhong5297)
[@0xKofi](https://twitter.com/0xKofi)
[@unionepro](https://twitter.com/unionepro)
[@21Shares](https://twitter.com/21Shares)


### Querying with ChatGPT

**This shit dumb as fuck just read the tutorials and dune docs instead.**

This thread highlights how to create query data on GPT with SQL, seemingly as an easy way out instead of learning SQL prior to using Dune:
https://twitter.com/0xanyaa/status/1601494765375483910?s=46&t=xd_Umlrl4uay0Xg3aq8w6A

This starts out by first pulling up certain table names from Dune by saying "i want to query dex.trades table on Dune"

Basically asking it what queries to use and how to answer questions like "Find the last 24hrs of volume traded on eth blockchain" then paste code as needed

Here's their example:
![](Pasted%20image%2020221223182920.png)

And the output:
![](Pasted%20image%2020221223182940.png)

From here they dive into more complex queries, this time on weekly traded volume for each DEX. Ran into an issue with the "WEEK" function but instead asked for another function, which GPT replied as "DATE_TRUNC"

Input:
![](Pasted%20image%2020221223183130.png)

Output:
![](Pasted%20image%2020221223183138.png)

New output after changing Line 3:
![](Pasted%20image%2020221223183458.png)

#### ChatGPT Inputs
How can I get started on Dune Analytics?

>To create dashboards for viewing Ethereum transactions using Dune Analytics, you will need to do the following:

1.  Sign up for a Dune Analytics account and connect it to your Ethereum wallet. This will allow you to access data from the Ethereum blockchain and use it to build dashboards.
    
2.  Use Dune Analytics' Query Editor to write SQL-like queries that extract data from the Ethereum blockchain. You can use various clauses and functions to filter and manipulate the data as needed.
    
3.  Use the Dune Analytics Dashboard Builder to create a dashboard layout and add widgets to display the data from your queries. You can customize the appearance and layout of your dashboard as needed.
    
4.  Use Dune Analytics' sharing and collaboration features to share your dashboards with others, or to work on dashboards with a team.
    

Overall, Dune Analytics provides a user-friendly interface for creating and sharing dashboards and analysis of Ethereum blockchain data, including transactions.

First thing I asked for is DEX trading volume, this is the codebase provided:
```
```SELECT
  SUM(value) as volume
FROM
  trades
WHERE
  exchange = 'Uniswap'
  AND to_timestamp(timestamp) BETWEEN '2022-01-01' AND '2022-12-31'
```

This query will retrieve the total trading volume (in terms of the value of the assets traded) on the Uniswap DEX for the year 2022. You can adjust the `exchange` and `timestamp` criteria to match your desired parameters.

Already got an error so trying again with a different input:

```
SELECT
  SUM(inputs.amount * token_prices.price) as volume
FROM
  trades
  INNER JOIN token_prices ON trades.inputs.token = token_prices.token
WHERE
  trades.exchange = 'Uniswap'
  AND to_timestamp(trades.timestamp) BETWEEN '2022-01-01' AND '2022-12-31'


```

Okay yeah GPT is just bullshitting at this point, would be better to just read the tutorials instead. It's only output is to change words like Trades to Transactions or to Logs as if that is a workaround.

Now reverting back to Anya's suggesting and asking for dex.trades table

Okay I literally wrote the same thing as this bitch and nothing pulled up?? Error for amount_usd make it make sense
``` 
SELECT SUM(amount_usd) as volume_usd
FROM dex.trades
WHERE blockchain = 'avalanche'
  AND block_date >= DATEADD(day, -1, CURRENT_DATE)
```

Did the same for the more complex one and I keep getting this error:

```
SELECT project
    SUM(amount_usd) as volume_usd
    DATE_TRUNC('week', block_data) as week_num
FROM dex.trades
WHERE blockchain = 'ethereum'
    AND block_date >= DATEADD(month, -12, CURRENT_DATE)
GROUP BY project, week_num
ORDER BY project ASC, week_num ASC
```
Error: Syntax error at or near "(" at line 2, position 8.

GPT is kinda retarded now

When asked it changed this query to this?
SELECT
  project,
  SUM(amount_usd) as volume_usd,
  DATE_TRUNC('week', block_date) as week_num
FROM
  dex.trades
WHERE
  blockchain = 'ethereum'
  AND block_date >= DATEADD(month, -12, CURRENT_DATE)
GROUP BY
  project,
  week_num
ORDER BY
  project ASC,
  week_num ASC

Nope got the same error, closing out GPT and just going to use the actual guides/tutorials people have created. Stupid ass shit.


## Readings
### How to use Dune like a Degen

This is a Mirror article by Alex Kroeger, dropped around Nov. 17th, 2021 and hopefully is a much more useful method for receiving data outputs from Dune.

https://alexkroeger.mirror.xyz/0C3EQBtFqAK4k2TAGPZhg0JMY-upfTAxuTD-o91vBPc

This article first begins with writing Dune queries but for unverified contacts. The framing of this article is centered toward experienced developers or at least people that have some understanding of ETH events and programming. 

His example focuses on a Juicebox Terminal V1 Contract https://etherscan.io/address/0xd569d3cce55b71a8a3f3c418c329a66e5f714431#code

Richard Chen is apparently a leading Dune wizard to follow so this article is focused on breaking down the steps that he used to create his query/dashboard. Seen here: https://dune.xyz/queries/244441/456924

#### ETH Events
These are known as logs and store info in a cheaper fashion than contract storage. This is primarily used for pulling fast information about a transaction and can work hand in hand with those looking to extract and analyze blockchain data.

The 'Pay' events on this contract are for who paid into the DAO and how much. Basically looks like pulling up different contract addresses, reading their functions, then understanding what each event is doing per query.

Thankfully, Dune has these events/logs already in place and can be searched via 'ethereum.logs'. Interesting fact here is that each of these events can have 4 indexed paraments as shown in the image above with topic 0-3

First topic shows "event signatures" which looks like a basic hash/public key. He explains that these can be:
1. Pulled from an example event
2. Computed personally using the event information

