| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-60 | Sport AMM  | Draft | gruja.work (@gruja.work), KirilA (@kirilaa), Red (@Red-Thales) | This TIP proposes to implement and release a Sport AMM | https://discord.gg/8bzFdpGTrp | 2022-06-17

## Simple Summary

This TIP proposes to implement and release a Sport AMM. Sports AMM is a positional market for sports games that are created from a Chainlink sports data [oracle](https://market.link/nodes/TheRundown/integrations)

@Red please add 

## Abstract

Sports AMM is an AMM dedicated for trading positional sport markets using Chainlink feeds for price calculation. 
For each market, there are two or three positions/outcomes (home win, away win, or draw). 
Additionally, a game can be cancelled which in that case the last provided odds are used to exercise the users' positions.

@Red please add 

## Motivation

@Red please add 

## Specification

The Sports AMM enables creation of markets, positions trading and exercising user positions. 
Hence, the workflow of the SportsAMM is divided in three parts:

- Market creation
- AMM trading
- Market resolution

### Market creation

This is the starting phase when markets are created from games offered by the [Chainlink end-point](https://market.link/nodes/TheRundown/integrations).
The games are organized in `sportIds` which represent a league competition of given sport, not only sport in general. 
Current list of supported `sportIds` (or leagues):
- NCAA Men's Football: 1 (American football)
- NFL: 2 (American football)
- MLB: 3 (Baseball)
- NBA: 4 (Basketball)
- NCAA Men's Basketball: 5 (Basketball)
- NHL: 6 (Hockey)
- WNBA: 8 (Basketball)
- MLS: 10 (Soccer)
- EPL: 11 (Soccer)
- Ligue 1: 12 (Soccer)
- Bundesliga: 13 (Soccer)
- La Liga: 14 (Soccer)
- Serie A: 15 (Soccer)
- UEFA Champions League: 16 (Soccer)

The market creation starts with fetching games for each `sportId` each day from the end-point. The fetched games are stored on-chain.
Next, markets are created from every fetched game. Each game is a positional market with two or three positions depending on the possible outcomes of the game. For e.g., in a basketball game there are two outcomes: home win and away win, but in a soccer game there are three possible outcomes: home win, away win, and a draw. 
The created market becomes active and eligible for AMM trading. 

### AMM trading

### Market resolution


Based on CL sports data, the system fetches the games and creates, resolves, and pulls odds. The system then creates markets, updates the price per position automatically, and resolves markets.

Sports that are supported by Sport AMM are:

@Red please add the sports and elaborate

Based on the requirements, there are needs for the following technical specifications:

1) *Wrapper contract* - is part of fetching games from chainlink sports data, it contains fetching games, results, and odds from CL, and that data is transferred to the consumer contract. Wrapper contract will be called by bots that execute those fetching functions:

    - `requestGames` - this function is called when games need to be created (input params are the date of the game and sports id), the function is called for each sport 7 days in advance, two times per week
    - `requestGamesResolveWithFilters` - this function is called when games need to be resolved and it is called when the game has ended (the calculation is based on the start of the game, and the type of sport, now it is set to 3 hours from the start of the game, regardless of a sport)
    - `requestOddsWithFilters` - this function is called when odds need to be pulled. Each game's odds will be pulled every 6 hours, except on game day, when will be pulled each hour.

    This contract has LINK inside which will be used to pay for the CL requests. 
    Also, all those methods can be called manually but only from whitelisted addresses, which prevents LINK from being spent by calling methods from some untrusted address. Besides fetching functions, the contract will have the following methods which can be called only if you are the contract owner:

    - `addToWhitelist` - adding address to whitelist
    - `setOracle` - setting oracle from CL if change is needed
    - `setConsumer` - set consumer address if needed
    - `withdrawLink` - if we need to change the contract this function will withdraw LINK from the contract 

2) *Consumer contract* - is part of the processing pipeline and store games that are sent from the wrapper contract. This contract is a proxy contract, and stores all data from games, and also calls the queue contract to store data that are needed for the processing part of the results and odds. Consumer calls the market creator to create/resolve/update odds based on which request is sent from the wrapper. In this contract, there is a method for manual resolution/cancellation of games. Also, all those methods can be called only from the wrapper address or a whitelisted address. This contract is going to send normalized odds based on moneyline (American) odds which we get from a CL.

    The main functions of the consumer contract are:

    - `fulfillGamesCreated` -  wrapper can only call the function which fills the contract with games that are fetched from CL
    - `fulfillGamesResolved` - wrapper can only call the function which fills the contract with game results that are fetched from CL
    - `fulfillGamesOdds` - wrapper can only call the function which fills the contract with game odds results that are fetched from CL
    - `createMarketForGame` - creates market for a certan game id 
    - `resolveMarketForGame` - resolves the market for a certain game id 
    - `resolveMarketManually` - resolving of a game based on market id and outcome, only whitelisted address can call this function
    - `resolveGameManually` - resolving of a game based on game id and outcome, only whitelisted address can call this function
    - `cancelGameManually` - the cancellation of a game based on game id and outcome, only whitelisted address can call this function
    - `cancelMarketManually` - the cancellation of a game based on market id and outcome, only whitelisted address can call this function
    - `getNormalizedOdds` - a function that does a calculation based on moneyline odds to transfer them into normalized odds to a 100%

    Owner functions:

    - `addToWhitelist` - adding address to the whitelist
    - `setSupportedSport` - setting a new sport that is supported by markets
    - `setSupportedResolvedStatuses` - setting supported resolve statuses of a game
    - `setSupportedCancelStatuses` - setting supported cancel statuses of a game
    - `setwoPositionSport` - adding a sport if the sport is two positional (like NBA, no draw allowed)
    - `setSportsManager` - setting new sports manager if needed 
    - `setWrapperAddress` - setting new wrapper address if needed
    - `setQueueAddress` - setting new queue address if needed


3) *GamesQueue contract* - is a contract part of a processing pipeline which is a pure store contract that contains all games that are created, and based on that queue is pulling odds. Game resolving is working by finding which game is needed to be processed. This contract is also a proxy contract.

    The main functions in the games queue contract and which can be called only from a consumer contract are:

    - `enqueueGamesCreated` - populate queue when the game is created
    - `dequeueGamesCreated` - remove the game from the queue when the market is created based on the id
    - `enqueueGamesResolved` - populate queue when the game is resolved
    - `dequeueGamesResolved` - remove the game from the queue when the market is resolved based on id
    - `removeItemUnproccessedGames` - removing the game from a list of games that is resolved

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
