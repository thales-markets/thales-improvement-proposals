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
The Parlay AMM calculates the price of such a ticket by multiplying the individual prices of all single positions by getting quotes from the underlying Sport Markets AMM and adding a ParlayAMMFee and the SafeBoxFee.  
The Parlay AMM proceed to buy those 1 of each of the 4 positions and tokenizes them into a new position with a contract ParlayAMMMarketPosition. Maximum return of a Parlay is capped at max_price_supported price with initial value of 20x.   
When a ParlayAMM market is resolved, in that same method all individual positions are exercized from underlying Sport Markets AMM and all sUSD is moved to the ParlayAMM contract (similar implementation to RangedMarketsAMM).   
A user can then exercize his winnings from the ParlayAMMContract.  

For this to be economically feasible, the underlying Sport Markets AMM will have to greatly reduce the SafeBox fee when the buyer is the ParlayAMM. The ParlayAMM will also have its own SafeBoxFee variable.     

The parlay AMM has to keep track of how much it can risk in total and make sure its solvent at any given time (it can not mint a new Parlay if it doesnt have enough sUSD to collaterize it).

-------------
TBD: If one or more markets in a parlay result in cancellation, usual approach in centralized books is to ignore that market, but multiple the odds for other winning markets in the parlay. However, since we are collaterizing each position of a parlay, the Parlay AMM will still be able to claim back what it paid for such a market.  This needs more thinking on how to handle it exactly. I think the way it should be done is that not every position needs to be collaterized with an equal amount in the Parlay AMM, but rather it should be a function of individual odds per position.  
0.25 =>4x
0.5 =>2x 
0.125 =>8x 
Parlay token price = 0.015625 = 64x

if the first game is cancelled the return should be 16x = 0.25  
if both first and second game are cancelled the return should be 8x = 0.125

To achieve this, 1 such parlay token needs to be collaterized with: 
???   
-------------

## Test Cases  
### Example 1
A user chooses 4 markets to buy 10 ParlayPosition tokens:  
* 2.5 tokens for EPL game Man United - Liverpool for position Man United with a quote 0.75 sUSD, which means base price is 0.3 
* 2.5 tokens for EPL game Man City - Chelsea for position Draw with a quote 0.5 sUSD, which means base price is 0.2
* 2.5 tokens for Primera game Real- Barcelona for position Real with a quote 1.25 sUSD, which means base price is 0.5
* 2.5 tokens for NBA game Lakers vs Clippers for position Lakers with a quote 1.5 sUSD, which means base price is 0.6  

If all 4 positions are correct, the ParlayContract can exercize 4 sUSD from the underlying SportsAMM so the Parlay for the user is fully collaterized that way.    

So Parlay AMM has to calculate the price for these 4 positions by multiplying individual base prices the add the ParlayAMMFee and SafeBoxFee.  
    
ParlayAMM fee is added to each quote and summed up.  

**ParlayAMM fee = (0.75+0.5+1.25+1.5) x 0.002 = 0.008**    

**Parlay base token price = 0.3x x 0.2x x 0.5x x 0.6 = 0.018 which is 55x winning**   

**Parlay token price with fees = (0.018+0.008)x1.005 =  0.02613 => 38x**  


### Example 2
A user chooses 4 markets to buy 10 ParlayPosition tokens:  
* 2.5 tokens for EPL game Man United - Liverpool for position Man United with a quote 0.5 sUSD, which means base price is 0.2
* 2.5 tokens for EPL game Man City - Chelsea for position Draw with a quote 0.5 sUSD, which means base price is 0.2
* 2.5 tokens for Primera game Real- Barcelona for position Real with a quote 0.5 sUSD, which means base price is 0.2
* 2.5 tokens for NBA game Lakers vs Clippers for position Lakers with a quote 0.5 sUSD, which means base price is 0.2  

**ParlayAMM fee = 2x 0.002 = 0.004**    

**Parlay base token price = 0.5^4  = 0.0625 which is 16x winning**   

**Parlay token price with fees = (0.0625+0.005)x1.005 =  0.0678375 => 14.74x**  

### Example 3
A user chooses 3 markets to buy 10 ParlayPosition tokens:  
* 3.33 tokens for EPL game Man United - Liverpool for position Man United with a quote 0.75 sUSD, which means base price is 0.3 
* 3.33 tokens for EPL game Man City - Chelsea for position Draw with a quote 0.5 sUSD, which means base price is 0.2
* 3.33 tokens for Primera game Real- Barcelona for position Real with a quote 1.25 sUSD, which means base price is 0.5

**ParlayAMM fee = (0.75+0.5+1.25) * 0.002 = 0.005**    

**Parlay base token price = 0.3x x 0.2x x 0.5x  = 0.03 which is 33.33x winning**   

**Parlay token price with fees = (0.03+0.005)x1.005 =  0.035175 => 28.4x**  

### Example 4
A user chooses 4 markets to buy 10 ParlayPosition tokens:  
* 2.5 tokens for EPL game Man United - Liverpool for position Man United with a quote 2 sUSD, which means base price is 0.8
* 2.5 tokens for EPL game Man City - Chelsea for position Draw with a quote 1.75 sUSD, which means base price is 0.7
* 2.5 tokens for Primera game Real- Barcelona for position Real with a quote 1.5 sUSD, which means base price is 0.6
* 2.5 tokens for NBA game Lakers vs Clippers for position Lakers with a quote 2.25 sUSD, which means base price is 0.9  

**ParlayAMM fee = 7.5x 0.002 = 0.015**    

**Parlay base token price = 0.6x0.7x0.8x0.9  = 0.3024 which is 3.3x winning**   

**Parlay token price with fees = (0.3024+0.005)x1.005 =  0.308937 => 3.23x winning**  


## Variables
1. ParlayAMMFee - a fee applied to each individual quote = 5%
2. min_supported_price - minimum supported price per Parlay token = 0.05c 
3. SafeBoxFee on Parlay contract = 5% 
4. SafeBoxFee on Sport Markets AMM when Parlay is the called = 0.1%  

## Implementation
N/A
## Copyright
Copyright and related rights waived via CC0.
