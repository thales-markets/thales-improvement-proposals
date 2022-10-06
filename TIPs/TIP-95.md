| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-95 | Add discounts to Overtime| Draft | Danijel (@danthales)| Add the discounts implementation to Overtime  | https://discord.gg/rPpPcMXSeU | 2022-10-06
 
## Simple Summary
 
This TIP proposes to add the discount concept to Overtime that aims to balance the Sports AMM as introduced in Thales AMM
 
## Abstract
 
Add discounts concept to Sports AMM.  
Increase skew impact from 5% to 10%, so that maximum discount is 5%.  
Increase min_spread variable from 0.5% to 1%.  

## Motivation
 
The discount concept was added to Thales AMM and I believe its a very good tool for balancing the AMM exposure. In addition it can be very attractive for traders, much more so that for Crypto Positions, as there is no concept of out of the money position, rather you could get a bonus profit on a team you were already thinking of positioning on. 
The discount concept together with increased skew impact would in a sense act as a self balancing sports book, which gives the AMM more flexibility in mitigating occasional stale odds, which can be reduced with more frequent polling of oracles, but can never really be 100% removed.
 
## Specification
 
Add the discount implementation to Sports AMM as it was done in Thales AMM. 
Max discount would be maxSkewImpact/2; 
 
While the implementation can be applied 1 to 1 to sports with binary outcome, for those with ternary (that have a draw), the discount would be a function of the side where the AMM is most exposed.

For the mechanism of self-balancing book to be efficient we need a higher max skew impact, so that we can offer a higher discount. I am proposing a change to max_skew_impact variable from 5% to 10%.  
  
To the same effect, I am proposing increasing min_spread from 0.5% to 1%, as discounts introduce a risk to the AMM if there isn't at least a minimal spread (0.5% can be used up for referrals, which many traders leverage). 

The fee adjustments are also a preparation for Parlays, where combining multiple discounts could offer a huge bonus to traders, but we also need to make sure to not offer higher discounts than what was charged for skew impact. 
## Variables
 
discountDivider = 2 (maxSkewImpact/2)
 
## Implementation
 
https://github.com/thales-markets/contracts/pull/207
 
## Copyright
 
Copyright and related rights waived via CC0.
