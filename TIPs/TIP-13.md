| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-13 | Thales Royale mainnet rollout| Draft | Danijel (@dgornjakovic) | Deploy and support Thales Royale as a recurring event on Optimism Mainnet | https://discord.gg/8bzFdpGTrp | 2021-12-10
 
## Simple Summary
 
This TIP proposes to include Thales Royale as part of Thales protocol offering. 
 
## Abstract
 
Thales Royale started off as an experiment to gamify Thales Binary Options experience. Testnet competition was well liked and praised by the community so this TIP proposes to add it as part of the Thales protocol on L2 mainnet.
 
## Motivation
 
As a young protocol in DeFi Thales MVP served to showcase the vision of the protocol and the tehnical capabilities of the core team. Thales started as a Binary Options spin-off seeded by Synthetix, but its now scalling as protocol focused on Parimutuel markets.
In parimutuel markets users place their buy-ins in a pot which winners get to split.
Thales Royale was motivated by Battle Royale games and Squid game show so it consist of several rounds of speculating on a movement of a certain asset. Players who guess the movement correctly make it to the next round. 
Players that make it past the last round get to split the pot.  

Thales Royale format can be used also to speculate on Sport events or other outcomes per round once sport feeds become available on Optimism Mainnet from Chainlink.
 
## Specification
 
Thales Royale will be initially rolled out as it was in the testnet, but with a buyin. It will be incentivisized from the treasury early on.  
Proposed format:
* Royales start on Monday, 3 days signups then 6 daily rounds
* Next royale on Monday 2 weeks away
* First 6 Royales are boosted with 1000 sUSD from the treasury
* Buyin set to 20 sUSD  
* Positioning 8h, total round length 24h
* If there is only a single person alive after a certain round, he is declared winner
* If everyone has been eliminated after a single round, they are all declared winners
* Winners split the pot and can claim sUSD directly from the contract
* Thales Royale is now a seasonal event and users can navigate through past seasons. By default the current season is presented.


## Test Cases
 
 
## Implementation
 
https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyale.sol
 
## Copyright
 
Copyright and related rights waived via CC0.
