| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-29 |  Deployment of Thales Royale Pass Utility NFT| Draft | padzank(@padzank) | Deploy Thales Royale Pass NFTs to act as transferable Buy-Ins | [Discord URL](https://discord.gg/hHH7EJf8M5) | 2022-02-20

## Simple Summary
 
This TIP proposes to deploy Thales Royale Pass NFTs on Optimism that will be purchasable for 30 sUSD and be used as transferable Thales Royale Sign-Ups
 
## Abstract
 
By initial design, a user sign ups for Thales Royale with a 30 sUSD buy-in that whitelists that specific wallet for the ongoing Thales Royale Season participation. This TIP proposes to introduce a Thales Royale Pass NFT that will be purchasable with 30 sUSD, and that NFT would enable a wallet that is holding it a free Sign-Up for any 30 sUSD buy-in Thales Royale Season of choice. This way, any wallet can purchase Thales Royale Pass (or multiple Passes) and sponsor an another wallet/s by sending it the Thales Royale Pass NFT.

## Motivation
 
There are several clear benefits of having Thales Royale Pass NFTs.  

 - By having a transferable Thales Royale Pass NFTs that offers a Sign-Up to Thales Royale Season of choice for a wallet that is holding it, mechanism similar to that of a Gift Card is achieved. This can potentially be a powerful marketing tool, allowing users to sponsor other users and thus promote the Thales Royale.  
 - Thales Royale Pass NFT receiver avoids a friction point of acquiring sUSD in his wallet for the Buy-In required for the Sign Up, but instead the NFT itself holds the 30 sUSD that is used as a Buy-In for a Thales Royale Sign Up.
 - Introduction of Thales Royale Pass mechanism is the required first step towards developing further NFT representations of Thales Royale positions and further expansion of flexibility and utility of Thales Royale participation.
 
## Specification

This TIP entails the Protocol DAO to ...



 This TIP additionally entails the Protocol DAO to remove the following reduntant method from the Thales Royale contract that served it's purpose for the elapsed Season II Round 1:

 - signUpOnBehalf(address player) external *onlyOwner*

## Test Cases

## Implementation
 
## Copyright
 
Copyright and related rights waived via CC0.
