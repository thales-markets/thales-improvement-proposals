| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-99 | Open up Sports AMM for liquidity providing | Draft | Danijel (@danThales)| Allow anyone to deploy liquidity to Sports AMM  | https://discord.gg/rPpPcMXSeU | 2022-10-17


## Abstract

Implement the architecture to allow anyone to deposit into the Sports AMM. 
Deprecate method "sellToAMM".
 
## Simple Summary
 
This TIP proposes to open up Sports AMM to anyone to provide liquidity. 
 
## Motivation
 
So far the liquidity of the Overtime has been fully seeded from Thales DAO treasury. With Overtime running for more than 3 months and generating more than $1,500,000 of volume, it has huge potential to scale up 10x or 100x, specially with the Parlays release around the corner.  
The PnL of the Sports AMM has been somewhat volatile, mostly due to experimenting with sports that did not offer the sharpest odds and some other growing pains with the data that are now solved, and I believe the AMM is at a point where it can accept liquidity from anyone who would like to "be the house". 
With the release of discounts and soon Overtime Discount Chaser vaults, the exposure of the AMM is expected to be much more balance, so liquidity providers would find it tempting to take the other side of what the traders are doing and scoop up the trading fees.  

Furthermore, Overtime liquidity providing program is to be incentivized with OP and THALES rewards as well as count towards gamified staking rewards.  

Liquidity providers will split a pot of 5,000 OP tokens and 5,000 THALES tokens a week for 12 weeks, which can be extended with a governance vote.      

## Specification 

Two different ways of implementing this are shared below. 
Common for both cases is that I am proposing to lose the "sellToAMM" function as I feel it just increases the complexity and risk surface, without having a lot of value of the product itself. 

For the initial few weeks, only whitelisted addresses will be able to add liquidity which would be Treasury and team wallets, which would serve to make sure we have covered any possible edge case with games being cancelled or moved or odds shifting significantly.  

Its important to note that ParlayAMM is completely decoupled from this, and would have its own liquidity providing mechanism    

# Option 1

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


# Option 2 

## Specification
 
Liquidity providing will be based on shares with would be ERC20 tokens with 18 decimals. Users deposit before the beginning of trading.  
Before the beginning of trading, a single share token is minted for each sUSD deposited.  

When trading starts the price of a single share will be determined based on the price of the positions held by the AMM. 
That price is available to be read from the contract at any given time by iterating through all of the positions of unresolved markets in the AMM and multiplying the number of positions with the last odds received from the oracle.  

Users can deposit and withdraw at any given time, unless there is a market that has entered maturity but is not resolved yet.  

When users deposit, new shares are minted at current price, e.g. if current price is $1.1, for $1100 deposit a user gets 1000 new minted shares.  

When users withdraw, their shares are burned and they get either sUSD in return at current price.  

If there is not enough sUSD for users to withdraw, they may chose to exit by receiving a proportional amount of each position held by the AMM compared to their share in the pool.  

The value of the AMM is always split between the sUSD in it and ongoing positions. When a position is exercised, if those positions were winning, the sUSD amount automatically to the total value of the AMM.     

## Examples 

AMM starts with 100k sUSD so 100k shares are minted.  

Some trading transpires so AMM now has 93k sUSD and 10k positions on one market, and 5k positions and another market.  
   
The 10k positions are valued at 60 cents a piece, which makes for 6k while the 5k positions are now valued at 80 cents, which makes for $4000.  

Total value of the AMM is now 102k, or value per share is $1.02.  

Someone wants to deposit $1200 into the AMM. 1000 shares are minted and sent to that wallet and the total number of shares is now 101k.  



## Variables

minDepositAmount = 100 sUSD
 
## Implementation
 
## Copyright
 
Copyright and related rights waived via CC0.
