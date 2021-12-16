| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-14 | Thales Royale Private Rooms mainnet rollout| Draft | Gruja (@grujawork) | Deploy and support Thales Royale Private Rooms as a recurring event on Optimism Mainnet | https://discord.gg/8bzFdpGTrp | 2021-12-16
 
## Simple Summary
 
This TIP proposes to formalize inclusion of Thales Royale Private Rooms as part of Thales protocol offering. 
 
## Abstract
 
Thales Royale started as an experiment to gamify Thales Binary Options experience. Based on that experience and community feedback there was a proposal for Thales Royale which will be created by the users themselves and try to compete with a closed group of people or set their own rules of Royale.
 
## Motivation
 
After the successful lunch of Thales Royal on OP Kovan testnet there was a community proposal that seems to bring more attention to Thales CC's, and that created your own Thales Royale. So, their idea of private rooms started.

Thales Royale Private Rooms is a child from a parent Thales Royale ([TIP-13](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-13.md)), and all battles are inherited from that idea - compete with each other with your own set of rules (number of rounds, game type, periods for choosing, finishing rounds, etc.).

As Thales CC's love to compete we love this idea and we came to this proposal.

## Specification
 
This TIP entails Thales Protocol DAO to support [Thales Royale Private Rooms contract](https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyalePrivateRoom.sol) deployment on Optimism Mainnet. 

Thales Royale Private Rooms will be rolled out in L2 mainnet, with the specification which is explained below.

Proposed specification:  

1. Each user can create his private room for Thales Royale and pick his own set of rules (hereinafter: Creator)
2. Creator is also first participant and he will be included into buy-in (which he sets) immediately when creating a room
3. As said above creator will set buy-in for him and other players (equal amount) and each user will on sign-in pay that amount in sUSD, minimum sUSD buy-in is 1 sUSD
4. Creator will choose how many rounds will be in his Thales Royale (minimum number of rounds is 2)
5. Creator will choose how much time will be choosing period length, round length, and sign-in period, claim time
   - Minimum sign period is 15 min.
   - Minimum round time is 30 min.
   - Minimum choose time is 15 min.
   - Minimum offset between choose time and round end is 15 min.
   - Minimum claim time is 1 day
6. Creator will choose assets on which royale is playing for now available assets for choose are ["BTC", "ETH", "LINK", "SNX"], one asset per royale
7. Creator will be choosing the game type 
   - LAST_MAN_STANDING - there is only one winner, in this case, the creator chooses the number of rounds but if there is in last more than one player Royale is continued until one is the winner
   - LIMITED_NUMBER_OF_ROUNDS - no matter number of winners in the last round all are winners and the pot are split, also in this game type splitting a pot is active if all players in the round choose the wrong position
8. Creator will be choosing the room type
   - OPEN - a open room is a room that will be open to everyone but with a limited number of players per Royale (a number which Creator will set)
   - CLOSED - a closed room is a room that will be open only to people (addresses) which Creator will specify and the max number of people in a closed room is 10 (Creator plus nine more)

Proposed specification for room management:

NOTE: All below specification points are valid only if Royale is not started yet.

1. Increasing/decreasing buy-in amount - Creator will be able to increase buy-in amount or decrease it (decrease not less than minimum buy-in) until the first person is sign-up for his room.
   - in a case of decreasing - the difference will be returned to Creator and a new amount is set
   - in a case of increasing - the difference will need to be paid by Creator and a new amount is set
2. Setting new round length - Creator will be able to set new round length, the round length must be greater than minimal round length, and also offset time between round length and choosing period is also checked
3. Setting new claim time  - Creator will be able to set new claim time, claim time must be greater than minimum claim time
4. Setting new sign up period - Creator will be able to set a new sign up period, that period must be greater than the minimum period time
5. Setting a new number of rounds - Creator will be able to change the number of rounds which is not less than a minimal number of rounds.
6. Setting new round choosing period - Creator will be able to set new round choosing length, the round choosing length must be greater than minimal round choosing length, and also offset time between round length and choosing period is also checked
7. Setting a new asset - Creator will be able to update on which asset royale is playing and that asset must be in allowed assets ["BTC", "ETH", "LINK", "SNX"]
8. Setting new players that are allowed to play - Creator can change allowed players if room type is CLOSED and players did not start sign-up
9. Adding new players in allowed players list - Creator can add players in a list only if the type of room is CLOSED
10. Setting amount of players - Creator can set a new amount of players to participate in a room only if the room type is OPEN and that amount is less or equal to the maximum amount of players per room.
11. There will be no way that creator can change room type or game type.

## Test Cases

## Implementation
 
https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyalePrivateRoom.sol

## Copyright
 
Copyright and related rights waived via CC0.
