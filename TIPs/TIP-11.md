| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-11 | Deploy an AMM implementation to ensure initial liquidity for Thales Markets on Optimism layer 2 | Draft | Danijel (@dgornjakovic) | Describe the AMM contract that Thales would use to provide some out of the box liquidity to Thales Markets | https://discord.gg/8bzFdpGTrp | 2021-12-10
 
## Simple Summary
 
This TIP proposes to implement and release a Thales AMM contract with funded liquidity from treasury with sUSD on OP mainnet, and for it to be used to provide liquidity for Thales Markets.
 
## Abstract
 
MVP implementation of Thales involved just peer to peer trading based on limit orders. While L1 gas costs were definitely a reason for lack of trading volume, we do acknowledge most DeFi users are more accustomed to an AMM approach and UX. We feel Thales protocol needs to work iteratively to deliver an AMM feature that can meet the demand for Thales Binary Options.  

This TIP proposes to deploy a Version 1, or Minimal Viable Product version of the AMM that will be based on Black-Scholes pricing algorithm and will use a spread and price impact logic with an addition of cap per market to minimize its exposure. The said AMM is to be monitored and iteratively improved so that eventually the cap is increased if not removed and users can deposit into the AMM as liquidity providers and earn fees+THALES rewards.

This TIP also proposes to deploy a `burn` functionality to BinaryOptionMarket.sol contract that allows for burning of sLONG and sSHORT options tokens to withdraw sUSD from a respective Thales market of said options tokens.
 
## Motivation
 
A number of protocols have enquired about integrating with Thales to hedge using binary options. However, all those protocols require guaranteed liquidity.  

DeFi users are not as accustomed to using limit orders as CEX users. Limit orders in case of binary options also require some overhead as the price of binary options can be very volatile and ultimately the said limit orders have to be frequently monitored and managed.  

While L2 is definitely going to make trading with limit orders a lot cheaper, we want to ensure there is liquidity present in each market as soon as the market is created. Order making bots were deployed on L1 mainnet, however those required a lot of overhead. An AMM contract is much more convenient to do this job, while requiring no overhead per market.
  
Due to the volatile nature of binary options a traditional DEX AMM solution is not well suited due to potential impermanent loss. Instead, a custom-built AMM can leverage the specifics that binary options carry and use existing Thales Contracts to dynamically price, mint, burn, buy or sell sLONG or sSHORT options.
 
## Specification

