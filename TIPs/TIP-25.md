| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-25 | Integrate AAVE, EUR, SOL and UNI as available assets on Thales | Draft | padzank (@padzank)| Add AAVE, EUR, SOL and UNI price feeds from Chainlink to Thales on Optimism and enable market creation around those assets price feeds. | https://discord.gg/rPpPcMXSeU | 2022-01-31

## Simple Summary

Add Aave (AAVE), Euro (EUR), Solana (SOL) and Uniswap token (UNI) price feeds from Chainlink to Thales and enable market creation around those assets price feeds on Optimism.

## Abstract

Until recently, only available Chainlink data feeds on Optimism were BTC, ETH, LINK and SNX. With [Chainlink expanding its offering of data feeds to Optimism L2 network](https://docs.chain.link/docs/optimism-price-feeds/), this TIP proposes to integrate AAVE, EUR, SOL and UNI price feeds into PriceFeed.sol contract and thus enable market creation around those assets on the Thales marketplace. With this integration, Thales would effectively double the amount of available assets on Optimism.

## Motivation

With offering Positional Markets for assets such as AAVE, EUR, SOL and UNI, Thales has the opportunity to become one of the firsts protocols to offer decentralized and immutable derivatives product for these assets on a cheap and fast layer 2 network such as Optimism. Most derivative trading products regarding these assets are based on centralised exchanges and are exclusively in form of perpetual futures.

With the recent introduction of the novel Thales AMM contract, users would also have on-demand liquidity of positional tokens for markets created around these new assets. If we consider using Implied Volatility parameter of AAVE, SOL and UNI the same as SNX (120%), frequent short-term term markets can be created. Regarding the Euro (EUR) asset, the Implied Volatility parameter on major centralised trading desks seems to be around 6% and hence make more sense to be utilized for the creation of long term markets around the ratio of EUR/USD.

## Specification

This TIP entails the Thales Protocol DAO to integrate the following Chainlink Optimism data feeds into the [PriceFeed.sol](https://github.com/thales-markets/contracts/blob/main/contracts/PriceFeed/PriceFeed.sol) contract and this way enable creation of markets around these assets:

 - AAVE/USD	(Proxy: 0x338ed6787f463394D24813b297401B9F05a8C9d1)
 - EUR/USD (Proxy: 0x3626369857A10CcC6cc3A6e4f5C2f5984a519F20)
 - SOL/USD (Proxy: 0xC663315f7aF904fbbB0F785c32046dFA03e85270)
 - UNI / USD (Proxy: 0x11429eE838cC01071402f21C219870cbAc0a59A0)

## Rationale

n/a

## Test Cases

n/a

## Implementation

n/a

## Copyright

Copyright and related rights waived via CC0.