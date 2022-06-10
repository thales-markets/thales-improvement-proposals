| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-58 | Implement seemless swaps from USDC, USDT and DAI to sUSD in the Thales AMM contract | Draft | padzank (@padzank) | Deploy and enable an implementation that allows Thales traders to directly trade with USDC, USDT and DAI when using the Thales AMM | https://discord.gg/8bzFdpGTrp | 2022-06-10
 
## Simple Summary
 
This TIP proposes to deploy and enable an implementation that allows Thales traders to directly trade with USDC, USDT and DAI on the Thales AMM

## Abstract
 
Allowing Thales traders to also use other types of stablecoins when trading with the AMM, was frequently proposed as a solution that would increase UX and onboarding for many new traders that have no sUSD exposure.  
 
This TIP proposes to introduce an implementation that allows Thales traders to directly trade with the Thales AMM with USDC, USDT or DAI as well by **seamlessly swapping them to sUSD in the same transaction**. Traders will be able to position on Thales markets with these stablecoins, while the contract will swap to sUSD in the background using the sUSD+3CRV Curve pool before executing the trade. First iteration of this solution will allow only **purchases** of Positional Tokens, while Exercising and Selling will be supported on the next iteration of this implementation.
 
## Motivation
 
Thales protocol's choice of sUSD as the main form of collateral was decided for many beneficial reasons. It is a robust, overcollateralized and censorship resistant stablecoin that directly benefits the robustness of Thales protocol itself. The alignment with the Synthetix ecosystem is also a factor where Thales is doing its part in pushing for a wider sUSD adoption and demand. Also, sUSD is one of the most liquid stablecoins on the Optimism network, the network where Thales made its home.  
 
This specific solution that allows trading on Thales additionally using USDT, USDC and DAI next to sUSD, perfectly balances between capturing a wider range of new users that perhaps don't have exposure to sUSD and additionally supporting the demand and adoption of sUSD. The proposed solution involves that every trade done with USDT, USDC or DAI in the Thales Marketplace, is seamlessly swapped to sUSD in the background first using Curve before executing the trade on the contract side. Thales contracts keep zero exposure to these centralized stablecoins while the end users have an exponentially better UX. If a interested trader does not have sUSD but wants to take a position on some Thales market, he no longer has to do additional steps of manually swapping to sUSD, the Thales contracts do it on his behalf while the experience stays the same as if USDC, USDT and DAI are supported collateral types.  
 
This implementation can be a significant step towards inviting more trading volume, increasing user retention and overall boosting a wider adoption of the Thales AMM.
 
 
## Specification
 
This TIP entails the Thales Protocol DAO to implement a new method to the [AMM contract](https://optimistic.etherscan.io/address/0x5ae7454827D83526261F3871C1029792644Ef1B1) that, when called, triggers the AMM contract to interacts with the [sUSD+3CRV](https://optimism.curve.fi/factory/0) pool on Curve on Optimism and swap the users stablecoin of choice to sUSD before executing the trade in the same transaction.  

- Branch with the deployed implementation: https://github.com/thales-markets/contracts/tree/curve-onramp
 
## Rationale
N/A
## Test Cases
N/A
## Implementation
N/A
## Copyright
Copyright and related rights waived via CC0.