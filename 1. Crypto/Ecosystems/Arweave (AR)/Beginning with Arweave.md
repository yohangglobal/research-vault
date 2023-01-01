# Looking into Arweave
What is Arweave? 
arweave.news
arweave.org

How to upload data to arweave

Getting started with ardrive (make new note specifically for this as well)

## Arweave thesis
### The case for Arweave
https://twitter.com/0xchau/status/1481377665655345155?s=21

### Kyle's summary on Arweave 

In short, it is an amazing project with tremendous opportunity, Data is the new oil of the internet. ARWeave is positioned to be perhaps the greatest storage option out there in the blockchain space. There is minor cause for concerns with this project apart from some tokenomics issues which will be addressed shortly. 

Price action: Follows Solana closely, which is why it has seene massive returns recently, but doesn't seem to follow other competitors that well, though Trevor and I didn't look too much into that, we chose Filecoin as the base, but would have to analyze Story and or Sia to get a better overview. As of now ARweave seems to be worth ⅓ or less that of Filecoin in terms of market cap.

Competitors: The main competitors to ARweave are Filecoin, Storj, and SIA. I've not done a complete analysis of these tokens, but the main difference that ARWeave espouses is the fact that AR is permanent in its storage. That being, when you upload something to AR, it's there, and should you make changes to your data, it keeps the original.

With other options, you pay to keep your data stored and it will stay there as long as you keep paying, with AR, it's a one and done deal. As of now they accomplish this by estimating the cost to store data over the course of 200 years and factor in lowering costs. As of now the going rate is $15 per GB, which is incredibly high, but you're paying for permanence.

Cloud Storage as an industry is 46 Billion, which should reach 227 Billion by 2027. Using Data Storage numbers brings that down to 50+ Billion. Any way you put it, this is a massive industry that will only grow over time as people generate more data. I don't think it's hard to say that AR could grow to 10 billion in MRK cap in the next cycle or 2, which is around a 5x return of current numbers (Not fully diluted market cap). Solana is driving great demand as of now, but I will dive deeper on this.

How does it work: 2 layers Blockweave: Hard to explain in a not technical way, but essentially think proof of stake but throw in a random block called a recall block. In short it incentives nodes to store as much data as possible to earn rewards, speedy data recovery for searches etc. It uses Moneros randomx mining but it might have stopped using that back in the Feb upgrade, there's conflicting sides to that.

Tokennomics: Overall pretty good, better than SOL in some ways. 66 Mill total, 55 mill premined, 40% went to investors (some great ones) 3% to advisors, 15% to team and future projects, seems like a 5 year vesting schedule, but these details are murky. Users: It's okay, has 11 terabytes stored as is, around 92k+ wallet addresses, 10K plus downloads of it's browser extension, 13 million in transaction volume. But as I will address in concerns, a noticeable lack in activity in its own ecosystem of smart contracts

