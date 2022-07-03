Tip-62 Bonus Reward Calculation

| id | Title | Status | Author | Description | Discussions to | Created |
 | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | 
| TIP-62 | Bonus Reward Calculation | Draft | Milkywave & BigPenny | Distribute the staking bonus rewards via snapshot | https://discord.gg/GgUKeMbX9y | 2022-07-03

## Simple Summary
Distribute the staking bonus rewards via snapshot method and calculate the share per user only among those actually eligible.

## Motivation
Currently the base staking rewards are calculated pro rata for all stakers based on a weekly snapshot. The bonus rewards are calculated via a “rolling tally” of staked SNX and protocol trading volume resulting in a maximum bonus of 50% on top of the weekly base rewards. Unclaimed bonus rewards are returned to the treasury. The rolling tally is calculated throughout the entire rewards epoch, until the staker decides to claim. 

We propose that the bonus rewards calculation gets changed from a “rolling tally until claim” to a “rolling tally until snapshot”, so that only active SNX stakers and protocol users at the time of the weekly snapshot benefit from the bonus rewards. SNX stakes or protocol volume generated after the snapshot will be counted towards the next rewards epoch. Thus, active SNX stakers as well as protocol users benefit from the entire bonus rewards pool and not only from a fixed share.

This is a prerequisite for the "TIP-63 Rewards Rollover & Burn" would require this, otherwise the calculation (max. 50% on top of the base rewards) is not feasible.

## Specification
Change the bonus rewards calculation from a “rolling tally until claim” to a “rolling tally until snapshot”. The time of the bonus snapshot is identical with the time for the base rewards snapshot.
Calculate bonus rewards only amongst those stakers who are eligible for bonus rewards at the time of the snapshot.This effectively removes the 50% limit for bonus rewards, since
the number now varies. The minimum of 50% bonus rewards on top of the base rewards at 100% eligibility remains unchanged by this.

## Test Cases
### Status Quo:
Total Bonus Rewards: max 50% on top of the base rewards (Total reward pool size 15 Thales)
* Alice: 
Base rewards of 10 Thales and and has sufficient protocol volume and SNX stake to receive the maximum bonus reward
*Bob:
Base rewards of 20 Thales and has no protocol volume and did not stake SNX.

#### Current allocation of bonus rewards:
* Alice: 5 Thales (Can be claimed, as requirement are met)
*Bob: 10 Thales (Cannot be claimed, as requirements not met)
#### Proposal:
*Since only Alice was eligible for the max. bonus rewards allocation in the snapshot, she has the possibility to claim the entire bonus rewards of 15 Thales

## Copyright Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

