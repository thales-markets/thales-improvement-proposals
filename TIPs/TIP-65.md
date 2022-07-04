| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-65 | Market Creation risk management limitations | Draft | padzank (@padzank) | This TIP proposes an implementation for certain risk management limits regarding Market Creation and thus pave the way towards eventual lifting the Market Creation whitelist | https://discord.gg/8bzFdpGTrp | 2022-07-04

## Simple Summary

This TIP proposes implementation of certain risk management limits around Market Creation to combat the risk of too similar markets existing at the same time rendering the par-market risk management mechanisms ineffective.

## Abstract

Currently, Thales AMM trading is done on Positional Markets that are manually created each week by following a Strike Price distribution standard per asset decided by Thales Core Contributors.

As Thales strives to slowly mature towards a fully open and permissionless platform for market creation, this TIP proposes a solution that would enforce certain boundaries around market creation by the contract and thus mitigate potential risks that are entailed to the AMM.  
Those rules are:

- A specific market can only be created if there is no other market around that asset within the same couple of days that has a similar Strike Price. Initial parameters for this limit are proposed to be +-3 days in Maturity Time difference alongside ±(`Implied Volatility * 0.05`)% in Strike Price difference.

- A specific market can only be created with a Maturity Date under 30 days from the time of Market Creation.

## Motivation

When Thales Minimal Viable Product launched in 2021, there was no AMM but only Order book based trading. It was deployed on Ethereum Mainnet and anyone could create a custom Positional Markets. As the main issue with trading on Thales was liquidity (market making), the Thales AMM was subsequently developed and deployed in tandem with the platform's Optimism deployment. The AMM contract provides liquidity to all Positional Markets deployed on Thales, and as such is exposed to risk for each and every market. For this reason of risk management, the market creation function was closed to the public for the initial launch of the AMM. Only Thales CCs were whitelisted to curate new markets and that way keep the risk under management until the AMM matures as a product. **Now that the AMM is slowly maturing and the risk behaviour is more familiar, the Permissionless Market Creation function can potentially again be opened to the public if there are certain safety conditions embedded in the contract.**  
The specific motivation behind limiting the permissionless market creation so to not have markets that are relatively close to each other in strike price and maturity date, is that if you allow duplicate or close-by markets to be created, all of the per-market based safety limitations effectively lose their impact putting the entire AMM collateral at risk.  

## Specification

This TIP entails the Thales Protocol DAO to implement the following safety limits in the contracts for Market Creation:

- A specific Positional Market can only be created if there is no other same asset market with the Maturity Date within +-3 days of the new market's Maturity Date with ±(`Implied Volatility * 0.05`)% in Strike Price difference.
 
- A specific Positional Market can only be created with a Maturity Date under 30 days from the time of Market Creation.
 
This TIP additionally entails the Thales Protocol DAO to remove the Initial Collateral requirements for Market Creation as this is a deprecated requirement from when the market creators were the source of initial liquidity as well.

## Rationale
 
N/A
 
## Test Cases
 
## Implementation
 
N/A
 
## Copyright
 
Copyright and related rights waived via CC0.


