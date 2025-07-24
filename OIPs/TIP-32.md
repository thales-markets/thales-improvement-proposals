| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-32 | Closing airdrop claims windown| Implemented | BigPenny| Close airdrop claim window and set 2 weeks notice to close migrated rewards claims  | https://discord.gg/rPpPcMXSeU | 2022-03-06
 
## Simple Summary
 
1. End the claiming phase of the initial THALES airdrop (137 THALES) and return the funds to Treasury 
2. Give a two weeks notice and then end the claiming phase of the unclaimed L1 rewards which were migrated to L2 and move the funds to Treasury.  

 
## Abstract
 
see #motivationn
 
## Motivation
 
Since making the Airdrop claimable on L2 we have had about 400 claims. pDAO has informed the council that likely 90% of the claims come from sybil accounts that have claimed and dumped in batches of 50+ airdrops.  

We believe that 4 months on L1 and more than a month on L2  was enough time for all organically interested users in Thales to claim their Airdrop. It is more beneficial to the community as a whole to stop those airdrops now and (for one week after this TIP gets enacted).   

It is usual practice in DeFi projects to have a limited window for airdrop claims, and that time window is usually much smaller than what Thales has allowed. It protects both the community and Core Contributors (reduced risk surface and operational overhead) to have a closure on these features. With that said this TIP also addressed unclaimed migrated rewards from L1. Due to the low gas costs on Optimism and the free ETH provided by Treasury, there is no reasonable motive for someone to not have already claimed their rewards and continue staking, providing to the LP or even selling by now. To give every legitimate user a chance to claim their pending L1 rewards we will give a two weeks notice starting with the enactment of this TIP and only then disable claiming and move the rewards to treasury.
 
## Specification
 
Airdrop contract is paused as soon as this TIP is voted in and remaining funds are moved to treasury. There is 1 week window for people to reach out to any CC and prove they have an organic (non-sybil) claim on the airdrop. The proof would just be sharing of a wallet with a history of SNX staking that is:  
* More than 1 SNX  
* Longer than 1 snapshot  

Migrated rewards contract will be active for 2 more weeks after the time this TIP is voted in (cca 20th of March 2022). At the end of that window the contract will be paused and remaining THALES will be sent back to the treasury.

## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.
 

