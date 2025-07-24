## Simple Summary

Add the Tether (USDT) price feed from Chainlink to Thales and enable USDT market creation. 

## Abstract

The list of supported assets by Thales dapp is currently lacking a stablecoin for a binary market to be created around it.

Adding a [USDT price feed](https://data.chain.link/ethereum/mainnet/stablecoins/usdt-usd) from Chainlink to the list of supported assets on Thales will enable users to create, trade, and exercise USDT markets, expanding the platform's current possibilities.

## Motivation

Integrating the Chainlink USDT price feed to Thales will effectively allow users to trade against each other, given Thales p2p nature, manifesting their convictions related to Tether USD and the stability of it’s peg.

Tether is [ranked #1 stablecoin](https://www.coingecko.com/en/stablecoins) in regards to market capitalization and trading volume. It is also a popular topic in the cryptocurrency space for its multi-year regulatory uncertainty.

This kind of environment provides Thales with an opportunity to attract users that would like to:

* Express their beliefs regarding a possible USDT collapse
* Hedge their USDT exposure.

Currently there are a few ways for people to actively short USDT:

* Using a centralised exchange (Examples: [USDTHEDGE 1X](https://ftx.com/intl/tokens/USDTHEDGE) and [USDTBEAR 3x](https://ftx.com/tokens/USDTBEAR), both on FTX)
* Using Defi lending protocols to borrow USDT

Shorting USDT on a centralized exchange involves trusting a centralized 
entity on functioning properly in case of a USDT black swan event. Many users avoid this solution since it includes a non-trivial amount of trust on historically unreliable services (especially during violent black swan events), and borrow rates are often abnormally high (10% - 20% APR).

Using a Defi lending protocol involves actively managing your debt position and locking a large amount of funds in form of collateral compared to potential payout in case of a USDT collapse. Additionally, there are several additional risks, involving a lending protocol, in case of USDT collapse:
* Possibility that a large black swan event, such as Tether USD collapse, can render a lending protocol insolvent
* Violent price changes can trigger an unwarranted liquidation of your collateral
* Abnormally high increase of variable borrow rate

Thales can potentially provide a novel on-chain, permissionless and non-custodial mechanism for speculating on the USDT ability to keep its peg and offer unique benefits and competitive returns on both sides of the market, compared to other solutions.

## Specification

This new USDT price feed will be used as other price feeds and requires no new smart contracts to be developed.

The proposal also entails requesting the Thales protocol DAO to create a USDT market with the following parameters:

* **Duration of 6 months until expiry** - Half yearly basis should provide a solid balance between turnover and amount of time for which the funds are locked. 

* **Strike price of 0.95** - Rationale behind the choice of 0.95 strike price is that under normal circumstances, Tether USD never drifts from the price of 1$ for more than a few basis points and any move above few percentages, that is not getting arbed, can be considered a start of a black swan event.

After each expiry, the markets are to be renewed for another period of 6 months. 


## Rationale

n/a

## Test Cases

n/a

## Implementation

n/a

## Copyright

Copyright and related rights waived via CC0.