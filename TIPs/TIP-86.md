| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-86 | Implement contract changes inline with Audit report | Draft | Danijel (@Danijel) | Implement changes to Thales contracts based on report from recent smart contract Audit by Iosiro | https://discord.gg/8bzFdpGTrp | 2022-08-30
 
## Simple Summary
 
Implement changes to Thales contracts based on reports from recent smart contract audit by Iosiro
 
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

- Multi-collateral onboarding peg check:

- Mint/Burn exclusive AMM whitelist:

- Base Price check fix:

- Typo fix on `_updateSpentOnOnMarketOnBuy`:

- Gas optimizations:


## Copyright

Copyright and related rights waived via CC0.