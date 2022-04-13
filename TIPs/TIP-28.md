| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-28 | Optimistic Exotic Positional Markets | Draft | Danijel (@danijelthales) | Implement Thales Optimistic Exotic Positional Markets | https://discord.gg/rPpPcMXSeU | 2022-02-09 

## Simple Summary
 
This TIP proposes a format for Optimistically created and resolvable Exotic Positional Markets.
 
## Abstract
 
It's the vision of the Thales Protocol to support Exotic Positional markets that anyone can create. This TIP proposes a format that can achieve this in a decentralized manner with an optimistic oracle type overviewed by an Oracle Council voted in by Thales Stakers. 
 
## Motivation
 
Since inception Thales set out to become a parimutuel protocol where participants chip-in and take a position. The said positions have to be mutually exclusive and capture a full range or potential outcomes.  
Initially only binary positions were supported, but the framework proposed here allows for any number of positions to be defined, as long as those adhere to the rules of being mutually exclusive and capturing all outcomes.  

Thales wants to be fun, dynamic and flexible. Thales will continue working with Chainlink and pursuing Chainlink provided feeds for Sports and other data.  
However, it is fully expected that to meet the community demand for exotic markets Thales needs another framework that allows for more flexible ad-hoc markets.  

The proposed framework intents to capture such markets and is quite flexible in terms of possibilities it could lead to.

All details of the framework are in specification section.

## Specification

### Thales Oracle Council 
Thales Oracle Council is described in TIP-35 https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-35.md.

### Duties of Oracle Council

### Market Creation   

Anyone can create a market. When creating a market, the creator has to put up a bond of 100 sUSD.  
With this bond the creators commits to have created a market adhering to the guidelines and to submit a request to resolve a market no longer than 24h after the market is theoretically resolvable.  

When creating a market the following parameters have to be provided:  
- Market question (String up to 200 characters)
- Market data sources (String up to 200 characters, can basically be a url linking to a page that will show the result on maturity)
- An array of positions participants can assume (up to 8 positions supported of type String)
- End of positioning phase (timestamp - minimum 8 hours for positioning)
- Type:  
          - `Fixed Ticket` (same ticket price for anyone, min 10 sUSD), needs amount to be specified  
          - `Open Bid`  (min 10 sUSD)
          - Placeholder for more types that will be in additional TIPs
- Creator's initial amount and position (creator has to put up at least the minimum 10 sUSD into a single position)
- Withdrawals allowed (if allowed can be made only up to 8h before positioning ends)
- An array of up to 5 tags from the available list of tags. Tags will be used by dapps for easier market discovery. 

The list of available tags is managed by Oracle Council. Examples are: Sports, Politics, Football, NBA, Esports, DeFi, Crypto...   

As soon as a market is created it is considered in positioning phase and open to participants to bid and position.

Each bid is subject to a total fee of 3%, out of which 1% goes to the market creator, 1% to the market resolver and 1% towards the Safe Box. The fees are only paid out in case market is not cancelled.  
If allowed, withdrawals are subject to a total 6% fee. 3% paid to the market creator and 3% towards Safe Box. These fees are paid within the withdrawal transactions.  


Market creator can cancel the market at any time if there are no other bids but his/her own in the market pool.

Market creation will be reverted on contract side if the following is not adhered to:
- Market question is not blank   
- Market data sources parameter is not blank
- There are a minimum of 2 positions and those are not blank
- Length of positioning phase has to be at least 8h
- Market has at least one tag


Every market must be created according to the guidelines maintaned by Oracle Council.

### Positioning phase
During the positioning phase participants pay the fixed entry bid in case of `Fixed Ticket` markets or put up custom sized bid in case of `Open Bids` markets.  

For `Fixed Ticket` market one wallet can buy only one ticket and choose a single position. The position can be changed during positioning phase as many times as that participant wishes.  

For `Open Bid` market one wallet can enter multiple bids and spread the bids across multiple positions. To reposition, they have to first pull the bid from a position and then choose to deposit it into a new position.


### Disputes in positioning phase
Anyone, that is not a member of Oracle Council, can dispute a market while in positioning phase. To open a dispute the wallet raising the dispute needs to put up 100 sUSD as a bond.
On raising the dispute, the person disputing the market inputs the reason for the dispute as string (up to 1000 characters).  
The number of open disputes on a market is not limited, but duplicating disputes can lead to a slash for the wallet raising the duplicated dispute.

