| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-60 | Sport AMM  | Draft | gruja.work (@gruja.work), KirilA (@kirilaa), Red (@Red-Thales) | This TIP proposes to implement and release a Sport AMM | https://discord.gg/8bzFdpGTrp | 2022-07-01

## Simple Summary

This TIP proposes to implement and release a Sport AMM suite of contracts. This captures positional markets for sports games that are created from a Chainlink sports data [oracle](https://market.link/nodes/TheRundown/integrations) and an AMM contract that supports trading on such markets.

The TIP will outline the oracle supported sports and leagues, the specification behind the novel Sport AMM, as well as the motivation behind the Sport AMM release.

## Abstract

Sports AMM is an AMM dedicated for trading positional sport markets using Chainlink feeds for price calculation. 
For each market, there are two or three positions/outcomes (home win, away win, or draw). 
Additionally, a game can be cancelled which in that case the last provided odds are used to exercise the users' positions.

It's the vision of the Thales Protocol to support Sport markets and the sport AMM integration. This TIP proposes a format that can achieve this in a decentralized manner with the support of Chainlink data feed.

## Motivation

In the summer of 2020, Thales built markets around the Olympic medal ranking of the Olympics in Tokyo. The markets were supported by Chainlink oracles and we were able to create a unique product within Thales' offering. The markets were successful and the results reliable, this was a first for many within the community where they got the ability to watch and trade on their favourite sporting event in a decentralised way. 

Although successful, the orderbook mechanism and gas costs on Ethereum mainnet weren’t an ideal combination when dealing with sports markets making for an inconvenient user experience. Now, with the convenience of layer2 roll-ups, the innovation behind our Sport AMM, and the proven reliance or Chainlink oracle it is in Thales and its community best interest to launch its Overtime platform.

The sport AMM is one of the most anticipated products built on Thales and will allow users to position themselves based on their favourite sports teams through the whole season. The Overtime platform will be able to offer sports such as soccer, football, baseball, hockey, and basketball. Over the next few months we will be growing our product to include more sports, and deliver from more API. Potential sports that might be included: UFC, Formula 1, Moto GP and more.

The sport AMM product also has the opportunity to showcase the usage of blockchain technology to one of the biggest industries in the world. The market has reached a maturity point with an opportunity for us to tap into mass adoption. Our goal to gamify DeFi stays the same, Thales keeps building and brings you Overtime, the first decentralized sport AMM.

## Specification

The Sports AMM enables creation of markets, positions trading and exercising user positions. 
Hence, the workflow of the SportsAMM is divided in three parts:

- Market creation
- AMM trading
- Market resolution

The Sports AMM smart contract is a modified version of the Thales AMM to support three outcomes ([TIP-11](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-11.md), [TIP-30](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-30.md)).
Each market smart contract is a modified version of the Positional market. More in technical details section.

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

Protocol DAO would like to reserve the right to enable sports 1 by 1 as the product matures and becomes more battle tested.

### AMM trading

Each market is open for AMM trading after it is created. 
The AMM trading finishes when the game starts (or a fixed period of time before the game starts, e.g. 10 minutes before the game). 
Each market offers buying/selling of positions:
- HOME and AWAY - for two positional markets (basketball)
- HOME, AWAY and DRAW - for three positional markets (soccer)

The price of each position is calculated using the Chainlink odd feeds and the price impact upon each trade. The price impact is determined by the minimum/maximum skrew impact set in the Sport AMM contract. This mechanism motivates traders to jump in early on without delay. 

The price per position is in the range from 0 to 1.  
For example, if the price of the HOME team to win is 0.55, it means: **a user to buy 1 HOME position needs to pay 0.55 sUSD.**

Each game is capped with a default cap. This means if the traders continously buy from AMM only the HOME position, the trading for the HOME position goes out of liquidity once the default cap is exceeded.

The Sports AMM allows for multi-collateral trading by seamless use of sUSD, DAI, USDC, USDT as in [TIP-58](https://github.com/thales-markets/thales-improvement-proposals/blob/main/TIPs/TIP-58.md).

### Market resolution

Each market can be resolved with one of the two/three outcomes or cancelled. 
Users possesing winning positions are eligible to exercise and receive payment in sUSD. 

**1 WINNING OPTION = 1 sUSD**

In case of cancellation, each user can exercise its position and receive sUSD according to the last recorded price per option.  
For example: *if the user poses 1 HOME option, for which the last price per HOME option is 0.55, the user will receive 0.55 sUSD in case of cancellation.*

## Technical details

Based on CL sports data, the system fetches the games and creates, resolves, and pulls odds. The system then creates markets, updates the price per position automatically, and resolves markets.

Sports that are supported by Sport AMM are:

Baseball, Football, Soccer, Hockey, and Basketball.

Due to the nature of our launch schedule, the Sport AMM will first focus on the MLB & MLS leagues as these two are ongoing and match our release schedule. As the other leagues start their season over the next few months they will be integrated within. The current list of leagues is also up to change and we are likely to obtain major tournaments integrated as they approach the start date.

Based on the requirements, there are needs for the following technical specifications:

1) *Wrapper contract* - is part of fetching games from chainlink sports data, it contains fetching games, results, and odds from CL, and that data is transferred to the consumer contract. Wrapper contract will be called by bots that execute those fetching functions:

    - `requestGames` - this function is called when games need to be created (input params are the date of the game and sports id), the function is called for each sport 7 days in advance, two times per week
    - `requestGamesResolveWithFilters` - this function is called when games need to be resolved and it is called when the game has ended (the calculation is based on the start of the game, and the type of sport, now it is set to 3 hours from the start of the game, regardless of a sport)
    - `requestOddsWithFilters` - this function is called when odds need to be pulled. Each game's odds if the odd changed by 2% from priveous stored odd.

    This contract will have buy-in on each request which amount is set into `payment` variable user/bot needs to pay(for now CL on OP Main request is 0.3 LINK). 
    Also, all those methods can be called manually but then user needs to pay amount of each request. Besides fetching functions, the contract will have the following methods which can be called only if you are the contract owner:

    - `setOracle` - setting oracle from CL if change is needed
    - `setConsumer` - set consumer address if needed
    - `setLink` - set new LINK address
    - `setPayment` - set new payment amount for each request

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
    - `pauseOrUnpauseMarketManualy` - the pause/unpause of a game based on market id and flag, only whitelisted address can call this function
    - `pauseOrUnpauseGameManualy` - the pause/unpause of a game based on game id  and flag, only whitelisted address can call this function
    - `getNormalizedOdds` - a function that does a calculation based on moneyline odds to transfer them into normalized odds to a 100%
    - `removeFromResolvedQueue` - a function that which removes game from resolved queue 
    - `removeFromCreatedQueue` - a function that which removes game from created queue 
    - `removeFromUnprocessedGamesArray` - a function that which removes game unprocessed array

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

4) *SportPositionalMarketManager* - is a contract responsible to relay creation of a game market or resolution of a game market. The market creation is relayed from `Consumer` to the `SportPositionalMarketFactory`. Each game is created as a market clone of `SportPositionalMarket`. Each game market position is a ERC-20 `SportPosition` contract.   
    The main contract functions are:
    - `createMarket` - creation of a game market based on the game details. Only Therundown consumer can create a market. 
    - `resolveMarket` - resolution of a game market.
    - `expirveMarkets` - expire old markets, so they are not considered *active*.
    - `isActiveMarket` - check if a game market is active.
