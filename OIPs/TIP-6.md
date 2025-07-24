| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-6 | Title | Implemented | padzank (@padzank) | Adapt ongoing THALES distribution ratio between L1 and L2 SNX stakers dynamically | https://research.thales.io | 2021-10-05

## Simple Summary

This TIP proposes to dynamically adapt the ratio of THALES rewards between ongoing L1 and L2 SNX stakers as to stay proportional to the L1 and L2 ratio of SNX inflation rewards.

## Abstract

Weekly SNX inflation towards stakers can be seen in this spreadsheet: https://docs.google.com/spreadsheets/d/1a5r9aFP5bh6wGG4-HIW2MWPf4yMthZvesZOurnG-v_8/edit?usp=sharing.  

Out of the total weekly number of SNX tokens issued, currently 50,000 SNX are routed towards L2 stakers. This TIP proposes that allocation of 125,000 weekly THALES rewards for ongoing SNX stakers also follow this ratio for each weekly snapshot and to dynamically adapt the weights of THALES rewards between L1 and L2 stakers by mirroring this ratio with every subsequent change of weights from Synthetix.

## Motivation

As Synthetix slowly progresses towards migrating completely to L2, ratio of SNX staking rewards for L2 stakers will also increase. Thales needs a system to follow these changes for every weekly snapshot and to fairly allocate rewards between ongoing L1 and L2 SNX stakers.

## Specification

This TIP entails Thales ProtocolDAO to follow SNX rewards ratio between L1 and L2 stakers on a weekly level, and allocate the 125,000 weekly THALES rewards between L1 and L2 SNX stakers in the same exact ratio.

This entails to reset the airdrop contract (https://github.com/thales-markets/contracts/blob/main/contracts/Airdrop/OngoingAirdrop.sol) Merkle tree, used for ongoing distribution to SNX stakers, according to the statement above on a weekly basis.

**Every SNX staker, either on L1 or L2, will be eligible for pro-rata THALES rewards only if the staker claimed his SNX staking rewards for the previous week.**

## Rationale

n/a

## Test Cases

n/a

## Implementation

n/a

## Copyright

Copyright and related rights waived via CC0.