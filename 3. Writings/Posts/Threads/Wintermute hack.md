# Wintermute hack

![](Recording%2020220920110524.webm)

## Summary:
Attackers address: 0xe74b28c2eAe8679e3cCc3a94d5d0dE83CCB84705 Hacker already put over $80m of usdt and usdc in curve [https://etherscan.io/tx/0xd7bf7b67e0d0095b7eb1813a4a60c129b45694374bf996f9ecc249d07efbcd02](https://etherscan.io/tx/0xd7bf7b67e0d0095b7eb1813a4a60c129b45694374bf996f9ecc249d07efbcd02 "https://etherscan.io/tx/0xd7bf7b67e0d0095b7eb1813a4a60c129b45694374bf996f9ecc249d07efbcd02") to avoid blacklisting them by Circle/Tether… Tx hash: 0xe74b28c2eAe8679e3cCc3a94d5d0dE83CCB84705 They targeted this contract: etherscan.io/address/0x00000000ae347930bd1e7b0f35588b92280f9e75 
They used an ancillary contract for doing the job: etherscan.io/tokentxns?a=0x0248f752802b2cfb4373cc0c3bc3964429385c26 

This is the attackers current wallet address
0xe74b28c2eAe8679e3cCc3a94d5d0dE83CCB84705
https://twitter.com/zachxbt/status/1572136997241917440?s=21&t=Acq67L09dE56dvSJXSWr_A

The initial cause of the hack is from a bug in the Eth vanity address generating tool Profanity
https://blog.1inch.io/a-vulnerability-disclosed-in-profanity-an-ethereum-vanity-address-tool-68ed7455fc8c

## Thread
https://twitter.com/YohanGGlobal/status/1572252678247555073?s=20&t=pz1_dEJAMM7gCsfLkaGVIQ
## Thoughts
Reading over the wintermute hack some more, pretty interesting that Profanity chose to use random 32-bit vectors to seed 256 bit priv keys. allowing anyone with a lot of GPUs to brute force the addresses themselves

Most interesting here is that this is a relatively simple process for ppl with a lot of gpus to do, maybe even just optimize for richest wallets and then go for those?

or test with a few gpus and see what hits first

This github issue talks about what this process would look like for a gpu
https://github.com/johguse/profanity/issues/61
![](profanity-bruteforce.jpg)

## Tweets

Andrew T displays Wintermute has at least $200m in debt on diff DeFi protocols too through Nansen portfolio
Nansen dashboard
https://t.co/6WRDDdSfk5

https://twitter.com/blockanalia/status/1572216230890864642?s=21&t=Acq67L09dE56dvSJXSWr_A

Mewn comments on how current wallet infrastructure won't necessarily  improve without governance inclusions

![](Pasted%20image%2020220920100146.png)

The followup on the initial tweet is pretty similar to creating a multisig with different devices and addresses you maintain to act as a set of guardians, i think degenspartan talked about this awhile ago

honestly similar process i've used for gnosis safe and managing funds without having a cold wallet. this is a must tho, would be 10x easier for my life to have a gridplus right here smh

![](Pasted%20image%2020220920100410.png)