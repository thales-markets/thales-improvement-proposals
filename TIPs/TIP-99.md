| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-99 | Open up Sports AMM for liquidity providing | Draft | Danijel (@danThales)| Allow anyone to deploy liquidity to Sports AMM  | https://discord.gg/rPpPcMXSeU | 2022-10-17
 
## Simple Summary
 
This TIP proposes to open up Sports AMM to anyone to provide liquidity. 
 
## Motivation
 
So far the liquidity of the Overtime has been fully seeded from Thales DAO treasury. With Overtime running for more than 3 months and generating more than $1,500,000 of volume, it has huge potential to scale up 10x or 100x, specially with the Parlays release around the corner.  
The PnL of the Sports AMM has been somewhat volatile, mostly due to experimenting with sports that did not offer the sharpest odds and some other growing pains with the data that are now solved, and I believe the AMM is at a point where it can accept liquidity from anyone who would like to "be the house". 
With the release of discounts and soon Overtime Discount Chaser vaults, the exposure of the AMM is expected to be much more balance, so liquidity providers would find it tempting to take the other side of what the traders are doing and scoop up the trading fees.  

Furthermore, Overtime liquidity providing program is to be incentivized with OP and THALES rewards as well as count towards gamified staking rewards.  

Liquidity providers will split a pot of 5,000 OP tokens and 5,000 THALES tokens a week for 12 weeks, which can be extended with a governance vote.      
   

## Specification
 
Liquidity providing will be based on weekly rounds with deposits allowed until a round starts. 
The rounds would begin on Tuesday 9am UTC and go on until next Tuesday at the same time. 
The times are chosen to capture all weekend action and not have any other games unresolved at the time to round end.  

During round 0 users deposit funds into the AMM. Users can choose to deposit funds to any of the upcoming rounds, with the default being the next round.  
Users that have deposited in a round, can choose to exit at the rounds end by signaling a withdrawal during the round and then withdrawing when all round PnL has been calculated. 

A single market can only belong to 1 round, which is defined based on the maturity date of the market. When a round ends, the PnL from all markets in a round is summed up, and allocated correctly to all liquidity providers. 

Any round after round 1 will have all of the deposits + profits from previous round plus any new deposits at round start.  

Sometimes markets are delayed and the start time of a game is changed. If such a change would move the market from one round to another, that market has to be cancelled in the round it previously belonged with all positions refunded, and recreated in a new round.

## Examples  


Round 0 starts at 1st of November.  
Users deposit $100k for round 1.    
Round 1 starts at 8th of November with $100k. If you provided $1000 your share is 1%.   
Round 2 receives $20k of new deposits.   
Round 1 ends with a total of 110k in the AMM. Your balance is now $1100 entering round 2.  
Total in round 2 at the start is $130k. Your share is 1100*100/130000 = 0.84615%  


## Variables
 
## Implementation
 
## Copyright
 
Copyright and related rights waived via CC0.
