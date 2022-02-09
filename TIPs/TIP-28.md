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
Form a Thales Oracle Council of 4 members elected by THALES stakers.  
The nominations and elections process as well as stipends are as established before for the Thales Council (1000 THALES per month).  
First epoch will be shorter to align it with regular council epoch going forward, so it will end 30th of June 2022.    

Thales Treasury DAO will fund Oracle Council multisig wallet with 10,000 THALES budget to be used to reward successful disputes.


### Duties of Oracle Council
Oracle Council has to resolve raised disputes during a market positioning or maturity phase.
The oracle council does this by having 3 out of 4 members opt for the same resolution on the smart contract directly.  
Oracle Council commits to resolve disputes within 24h, otherwise the council as a whole or individual members could be relieved at the discretion of Thales council.  

Thales Council needs to maintain the guidelines for market creation and keep active communication with community asking for feedback about potential markets to create.

### Market Creation   


Anyone can create a market. When creating a market, the creator has to put up a bond of 100 THALES.  
When creating a market the following parameters have to be provided:  
- Market question (String up to 100 characters)
- Market data sources (String up to 100 characters, can basically be a url linking to a page that will show the result on maturity)
- An array of positions participants can assume (up to 5 positions supported of type String)
- End of positioning phase (timestamp)
- Strike date (timestamp)
- Type:  
          - `Fixed Ticket` (same ticket price for anyone), needs amount to be specified  
          - `Open Bid`  
          - Placeholder for more types that will be in additional TIPs
- Withdrawals allowed

As soon as a market is created it is considered in positioning phase and open to participants to bid and position.

Each bid is subject to a total fee of 2%, out of which 1% goes to the market creator and 1% towards the Safe Box. The fees are only paid out in case of a successful market resolution.  
If allowed, withdrawals are subject to a total 6% fee. 3% paid to the market creator and 3% towards Safe Box. These fees are paid within the withdrawal transactions.  

Market creation will be reverted on contract side if the following is not adhered to:
- Market question is not blank   
- There are a minimum of 2 positions and those are not blank
- Length of positioning phase has to be at least 8h
- Strike date is after end of positioning phase



Every market must be created according to the following guidelines. Not adhering to these guidelines can be a subject of a dispute:
- Market question has to be precise and free of any ambiguity
- The list of available positions has to be mutually fully exclusive and capture the full range of potential outcomes
- End of positioning phase has to be at least 1h before the event actually starts
- Strike date has to be at least 1h after the event is expected to end
- The market question should not have an option to become obsolete or resolved before the end of positioning
- No morbid, racist, death related markets or otherwise malicious markets are allowed and will be disputed and slashed


### Positioning phase
During the positioning phase participants pay the fixed entry bid in case of `Fixed Ticket` markets or put up custom sized bid in case of `Open Bids` markets.  

For `Fixed Ticket` market one wallet can buy only one ticket and choose a single position. The position can be changed during positioning phase as many times as that participant wishes.  

For `Open Bid` market one wallet can enter multiple bids and spread the bids across multiple positions. To reposition, they have to first pull the bid from a position and then choose to deposit it into a new position.

### Disputes in positioning phase
Anyone can dispute a market while in positioning phase. To open a dispute the wallet raising the dispute needs to put up 100 THALES as a bond.
On raising the dispute, the person disputing the market inputs the reason for the dispute as string (up to 100 characters).  
The number of open disputes on a market is not limited, but duplicating disputes can lead to a slash for the wallet raising the duplicated dispute.

Apart from disputes about not following the guidelines one can also raise a dispute for every onforeseen event that causes the market to become obsolete, e.g. a game is postponed. 

Oracle council is the body resolving the disputes. 
An open dispute does not affect the market while its been processed (buy-in and positioning still goes on unaffected).

Oracle council can choose the following options to resolve a dispute:
- `Accept the dispute` in which case the market is closed and everyone can claim the full refund from the market. This resolution is split into two sub-resolutions depending on whether a slash will occur:
    - `Accept the dispute and slash the creator` The wallet that opened the dispute gets the bond back and the bond of the creator
    - `Accept the dispute but do not slash the creator` The wallet that opened the dispute gets the bond back and additional 100 THALES from Oracle Council budget 
