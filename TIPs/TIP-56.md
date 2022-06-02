| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-56 | OP token allocation towards pro rata Trading Incentives | Draft | padzank (@padzank)| Detailed plan around allocating 250,000 OP tokens from Thales Phase 0 distribution towards traders the Thales Marketplace traders as Pro rata Trading Incentives | https://discord.gg/rPpPcMXSeU | 2022-06-02
 
## Simple Summary
 
This TIP proposes a plan on how to execute the allocation of 250,000 OP tokens and 100,000 THALES tokens towards the Thales Marketplace traders as Pro rata Trading Incentives
 
## Abstract
 
This TIP proposes to distribute 200,000 OP tokens towards the Thales Marketplace traders as Pro rata Trading Incentives. The proposal is to emit these tokens in amounts of 20,000 OP tokens and 100,000 THALES tokens per 14-day round of new markets. Proposing that each round of incentives is split between **Buy Volume** of UP, DOWN, IN and OUT  tokens. This effectively means that each of the 4 types of positions will be incentivised with dedicated 5,000 OP and 2,500 THALES tokens per 14-day round, for a total program duration of 20 weeks (10 14-day rounds).
 
## Motivation
 
Direct Trading Incentives towards Thales traders are proven to have a high impact on the platform overall increase in trading volume, which is one of the main performance indicators of the protocol. Subsequently, the presence of lucrative direct trading incentives has the effect of inviting new unique traders to try out and learn how to trade on Thales.  
  
The choice of splitting the incentives as dedicated pro rata rewards for each of the 4 possible possible positions (UP, DOWN, IN and OUT) equally, is decided for the reason of organically balancing the AMM skew. Using this method, the amount of rewards a trader gets per round are inversely correlated to the amount of total sUSD buy volume his specific type of position has for said round. This causes the organic effect of awards being more lucrative for the positional tokens that are overall less purchased, thus incentivising traders to buy the less purchased type of a positional token and this way help in balancing the global AMM skew or helping the AMM to have less risk (exposure) to which way the markets resolve.  

For example, if Thales traders heavily buy UP tokens from the markets but don't buy as much DOWN tokens, DOWN tokens Buy Volume will organically accrue more rewards because you will get the "larger piece of the 5,000 OP tokens pie" than if you were to buy UP tokens. The subsequent effect is that traders will be more incentivized to buy the positional tokens that help the AMM increase the overall balance.
 
## Specification
 
 This TIP entails the Thales Treasury to dedicate 100,000 THALES tokens and 200,000 OP tokens from the total Phase 0 OP tokens distribution for Thales, as a 20-week Pro Rata Trading Incentives program for Thales traders. The distribution between traders for each round and for each positional token buy volume is to be calculated by off-chain scripts, and distributed accordingly.

## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.