| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-66 | Implement claimOnBehalf method on the THALES staking contract | Implemented | padzank (@padzank) | This TIP proposes to implement claimOnBehalf method for THALES staking contract so individual stakers can automate weekly claims of THALES staking rewards | https://discord.gg/8bzFdpGTrp | 2022-07-05
 
## Simple Summary
 
This TIP proposes to implement the `claimOnBehalf` method on the THALES staking contract so individual stakers are able to automate weekly claims of THALES staking rewards.
 
## Abstract
 
Currently THALES staking rewards need to be claimed manually on a weekly basis or the weekly reward is forfeited and returned to the treasury. This TIP proposes to implement the `claimOnBehalf` method on the [THALES staking contract](https://optimistic.etherscan.io/address/0xC392133eEa695603B51a5d5de73655d571c2CE51) that will allow THALES stakers to individually enable a third-party solution to trigger that method for them and thus automate the weekly claiming process.
 
## Motivation
 
There is no protocol relevant reason to keep claiming of weekly staking rewards mandatory so to accrue rewards. One positive case for mandatory weekly claiming is that it makes people interact with the protocol on a weekly level, but the more impactful countereffect is that some stakers feel forced and pressured to reach the snapshot deadline. This mechanism can potentially disincentivize THALES stakers and overall have a negative effect on overall user experience. This TIP's proposal to implement the `claimOnBehalf` method will make it possible for individual stakers to explore automating their award claiming and thus improve their UX significantly.
 
**Implementing the `claimOnBehalf` method only opens the option for individual stakers to automate the claiming process. After this method is implemented, each staker wanting to automate claiming would have to manually create a task for auto claiming via a third party service such as Gelato.**
 
## Specification
 
This TIP entails the Thales Protocol DAO to implement `claimOnBehalf` method to the [StakingThales](https://optimistic.etherscan.io/address/0xC392133eEa695603B51a5d5de73655d571c2CE51) contract.
  
The `claimOnBehalf` method is to additionally support `address` input parameter that allows stakers to whitelist addresses to enable them to trigger the claim on their behalf.
 
## Rationale
 
N/A
 
## Test Cases
 
## Implementation
 
## Copyright
 
Copyright and related rights waived via CC0.
 