- `Refuse the dispute` with two sub-resolutions 
    - `Refuse the dispute and slash the wallet that raised it` The bond goes towards Oracle council budget 
    - `Refuse the dispute but do not slash the wallet that raised it` The wallet that made the dispute gets the bond back
    
Bonds are intended to ensure good behaviour, but are not meant to be punitive. Its within the autonomy of Oracle Council to decide if there was irresponsibility of malice when deciding if a certain bond should be slashed.


### Maturity phase

Once the market hits maturity phase the market creator has 24h to resolve a market.  

If he fails to do so in the given time, the market is open for anyone to resolve the market, but that wallet has to put up 100 THALES bond.  
If there are no disputes to the outcome, the wallet that resolved the market gets the bond of the creator.

In addition to all positions listed on the market creation, there is a default position available to select when resolving a market which is called `Cancelled`.  
Resolving a market with this position will allow anyone who bid on the market to claim a full refund.  

Once a market has been resolved, there is 24h window for anyone to raise a dispute on the market outcome.
This dispute has to have a `reasonForDispute` string and the proposed winning position result.
 
The Oracle council reviews the dispute and can decide the following:
    - `Accept the dispute` in which case the market is now resolved with the proposed position within the dispute. Two subtypes are:
        - `Accept the dispute and slash the resolver` The wallet that made the dispute gets the bond of the resolver. If the resolver is not the market creator, the market creator bond goes to the Oracle Council budget.
        - `Accept the dispute but do not slash the resolver` The wallet that opened the dispute gets the bond from creator if the resolver was not the creator, or from the Oracle Council budget if the resolver was the creator.  
    - `Refuse the dispute` with two sub-resolutions 
        - `Refuse the dispute and slash the wallet that raised it` The bond goes towards Oracle council budget 
        - `Refuse the dispute but do not slash the wallet that raised it` The wallet that made the dispute gets the bond back

If 24h has passed since the market was resolved and at least 2h since the last dispute was closed, the market is formally resolved.   

Oracle council can not set the result of a market themselves, they can only accept a correct result from a dispute.


### Oracle Council backstop
Bonds serve as deterrent for bad actors while creating, resolving and disputing markets, but what if oracle council decides to collude?
Protocol DAO will maintain the possibility to pause either individual markets or all markets if it detects any suspicious behavious and inform Thales Council about malpractice of Oracle Council members.
Thales Council can then choose to replace individual council members with the next candidate per voting tally, or call a new election if needed.

Treasury DAO will set aside 500k THALES as insurance fund for all market participants.       
       

## Rationale
 
TBD
 
## Test Cases
 
###Example1
WalletA creates a market "Who will win the Super Bowl LVI", with positions `Rams` or `Bengals` and a `Fixed Ticket` type with 50 sUSD ticket.
The market parameters are all correctly set (positioning ends before the game starts, strike is at least 5h after the game is scheduled to start).
The creator resolves the market correctly within 24h hours. There are no disputes in the following 24h so those that positioned on the winning side can redeed their winnings.

###Example2
WalletB creates a market "Will Lakers win the NBA Championship 2022-23" with positions `Yes` and `No`.   
End of positioning is set at end of regular season.  

While this market might look ok at first glance, it can be disputed because Lakers have not secured a play-off spot and thus the market might become obsolete before the end of positioning.  


###Example3
WalletC creates a market "How many goals will be scored in the match Liverpool vs Manchester United" with positions "0-2", "3-4" or "5+".  
All dates are set correctly, end of positioning is before the match starts and market can be resolved 3h after the match start time.  
The creator resolves the market correctly within 24h hours. There are no disputes in the following 24h so those that positioned on the winning side can redeed their winnings.

This is an example of a market with more than 2 positions, but only one position can be the winning one. 
 
 
## Implementation
 
TBD
 
## Copyright
 
Copyright and related rights waived via CC0.
