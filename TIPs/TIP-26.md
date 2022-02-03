| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-26 | Integrate CRV as available asset on Thales | Draft | padzank (@padzank)| Add CRV price feed from Chainlink to Thales on Optimism and enable market creation around this assets price feeds. | https://discord.gg/rPpPcMXSeU | 2022-02-03
 
## Simple Summary
 
Add Curve (CRV) price feed from Chainlink to Thales and enable market creation around this asset price feeds on Optimism.
 
## Abstract
 
Recently, Chainlink started implementing new data feeds on Optimism to accompany BTC, ETH, LINK and SNX. With [Chainlinks data feeds list for Optimism L2 network](https://docs.chain.link/docs/optimism-price-feeds/) expanding rapidly, this TIP proposes to additionally integrate CRV price feed via PriceFeed.sol contract and thus enable market creation around this asset on the Thales marketplace.
 
## Motivation
 
 With increasing the offering of Positional Markets to smaller assets compared to BTC and ETH, Thales users will have the luxury to participate in a unique super-diverse trading experience that this space has not seen yet. By integrating CRV price feed and offering positional markets around that asset, users are enabled to hedge their CRV exposure in a unique way, while their spot CRV is used in various integrations that his token is known for.
 
With the recent introduction of the novel Thales AMM contract, users would also have on-demand liquidity of positional tokens for markets created around this new asset. If we consider CRV to have the same Implied Volatility of 120%, as existing medium-sized market capitalization assets (AAVE, SOL, UNI and SNX), this would allow the creation of short-term maturing markets and mid-term maturing markets around the price of CRV.
 
## Specification
 
This TIP entails the Thales Protocol DAO to integrate the following Chainlink Optimism data feed into Thales smart contracts and this way enable creation of markets around this asset:
 
 - CRV/USD (Proxy: 0xbD92C6c284271c227a1e0bF1786F468b539f51D9)
 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.
