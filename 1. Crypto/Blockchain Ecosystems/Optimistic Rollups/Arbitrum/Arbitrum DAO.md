---
date_created: 2023-04-08
tags: optrollups, dao
category: Crypto
subcategory: Blockchain Ecosystems
topics: optimistic rollups, arbitrum, governance
---

# Overview of the Arbitrum DAO
#optrollups #dao 

## Information

Docs are built using Docusaurus:
https://github.com/ArbitrumFoundation/docs

Governance repo is here:
https://github.com/ArbitrumFoundation/governance

This summarizes the background of the DAO and Arbitrum chains:
![[Pasted image 20230409141031.png]]

## Initial foundation setup
>Source: https://docs.arbitrum.foundation/foundational-documents/transparency-report-initial-foundation-setup

### Directors

Important section to remember, DAO can vote out or add to these directors:
![[Pasted image 20230409141053.png]]

### Set-up Costs

>With the launch of the ArbitrumDAO, the responsibility for operation of the Arbitrum network was transferred to the ArbitrumDAO. As part of its responsibilities to the DAO, the Foundation has assumed the costs of paying for operations, blockchain operation, infrastructure, service contracts, and ongoing improvements to the Arbitrum ecosystem. In addition, the net on-chain fee revenue (the net difference between fees collected by on-chain operations and L1 fees paid by the Sequencer) from the Arbitrum One and Arbitrum Nova chains is now being sent to the ArbitrumDAO treasury. As such, the ArbitrumDAO will need to ensure The Arbitrum Foundation is adequately funded going forward to continue operating core infrastructure for the Arbitrum network including the Sequencer and public RPC interface.

Basically we have funded this amount of the DAO and all setup costs, so need that money from DAO.
All fee revenue is going back to the DAO treasury and they state that they are adequately funded at this point in time.
![[Pasted image 20230409141105.png]]

This next part is interesting because we don't actually know how much of this 0.1% was used for the "following expenses".

The admin budget wallet does not have a label, nor do any other wallets. We do know that the majority was sent to the treasury with 11.62% going to users.

### Governance

Currently the $ARB tokenholders have the majority of power during proposals and can vote and effectuate any AIPs.

- $ARB tokenholders, who make up the ArbitrumDAO, play the most critical role in the proper functioning of decentralised governance in the pursuit of a trustless, transparent and verifiable Arbitrum ecosystem. As Arbitrum is intended to be a public good, it is only right that governance over it should be directed by those for whom such public good is intended.
- $ARB token holders have the ability to directly propose, vote on and effectuate on-chain AIPs with respect to the ArbitrumDAO-governed chains.

#### Security Council

They also have a Security Council which can perform emergency actions during critical vulnerabilities. I'll be honest, holy shit it's just crazy to me that each cohort can basically do nothing and receive $5k/month as part of the Council. I'll have to refer to the Constitution itself to review their election process.

No major comment here, these all seem like friends/colleagues of the company even if they are well-respected in their own rights. Although think it's interesting that both Offchain Labs cofounders are part of the security council lol which I guess makes sense as part of keeping the Labs values and focuses within this.

![[Pasted image 20230409141156.png]]


#### DA Committee

The next section is about the data availability committee (don't care too much since it's just for Arbitrum Nova). These teams are responsible to be
-   Reddit, Inc.
-   ConsenSys Software Inc.
-   QuickNode, Inc.
-   P2P
-   Google Cloud
-   Offchain Labs, Inc.
-   Opensea Innovation Labs Private Limited

>in the event that a Data Availability Committee member resigns without a replacement, the Security Council may execute an emergency action (9-of-12 approval required) to appoint a replacement for such removed or resigned Data Availability Committee member.

Security council still has a decent amount of control over this as well. One other highlight though is that this committee is receiving 8% of all L2 base fees on Nova with 12% going to the Nova validators. Not sure if that's really an issue at all but found that split to be interesting. For instance, what are these authorized representatives actually doing as each tx data batch is stored?

Beyond that I don't think there's really any big scandal here, congestion fees on Nova are sent back to the DAO treasury and 80% of this L2 base fee is also sent back to treasury.

Overall seems like there's at least some attempt to remove control and power(wealth) from the foundation.

#### Voting Procedure

>There are several governance avenues available, each serving its own purpose.
>1.  Discourse: [https://forum.arbitrum.foundation/](https://forum.arbitrum.foundation/) is a discourse forum for governance related discussions. Community members must register for an account before sharing or liking posts.
>2.  Snapshot: [https://snapshot.org/#/arbitrumfoundation.eth](https://snapshot.org/#/arbitrumfoundation.eth) is an off-chain voting interface that allows the community to signal sentiment on the proposed AIP.
>3.  Tally: [Tally.xyz](https://www.tally.xyz/gov/arbitrum) serves as the initial on-chain voting platform for the ArbitrumDAO to submit and vote on AIPs

