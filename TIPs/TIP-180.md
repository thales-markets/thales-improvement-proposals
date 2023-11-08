| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-180 | Removal of Incentives from THALES USDC Pools | Draft | degeneratoor | This TIP proposes the discontinuation of incentives for THALES-USDC liquidity pools across all chains to prevent resource waste and consolidate liquidity provision efficiency. |  | 2023-11-07
 
TIP: 180 - Removal of Incentives from THALES-USDC Pools

## Simple Summary
This TIP suggests the complete removal of incentives from THALES-USDC liquidity pools on all chains where they are currently active.

## Abstract
The proposal aims to cease all incentive emissions to the THALES-USDC pools across all chains, including the base chain, Optimism, and Arbitrum.

## Motivation
The THALES token currently has liquidity pools paired with both WETH and USDC. Given that both WETH and USDC are highly liquid assets and that there is a straightforward conversion path between the two, maintaining incentives for liquidity provision in both pools may not be an efficient use of the protocol's resources. The THALES-WETH pool will continue to receive incentives as per the current or any future TIP, thereby ensuring sufficient liquidity for the THALES token.

## Specification
The removal of incentives will affect the following liquidity pools:

- THALES-USDC pool on the base chain
- THALES-USDC pool on Optimism
- THALES-USDC pool on Arbitrum
This means the Thales Protocol DAO and Treasury DAO will no longer allocate any rewards (in OP, THALES, or any other form) to these pools.

## Rationale
Concentrating incentives on the THALES-WETH liquidity pool allows the protocol to avoid the unnecessary dispersion of resources across multiple pools when such diversity does not significantly contribute to the protocol's liquidity or functionality. With USDC and WETH being highly liquid assets, and the ease of converting between the two, incentivizing a THALES-USDC pool is redundant and constitutes a waste of the protocol's assets. By eliminating incentives for the THALES-USDC pool, the protocol can preserve its resources and enhance the efficiency of its incentive allocations.
## Implementation
Upon acceptance of this TIP, the following actions will be implemented:

Cessation of all reward emissions to THALES-USDC pools effective immediately after the conclusion of the current rewards cycle.
Update to the protocol documentation and communication to reflect this change.
