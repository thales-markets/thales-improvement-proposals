| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-55 | OP token allocation towards THALES/WETH liquidity providers | Implemented | padzank (@padzank)| Detailed plan around allocating 315,000 OP tokens from Thales Phase 0 distribution towards THALES/WETH liquidity providers | https://discord.gg/rPpPcMXSeU | 2022-05-27
 
## Simple Summary
 
This TIP proposes a plan on how to execute the allocation of 315,000 OP tokens towards THALES/WETH liquidity providers from Optimism Phase 0 OP token distribution.
 
## Abstract
 
This TIP proposes to distribute 315,000 OP tokens towards THALES/WETH liquidity providers as a second stream of LP rewards for an already active LP staking contract that emits THALES rewards. The proposal is to emit these tokens in amounts of 15,750 OP tokens awarded per week. As these emissions will run in parallel with the current LP rewards program which emits THALES rewards, the current LP staking contract is to be adapted to support dual reward emissions and claiming.
 
## Motivation
 
Since liquidity increase is in Optimism's and in Thales' best interest at the same time, having OP token as a second stream of LP rewards alongside THALES token rewards themselves will alleviate the need for spending more THALES tokens for that cause. With these weekly emissions, a duration of 20 weeks should ensure healthy and stable liquidity for the THALES token for almost 5 months and there is a good chance to renew these incentives for an even longer time if Phase 1 OP token distribution is successful for Thales. However, flexibility to adapt as things change and progress will be kept and the amount of weekly emissions will be a subject of change under those circumstances.
 
## Specification
 
 This TIP entails the Thales Protocol DAO to adapt the already active [LP staking contract](https://optimistic.etherscan.io/address/0x31a20E5b7b1b067705419D57Ab4F72E81cC1F6Bf) of THALES/WETH G-UNI LP tokens to support dual rewards and implement emissions and claiming of 15,750 OP tokens weekly as rewards to run alongside current emissions of THALES rewards.
 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.