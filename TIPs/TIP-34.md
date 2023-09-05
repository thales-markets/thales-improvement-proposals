| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-170 | Integrate PYUSD as supported assets on Thales| Vote Pending | padzank (@padzank)| Add PYUSD price feeds from Chainlink to Thales on Optimism and enable market creation around those assets price feeds. | https://discord.gg/rPpPcMXSeU | 2022-03-14
 
## Simple Summary
 
Add PYUSD price feeds from Chainlink to Thales and enable market creation around those assets price feeds on Optimism.
 
## Abstract
 
With [Chainlink further expanding its offering of data feeds to Optimism L2 network](https://docs.chain.link/docs/optimism-price-feeds/), this TIP proposes to integrate AAVE, SOL and UNI price feeds into PriceFeed.sol contract and thus enable market creation around those assets on the Thales marketplace.
 
## Motivation
 
With streamlined expansion of Thales offerings for Positional Markets for assets such as proposed by this TIP, Thales continues to move forward as one of the only decentralized and immutable derivatives products for these assets on a cheap and fast layer 2 network such as Optimism.  
   
With the recent introduction of the novel Thales AMM contract, users would also have on-demand liquidity of positional tokens for markets created around these new assets. Increasing the offering of Thales marketplace with these assets creates more flexibility for market creation, Thales Royale organization and has a direct impact on driving volume and increasing the user base of the Thales protocol.  
  
The Implied Volatility parameter of these assets, that will be used for Thales AMM integration, will be derived from measure of `Historical Volatility` for each asset multiplied by `Implied Volatility / Historical Volatility` ratio of ETH. Historical volatility (HV) is a statistical measure of the dispersion of returns for a given security or market index over a given period of time. Historical volatility period of time to be used in this case is 30 days. Implied Volatility of ETH to be used for reference will be the the [Deribit ETH Volatility Index (DVOL)](https://www.deribit.com/statistics/ETH/volatility-index).
  
## Specification
 
n/a 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.
