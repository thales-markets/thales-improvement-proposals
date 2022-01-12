| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-20 | Staked THALES migration to L2 | Draft | Danijel (@dgornjakovic) | Automatic migration of staked THALES to L2 | https://discord.gg/8bzFdpGTrp | 2022-01-01
 
## Simple Summary
This TIP proposes an automatic migration of all Stakers to L2.
## Abstract
Initial plan laid out in TIP-17 was to reduce the staking cooldown to a minimum value of 1 block so that all stakers can migrate individually. However, considering the 3 digits gas prices we witnessed lately, I want to propose to the council and the community to consider allowing Protocol DAO to conduct an automatic migration of all Staked THALES as well as for Escrowed THALES.
## Motivation
A number of THALES stakers have enquired about the possibility to be auto-migrated to L2 once staking is available there. Initially, we found this unconventional as the usual path when moving to another chain is that everyone chooses to migrate individually.
However, after more consideration, it felt fair to give the Thales council and community a chance to express their view and wish on how this should be handled.  

## Specification
Before getting into the proposal itself, lets review the previous plan: 
* Unstaking cooldown would be reduced to a single block
* Stakers would have to start the cooldown, unstake, migrate to L2 and finally restake on l2
* That's total of 3 L1 transactions and 1 L2 transaction
* At current 100+ GWEI the said 3 L1 transactions would set someone back $100 to $200 in gas
* First two weeks on l2 would have extra baes rewards (100k instead of 70k) to offset the gas costs
* L1 rewards will stop being distributed, so the only reason someone would not migrate is: a. Gas costs or b. Wasnt aware of the migration
* This means stakers technically need to migrate in a week or mostly two to capture those early rewards
* There is no way to allow a similar quick migration of the escrowed THALES, the only approach for that is to let it fully vest, claim it, migrate to L2 and restake it.
* That would be two more L1 transactions and in addition the escrowed THALES is not compounding rewards until its migrated to l2 and restaked

If we review the staking breakdown on L1 https://thalesmarket.io/governance/thales-stakers/, we will see that there are about 150 stakers that staked the airdrop of 137 THALES. This is quite commendable due to L1 gas costs, but lets be realistic, spending $200 in gas to migrate that amount to L2 is quite unrealistic of an ask...

The approach above is a usual one for migrating from one chain to another where everyone is in charge of moving their funds if they wish so. However, in this case and for THALES stakers specifically, there isn't any actual reason to stay on L1, so let's consider the alternative approach:
* StakingThales and EscrowThales contract both have an out-of-the-box method in Ethereum which is called `selfDestruct` and can be called by Thales Protocol DAO to destroy the contract and retrieve the funds
* To be fully transparent, we initially did not include such methods in contracts, which is why the RetroUnlock contract doesnt have it and is fully immmutable
* However, after the lessons learned in [link](https://thalesmarket.medium.com/a-part-of-thales-core-contributors-tokens-are-locked-and-its-implications-241fcec37888?source=user_profile---------6-------------------------------) and by following the industry standards, we realized its acceptible to have such safety measures that are entrusted to Protocol DAO and it introduces no additional risk to the protocol as Protocol and Treasury DAO are already entrusted with all value locked in the protocol and basically keeping the protocol safe.
* Protocol DAO could pause both StakingThales and EscrowThales, take a snapshot of all balances, destroy the contracts and recreate them with the snapshot state on L2
* To reduce some overhead, I suggest to allocate all EscrowedThales directly to the staked balance on L2. It would be locked for 7 days (unstaking cooldown by default), and considering that it will take time for liquidity to build on l2, and that rewards will be quite high for stakers in the first few weeks, there is no real concern that the EscrowedThales that is made available earlier in such a way will be used in any different way than for staking.
* The migration will be announced with at least one week notice

The implication of the suggested approach is that technically stakers lose custody of their staked THALES for a brief amount of time and Protocol DAO seizes that custody to perform the migration and then relinquishes it.  While personally I found this controversial when first brought up, I am now under belief that its the purpose of Protocol DAO and myself to offer such potential solutions and have the governance and thus the said stakers decide how they want the migration executed.

Perhaps an interesting approach to this is the old-school pros and cons.

PROs:
* Save individual stakers at least $100 and likely more in gas costs for direct migration of Staked balance
* Ensure everyone is migrated to L2, even people that might not be actively monitoring their Thales staking
* Save individual stakers who have THALES in Escrow at least $100 in gas costs to vest and migrate to L2.
* Allow the already claimed and escrowed THALES to participate in early staking on L2
* Allows everyone to stake THALES just before the migration and thus only pay the cost of 1 staking transaction instead of full migration

CONs:
* Unconvential approach where Protocol DAO takes temporary custody over staked funds
  
## Test Cases
 
## Implementation

## Copyright
 
Copyright and related rights waived via CC0.
