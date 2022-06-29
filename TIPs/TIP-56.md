| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-56 | OP token allocation towards pro rata Trading Incentives | Draft | padzank (@padzank)| Detailed plan around allocating 200,000 OP tokens from Thales Phase 0 distribution towards traders the Thales Marketplace traders as Pro rata Trading Incentives | https://discord.gg/rPpPcMXSeU | 2022-06-02
 
## Simple Summary
 
This TIP proposes a plan on how to execute the allocation of 200,000 OP tokens and 500,000 THALES tokens towards the Thales Marketplace traders as Pro rata Trading Incentives
 
## Abstract
 
This TIP proposes to distribute 200,000 OP tokens towards the Thales Marketplace traders as Pro rata Trading Incentives. The proposal is to emit these tokens in amounts of 20,000 OP tokens and 50,000 THALES tokens per 14-day rounds of trading.  
  It is also proposed to split the reward token amounts, for the sake of organically balancing the AMM, as following:
  - 7,500 OP + 20,000 THALES pro-rata towards UP token Buyers
  - 7,500 OP + 20,000 THALES towards DOWN token Buyers
  - 5,000 OP + 10,000 THALES towards Ranged Markets IN/OUT tokens Buyers
 
## Motivation
 
 - Direct Trading Incentives towards Thales traders are proven to have a high impact on the platform overall increase in trading volume, which is one of the main performance indicators of the protocol. Subsequently, the presence of lucrative direct trading incentives has the effect of inviting new unique traders to try out and learn how to trade on Thales.  

 - Regarding mitigating wash trading risk, if a trader wants to BUY a position on Thales from the AMM and then immediately SELL that same position back to the AMM, he would lose a significant amount of the initial capital in the process from the BUY/SELL spread that exists. This is caused by our AMMs Skew Impact mechanism that is put in place to incentivize keeping the AMM as market neutral as possible by adjusting the price premium of UP/DOWN tokens based on the amount of risk that the AMM is exposed to.
Evidently, the unintentional effect of this is that it is not economically feasible for a trader on Thales to be market neutral against the Thales AMM. Thales has the luxury of keeping this spread active across markets as our product offers really novel and exotic exposure towards supported assets based on probability calculations and traders are willing to accept it as they deem their risk/reward ratio favorable either way.  
  
 - The choice of splitting the incentives as dedicated pro rata rewards between UP buyers, DOWN buyers and Ranged Market buyers is decided for the reason of organically balancing the AMM skew and also putting some of the focus on Ranged Markets with dedicated rewards. Using this split method, the amount of rewards a trader gets per round are inversely correlated to the amount of total sUSD buy volume his specific type of position has for said round. This causes the organic effect of awards being more lucrative for the positional tokens that are overall less purchased, thus incentivising traders to buy the less purchased type of a positional token and this way help in balancing the global AMM skew or helping the AMM to have less risk (exposure) to which way the markets resolve. For example, if Thales traders heavily buy UP tokens from the markets but don't buy as much DOWN tokens, DOWN tokens Buy Volume will organically accrue more rewards because you will get the "larger piece of the 7,500 OP tokens pie" than if you were to buy UP tokens. The subsequent effect is that traders will be more incentivized to buy the positional tokens that help the AMM increase the overall balance.
 
## Specification
 
 This TIP entails the Thales Treasury to dedicate 500,000 THALES tokens and 200,000 OP tokens from the total Phase 0 OP tokens distribution for Thales, as a 20-week Pro Rata Trading Incentives program for Thales traders. The distribution between traders for each round and for each positional token buy volume is to be calculated by off-chain scripts, and distributed accordingly.

**Thales Governance structure will keep the option open to revise the emission numbers at any time during the 20 week program based on effectiveness and performance of the incentives.**

## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.