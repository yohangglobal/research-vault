# Flywheeling with Crv/Cvx
#defi #strategies 

You can still earn good yield as a shrimp, you just need to keep in mind a few basic principles:

1.  Move money as seldom as possible
    
2.  Avoid accumulating small amounts that cost too much to claim.
    

Counterintuitively, this makes it tougher to diversify your portfolio and earn yield as a shrimp. If you’re in one pool, you can afford to harvest and compound, maybe, once per month. If you split this money into ten pools, you might need to wait 10x as long, so you might not be able to claim for a year.

Anybody playing with small amounts should consider bridging to an L2 and playing where gas fees are cheaper. Nonetheless, all the cool toys launch on L1, so you we forgive you if want to stay on mainnet.

Here’s our guide on how to get the most out of the Curve flywheel if you’re on L1. Since it’s only for entertainment purposes, and certainly not financial advice, we’ll offer tips and best practices for shrimps looking to maximize three separate flywheel yield farming strategies, roughly in order of risk appetite.

1.  Stablecoins
    
2.  v2 Pools
    
3.  Flywheel: $cvxCRV/$CVX Staking
    

# Stablecoins

Several newcomers’ first thought on visiting Curve and seeing stablecoin APYs above TradFi’s 0.05% is to use Curve as an alternative to your bank account. Why not bridge your life savings to $USDC and then park into one of these pools? Staying denominated in stables feels fairly safe, right? Crypto may roller coaster, but your net worth stays safe in stables.

Well, several issues to consider. For starters, stablecoin yield is relatively low at the moment across all of DeFi. To get inflation-beating yields, you’ll have to look at riskier strategies that put your bottom line at risk. We’ll assume if you’re following a stablecoin strategy, that you just want the properties of a savings account, relatively low risk and your total dollar values stay at least the same, but maybe you have a shot at beating inflation.

