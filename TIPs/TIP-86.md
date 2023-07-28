| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-86 | Implement contract changes inline with Audit report | Implemented | Danijel (@Danijel) | Implement changes to Thales contracts based on report from recent smart contract Audit by Iosiro | https://discord.gg/8bzFdpGTrp | 2022-08-30
 
## Simple Summary
 
Implement changes to Thales contracts based on reports from recent smart contract audit by Iosiro https://iosiro.com/audits/thales-amm-smart-contract-audit
 
 ## Abstract

In light of recent audit of Thales Protocol smart contracts by Iosiro, this TIP proposes to implement the following changes to Thales smart contracts:
  
- Forbid USDC, USDT or DAI background swap for multi collateral onboarding if the peg is deviated from `1` by amount larger than set variable (initial deviation threshold variable to be set at `2%`)
- Disable minting and burning unless the function caller is the AMM contract
- Fix base price check against `minSupportedPrice` and `maxSupportedPrice` values
- Fix typo on `_updateSpentOnOnMarketOnBuy`
- Various Gas optimizations

## Motivation

Reports from a recent audit of Thales smart contract by Iosiro were promising, without any critical vulnerabilities or design flaws discovered on Thales novel architecture. The issues that were uncovered were of a low severity. With this new formal smart contracts audit, the Thales brand increased its credibility in the space and its end users will feel more comfortable when using the Thales products.

## Specification

This TIP entials the Thales ProtocolDAO to implement the following Smart Contract changes:

- Multi-collateral onboarding peg check

- Mint/Burn exclusive AMM whitelist

- Base Price check fix

- Typo fix on `_updateSpentOnOnMarketOnBuy`

- Various gas optimizations listed below  


### Gas Optimizations
During feasibility testing of BSC deployment it has come to attention that our gas costs are very unfavourable for an environment that charges L2 gas pro rata (optimism transactions are mostly a variable of L1 gas).  
We have thus analyzed and implemented various improvements for gas costs:  
- Refactor methods so that BlackScholes is never called twice within a single atomic transaction
- Instead of DeciMath library use PRB math library. This requires an upgrade to solidity v0.8 which will be used for Arbitrum and BSC, and at a later point will be rolled out to Optimism (as it requires migrating contracts)
- In ranged markets, don't use quotes to verify slippage but returned values of buy and sell from underlying AMMs 
- Multiple other refactorings that terminate methods as soon as possible if conditions are not met and simplify the used math
  
## Source code
https://github.com/thales-markets/contracts/tree/iosiro-amm-audit

## Copyright

Copyright and related rights waived via CC0.
