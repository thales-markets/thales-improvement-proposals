| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-80 | Deploy Thales protocol to Binance Smart Chain | Implemented | Danijel (@danthales) | Deploy and enable the UP/DOWN/RANGE AMM markets on Binance Smart Chain | https://discord.gg/pending | 2022-08-25
 
## Simple Summary
 
This TIP proposes to deploy Thales Positional Markets, AMM and Ranged AMM contracts to Binance Smart Chain
 
## Motivation

Thales Crypto positional markets and corresponding AMMs have matured to a point where deploying those to EVM compatible chains is not much of an additional overhead.  
Binance Smart Chain has a huge user database, and I believe its in the best interest of the Thales Protocol to explore if those users are interested in the products Thales has to offer.  
In addition, I believe BSC presence will also be helpful for a potential Binance listing down the line.  

In terms of collateral, it seems intuitive to me to go with BUSD. As it has 18 decimals, it won't require any additional contract changes.
 
## Specification
 
The Thales Protocol DAO shall:  

* Deploy all contracts necessary to fascilitate UP/DOWN/RANGE AMM markets on BSC with BUSD as their base currency.

* Deploy all contracts necessary to facilitate referrals rewards in BUSD on BSC.

* Deploy all contracts necessary to facilitate SafeBox functionality with BUSD on BSC.


The following assets will be supported with the initial deployment: ETH, BTC and BNB.  

Most variables will be inherited from the current Optimism deployment. However, I am proposing to lose the whitelisting concept of creating markets, and allow anyone to create markets on BSC. This would be a sort of a beta test for losing the whitelisting.  
As established in previous TIPs, pDAO has the discretion to choose Assets, Caps and implied volatility values. The AMM will start with $5000 for cap per market for all supported assets.  


## Test Cases
N/A
## Implementation
N/A
## Copyright
 
Copyright and related rights waived via CC0.
 
