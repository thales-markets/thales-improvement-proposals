| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-95 | Add discounts to Overtime| Draft | Danijel (@danthales)| Add the discounts implementation to Overtime  | https://discord.gg/rPpPcMXSeU | 2022-10-06
 
## Simple Summary
 
This TIP proposes to add the discount concept to Overtime that aims to balance the Sports AMM as introduced in Thales AMM
 
## Abstract
 
Add discounts concept to Sports AMM.  
Maximum discount is to be equal to max skew impact
Increase min_spread variable from 0.5% to 1%.  

## Motivation
 
The discount concept was added to Thales AMM and I believe its a very good tool for balancing the AMM exposure. In addition it can be very attractive for traders, much more so than for Crypto Positions, as there is no concept of out of the money position, rather you could get a bonus profit on a team you were already thinking of positioning on.   
 
## Specification
 
Add the discount implementation to Sports AMM as it was done in Thales AMM.  
Max discount would be maxSkewImpact/2.   
 
While the implementation can be applied 1 to 1 to sports with binary outcome, for those with ternary (that have a draw), the discount would be a function of the side where the AMM is most exposed.

For the mechanism of self-balancing book to be efficient we need to have an equal discount to the skew impact applied on the other side.
  
I am proposing increasing min_spread from 0.5% to 1%, as discounts introduce a risk to the AMM if there isn't at least a minimal spread (0.5% can be used up for referrals, which many traders leverage). 

## Variables
 
discountDivider = 1
 
## Implementation
 
https://github.com/thales-markets/contracts/pull/207
 
## Copyright
 
Copyright and related rights waived via CC0.
