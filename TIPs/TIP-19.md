| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-19 | AMM v0.2 | Draft | Danijel (@dgornjakovic) | Capture changes proposed for AMM v0.2  | https://discord.gg/8bzFdpGTrp | 2022-01-01
 
## Simple Summary
This TIP aims to summarize the proposed changes for AMM v0.2
## Abstract
Following up on the epilogue of AMM round 1 we have a number of changes we want to implement for round 2
## Motivation
The AMM managed to support 500k of volume with 70k funding. The overall feedback was overwhelmingly positive, and ultimately the AMM ended up with 21k net profit mostly due to a sudden market drop in last 2 days of trading.  
However, it is noticeable that the AMM needs more way of mitigating its risk. This TIP proposes an introduced for a SafeBox/FeePool where the AMM will send 1% of sUSD value from each trade which would not be re-exposed to risk.  
The said SafeBox is to be reused by other Thales products (e.g. Royale) to capture sUSD as a share from volumes and eventually find its way into the hands of THALES stakers.

The second proposed change is to increase the cap from 5k sUSD per market to 7k per market reusing the profit from round 1 to allow more liquidity.  

The third change is a fix for maximum skew impact when selling to the AMM which at times was more than tha maximum intended 10%. 

## Specification
1. Introduce the concept of SafeBox contract where sUSD that is captured as a percentage of protocol volume is stored with the idea to be distributed to THALES stakers once the captured fees are large enough to offset gas costs to claim them
2. Add a variable SafeBoxImpact with value 1%. The variable is applied to each AMM trade and will effectively send 1% from each trade to the SafeBox address
3. Reduce the min_spread variable from 2% to 1% thus having no change to the price a trader pays after the introduction of SafeBox
4. Increase the cap per market from 5k sUSD to 7k sUSD reusing the profits in the first round to increase available liquidity
5. Fix the logic of applying maximum skew impact on sells which at times had values larger than maximum 10%

## Test Cases
 
## Implementation

## Copyright
 
Copyright and related rights waived via CC0.
