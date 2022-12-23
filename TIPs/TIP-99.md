| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-99 | Open up Sports AMM for liquidity providing | Draft | Danijel (@danThales)| Allow anyone to deploy liquidity to Sports AMM  | https://discord.gg/rPpPcMXSeU | 2022-10-17


## Abstract

Implement the architecture to allow liquidity providing into the Sports AMM. 
 
## Simple Summary
 
This TIP proposes to open up Sports AMM for providing liquidity based on the amount of THALES a wallet has staked. 
 
## Motivation
 
So far the liquidity of the Overtime has been fully seeded from Thales DAO treasury. With Overtime running for more than 6 months and generating more than $5,000,000 of volume, it has huge potential to scale up 10x or 100x, specially with the Parlays and Vaults released on products on top which also serve to somewhat balance the AMM risks.  
The PnL of the Sports AMM after World Cup has shown that with organic volume and sharp oracles, there is a pretty good chance of lucrative earnings for liquidity providers. After some lessons we learned the hard way with experimenting with low liquidity sports and preseasons, we are now focused only on high liquidity sports, and with Oracle changes in TIP-114 putting us in a much better spot to fight frontrunning,  I believe the AMM is at a point where it can accept liquidity from anyone who would like to "be the house". 


## Specification

Liquidity providing will be based much on the proven concept established through vaults. Much of the architecture is inheritted from TIP-70. 
 
Liquidity providing will be done in weekly rounds with deposits allowed until a round starts. 
The rounds would begin on Tuesday 9am UTC and go on until next Tuesday at the same time. 
The times are chosen to capture all weekend action and not have any other games unresolved at the time to round end.  

During round 0 users deposit funds into the AMM. Users always deposit for the next round.  
  
Users that have deposited in a round, can choose to exit at the rounds end by signaling a withdrawal during the round and then withdrawing when all round PnL has been calculated. 

A single market can only belong to 1 round, which is defined based on the maturity date of the market. When a round ends, the PnL from all markets in a round is summed up, and allocated correctly to all liquidity providers. 

Any round after round 1 will have all of the deposits + profits from previous round plus any new deposits at round start.  

Sometimes markets are delayed and the start time of a game is changed. If such a change would move the market from one round to another, that market has to be cancelled in the round it previously belonged with all positions refunded, and recreated in a new round.


If there isnt enough liquidity in a certain round, AMM liquidity pool borrows from the Treasury Liquidity Pool contract,
 and sets it as one of the depositors for that round.
This can only be done if that round hasnt started yet (previous round did not finish).
When the round finally starts, the Treasury Liquidity Pool is repaid from deposits that enter the round, or if there isnt enough to cover what was used from TLP, the TLP enters the round as a regular depositor.

A user can only deposit 1 sUSD per 1 THALES he stakes. A user can only signal withdrawal if he has at least 1 THALES per 1 sUSD that he currently has in that round.


A difference to vaults is that all rounds are statically predetermined at startDate+(roundNumber x 7days). This is done as we dont want to block users from trading an upcoming markets which are sometimes scheduled and available on Overtime even weeks in advance.  
## Examples  


Round 0 starts at 1st of November.  
Users deposit $100k for round 1.    
Round 1 starts at 8th of November with $100k. If you provided $1000 your share is 1%.   
Round 2 receives $20k of new deposits.   
Round 1 ends with a total of 110k in the AMM. Your balance is now $1100 entering round 2.  
Total in round 2 at the start is $130k. Your share is 1100*100/130000 = 0.84615%  


## Variables

minDepositAmount = 100 sUSD  
maxAllowedUsers = 100  
sUSDPerThalesStakedRatio = 1
 
## Implementation
 
## Copyright
 
Copyright and related rights waived via CC0.
