| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-70 | Thales vaults| Draft | Danijel (@danijelthales) | Introduce Thales Vaults | https://discord.gg/8bzFdpGTrp | 2022-07-18
 
## Simple Summary
 Vaults will be a suite of automated trading strategies, where users can deposit funds that trade with Thales AMM.  
 
 ## Motivation
Structured products are very popular in DeFi space. Thales unique offering allows for many interesting automated strategies to be implemented. Furthermore, the concept can be reused by external contributors to create their own automated stategies and allow users to deposit into those (similar to dhedge).  

With the addition of AMM discounts, Vaults can be leveraged to balance the AMM, while offering longterm profitable returns to users depositing into vaults (as math says that with discounts the vault should be winning given enough time and sample, assuming BlackScholes pricing is correct). Depositing in such vaults is almost an equivalent to providing liquidity into AMM. 

This TIP is to establish the general concepts of vaults, whereas specific vaults will be added ad hoc. 
Due to complexity of managing vaults and its many parameters, I am asking to give pDAO freedom to add new vaults and adapt vault parameters ad hoc until the product matures and most popular vaults are established and don't require continuous and frequent tuning.

## Specification  
Base vault contract will be created that establishes the following framework for vault instances: 
- Vaults run in rounds, e.g. 1 week or 2 weeks
- Users can deposit for a round prior to the round start  
- All trading that the vault does is permissionless (anyone can call the method to make a trade)  
- A trade can only go through if it meets the generic and specific criteria of the vault itself and if there are enough unutilized funds in the vault  
- All vaults will be diversified to not focus only on a single asset. Exact thresholds are subject to change for specific vaults. Default values ensure that a vault does not expose itself to more than 30% BTC options, 30% ETH options and no more than 10% of any other asset.  
- Vault trades can only be made on markets that mature prior to the end of the round so that the vault PnL in a round can be calculated correctly at the end of the round
- At any time prior to a new round starting, users that have deposited into existing round can signal that they want to leave the vault. If they don't, their funds are reused in the next round.  
- All vaults will have a cap of how much can be deposited into them and a utilization rate variable that controls how much of the funds can be utilized for trading  

All protocol ran vaults will have keeper bots that check if a trade can be made and execute those, but the trading itself is permissionless and can be called by any address.

The product will initially have two vaults:
- Deep in the money vault that buys only options above 80 cents that have 0 or negative skew impact  (discounts)
- Discount chaser vault that only buys options at a discount higher than 2%  

Variables values above are tentative and will be further refined.  

Other vaults that are planned and will be supported in the future:
- Crab vault that buys IN tokens if the asset price is no more than 5% away from the middle of the IN range  
- High volatility markets (buying OUT options when current price is inside the range) 
- Max degen vault (only buying options with a max price of 15 cents and no skew impact)  

More complex and dynamic vault strategies are being considered for future. 
Vaults allow the community to get very creative and there is potential to create a UI where anyone will be able to run their own vault and have users deposit into it.

## Implementation  
https://github.com/thales-markets/contracts/tree/feat/trading-vaults
 
## Copyright
 
Copyright and related rights waived via CC0.
 

