| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-74 | Implement seamless swaps from sUSD to USDC, USDT and DAI | Vote Pending | BigPenny (@RealBigPenny) | Deploy and enable an implementation that allows Thales traders to directly exercise "in the money" options with USDC, USDT and DAI when using the Thales AMM | https://discord.gg/coming_soon | 2022-08-05
 
## Simple Summary
 
This TIP proposes to deploy and enable an implementation that allows Thales traders to directly exercise "in the money" options with USDC, USDT and DAI when using the Thales AMM

## Abstract
 
Allowing Thales traders to retrieve other types of stablecoins when excercising "in the money" options is the logical next step due to the fact that the largest buy transactions on the AMM are done with USDC and USDT. Allowing people to directly exercise options in their preferred stablecoin will is necessary to provide a holistic positive UX for users that have no sUSD exposure.  
 
This TIP proposes to introduce an implementation that allows Thales traders to directly withdraw profits from the Thales AMM in USDC, USDT or DAI by **transparently swapping sUSD to the preffered stablecoin in one transaction**. Traders will be able to excercise their options on Thales markets, while the contract will swap sUSD to USDC, USDT or DAI in the background using the sUSD+3CRV Curve pool before sending the funds to the users wallet.
 
## Motivation
 
Since TIP-58 was implemented many of the largest buy transactions on the Thales AMM were done with USDC and USDT. This is a strong indicator that users with large stablecoin holdings prefer to trade on Thales directly with their dollar coin denomination of choice. For a holstically positive user experience it is necessary to allow those players to excerise their options in their preffered stablecoin denomination as well. This will make the fact that Thales is using sUSD as its base currency nearly irrelevant to most users, especially on short term markets.
 
This proposal does not address users who don't want any sUSD exposure at all, while they are holding a position. A solution with majority appeal that accomodates players of that type has yet to be found. However this proposal addresses the vast majority of Thales users needs in regards to stablecoin choice and as such is a good and important addition to the Thales user experience and the logical advancement from TIP-58 

 
## Specification
 
This TIP entails the Thales Protocol DAO to implement a new method to the [AMM contract](https://optimistic.etherscan.io/address/0x5ae7454827D83526261F3871C1029792644Ef1B1) that, when called, triggers the AMM contract to interacts with the [sUSD+3CRV](https://optimism.curve.fi/factory/0) pool on Curve on Optimism and swap sUSD to the users stablecoin of choice after executing their options in the same transaction.  

A small mouse over tooltip shall be added to the UI which informs the user that exercising their options in any other stablecoin than sUSD could lead to them receiving slightly more or less than 1 dollar coin denomination per option due to sUSD being swapped to their stablecoin of choice. 
 
## Rationale
N/A
## Test Cases
N/A
## Implementation
N/A
## Copyright
Copyright and related rights waived via CC0.
