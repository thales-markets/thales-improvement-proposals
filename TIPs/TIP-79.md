| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-79 | Deploy Thales protocol on Arbitrum Mainnet | Draft | BigPenny (@RealBigPenny) | Deploy and enable the UP/DOWN/RANGE AMM markets on Arbitrum Mainnet | https://discord.gg/pending | 2022-08-23
 
## Simple Summary
 
This TIP proposes to deploy and support Thales protocol on Arbitrum Mainnet.
 
## Abstract
 
This TIP proposes to deploy and support Thales UP/DOWN/RANGE AMM market contracts to Arbitrum mainnet.
This TIP additionally proposes to pre-approve a the offering of our "multi stablecoin buy-in and exercise"-feature on Arbitrum at a later date, to avoid delaying the launch. Until such a feature has been fully discussed and developed and more importantly until sUSD is available on Arbitrum USDC shall be used for this deployments base collateral.
 
## Motivation

Community discussion has shown two major sentiments within the Thales community:

1. Thales should use every reasonable opportunity to establish istself as a multichain protocol that offers its services to a large as possible audience.

2. Avoid single points of failure and centralization risks by diversifying deployments over multiple chains/layers. 

In the case of Arbitrum in particular it is expected that we find a way to colab with Offchain Labs in some capacity to introduce Thales to Arbitrum and incentivize adoption of our protocol within their ecosystem. The exact nature of a possible collaboration as well as additional incentive programs is still up for discussion and the Thales community is expected to work out the required details in one or more complementary TIPs.

The Thales CCs are asked to determine the optimal paramenters for running the Thales UP/DOWN/RANGE AMM market contracts in a safe manner on Arbitrum, given the specific technical circumstances of the chain/layer. This proposal assumes the current configuration for UP/DOWN/RANGE AMM markets on Optimism, including referral rewards and SafeBox paid in USDC, to be the approved default at the time of deployment. Any relevant changes from that default are subject to normal governance procedures as they would be on Optimism. 

At the point of writing Thales Dev Team has already concluded that the "multi stablecoin buy-in and exercise"-feature is not viable for the initial launch on Arbitrum. However this proposal seeks to pre-approve that feature so it can be added in at a later date without the approval of separate TIP.
 
## Specification
 
The Thales Protocol DAO shall:  

* Deploy all contracts necessary to fascilitate UP/DOWN/RANGE AMM markets on Arbitrum with USDC as their base currency.

* Deploy all contracts necessary to facilitate referrals rewards in USDC on Arbitrum.

* Deploy all contracts necessary to facilitate SafeBox functionality with USDC on Arbitrum.

* Ask the Thales Core Contributors to develop a modified version of the "Buy-in and exercise with USDC, USDT, DAI"-feature as described in TIP-58 and TIP-74, but with USDC being the base currency and Curve Arbitrum being used (https://arbitrum.curve.fi/), for deployment at a later date after launch.

 
## Rationale
N/A
## Test Cases
N/A
## Implementation
N/A
## Copyright
 
Copyright and related rights waived via CC0.
 
