
| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-89 | New overtime feed and Rundown improvements | Draft | @danthales | Add Apex feed support to overtime to support MotoSports. Improve Rundown consumer. | https://discord.gg/thales | 2022-09-12

## Simple Summary

This TIP entails Thales protocol to add support for Apex146 [feed](https://market.link/nodes/Apex146/integrations).   
It also includes other improvements to overtime protocol listed in #specification  

## Motivation  
Overtime aims to continuously upgrade its offer in supportd sports and markets. [Apex](https://www.apex146.com/) has reached out to Thales CCs to enquire if there is interest in using the specialized data for created F1 and MotoGP markets.  
After feasibility and integration tests that CCs have conducted, I am proposing that we make these markets part of Overtime offer.  

Adding more feeds and data providers also improves the decentralization and diversification aspect of Overtime, as in Rundown API no longer not being a single point of failure for the whole platform.  

## Specification
###Apex integration
Create a new contract called ApexConsumer that will call chainlink jobs serving data from Apex. These contracts will be able to create markets and resolve markets on overtime.  
Apex supports a number of sports and bet types, but we will start with F1 and MotoGP.  
Initially only h2h (head to head) bet type will be supported. For each F1 or MotoGP Apex will prepare 10 head to head markets (1 driver vs another), where the odds are calculated based on their algorithm and empirical data.  

During the beta testing of this new feed, only whitelisted addresses will be able to interact with the ApexConsumer contract. Once a few races have concluded and we get more comfortable with the robustness of the feed, the whitelisting can be removed.  

This TIP entails Protocol DAO to utilize other available bet types and sports from Apex feed if there is community interest for those.  

###Rundown improvements

Based on our observations working with Rundown feed last few weeks, we are proposing a number of improvements to ensure a more robust experience for overtime users:  
    - For UFC: Upgrade the rundown consumer contract so that it automatically cancels markets if UFC fighters change and create a new market for the new fight  
    - For all sports: Introduce logic that check if the start of the market has been changed on the data side since the market has been created. If yes and if the new time is in the future, update the time. If the new time is in the past, pause the market.  
    - Introduce a list of whitelisted addresses that can pause markets in case of emergencies.        


## Implementation
https://github.com/thales-markets/contracts/tree/apex-integration

## Copyright

Copyright and related rights waived via CC0.
