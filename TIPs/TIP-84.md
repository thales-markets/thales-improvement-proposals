| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-84 | Pause trading contracts on Optimism during ETH 2.0 Merge | Draft | padzank (@padzank) | Pause ThalesAMM, RangedAMM and SportsAMM contracts 1h before Synthetix contracts pause on the day of ETH2.0 Merge and unpause after Synthetix unpauses contracts | https://discord.gg/8bzFdpGTrp | 2022-09-02
 
## Simple Summary
 
This TIP proposes to pause [ThalesAMM](https://optimistic.etherscan.io/address/0x5ae7454827D83526261F3871C1029792644Ef1B1), [RangedAMM](https://optimistic.etherscan.io/address/0x2d356b114cbCA8DEFf2d8783EAc2a5A5324fE1dF) and [SportsAMM](https://optimistic.etherscan.io/address/0x170a5714112daEfF20E798B6e92e25B86Ea603C1) contracts on the day of ETH2.0 Merge on timing that coincides with 1h prior to Synthetix System Wide Suspension ([SIP-271](https://sips.synthetix.io/sips/sip-271/)) and subsequently unpause them when Synthetix contracts resume activities.
 
 ## Abstract
 
Ethereum Merge event is planned on timing when Total Terminal Difficulty (TTD) crosses `58750000000000000000000` while Synthetix will pause their contracts activity approx. 3h earlier on `58740000000000000000000` TTD cross.  
 
Since Thales uses Synthetix' sUSD as main collateral and it is generally safe practice to pause all activities during the Merge, this TIP proposes that Thales Protocol DAO pauses all the relevant trading contracts on Optimism approximately 1h before Synthetix and resume operations subsequently when Synthetix resumes it's own operations post-merge.  
 
**The previous information entails the approximate timing of Thales pause to be 4h prior to the Merge estimation that can be found [here](https://wenmerge.com/).**
 
## Motivation
 
As Ethereum Merge is scheduled to be executed on September 15th 2022, there is no way of knowing how the key infrastructure that Thales relies upon will act during this transition time. Key dependencies for Thales are sUSD stablecoin and Chainlink on-chain data feeds. To not be affected by Synthetix System Wide Suspension, to avoid the risk of abnormal oracle data inputs during the transition to the new Ethereum network and to avoid the risk of all possible unforeseen issues, the timing of the pause of contracts on Optimism is chosen as 1h before Synthetix.
 
## Specification
 
This TIP entails the Thales Protocol DAO to pause the following contracts on Optimism 1h before [Synthetix System Wide Suspension](https://sips.synthetix.io/sips/sip-271/) or ~4h before the [planned timing of the Merge](https://wenmerge.com/):
 
- [ThalesAMM](https://optimistic.etherscan.io/address/0x5ae7454827D83526261F3871C1029792644Ef1B1)
- [RangedAMM](https://optimistic.etherscan.io/address/0x2d356b114cbCA8DEFf2d8783EAc2a5A5324fE1dF)
- [SportsAMM](https://optimistic.etherscan.io/address/0x170a5714112daEfF20E798B6e92e25B86Ea603C1)
 
## Copyright
 
Copyright and related rights waived via CC0.