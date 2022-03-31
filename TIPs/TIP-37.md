| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-37 | Stop vesting of the retro SNX rewards | Draft | Kain | Stop the linear retro unlocking rewards | https://discord.gg/rPpPcMXSeU | 2022-03-24
 
## Simple Summary
 
This TIP proposes to terminate the linear unlocking of THALES token allocation towards past SNX stakers.
 
## Abstract  
 
Retroactive pro rata rewards of THALES tokens towards SNX stakers captured all of historical SNX stakers. The effect of this proportional distribution meant that 80% of this specific allocation went to the top 10 historical SNX stakers. As some of these Top 10 SNX stakers are no longer aligned with Synthetix, and hence no longer aligned with Thales, this allocation proved to be dangerous for the liquidity of the THALES token and this TIP proposes a plan to terminate this specific allocation.
 
## Motivation
 
Thales initially set out to distribute 35% of its total supply directly to SNX stakers. This was split into following buckets:  
 
    - Retro rewards since start of SNX staking until THALES TGE: 15% of total supply  
    - Ongoing rewards towards present SNX stakers: 18% of total supply
    - "One-off" airdrop to every wallet that ever staked SNX: 2% of total supply
   
Since THALES TGE event until time of writing this TIP, certain large Retro reward eligible wallets have "dumped" almost all of their unlocked THALES to date (a total of approximately 600,000 THALES tokens). Considering the limited early liquidity, this has been a significant hit on liquidity providers.  
 
To further elaborate on initial decision making around this allocation, after THALES committed to initial tokemonics of percentage of total supply, other ecosystem projects introduced the narrative of percentage of early circulating supply. If we implement that logic into distribution of THALES tokens to date, we get the following numbers already distributed to SNX stakers so far:
 
    -  4,500,000 THALES to retro SNX stakers  
    -  2,500,000 THALES to ongoing SNX stakers  
    -  2,200,000 THALES via "one-off" airdrop    
   
This adds up to a total of 9.2 million THALES tokens towards SNX stakers so far. Current THALES circulating supply is close to 16m, so Thales has effectively distributed almost 60% of circulating supply to SNX stakers in one way or another.  
Furthermore, considering that the rest of circulating supply came from THALES staking, reusing some of the logic introduced by other ecosystem projects, we can get that percentage closer to a total of 70% unlocked tokens.  
 
As the largest individual retro staker, I find it within my best interest and thus the interest of any other THALES holder that is still aligned with the ecosystem, to stop the retro rewards effectively forfeiting the remainder of my unlocking allocation.  
I am positive that there is more value in staking THALES which was unlocked so far and thus increase individual ownership of total supply during time, without having unaligned wallets accrue non-trivial amounts of THALES tokens for free.  Bonus staking rewards for SNX stakers that THALES has included in their staking logic surely help with that.
 
Every THALES token unlocked so far since TGE will be available for claiming to wallets in question, on L2 with an airdrop contract. However, as we learned the lessons from previous airdrops, there should be a time limit on how long these tokens are claimable. This TIP additionally proposes a 1 month window for claiming the unlocked rewards.    
 
The remaining tokens that were not yet unlocked (approximately 9 million THALES), are to be returned to treasury and used in a variety of ways as to be most optimally distributed to those aligned with the Thales protocol, which many of current SNX stakers are.
 
## Specification
 
Retro distribution contract is immutable, however it is using the old THALES token.  
This TIP proposes an execution plan that involves stopping the old THALES migration contract, and auto-migrating all current holders of old THALES tokens. Effectively completely deprecating the legacy THALES token.
Additional note is that the same contract contains and handles strategic partners unlocks, so that allocation is to be handled separately on separate terms.
 
Current proposed execution steps that are subject to change as we dry run the approach:
 
1. Take a snapshot of all holders of old THALES token
2. Take a snapshot of all DODO THALES/ETH liquidity providers, the corresponsive ETH and THALES balances of their positions and unclaimed THALES rewards.
3. Coordinate with all relevant tools/websites to adapt to following changes (coingecko, CMC, DeBank, Blockfolio... etc)
4. Coordinate a manual migration of Discord TipBot balances
5. Once all of the above is prepared, terminate the token migration contract
6. Manually send new THALES to all holders from the snapshot
7. Manually send new THALES and ETH to all DODO Liquidity Providers
8. Prepare a snapshot of all unlocked THALES from the retro contract and make it available to be claimed as new THALES on a newly deployed airdrop contract (L1 or L2 is yet to be determined)
9. Run calculations for Strategic investors on how much they still have left to be unlocked and prepare a new retro vesting contract for them. Gather their sentiment on how and on what network they wish to proceed.
 
 
 
 
## Copyright
 
Copyright and related rights waived via CC0.
