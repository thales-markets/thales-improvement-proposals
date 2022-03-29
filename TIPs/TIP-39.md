| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-39 | Allow Thales pDAO to integrate new assets from Chainlink on their own discretion | Draft | padzank (@padzank)| Allow Thales pDAO to integrate new assets from Chainlink on their own discretion and thus remove overhead of having a separate TIP for each integration. | https://discord.gg/rPpPcMXSeU | 2022-03-29
 
## Simple Summary
 
Allow Thales pDAO to integrate new assets from Chainlink on their own discretion and thus remove overhead of having a separate TIP for each integration.
 
## Abstract
 
With [Chainlink further expanding its offering of data feeds to Optimism L2 network](https://docs.chain.link/docs/optimism-price-feeds/), this TIP proposes to allow the Thales Protocol DAO to be able to integrate new feeds to Thales smart contracts on their own discretion and this way avoid having to vote for each assets individually.
 
## Motivation
 
With streamlining expansion of Thales offerings for Positional Markets for new assets from Chainlink as they come along, Thales has the opportunity to rapidly integrate new assets and deploy markets around those in a safe manner. With the way Thales AMM operates with its security limits, there are no inherent risks whatsoever when introducing new markets around new assets available from Chainlink on Optimism. Riskless increase of flexibility for market creation, Thales Royale organization possibility and a direct impact on driving volume and increase of user base of the Thales protocol due to markets that cannot be found anywhere else in the Defi space.  
   
The Implied Volatility parameter of upcoming assets, that will be used for Thales AMM integration, will be derived from measure of `Historical Volatility` for each asset multiplied by `Implied Volatility / Historical Volatility` ratio of ETH. Historical volatility (HV) is a statistical measure of the dispersion of returns for a given security or market index over a given period of time. Historical volatility period of time to be used in this case is 30 days. Implied Volatility of ETH to be used for reference will be the [Deribit ETH Volatility Index (DVOL)](https://www.deribit.com/statistics/ETH/volatility-index).
 
## Specification
 
This TIP allows the Thales Protocol DAO to integrate Chainlink Optimism data feeds into Thales smart contracts on it's own discretion, and this way enable creation of markets around integrated assets.
 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.