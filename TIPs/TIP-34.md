| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-34 | Integrate ATOM, AVAX, BNB, FLOW, FTM, MATIC, NEAR, ONE and SAND as supported assets on Thales| Draftd | padzank (@padzank)| Add ATOM, AVAX, BNB, FLOW, FTM, NEAR, ONE and SAND price feeds from Chainlink to Thales on Optimism and enable market creation around those assets price feeds. | https://discord.gg/rPpPcMXSeU | 2022-03-14
 
## Simple Summary
 
Add ATOM/USD, AVAX/USD, BNB/USD, FLOW/USD, FTM/USD, MATIC/USD, NEAR/USD, ONE/USD and SAND/USD price feeds from Chainlink to Thales and enable market creation around those assets price feeds on Optimism.
 
## Abstract
 
With [Chainlink further expanding its offering of data feeds to Optimism L2 network](https://docs.chain.link/docs/optimism-price-feeds/), this TIP proposes to integrate AAVE, SOL and UNI price feeds into PriceFeed.sol contract and thus enable market creation around those assets on the Thales marketplace.
 
## Motivation
 
With streamlined expansion of Thales offerings for Positional Markets for assets such as proposed by this TIP, Thales continues to move forward as one of the only decentralized and immutable derivatives products for these assets on a cheap and fast layer 2 network such as Optimism.  
   
With the recent introduction of the novel Thales AMM contract, users would also have on-demand liquidity of positional tokens for markets created around these new assets. Increasing the offering of Thales marketplace with these assets creates more flexibility for market creation, Thales Royale organization and has a direct impact on driving volume and increasing the user base of the Thales protocol.  
  
The Implied Volatility parameter of these assets, that will be used for Thales AMM integration, will be derived from measure of `Historical Volatility` for each asset multiplied by `Implied Volatility / Historical Volatility` ratio of ETH.  
  
  When using this logic, the following Implied Volatility percentages are measured for each price feed:  

- AVAX/USD 88%
- BNB/USD 111% 
- FLOW/USD 85% 
- FTM/USD 140% 
- MATIC/USD 80%
- NEAR/USD 165%
- ONE/USD 120%
- SAND/USD 80%
 
## Specification
 
This TIP entails the Thales Protocol DAO to integrate the following Chainlink Optimism data feeds into Thales smart contracts and this way enable creation of markets around these assets:
 
 - ATOM/USD  (Proxy: [0xEF89db2eA46B4aD4E333466B6A486b809e613F39](https://optimistic.etherscan.io/address/0xEF89db2eA46B4aD4E333466B6A486b809e613F39)) 
 - AVAX/USD  (Proxy: [0x5087Dc69Fd3907a016BD42B38022F7f024140727](https://optimistic.etherscan.io/address/0x5087Dc69Fd3907a016BD42B38022F7f024140727))
 - BNB/USD   (Proxy: [0xD38579f7cBD14c22cF1997575eA8eF7bfe62ca2c](https://optimistic.etherscan.io/address/0xD38579f7cBD14c22cF1997575eA8eF7bfe62ca2c))
 - FLOW/USD  (Proxy: [0x2fF1EB7D0ceC35959F0248E9354c3248c6683D9b](https://optimistic.etherscan.io/address/0x2fF1EB7D0ceC35959F0248E9354c3248c6683D9b))
 - FTM/USD   (Proxy: [0xc19d58652d6BfC6Db6FB3691eDA6Aa7f3379E4E](https://optimistic.etherscan.io/address/0xc19d58652d6BfC6Db6FB3691eDA6Aa7f3379E4E9))
 - MATIC/USD (Proxy: [0x0ded608AFc23724f614B76955bbd9dFe7dDdc82](https://optimistic.etherscan.io/address/0x0ded608AFc23724f614B76955bbd9dFe7dDdc828))
 - NEAR/USD  (Proxy: [0xca6fa4b8CB365C02cd3Ba70544EFffe78f63ac82](https://optimistic.etherscan.io/address/0xca6fa4b8CB365C02cd3Ba70544EFffe78f63ac82))
 - ONE/USD   (Proxy: [0x7CFB4fac1a2FDB1267F8bc17FADc12804AC13CFE](https://optimistic.etherscan.io/address/0x7CFB4fac1a2FDB1267F8bc17FADc12804AC13CFE))
 - SAND/USD  (Proxy: [0xAE33e077a02071E62d342E449Afd9895b016d541](https://optimistic.etherscan.io/address/0xAE33e077a02071E62d342E449Afd9895b016d541))
 
## Rationale
 
n/a
 
## Test Cases
 
n/a
 
## Implementation
 
n/a
 
## Copyright
 
Copyright and related rights waived via CC0.