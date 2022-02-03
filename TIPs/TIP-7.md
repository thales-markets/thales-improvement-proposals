| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-7 | Title | Implemented | padzank (@padzank) | Deployment and inflation lowering of THALES single side staking | https://research.thales.io | 2021-10-07

## Simple Summary

This TIP proposes to deploy THALES single side staking on Wednesday, 13th October 2021, and to lower the initial THALES inflation for stakers by half and reserve the other half for when THALES staking launches on L2

## Abstract

From the THALES tokenomics article, planned inflation towards single side staking is 100,000 THALES tokens weekly. Plans to deploy the product and, subsequently, the THALES token on Optimism layer 2 network were revealed and entailed this TIP that proposes to lower this inflation number to 50,000 THALES tokens weekly and to reserve the other half of 50,000 THALES tokens weekly for rewards towards upcoming THALES staking on Optimism layer 2.  

THALES staking with these parameters is to be deployed on Wednesday, October 13, 2021.

## Motivation

Highest priority of further Thales developement is deployment on layer 2. Protocol roadmap is to deploy the product on L2 and then start the slow process of migrating THALES token. To expedite this process in due time, there needs to be incentives in place so THALES holders are motivated to migrate. This TIP proposes to allocate half of planned staking rewards to this goal. At this current point of THALES unlock schedule, inflation rate of 50,000 THALES tokens is guaranteed to provide a lucrative APR percentage for stakers. In time of writing this TIP, the circulating supply of THALES token is ~5.1 million tokens. For THALES single side staking to remain above 100% APR with 50,000 weekly inflation, there needs to be less than 2.6 million tokens locked in the staking contract. These previous facts guarantee that, even with halving the staking inflation, rewards are bound to be more than lucrative.

## Specification

This TIP entails Thales ProtocolDAO to deploy the following contracts on Wednesday, October 13, 2021:  

- https://github.com/thales-markets/contracts/blob/main/contracts/Staking/StakingThales.sol  

- https://github.com/thales-markets/contracts/blob/main/contracts/Staking/EscrowThales.sol  

  

This TIP also entails ThalesDAO to allocate 50,000 THALES tokens weekly to the staking contract as weekly rewards for THALES stakers.

## Rationale

n/a

## Test Cases

n/a

## Implementation

n/a

## Copyright

Copyright and related rights waived via CC0.
