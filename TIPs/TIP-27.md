| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-27 | Thales Royale new features| Draft | gruja (@gruja.work), padzank(@padzank) | Implement default position choosing on Sign Up for Thales Royale and temporarily allow Protocol DAO to sign in addresses for the Thales Royale sponsored by the Treasury DAO | [discord url](https://discord.com/channels/906484044915687464/939095931490549800) | 2022-02-09

## Simple Summary
 
This TIP proposes to implement default position choosing on Sign Up for Thales Royale and to temporarily allow Protocol DAO to sign in addresses for the Thales Royale, sponsored by the Treasury DAO
 
## Abstract
 
After doing a communnity sentiment gauge, this TIP proposes to allow a default position choosing on Sign Up and this way increase Thales Royale UX significantly. Also, this TIP proposes to promote fairness for all participants that missed the Season 1 first round positioning due to lack of notification system, by implementing a function that temporarely allows the Thales Protocol DAO to sign in addresses for Thales Royale on their behalf.
 
## Motivation
 
Shortly after Thales Royale positioning phase for round 1 of Season I started, it was evident that a significant percentage of Signed Up addresses failed to choose a position. Seems that the majority of users behind these addresses simply were not aware of the approaching deadline and were simply too late to position. For this reason, the community felt strongly about implementing a default position choosing on Sign Up to make the start of Thales Royale as fair as possible for all participants. For this to be made possible, there needs to be a new `signUpWithPosition` method implemented into Thales Royale contract.

It is a fact that during the start of Season I, Thales Discord did not have a notification system in place for Thales Royale players so they are reminded of approaching positioning deadline. To compensate for the lack of this feature during round 1 of Season I, community also felt strongly about allowing Protocol DAO to manually sign up and sponsor each address that missed the round 1 position on Season I, for participation in Season II. For this to be made possible, there needs to be a new `signUpOnBehalf` method implemented into Thales Royale contract.
 
## Specification

Based on discussions and [community feedback](https://discord.com/channels/906484044915687464/939095931490549800), this TIP entails the Protocol DAO to implement the following changes:

* Add option for a player to choose default position on a first round (UP or DOWN)
* Add a temporary option for Protocol DAO to sign in players which didn't choose a position for Season I round 1.

 Methods to be added in the Thales Royale contract:

 - signUpWithPosition(uint position)
 - signUpOnBehalf(address player) external *onlyOwner*

NOTE: There will still be an option to opt-out from choosing a default position on the first round.

## Test Cases

- Sign Up on behalf with added owner address
- Sign Up on behalf with no owner address
- Sign up with position, no changing positions
- Sign up with postition with changing positions after Royale started
- Try to change Sign up with position before Royale started

## Implementation
 
https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyale.sol
 
## Copyright
 
Copyright and related rights waived via CC0.
