| id     | Title                  | Status | Author  | Description             | Discussions to                | Created    |
| ------ | ---------------------- | ------ | ------- | ----------------------- | ----------------------------- | ---------- |
| TIP-46 | AMM - cap per asset | Draft  | Danijel | Introduce Cap per asset for AMM and other param changes | https://discord.gg/rPpPcMXSeU | 2022-05-09 |

## Simple Summary

This TIP proposes to introduce cap per asset into AMM, change the way min_spread variable is applied and revert to 10-90 and 24h rules for AMM trading.  
This TIP also proposes to allow whitelisted addresses to configure Implied Volatility of assets to allow for more dynamic reconfiguration of IV as needed.

## Motivation

Thales AMM made a significant profit (~150k sUSD) at the time releasing v0.3, so CCs and governance felt more comfortable experiment and opening up AMM for trading up to 8h till maturity and with 5-95 delta cut off. Protocol DAO also added more assets to keep things interesting on both Optimism and Polygon.  
AMM observed some losses last few weeks, and while some of those were just organic trading, AMM was hurt on volatile assets such as APE and CVX.  

I propose to introduce a variable cap_per_asset where we can control the cap on specific asset and continue having high liquidity for assets such as BTC and ETH, but also continue supporting exotic assets such as APE, but at lower cap.    

AMM v0.3. introduced an improvement to how the skew impact is applied so that its applied to the potential winnings of a trade rather that the position cost. This, however, made deep in-the-money positions quite cheap with min_spread variable having almost no impact the closer to 100c price the positions are.  
I propose to apply the min_spread variable as it was originally intended which is to add 2c to the algorithmic pricing in any case and then apply skew impact if any as proposed in v0.3.

I further propose to revert AMM rules to 24h and 90-10 in preparation for ranged markets release. 
Trading AMM positions that close to maturity results in leveraged pricing changes as the price of the underlying asset changes and unfortunately is prone to frontrunning.  

This TIP also proposes an addition of whitelisted addresses concept into the AMM. The whitelisted addresses, which would be hardware wallets owned by CCs, can update the IV (implied volatility) per asset.  
Right now this can only be done by protocol DAO, but with the growing number of assets and the need to keep IVs up to date, this will allow us to stay on top of IV configuration.  
The whitelisted addresses have to checked off with Thales Council.
## Specification
- Introduce capPerAsset variable and use it in place of capPerMarket  
- Fallback to capPerMarket for assets which dont have an explicit cap set    
- Revert AMM trading rules to 24h and 90-10  
- Apply min_spread as absolute pricing change of 2c to algorithmic pricing  
- Add the concept of whitelisted addresses into the AMM which can configure IV per asset

Individual cap per asset is to be managed at Protocol DAO discretion, but an example it could be something like:
Cap per asset:  
- Tier 1 = 15k BTC, ETH
- Tier 2 = 7.5k SNX, LINK, MATIC...
- Tier 3 = 5k APE, OHM ...


## Variables  
capPerAsset

## Test Cases

n/a

## Implementation

https://github.com/thales-markets/contracts/tree/cap_per_asset

## Copyright

Copyright and related rights waived via CC0.
