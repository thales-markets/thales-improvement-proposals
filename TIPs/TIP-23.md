| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-23 | Deployment of incentivised opTHALES/ETH G-UNI pool on Optimism  | Draft | padzank (@padzank) | Support THALES token migration to Optimism with an incentivized THALES/ETH G-UNI pool | https://discord.gg/rPpPcMXSeU | 2022-01-22
 
## Simple Summary
 
This TIP proposes to deploy a THALES/ETH G-UNI pool on Optimism network to support the THALES token migration together with a subsequent staking contract that accepts G-UNI LP tokens of this pool, and in return awards in THALES tokens pro rata.
 
## Abstract
 
 Currently, on Optimism, the sole solution for a fungible Uniswap v3 liquidity is G-UNI framework from Gelato. This TIP proposes that Thales deploys an **incentivized** 0 <-> infinity range THALES/ETH Uniswap V3 pool using the G-UNI framework and this way support liquidity on Optimism. The pool would be fully immutable and trustless without anyone having the ability to change any parameters of the underlying Uniswap V3 position.
 Proposed incentives for this pool would be **35,000 THALES tokens per week** for the duration of **10 weeks**. After the period of 10 weeks, further continuation of LP incentives is to be revised by the Thales Council.

## Motivation
 
With the plan to execute the token migration to Optimism on February 2nd, incentives are needed to be put in place to invite THALES token holders to migrate their liquidity. Currently, there are not many liquidity mining frameworks available on Optimism for Thales to use. Uniswap is the only acceptable DEX currently on Optimism, but with Uniswap LP positions being represented by NFTs rather than ERC20 tokens, this creates an obstacle for projects wanting to incentivize liquidity provision on Uniswap. On L1 Ethereum, THALES token swap 24h volume was consistently four times greater on Uniswap than on the DODO exchange, even though liquidity on DODO was ~70% greater at any given moment. Currently, the only optimal solution that encompass all of the previous points is the Gelato G-UNI framework. 

Gelato G-UNI framework is the first Uniswap V3 liquidity mining solution on Optimism. 
> G-UNI is a neutral, unopinionated framework for concentrated and fungible  Uniswap v3 liquidity. By turning NFT of LP positions into fungible ERC-20 tokens and automatically compounding fees, G-UNI offers a simplified experience to liquidity providers and a composable option for platforms who want to fit Uniswap v3 in the money legos of their protocol.
G-UNI framework allows THALES to implement a LP incentives program on Optimism by deploying a staking contract that locks in G-UNI LP tokens and emits THALES token as rewards. Another alignment is that Gelato just recently announced an integration with Olympus that introduces using G-UNI LP tokens for a bond mechanism, which basically introduces a mechanism for protocol-owned Uniswap V3 liquidity, something Thales is exploring for the near future.

The proposal of emitting 35,000 THALES tokens weekly to LPs should be generous enough to provide competitive APR, bot not too generous to risk majority of THALES tokens being locked up in this LP and not in the revamped single side staking contract. For clarity, single side staking will launch at the same time as LP incentives with the inflation in the range of 70,000 and 91,000 THALES tokens per week. 

Currently, Gelato does not support automated rebalancing strategies for G-UNI pools on Optimism, as they are aiming for late February deployment. Only manual rebalancing, via the inherited manager role, is possible at the moment.  Either way, there are certain risks for using rebalancing strategies. One of the risks is that, if you wish to enable rebalancing strategies, you have to give some address or contract a manager role. Manager role has power over the full underlying Uniswap V3 liquidity of a certain G-UNI pool, so it can change relevant parameters in various ways. This can potentially cause concerns regarding regulatory risk, trust level, security and human error. Might be worth the risk in the future when there are trustless battle-tested automated strategies developed. However, to avoid any possible risk introduced with managed G-UNI pools and rebalancing, most optimal solution is to use a fully immutable, trustless and manager-free type G-UNI THALES/ETH pool with infinite range. The choice of infinite range for this type of pool and not concentrating liquidity is because, if THALES token ever goes beyond the chosen range, a new pool would then have to be deployed with a new range and all of the LPs would have to shift their liquidity to the new pool. Risk of getting into this kind of situation is mitigated by deploying a pool with infinite range from the start.


## Specification
 
  - This TIP entails the Thales Protocol DAO to use a `GUniFactory` contract to call the `createPool` function to create a manager-free, infinite range THALES/ETH pool with fixed parameters.

 - This TIP also entails the Thales Protocol DAO to deploy a staking contract that accepts G-UNI LP tokens of the newly created THALES/ETH G-UNI pool as deposits, and in return emits THALES token as reward pro rata, with inflation parameters being set to equal 35,000 THALES tokens per week for the duration of 10 weeks.
 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.