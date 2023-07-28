| id     | Title                                      | Status | Author               | Description                                    | Discussions to                | Created    |
| ------ | ------------------------------------------ | ------ | -------------------- | ---------------------------------------------- | ----------------------------- | ---------- |
| TIP-99 | Open up Sports AMM for liquidity providing | Implemented  | Danijel (@danThales) | Allow anyone to deploy liquidity to Sports AMM | https://discord.gg/rPpPcMXSeU | 2022-10-17 |

## Abstract

Implement the architecture to allow liquidity providing into the Sports AMM.

## Simple Summary

This TIP proposes to open up Sports AMM for providing liquidity based on the amount of THALES a wallet has staked.

## Motivation

So far the liquidity of the Overtime has been fully seeded from Thales DAO treasury. With Overtime running for more than 6 months and generating more than $5,000,000 of volume, it has huge potential to scale up 10x or 100x, specially with the Parlays and Vaults released on products on top which also serve to somewhat balance the AMM risks.  
The PnL of the Sports AMM after World Cup has shown that with organic volume and sharp oracles, there is a pretty good chance of lucrative earnings for liquidity providers. After some lessons we learned the hard way with experimenting with low liquidity sports and preseasons, we are now focused only on high liquidity sports, and with Oracle changes in TIP-114 putting us in a much better spot to fight frontrunning, I believe the AMM is at a point where it can accept liquidity from anyone who would like to "be the house".

Liquidity providing will be gated to only THALES stakers with the amount one can deposit controled by variables based on the THALES staked amount (more details in specification section).

Besides the architecture of how LPing will work I am also proposing some changes in the fee structure as I believe its of utmost impoortance to ensure LPing is profitable when this is released.

## Specification

Liquidity providing will be based much on the proven concept established through vaults. Much of the architecture is inheritted from TIP-70. Liquidity providing is only enabled for THALES stakers with the amount of sUSD stakers can deposit controlled by a variable `stakedThalesMultiplier`

Liquidity providing will be done in weekly rounds with deposits allowed until a round starts.
The rounds would begin on Tuesday 9am UTC and go on until next Tuesday at the same time.
The times are chosen to capture all weekend action and not have any other games unresolved at the time to round end.

During round 0 users deposit funds into the AMM. Users always deposit for the next round.

Users that have deposited in a round, can choose to exit at the rounds end by signaling a withdrawal during the round and then withdrawing when all round PnL has been calculated.

A single market can only belong to 1 round, which is defined based on the maturity date of the market. When a round ends, the PnL from all markets in a round is summed up, and allocated correctly to all liquidity providers.

Any round after round 1 will have all of the deposits + profits from previous round plus any new deposits at round start.

Sometimes markets are delayed and the start time of a game is changed. If such a change would move the market from one round to another and shift a round start significantly, that market has to be cancelled in the round it previously belonged with all positions refunded, and recreated in a new round.

If there isnt enough liquidity in a certain round, AMM liquidity pool borrows from a special address called `defaultLiquidityProvider`,
and sets it as one of the depositors for that round.
This can only be done if that round hasnt started yet (previous round did not finish).
At the end of the round `defaultLiquidityProvider` always withdraws.

A user can only deposit 1 sUSD per X THALES he stakes. A user can only signal withdrawal if he has at least X THALES per 1 sUSD that he currently has in that round. A user can not unstake while he is providing liquidity. Just like with vaults, all user balance that goes into a round is counted towards gamified staking. 

A difference to vaults is that all rounds are statically predetermined at startDate+(roundNumber x 7days). This is done as we dont want to block users from trading an upcoming markets which are sometimes scheduled and available on Overtime even weeks in advance.

## Changes in fee structure

The min_spread variable has been applied with the same net value for both 2-positional (e.g. NBA) and 3-positional markets (soccer). This makes the spread higher on 3-positional markets, which is actually contrary to what most books have.  
The current setup is as follows:

- min_spread 1% (1c)
- safe_box fee 2%

This means that for soccer Overtime odds add up to (1+0.03) x 1.02 =1.056.  
For NBA this would be (1+0.02) x 1.02 = 1.044

Usually sportbooks have a tighter spread on soccer and 3 positional sports than on e.g. NBA, specially when it comes to handicap and totals markets.
I am proposing that the **min_spread variable should be multiplied by 1.5 when applied to 2 positional sports**, which would be a simple contract change, that ensure the spread on Overtime is the same regardless of the market and sport at this moment. The specific risks are managed in that case by liquidity caps per sport.

I am proposing to further **decrease SafeBox fee from 2% to 1%** on SportsAMM (not on ParlaysAMM) and use that reduction to increase the min_skew value from **1% to 1.33%**.  
Going forward, I believe we need to consider specific spreads per different sports, but as that is a larger contract change, I chose not to include it in this release.

I am also proposing that pDAO can change the value defined in [TIP-127](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-127.md) ad hoc, as we monitor the profit distribution between ParlayAMM and SportsAMM. For the TIP-99 release, we will set it to 0.2%.

## Examples

Users deposit $100k for round 1 and then the round is started
Round 1 starts at 8th of November with $100k. If you provided $1000 your share is 1%.  
Round 2 receives $20k of new deposits.  
Round 1 ends with a total of 110k in the AMM. Your balance is now $1100 entering round 2.  
Total in round 2 at the start is $130k. Your share is 1100\*100/130000 = 0.84615%

During round 2 a trade is made on a market that belongs to round 3 for an amount of $100. The `defaultLiquidityProvider` seeds the $100 and thus becomes a depositor for round 3. Let's assume round 2 had 0 PnL so the whole $130k is carried over. The total deposited into round3 when it starts is $130.1k.

## Variables

pDAO will conduct an iterative controlled release and slowly raise the `maxAllowedDeposit` variable as the need occurs and the product matures. `minDepositAmount` and `maxAllowedUsers` can also be changed by pDAO ad hoc.

`stakedThalesMultiplier` can only be changed via a TIP.

minDepositAmount = 10 sUSD  
maxAllowedUsers = 100  
maxAllowedDeposit = 200k  
stakedThalesMultiplier = 10  
roundLength = 7 days (cant be changes without moving liquidity to a new contract)

## Implementation

https://github.com/thales-markets/contracts/pull/256

## Copyright

Copyright and related rights waived via CC0.
