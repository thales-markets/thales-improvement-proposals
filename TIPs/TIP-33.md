| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-33 | Formalize the new DAO token | Draft | padzank (@padzank) | Formalize the new DAO token and this way support future token related processes such as CEX listings, fast-bridge integrations and similar  | https://discord.gg/8bzFdpGTrp | 2022-03-10
 
## Simple Summary
This TIP aims to formalize the new DAO token and this way support future processes of CEX listings, fast bridging integrations and similar.
## Abstract
After the successful migration of THALES token to the new token contract on Optimism, rewards contracts migration to Optimism and sufficient liquidity build-up, this TIP proposes to formalize the new THALES token contract as the official DAO token. 
## Motivation  
Since deployment in early 2022, the THALES token migration to Optimism was a seamless "one-txn" experience that included migrating the THALES token to the new token contract and bridging it to Optimism. Initial motivation for the token migration was the mitigation of Core Contributor token allocation incident from late 2021. With this successful seamless migration, additional motivation was to transfer all THALES token related operations to a cheap and fast environment such as Optimism. Now that there are no more LP incentives for the old token on L1 and that the majority of the supply and liquidity is on Optimism layer 2 network in the form of the new token contract, it is time to formally acknowledge the new token contract as the main official DAO token.  
  
**As we formalize the new token as the official DAO token, migration from legacy token to the new token will be supported in a frictionless way from the Thales dapp indefinitely. Retro distribution contract, being fully immutable from launch, will continue to emmit legacy THALES tokens to receiving addresses which will be able to use the THALES migration tool from the Thales dapp at all times to convert their legacy THALES tokens to new THALES token contract.**  
  
Formalization proposed by this TIP will allow the new THALES token to expand it's presence on L1 and potentially other networks in the future, without any complication and confusion that could derive from having the legacy token and the new THALES token present at the same network. This formalization is also a necessity if we are to facilitate future CEX listings, fast-bridge solution partnerships and other various potential integrations that require spotless clarity around the official DAO token.  

## Specification

This TIP entails the Thales Protocol DAO to support the new THALES token as official DAO token that has the following addresses:  
- THALES token contract on **Optimism**: [0x217d47011b23bb961eb6d93ca9945b7501a5bb11](https://optimistic.etherscan.io/token/0x217d47011b23bb961eb6d93ca9945b7501a5bb11)
- THALES token contract on **Ethereum mainnet**: [0x8947da500Eb47F82df21143D0C01A29862a8C3c5](https://etherscan.io/token/0x8947da500Eb47F82df21143D0C01A29862a8C3c5)

## Test Cases
 
## Implementation

## Copyright
 
Copyright and related rights waived via CC0.
