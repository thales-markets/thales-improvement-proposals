| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-22 | Extension of THALES/ETH LP rewards on L1 | Implemented | slade (@slade45), padzank (@padzank)| Extend THALES rewards for THALES/ETH pair on DODO on L1 to allow for gradual transition towards Optimism L2 | https://discord.gg/rPpPcMXSeU | 2022-01-18
 
## Simple Summary
 
This TIP proposes to extend the rewards for THALES/ETH liquidity providers on DODO DEX on L1 Ethereum mainnet to allow for a gradual transition towards L2 Optimism network
 
## Abstract
 
Currently there is an LP program in place on Dodo exchange which emits 50,000 THALES tokens weekly to LP providers. With L1 liquidity provider (LP) incentives coming to an end in February, this TIP outlines the preparation for future LP incentives beyond the incentives currently in place.  
Incentives for liquidity providers of THALES/ETH pair on DODO exchange are scheduled to end on Friday, Jan 28 2022 ([block number 14092340](https://etherscan.io/block/countdown/14092340)).  
In order to not have a sudden break in incentives and also encourage slow build-up of liquidity on L2 Optimism, since the migration of THALES token to Optimism is planned for Feb 02 2022, this TIP proposes to extend the existing LP incentives on L1 for **5 weeks** with inflation lowered to **20,000 THALES per week** (from original 50,000 THALES per week). This should ensure the liquidity remains stable for the THALES token while the gradual migration towards Optimism is taking place.

## Motivation
 
After the initial launch of the THALES token, DODO team has created a THALES/ETH pool that was seeded initially with 80,000 THALES and 56 ETH. After the pool creation, DODO and Thales agreed to incentivise liquidity provision for this pool with dual rewards of 50,000 THALES and 15,000 DODO per week for the total duration of 20 weeks. 

This 20 week long program is scheduled to end in the last week of January. The plan is to migrate the THALES token to Optimism on 2nd February and slowly start building liquidity there. There is a risk of a short period of liquidity instability of the THALES token in this transition period. To mitigate this risk, this TIP proposes to extend the rewards for the existing THALES/ETH DODO pool. As of time of writing this TIP, there is a ~158% APR of THALES emissions with ~$2.5M of TVL. As we are looking to avoid a complete and sudden cutoff of rewards that would potentially cause a large scale exodus of liquidity, extending the rewards for **5 weeks** with lower inflation of **20,000 THALES tokens per week**, should help mitigate this scenario. LPs will still be able to collect significant rewards while the liquidity for the new token is slowly being built on Optimism.  
With the current TVL of ~2.5M, the projected APR with the 20,000 THALES rewards per week would be ~65%. However, we can expect a large portion of this TVL to migrate towards Optimism and participate in either staking or novel LP incentives on Optimism, and thus increase the projected yield for remaining LPs on L1 above 100%. We can expect the APR to be competitive and organically balanced out between L1 and L2 incentives for the duration of these 5 weeks.  

## Specification
 
 This TIP entails the Thales TreasuryDAO to facilitate a transfer of 100,000 THALES tokens to DODO mining rewards contract designated for the THALES/ETH pool, extend the duration of inflation for exactly 5 weeks and lower the emissions for the said contract to 20,000 THALES tokens per week.
 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.
