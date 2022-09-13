| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-51 | Allow negative AMM skew impact| Draft | Danijel| Allow AMM to offer negative skew impact to help balance AMM exposure | https://discord.gg/rPpPcMXSeU | 2022-05-12
 
## Simple Summary
 
This TIP proposes to allow discounts on markets that need balancing to reduce AMM risk.
 
## Abstract
 
Allow skew impact to be negative to incentivize balancing AMM.
 
## Motivation

There is now enough data to claim that skew impact, even maxxed out, isn't enough deterrent to balance the demand for both sides of individual markets, so I am proposing to allow skew impact to also introduce discount on the other side of a skewed market, to allow potential interested market makers to buy discounted positions and reduce AMM risk. 
This also allows Thales to introduce the concept of many different vaults with strategies focusing on those discount.   

## Specification 

Skew impact currently goes from 0 to 20%.  
I am proposing that on top of making the skewed side more expensive, we introduce a 0 to 10% potential discount on the other side which is proportional to how big the skew impact is on the side which was more demanded by the buyers.  

The discount will be easy to read from contract and easy to discover in the UI so that interested parties can get positional tokens at discount and thus balance AMM risks.  

Example1:
UP is 80 cents, down is 20 cents per option  
Someone buys all of the UP tokens, let's say thats 10,000 options, which means the current skew impact on UP is 20%. 
The discount on the DOWN tokens starts at 20%/2=10%.  
AMM holds 10,000 DOWN options. 
If someone was to buy 5,000 DOWN options, his discount starts at 10% and ends at 5%, and as it's applied linearly, the average skew impact is 7.5%.   
If someone was to buy all 10,000 DOWN options, his discount starts at 10% and ends at 0, so average discount is 5%. 
The discount is applied to the pricing of the option. As price of the short option is 20 cents, a 10% discount takes that price down to 18 cents. 

Let's go back to the state where AMM has 10,000 DOWN options starting at 10% discount. What if someone wants to buy more than 10,000 options?  
E.g. someone wants to buy 15k options. 
We established he will get a 5% discount for 10,000 options, so he pays for those 19 cents a piece. 
The remaining 5,0000 options is subject to a positive skew impact, starting at 0% and ending at 5%, so an average of 2.5%.  
The positive skew impact is applied to the profits, so we have to calculate how much 2.5& premium is from 80 cents profit and then calculate how much skew impact is that on the price itself.  
(80x0.025/20) x 100 = 10% skew impact on the price  

The resulting skew impact for his quote is:  
(10,000 * (-5%)+5000 * 10%) / 15000 = 0  


## Copyright
 
Copyright and related rights waived via CC0.

