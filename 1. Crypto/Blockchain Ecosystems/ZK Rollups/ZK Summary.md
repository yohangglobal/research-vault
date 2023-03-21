# What are Zero Knowledge Proofs?
#research #zkrollups 

# Summary
> How do ZK-Rollups work?

ZK-Rollups are a type of Layer 2 scaling solution which bundle or “rollup” transactions into a single batch, which is then posted to the Ethereum blockchain alongside a proof attesting to the validity of the bundled transactions. Further, ZK-Rollups allow user balance data on Layer 2 to be available on Layer 1, allowing anyone to validate the state. Scalability benefits in rollups come from moving the expensive computational work off-chain, and only verifying the proof attesting to the validity of the state transition on-chain.

ZK-Rollups offer high throughput, instant finality (no danger of trade rollbacks), self-custody, and privacy, and are therefore well suited to the high-value exchange use case. Further, in the event the dYdX servers becomes unresponsive, all the data needed to reclaim user's funds on an escape event is right there on the Ethereum blockchain - there are no additional trust assumptions.

Thread explaining ZK proofs
https://twitter.com/Ravjot_/status/1482252484328718338