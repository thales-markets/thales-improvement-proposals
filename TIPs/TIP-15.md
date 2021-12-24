| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-15 | Adapt AMM parameter| Draft | Danijel (@dgornjakovic) | Adapt Thales AMM maximum skew impact | https://discord.gg/8bzFdpGTrp | 2021-12-16
 
## Simple Summary
 
Given the very imbalanced demand for LONG options on Thales market this TIP proposes to increase the maximum skew impact from 5% to 10% 
 
## Abstract
 
-
 
## Motivation
 
Current AMM skew is 90-10 LONG dominated.  
The maximum skew impact is set to 5% at the moment, but even with that the LONG options are more popular than SHORT options which are being offered without a skew impact.  
To reduce some of the AMM exposure this TIP proposes to have the maximum skew impact set to 10%.    

Skew impact is determined by the AMM skew on a certain market. If half of the LONG options from the total number of LONG options AMM can offer on a certain market are being bought, but there are 0 SHORT options bough, the skew impact will be maxSkewImpact/2.

## Specification
 


## Test Cases
 
## Implementation

## Copyright
 
Copyright and related rights waived via CC0.
