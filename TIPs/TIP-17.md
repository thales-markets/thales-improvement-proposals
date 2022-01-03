| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-17 | THALES L2 rollout| Draft | Danijel (@dgornjakovic) | Formalize a plan for THALES l2 rollout| https://discord.gg/8bzFdpGTrp | 2021-12-29
 
## Simple Summary
 
The TIP aims to formalize a plan on how rolling out THALES token on Optimism mainnet will be conducted. 
 
## Motivation
THALES token is currently only available on layer 1 Mainnet. As most of Thales protocol volume is happening and is planned to happen on Optimism Mainnet, Thales should also offer token bridge and staking on Optimism Mainnet, as well as build liquidity for its native governance token on that layer 2 chain.  
Furthermore, this TIP aims to improve Thales Staking module by offering a gamified approach to staking which rewards active protocol users.  

Per [link](https://thalesmarket.medium.com/a-part-of-thales-core-contributors-tokens-are-locked-and-its-implications-241fcec37888?source=user_profile---------6-------------------------------) we explained how a large chunk of Core Contributor tokens got locked mistakenly in a contract for 5 years. To offset this, Thales will deploy an Exchanger contract that offers 1 to 1 exchange to a new token which is provisionally called OpTHALES and which will be bridged to and supported on Optimism Mainnet.  

Thales has been rewarding 125k THALES rewards to SNX users pro rata based on the SNX staking debt on a weekly level. While this number is a large portion of THALES inflation, it did not make a significant impact on Synthetix staking due to the large TVL in SNX staking and it hardly makes a difference to an average SNX staker. This TIP proposes to reduce that total number of weekly rewards for SNX stakers, while reverting the value of that inflation to THALES staking. To achieve this SNX staking will have a significant weight in the new gamified THALES staking approach that provides a bonus to stakers based on certain parameters.    

## Specification
When all contracts are ready which is planned to be toward end of January/early February 2022. this TIP proposes the following:

1. Create a seamless Exchanger+Bridge on Ethereum mainnet that accepts THALES as input, exchanges it 1 to 1 to OpTHALES and migrates it to Optimism mainnet. The said contract also accept exchanging OpTHALES to THALES. OpTHALES will have 100m supply, identical to THALES, but 15.9m tokens that were mistakenly locked will be kept in treasury, while 85.1 million will be put into the exchanger contract, and only minted when THALES is offered in exchange 1 to 1.
2. Move all unclaimed airdrops to optimism mainnet, thus allowing those who still haven't claimed the airdrop to claim it on L2
3. Shift all pending ongoing rewards and make those claimable on Optimism Mainnet
4. Reduce the staking cooldown to 1 second (whatever is minimum) to allow a smooth migration to L2
5. Deprecate L1 staking and rollout staking on L2 where the first week will have doubled base rewards (50k to 100k THALES) to incentivize migration.
6. Deprecate ongoing rewards concept which required a centralized approach to offset for layer 1 gas costs
7. Upgrade the staking module to Thales gamified staking approach that offers up to 2x bonus on base rewards based on the specification below.  


Gamified THALES staking on Optimism Mainnet:
- Base weekly rewards of 70k THALES
- Introduce a bonus with a maximum value of 30% on top of base rewards that is calculated based on the following:  
      - 50% based on SNX staking. If a THALES staker has at least 1 SNX staked per THALES he would receive as base reward, he gets maximum bonus, otherwise he gets proportional to the SNX he has staked   
      - 40% weight to AMM trading volume. If a THALES staker has at least 10 sUSD AMM volume in last 4 epochs per 1 THALES he gets as base reward, he gets maximum bonus in this category, otherwise he gets a bonus proportional to the average volume he generated in the last 4 epochs divided by the base THALES rewards he is eligible to receive.    
      - 10% weight if the staker participated in the last Thales Royale. This value can be either 0 or max.
       
      
On Optimism Mainnet rewards will have to be claimed weekly and be subject to same escrow rules as in the staking contract on Ethereum Mainnet.
Further improvements to staking can be formalized in additional TIPs.

This TIP, if voted in, would seize ongoing inflation of 125k to SNX stakers in favor of a more effective mechanism that still maintains the ongoing aligment with SNX stakers, but reverting value back to THALES staking. THALES that is being saved with this new approach can be used to increase THALES staking rewards or offer other incentives for the benefit of the protocol. 

## Test Cases
 
## Implementation

## Copyright
 
Copyright and related rights waived via CC0.
