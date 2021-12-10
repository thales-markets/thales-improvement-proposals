| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-12 | Deploy Thales protocol on Optimism Mainnet| Draft | Danijel (@dgornjakovic) | Deploy and enable the suite of contracts pertaining to Thales protocol on Optimism Mainnet | https://discord.gg/8bzFdpGTrp | 2021-12-10
 
## Simple Summary
 
This TIP proposes to deploy and support Thales protocol on Optimism Mainnet L2 chain.
 
## Abstract
 
With the rollout of OVM 2.0 Thales has been whitelist to deploy on Optimism Mainnet. Our contracts have been tested and working on OVM and we are now ready from a technical standpoint to support this L2 chain.
 
## Motivation
 
MVP version of Thales was deployed on mainnet to showcase to the community at large what Thales is about. Gas prices on L1 have held Thales back to an extent, but we grew together as a protocol and community, learned some lessons which we have incorporated into the L2 rollout and our now proposing to the council to formally deploy and enable Thales on Optimism Mainnet. 
 
## Specification
 
* Deploy the following contracts from the BinaryOptions suite to the Optimism Mainnet:  
    * BinaryOptionMarketFactory.sol
    * BinaryOptionManager.sol
    * BinaryOptionMarketdata.sol
    * BinaryOptionMarketMastercopy.sol
    * BinaryOptionMarketcopy.sol

* Deploy the Thales PriceFeed proxy that will serve asset prices from Chainlink for resolving markets:
    * PriceFeed.sol

* Deploy Thales AMM contract to support out of the box liquidity on Thales markets:
    * ThalesAMM.sol
    * DeciMath.sol (helper contract for Math operations)

* Deploy Thales Royale contract with seasons and buyins (more details in a dedicated TIP):
    * ThalesRoyale.sol 

* Add support in the thalesmarket.io dapp for Optimism L2 with limit orders backed by 1inch protocol.
    * Include 1inch integration to buy sUSD directly from the dapp
  

## Rationale
 

 
## Test Cases
N/A
## Implementation
N/A 
## Copyright
 
Copyright and related rights waived via CC0.
