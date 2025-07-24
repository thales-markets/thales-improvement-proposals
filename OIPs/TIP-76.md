| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-76 | Overtime Voucher Contract | Vote Pending | Danijel (@danthales) | Deploy a Overtime Voucher NFT Contract | https://discord.gg/8bzFdpGTrp  | 2022-08-18
 
## Simple Summary
 
This TIP proposes to add a Overtime Voucher Contract that is an ERC721 NFT, which when minted contains sUSD for the owner to use to interact with the Sports AMM. 

## Motivation

Overtime vouchers will be used to support marketing campaigns such as the upcoming Sports Trivia competition. The idea is to create a rewards loop that sends the recipients back overtime, thus helping overtime gain traction and users.  
Instead of sending the sUSD directly to the users, which they would not technicaly be enforced to even use on overtime, we send them an NFT that, besides looking great, contains rewarded sUSD and can be used on the overtime dapp to buy sport positions.  
A voucher can also be considered as a gift card.    
 
## Specification
 
The Voucher contract inherits much from the Thales Royale Pass contract. It will have 6 predefined values which can be used to mint a voucher:  
    - 20 sUSD  
    - 50 sUSD  
    - 100 sUSD  
    - 200 sUSD  
    - 500 sUSD  
    - 1000 sUSD 
    
On the mint transaction, the sUSD is sent from the caller to the NFT contract. The contract will have a method "buyFromAMM", which receives the sports market and position and amount which the owner of the NFT wants to purchase using the voucher.  
The voucher can be reused many times as long as there is more than 1 sUSD left in it. If the amount drops below 1 sUSD after, the voucher is burnt and any remaining sUSD is sent to the owner.  

The following art will be used for the NFT voucher:  
- https://thales-protocol.s3.eu-north-1.amazonaws.com/voucher1-20.png  
- https://thales-protocol.s3.eu-north-1.amazonaws.com/voucher1-50.png  
- https://thales-protocol.s3.eu-north-1.amazonaws.com/voucher1-100.png  
- https://thales-protocol.s3.eu-north-1.amazonaws.com/voucher1-200.png  
- https://thales-protocol.s3.eu-north-1.amazonaws.com/voucher1-500.png  
- https://thales-protocol.s3.eu-north-1.amazonaws.com/voucher1-1000.png   
     
## Rationale
N/A
## Test Cases
Fully covered with tests on https://github.com/thales-markets/contracts/tree/overtime-voucher
## Implementation
https://github.com/thales-markets/contracts/tree/overtime-voucher
## Copyright
Copyright and related rights waived via CC0.
