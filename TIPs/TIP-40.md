| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-40 | Deploy Thales protocol on Polygon Mainnet | Draft | padzank (@padzank) | Deploy and enable the suite of contracts pertaining to Thales protocol on Polygon Mainnet | https://discord.gg/8bzFdpGTrp | 2022-04-07
 
## Simple Summary
 
This TIP proposes to deploy and support Thales protocol on Polygon Mainnet.
 
## Abstract
 
This TIP proposes to deploy and support Thales protocol contracts to Polygon mainnet. Contracts have been tested and working on Polygon Testnet and Thales project is now ready, from a technical standpoint, to support this chain.
This TIP additionally proposes to use **USDC** for this deployment as collateral for Thales Markets on Polygon only, since sUSD still has not established presence on the Polygon network.
 
## Motivation
 
After the deployment of Thales Protocol contracts on Optimism with addition of the new AMM contract, a healthy trading action on the Thales marketplace was finally possible and observed. It was evident that Thales can reach its full potential only on a fast and cheap network. Polygon also fits into that category and another big benefit is that it has a large user base. That fact can also help Thales acquire more users and that way drive more volume, increase exposure and help marketing efforts.  
 
For maximum impact, Thales Core Contributors have been in active communication with the Polygon team about support for this deployment from their side. It was agreed that Thales and Polygon would join forces to sponsor a **Trading Competition** on Polygon with a total prize pool worth ~$60,000 in THALES and MATIC. It will run for 3 weeks and it will have two separate leaderboards: Ranking by Net Profit and Ranking by % Profit. After the trading competition, Polygon and Thales will incentivise 5 seasons of Thales Royale on Polygon mainnet around the price of MATIC.  
 
One more exciting point about the Polygon deployment is that the Thales AMM will be running a newest v0.3 version, explained by [TIP-30](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-30.md). This means that Thales markets will offer liquidity for longer time and for a wider range of Positional Token prices, and will offer much better User Experience.  
 
 
## Specification
 
This TIP entails Thales Protocol DAO to execute the following points:  
 
* Deploy the following contracts from the Positions suite to the Polygon Mainnet:  
 
    * [PositionalMarketFactory.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Positions/PositionalMarketFactory.sol)
    * [PositionalMarketManager.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Positions/PositionalMarketManager.sol)
    * [PositionalMarketData.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Positions/PositionalMarketData.sol)
    * [PositionalMarketMastercopy.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Positions/PositionalMarketMastercopy.sol)
    * [PositionMastercopy.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Positions/PositionMastercopy.sol)
   
* Deploy the Thales PriceFeed proxy that will serve asset prices from Chainlink for resolving markets:
    * [PriceFeed.sol](https://github.com/thales-markets/contracts/blob/main/contracts/PriceFeed/PriceFeed.sol)  
 
* Deploy Thales AMM contract to support out of the box liquidity on Thales markets:
 
    * [ThalesAMM.sol](https://github.com/thales-markets/contracts/blob/ThalesAMM/contracts/AMM/ThalesAMM.sol)
    * [DeciMath.sol](https://github.com/thales-markets/contracts/blob/ThalesAMM/contracts/AMM/DeciMath.sol) (helper contract for Math operations]
 
* Deploy Thales Royale contract with seasons and buy-ins:
 
    * [ThalesRoyale.sol](https://github.com/thales-markets/contracts/blob/ThalesAMM/contracts/ThalesRoyale/ThalesRoyale.sol)
 
* Add support in the thalesmarket.io dapp for Polygon L2 with limit orders backed by 1inch protocol.
    * Include 1inch integration to buy sUSD directly from the dapp
 
 
## Rationale
N/A
 
## Test Cases
N/A
## Implementation
N/A
## Copyright
 
Copyright and related rights waived via CC0.
 

