| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-27 | Thales Royale change contract| To be confirmed | gruja (@gruja.work) | Change of default position, sign up players on behalf of owners which did't position at first season first round | [discord url](https://discord.com/channels/906484044915687464/939095931490549800) | 2022-02-09

## Simple Summary
 
This TIP proposes change of [TIP-13](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-13.md) - Thales Royale. 
 
## Abstract
 
Thales Royale change is about default position in the first round and sign-in players on behalf of the owner.
 
## Motivation
 
On a discord channel, we had a pool in the middle of season 1, and the community agreed on minor changes on the Thales Royale contract.
 
## Specification

Based on discussions and [community feedback](https://discord.com/channels/906484044915687464/939095931490549800) we added two points:

* Adding possibility for a player to choose default position on a first round (UP or DOWN)
* Adding possibility for owner of a contract to sign in players which didn't choose a position at first season first round

## Added methods in contract

* signUpWithPosition(uint position)
* signUpOnBehalf(address player) external *onlyOwner*

NOTE: There is still a possibility to not choosing default position on the first round.

## Test Cases
 
## Implementation
 
https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyale.sol
 
## Copyright
 
Copyright and related rights waived via CC0.
