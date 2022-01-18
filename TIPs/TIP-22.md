 
 
| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-22 | Extension of THALES/ETH LP rewards on DODO L1 | Draft | padzank (@padzank) | Extend THALES rewards for THALES/ETH pair on DODO on L1 to allow for gradual transition towards Optimism L2 | https://discord.gg/rPpPcMXSeU | 2022-01-18
 
## Simple Summary
 
This TIP proposes to extend the rewards for THALES/ETH liquidity providers on DODO DEX on L1 Ethereum mainnet to allow for a gradual transition towards L2 Optimism network
 
## Abstract
 
Incentives for liquidity providers of THALES/ETH pair on DODO exchange are scheduled to end on Friday, Jan 28 2022.  
Since the migration of THALES token to Optimism is planned for Feb 02 2022, this TIP proposes to extend the existing LP incentives on L1 for **10 weeks** with inflation lowered to **20,000 THALES per week** (from original 50,000 THALES per week). This should ensure the liquidity remains stable for the THALES token while the gradual migration towards Optimism is taking place.

## Motivation
 
After the initial launch of the THALES token, DODO team has created a THALES/ETH pool that was seeded initially with 80,000 THALES and 56 ETH. After the pool creation, DODO and Thales agreed to incentivise liquidity provision for this pool with dual rewards of 50,000 THALES and 15,000 DODO per week for the total duration of 20 weeks. 

This 20 week long program is scheduled to end on the last week of January. Since the plan is to migrate the THALES token to Optimism on 2nd February and slowly start building liquidity there, there is a risk of a short period of liquidity instability of the THALES token in this transition period. To mitigate this risk, this TIP proposes to extend the rewards for the existing THALES/ETH DODO pool. As we are looking to avoid a complete and sudden cutoff of rewards that would potentially cause a large scale exodus of liquidity, extending the rewards for 10 weeks with lower inflation of 20,000 THALES tokens per week, should help mitigate this scenario. LPs will still be able to collect significant rewards while the liquidity for the new token is slowly being built on Optimism.

## Specification
 
 This TIP entails the Thales TreasuryDAO to send 200,000 THALES tokens to DODO mining rewards contract designated for the THALES/ETH pool, extend the duration of inflation for exactly 10 weeks and lower the emissions for the said contract to 20,000 THALES tokens per week.
 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.