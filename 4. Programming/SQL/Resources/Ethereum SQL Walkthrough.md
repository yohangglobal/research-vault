# Learn ETH Concepts with SQL
#dataanalysis #guide 

Source:
https://ethereum.org/en/developers/tutorials/learn-foundational-ethereum-topics-with-sql/

Dune dashboard:
https://duneanalytics.com/paulapivat/Learn-Ethereum

## Regular Txs

The transactions that we normally see on Ethereum can be queried as such. From an initial look, data is specified starting from the base layer and moves into each section of a transaction. For instance, starting with the "tx hash" and moving into the origin and destination of the transaction.

```
WITH temp_table AS (

2 SELECT
3    hash,
4    block_number,
5    block_time,
6    "from",
7    "to",
8    value / 1e18 AS ether,
9    gas_used,
10    gas_price / 1e9 AS gas_price_gwei
11 FROM ethereum."transactions"
12 WHERE "to" = '\xde0B295669a9FD93d5F28D9Ec85E40f4cb697BAe'
13 ORDER BY block_time DESC
14 )
15 SELECT
16    hash,
17    block_number,
18    block_time,
19    "from",
20    "to",
21    ether,
22    (gas_used * gas_price_gwei) / 1e9 AS txn_fee
23 FROM temp_table
```

Doing so provides the accustomed information that Etherscan displays for every transaction.
![](Pasted%20image%2020230321143927.png)

### Tx Breakdown

Each of these transactions also operates around similar queries on Dune Analytics: https://duneanalytics.com/paulapivat/Learn-Ethereum.

This is the main datasets that each tx comprises of:
-   **Recipient**: The receiving address (queried as "to")
-   **Signature**: While a sender's private keys signs a transaction, what we can query with SQL is a sender's public address ("from").
-   **Value**: This is the amount of ETH transferred (see `ether` column).
-   **Data**: This is arbitrary data that's been hashed (see `data` column)
-   **gasLimit** – the maximum amount of gas units that can be consumed by the transaction. Units of gas represent computational steps
-   **maxPriorityFeePerGas** - the maximum amount of gas to be included as a tip to the miner
-   **maxFeePerGas** - the maximum amount of gas willing to be paid for the transaction (inclusive of baseFeePerGas and maxPriorityFeePerGas)

To actually query the above data, use this code block:

```
SELECT

2    "to",

3    "from",

4    value / 1e18 AS ether,

5    data,

6    gas_limit,

7    gas_price / 1e9 AS gas_price_gwei,

8    gas_used,

9    ROUND(((gas_used / gas_limit) * 100),2) AS gas_used_pct

10FROM ethereum."transactions"

11WHERE "to" = '\xde0B295669a9FD93d5F28D9Ec85E40f4cb697BAe'

12ORDER BY block_time DESC
```

### Blocks

In order to understand how/when to query info from Ethereum, first we must recognize that each transaction changes the state of the EVM. This means that each new block added to the chain/network will be verified and added to the block and can be queried as a specific block number. 

Each of these blocks also contains the parent hash, or the hash of the previous block. Here's this query as an example: https://duneanalytics.com/queries/44856/88292.

The layout for each SQL query has SELECT as the Column headers for the query results, for example Time Number Hash Parent Hash Nonce on top, then tells Dune to pull from Eth blocks betweena certain set of blocks. 854 to 856

```
SELECT

2   time,

3   number,

4   hash,

5   parent_hash,

6   nonce

7FROM ethereum."blocks"

8WHERE "number" = 12396854 OR "number" = 12396855 OR "number" = 12396856

9LIMIT 10
```

From here we can also examine each block based on the number, time of the block's completion, difficulty, etc.

The article explains that there's two different types of data that we would be working with.
- Chain data: list of blocks/txs, explicit, stored on-chain itself
- State data: result of each tx's state impact, implicit, not stored on-chain.

For Dune, it's better to query what is actually hosted on-chain. Same goes for using SQL for this data.

The majority of these queries operate around a selection, pulling from Ethereum's "transactions" and then specifying their origin and how to order them.
```
SELECT * FROM ethereum."transactions"

2WHERE block_number = 12396854

3ORDER BY block_time DESC`
```

We can also view the overall success of the bundle of txs included in this block via this query:

```
WITH temp_table AS (

2    SELECT * FROM ethereum."transactions"

3    WHERE block_number = 12396854 AND success = true

4    ORDER BY block_time DESC

5)

6SELECT

7    COUNT(success) AS num_successful_txn

8FROM temp_table

9
```

#### How many Txs per day?

Their next section focused on proving that blocks are committed approx. every 15 seconds.

By dividing the amount of seconds in a day (86400) by 15, the average number of blocks produced per day is ~5,874.

Interestingly enough, the query for this data is a bit more in-depth and involves date/times, how to group each of them, and pulls from ethereum."blocks".
```
# query to visualize number of blocks produced daily since 2016

2

3SELECT

4    DATE_TRUNC('day', time) AS dt,

5    COUNT(*) AS block_count

6FROM ethereum."blocks"

7GROUP BY dt

8OFFSET 1

9

10# average number of blocks produced per day

11

12WITH temp_table AS (

13SELECT

14    DATE_TRUNC('day', time) AS dt,

15    COUNT(*) AS block_count

16FROM ethereum."blocks"

17GROUP BY dt

18OFFSET 1

19)

20SELECT

21    AVG(block_count) AS avg_block_count

22FROM temp_table
```

### Gas

The next segment to realize is that each block has a maximum size they can reach, although they are dynamic to network demand. The units used to determine this size are normally referenced as "gas fees" and occur between 12.5m to 25m units. There are also limits included to avoid large block sizes from putting strain on full nodes (devices that are storing and validating transactions on the entire ethereum blockchain).

This page describes how the gas limit per block can be viewed as the supply of available block space. This query looks like the following:
```
SELECT

2    DATE_TRUNC('day', time) AS dt,

3    AVG(gas_limit) AS avg_block_gas_limit

4FROM ethereum."blocks"

5GROUP BY dt

6OFFSET 1
```

We can also do the same for block space demand like so:
```
SELECT

2    DATE_TRUNC('day', time) AS dt,

3    AVG(gas_used) AS avg_block_gas_used

4FROM ethereum."blocks"

5GROUP BY dt

6OFFSET 1
```

![](Pasted%20image%2020230321150432.png)

#### Gas per Tx

This next query focuses on how much was paid for gas per each transaction. This is primarily centered around the Ethereum Foundation's gas but can be applied to any wallet on Ethereum.

```
SELECT

2    block_time,

3    gas_price / 1e9 AS gas_price_gwei,

4    value / 1e18 AS eth_sent

5FROM ethereum."transactions"

6WHERE "to" = '\xde0B295669a9FD93d5F28D9Ec85E40f4cb697BAe'

7ORDER BY block_time DESC
```

