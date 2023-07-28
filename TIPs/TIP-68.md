| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-68 | Overtime referrals and new configuration| Implemented | Danijel (@danijelthales) | Add referrals to Overtime, increase liquidity, reduce fees | https://discord.gg/8bzFdpGTrp | 2022-07-18
 
## Simple Summary
 
This TIP proposes to add a referral program to Overtime, increase liquidity per market and reduce LP fee
 
 ## Motivation

After the initial soft launch of Overtime, which has demonstrated a stable architecture and a well laid out product, we are ready to go into the next phase of more liquidity and more agressive marketing approach, just in time for more sports/leagues to start their 2022-23 seasons and become supported on the platform.
    
For this to be achieved, I am proposing reducing the min_spread variable from 1% to 0.5%, which should effective make the odds offered on Overtime overall the best across all known sport books.  
  
I am also proposing allowing the remaining 0.5% to be used for a referral program as introduced in [TIP-54](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-54.md).  
Effectively for every new trader on overtime someone refers, the referrer will get 0.5% of volume that trader generates in sUSD. Program will be onboing until decided otherwise by governance.  

Lastly, I am proposing increasing liquidity on any given market from 1000 sUSD to 5000 sUSD maximum that the AMM can use for collateralizing positions.  
As we have already forfeited any LP fees with the above reduction and referral program, I am proposing to couple this increase with increasing the max skew impact from 5% to 10%. Important to note that this is only worse than current configuration if AMM is skewed on a single position in a given market for more tan 2500 sUSD (at risk).  Considering the current cap of 1000 sUSD, at that size the skew impact is effectively decreased 2.5x.    

The above should be coupled with further marketing incentives in both THALES and OP tokens. The incentives can be laid out in this TIP following a governance discussion or a decoupled TIP.      

## Specification

- Reduce min_spread variable from 1% to 0.5%  
- Introduce referral program where the referrer gets 0.5% of any trade of a wallet that came via his/her referral link  
- Raise cap per market from 1000 sUSD to 5000 sUSD  
- Raise maximum skew impact from 5% to 10%  
 
## Copyright
 
Copyright and related rights waived via CC0.
 

