| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-96 | Increase Overtime SafeBox fee to 3% | Draft | padzank (@padzank)| Increase Overtime SafeBox fee to 3%  | https://discord.gg/rPpPcMXSeU | 2022-10-11
 
## Simple Summary
 
This TIP proposes to increase Overtime SafeBox fee from 2% to 3% as to complement the Fee Rebates incentives program currently live for Overtime.
 
## Abstract
 
Currently, SafeBox fee for Overtime Markets is set to 2%. With recent implementation of Fee Rebates program for Overtime Incentives, every trader on Overtime gets Fee Rebates in OP+THALES tokens equal to the amount of fees they generated.  

This TIP proposes to increase SafeBox fee to 3% as to increase SportsAMM liquidity security while not affecting UX as the fees will get rebated to users.

## Motivation
 
With the recent deployments of new leagues, sports and preseason offerings for Overtime Markets, there needs to be additional security to SportAMM's liquidity until these new offerings are tested, optimized and mature. As the fee rebates are deployed and in production, increasing the SafeBox fee to 3% seems like a logical step as it will not affect UX of traders because it also increases their rewards of OP+THALES by the same margin.
 
## Specification
 
This TIP entails the Thales Protocol DAO to increase the SafeBox fee for Overtime Markets to `3%`.

## Variables
 
`_safeBoxImpact` = `30000000000000000`
 
## Implementation
 
 
## Copyright
 
Copyright and related rights waived via CC0.
