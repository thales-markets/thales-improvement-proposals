| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-29 |  Deployment of Thales Royale Pass Utility NFT| Implemented | padzank(@padzank), gruja.work(@gruja.work) | Deploy Thales Royale Pass NFTs to act as transferable Buy-Ins | [Discord URL](https://discord.gg/hHH7EJf8M5) | 2022-02-20

## Simple Summary
 
This TIP proposes to deploy Thales Royale Pass NFTs on Optimism that will be purchasable for 30 sUSD and be used as transferable Thales Royale Sign-Ups
 
## Abstract
 
By initial design, a user sign ups for Thales Royale with a 30 sUSD buy-in that whitelists that specific wallet for the ongoing Thales Royale Season participation. This TIP proposes to introduce a Thales Royale Pass NFT that will be purchasable with 30 sUSD, and that NFT would enable a wallet that is holding it a free Sign-Up for any 30 sUSD buy-in Thales Royale Season of choice. This way, any wallet can purchase Thales Royale Pass (or multiple Passes) and sponsor an another wallet/s by sending it the Thales Royale Pass NFT.

## Motivation
 
There are several clear benefits of having Thales Royale Pass NFTs.  

 - By having a transferable Thales Royale Pass NFTs that offers a Sign-Up to Thales Royale Season of choice for a wallet that is holding it, mechanism similar to that of a Gift Card is achieved. This can potentially be a powerful marketing tool, allowing users to sponsor other users and thus promote the Thales Royale.  
 - Thales Royale Pass NFT receiver avoids a friction point of acquiring sUSD in his wallet for the Buy-In required for the Sign Up, but instead the NFT contract holds the 30 sUSD that will be transfered to Thales Royale contract as a Buy-In on Sign-Up for the user of that NFT pass.
 - Introduction of Thales Royale Pass mechanism is the required first step towards developing further NFT representations of Thales Royale positions and further expansion of flexibility and utility of Thales Royale participation.
 
## Specification

This TIP entails the Protocol DAO to create [NFT contract](https://github.com/thales-markets/contracts/tree/main/contracts/ThalesRoyale) which will be a representation of Thales Royale Pass.

NFT contract contains:
 - `mint` method which creates a new NFT and sends it to the recipient, who can then be used to sign in for Thales Royale, each minting is 30 sUSD (buy-in amount)
 - `burnWithTransfer` method which is called from [Thales Royale contract](https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyale.sol) only, this method will be called inside signUpWithPass method, after burning this NFT can not be used in the future.
 - the contract will have paused flag which is set to `false` and can be set to `true` when needed, this will pause all future minting.

 This TIP additionally entails the Protocol DAO to remove the following reduntant method from the Thales Royale contract that served it's purpose for the elapsed Season II Round 1:

 - signUpOnBehalf(address player) external *onlyOwner*

In the Thales Royale contract will be added two methods for signing in into Royale with Pass:

 - `function signUpWithPass(uint passId) external playerCanSignUpWithPass(passId)` - Sign up with Royale pass without default position for first round
 - `function signUpWithPassWithPosition(uint passId, uint position) external playerCanSignUpWithPass(passId)` - Sign up with Royale pass with default position for first round

 For both methods, the buy-in amount will be transferred from NFT contract to the Thales Royale contract and included in the total prize money.

## Configurable Variables

Thales Royale Pass will have configurable variables

- *price* - price is the amount of sUSD which minter will pay for the Thales Royale Pass, default is set to `30 sUSD`, this amount will be in sinc with buy-in amount in Thales Royale contract
- *tokenURI* - is URI to an image of the NFT, which is changed if some of the functionality is changed 
- *paused* - variable which allows NFT to be minted, the default value is `false`.

## Test Cases

- mint NFT for yourself, NFT in wallet
- mint NFT for another player, NFT in wallet
- mint NFT transfer to another player and play royale, NFT burned
- sign up with pass with position, play royale, NFT burned
- sign up with pass without position, play royale, NFT burned
- try to sign up with a pass from another player, expected to fail, failed

## Implementation

- [Thales Royale Contract](https://github.com/thales-markets/contracts/blob/main/contracts/ThalesRoyale/ThalesRoyale.sol)
- [Thales Royale Pass Contract](https://github.com/thales-markets/contracts/tree/main/contracts/ThalesRoyale)
 
## Copyright
 
Copyright and related rights waived via CC0.