Unfortunately, without risk there’s little chance of good yield. The highest yielding Curve pools also happen to be the riskiest. Among the pools giving double digit token emission percentages are $MIM and $UST, [both of which suffered a heavy depeg risk in the last crash](https://email.mg2.substack.com/c/eJxVkLtuxCAQRb9m6dbiZQMFRZr8hoVhFqNgsAA78t-HXVeRZqaY19U91jTwuVx6z7Whd5nbtYNO8FsjtAYFHRXKHJxmE5VKEIGc5o7IUaJQ51cB2EyIupUD0H4sMVjTQk7vCzIpQie0aselBGWs4hRPfBLSCs4tedmFE0GB3MLmcAGSBQ0nlCsnQFGvre31wb4e9LuHPcoJQz2W2oz9GWzeenPv2VZ4niaFuobkn3WHGJ8oaIppDyzJiAVXAx0EHScGDDO1SMFGNlgugiquPDjePP33GhV95dUk7_vQe2v20EwcQn7bnPvCdqTQrhmSWSK4m0C7QX6YzB4SlA7YzaZ1GJwzRrvsNOLbcEfEhcKEEo66ssv9KumPyT9WsYge). They ultimately held their peg (resulting in really good profits for users in the pools), but it could just as soon been a total wipeout.

A depeg is the most serious risk on Curve, as it could cause you to lose half your funds or more. Some stablecoins have a longer track record and therefore considered less risky. As chance would have it, these “safer” pools also tend to give lower yields. I’d consider [3pool](https://email.mg2.substack.com/c/eJwlkE2OwyAMhU9Tloh_woLFbHqNiICToiEQAekotx_aSJZlyX5--p53HbZSL3uU1tGnzf06wGb4awl6h4rOBnWOwXLFJqOpRsGKQCc5odjmtQLsLibb6wnoOJcUveux5I-CKkOZQi9LF6WYlEQ7EsIUyApmMYpMq5HGAJjb2J0hQvZg4Q31KhlQsq_ej_bgPw_2HOXP-ga8xjHyo5SEomWEjSITHd-FwQxrJhUHTrhZJs0lx17oaGqoD0H2jeF2Lq07_4t92VG1V3m5vG1juW3eHbG7hGP5kMzjYD9z7NcM2S0Jwg3Z76y-2PMGGerIMMyuD14hOGfDVklyM40UhDaEMirQcA5lqLL9cvwDrTx9kQ) to be among the safer pools, since it has lots of liquidity and contains the most battle tested coins in $DAI, $USDC, and $Tether. On 3pool you can only top out rewards at 1.25% on Curve as of publication, so you’re still losing to inflation, just not as much as a normal savings account.

[](https://email.mg2.substack.com/c/eJxVUkuO5CAMPU1ll4hvAQsWrZHmGhEfh0KdQBpIdVeffkhlNZJlGxv7WX52pkHI5aX3XNtwqrm9dtAJvusKrUEZjgpljl7TO5FKYDF4zTyWXA6xzksB2ExcdSsHDPth1-hMizmdFfiuMLkPDy0W7xfCCEjBnOWIWQyMcI4MEVRSfgGbw0dIDjQ8obxygmHVj9b2eqMfN_K3i_NpqoetzbjPyeWth-JmAnS7QHOP0_Y2Ld_In6_LoR8hZ9_fyzrvJYcCtcYn9HhtAHuvuCAIP0H4CdOVPdwn9HwZAXFrnWSjNYaOjAoYFcdyNN5SYkEIJdlU6WQ285uT-a7XXL3HtYy3-x6yXp29BW8UH_GClpFhtoySYzr23UphFXeLtzNX_IeKaU9hiJog0gVJzJFgaiKTIPxOgSKqrBSU08kxEVXx5cbQFsh_GxqKfuWHSSH0ZAjO7LGZdYr55GruH7YjxfaaIRm7gr9obNc1vImdAyQo_Ur8bFpnlDFKSYe9c3Sx1nlmQiFMMBs6ss-9Kml3lCf8A3Tew6w)

At any rate, let’s imagine you’re going for it. You’ve researched the stablecoins thoroughly and decided to park your idle savings into Curve. What’s your best play? We’d recommend the following transactions.

1.  Use Curve.fi to run `approve` and `add_liquidity` transactions into your target pool, but stop short of adding rewards to gauge. This gives you a Curve LP token, an ERC20 token representing your position in the pool.
    
2.  Head to [Convex’s stake page](https://email.mg2.substack.com/c/eJwlUEmOhDAMfE3niLJB4JDDXOYbURaTjgYSlKUZfj9hkCxLtqtcqrK6gk_5kkcqFd1N1esAGeEsG9QKGbUCWQUn2UTnRRCBnOSOzOOMQlFrBth12GTNDdDRzBasriHFm0GmhdAJvaWGdeXWGUspXwi3Bgsz45EJwEZwyh5h3VyAaEHCB_KVIqBNvms9yot9veh3r_M8B5viB37XEHWH9mnv-1L1D6AgKaa98ExGLPgy0EHQcWLAMFvMLNjIBstFWLLLL453T4fSTOfan_sPyvJKbx2970fvrT5C1dsQ0m1LdcDeYqiXgqjNBu5xXJ_g_jNQHiLkHqhTunbznDNGu-w04sdgj4SLBRNKOOrKLnVWlLblD_wBcmqDOA) to stake your shiny new LP token there.
    

[](https://email.mg2.substack.com/c/eJxVUkuO5CAMPU1ll4jwCWTBojXSXCMy4FCoE0gD6Z6a0w-prEaybGNjP8vPFir6lF_6SKV2l1rq60Ad8adsWCvm7iyYl-A0m6ia5Sg7p7kblVBdKMuaEXcIm675xO44zRYs1JDiVTFO80in7qkl4LyOKMGgmgRxilhmVzuZkXGQhN3AcLqA0aLGb8yvFLHb9LPWozzYx4P-bmJdHMppSgX7Odi0t1DYwWOzK1b7vGxrU9OD_vq6HfbhU3LtvW7LkZPPWEr4xhYvFfFoFTcEFReIuGCaMqf9xJbPPRJhjFW8NwCs50xiP4tR9eAMowalnBUfChtgh78pwk-552o97mW83feQ5e0KsEKuTvbKCNv6CdeDsbaflGphYYBwvkxk_iPEcETfBU0JbULUKIjk80AHScXEkBE2GyWZYIPlMszZ5Qcnu6f_bajL-pWeEL1vSe8tHKHCNoR0cbW0D_sZQ30tGMFs6G4a630Nb2IXjxFzuxK3QG2Mcs4YbbCNxpu1xjOXMxnpyLuG7FKritqe-Rv_AfsIxJE)

Convex is the play here because Convex rewards are usually a bit higher (2.42% versus Curve’s 1.5% for 3pool). Convex gives out $CVX tokens at the moment, in addition to most of the same rewards you’d get on Curve. It also saves you the extra hassle of managing your veCRV, which would require a lot of work and upfront expenses for a newbie.

There’s one last consideration. Gas costs! Achieving max boosts will require at least 4 transactions (two approvals, two staking transactions), and in some cases it could be more. As a shrimp, you’ll need to consider your payback period based on gas losses.

By way of example, here we simulate the costs of staking into $[MIM](https://email.mg2.substack.com/c/eJwlkMluxCAQRL9mOFpsBnzgkEt-A7H0MCg2WCwT-e_DxFKp1VJ3qfTK2w6x1EufpXX0GaZfJ-gMv22H3qGi0aCaFDQTVG2SSBQ0D0StCqVmnhXgsGnXvQ5A53B78rankj8OIjZCBXppLtT0Muw8YAfPIBmVUmFLrbJEuHAH2xESZA8a3lCvkgHt-tX72R7s60G_p_yob1ieaa5HOlDSFNMprMiKJd8Wuki6CgYMs80pyVa2eC7TVkN9cHxEurThWrf-Z_HlQFVf5WVzjPMYo7dn6nZfUvlwmPlwjJz6ZSBbt0O4Efvd1D-0iZChzgaDsX3Scs4YnbFixTfR7IDLDRNKOJrJoUxX1v8Uf8DgfPk) (~10% rewards tAPY) via 3pool and then staking into Convex. This route took six total transactions, for a total gas cost of 0.096 ETH if gas was 100 gwei. At today’s $ETH prices, it means $300 to get into the pool.

[](https://email.mg2.substack.com/c/eJxVUkuO5CAMPU1llyj8AixYtEaaa0R8HAp1Amkg1Z0-_ZDKaiTLNjb2s_xsdQWf8qn2VGp3qbmeO6gI32WFWiF3R4E8B6fIhIXkiHdOUYcEE10o85IBNh1WVfMB3X6YNVhdQ4pXBZokwlP3VJQvjBLJrZkwInLhIBbBRo3xhDQnyw2sDxcgWlDwgnymCN2qnrXu5UE-HvhvE-viUA5Tqrafg01bC4VNe2h2gWqfl21tanrgP1-3Qz58Sq69l3Xec_IZSgkvaPFSAfZWcUNgdoGwC6Ypc9hPaPncw8iMsYL2RmvSU8KhlwyJXjtDsAHOpaBDIYPe9G-K-rvcc7Ue9zLe7nvI8nbpaLCZuOkRQbSn3NheaId72RLSMbxIYHNb1Q-iYtij74LCI24yCsRGTuWAB47ZRICMRBrBCSODpTzI7PKDjpvH_62oy-pMTx29b0nvrd5D1esQ0kXW3D5sRwz1nCFqs4K7eaz3ObyZnT1EyO1M3Kxro5RSQnCDndh409aIplyOCCPaNWSXWlVU9sgv-AdKoMMh)

Don’t forget that you’ll then need two transactions to get out, (.067 $ETH in a recent simulation at 100 gwei), meaning another few hundred on the way out. To cash out, you’d presumably also need to consider the cost of sending your stablecoin stack back to your centralized exchange (ie Coinbase), and then whatever costs (if any) your exchange charges to withdraw. And you have to pay tax on your yields too! It’s hard out here for a shrimp.

You may be able to move funds around cheaper using certain zap contracts and timing your transactions when gas is low. Still, if you’re spending a few hundred bucks on gas, you put $1000 into a pool, and assume you hit 5%, it will take about _four years_ to recoup your gas fees. If you put $5000 into a pool at 5%, it will take you closer to _a full year_ before you recoup your gas fees. Once you get to $10,000, your payback window is down to a few months. Hence we used $25,000 as the benchmark where you can start to play without so much concern.

When considering staking over a longer payback window, you also have to game out the changing landscape of the Curve Wars over this window. In one year’s time, Curve has changed significantly. If you’re trying to invest $1000 and think you can predict where your funds can sit safely for four years to pay back gas costs, you’re probably wrong.

Yields come and go based heavily on other protocols’ willingness to participate in the Curve Wars, and this can be unpredictable. Over the course of a year, I observed a half dozen pools that seemed to be the a good bet at the time based on conditions to measure how a hypothetical portfolio of $5K staked for a year might perform. These bets included $MIM, $LUSD, $IB, $alUSD, $USDN and $LUSD.

Of these, thankfully none depegged, so it would have been a profit overall. Yields on $LUSD and $ALUSD dropped the lowest, down to 4.12% at the moment. A year in the pool would have earned you about $600 worth of $CRV, a bonus $15 from APY, plus both pools kicked in a few hundred in rewards from their own token. Total gas cost ran around a few hundred bucks in these cases, so it came close to breaking even or making a slight profit if you happened to pick the worst pools.

The best of this batch was $USDN or $MIM. $MIM, as we discussed, nearly depegged so it was certainly with some risk, but this ended up leading to amazing trading fees. $USDN also floats off peg quite frequently, at present trading at $1 to $0.98 for other stablecoins, but it also gives a higher base APY so you still ended up making pretty good yield for the risk.

[](https://email.mg2.substack.com/c/eJxVUsmO5CAM_ZrKLRFrgAOH1kjzGxGLQ6FOIA2ke2q-fkjlNJLlFftZfjjTIOTy0keubbjU0l4H6AQ_dYPWoAxnhbJEr-lMpBJYDF4zjyWXQ6zLWgB2EzfdygnDcdotOtNiTlcHnhUm8_DUTDLFpJ-dlFYKRSkGPNvVKO-RB8A3sDl9hORAwzeUV04wbPrZ2lEf9ONBfndxPk31tLUZ9zm5vPdU3E2Abldo7nnZPqblB_n1dTv0I-Tse7xuy1FyKFBr_Iaerw3g6B03BOEXCL9gurKn-4ReLyMgbq2TbLTG0JFRAaPiWI7GW0osCKEkmyqdzG7-5mR-6r1Xn3Ef4-2-l6xvFxMnYOZ29NzByHz3LL1Cua6YIG-oXxfO2R-C0HSkMERNEOmCJOZIMDWRSRA-U6CIqn5NyunkmIiq-PJgaA_kvxMNRb_y06QQejEEZ47YzDbFfJG19Af7mWJ7LZCM3cDfPLb7O7yZXQIkKP2b-MW0TiljlJIOO3N009aJZkIhTDAbOrLPvStpd5Zv-AdHtcTD)

This illustrates where life is bad for the shrimp. Diversifying over several pools is the best way to smooth out this risk and get better gains, but gas costs compel you to just pick one pool and let it all ride. Meanwhile, a whale could easily diversify, tossing five or six figures into every pool and just rotating out of the duds every month, easily making profit. Life is always better for the wealthy.

If you do want to go the route of gambling everything on one pool, I’d research which protocols [you see bribing](https://email.mg2.substack.com/c/eJwlkEtuxCAQRE8zLC2-BhYsssk1LD5tBgWDhfFEvn1wLJV60d2l0itvO8TaLrPXo6N7LP3awRT4PTL0Dg2dB7QlBcNmqrQkEgXDA1FCoXQsawPYbMqmtxPQfrqcvO2plttBZk3ojN5GMHDErpx4x5jXEogjLtBVa8WFluoJtmdIUDwY-EC7agGUzbv3_Xixrxf9HsrZbnayqa21eRgLlAzFdAgrIrDkeqKTpGJmwDDTTkkm2OS5TLqF9uJ4i3Q6Tnd0638mXzfUzFXftsQ4jjF6u6du85TqjbKMh-0sqV8LFOsyhIeyP2X9cy8RCrRRYlhsH8CcM0ZH7CzwAzVq4FJjQglHIznU4SrGn-0Df243fiE) fairly consistently on Votium. These protocols are arguably more committed to the Curve Wars and may find ways to max out this yield for some time to come. Toss your money into their associated stablecoin pool. All of these coins playing the Curve Wars have their drawbacks so research them heavily, but you’ll have to accept higher risk to get that higher reward.

Also, if the price of $ETH shoots up over the next four years, don’t forget that your payback window is even longer because gas costs will also rise accordingly. If $ETH hits $100K, you will likely never be able to get your $1K deposit out and should have just parked your money in $ETH. Shrimp playing in stables have to pray for price of $ETH to tank.

Of course, if you’re already considering accepting higher risk, you may want to just graduate to the better yielding strategies…

# V2 Pools

So maybe now you’re convinced you need some more risk in your life if you don’t want to fall prey to gas costs. In this case, you should look into Curve’s new v2 pools.

Other AMMs make it very challenging for LPs to earn money on riskier assets. For instance, an LP on Uniswap v3 will need to rebalance their position frequently to keep up with price swings.

[

![Twitter avatar for @0xAlunara](blob:https://mail.protonmail.com/9f696ff4-7553-483e-a4ed-6b329f39e49a)Alunara @0xAlunara

Without active market makers monitoring and adjusting concentrated liquidity Uni v3 pools can seriously wreck you on price movements. Curve v2 fixes this.

](https://email.mg2.substack.com/c/eJwlkEtuxCAMQE8zLCMwJMCCRTe9RsTHk0FNSMRnprl9SSNZyMiYZz9vKy57Ps2xl0quY67ngSbhp6xYK2bSCuY5BsMnUFoySYIRgalRkVjmZ0bcbFxNzQ3J0dwava1xT1cHmzSDibyME8pRD6C1lI7J58TAK_BUsVFNlLsbbFuImDwafGM-94RkNa9aj_LgXw_47lE_8Rpp8PvWb_T3a23JZtvzUm1tpSdMaEYpl2LUIIAzJoFEAxR6XDwqhR5gkDBOHDnl2inJRz54IaPOIT8E3RYYSnP9S_9zoUg25_6yaVl6cVm8PWK16xD3a9-5P9haivWcMVm3YrhV1Nvov5x5wYS5mw6zrd2KEJxDx04jvTfvroTUlAETpJPD3ruS8S2_8Q8ztIdx)[

February 8th 2022

2 Retweets4 Likes

](https://email.mg2.substack.com/c/eJwlkEtuxCAMQE8zLCMwJMCCRTe9RsTHk0FNSMRnprl9SSNZyMiYZz9vKy57Ps2xl0quY67ngSbhp6xYK2bSCuY5BsMnUFoySYIRgalRkVjmZ0bcbFxNzQ3J0dwava1xT1cHmzSDibyME8pRD6C1lI7J58TAK_BUsVFNlLsbbFuImDwafGM-94RkNa9aj_LgXw_47lE_8Rpp8PvWb_T3a23JZtvzUm1tpSdMaEYpl2LUIIAzJoFEAxR6XDwqhR5gkDBOHDnl2inJRz54IaPOIT8E3RYYSnP9S_9zoUg25_6yaVl6cVm8PWK16xD3a9-5P9haivWcMVm3YrhV1Nvov5x5wYS5mw6zrd2KEJxDx04jvTfvroTUlAETpJPD3ruS8S2_8Q8ztIdx)

Fortunately, Curve’s v2 setup is far friendly to passive LPs. Curve’s v2 pools rebalance automatically, so once you’re into the pool then you can park yourself and forget it while you earn yield. Here’s what your options look like today.

[](https://email.mg2.substack.com/c/eJxVUkuO5CAMPU1llyj8AiyyaI0014gMOBTqBNJAuqfm9EMqq5Es2_j3LD8sVPQpv-YjldpdaqmvA-eIP2XDWjF3Z8G8BDeziSotiezczB1RQnWhLGtG3CFsc80ndsdptmChhhSvDjJpQqfuOROGbmVMSjcRZTVMoFfKDZNGg4CV3sBwuoDR4ozfmF8pYrfNz1qP8mAfD_q7iXVxKKcpFeznYNPeQmEHj82uWO3zsm1MTQ_66-t22IdPybX3ui1HTj5jKeEbW7xUxKN13BBUXCDigmnKnPYTWz73OApjrOK9AWA9ZxJ7LYjqwRlGDUqpFR8KG2CHvynCT7n3ajPuY7zd95Ll7VqLmjAGPRWr6LkyplcgeU8mMTGu1ARWLpPifxjXwxF9F2Y60iajImKULUgHSVstspFpoyQTbLBcBp1dfvBx9_S_E3V5fqUnRO9b0nsLR6iwDSFdZC2tYD9jqK8FI5gN3c1jvb_Dm9nFY8TcvolboDZKOWeMNthJjDdtjWgu9Ugo4V1Ddql1xdme-Rv_AZhkw7o)

If you’re in the typical V2 pool, you’re likely getting pretty good rewards in the form of $CRV. Generally, V2 pools expose you to $ETH and one other crypto asset. So ultimately you’re susceptible to the fluctuating price of $ETH. If $ETH tanks to zero, you lose it all. Fortunately I happen to be bullish on $ETH, so this is more feature than bug for me, but your appetite may differ.

You also are at risk of impermanent loss, as your portfolio rebalances with price changes. In other words, you end up with more exposure to whichever asset performs worse. Since most alts struggle to outperform $ETH, practically speaking this means you should pick a pool where you’re OK holding the other coin in the pair. If your coin outperforms $ETH, you only get about half the gains, diluting yourself a bit with worthless $ETH. For pools like [CRVETH](https://email.mg2.substack.com/c/eJwlkM2KhDAQhJ9mcpT8meghh73Ma0h-2hhWE4ntLL79xhGKpqG7KL7yFiGWepm9HEjuMeG1g8nwd6yACJWcB9QpBSMUH0bNNAlGBjb0A0nHNFeAzabVYD2B7Kdbk7eYSr4dTI2MK7KYWYBzvWSzo8IpHoKlwfVacRhmMQr9BNszJMgeDHygXiUDWc2CuB8v8fPi7yZ_1g90c7rXtuFCkuGUN9GB9VTLseOd5r0SIKgY3aBFLzovdRprqC9Jt8i743QHWv_b-bKRaq6y2BxjO8bo7Z7Qrl0qN8rUHrYzJ7wmyNatEB5KfMr6ck8RMtRWYpgsNmApheAtVvX0gWo1SD1SxpkkLTmU5srmC_IP4eh-oA) and [CVXETH](https://email.mg2.substack.com/c/eJwlkEtuhDAQRE8zXiL8h4UX2eQayJ8GrICN7GYSbh8zSKVWS92l0itvEZZcLnPkiuQeE14HmAS_dQNEKOSsUKYYDFdsGDXVJBgR6CAHEus0F4Ddxs1gOYEcp9uitxhzuh1UjZQpshrJVVBOQXBeOqn1bK0e6MzkGMSghHuC7RkiJA8G3lCunIBsZkU86ot_vdh3kz_LG7o53uv7D3Al0bCeNfUDlb0WY8c6zaTiwHs-ukFzyTsvdBxLKC_R7wvr6ukqWv_T-byTYq682rQs7bgs3h4R7dbFfKNM7WE_U8RrgmTdBuGhxKesD_e0QILSSgyTxQYsBOesxSrZP1CtBqHHnjIqSEsOubmS-YD8A8cyfos), where the other coin happens to have some productive upside, it feels pretty cozy to me.

In practice, lots of these $ETH-paired coins tend to see price movements roughly in line with $ETH, so these pools are roughly stable. Then you earn pretty good $CRV yields on top that helps paper over the differences. Hence why I happen to think these pools are a pretty sharp place to hang out.

Let’s review two possible strategies for playing with v2 pools, first if you want to play with dollars, second if you want to play with $ETH.

### V2 with Dollars

If you’ve got dollars, let’s imagine it’s last week where $BTC and $ETH crashed. If you believed it was roughly at a bottom and wanted to buy the dip, your play would be to get your dollars into $Tether and buy into [TriCrypto2](https://email.mg2.substack.com/c/eJwlkM2KxCAQhJ9mPAb_osnBw17mNcRoJyObaNB2lrz9OhMomobuovjKO4Qtl8ucuSL5DIvXCSbBX90BEQppFYqNwQjFp1kzTYKRgU3jRGK1awE4XNwNlgbkbMsevcOY08fB1My4Ii-zwhKkF0wK7hahgheOzUBXRj1wxcMd7FqIkDwYeEO5cgKymxfiWR_i58GfXb6VNwxr7CuW6Mt1YuYkGk55F53YSLWcBz5oPioBgop5mbQYxeCljnMJ5SHpsfGhtqWi87-Dzwcp5sovl7atH7fNuzOi24eYPzi2PxwtRbwsJLfsEG5SvAv7stsNEpReZLAOO7SUQvAeq0Z6g_UqpJ4p40ySnhxydyXzhfkHMbeAUQ). If BTC + ETH rise, then you’d get exposed to about 2/3 of these gains.

Staked into Convex, you’re also earning about 14% in $CRV and $CVX — if $BTC + $ETH drop further and you’re down a bit in dollar terms, the flywheel bonuses help you paper over these losses a bit. It happens that $CRV and $CVX staking are pretty great in a bear market, so maybe the loss doesn’t hit so hard.

[](https://email.mg2.substack.com/c/eJxVUkmO3DAMfE37ZkP7cvBhECDfMLTQamFsyZHkmXReH7mdSwCCpEiRRbDoTIOQy2s-cm3DpZb2OmBO8F03aA3KcFYoS_QzFURpieXgZ-ax4mqIdVkLwG7iNrdywnCcdovOtJjTVYGFxkQMzxkrYbAHLbA13MiVYmWR58xQ65gAdAOb00dIDmb4gvLKCYZtfrZ21Af9eJCfXZxPUz1tbcZ9Ti7vPRR3E6DbFZp7Xra3aflBfvy6HfoRcvb9vW7LUXIoUGv8gh6vDeDoFTcE4RcIv2C6sqf7hJ4vIyBurVNstMbQkVEJo-ZYjcZbSixIqRWbKp3Mbv7kZL7rPVfvcS_j7b6HrG-XELE6JezoMFcjQ5z1flqOyqPVI-04sXzBWIrfUk5HCkOcCSJdkMIcSaYnMknCBQWKqLZKUk4nx2TUxZcHQ3sg_61oKPMrP00KoSdDcOaIzWxTzBdZS_-wnym21wLJ2A38zWO7z-HN7BIgQeln4hfTOqWMUUo6rOD_aOtEM6kRJpgNHdnnXpVmd5Yv-As9EsNy)

I also like this pool for newcomers in terms of its optionality. If you’re sitting in TriCrypto2, you have the capability to exit to $WBTC, $WETH, or $Tether depending on your need. Your bank account only lets you withdraw into worthless dollars.

Plus TriCrypto2 is a fairly major hub in the Curve v2 ecosystem. As more v2 pools launch, we’re likely to see TriCrypto2 become a fairly major hub to route funds, so it could see some nice volume. I could even image people using the [v2 factory](https://email.mg2.substack.com/c/eJwlkE2OhCAQhU_TLI38w4LFbOYaBKG0ySgYLHvi7QfHpEJIQdV734sBYantcns9kNyHx2sHV-D3WAERGjkPaD4nxxUzVlNNkhOJGmlIPvzcALaQV4ftBLKf05pjwFzLPUGVpUyRt2M8cmGs0TYqzZVKiVsrI9NyNn1XeITDmTKUCA4-0K5agKzujbgfL_71Yt-94tk-MMy5X-cQsfu-mw06BMmOjazXaKgctbADGzSTigMfuZ2M5pIPUehsW2ovMW4LG45zOjDEnyHWjTR31Xcoy9IflyWGPWNYh1xvKN8_bGfJeHkoYVohPbz4xPafgF-gQOtOkg_Y0YXgnHVZJccHrwcitB0po4J05VT7VHH_SH_9u4Ei) to launch metapools with the TriCrypto2 LP token as one of the coin pairs. Of course none of this is a guarantee.

The risks of the TriCrypto2 strategy? If Bitcoin and Ethereum drop then you’ll be on the losing side of the bet. Additionally, TriCrypto2 may be a major hub, but major hubs don’t always mean great yield. 3pool is also a major hub, and while I love the 3pool_lp token for its utility and composability, its rewards yield is unremarkable (~1.4%). TriCrypto2 rewards have dropped from its launch, and if I had to guess I’d guess it continues to slide as more v2 pools enter the competition.

For whatever it’s worth, I made this exact move when $BTC plunged into the mid 30s. When gas was cheap I rounded up all the underperforming dollar pools I was sitting in, batched into Tether, dumped it all into TriCrypto, and staked on Convex. If the market does go up, then maybe I’ll pull out some ETH when things go well. If the market goes sideways, I’m earning good yield. If the market goes down, I’ll put more dollars into it.

In real number terms, I made this transaction a bit over a week ago with ~$33K worth of Tether, when $BTC was around $37K and $ETH $2.5K. Today the price of $BTC and $ETH are closer to $44K and $3.1K. If I liquidated my position to $USDT today, I could withdraw $54K, and I’d have a bonus 58 $CRV and 9.4 $CVX from my week of staking, worth about $1K, amounting to a net gain of $18K.

[](https://email.mg2.substack.com/c/eJxVUkuO5CAMPU1ll4jwCbDIojXSXCMy4FCoE0gD6Z6a0w-prEaybGNjP8vPFir6lF_zkUrtLrXU14FzxJ-yYa2Yu7NgXoKb2USVlqPs3MzdqITqQlnWjLhD2OaaT-yO02zBQg0pXhXjpEc6dc95VasyotXbUQEIBlqvkittFXBijLiB4XQBo8UZvzG_UsRum5-1HuXBPh70dxPr4lBOUyrYz8GmvYXCDh6bXbHa52Vbm5oe9NfX7bAPn5Jr73Vbjpx8xlLCN7Z4qYhHq7ghqLhAxAXTlDntJ7Z87pEIY6zivQFgPWcSey1G1YMzjBqUUis-FDbADn9ThJ9yz9V63Mt4u-8hy9vlStKVge0nqmXPKVO9dsT2pK1I2lGvoNeFKvGHseGIvgszJbQJUaMgkuuBDpKKiSEjTBslmWCD5TLo7PKDk93T_zbU5fmVnhC9b0nvLRyhwjaEdHG1tA_7GUN9LRjBbOhuGut9DW9iF48Rc7sSt0BtjHLOGG2wkyA3a41nLjUZ6ci7huxSq4qzPfM3_gOnOMNq)

At 100 gwei, the gas to do this would cost $208. Not bad for a week’s work. I’ll just let it ride. Don’t forget the tax burden when you claim and cash out, which can be a headache in terms of paperwork.

### V2 with $ETH

Let’s consider a different strategy. Say you bought the dip and put some money into $ETH. $ETH is wonderful, but there’s no sense in just sitting around looking at it. Presumably you’re looking at amounts under 32 $ETH, otherwise you’d run a validator node and earn the guaranteed 5%.

Much of the same analysis as above applies. The pure $ETH v1 pools are not ideal places for LPs.

[](https://email.mg2.substack.com/c/eJxVUkuO5CAMPU1ll4jwCWTBojXSXCMy4FCoE0gD6Z6a0w-prEaybGNjP8vPFir6lF_6SKV2l1rq60Ad8adsWCvm7iyYl-A0m6ia5Sg7p7kblVBdKMuaEXcIm675xO44zRYs1JDiVTFO80in7qklTJNQ1FCjHBNyXYmyFOQq5CQMc_wGhtMFjBY1fmN-pYjdpp-1HuXBPh70dxPr4lBOUyrYz8GmvYXCDh6bXbHa52Vbm5oe9NfX7bAPn5Jr73Vbjpx8xlLCN7Z4qYhHq7ghqLhAxAXTlDntJ7Z87pEIY6zivQFgPWcS-1mMqgdnGDUo5az4UNgAO_xNEX7KPVfrcS_j7b6HLG-XjUJIw11PwIieWzn1MHPsV-6aMM4JV8uk2J-R8OGIvguaEtqEqFEQyeeBDpKKiSEjbDZKMsEGy2WYs8sPTnZP_1tRl_UrPSF635LeWzhChW0I6SJraR_2M4b6WjCC2dDdPNb7HN7MLh4j5nYmboHaKOWcMdpgJ0Fu2hrRXM5kpCPvGrJLrSpqe-Zv_Af9PsN5)

Of them stETH and seth are the best if you’re entirely risk averse. You’re not earning more than ~2%, or building up some $LDO governance token for the case of stETH. If you were running a validator node, your ETH is frozen, so maybe you take the ~2% in exchange for liquidity.

If you want a riskier option, TriCrypto is not the option I’d look at. I personally suspect $ETH price is low and likely to go up. When you’re buying into v2 pools, you want to buy in with the asset you think is overpriced. If you do think $ETH is going to nuke from here, then maybe you might buy into TriCrypto. At any rate, shrimp shouldn’t be really be timing the market and trading frequently.

If I was looking to gamble my $ETH, I’d look at the various v2 pools. All of the pools that have got through governance rewards are earning really good rewards at the moment.

[](https://email.mg2.substack.com/c/eJxVUkuO5CAMPU1ll4hvCAsWrZHmGhEfh0KdQBpIdadPP6SyGsmyjY39LD9bXcGnfKo9ldpdaq7nDirCd1mhVsjdUSDPwSk6kkkKLDqnmMMTn7pQ5iUDbDqsquYDuv0wa7C6hhSvCjxKTMbuqZDFUhIJAgNBckESmjJkIRjMogW7gfXhAkQLCl6QzxShW9Wz1r086MeD_G1iXRzKYUrV9nOwaWuhsGkPzS5Q7fOyrU1ND_Ln63boh0_JtfeyzntOPkMp4QUtXirA3ipuCMIvEH7BNGUO-wktn3tA3Bg7sd5oTXtGBfSS46nXzlBiQAg5saHQQW_6N0X9Xe65Wo97GW_3PWR5u2QkYCduey246BnRuDduMT121DBnuUQSzePEfwjFwx59FxRBpAmaMEeCyYEMgvCRAkVUmklQTgfLRJDZ5QdDmyf_rajL6kxPHb1vSe-t3kPV6xDSRdbcPmxHDPWcIWqzgrt5rPc5vJmdPUTI7UzcrGujlDFKSYMdObppa0QzIREmmHUN2aVWFZU98gv-AZIQw_s)

Based on the above principle (buy in with the overpriced asset) you might want to consider here which asset is likely to outperform $ETH going forward, in which case you would gain from putting in $ETH. I’m not terribly familiar with $T, so I can’t comment on this one. $SPELL took a beating, so you could see it outperforming if it recovered. That $YFI yield is bound to drop, but it may be worth a look too.

Personally I’d look at $CRV and $CVX because they are my favorite assets and I’d feel quite cozy in these pools. If they lose value against $ETH, then I wouldn’t be heartbroken to be get a bit more $CRV or $CVX, for reasons we’ll see in the next section.

For what it’s worth, this is exactly what [PAC DAO](https://email.mg2.substack.com/c/eJwlkM1uxCAMhJ9mOUbhL8CBQy99jcgBL4uaQARk2_TpSxppZFmyR6NvHDQMuZx2z7WRa8zt3NEm_K4rtoaFHBXLHL3lE9NGUUW8FZ5qqUms87MgbhBX28qBZD-WNTpoMafLQSdD2UReVnkntPTcU6WkV8wtEsAAwlOjdkLcwXD4iMmhxTeWMyckq321ttcH_3iwz64d3PBz_vaNRMtG1jVqKkclzMAGxeTEkY_cLFpxyQcnVDTFl4cYt8CGeiy1gfsaXN5IsWd-QQqhH0NwsMcG6xDzxTD3h-1IsZ0zJlhW9Ddeu1v6B54DJiy9PT9D66RCcM567CTHm6bzC2VGyqggPdnn7krWHeWNfzVne_8) did with its modest treasury. Two weeks ago it staked about 30 ETH (a bit under $100K) into the CVXETH pool and dumped it into Convex. In the intervening time, the market collapsed, but $CVX/$ETH stayed fairly well pegged. And the pool earned 141 $CRV and 23 $CVX, worth about $1100. Pretty good for a volatile few weeks. If it keeps it up, it could have enough to flywheel!

# Flywheel

OK, last strategy here. Potentially this is the “riskiest” because it’s untethered to any “familiar” assets. Here you use your dollars to buy $CRV or $CVX, meaning that if these prices collapse you lose everything.

On the plus side though, you get to take a spin on the flywheel. It’s delivering the juiciest returns, which you presume means you’re absorbing the most risk. Still, once you try it, you probably won’t want to go back.

[](https://email.mg2.substack.com/c/eJwlkEtuxCAQRE8zLC2-BhYsssk1LD5tBgWDhfFEvn1wLJV60d2l0itvO8TaLrPXo6N7LP3awRT4PTL0Dg2dB7QlBcNmqrQkEgXDA1FCoXQsawPYbMqmtxPQfrqcvO2plttBZk3ojN5GMHDErpx4x5jXEogjLtBVa8WFluoJtmdIUDwY-EC7agGUzbv3_Xixrxf9HsrZbnayqa21eRgLlAzFdAgrIrDkeqKTpGJmwDDTTkkm2OS5TLqF9uJ4i3Q6Tnd0638mXzfUzFXftsQ4jjF6u6du85TqjbKMh-0sqV8LFOsyhIeyP2X9cy8RCrRRYlhsH8CcM0ZH7CzwAzVq4FJjQglHIznU4SrGn-0Df243fiE)

You’ve got two ways to flywheel, $cvxCRV or $CVX. You need not obsess about one or the other since both give you exposure to each other.

### $cvxCRV

I’d probably recommend more cautious users start with $cvxCRV due to the fabled three cash flows.

[

![Twitter avatar for @CFrogE1](blob:https://mail.protonmail.com/f0f594fc-60b2-49e8-b849-b50843501368)MoonFrog || $CRV Booster || ve(👑,👑) @CFrogE1

Don't worry Anon. All you have to do is bend a knee and pledge allegiance to Curve. The 3 Incomes will save you from The Bera Market. FlyWheel it until you turn Green. $CVX $CRV $cvxCRV $3CRV 🐸😁

](https://email.mg2.substack.com/c/eJwlkNuOhCAMhp9muDQcRS-42Gx2XsMgVIesgoEyE99-cU2apk0Pf_s5i7CmfJojFSSXm_A8wET4lA0QIZNaIE_BG9HzYdRME2-kZ4MaSCjTkgF2GzaDuQI56rwFZzGkeE2wfmS8Jy8zLKwX3kmmloEK3hyosVesV24RdBG3sK0-QHRg4A35TBHIZl6IR3mIrwd_NsNPuE7qXNpb9v3Maf1hLSposZYWMKmFFJxxzeSgpKR0JMFwypvRgSmq5djxTnPVCxBUjPOghRKdkzqM2eeHpPvKu1LnttL9XkIkmzO9bFzXVlxXZ4-AdutCur6dWsNeY8BzgmjnDfwNAm-e_2imFSLkxtlPFhsTKYXgTbZX9P67kZJ6pIwzSZqyT20qGlfzG_4A8-qGiA)[

December 21st 2021

8 Retweets91 Likes

](https://email.mg2.substack.com/c/eJwlkNuOhCAMhp9muDQcRS-42Gx2XsMgVIesgoEyE99-cU2apk0Pf_s5i7CmfJojFSSXm_A8wET4lA0QIZNaIE_BG9HzYdRME2-kZ4MaSCjTkgF2GzaDuQI56rwFZzGkeE2wfmS8Jy8zLKwX3kmmloEK3hyosVesV24RdBG3sK0-QHRg4A35TBHIZl6IR3mIrwd_NsNPuE7qXNpb9v3Maf1hLSposZYWMKmFFJxxzeSgpKR0JMFwypvRgSmq5djxTnPVCxBUjPOghRKdkzqM2eeHpPvKu1LnttL9XkIkmzO9bFzXVlxXZ4-AdutCur6dWsNeY8BzgmjnDfwNAm-e_2imFSLkxtlPFhsTKYXgTbZX9P67kZJ6pIwzSZqyT20qGlfzG_4A8-qGiA)

To run this, you’ll convert your $CRV to $cvxCRV using the [factory pool](https://email.mg2.substack.com/c/eJwlkE2OwyAMhU9TlhEBws-CxWx6DUTASdEkEIHTUW4_tJGeLEu29fy94BHWUi97lIbkUxxeB9gMf20DRKjkbFBdipZLpo0aFYlWxFFPmqTmlgqw-7RZrCeQ45y3FDymkj8XozQjk-RlzeS1j0p4KqWWbFqC5mpZJEi-RKbMbezPmCAHsPCGepUMZLMvxKM9-M-DPbvCWd8wLKm3iw_Y_-4dYyRZRlkX1eNElTADGxSbJAdOuZm14hMfglDJ1Fgfgu4rG9o5N_ThdwhlJ9Ve5eXzuvbhugZ_JPTbkMoHyPWF_cwJLwfZzxvEmxXvyL70boUMtUcZnceOLQTnrNvKid5oPQyhDB3ZKEh3jqVfZfvF-QcC_3-g). Ideally you can time this to when the peg is a bit off, like now, so you get a small bonus.

[](https://email.mg2.substack.com/c/eJwlkE2OwyAMhU9TlhEBws-CxWx6DUTASdEkEIHTUW4_tJGeLEu29fy94BHWUi97lIbkUxxeB9gMf20DRKjkbFBdipZLpo0aFYlWxFFPmqTmlgqw-7RZrCeQ45y3FDymkj8XozQjk-RlzeS1j0p4KqWWbFqC5mpZJEi-RKbMbezPmCAHsPCGepUMZLMvxKM9-M-DPbvCWd8wLKm3iw_Y_-4dYyRZRlkX1eNElTADGxSbJAdOuZm14hMfglDJ1Fgfgu4rG9o5N_ThdwhlJ9Ve5eXzuvbhugZ_JPTbkMoHyPWF_cwJLwfZzxvEmxXvyL70boUMtUcZnceOLQTnrNvKid5oPQyhDB3ZKEh3jqVfZfvF-QcC_3-g)

With $cvxCRV, you then [stake it into Convex](https://email.mg2.substack.com/c/eJwlUEmOhDAMfE3niLJB4JDDXOYbURaTjgYSlKUZfj9hkCxLtqtcqrK6gk_5kkcqFd1N1esAGeEsG9QKGbUCWQUn2UTnRRCBnOSOzOOMQlFrBth12GTNDdDRzBasriHFm0GmhdAJvaWGdeXWGUspXwi3Bgsz45EJwEZwyh5h3VyAaEHCB_KVIqBNvms9yot9veh3r_M8B5viB37XEHWH9mnv-1L1D6AgKaa98ExGLPgy0EHQcWLAMFvMLNjIBstFWLLLL453T4fSTOfan_sPyvJKbx2970fvrT5C1dsQ0m1LdcDeYqiXgqjNBu5xXJ_g_jNQHiLkHqhTunbznDNGu-w04sdgj4SLBRNKOOrKLnVWlLblD_wBcmqDOA) (this whole transaction can be done right on Convex).

Once you’ve staked your $cvxCRV, you’re directly earning both $CVX and $CRV. These two tokens can be fed directly back into the flywheel when your stash becomes large enough to offset gas costs.

It also provides you a steady flow of cash in the form of the 3pool LP token, which can be cashed into USDC, Tether, or DAI. This means if $CRV and $CVX both collapse, you still end up with some cash back for your troubles. This cash exposure is why I’d suggest this pool for newcomers who may be nervous and still believe dollars aren’t worthless.

Staked $cvxCRV also has a one-click button to harvest all your rewards and restake them, giving you something like compounding. The tough part for shrimp here is that the button is very expensive, you may need to pay in the range of 0.1 $ETH. You’ll want to have a few thousand worth of gains to make this worthwhile. If you stake $5,000 worth of $CRV, it might be several months before you get to compound.

Also watch out, because $CVX emissions may effectively dry up by the end of the year. Maybe your $5K investment in $CRV gets you ~50 $CVX tokens by this time, which is nice. If $CVX shoots up in value though, you might wish you dropped the $5K into $CVX today to get 3-4x the quantity.

Last thing to note is that if you want to cash out, you’ll be at the mercy of the aforementioned $CRV-$cvxCRV bridge. The discount pretty much only goes in one direction, you may have to pay a premium to go the other direction when the peg is off.

### $CVX

Convex is also a great flywheel choice, particularly thanks to the recent development of [the Union](https://email.mg2.substack.com/c/eJwlkMtuxCAMRb9mWEa8SRYsuulvRDw8GVQCEZCp8vf1NJJlJIx1uCe4AVttlz1qH-TT1nEdYAv89gxjQCNnh7amaIXm82KYIdHKyGY1k9TXZwPYXcp2tBPIcfqcghupls8G0wvjmrxs8NSwqDVn0jMwajY4MJoqMwN34nmD3RkTlAAW3tCuWoBk-xrj6A_x9eDfWDm73U0utWdtAf7vBPazIBDPHXaPH06WU45FZ6aokcvEJ8OVFiCoWPxshBJTkCYtLbaHpPvGp376Plz4mULdSbNXfbmybTjctuCONFyeUv3EW_HBjrxxrVCczxDv5OMW-O9i3aBAQ7FxdQMlSCkER6xW9A6KaqRZKEMdBMmx4lax4Wxv-AOT1YO_).

[Locking into $CVX](https://email.mg2.substack.com/c/eJwlUMuOhCAQ_JrhtoaXAgcOc9nfMAg9DBkFA6jj3y-uSaeT7q7qSpU1FXzKp15TqehqYz1X0BGOMkOtkNFWII_BaTZQqQQRyGnuiOwlCmV8ZYDFhFnXvAFat2kO1tSQ4sUggyJ0QG8thDNUMSKF7SWxUkllLJdCMSmIfZFb2GwuQLSgYYd8pgho1u9a1_Jgzwf9bXUcR2dT3OH7CtE0aJuWtp-T_fzY_YuCppi2wpL0WHDV0U7QfmDAMFOTFKxnneUiqOzyg-PF065sU6nGfq5XKOszvU30vh29t2YN1cxdSJezsQGWLYZ6jhDNNIO7Tdc7u_8YRg8RcsvUjaY2_5wzRpvs0OPbY0uFC4UJJRw1ZZcaK2q75R3-ADCDg4c) gives you some $CRV back, so you can get some exposure to the above. You can use your vlCVX (vote locked Convex) to play the [Votium game](https://email.mg2.substack.com/c/eJwlkEtuxCAQRE8zLC2-xl6wyCbXsNrQw6DYYOFmIt8-TCyVWuqfSq88EMZSL3eUk9inLHQd6DL-nhsSYWXtxLqk4NQop9kKy4LTQUxmYulcnhVxh7Q5qg3Z0dYteaBU8udDjLOQI3s5MMFCMFo9-TrKFQAm00dqBY1BPvE2hhYSZo8O31ivkpFt7kV0nA_19ZDfXe9Cqe0DHEdvWHKSyy4-CcOtngc5WGlGhYqreZ2sMmrw2qa5hvrQfI9yONt6EvifwZedVXeVF-QY-zJGD0ci2IZUPhhLP9hbTnQtmGHdMNyEdAf1z7xEzFh7gGEB6rBaKyW77Wj4DdQj0HbmQgrNunMo_Ss73-ob_wAwdn2M). Every two weeks, you get to go shopping. Protocols will deposit bribes in exchange for your votes, so you can pick and choose which bribes you’d like to receive. Plus it’s gasless, so it’s a fun way for shrimp to play on L1.

The downside for shrimp is that you have to pay gas to claim these bags. If you are overly diversified, you’ll have tiny bags you can never afford to claim. Assume it costs ~0.01 ETH and plan accordingly. Practically speaking, you’ll be picking one strategy and sticking to it.

Fortunately, there’s a better way to max out your yields. Simply delegate your vote vlCVX to Votium on their site. Votium will optimize your votes, which sounds great but historically it meant you had the most diversified portfolio with a ton of small bags you could never claim.

[![Twitter avatar for @crypto_condom](blob:https://mail.protonmail.com/47f72b63-07f8-458b-8a14-73fd9889967b)CryptoCondom @crypto_condom

📢ATTENTION smol $vlCVX holders. @0xAlunara has created The Union. It will convert your @VotiumProtocol bribe into $cvxCRV & auto compound it for ⬆️ APR. No claiming required; it will continue to grow in the Pounder. A 2⃣% fee is applicable. 🤝](https://email.mg2.substack.com/c/eJwlkE2OwyAMhU9TlhG_ARYsZjPXiAi4KZoEInBa5fZDGsmybGHz_L7gEZZST7eXhuRKE547uAyftgIiVHI0qFOKTozcWM00iU5GZpQhqU3PCrD5tDqsB5D9mNcUPKaSrw02WsZH8nKjHJ_eg5qfevZM2Cd4RilwGmah9GhuYX_EBDmAgzfUs2Qgq3sh7u0hfh78twd-0nXSEMrWu1DPHcsUSo7fvqHHo_WCSSOUNUwKKphhnFpNkuOU96CGKaqlHfiguRoF9Bk7Gy2UGILUydZYH5JuCx_aMfcvw98lR6o7y8vnZemPyxL8ntCvQyqX537Cth054TlB9vMK8caBN9UvoGmBDLXTjpPHTkZKIXiXHRW93XdeUlvKOJOkK3dLPmUXjvqGf2Zkiqc) [llama.airforce/#/union/member](https://email.mg2.substack.com/c/eJwlkMtuxCAMRb9mWEa8SRYsuulvRDw8GVQCEZCp8vf1NJJlJIx1uCe4AVttlz1qH-TT1nEdYAv89gxjQCNnh7amaIXm82KYIdHKyGY1k9TXZwPYXcp2tBPIcfqcghupls8G0wvjmrxs8NSwqDVn0jMwajY4MJoqMwN34nmD3RkTlAAW3tCuWoBk-xrj6A_x9eDfWDm73U0utWdtAf7vBPazIBDPHXaPH06WU45FZ6aokcvEJ8OVFiCoWPxshBJTkCYtLbaHpPvGp376Plz4mULdSbNXfbmybTjctuCONFyeUv3EW_HBjrxxrVCczxDv5OMW-O9i3aBAQ7FxdQMlSCkER6xW9A6KaqRZKEMdBMmx4lax4Wxv-AOT1YO_)

[

January 19th 2022

27 Retweets104 Likes

](https://email.mg2.substack.com/c/eJwlkE2OwyAMhU9TlhG_ARYsZjPXiAi4KZoEInBa5fZDGsmybGHz_L7gEZZST7eXhuRKE547uAyftgIiVHI0qFOKTozcWM00iU5GZpQhqU3PCrD5tDqsB5D9mNcUPKaSrw02WsZH8nKjHJ_eg5qfevZM2Cd4RilwGmah9GhuYX_EBDmAgzfUs2Qgq3sh7u0hfh78twd-0nXSEMrWu1DPHcsUSo7fvqHHo_WCSSOUNUwKKphhnFpNkuOU96CGKaqlHfiguRoF9Bk7Gy2UGILUydZYH5JuCx_aMfcvw98lR6o7y8vnZemPyxL8ntCvQyqX537Cth054TlB9vMK8caBN9UvoGmBDLXTjpPHTkZKIXiXHRW93XdeUlvKOJOkK3dLPmUXjvqGf2Zkiqc)

Fortunately, the ever helpful Llama Airforce created [the Union](https://email.mg2.substack.com/c/eJwlkMtuxCAMRb9mWEa8SRYsuulvRDw8GVQCEZCp8vf1NJJlJIx1uCe4AVttlz1qH-TT1nEdYAv89gxjQCNnh7amaIXm82KYIdHKyGY1k9TXZwPYXcp2tBPIcfqcghupls8G0wvjmrxs8NSwqDVn0jMwajY4MJoqMwN34nmD3RkTlAAW3tCuWoBk-xrj6A_x9eDfWDm73U0utWdtAf7vBPazIBDPHXaPH06WU45FZ6aokcvEJ8OVFiCoWPxshBJTkCYtLbaHpPvGp376Plz4mULdSbNXfbmybTjctuCONFyeUv3EW_HBjrxxrVCczxDv5OMW-O9i3aBAQ7FxdQMlSCkER6xW9A6KaqRZKEMdBMmx4lax4Wxv-AOT1YO_) to solve this problem, especially for shrimp. When you join the Union, your rewards will get automatically forwarded to their Pounder, which will automatically compound all your tokens until you claim it (in the form of one token of your choosing). This really makes Votium great for shrimp, since the combined dust from several bags can add up.

Lately $vlCVX has earned in the neighborhood of $0.50 every two weeks. If this stays constant, you might expect to pay back your $CVX investment within a couple of years. Of course, your gamble is that $CVX price and bribes both increase to lessen this period. Given the moves Convex is making with FRAX and possibly other veTokens, it’s a bet I’d personally make. The downside risk, of course, is an utter collapse of Convex means you’re left with approximately 0.

Another downside of this strategy to mention is that you do need to keep relocking your vlCVX every couple of months, which costs a bit of gas. For this reason, I generally suggest new users play with the more passive $cvxCRV until they start to build up more sizeable positions.

---

However you flywheel, I do personally believe the ecosystem is far friendlier to shrimp than most other protocols. We’re interested in hearing any strategy from you though, within the flywheel or outside. Cryptocurrency offers tremendous promise to allow shrimp the opportunity to level up, so we’d look forward to any and all strategies that help us achieve this promise. WAGMI(NFA)!