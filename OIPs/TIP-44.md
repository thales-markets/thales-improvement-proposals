| id     | Title                  | Status | Author  | Description             | Discussions to                | Created    |
| ------ | ---------------------- | ------ | ------- | ----------------------- | ----------------------------- | ---------- |
| TIP-44 | Increase AMM Liquidity | Implemented  | Danijel | Increase cap per market | https://discord.gg/rPpPcMXSeU | 2022-04-29 |

## Simple Summary

This TIP proposes to increase cap per market from 10k to 15k and increase SafeBox fee to 2%

## Abstract

With the AMM v0.3 rolled out we are ready to raise the cap to provide more liquidity at fairer pricing for buyers

## Motivation

AMM v0.3 introduced various improvements to pricing including linear instead of absolute skew impact. This means that if someone were to drain the AMM on one side he would pay only half the impact compared to the previous version. It also improved the pricing so that skew impact is applied to potential winnings rather than the price per position.  
AMM has had a very successful run thus far amassing to 170k profit while initially seeded with 70k sUSD.  
With the extra liquidity AMM can now offer a deeper cap per individual markets which allows for further potential integration for integrators requiring more liquidity.

Given the pricing changes that are now more favourable to buyers, this TIP also proposes to raise the SafeBox fee from 1% to 2%.

## Specification

- Set cap per market to 15k sUSD from 10k sUSD
- Set SafeBox fee to 2% from 1%

## Rationale

n/a

## Test Cases

n/a

## Implementation

n/a

## Copyright

Copyright and related rights waived via CC0.
