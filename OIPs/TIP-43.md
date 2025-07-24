| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-43 | Modification of THALES token LP program | Implemented | BigPlutus (@BigPenny)| Modification of THALES token LP program | https://discord.gg/rPpPcMXSeU | 2022-04-16
 
## Simple Summary
 
This TIP proposes to revert the reduction of the LP staking rewards introduced by TIP-41.
 
## Abstract
 
This TIP proposes to set 45,000 THALES tokens rewards for the THALES/WETH G-UNI LP token stakers. The program will end according to the orginal schedule of TIP-41, namely the 13th of May, 2022.
 
## Motivation

The reduction of THALES rewards towards THALES/WETH G-UNI LP token stakers, from 50,000 to 30,000 THALES tokens weekly has resulted in the APY for Stakers outperforming the APY for liquidity providers. Considering that liquidity providers subject themselves to risk of impermanent loss, their rewards should not be lower than those of a secure single sided staking pool.

The idea of TIP-41 was to taper down LP reward while ramping up the bonds program, giving a stronger emphasis on bonds, however there is no need to reduce the LP incentives to achieve this goal. 
 
## Specification
 
  - This TIP entails the Thales Protocol DAO to increase THALES rewards towards THALES/WETH G-UNI LP token stakers, from 30,000 to 45,000 THALES tokens for the rest of the period until 13th of May.
 
 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.

