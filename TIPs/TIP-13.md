| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-13 | Thales Royale mainnet rollout| Draft | Danijel (@dgornjakovic) | Deploy and support Thales Royale as a recurring event on Optimism Mainnet | https://discord.gg/8bzFdpGTrp | 2021-12-10
 
## Simple Summary
 
This TIP proposes to formalize inclusion of Thales Royale as part of Thales protocol offering. 
 
## Abstract
 
Thales Royale started off as an experiment to gamify Thales Binary Options experience. Testnet competition was well liked and praised by the community so this TIP proposes to add it as part of the Thales protocol main offering on Optimism L2 mainnet.
 
## Motivation
 
As an early stage protocol in DeFi, Thales MVP served to showcase the vision of the protocol and the tehnical capabilities of the core team. Thales started as a Binary Options spin-off seeded by Synthetix, but its now scalling as a protocol focused on Parimutuel markets.
In parimutuel markets users place their buy-ins in a pot which winners get to split.
Thales Royale was motivated by Battle Royale games and the popular "Squid Game" TV show so it consist of several rounds of speculating on a movement of a certain asset. Players who guess the movement correctly make it to the next round. 
Players that make it past the last round get to split the pot. 

Thales Royale format can also be used to speculate on Sport events or other outcomes per round once sport feeds become available on Optimism Mainnet from Chainlink.
 
## Specification
 
This TIP entails Thales Protocol DAO to support [Thales Royale contract](https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyale.sol) deployment on Optimism Mainnet. Thales Royale will initially be rolled out in the same form as in the first testnet competition, but with added functionality of a buy-in. Subsequent L2 mainnet Royales are to be incentivisized from the treasury early on.  

Proposed format:  

* The first 6 Thales Royale Events will be boosted with 1000 sUSD from the Thales Treasury.
* Each Thales Royale will be played by speculating the price of ETH.
* Each Thales Royale Event starts on a Monday, 16:00 UTC time on a biweekly basis (clarification: the next Thales Royale Event starts two weeks after the previous one).
* Sign-up phase of each Royale to last for 3 days.
* After Sign-up phase is over, each Thales Royale starts with total of 6 rounds with each round lasting 24h.
* Each round has a 8h position phase and a 16h resolution phase.
* Buy-in is to be set to 20 sUSD.
* Each round has a 8h position phase and a 16h resolution phase.
* The price of ETH at the end of the 16h Resolution Phase is the result used for round resolution of the finished round and, at the same time, the starting Strike Price of the next round.
* Within the 8h Positioning Phase, players have to signal if the ETH price will be higher or lower at the end of the current round than current round Strike Price. Players can change their position as many times as they want during the positioning phase.
* If there is only a single person "alive" after a certain round, he is declared winner.
* If everyone is eliminated after a certain round, they are all declared winners.
* Winners split the pot and can claim sUSD directly from the contract.
* Thales Royale is now a seasonal event and users can navigate through past seasons. By default the current season is presented.
* A “Thales Royale Event” describes the entirety of the sign-up phase, all 6 rounds (or less if all or all but 1 player gets eliminated before the end of round 6) and the final conclusion of the winner(s).  


## Test Cases

Happy path
 - Sign up
 - Start season
 - Start royale in season
 - Take as position
 - Claim rewards - 1 player win
 - Claim rewards - multiple players win
 - Claim rewards - all players lose

Edge cases
 - Sign up for Thales Royale with no allowance
 - Sign up after sign up period has expired
 - Sign up with already signed up address
 - Try to start Season before sign up period expired
 - Try to start royale before seson is started
 - Try to take a position before royale started.
 - Try to take a position after round is finished
 - Try to start new royale, current is still ongoing
 - Try to start new season, current is still ongoing
 - Try to close the round, which is still ongoing.
 - Try to claim rewards second time
 - Try to claim rewards with no winner address
 
 
 
## Implementation
 
https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyale.sol
 
## Copyright
 
Copyright and related rights waived via CC0.
