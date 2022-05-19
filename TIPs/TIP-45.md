| id     | Title                  | Status | Author  | Description             | Discussions to                | Created    |
| ------ | ---------------------- | ------ | ------- | ----------------------- | ----------------------------- | ---------- |
| TIP-45 | Ranged Markets | Draft  | Danijel | Introduce Ranged Markets and RangedMarketsAMM | https://discord.gg/rPpPcMXSeU | 2022-04-29 |

## Simple Summary

This TIP proposes to add Ranged Markets and a corresponding AMM to Thales protocol offering

## Abstract

Thales now offers an AMM for UP and DOWN positions per single market. A lot of traders love playing the Iron Condor or Reverse Iron Condor strategies, which effectively means taking 2 markets from the current AMM which have the same asset and maturity date but different strike prices (e.g. ETH 3200 and ETH 3400) and taking a position whether ETH will finish IN that range or OUT of that range.  
We created a framework that tokenizes and offers an algorithmic pricing for such positions and are proposing to add it to the protocol.

## Motivation

Having tokenized IN and OUT positions and an AMM that offers fair pricing of those will attract more traders and improve the UX for existing traders leveraging Iron Condor or Reverse Iron Condor strategies.  
The implementation of the new Ranged AMM will leverage existing Positional Markets and the existing AMM to collaterize IN and OUT positions with the UP or DOWN tokens of the left and right positional markets per specification.  
Implementing it in such a manner where a trade into a IN position basically trades also with the underlaying Thales AMM means much more potential volume and SafeBox fees for the protocol.  

## Specification

A Ranged Market is created by passing an existing Positional left and right market to it. The ranged market AMM will check that the following is met:  
- Left market and Right market have the same asset (e.g. ETH)
- Left market and Right market have the same maturity date (same timestamp)
- Left market's strike price is lower than the one of the right market by at least 5% (too close of a range would yield odds unsupported by the AMM)
- A Ranged market with the same Left and Right positional market is not already created

Lets take an example of 4 Positional markets on the same date:
- ETH>3000  
- ETH>3200  
- ETH>3400  
- ETH>3600  

A keeper bot will iterate through available markets and look for opportunities to create ranged markets. As a result out of the 4 available positional markets we will have 6 ranged markets:  
- 3000<ETH<3200
- 3000<ETH<3400
- 3000<ETH<3600
- 3200<ETH<3400
- 3200<ETH<3600
- 3400<ETH<3600  


It's easy to declare that the number of potential ranged markets is equal to the number of combinations that meet the rules from the available positional markets.  

The Ranged AMM will offer IN and OUT positions.
It will collaterize each IN position with 0.5 UP position of left market and 0.5 DOWN position of the right market.  
It will collaterize each OUT position with 1 DOWN position of the left market and 1 UP position of the right market.  

By tapping into the existing Thales AMM, the Ranged AMM doesn't need to be seeded with as much liquidity to offer a decent amount of volume per market.  
For OUT positions the AMM will offer the amount of tokens supported by underlaying AMM, i.e. the lower of the two numbers:  
- availableToBuy DOWN on left market  
- availableToBuy UP on right market  

For IN positions the AMM will offer double the amount of tokens supported by underlaying AMM, i.e. the lower of the two numbers:  
- 2 x availableToBuy UP on left market  
- 2 x availableToBuy DOWN on right market  
However, when offering the IN tokens the RangedAMM actually takes a risk, as it will offer an algorithmic price to the buyer, thus the final amount of IN positions offered will be the minimum of available on RangedMarket AMM per cap per market and available on the underlaying AMM.  


When offering OUT tokens, the AMM calculates the price by summing up the price of DOWN position on left market and UP position on right market.  
When offering IN tokens, the AMM calculates the price by subtracting the odds of the opposite, i.g. the OUT token from 1.

Ranged AMM doesnt introduce a concept such as skew impact, instead it relies on the pricing of the underlaying Thales AMM.

## Variables

**capPerMarket = 5000 sUSD** - maximum risk the ranged AMM can take per market </br>
**minSupportedPrice = 10c** - minimum odds to support </br>
**maxSupportedPrice = 90c** - maximum odds to support </br>
**safeBoxImpact = 1%** - Safe Box fee applied to each IN trade </br>
**rangedAMMFee = 1%** - a fee applied for liquidity providers to to rangedAMM </br>  

Note: SafeBox impact will not be applied to OUT trades as ranged AMM has no additional risk, but rather just composes the two underlying positions into an ERC20 token

## Test Cases

n/a

## Implementation

https://github.com/thales-markets/contracts/tree/ranged_markets_amm/contracts/RangedMarkets

## Copyright

Copyright and related rights waived via CC0.
