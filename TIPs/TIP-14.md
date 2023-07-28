| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-14 | Thales Royale Private Rooms mainnet rollout| Implemented | Gruja (@grujawork) | Deploy and support Thales Royale Private Rooms as a recurring event on Optimism Mainnet | https://discord.gg/8bzFdpGTrp | 2021-12-16
 
## Simple Summary
 
This TIP proposes to formalize the inclusion of Thales Royale Private Rooms as a part of Thales protocol offering. 
 
## Abstract
 
Thales Royale started as an experiment to gamify the Thales Binary Options experience. Based on that experience and the community feedback, there was a proposal for a version of Thales Royale which will be created by the users themselves, where they could compete with a closed group of people or set their own rules of Royale.
 
## Motivation
 
After the successful launch of Thales Royal on the OP Kovan testnet there was a community proposal that caught the attention of Thales CC's - the possibilty to create your own Thales Royale. And that's how the idea of private rooms was born.

Thales Royale Private Rooms is a child from the parent - Thales Royale ([TIP-13](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-13.md)), and all battles are inherited from that idea - competing with each other with your own set of rules (number of rounds, game type, periods for choosing, finishing rounds, etc.).

As Thales CC's are avid competitors themselves, we loved this idea and came to this proposal.


## Specification
 
This TIP entails Thales Protocol DAO to support [Thales Royale Private Rooms contract](https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyalePrivateRoom.sol) deployment on Optimism Mainnet. 

Thales Royale Private Rooms will be rolled out on L2 mainnet, with the specification explained below.


Proposed specification:  

1. Each user can create his private room for Thales Royale and pick his own set of rules (hereinafter: Creator)
2. The Creator is also the first participant and he will be included into the buy-in (which he sets) immediately after creating a room
3. As said above the Creator will set the buy-in for him and other players (an equal amount) and each player will pay that amount in sUSD on sign-in,  the minimum buy-in being 1 sUSD
4. The Creator will choose how many rounds will there be in his Thales Royale (minimum number of rounds is 2)
5. The Creator will select the choosing period length, round length and sign-in period:
   - Minimum sign-in period is 15 min.
   - Minimum round time is 30 min.
   - Minimum choosing time is 15 min.
   - Minimum offset between choosing time and round end is 15 min.
6. The Creator will choose the assets whose price is to be predicted in the Royale. For now, the available assets to choose from are ["BTC", "ETH", "LINK", "SNX"], one asset per Royale.
7. The Creator will be choosing the game type 
   - LAST_MAN_STANDING - there is only one winner, in this case, the creator chooses the number of rounds, but if there is more than one player in the last round, the Royale is continued until there is only one winner
   - LIMITED_NUMBER_OF_ROUNDS - no matter the number of winners in the last round, all of them are winners and the pot is split. Also, in this game type, if all players in the round choose the wrong position, the pot is also split among them.
8. The Creator will be choosing the room type
   - OPEN - an open room is a room that will be open to everyone but with a limited number of players per Royale (a number which the Creator will set)
   - CLOSED - a closed room is a room that will be open only to people (addresses) which the Creator will specify and the max number of people in a closed room is 10 (Creator plus nine more)
9. There is a possibility of a safe box and safe box percentage. That percentage will be transferred from the buy-in amount to the safe box address and the rest of the sUSD will be added to the reward.

Proposed specification for room management:

**NOTE: All below specification points are valid and enabled only until the first user is signed in, which means he accepted the condition.**

1. Increasing/decreasing buy-in amount - The Creator will be able to increase buy-in amount or decrease it (decrease cannot be smaller than the minimum buy-in) until the first person has signed-up for his room.
   - in the case of decreasing - the difference will be returned to the Creator and a new amount is set, if safebox percentage is set the that % amount will NOT be transfered back from safebox, just the difference between rewards.
   Example:
   Buy in is 100 sUSD with 2% safebox if creator decrease buy in to 50 sUSD return will be 49 sUSD (98 - 49, difference after safebox calculation)  
   - in the case of increasing - the difference  needs to be paid by the Creator and a new amount is set, if safebox percentage is set that % amount will be transfered to safebox 
   Example:
   Buy in is 100 sUSD with 2% safebox if creator increase buy in to 200 sUSD and new 2 sUSD is put into safebox 
2. Setting new round length - The Creator will be able to set new a round length. The round length must be greater than the minimal round length, and offset time between round length and choosing period is also checked
4. Setting new sign up period - The Creator will be able to set a new sign up period, that period must be greater than the minimum period time
5. Setting a new number of rounds - The Creator will be able to change the number of rounds as long as it is not smaller than the minimal number of rounds.
6. Setting new round choosing period - The Creator will be able to set new round choosing length. The round choosing length must be greater than minimal round choosing length, and also offset time between round length and choosing period is checked
7. Setting a new asset - The Creator will be able to update the asset whose price is to be predicted in the Royale. That asset again must be one of the allowed assets ["BTC", "ETH", "LINK", "SNX"]
8. Setting new players that are allowed to play - The Creator can change the list of allowed players if the room type is CLOSED and players did not start sign-up
9. Adding new players to the allowed players list - The Creator can add players to the list only if the type of room is CLOSED
10. Setting the amount of players -The Creator can set a new amount of players to participate in a room only if the room type is OPEN and that amount is less or equal to the maximum amount of players per room.
11. Delete a room - Creator can "delete a room", room then goes into the state `published = false` and funds which the creator has paid will go back to his wallet, and users **can not** sign up for that room
12. There will be **no way** that the Creator can change the room type or game type.

## Test Cases
 
## Implementation

[Thales Royale Private Rooms Implementation](https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyalePrivateRoom.sol)



## Copyright
 
Copyright and related rights waived via CC0.
