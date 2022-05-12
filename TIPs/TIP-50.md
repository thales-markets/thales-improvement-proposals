| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-50 | Utilize Safe Box| Draft | Danijel| Use the sUSD from SafeBox as part of tokenomics  | https://discord.gg/rPpPcMXSeU | 2022-05-12
 
## Simple Summary
 
This TIP proposes to commense leveraging sUSD accrued in SafeBox as part of THALES token tokenomics
 
## Abstract
 
Use sUSD from SafeBox to buyback and burn THALES  
 
## Motivation
 
While SafeBox is still not at significant levels, it did 2x in a matter of couple of weeks and is holding approximately 22k sUSD (18k Optimism and 4k Polygon).  
With Thales releasing more products very soon (Ranged markets, Sport markets), and OP tokens distribution incentivizing protocol volume, it is expected SafeBox to receive further fees.  
This proposal however is more about establishing the infrastructure for potential buyback&burn strategy, while the exact rates are to be configured as we monitor the income of sUSD into SafeBox.  

I am proposing the buyback and burn strategy as I find it more impactfull now then distributing the sUSD fees to stakers on weekly basis.  At current low THALES price, this could allow a large amount of THALES to be burned, until such a time comes that sUSD fees distributed to THALES stakers can be significant and the protocol should move to seize buyback and burn and instead distribute the fees directly pro rata to stakers.    
 
## Specification 

Establish a rate in which THALES will be bought back using SafeBox contract. There will be a method called "executeBuyback" that will be callable if enough time has passes since last call per defined ratio.  
The method will be callable by anyone, but we will have a keeper bot doing it.  

I am proposing a low rate to get the framework started and adapting it as we monitor the inflow of sUSD into SafeBox.  
Proposed rate is 100 sUSD per 24h.  

# Variables  
`sUSDPerTick` - 100 sUSD   
`TickLength`  - 24h

## Implementation
Method executeBuyback can be called if at least 1 TickLength has passed since last buyback.  
It then calculates how many ticks passes and executes buyback via 1inch integrated contract.  

As burning makes no sense on L1, THALES will accrue in SafeBox contract until ProtocolDAO periodically pulls it, sends it to L1 and executes the Burn.
 
## Copyright
 
Copyright and related rights waived via CC0.

