| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-38 | Position per round on sign-up and asset per season at pDAO discretion| Vote Pending | Danijel | Allow position for each round to be submitted on royale sign-up. Allow Protocol DAO to choose the asset per season. Set rewards claiming deadline. | https://discord.gg/rPpPcMXSeU | 2022-03-28
 
## Simple Summary
 
- This TIP aims to allow users to submit an array of positions (one per each round) on signup.
- This TIP also allows ProtocolDAO to choose which asset from available THALES offering is used in a particular season.
- Additionally, this TIP proposes to set a one month deadline for winners to claim their prizes.
 
## Abstract
 
Following community feedback and data collection around participation behavior, this TIP proposes to implement a solution that allows submitting an array of positions for each round of Thales Royale in advance during the sign-up phase.
 
This TIP also proposes to allow pDAO to choose an asset to be speculated around on subsequent seasons on their own discretion.
 
Additionally this TIP proposes to set a deadline of 1 month for winners to claim their Thales Royale prize. Unclaimed rewards to be returned to treasury by default and subsequently to be rolled over manually to the next Thales Royale season as bonus to the prize pool by the Treasury DAO.  
 
## Motivation
 
In the first 4 Thales Royale seasons we have unfortunately witnessed many players miss positioning in a certain round.  
We added discord bots and have done a lot of reminders to a point where we probably focused too much energy on such trivial things, but still in last season 20 out of 51 players did not position in rounds 2.  
 
As we put funds and efforts into promoting the royale with Royale Passes NFTs, it is likely that a bunch of these players have tried the NFTs but didn't fully grasp the rules about the limited window for positioning. So marketing wise instead of attracting more players, we risk creating apathy.  
 
There are further benefits from allowing all positions to be submitted on sign-up:  
    - An average of 50% gas savings as half of the times you will be happy with your position in a certain round and would not have to change it  
    - Less pressure to have to be physically available to position on a certain day during the positioning window.  
    - Less frustration from scenarios where you believe you positioned, but somehow didn't see the transaction through till the end  
   
   
The biggest arguments against this so far was the competitive spirit where active players do not want "accidental winners".  
While this is a fair argument, the odds of someone winning without actively monitoring market movements in positioning phase are much less than the mathematical 1 to 64, as often markets will be quite skewed in certain rounds and price will move up to 10% from strike.  
It is also believed that there is more to gain from introducing this even for active players, as ultimately the goal of Royale is to maximize the pot and to onboard users into positional markets without much backfire.  
 
However, to ensure that even AFK "accidental winners" happen, the winning will be claimable for a limited window of 1 month.
 
Second part of this TIP is to allow ProtocolDAO to choose which asset will be speculated on within a certain season.  
The motivation behind this is to "keep things fresh" and as an example use SNX for season 5.  
It also allows us to set MATIC as an asset to speculate on during Polygon rollout.  
 
## Specification
 
This TIP entails the Thales pDAO to deploy a solution that allows a player, on sign-up for a certain Thales Royale season, to submit an array of 6 positions in advance for that specific season. One for each round. The individual positions will be adjustable by players during the position phase of the rounds themselves.  
 
This TIP entails the Thales pDAO to set a deadline of 1 month for winners to claim Thales Royale reward, from time of winning. Treasury DAO is entailed to facilitate the transfer of unclaimed rewards to the next Thales Royale season as bonus to the prize pool.  
 
Implementation is to be phased out in interest of time:  
 
 - Season 5 will have the default position applied in all rounds.
 - Season 5 will use SNX as an asset to speculate on to introduce some fresh experience.  
 - Season 6 will have the randomized positions for all 6 rounds offered in the UI and users will be able to change those before submitting.
 
 
## Copyright
 
Copyright and related rights waived via CC0.