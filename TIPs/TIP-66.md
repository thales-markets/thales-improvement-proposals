| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-66 | Implement claimOnBehalf method on the THALES staking contract | Draft | padzank (@padzank) | This TIP proposes to implement claimOnBehalf method for THALES staking contract so individual stakers can automate weekly claims of THALES staking rewards | https://discord.gg/8bzFdpGTrp | 2022-07-05

## Simple Summary

This TIP proposes to implement the `claimOnBehalf` method on the THALES staking contract so individual stakers are enabled to automate weekly claims of THALES staking rewards.

## Abstract

Currently THALES staking rewards need to be claimed weekly or they are forfeited and returned to the treasury. This TIP proposes to implement the `claimOnBehalf` method on the THALES staking contract that will allow THALES stakers to enable a third-party solution to trigger that method for them.

This TIP additionally proposes to initially only whitelist the Gelato automation contract for the `claimOnBehalf` method. Having this method open without a whitelist can lead to anyone claiming on behalf of anyone else, and this behaviour can jeoperdize Bonus Rewards maximization efforts of individual stakers trying to perfectly time their claims.

## Motivation

There is no protocol relevant reason to keep claiming of weekly staking rewards mandatory so to accrue rewards. One positive case for mandatory weekly claiming is that it makes people interact with the protocol on a weekly level, but the more impactful countereffect is that stakers feel forced and pressured to reach the snapshot deadline. This mechanism can potentially disincentivize THALES stakers and overall have a negative effect on overall user experience. This TIP's proposal to implement the `claimOnBehalf` method will allow individual stakers to explore automating their award claiming and thus improve their UX significantly.

**Enabling auto-claiming also keeps Protocol Users and SNX stakers to compound higher rewards and increase their overall ownership percentage of THALES total supply via Gamified Staking, compared to passive THALES stakers that only accrue base staking rewards.**

## Specification

This TIP entails the Thales Protocol DAO to implement `claimOnBehalf` method to the [StakingThales](https://optimistic.etherscan.io/address/0xC392133eEa695603B51a5d5de73655d571c2CE51) contract and whitelist the Gelato automation contract to be able to trigger the said method on behalf of users.

## Rationale
 
N/A
 
## Test Cases
 
## Implementation
 
## Copyright
 
Copyright and related rights waived via CC0.