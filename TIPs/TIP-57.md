| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-57 |  Exotic Markets referrals program | Deprecated | padzank | Enable a referral program for Exotic Markets | https://discord.gg/rPpPcMXSeU | 2022-06-14
 
 
## Simple Summary

Add the concept of on-chain referral program for the Exotic Markets product
 
## Abstract
 
This TIP proposes to commence an affiliate program via referrals and send sUSD from every AMM trade to the referrers while the program is ongoing. The proposal is to reduce the resolver fee from 1% to 0.5% and to dedicate 0.5% of total referral volume towards the referrer, distributed at the end of a succesful market resolution.
 
## Motivation
 
With an already implemented Referral Program form the Thales AMM, it's time to introduce a Referral Program for Exotic Markets platform also.
Exotic Markets users will also be able to generate links and share those with potential traders, but in this case the referral links are to be dedicated to specific markets. If referred traders start generating volume on the specific market that the referral link is dedicated to, the referrers get a percentage from each trade paid in sUSD directly, but only distributed after the entire market is succesfully resolved. If the market is cancelled, the referral program for that market is also cancelled and the fees are also rolled back to traders.
 
## Specification
 
This TIP entails the Thales Protocol DAO to reduce the Exotic Markets resolver fee from 1% to 0.5%.
 
This TIP additionally entails the Thales Protocol DAO to implement a referral program for Exotic Markets which, after the market is succesfully resolved, awards the referrer 0.5% of total sUSD volume his referrals drive on the specific market the referrer used for his link generation.
 
### Configurable Values
 
`Referral fee` = 0.5%
 
## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).