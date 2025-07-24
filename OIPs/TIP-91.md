
| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-91 | Increase Ranged AMM Fee | Implemented | @danthales | Increase Ranged AMM fee from 1% to 3% | https://discord.gg/thales | 2022-09-30

## Simple Summary

This TIP proposes to increase Ranged AMM fee from 1% to 3%

## Motivation  
Ranged AMM started with a very low fee of 1% to promote this unique derivative offering. It's been quite successful volume wise, but the AMM itself is taking a lot of risks, and the 1% fee does not fully cover that, which the PnL is depicting. 
The stats can be seen here https://dune.com/leifu/thales-ranged-market.  
I am proposing increasing the Ranged AMM fee from 1% to 3%.     

## Specification
The way the RangedAMM works is that it is collaterizing both IN and OUT tokens buy purchasing LEFT and RIGHT options from the underlying AMM. In doing so, it also pays all the fees of the underlying AMM and it takes on the risk of paying out users the difference between the collateral value and the probability of an IN token. 
I believe this is still the optimal implementation of the RangedMarkets as it drives most volumes and fees and inherits the skew information from the underlying AMM.  
However, as shown with the data, the 1% fee is not enough to cover the risks the RangedAMM takes on, specially during low volatility markets, with RangedAMM losing close to 50k (50% of the seeded value) to date.  

I am proposing a fee increase from 1% to 3% to better offset for the risk the RangedAMM is taking. The fee is applied to the pricing of IN and OUT tokens.

## Copyright

Copyright and related rights waived via CC0.