Some concerns: Sol is basically dictating the demand and success of ARweave, it's stupid easy to store on ARweave, and with its smart contract capabilities, has the potential to derive and foster it's own ecosystem. There is great potential in what they call Profit sharing tokens, where you can essentially create tokens, apps etc with its ecosystem and share the profit derived from those tokens (which btw can't be altered by 3rd parties) This could create problems with securities laws and go the route of Audius, XRP, but I digress.

The whole system is susceptible to a 51% attack with it's nodes and any changes to blocks by nodes (of which there is only 151) that could be retroactive. Also given this over 50% of tokens are held by 20 wallets, so these whales could dump. That being said, the Solana demand has helped this a bit. I also haven't seen much activity on projects built on ARWeave's ecosystem as it. Almost looks like around a 1000 users as is. This would have to grow in the future to separate AR from Solana. I also have seen AR try and reach out to other Cryptos to do essentially what SOL did to AR


# Resources

[arweave](https://www.arweave.org/)

[Getting started with Arweave](https://www.arweave.org/build)

[Getting Started](https://docs.arweave.org/info/)

[Mining Guide](https://docs.arweave.org/info/mining/mining-guide)

Cool apps

[Arweave App Explorer](https://explorer.arweave.co/)

[Arweave Forever Chess](https://vuljlnuj7tui.arweave.net/moNZ-mmpch7SH3GUsZiuR47m1Tn242vVtT6IjqsHcvM)

# Research on $AR

[Justin on Twitter: "The case for Arweave and the need for decentralized storage.@ArweaveTeam is a decentralized permanent on-chain data storage solution. It's proven to be scalable and the ecosystem is growing rapidly.1/x pic.twitter.com/a8txpMizk3 / Twitter"](https://twitter.com/0xchau/status/1481377665655345155?s=21)

[Permanent NFT Storage on the Arweave Network](https://arweave.medium.com/permanent-nft-storage-on-the-arweave-network-41f38d700a2d)

[Why NFTs on Arweave and Solana Took Off This Summer - arweave.news](https://arweave.news/nfts-on-arweave-and-solana/)

## MollyDao Writeup

[eGirl Capital](https://www.egirlcapital.com/portfolio/Arweave)

Decentralised storage is a piece of critical infrastructure for web3, smart contract platforms ( such as Ethereum) by itself isn’t designed for data storage. The primary reason for this is that the cost of the same storage on Ethereum is 1 million times higher than Amazon Web Service (AWS) - the incumbent web2 leader of cloud computing.

The most common solution to the problem is that DApps will use a mixture of storage solutions, they will only store the BLL and DAL data (smart contract, transactions, hashes of files and multimedia etc.) on Ethereum. While these are typically already decentralized, the majority of files UI data are still hosted on traditional centralized servers on GCP, AWS, Azure, Digital Ocean - so on and so forth.

DApps that take on this approach are still partially centralised, which gives cloud providers the power to suspend and censor at least parts of core functionality. Besides having a single point of failure, blockchain tech and crypto as a whole experience increased scrutiny from regulators, which exposes multiple attack vectors, for example - the security and user experience of dApps and NFT files stored on cloud providers will be threatened if cloud providers decide to shut down support and decide not to support web3 projects. There is also downtime risk as typical EC2 instances and S3 file buckets have a single point of failure.

The other alternative would be a decentralised storage solution, which is currently dominated by IPFS.

IPFS is the first decentralised storage solution, which went live in 2014. In order to make it Scalable and commercial use friendly, Protocol Labs introduced Filecoin as its incentive layer to incentivize storage providers to provide a reliable and robust decentralized file storage service.

The market structure of Filecoin has two main components: a storage market and a retrieval market.

Customers get the price quote from storage providers (the miners) based on the size of storage needed, and how many copies of redundancies come with it, and the duration to be stored.  If customers accept the price, customers would have to pay and sign a smart contract with miners.  After storing the data, they will need to pay miners to retrieve the data. And the price is determined by the miners.

I’ve simplified the explanation for the sake of brevity, but this design requires Filecoin miners to provide cryptographic proof that can’t be forged to prove that they are storing the customer’s data, this process is done by the PoRe(Proof of Replication).

And to ensure that miners are storing customer data according to the contract signed between them and the customers,  the  protocol needs to continuously check if the miners are not behaving maliciously and maintain healthy uptime. If this isn’t achieved, the miner responsible will be punished by the system via two forms - consensus fault slashing & storage fault slashing. Filecoin achieves this using PoTS(proof of spacetime) and requires miners to stake its native token file.

Miners are responsible for providing cryptographic proof, which requires significant computing power, which will increase the cost for miners because computing is a lot more expensive than storage.

Miners will also need to stake FILE upfront, which adds another layer of capital investment.  Therefore, the cost of storage services on filecoin won’t be very cheap compared to AWS.

On the customer front, users would have to pay miners to retrieve stored data on the network. And as I mentioned earlier this price is determined by the miners.  So, customers will face the dilemma of paying a high price to retrieve data and face the choice of having to migrate to another storage solution if miners set a very high price for them to retrieve the data.

The system will manage a lot of contracts and is responsible for checking how those contracts are executed to reward or punish the miners. That also adds complexity to the whole system and may cause latency, especially when compared to established storage providers like AWS, which has edge nodes deployed globally via Amazon CloudFront for example.

In order to encourage the miners to store more data and prevent miners from acting as fake customers to store some redundant data to get more rewards, the system also introduced KYC to verify customer identity, which is also a tricky issue. If the verification process is too strict, that will affect the UX and user acquisition. However, if requirements are too loose, it won’t be able to prevent miners from gaming the system.  And personally, I think kyc on a decentralised platform is kinda funny.

With all the problems mentioned above, the higher cost and highly complex system make it difficult for Filecoin to offer a competitive price when compared to its centralised competitors. So from the customer’s perspective, choosing a centralized cloud service provider and signing a legal contract to protect their access and recourse still seems to be a better option. This is the primary reason why there are still many dApps still choosing to use centralised cloud services.

Even though the underlying tech is different, the other decentralized storage protocols such as Sia and Storj are all facing the same challenges since they are sharing the same concept, users sign a contract with miners, and protocol checks how miners are execute the contract, and punish miners if they are not following the contract.

Historical experience tells us that if you repeatedly try to solve the problem with the same solution and ask, “why doesn’t this work?”, you’re probably ngmi. You gotta focus on the problem instead of the solution.

Take Bitcoin as an example; before it came along, if you want to build a decentralised system, then you need to solve the Byzantine failures, but Byzantine failures is a challenge of a pre-determined solution, not the challenge of a decentralised system itself.

Bitcoin ignored the Byzantine failures. Bitcoin achieved decentralisation  using a completely different approach, and that idea is simple: when a miner discovers a new block, the miner needs to include the hash of the previous block. If they act maliciously by including invalid transactions or unusual scripts in the block, he/she risks losing the mining reward because the next people who found the block are completely random and they won’t include a hash of an invalid block. Miners have to pay for computing, and including a hash of an invalid block will cause them to lose their mining reward. This design is simple, clever, and neat af.

> This brings me to Arweave, Arweave also took a similar approach.

It only maintains one market in the system. Customers pay the storage cost all at once, and get permanent access to the data. At the time of writing, Arweave is the only storage solution that offers data permanence among all the centralised and decentralised storage  solutions.

The system required AR tokens to be added to the endowment of AR tokens to cover the 200 years of storage cost in advance. In the event miners providing the storage service decide to stop, this ongoing endowment entices new miners to take over and fill the shoes of miners who are leaving the network.

Unlike Filecoin, Arweave doesn’t require miners to provide cryptographic proof to prove they’ve stored the data.

If you dig deeper, you should undoubtedly see similarities between Arweave’s & Bitcoin’s consensus mechanism.

Arweave’s blockweave is a set of data blocks that link to previous blockweave history. Miners who mine the new block will earn AR tokens from the endowment.  In each new block, there will be a randomly selected chunk of past data - the recall block.  Only the miners who’ve stored the recall block are able to compete for the reward.

Just like Bitcoin’s block discovery process, Arweave’s recall blocks are also unpredictable and randomly chosen past data. Miners who store more data will have a higher chance to join the mining, which also means an increased chance in getting the reward.

This design encourages miners to store as much data as possible and prioritise the data that has lesser copies. If the miner’s storage space is limited, then they will prefer to store the data that has a lesser redundancy count, because each past block has the same probability of being selected as the recall block.

When a block with less copied data is selected as the recall block, only a small number of miners can join the mining, which translates to a higher chance to win the reward.

Therefore, unlike Filecoin that needs to process massive amounts of contracts and transactions, and the need to constantly check each contract in terms of how it will execute in order to reward or slash miners, Arweave only needs to process one contract, and all the data is stored permanently. This makes Arweave’s design very elegant and translates to lower operational costs for miners & users alike. So, it’s cheaper and more reliable compared to a contract-based solution such as Filecoin.

At the time of writing this article, I believe Arweave is the most feasible solution to make decentralised data storage gain wider adoption.

According to data from Messari on July 21, 2021, Arweave currently only accounts for 0.1% of the total decentralized storage and only 8% of its market value. We believe with their superior technology and design, there is still a lot of room for Arweave to grow in the future.

Big thanks to Jeremy from Delphi who helped edit the article

![https://www.datocms-assets.com/45756/1630195529-ar1.png](https://www.datocms-assets.com/45756/1630195529-ar1.png)

---

## Writeup from Kyle

In short, it is an amazing project with tremendous opportunity, Data is the new oil of the internet. ARWeave is positioned to be perhaps the greatest storage option out there in the blockchain space. There is minor cause for concerns with this project apart from some tokenomics issues which will be addressed shortly.

Price action: Follows Solana closely, which is why it has seene massive returns recently, but doesn't seem to follow other competitors that well, though Trevor and I didn't look too much into that, we chose Filecoin as the base, but would have to analyze Story and or Sia to get a better overview. As of now ARweave seems to be worth ⅓ or less that of Filecoin in terms of market cap.

Competitors: The main competitors to ARweave are Filecoin, Storj, and SIA. I've not done a complete analysis of these tokens, but the main difference that ARWeave espouses is the fact that AR is permanent in its storage. That being, when you upload something to AR, it's there, and should you make changes to your data, it keeps the original. With other options, you pay to keep your data stored and it will stay there as long as you keep paying, with AR, it's a one and done deal. As of now they accomplish this by estimating the cost to store data over the course of 200 years and factor in lowering costs. As of now the going rate is $15 per GB, which is incredibly high, but you're paying for permanence.

Price analysis: As stated above we've seen a massive rally for AR, mainly due to Solana Summer train blasting off. As of late August we've seen some pull back as people take profits. AR as of writing is around 65-70 range. Looking at a log scale of the price action it's likely the next resistance level will be around 80. We should easily see $100 AR in this cycle. Cloud Storage as an industry is 46 Billion, which should reach 227 Billion by 2027. Using Data Storage numbers brings that down to 50+ Billion. Any way you put it, this is a massive industry that will only grow over time as people generate more data. I don't think it's hard to say that AR could grow to 10 billion in MRK cap in the next cycle or 2, which is around a 5x return of current numbers (Not fully diluted market cap). Solana is driving great demand as of now, but I will dive deeper on this.

---

## How does it work:

2 layers Blockweave: Hard to explain in a not technical way, but essentially think proof of stake but throw in a random block called a recall block. In short it incentives nodes to store as much data as possible to earn rewards, speedy data recovery for searches etc. It uses Moneros randomx mining but it might have stopped using that back in the Feb upgrade, there's conflicting sides to that.

Tokennomics: Overall pretty good, better than SOL in some ways. 66 Mill total, 55 mill premined, 40% went to investors (some great ones) 3% to advisors, 15% to team and future projects, seems like a 5 year vesting schedule, but these details are murky. Users: It's okay, has 11 terabytes stored as is, around 92k+ wallet addresses, 10K plus downloads of it's browser extension, 13 million in transaction volume. But as I will address in concerns, a noticeable lack in activity in its own ecosystem of smart contracts

Some concerns: Sol is basically dictating the demand and success of ARweave, it's stupid easy to store on ARweave, and with its smart contract capabilities, has the potential to derive and foster it's own ecosystem. There is great potential in what they call Profit sharing tokens, where you can essentially create tokens, apps etc with its ecosystem and share the profit derived from those tokens (which btw can't be altered by 3rd parties) This could create problems with securities laws and go the route of Audius, XRP, but I digress.

The whole system is susceptible to a 51% attack with it's nodes and any changes to blocks by nodes (of which there is only 151) that could be retroactive. Also given this over 50% of tokens are held by 20 wallets, so these whales could dump. That being said, the Solana demand has helped this a bit. I also haven't seen much activity on projects built on ARWeave's ecosystem as it. Almost looks like around a 1000 users as is. This would have to grow in the future to separate AR from Solana. I also have seen AR try and reach out to other Cryptos to do essentially what SOL did to AR

That being said, these are small concerns and don't take away the pros of this project. The smaller mark cap and better tokenomics make for an easy push for the price. I can see great growth potential for this project.

---