Apart from disputes about not following the guidelines one can also raise a dispute for a not foreseen event that causes the market to become obsolete, e.g. a game is postponed. 

Oracle council is the body resolving the disputes. 
An open dispute does not affect the market while its been processed (buy-in and positioning still goes on unaffected).

Oracle council can choose the following options to resolve a dispute:  
- `Accept the dispute` in which case the market is closed and everyone can claim the full refund from the market. This resolution is split into two sub-resolutions depending on whether a slash will occur:  
    - `Accept the dispute and slash the creator` The wallet that opened the dispute gets the bond back and the bond of the creator minus 10 sUSD which goes to the Safe Box. This is likely to happen if the guidelines were not adhered to, or if at least 24h has passed in which its considered that the creator has an opportunity to submit this dispute himself (e.g. a sport's match is postponed indefinitely and 24h passed since the news were released)
    - `Accept the dispute but do not slash the creator` The wallet that opened the dispute gets the bond back and an arbitrary reward in sUSD up to 100 sUSD from Oracle Council budget. In this case Oracle Council did not find enough reason to slash the creator, but considers the dispute valid.   
- `Refuse the dispute and slash the wallet that raised it` The bond goes towards Safe Box. In this case Oracle Council finds that the user that raised the dispute did so unjustifiably.   
    
When a dispute is accepted, all disputes raised after that dispute are cancelled and bonds are claimable back to those that raised them.
Accepting a dispute starts a timelock of 4h in which Protocol DAO or Thales Council can step in as backstops and pause the market from being cancelled if they have doubts about the decision OC made. 

When the 4h passes, users can claim their refunds from the market.
    
Bonds are intended to ensure good behaviour, but are not meant to be punitive. Its within the autonomy of Oracle Council to decide if there was irresponsibility of malice when deciding if a certain bond should be slashed.


### Maturity phase

Once the market hits maturity phase anyone can submit a request to resolve the market with a certain outcome and a bond of 100 sUSD.
Market creator can also submit a request to resolve the market, but he doesnt need to submit a new bond, rather his initial bond is used in case of a dispute.

In addition to all positions listed on the market creation, there is a default position available to select when resolving a market which is called `Cancelled`.  
Resolving a market with this position will allow anyone who bid on the market to claim a full refund, just like per rules in positioning phase due to a cancellation.

Once a market has been resolved, there is 24h window for anyone to raise a dispute on the market outcome with a bond of 100 sUSD.
This dispute has to have a `reasonForDispute` string.
 
The Oracle council reviews the dispute and can decide the following:  
- `Accept the dispute and set a result` in which case the resolver fee goes to the Safe Box.  
- `Accept the dispute and reset market result` (in case OC believes it is not yet possible to resolve a market)  
    Both cases lead to a slash for the resolver and the bond of the resolver, - 10 sUSD which go to the Safe Box, goes to the wallet raising the dispute.  
- `Refuse the dispute` the bond goes towards Safe Box  

When Oracle Council accepts a dispute all subsequent disputes are closed and bonds are claimable back to those that raised them.
If Oracle Council chose `Accepted the dispute and set a result` a timelock of 4h begins during which Protocol DAO or Thales Council can act as a backstop should they find the result set by the Oracle Council contentious.  

If 24h has passed since the market was resolved or at least 4h since a dispute was closed with `Accept the dispute and set a result`, the market is formally resolved and winners can start claiming their winnings.
In case there are no winners, everyone can claim their initial bid minus the fees.

### Oracle Council emergency pause
Each Oracle Council member is able to pause a malicious market in case of an emergency. 
The market can be resummed by the Protocol DAO. 
In the case of a malicious use of the emergency pause by an Oracle Council member, the Thales Council can then choose to replace the individual Oracle Council member with the next candidate per voting tally, or call a new election if needed.

### Oracle Council backstop
Bonds serve as deterrent for bad actors while creating, resolving and disputing markets, but what if oracle council decides to collude?
Protocol DAO will maintain the possibility to pause either individual markets or all markets if it detects any suspicious behavious and inform Thales Council about malpractice of Oracle Council members.
To ensure a swift reaction any of the Protocol DAO signers or Thales Council members will have the possibility to pause a market, but unpause can only be done via the Protocol DAO multisig.  

Thales Council can then choose to replace individual council members with the next candidate per voting tally, or call a new election if needed.

Treasury DAO will set aside 500k sUSD as insurance fund for all market participants.

### Product bonus (previous AMM bonus)
Every Thales staker trading Exotic markets contributes to the weekly Product bonus with maximum 12%, previously referred only as AMM bonus. 

Note that the accumulated Exoting trading volume is combined together with the AMM trading volume. 

The Exotic trading volume considers positioning on all active Exotic markets during a Thales staking period. Bonds for creation/disputes/resolution of Exotic markets are not calculated in the Exotic trading volume. 

### Table of dispute states and actions

| State / Disputes | ACCEPT & SLASH | ACCEPT NO SLASH | REFUSE ON POSITIONING | ACCEPT & RESULT | ACCEPT & RESET | REFUSE |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| Description | Accept the dispute and slash the creator | Accept the dispute but do not slash the creator | Refuse the dispute and slash the wallet that raised it | Accept the dispute and set a result | Accept the dispute and reset market result | Refuse the dispute |
| Phase | POSITIONING | POSITIONING | POSITIONING | MATURE | MATURE | MATURE |
| Creator fee | to Disputor minus 10 sUSD to SafeBox | to Creator | - | - | - | - |
| Resolver fee | - | - | - | to SafeBox | to Disputor minus 10 sUSD to SafeBox | - |
| Disputor fee | to Disputor + (Creator fee - 10sUSD) | to Disputor + (reward from: 10 to 100 sUSD) | to SafeBox | to Disputor | to Disputor + (Resolver fee - 10 sUSD) | to SafeBox |
| Funds to SafeBox | 10 sUSD | - | Disputor fee | Resolver fee | 10 sUSD | Disputor Fee |
| Disputor additional reward | - | up to 100 sUSD | - | - | - | - |
| Backstop timer | 4 h | 4 h | - | 4 h | 4 h | - |
| Market closed for disputes | CLOSED | CLOSED | OPEN | CLOSED | OPEN | OPEN |
| Unsolved Open Disputes -> dispute fees claimable | Claimable | Claimable | Not Claimable | Claimable | Not Claimable | Not Claimable |
| Market cancelled | Yes | Yes | No | No | No | No |
| Market resolved | Yes | Yes | No | Yes | No | No |
| Funds claimable | Market cancelled, deposited funds claimable | Market cancelled, deposited funds claimable | 24h after Market is resolved | Market reset, 4h after Dispute closure | 24h after Market is resolved | 24h after Market is resolved |


## Rationale
 
TBD
 
## Test Cases
 
### Example1
WalletA creates a market "Who will win the Super Bowl LVI", with positions `Rams` or `Bengals` and a `Fixed Ticket` type with 50 sUSD ticket.
The market parameters are all correctly set. 
The creator resolves the market himself and gets 2% of fees. There are no disputes in the following 24h so those that positioned on the winning side can redeed their winnings.

### Example2
WalletB creates a market "Will Lakers win the NBA Championship 2022-23" with positions `Yes` and `No`.   
End of positioning is set at end of regular season.  

While this market might look ok at first glance, it can be disputed because Lakers have not secured a play-off spot and thus the market might become obsolete before the end of positioning.  


### Example3
WalletC creates a market "How many goals will be scored in the match Liverpool vs Manchester United" with positions "0-2", "3-4" or "5+".  
All dates are set correctly, end of positioning is before the match starts.  
WalledD resolves the market correctly within 24h hours. There are no disputes in the following 24h so those that positioned on the winning side can redeed their winnings.

WalletC gets 1% of fees and WalletD gets 1% of fees.

This is an example of a market with more than 2 positions, but only one position can be the winning one. 


### General examples of markets that should not be created

Any markets speculating on deaths in any form should be instantly disputed and slashed.  
Any markets that community members could have inside info on, or otherwise be in a position to take advantage of non public info, should be instantly disputed and slashed.
Any racism or discriminatory markets should be instantly disputed and slashed.

Any market in which the outcome could be known before end of positioning, e.g. speculating on the number of ETH burned (this requires a different type of market to be defined in another TIP down the line).


### General examples of markets that would be acceptable

Winner of a sports match (positioning has to end before the match starts)
Winner of a tournament (positioning has to end before the tournament starts)
Speculating on asset prices or market caps is fine. Also speculating on their ratios (e.g. the flippening).
Winner of political elections ((positioning has to end before the election starts).




  
 
 
## Implementation
 
Only fixed type will be released in this iteration. Open bid needs more considerations about how to ensure fairness for participants.
 
## Copyright
 
Copyright and related rights waived via CC0.
