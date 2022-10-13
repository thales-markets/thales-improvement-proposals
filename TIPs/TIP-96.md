| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-96 | Increase Fee Rebates emissions for Overtime  | Draft | padzank (@padzank)| Increase Fee Rebates emissions for Overtime by setting Overtime SafeBox fee to 3%  | https://discord.gg/rPpPcMXSeU | 2022-10-11
 
## Simple Summary
 
This TIP proposes to increase Fee Rebates emissions for Overtime by setting the Overtime SafeBox fee from 2% to 3% and thus additionally support the SportsAMM collateral security without affecting the user experience.
 
## Abstract
 
 Currently, SafeBox fee for Overtime Markets is set to 2%. As there is additional room until the rebates get closer to the hard cap of 8,000 OP + 8,000 THALES per round, this TIP proposes to increase the SafeBox fee to 3% and increase security of the SportsAMM while the user experience will remain the same as the Fee Rebate rewards will also increase proportionally. 

## Motivation
 
Previous weeks of Fee Rebates program of Overtime saw the rewards per round reach not more than 60% of hard capped 8,000 OP + 8,000 THALES reserved for rebates. With the recent deployments of new leagues, sports and preseason offerings for Overtime Markets, there needs to be additional security to SportAMM's liquidity until these new offerings are tested, optimized and mature. As the fee rebates are deployed and in production, increasing the SafeBox fee to 3% seems like a logical step as it will not affect UX of traders because it also increases their rewards of OP+THALES by the same margin.
 
## Specification
 
This TIP entails the Thales Protocol DAO to increase the SafeBox fee for Overtime Markets to `3%`.

## Variables
 
`_safeBoxImpact` = `30000000000000000`
 
## Implementation
 
 
## Copyright
 
Copyright and related rights waived via CC0.