5) *SportPositionalMarketFactory* - is a contract responsible for creation of game markets - `SportPositionalMarket`.  
    The main contract functions is:
    - `createMarket` - creation of a game market based on the game details. Only Therundown consumer can create a market. 
6) *SportPositionalMarket* - is the game market contract.
    The main contract functions are:
    - `initialize` - all the game market parameters are initialized, and each `SportPosition` is created as ERC-20 position. 
    - `mint` - mints new tokens for each position.
    - `burnOptions` - burn number of position tokens.
    - `resolve` - resolves the game market.
    - `exerciseOptions` - burns user's tokens, and sends back to the user an amount of sUSD based of the caller holding of winning position tokens. Example: *if the user has 100 HOME, and HOME is the winning resolved position, the user receives 100 sUSD.*
7) *SportPosition* - is a position contract which represent a single position of a given game market. For example, a *HOME position for game market X vs. Y*. 
    The main contract functions are:
    - `mint` - creation of new position tokens.
    - `exercise` - burning user tokens.
8) *SportsAMM* - is the main contract for buying/selling positions for active markets
    The main contract functions are:
    - `isMarketInAMMTrading` - checks if a game market is eligible for AMM trading.
    - `availableToBuyFromAMM` - checks the available position tokens that can be bought from AMM for a specific game market.
    - `availableToSellToAMM` - checks the amount of position tokens that can be sold to the AMM for a specific game market.
    - `getMarketDefaultOdds` - obatins the odds for each position (including skew impact) for a specific game market.
    - `buyFromAmmQuote` - returns the amount of sUSD required to pay for a specified number of positional tokens for a specific game market.
    - `sellToAmmQuote` - returns the amount of sUSD that a user would receive for seling a specified number of positional tokens for a specific game market.
    - `buyFromAMM` - buying a specified number of positional tokens from AMM for a specific game market.
    - `sellToAMM` - selling a specified number of positional tokens to AMM for a specific game market.

    Main variables:
    - `defaultCapPerGame` - default cap in sUSD per game market - set to 1000 sUSD.
    - `minSupportedOdds` - minimal supported oracle odds - set to 0.1.
    - `maxSupportedOdds` - maximum supported oracle odds - set to 0.9.
    - `min_spread` - minimal skew impact - set to 1%.
    - `max_spread` - maximum skew impact - set to 5%.
    - `safeBoxImpact` - safeBox percentage - set to 1%.


## Rationale

The sport AMM implementation is a novel idea built on Thales.  The AMM allows users to trade sport markets with deep liquidity. The product being fully on-chain enables our users to engage in their favourite games and mega sport events in a truly decentralised manner. With this TIP Thales keeps pushing the boundaries of gamified DeFi.

## Test Cases

 - Buy and sell home team options
 - Buy and sell away team options
 - Buy and sell draw options
 - Buy and keep options until maturity
 - Exercise mature options
 - Sell unbought options
 - Buy options with insufficient funds
 - Buy options for a game that has started
 - Sell options for a game that has started
 - Exercise options for a game that has not started / is in progress
 - Exercise losing options
 - Buy options without approval
## Implementation

Implementation is on a [link](https://github.com/thales-markets/contracts/tree/main/contracts/SportMarkets)

### Variables

1. Default cap in sUSD per game market = 1000 sUSD.
2. Minimal supported oracle odds = 0.1.
3. Maximum supported oracle odds = 0.9.
4. Minimal skew impact = 1%.
5. Maximum skew impact = 5%.
6. SafeBox percentage = 1%.

Protocol DAO would like to keep the discretion to raise sUSD per game as the product matures without an additional explicit TIP.
    
## Copyright

Copyright and related rights waived via CC0.
