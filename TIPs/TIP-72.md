| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-72 | Parlay AMM  | draft| Danijel (@danijelthales) | Implement a Parlay AMM | https://discord.gg/8bzFdpGTrp | 2022-07-28

## Simple Summary

This TIP proposes an implementation for Parlay AMM for sport markets

## Abstract

Spec out and implement a Parlay AMM

## Motivation

While individual markets are popular with some Sport Markets users, the majority of web2 sport books users are usually combining multiple games into a single position.  
This TIP proposes how Thales can build such a mechanism on top of its existing Sport Markets AMM by composing multiple tokenized positions into a single ERC20 position with an automated market maker initially only for buys.     

## Specification
A user can choose up to 4 positions on different markets to create a Parlay ticket.   
The Parlay AMM calculates the price of such a ticket by multiplying the individual prices of all single positions by getting quotes from the underlying Sport Markets AMM and adding a ParlayAMMFee to each individual quote.  
The Parlay AMM proceed to buy those up to 4 positions and tokenizes them into a new position with a contract ParlayAMMMarketPosition. Maximum return of a Parlay is capped at max_price_supported price with initial value of 20x.  
Parlay AMM has to colaterize each Parlay position with the amount of sUSD a user can exercize should he be correct on all individual positions.  
When a ParlayAMM market is resolved, in that same method all individual positions are exercized from underlying Sport Markets AMM and all sUSD is moved to the ParlayAMM contract (similar implementation to RangedMarketsAMM).  
A user can then exercize his winnings from the ParlayAMMContract.  

The parlay AMM has to keep track of how much it can risk in total and make sure its solvent at any given time (it can not mint a new Parlay if it doesnt have enough sUSD to collaterize it).
 

## Test Cases
A user chooses 4 markets to buy 10 ParlayPosition tokens:  
* 10 tokens for EPL game Man United - Liverpool for position Man United with a quote 3 sUSD, which means base price is 0.3
* 10 tokens for EPL game Man City - Chelsea for position Draw with a quote 2 sUSD, which means base price is 0.2
* 10 tokens for Primera game Real- Barcelona for position Real with a quote 5 sUSD, which means base price is 0.5
* 10 tokens for NBA game Lakers vs Clippers for position Lakers with a quote 6 sUSD, which means base price is 0.6  

So Parlay AMM has to calculate the price for these 4 positions by multiplying individual base prices increased by ParlayAMMFee which is 5% as example:  
Parlay token price = 0.3x0.95 x 0.2x0.95 x 0.5x0.95 x 0.6x0.95 = 0.0146611125
Which is 68x winning. This would not be supported as the min_supported_price is 0.05, but lets follow through on this example. 
So the ParlayAMM qoutes the user 10 x 0.0146611125 = 0.146611125 sUSD. The user pays about 15 cents and he can win 10 sUSD.  

Parlay AMM proceed to buy the individual tokens from SportsAMM and pays for them 3+2+5+6=16 sUSD. Parlay AMM now has 10 positions of each market. If all the positions are succesfull the Parlay AMM can exercize 40 sUSD, it pays the user 10 sUSD, and effectively earns 40-10-16 = 14 sUSD itself. 
If all positions fail, the user just risked 15 cents, but Parlay AMM is down 16 sUSD - 0.15 sUSD = 15.85 sUSD.  
If 2 positions are correct, the user lost 15 cents, but Parlay AMM is good 20 sUSD - 16sUSD + 0.15 sUSD = 4.15 sUSD.    

## Variables
1. ParlayAMMFee - a fee applied to each individual quote = 5%
2. min_supported_price - minimum supported price per Parlay token = 0.05c 

## Implementation
N/A
## Copyright
Copyright and related rights waived via CC0.
