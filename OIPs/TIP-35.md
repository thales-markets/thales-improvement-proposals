| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-35 | Formalize Oracle Council | Vote Pending | Danijel (@danijelthales) | Define Oracle Council rules and duties | https://discord.gg/rPpPcMXSeU | 2022-03-24 

## Simple Summary
 
This TIP is to describe the new DAO elected by THALES stakers which will serve to govern Exotic Markets per TIP-28
 
## Motivation
TIP-28 introduces Exotic Parimutuel Positional Markets which are to be governed by Oracle Council. As the TIP itself is quite complex and needs a bit more fine tunning, this TIP aims to formalize Oracle Council so that the nominations and elections can be started. 

## Specification
 
Form a Thales Oracle Council of 5 members elected by THALES stakers.  
  
The nominations and elections process are as established before for the Thales Council.
  
Stipend is hereby increased to 2000 THALES both Oracle and Thales council members.  

First epoch will be shorter to align it with regular council epoch going forward, so it will end 30th of June 2022.    

Thales Treasury DAO will fund Oracle Council multisig wallet with 10,000 sUSD budget to be used to reward successful disputes.


### Duties of Oracle Council
Oracle Council has to resolve raised disputes during a market positioning or maturity phase to maintain fairness for market pariticipants and to ensure the correct result is set on a given market.  

The oracle council does this by having 3 out of 5 members opt for the same resolution on the smart contract directly.  
  
Oracle Council commits to resolve disputes within 24h, otherwise the council as a whole or individual members could be relieved at the discretion of Thales council.  

Oracle Council needs to maintain the guidelines for market creation and keep active communication with community asking for feedback about potential markets to create.  

Oracle Council maintains a list of tags which can be assigned on markets.  

### Initial Guidelines for market creation
Every market must be created according to the following guidelines. The list of guidelines is preliminary and after Oracle Council is voted in its their duty to complement it and update it as new edge cases are discovered.  
Not adhering to these guidelines can be a subject of a dispute:
- Market question has to be precise, written in English language and free of any ambiguity
- Market has to be mainstream and verifiable via data sources parameter.
- The list of available positions has to be mutually fully exclusive and capture the full range of potential outcomes
- End of positioning phase has to be before the event actually starts
- End of positioning must not be more than 1 month into the future
- Market resolution/question should not be more than 2 months into the future
- The market must not be theoretically resolvable with any of the offered positions before the end of positioning
- No morbid, racist, death related markets or otherwise malicious markets are allowed and will be disputed and slashed
- The market has to be linkable to at least one of the offered tags maintained by Oracle Council
- No duplicated markets should be created. Its ok to create more markets around the same event, but with a different sentiment (different question and/or positions).  


### Initial Tags available for market creation
- Sport
- Politics
- Crypto
- E-Sports
- Pop Culture
- NFTs
 
## Copyright
 
Copyright and related rights waived via CC0.
