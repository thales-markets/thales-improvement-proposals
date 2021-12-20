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
    To be elaborated. For example increase, buy-in amount, increase round length when this is possible, etc. section below this [ROOM MANAGEMENT](https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyalePrivateRoom.sol#L390)

## Test Cases

## Implementation
 
https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyalePrivateRoom.sol

## Copyright
 
Copyright and related rights waived via CC0.
