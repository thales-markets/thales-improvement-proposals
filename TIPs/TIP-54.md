| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-54 |  Thales referrals program | Draft | Danijel | Enable referral program into Thales AMMs | https://discord.gg/rPpPcMXSeU | 2022-05-26


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

--TODO:Marketing experts to elaborate on marketing reasoning 

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

