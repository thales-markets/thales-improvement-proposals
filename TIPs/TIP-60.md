| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-60 | Sport AMM  | Draft | gruja.work (@gruja.work), kirilA (@kirila), Red (@Red-Thales) | This TIP proposes to implement and release a Sport AMM | https://discord.gg/8bzFdpGTrp | 2022-06-17

## Simple Summary

This TIP proposes to implement and release a Sport AMM. Sports AMM is a positional market for a sport games which is created from a Chanlink sport data [oracle](https://market.link/nodes/TheRundown/integrations)

@Red please add 

## Abstract

Sports AMM is a positional market for a sport games. In each market there is a two positional or three positional sports game (home win, away win or draw).

@Red please add 

## Motivation

@Red please add 

## Specification

Based on a CL sports data, system grep games from it and create, resolve and pull odds. System then create markets, update automaticlly price per position and resolve markets.

Sports that are supported by Sport AMM are:

@Red please add and elaborate

Based on a requrement there is a need for next technical specification:

1) *Wrapper contract* - is part of a grapping games from chainlink sports data, it contains grapping games, results and odds from CL, those data is transfered to consumer contract. Wrapper contract will be called from bots which execute those grapping functions:

    - `requestGames` - function which is called when games needed to be created (input params are date of a game and sports id), function is called for each sport 7 days in front two times per week
    - `requestGamesResolveWithFilters` - function which is called when games needed resolved and it is resolved when game is ended (calculation based on a start of game depending on a sport, now it is set 3 hours from starting of a game regardless of a sport)
    - `requestOddsWithFilters` - function which is called when odds needed to be pulled. Each game odds will be pulled on 6h, except on a game day which will be pulled each hour.

    This contract has LINK inside which will be used for pay to CL request. 
    Also, all those methods can be called manually but only from whitelisted addresses, which prevent LINK to be spend by calling methods from some untrusted address. Beside grapping functions, contract will have next methods which can be called only if you are an contract owner:

    - `addToWhitelist` - adding address to whitelist
    - `setOracle` - setting oracle from CL if change is needed
    - `setConsumer` - set consumer address if needded
    - `withdrawLink` - if we need to change contract this function will withdraw LINK from contract 

2) *Consumer contract* - is part of processing pipeline and store dames which are sended from wrapper contract. This contract is a proxy contract, and stors all data from games, and also calls queue contract to stora data which are needed for processing part of a results and odds. Consumer calls market creator to create/resolve/update odds based on which request is send from a wrapper. In this contract there is a methods for manual resolve/cancel of a games. Also, all those methods can be called only from a wrapper address or whitelisted address. This contract is going to sen normalized odds based on moneyline (american) odds which we get from a CL.

    Main functions in consumer contract are:

    - `fulfillGamesCreated` -  wrapper can only call function which fulfill games which are fetched from CL
    - `fulfillGamesResolved` - wrapper can only call function which fulfill game results which are fetched from CL
    - `fulfillGamesOdds` - wrapper can only call function which fulfill game odds results which are fetched from CL
    - `createMarketForGame` - craates market for a certan game id 
    - `resolveMarketForGame` - resolve market for a certan game id 
    - `resolveMarketManually` - resolving of a game based on market id and outcome only whitelisted address can call this function
    - `resolveGameManually` - resolving of a game based on game id and outcome only whitelisted address can call this function
    - `cancelGameManually` - cancel of a game based on game id and outcome only whitelisted address can call this function
    - `cancelMarketManually` - cancel of a game based on market id and outcome only whitelisted address can call this function
    - `getNormalizedOdds` - function that do a calculation based on moneyline odds to transfer them into normalized odds to a 100%

    Owner functions:

    - `addToWhitelist` - adding address to whitelist
    - `setSupportedSport` - setting new sport which is supported by markets
    - `setSupportedResolvedStatuses` - setting supported resolve statuses of a game
    - `setSupportedCancelStatuses` - setting supported cancel statuses of a game
    - `setwoPositionSport` - adding sport if sport is two positional (like NBA, no draw allowed)
    - `setSportsManager` - setting new sports manager if needed 
    - `setWrapperAddress` - setting new wrapper address if needed
    - `setQueueAddress` - setting new queue address if needed


3) *GamesQueue contract* - is a contract part of a processing pipeline which is a pure store contract which has all games that are created, and based on that queue pulling odds and game resolve is working by finding which game is needed to be processed. This contract is also a proxy contract.

    Main functions in games queue contract and which can be called only from a consumer contract are:

    - `enqueueGamesCreated` - populate queue when game is created
    - `dequeueGamesCreated` - remove game from queue when market is created based on id
    - `enqueueGamesResolved` - populate queue when game is resolved
    - `dequeueGamesResolved` - remove game from queue when market is resolved based on id
    - `removeItemUnproccessedGames` - removing game from a list of games that is resolved

    Owner functions:

    - `setConsumerAddress` - setting new consumer address if needed

4) ...

@Kirila please add 


## Rationale

@Red please add 

## Test Cases

@coa @cvija please add

## Implementation

Implementation is on a [link](https://github.com/thales-markets/contracts/tree/main/contracts/SportMarkets)

## Copyright

Copyright and related rights waived via CC0.
