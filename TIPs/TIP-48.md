| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-48 | Changes to gamified staking | Draft | Danijel| Change gamified staking configuration  | https://discord.gg/rPpPcMXSeU | 2022-05-12
 
## Simple Summary
 
This TIP proposes to increase protocol usage bonus while reducing the minimal threshold to receive it.    
It also proposes removing Thales Royale bonus and the SNX bonus.  
 
## Abstract
 
With council agreeing protocol usage is the most important aspect for Thales growth with regards to distributing OP tokens, and Thales releasing 3 new products (ranged AMM, exotic markets and sport markets) it makes sense to focus THALES inflation allocation for stakers on usage of these products.  
 
## Motivation
 
Is is currently relatively difficult to max out protocol usage bonus.  
With Thales releasing 3 new products: Ranged AMM, Exotic Markets and Sport' Markets, it makes more sense to focus staking rewards to additionaly rewards stakers that use the protocol, per the original idea of gamified staking. 
Thales Royale is to be paused after season 10 (Royale of Royales).  

With the above in mind I propose the following in specification section.   

 
## Specification 

Current Gamified staking configuration is:  
- 70k THALES base rewards  
- 21k THALES bonus rewards  
  - 50% or 10.5k THALES based on SNX staking. If a THALES staker has at least 1 SNX staked per THALES he would receive as base reward, he gets maximum bonus, otherwise he gets proportional to the SNX he has staked     
  - 40% or 8.4k THALES based on AMM trading volume. If a THALES staker has at least 10 sUSD AMM volume in last 4 epochs per 1 THALES he gets as base reward, he gets maximum bonus in this category, otherwise he gets a bonus proportional to the average volume he generated in the last 4 epochs divided by the base THALES rewards he is eligible to receive.      
  - 10% or 2.1k THALES weight if the staker participated in the last or ongoing Thales Royale. This value can be either 0 or max.  
  
I propose the following:  
- 70k THALES base rewards  
- 21k THALES bonus rewards
  
21k THALES go to Protocol Usage bucket. This counts sUSD volume from AMM trading, ranged AMM trading, sport's AMM trading and exotic markets bidding. To max out the bucket a user needs to have at least 5 sUSD traded per 1 THALES received in last 4 weeks (staking epochs).  If he has less, he gets proportionally less rewards.
 
    
Effectively the threshold for protocol usage bucket is halved while offering multiple products in which this bonus can be increased.  
The SNX bucket is removed. 
 

## Implementation
The TIP entails changing configuration of StakingThales contract
 
## Copyright
 
Copyright and related rights waived via CC0.

