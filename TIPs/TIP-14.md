| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-14 | Thales Royale Private Rooms mainnet rollout| Draft | Gruja (@grujawork) | Deploy and support Thales Royale Private Rooms as a recurring event on Optimism Mainnet | https://discord.gg/8bzFdpGTrp | 2021-12-16
 
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
5. The Creator will select the choosing period length, round length, sign-in period and the claim time:
   - Minimum sign-in period is 15 min.
   - Minimum round time is 30 min.
   - Minimum choosing time is 15 min.
   - Minimum offset between choosing time and round end is 15 min.
   - Minimum claim time is 1 day
6. The Creator will choose the assets whose price is to be predicted in the Royale. For now, the available assets to choose from are ["BTC", "ETH", "LINK", "SNX"], one asset per Royale.
7. The Creator will be choosing the game type 
   - LAST_MAN_STANDING - there is only one winner, in this case, the creator chooses the number of rounds, but if there is more than one player in the last round, the Royale is continued until there is only one winner
   - LIMITED_NUMBER_OF_ROUNDS - no matter the number of winners in the last round, all of them are winners and the pot is split. Also, in this game type, if all players in the round choose the wrong position, the pot is also split among them.
8. The Creator will be choosing the room type
   - OPEN - an open room is a room that will be open to everyone but with a limited number of players per Royale (a number which the Creator will set)
   - CLOSED - a closed room is a room that will be open only to people (addresses) which the Creator will specify and the max number of people in a closed room is 10 (Creator plus nine more)

Proposed specification for room management:
    To be elaborated. For example increase buy-in amount, increase round length when this is possible, etc. section below this [ROOM MANAGEMENT](https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyalePrivateRoom.sol#L390)


## Test Cases

## Implementation
 
https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyalePrivateRoom.sol

## Copyright
 
Copyright and related rights waived via CC0.
