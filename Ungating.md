
| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-145 | Ungating Overtime and Thales AMM | Draft | fhd | Changing AMM usage rules and PnL distribution | [discordlink](https://discord.com/channels/906484044915687464/1112764291347648532) | 2023-05-29

## Simple Summary
Allow anyone to deposit to the Overtime and Thales AMM. 


## Motivation
More LP's will be marketing in itself, and Thales Stakers' LP's will be able to profit from regular users' LP's by earning a static percentage of the overall AMM's PnL.

## Specification
Instead of complicating things with bringing revenue to stakers, which rewards those who don’t even care to LP on Overtime and Thales AMM, I propose to keep all revenue generation within the LP’s. As follows:

**Thales Stakers can LP on Overtime and Thales AMM at 5:1 Ratio** 

- LP’s earn `50%` of profit on all profitable rounds
- LP’s earn the SafeBox Fee
- LP’s take `0%` of the AMM losses

**All Users can LP on Overtime and Thales AMM without staking**

- LP’s earn `50%` of profit on all profitable rounds
- LP’s take on `100%` of the AMM losses

## Rationale
The point is that by gating a certain amount of USD per Thales, the earning power of each Thales increases as the AMM scales. This keeps the power to the Thales Stakers while also allowing users to dip their toes into Overtime. This also means that as the AMM TVL increases, so does the value of each Thales token, and the market will price this accordingly.

Additionally, this method rewards those who stake longer. Compounding APR to those who remain instead of static rewards directly to stakers.

**Most user’s will be happy to take anything over 30% APY, non-inflationary. We can take advantage of this, and should do so sooner rather than later.**

## Test Cases
$1,000,000 USD AMM balance from Thales Stakers

$1,000,000 USD AMM balance from regular users

- Profitable Round, $10,000 profit
    - Thales Stakers LP’s earn $5,000, or `0.5%`, as well as SafeBox Fee
    - Regular users earn $5,000, or `0.5%`
- Losing Round, $5,000 loss
    - Thales Stakers LP’s stay even, and earn SafeBox fee
    - Regular users lose $5,000, or `0.5%`

$1,000,000 USD AMM balance from Thales Stakers

$10,000,000 USD AMM balance from regular users

- Profitable Round, $200,000 profit
    - Thales Stakers LP’s earn $100,000, or `10%`, as well as SafeBox Fee
    - Regular users earn $100,000, or `1%`
- Losing Round, $100,000 profit
    - Thales Staker LP’s stay even, and earn SafeBox fee
    - Regular user’s lose $100,000, or `1%`

## Implementation


## Copyright

Copyright and related rights waived via CC0.
