Tip-63 Rewards Rollover & Burn

| id | Title | Status | Author | Description | Discussions to | Created |
 | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | 
| TIP-64 | Rewards Rollover & Burn | Deprecated | BigPenny & Milkywave | Rollover & partially burn unclaimed staking rewards | https://discord.gg/ZK89ZkDZwT | 2022-07-03



## Simple Summary
Staking rewards, including base rewards and bonus rewards which get not claimed till the end of an epoch get partially burned and partially rolled over to the next weekly epoch instead of being sent back to Treasury.


## Motivation
Right now THALES stakers get a pro rata share of the total weekly base rewards assigned to them which they have to claim before the start of the next weekly epoch. Additionally Stakers can earn bonus rewards for staking SNX and generating volume on the Thales protocol markets. Base rewards and bonus rewards which are not claimed until the end of a weekly epoch get sent back to the Treasury. Effectively every new staker dilutes the base rewards for every other staker, regardless of them claiming or not.

Active stakers benefit from the partial roll over and all Thales token holders benefit from the partial burn, as the total supply is reduced (+ token value due to future fee distribution share). Given the fact that not everyone who claims base rewards also claims 100% of their bonus rewards, there will be a surplus of bonus rewards after the base rewards supply is fully depleted. That surplus shall be burned as well, concluding the token distribution schedule.

## Specification
* 50% of all rewards which were not claimed until the end of the current weekly epoch get sent to address 0x000000000000000000000000000000000000dEaD, effectively burning the tokens.

* 50% of all rewards which were not claimed until the end of the current weekly epoch get rolled over to the next weekly epoch, effectively augmenting that weeks reward supply for everyone.

After the depletion of the entire base rewards supply, 100% of the remaining bonus rewards supply gets burned, concluding the token distribution schedule.

The share of burned and rolled over tokens can be adjusted by governance via TIP.

## Copyright Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
