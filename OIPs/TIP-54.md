| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-54 |  Thales referrals program | Implemented | Danijel | Enable referral program into Thales AMMs | https://discord.gg/rPpPcMXSeU | 2022-05-26


## Simple Summary
Add the concept of on-chain referral program into Thales AMMs

## Abstract
This TIP proposes to commence an affiliate program via referrals and send sUSD from every AMM trade to the referrers while program is ongoing.

## Motivation
With Thales having released or about to release a number of unique and innovative products as well as having commenced the buyback&burn program, it feels like a good time to focus on user acquisition and boosting protocol volume.  
By introducing the referral/affiliate program, Thales users can generate links and share those with potential traders. If such new traders start generating volume on Thales protocol, the referrers get a percentage from each trade paid in sUSD directly.  
As we want to get as much fees into SafeBox as possible, I am proposing to pay the referral fee out of the AMM fees, rather than take a cut of the SafeBox fees.    

In addition I am proposing to maintain a leaderboard of all referrers and dedicate a bucket of 20k OP tokens from Protocol Incentives to be allocated at Thales council discretion to top referrers at arbitrary time during the program.  

Initially Thales AMM and RangedAMM will be supporting this program. Exotic and Sports products will be considered at a later point due to technical overhead.

Regarding marketing initiatives:  
  
Affiliate/referrals are an integral part of marketing plans and they come in different formats. There are different examples from Binance, Okex, PERP protocol, KNC, and many others projects related to web3. If we delve into web2 there are tons of other examples too.
Thales hasn't delved into using this marketing tool yet and right now, with the products matured and already iterated with community feedback we feel it's the right time to start tapping into this and trialing it.

Why affiliate/referrals work (in general)?  

- The idea is to orchestrate and put a system in place to basically boost the word-of-mouth we already have (because we've already been developing the products and iterating those with the community, so now they are finally at the point where we can start reaching out outside our existing userbase).

- Affiliate/referrals give people a reason (besides just liking the product) that directly benefits them, and this beats passively hoping for word-of-mouth to come into place.

- Users almost always know other users that are like them or share the same interests, so if they would recommend the product to someone else, by having an affiliate/referral program they are incentivized to do so by making both parties win: The user they refer gets to use such a cool product as Thales ones and the one who refers gets double benefit by: a) Being aknowledged by the one they refer and b) Also winning in a tangible way for them, monetarily speaking.

This affiliate marketing tool initiative will be part of the wider marketing funnel as the idea is to amplify it so it can reach as many interested people as possible.   


## Specification
A new contract `Referrals` is added. The contract stores the link between the referrer and the address that it referred Thales too.  
The link is generated on the first AMM or Ranged AMM buy the referred address does.  
The referrer gets a percentage of each trade in sUSD that the referred address makes until the program lasts.  

Initial proposed fee is 50% of the minimal AMM skew, so effectively 1% of every trade goes to the referrer.  

The program can be terminated by a TIP or reconfigured to be a time period since a referral link is generated, e.g. 3 months for each new trader.  

### Configurable Values

`Referral fee` = 1% 


## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

