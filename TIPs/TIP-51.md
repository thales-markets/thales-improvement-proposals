| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-51 | Allow negative AMM skew impact| Draft | Danijel| Allow AMM to offer negative skew impact to help balance AMM exposure | https://discord.gg/rPpPcMXSeU | 2022-05-12
 
## Simple Summary
 
This TIP proposes to allow discount on markets that need balancing to reduce AMM risk.
 
## Abstract
 
Allow skew impact to be negative to incentivize balancing AMM.
 
## Motivation

Given the recent volatility in Markets, Thales AMM got very large exposure to traders wanting to short. 
Skew impact, even maxxed out, wasnt enough deterrent to balance the demand, so I am proposing to allow skew impact to also introduce discount on the other side of a skewed market, to allow potential interested market makers to buy discounted positions and reduce AMM risk.   

## Specification 

Skew impact currently goes from 0 to 20%.  
I am proposing that on top of making the skewed side more expensive, we introduce a 0 to 5% potential discount on the other side which is proportional to how big the skew impact is on the side which was more demanded by the buyers.  

The discount will be easy to read from contract and easy to discover in the UI so that interested parties can get positional tokens at discount and thus balance AMM risks.    

## Copyright
 
Copyright and related rights waived via CC0.

