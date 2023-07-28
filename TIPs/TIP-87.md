| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-87 | Increase SafeBox fee of ThalesAMM.sol contract by +1% | Implemented | padzank (@padzank) | Increase SafeBox fee of ThalesAMM.sol contract by +1% | https://discord.gg/8bzFdpGTrp | 2022-09-07
 
## Simple Summary
 
Increase the SafeBox fee percentage from trades that go through ThalesAMM.sol contract by `+1%` and additionally increase `IN` token trades fee by `+1%`

## Abstract

As it does not effect UX to a large extent, but it significantly increases the SafeBox contract accrual, this TIP proposes to increase SafeBox fee percentage for Thales AMM trades by `+1%` to a total of `3%`, and subsequently increase the `IN` token trading fee by `+1%` to follow the mentioined increase.

## Motivation

Current SafeBox fee percentage is 2% of every executed trade on the Thales Marketplace. Since the launch of OP Trading Incentives, significant increase in Volume was observed which also exponentially increased the influx in SafeBox contract. With this increase in Volume, comes opportunity to gather increase in data and tweak the AMM parameters more efficiently to create more balance. Increasing the SafeBox fee seems like a rational move that will increase the security of the AMM by increasing the funds in the SafeBox contract. Since the nature of trading on Thales is probability based with fluid and volatile probabilities and subsequently pricings of Positional Tokens, by increasing the trading fees above the accustomed industry standard, the UX does not suffer as much but the accrual to SafeBox increases exponentially.

## Specification

This TIP entails the Thales Protocol DAO to increase the SafeBox fee for the ThalesAMM.sol contract from `2%` to **`3%`**.

## Copyright

Copyright and related rights waived via CC0.