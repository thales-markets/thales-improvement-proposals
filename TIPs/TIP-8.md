

| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-8 | Replacement of Synthetix ExchangeRates data feed with custom PriceFeed contract; Removal of minting fees; Adding implicit allowance to 0x exchanger contract | Approved | padzank (@padzank) | Replacement of Synthetix ExchangeRates data feed with custom PriceFeed contract; Removal of minting fees; Adding implicit allowance to 0x exchanger contract | https://research.thales.io | 2021-11-04

## Simple Summary

This TIP proposes to replace Synthetix ExchangeRates for data feeds with versatile in-house PriceFeed; Remove the 1% minting fees for Market Makers; Add implicit allowance for positional tokens to 0x exchanger contract.

## Abstract

Since the launch of the Thales marketplace, Thales protocol has been using Synthetix ExchangeRates data feeds for market resolutions. This TIP proposes to replace ExchangeRates with an independent PriceFeed contract that would allow Thales to directly tap into any desired Chainlink feed.  

Until now every minter of positional tokens on Thales paid 1% fee towards Thales Fee Pool and the respective market creator. This proposal suggests that this fee should be set to 0% to reduce friction until sufficient volume and liquidity is built up and a new fee structure is devised.  

This TIP also proposes to deploy an implicit approval for the 0x exchange contract that would remove the need to approve the positional tokens on every single market individually and thus assist in gas cost reduction and improve user experience.  

## Motivation

As a project born out of the Synthetix ecosystem, Thales protocol has used Synthetix ExchangeRates data feeds for market resolutions since the MVP launch. This means that Synthetix acted as an intermediary between Thales and Chainlink data feeds and Thales could only use data feeds that Synthetix uses for it’s Synths. To allow Thales protocol to tap into any desired Chainlink data feed for market creation and to avoid the risk of Synthetix deprecating data feeds that Thales is using, there needs to be a direct link to Chainlink without intermediaries. Deploying a custom PriceFeed contract that accomplishes this prior statement would allow Thales to freely integrate any data feed that the Thales governance sees fit as a new asset for market creation.  

Continuing on increasing freedom and lowering friction of the entire platform, this TIP also proposes to remove the 1% minting fees entirely. Until there is sufficient volume and liquidity in the Thales markets, incentivising user onboarding is of the utmost importance.  

In the current form of the Thales marketplace, users need to approve positional tokens for trading on each market separately. As far as user experience is concerned, this gas-intensive flow creates a lot of friction and a disincentive to trade on the Thales marketplace on Layer 1 Ethereum. By allowing for an implicit allowance for positional tokens to 0x exchanger contract, users would only need to sign an approval transaction once and thus avoid the costly frequent approval transactions for each subsequent market.  


## Specification

This proposal entails the Protocol DAO to merge the following commits to Thales smart contracts:

- BinaryOption.sol: 
  - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOption.sol#L35 
  - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOption.sol#L49-L58 
  - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOption.sol#L118-L134


- BinaryOptionMarket.sol:
  - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOptionMarket.sol#L66
  - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOptionMarket.sol#L78
  - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOptionMarket.sol#L272-L280


 - BinaryOptionMarketFactory:
   - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOptionMarketFactory.sol#L43
   - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOptionMarketFactory.sol#L77-L81
   - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOptionMarketFactory.sol#L86
	
 - BinaryOptionMarketManager:
   - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOptionMarketManager.sol#L40
   - https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/BinaryOptions/BinaryOptionMarketManager.sol#L86-L90 
  
This proposal also entails the Protocol DAO to deploy the following PriceFeed.sol smart contract:
- https://github.com/thales-markets/contracts/blob/b5e6f6f1681115cb73e427b4d2f7ca4249a85fbf/contracts/PriceFeed/PriceFeed.sol

And also entails that the Protocol DAO deploys the following commit that removes all logic regarding minting fees:
 - https://github.com/thales-markets/contracts/pull/14/commits/3feb2d7016b0ad7f275498797fb2dece7376256f


  
## Rationale

n/a

## Test Cases

n/a

## Implementation

n/a

## Copyright

Copyright and related rights waived via CC0.
