| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-72 | Parlay AMM  | draft| Kiril, Danijel (@danijelthales) | Implement a Parlay AMM | https://discord.gg/8bzFdpGTrp | 2022-07-28

## Simple Summary

This TIP proposes an implementation for Parlay AMM for sport markets

## Abstract

Spec out and implement a Parlay AMM

## Motivation

While individual markets are popular with some Sport Markets users, the majority of web2 sport books users are usually combining multiple games into a single position.  
This TIP proposes how Thales can build such a mechanism on top of its existing Sport Markets AMM by composing multiple tokenized positions into a single ERC20 position with an automated market maker initially only for buys.     

## Specification
A user can choose up to 4 positions on different markets to create a Parlay ticket.   
The Parlay AMM calculates the price of such a ticket by multiplying the individual prices of all single positions by getting quotes from the underlying Sport Markets AMM and adding a ParlayAMMFee and the SafeBoxFee.  

The calculation is done in two phases:  
1. The total (payout) amount is calculated by using the product of the default odds per position.  
2. The total (payout) amount is spread accross the different positions.  
The Parlay AMM proceed to buy each of the positions inversely proportional to the buy quote of each position.  
In simple wording the Parlay AMM buys the most positions with the least likely outcome (lowest odds -> highest amount purchased), while the least positions are purchased for the positions with the most likely outcome (highest odds -> lowest amount purchased).  
The rationale behind this strategy is that when a user wins the parlay, the Parlay AMM purchased it for a lower price than using uniform distribution (equally purchased amount for each position).  
In this case the product of the odds is different than the one from step 1, mainly due to the different skew impact per position.

Maximum return of a Parlay is capped at `maxSupportedAmount` price with initial value of 20x or `maxSupportedOdds = 0.05`.   
When a Parlay AMM market is resolved, in that same method all individual positions are exercized from underlying Sport Markets AMM and all sUSD is moved to the ParlayAMM contract (similar implementation to RangedMarketsAMM).   
A user can then exercize his winnings from the ParlayAMMContract.  

For this to be economically feasible, the underlying Sport Markets AMM will not be charging SafeBox fee when the buyer is the ParlayAMM. The ParlayAMM will have its own SafeBoxFee variable.     

The Parlay AMM has to keep track of how much it can risk in total and make sure its solvent at any given time (it can not mint a new Parlay if it doesnt have enough sUSD to collaterize it). To lower the exposure, there is a `maxAllowedRiskPerCombination` variable that prevents the Parlay AMM to be over-exposed for a same set of games in a parlay. This caps the sum of all the user deposits per parlay combination up until the `maxAllowedRiskPerCombination` (for example parlay with games combination `[A, B, C, D]`, `[A, D, C, B]` or `[B, D, C, A]`).

-------------
On cancelled games:  
If one or more markets in a parlay result in cancellation, usual approach in centralized books is to ignore that market, but multiplu the odds for other winning markets in the parlay.   
The current implementation implements this logic. The cancelled game is included with odd `1` in the total odds calculation. If the parlay has four games with odds `[ 0.6, 0.5, 0.3, 0.7]` with total product of `0.063` and the third game is cancelled, the parlay will result in the `[ 0.6, 0.5, 1, 0.7]` with total product of `0.21`.   
In the case of winning parlay with cancelled positions, the user obtains, as expected, less than the total winnning amount while the Parlay AMM is refunded for the cancelled positions. 

-------------
Ristricted combinations:  
- Same game can not be included more than once, even with different positions.  
- Same team/player/fighter can not be combined in a same parlay. Even if the games are in different dates.
- Single motorsport game is allowed per parlay.
-------------

## Test Cases  
### Example 1
A user choses to place 10 sUSD on parlay with games:
* Man United vs. Liverpool - position on Man United - home team initial quote = 0.3
* Lakers vs. Clippers - position on Lakers - home team initial quote = 0.55
* Adesanya vs. Pereira - position on Pereira - away fighter initial quote = 0.5
* Patriots vs. Jets - position on Patriots - home team initial quote = 0.65  

First step is to calculate all the initial values:  
**total quote** = 0.3 x 0.55 x 0.5 x 0.65 = 0.053625  
**sUSD after fees** = placedAmount - (parlayFee + safeBoxFee) = 10 - 6% = 9.4  
**expected payout** = 9.4/0.053625 = 175.291

Second step is to calculate the positions to be bought from SportsAMM per game. The strategy is to use inverse distribution of the buying amount:  
* Man United inverse quote = 0.7
* Lakers inverse quote = 0.45
* Pereira inverse quote = 0.5
* Patriots inverse quote = 0.35  
**sum of inverse quotes** 0.7 + 0.45 + 0.5 + 0.35 = 2  
**position amount calculation** = (inveseQuotePerGame x initialPayout) / (inverseSumOfQuotes)  
* Man United position amount = (9.4 * 0.7) / (0.053625 * 2) = 61.35
* Lakers position amount = (9.4 * 0.45) / (0.053625 * 2) = 39.44
* Pereira position amount = (9.4 * 0.5) / (0.053625 * 2) = 43.82
* Patriots position amount = (9.4 * 0.35) / (0.053625 * 2) = 30.67  
**totalAmountToBuy** = 61.35 + 39.44 + 43.82 + 30.67 = 175.28

Due to the skewImpact in the SportsAMM, the values are adjusted accordingly for:
* totalQuote 
* expectedPayout
* quotesPerGame  

The last step is buying the position amounts using the ParlayMarketsAMM contract, with additional slippage.  
All the positions are transferred to the newly created ParlayMarket.  
**In case all the positions are winning, the user can exercise and claim** = 175.28 sUSD


## Variables
1. `minUSDAmount` = 20 sUSD - minimum user deposit amount per parlay
2. `maxSupportedAmount` = 5000 sUSD - maximum payout amount per parlay
3. `maxSupportedOdds` = 0.05 - maximum total quote per parlay
4. `maxAllowedRiskPerCombination` = 5000 sUSD - maximum allowed risk for same set/combination of games in parlay. 
5. `parlaySize` = 4 - max number of games per parlay
6. `parlayAMMFee` = 3% - a parlay fee for each parlay
7. `safeBoxFee`   = 3% - a safe box fee for each parlay
8. `referrerFee`  = 0.5% - a referral fee for each parlay

## Implementation

### ParlayMarketsAMM
Main contract used for quoting and buying `ParlayMarket`. 
Each quote/buy requires a set of `sportMarkets` and `positions` plus a `sUSDamount`.
The size set can not be higher than the `parlaySize`.

On buy, the `totalAmount` of sport positions are bought from SportsAMM and transferred to the newly created `ParlayMarket`.

### ParlayMarket
Contract holding the user positions for a parlay. 
The sum of all positions is equal to the `expectedPayout` for a parlay. 
On exercise, if parlay poses only winning positions, the winning sUSD amount is transferred to the user.
In other cases, winning positions are exercised and transferred to `ParlayMarketsAMM`.

### ParlayMarketData
Used for monitoring on-chain Parlay data.

## Copyright
Copyright and related rights waived via CC0.
