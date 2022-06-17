| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-61 | Introduce Global Skew Impact per Asset for Thales AMM | Draft | padzank (@padzank) | This TIP proposes to introduce a new global skew impact per asset for the Thales AMM | https://discord.gg/8bzFdpGTrp | 2022-06-17

## Simple Summary

This TIP proposes to introduce a new global skew impact per asset for the Thales AMM to mitigate the AMM disbalance on large single sided market swings.

## Abstract

Current Skew Impact mechanism on the Thales marketplace operates on a per-market basis, which alone does not sufficiently protect the global AMM risk.  
  
This TIP proposes to implement an additional global per-asset Skew Impact mechanism that complements the per-market based Skew Impact. In efforts to further help balance the AMM, this Global per-asset Skew Impact will affect all markets of a specific asset with the same respective premium percentage that is determined by the global difference between UP and DOWN tokens the AMM owns of that specific asset.  

## Motivation

Current Skew Impact mechanism on the Thales marketplace operates on a per-market basis. As there are markets that share the same asset and maturity date, but with a certain amount of difference between Strike Prices, this method of Skew Impact applying does not sufficiently balance the amount of risk the AMM is taking. A trader can spread his position purchases across several markets that have the same asset and maturity date but different strike prices and this way the trader can have minimal skew impact on his overall position on that asset's direction. This effect is especially visible on large market swings such as black swan events. The per-market Skew Impact simply does not sufficiently protect the global AMM risk.  
  
With this proposed implementation of Global Per-Asset Skew Impact, there will be two complementing skew impacts on each markets: the existing per-market skew impact, and the other global per-asset skew impact. Both of them will either add up to each other or negate each other to some extent, depending on if the per-market skew impact is sharing the same direction as the global per-asset skew impact.

## Specification

This TIP entails the Thales Protocol DAO to implement a new Global Per-Asset Skew Impact mechanism to the AMM contract that works with the following parameters:   
    
- Global Per-Asset Skew Impact is proposed to have limits between 0% and 20% for each asset.
  
- Global Per-Asset Skew Impact is to be equal to 0% for any of the respective asset’s positional tokens, if the difference between UP and DOWN tokens that the AMM owns of that asset is equal to 0.  
  
- Global Per-Asset Skew Impact is to be equal to maximum amount of 20% for the respective asset’s positional token type, if the difference between the number of those tokens and its counterparty tokens, that the AMM owns of that asset, is equal or above of **4x of CapPerAsset** limit of that specific asset.

- The percentage of Global Per-Asset Skew Impact lineraly increase from 0% to 20% for a specific asset, following the increase of total difference between UP and DOWN tokens from 0 to number equal to **4x of CapPerAsset** limit of the same respective asset.


## Rationale
N/A
## Test Cases

Let’s take the following AMM Position Distribution as a snapshot for calculating the Global Skew Impact per Asset using the previously proposed parameters.

![4](./images/4.PNG)

 - **AAVE** - AAVE’s getCapPerAsset = 5000. AMM owns 5,000 UP tokens and 0 DOWN tokens. Difference between UP and DOWN tokens owned is 5,000, which is 25% of 20,000. This means that the Global Skew Impact (premium) for DOWN tokens of AAVE markets is 5%.

 - **BTC** - BTC’s  getCapPerAsset = 10,000. AMM owns 9,038 UP tokens and 15,116 DOWN tokens. Difference between UP and DOWN tokens owned  is -6,078, which is 15.19% of 40,000. This means that the Global Skew Impact (premium) for UP tokens of BTC markets is 3.03%.

 - **CRV** - CRV’s getCapPerAsset = 5000. AMM owns 5,250 UP tokens and 1,050 DOWN tokens. Difference between UP and DOWN tokens owned  is 4,200, which is 21% of 50,000. This means that the Global Skew Impact for DOWN tokens of CRV markets is 4.2%.

 - **ETH** - ETH’s  getCapPerAsset = 10,000. AMM owns 38,823 UP tokens and 28,169 DOWN tokens. Difference between UP and DOWN tokens owned  is 10,654, which is 26.6% of 40,000. This means that the Global Skew Impact for DOWN tokens of ETH markets is 5.32%.

 - **OP** - OP’s getCapPerAsset = 5000. AMM owns 6,825 UP tokens and 1,754 DOWN tokens. Difference between UP and DOWN tokens owned  is 5,071, which is 25.3% of 20,000. This means that the Global Skew Impact for DOWN tokens of ETH markets is 5.07%.

 - **PERP** - PERP’s getCapPerAsset = 5000. AMM owns 11,377 UP tokens and 150 DOWN tokens. Difference between UP and DOWN tokens owned  is 11,227, which is 56.1% of 20,000. This means that the Global Skew Impact for DOWN tokens of ETH markets is 11.22%.

 - **SNX** - SNX’s getCapPerAsset = 8000. AMM owns 35,880 UP tokens and 9,559 DOWN tokens. Difference between UP and DOWN tokens owned  is 26,321, which is 82.2% of 32,000. This means that the Global Skew Impact for DOWN tokens of ETH markets is 16.45%.

 - **SOL** - SOL’s getCapPerAsset = 5000. AMM owns 4,778 UP tokens and 700 DOWN tokens. Difference between UP and DOWN tokens owned  is 4,078, which is 20.3% of 20,000. This means that the Global Skew Impact for DOWN tokens of ETH markets is 4.07%.


## Implementation
N/A
## Copyright
Copyright and related rights waived via CC0.
