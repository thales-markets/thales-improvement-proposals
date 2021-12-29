| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-16 | Utilize Thales NFTs| Draft | Danijel (@dgornjakovic) | Provide utility to NFTs on https://opensea.io/collection/thales-market| https://discord.gg/8bzFdpGTrp | 2021-12-29
 
## Simple Summary
 
With the L2 release and the AMM being the dominant volume driver we can provide some utility to the holders of the NFTs which are part of https://opensea.io/collection/thales-market collection. 
 
## Motivation
Thales NFTs on https://opensea.io/collection/thales-market were drawn by famous illustrator https://en.wikipedia.org/wiki/Dobrosav_%C5%BDivkovi%C4%87 and sponsored by Thales Treasury DAO.  
The NFTs were allocated based on various criterias to early users of Thales protocol.  
Thales was always planning to provide more utility to these NFTs (i.g. the corresponding holders), and this proposal aims to do so as applicable at this point.  
Further utility to more NFTs in that collection would be added via future TIPs. 
 

## Specification
AMM currently applies a `min_impact` modifier (currently at 2%) to the base price it calculates via BlackScholes algorithm. I am proposing to provide discounts on that impact as follows:  
* 30% off to Thales Baby Traders https://opensea.io/assets/0x495f947276749ce646f68ac8c248420045cb7b5e/31703445546616290914096692282728113635967647495258376160375559125425176182874
* 50% off to Thales Traders https://opensea.io/assets/0x495f947276749ce646f68ac8c248420045cb7b5e/31703445546616290914096692282728113635967647495258376160375559118828106416148
* 50% off plus an additional 10% off the skew impact if the option in question has the skew impact applied to it to Thales Pro Traders https://opensea.io/assets/0x495f947276749ce646f68ac8c248420045cb7b5e/31703445546616290914096692282728113635967647495258376160375559124325664555014


## Test Cases
 
## Implementation

## Copyright
 
Copyright and related rights waived via CC0.