This TIP entails the Protocol DAO to deploy a `burn` functionality into the [BinaryOptionMarket.sol](https://github.com/thales-markets/contracts/blob/main/contracts/BinaryOptions/BinaryOptionMarket.sol) contract so to allow market participants to burn sLONG and sSHORT options tokens in 1:1 ratio and subsequently withdraw sUSD from the respective market equal to number of sLONG+sSHORT pairs burned for said market.
 
This TIP also entails the Protocol DAO to implement and deploy a [ThalesAMM.sol](https://github.com/thales-markets/contracts/blob/ThalesAMM/contracts/AMM/ThalesAMM.sol) contract with the following methods:  

####VARIABLES:  

`capPerMarket` // maximum that can be risked on a certain market    
`impliedVolatility` // input variable for BlackSholes pricing, for now we have to set it manually, but Chainlink might deliver an oracle for it.       
`min_spread` // AMM needs to add a price impact to its buy and sell offers to offset for taking on all of the risk  
`max_spread` // Maximum price impact    
`minimalTimeLeftToMaturity` // AMM will not be supporting markets that are in the final hours until maturity due to timestamp delay on L2 and just general frontrunning risk. Currently set to 2h.    
 
#####READ:  
`spentOnMarket` // How much is currently spent on a given market    
`availableToBuyFromAMM` // How many options can the AMM currently sell for a given market and a position (LONG vs SHORT)    
`buyFromAmmQuote` // Get a buy quote for a given market, position and amount  
`buyPriceImpact` // Get the buy price impact for a given market, position and amount  
`availableToSellToAMM` // How many options can the AMM currently buy for a given market and a position (LONG vs SHORT)    
`sellToAmmQuote` //  Get a sell quote for a given market, position and amount  
`sellPriceImpact` // Get the sell price impact for a given market, position and amount  
`price` // Calculated price for a given market per BlackScholes  
`calculateOdds` // Calculated odds (0 to 100) for a given market per BlackSholes  
`isMarketInAMMTrading` // Check if market is active in trading and does not mature in less then minimalTimeLeftToMaturity     
`canExerciseMaturedMarket` // Check if the AMM can exercise options on a given market  
  
#####WRITE:
 
`buyFromAMM` // buy options from the AMM for the selected market and position and amount    
`sellToAMM`// sell options to the AMM for the selected market and position and amount  
`exerciseMaturedMarket`// exercise AMM options for a given market, to be maintained by a keeper  
 
#####SETTERS:  
`setMinimalTimeLeftToMaturity`    
`setMinSpread`  
`setMaxSpread`  
`setImpliedVolatility`    
`setCapPerMarket`   
`setPriceFeed`  

## Rationale
 
As the AMM is taking all of the risk and is experimental in its nature the main focus is to limit the possible losses until the contract is battle tested. To ensure this, the variable capPerMarket is the focal point of how much liquidity is available on a certain side of a Market. The AMM will never expose itself to more than the cap for a given market (examples below).
The price is determined using the Black-Scholes algorithm for options pricing. However, implied volatility is the dominant parameter for this algorithm, and for crypto it is still kind of experimental. The value for implied volatility can range from 50% per year to 150% per year. We have to choose a value to start with and adapt based on the AMM behaviour we see in the first few months of testing it. We expect Chainlink to eventually have a price feed for implied volatility at which time we will use that in the AMM contract.
To offset some of the risk, variables minSpread and maxSpread are used. If a potential buyer is trying to buy all available Long options on a market he will get maxSpread applied to pricing. However, the AMM also uses those variables to balance its exposure, so if it's currently exposed only to LONG options, it will offer SHORT options at minimal price up until the amount of LONG and SHORT options in the AMM is identical.
AMM required a burn method to be added to the contract BinaryOptionMarket so that it can get sUSD every time it has both LONG and SHORT options on a given market. This enabled much more flexibility and additional liquidity to the AMM.

 
## Test Cases
 
1. New market, LONG price is 30c per market, capPerMarket is 1000sUSD, assume no slippage, user wants to buy maximum LONG options  
  
        AMM can sell 1428.4 LONG options because:
        1428.4*0.3=428.4 sUSD
        AMM has to mint an equal amount of LONG and SHORT options to have liquidity to sell, so the AMM puts 1428.4 sUSD into minting but gets 428.4 sUSD from the sell transaction, so its exposure is 1000 sUSD.
[case 1](https://raw.githubusercontent.com/MamercusOfMiletus/shemeTIP/main/Desktop%20-%201.png)

2. New market, LONG price is 30c per market, capPerMarket is 1000sUSD, assume no slippage, user wants to sell maximum LONG options
  
        AMM can risk up to 1000sUSD, so the amount of options it can buy is 1000/0.3=3333

3. Existing market, LONG price is 30c per market, capPerMarket is 1000sUSD, but 500sUSD already spent, so 500sUSD left, AMM has a skew of 100 SHORT options, assume no slippage, user wants to sell maximum LONG options  

        Things get more complex when the AMM already has some options. Since the user wants to sell LONG options and the AMM has some SHORT options, AMM can burn the bought LONG options to get sUSD back, so for 100 options:
        AMM buys 100 options for $30, burns them and gets $70 back to spend
        AMM now has 570sUSD to spend so it can buy 1900 more options cause 570/0.3=1900
        In total the AMM can buy 100 (that it will burn) + 1900= 2000 LONG options
 
4. Existing market, LONG price is 30c per market, capPerMarket is 1000sUSD, but 500sUSD already spent, so 500sUSD left, AMM has a skew of 100 LONG options, assume no slippage, user wants to buy maximum LONG options  

        AMM already has 100 LONG options, so it can sell that straight away and it gets $30 back, so it can now spend 530sUSD.
        AMM can risk up to 530sUSD now
        AMM can sell 757 LONG options cause 757*0.3=227=>757-227=530
        With the 100 it already sold, the AMM can sell a total of 857

 
## Implementation
 
https://github.com/thales-markets/contracts/blob/ThalesAMM/contracts/AMM/ThalesAMM.sol
 
## Copyright
 
Copyright and related rights waived via CC0.
