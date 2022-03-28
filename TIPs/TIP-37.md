| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-37 | Stop vesting of the retro SNX rewards | Draft | Kain | Stop the linear retro unlocking rewards | https://discord.gg/rPpPcMXSeU | 2022-03-24 

## Simple Summary
 
This TIP aims to stop the linear unlocking THALES rewards allocation to SNX stakers.
 
## Motivation

Thales initially set out to distribute 35% of its total supply directly to SNX stakers. This was split into following buckets:  
    - Retro rewards since start of staking till TGE 15%  
    - Ongoing rewards for SNX stakers 18%  
    - Airdrop 2% to everyone that ever staked SNX  
    
Retro rewards captured stakers since day 1 of SNX staking. The effect of this was that 80% of this allocation went to top 10 stakers. 
While the intent of this was to "thank" all the SNX supporters since beginning, a number of those top 10 historical stakers are no longer aligned with Synthetix.  
Those wallets have dumped almost all unlocked THALES to date so a total of close to 600k THALES, which considered the low early liquidity has been a huge hit on liquidity providers.  

To futher elaborate on the reasoning, after THALES commited to initial tokemonics, other ecosystem projects introduced the narrative of percentage of early circulating supply, or on TGE.  
Reusing that logic on THALES to date the following has been distributed:  
    -  4,500,000 THALES to retro stakers  
    -  2,500,000 THALES to ongoing stakers  
    -  2,200,000 THALES via airdrop    
    
This adds up to a total of 9.2 million. Current THALES circulating supply is close to 16m, so THALES has effectively distributed almost 60% of circulating supply to SNX stakers in one way or another.  
Furthermore, considering that the rest of circulating supply came from THALES staking, reusing some of the logic introduced by other ecosystem projects, we can get that percentage closer to 70%.  

As the largest individual retro staker I find it within my best interest and thus the interest of any other THALES holder that is still aligned with the ecosystem to stop the retro rewards, thus forfeiting the rest of my allocation.  
I am positive that there is more value in staking THALES which was unlocked so far and thus accumulating more without the sell pressure of whales no longer aligned with the ecosystem.  

Everything that was unlocked so far will be available to those wallets to claim on L2 with an airdrop contract as Thales has used before. However, as we learned from previous airdrops, there should be a time window on how long this is claimable. This TIP proposes a 1 month window for claiming the unlocked rewards.     

The remaining for retro unlock which is close to 9m THALES is to be returned to treasury and can be used in a variety of ways to be distributed to those aligned with Thales protocol, which many of current SNX stakers are.


## Specification
Retro distribution contract is immutable, however it is using old THALES token.  
This TIP can be executed by stopping the old THALES migration contract, and automigrating all current holders of old THALES.  
Also the contract contains strategic unlocks, so that has to be handled separately. 

Current known steps that are subject to change as we dry run the approach:
1. Take a snapshot of all holders of old THALES token
2. Take a snapshot of all DODO LPers and their corresponsive ETH and THALES balances and still unclaimed THALES rewards
3. Ensure there is no other major tool such as coingecko, coinmarketcap, blockfolio, etc... that dispays the old THALES token
4. Handle things such as old THALES in tip bot
5. Once the above is all prepared: kill token migration contract
6. Manually send new THALES to all holders from the snapshot
7. Manually send new THALES and ETH to all DODO LPers
8. Prepare a snapshot of all unlocked THALES from the retro contract and make it available to be claimed as new THALES on a airdrop contract (L1 or L2 is the question?)
9. Run calculations for Strategic investors on how much they still have left to be unclocked and prepare a new retro vesting contract for them. Talk to them about where they would like 
 


 
## Copyright
 
Copyright and related rights waived via CC0.
