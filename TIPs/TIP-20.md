| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-20 | THALES token migration to l2| Draft | Danijel (@dgornjakovic) | Details of THALES token migration to l2 | https://discord.gg/8bzFdpGTrp | 2022-01-01
 
## Simple Summary
This TIP describes all the nuances of THALES token migration to L2
## Abstract
As Thales is getting ready to rollout token support on L2, there are a lot of details to consider. This TIP aim to summarize all of those and provide a detailed migration plan.
## Motivation
As per [link](https://thalesmarket.medium.com/a-part-of-thales-core-contributors-tokens-are-locked-and-its-implications-241fcec37888?source=user_profile---------6-------------------------------) 15.9m THALES tokens that were supposed to be added to a vesting contract for CCs per tokenomics vesting schedule of 4 years linear unlock, have been locked fully for 5 years. To offset for this, we propose a seamless token migration, that will swap THALES for a new token provisionally called OpTHALES 1 to 1 on L1 and migrate in to L2.  

Alongside  the release of new token, Exchanger and Bridge, this TIP proposes to migrate all unclaimed rewards to L2, as well as all staked and escrowed THALES from L1 to L2 for wallets that do not opt out and are not contracts.
More details about the auto-migration of staking and escrow below:

## Automigration of staking and escrow motivation
A number of THALES stakers have enquired about the possibility to be auto-migrated to L2 once staking is available there. Initially, we found this unconventional as the usual path when moving to another chain is that everyone chooses to migrate individually.
However, after more consideration, it felt fair to give the Thales council and community a chance to express their view and wish on how this should be handled.  

Before getting into the proposal itself, lets review the previous plan: 
* Unstaking cooldown would be reduced to a single block
* Stakers would have to start the cooldown, unstake, approve migration, migrate to L2 and finally restake on L2
* That's total of 4 L1 transactions and 1 L2 transaction
* At current 100+ GWEI the said 4 L1 transactions would set someone back $100 to $200 in gas
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

## Specification

* On 26th of January set the unstaking cooldown to 1 minute thus giving everyone an option to unstake before migration
* Add an option to opt out of migration via message signing. If someone opts out we will send THALES to that address on L1
* Last period of staking on L1 ends on 2nd of February
* After the last period is closed and final rewards are calculated into ongoing airdrop contract, we pause the following contracts on L1:  
    * Airdrop https://contracts.thalesmarket.io/mainnet/Airdrop
    * OngoingAirdrop https://contracts.thalesmarket.io/mainnet/OngoingAirdrop
    * StakingThales https://contracts.thalesmarket.io/mainnet/StakingThales
    * EscrowThales https://contracts.thalesmarket.io/mainnet/EscrowThales
* Snapshots are taken for all of the above contracts
* Airdrop of 137 will be made available on l2 to all that didnt claim it already, unless the address that did not claim is a contract.
* There are 119 contracts on L1 that did not claim the airdrop. Its unlikely those addresses will ever claim the airdrop, so the proposal is to leave that THALES 119*137 on stand by should anyone of those contract owners reach out with a desire to claim the airdrop. In such a case, we can confirm the address ownership and send 137 THALES directly.
* All ongoing rewards are migrated to L2 using the same contract (ongoing airdrop), unless the address that did not claim is a contract, in which case it will be handled as described above.
* Balances of Staking and Escrow are summed up per wallet and auto-staked on L2 if the said wallet was staking on l1
* Balance of Escrow that wasnt staked on L1 will be directly sent to that wallet on L2
* If someone triggered unstaking, the unstaking balance will be sent directly to him on L1
* Important: If an address is a contract, it will not be migrated. All contracts will be able to claim their pending balances on L1.
* The migration might take hours to days. We'll make sure to check all the data as long as we need to until we are 100% comfortable to release the new balances on L2.
* Once migration is done and new balances are available on L2:
  * Destroy StakingThales contract on L1
  * Destroy Escrow contract on L1
  * Destroy Ongoing airdrop contract on L1
  * Airdrop contract on L1 can not be destroyed before Septembar 2022. It will remain paused until it can be destroyed
* Each staker that doesnt have any ETH on L2 will get $10 worth of ETH during migration

Technical details:
* OpTHALES will be deployed both on L1 and L2
* 100m will be minted on L1 and sent to the treasury. For safety reason not all supply will be put in the Exchanger contract immediately, but the treasury will not use any OpTHALES unless it puts up collateral THALES in the Exchanger and user regular Exchanger methods to get OpTHALES
* On l2 only the standard optimism bridge implementation can mint OpTHALES
* Initially only the standard withdrawal with 7 days wait period can be used. There is no clear scenario while there would be a lot of reason to bridge to L1 other than arbing between THALES liquidity pools.  

The following contracts will be deployed on L2:  
* [ThalesExchanger](https://github.com/thales-markets/contracts/blob/main/contracts/exchange_L1_L2/ThalesExchanger.sol)
* [OpTHALESL1](https://github.com/thales-markets/contracts/blob/main/contracts/Token/OpThales_L1.sol)
* [OpTHALESL2](https://github.com/thales-markets/contracts/blob/main/contracts/Token/OpThales_L2.sol)
* [StakingTHALES](https://github.com/thales-markets/contracts/blob/main/contracts/EscrowAndStaking/StakingThales.sol)
* [EscrowTHALES](https://github.com/thales-markets/contracts/blob/main/contracts/EscrowAndStaking/EscrowThales.sol)
* [OngoingAirdrop](https://github.com/thales-markets/contracts/blob/main/contracts/Airdrop/OngoingAirdrop.sol)
* [Airdrop](https://github.com/thales-markets/contracts/blob/main/contracts/Airdrop/Airdrop.sol)
   

  
## Test Cases
 
## Implementation

## Copyright
 
Copyright and related rights waived via CC0.
