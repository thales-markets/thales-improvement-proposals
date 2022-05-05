| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-30 | Thales AMM v0.3 Update | Implemented | Danijel (@dgornjakovic), padzank(@padzank) | Thales AMM token pricing and skew impact core improvements and parameter changes | https://discord.gg/8bzFdpGTrp | 2022-02-21
 
## Simple Summary
 
Thales AMM upgrade to version 0.3 that includes major improvements to pricing and skew impact mechanism, allowing for a subsequent lowering of strict safety limitation parameters and thus majorly improving UX for traders on the Thales marketplace.
 
## Abstract
 
Initial deployment of the Thales AMM contract introduced a solution for on-demand liquidity of Positional Tokens to Thales traders. First version was launched as a public beta with subsidized liquidity from the Treasury DAO with strict safety limitations of total sUSD risk per market for the AMM, conservative range of Positional Token prices at which the AMM offers liquidity and safe distance to Market Maturity at which the AMM closes on-demand liquidity offering to avoid edge cases with the pricing algorithm super close to Market Maturity. These strict measures were used to offer safe and fair trading to all market participants while sufficient data is being collected for further AMM optimizations and edge case fixes. Even though the AMM performance was a massive success so far, certain small design flaws and edge cases surfaced in regards to Skew Impact and the pricing of Positional Tokens. To drastically increase the quality of Thales trader UX, this TIP proposes to react to these discoveries by introducing the following core changes to the AMM contract:
 
 -  **Buyer Skew Impact calculation to be done against the potential profit of the respective Positional Token**, instead of having buyer Skew Impact calculation done to proportion of Positional Token base price. This change fixes the non-trivial discrepancy of pricing between buying from the AMM against minting and then selling to the AMM. It also fixes an edge case where Positional Tokens priced above 0.9 could potentially go above 1.0 with high Skew Impact. This edge case is one of the reasons why the 0.1 <-> 0.9 pricing limit was introduced, and with this change it can be increased and the AMM will be able to provide on-demand liquidity for a much wider price range. Another effect this introduces is higher price impact towards buyers of cheaper (riskier) Positional Tokens, while providing better pricing for buyers of more expensive (safer) Positional Tokens, when compared to previous contract design.
 
 - **Skew Impact to be calculated as linearly applied for each subsequent token purchased in the batch**, instead of having the same quoted Skew Impact for every token in the batch. With this change, effective final cost of Skew Impact to each buy from the AMM will be halved while pertaining the Skew Impact effect on each respective subsequent traders. This change increases price fairness for large traders, allows for safe increase of Maximal Possible Skew Limit without affecting large traders and fixes the flaw in design where a trader profits more if he splits the purchase into several small batches instead of one large buy.
 
- **Decouple SafeBox impact from the Skew Impact calculation** by introducing it to the final pricing, instead of adding it to the Skew Impact at initial trade calculations.
 
With these core changes and optimizations allowing for it, this TIP additionally proposes to:  
 - Increase Positional Token supported price range -  from 0.1 <-> 0.9 to **0.05 <-> 0.95**
 - Increase allowed sUSD risk per market for the AMM and thus offer deeper liquidity per market - from 7k to **10k sUSD** risk per market
 - Increase Skew Impact total range - from 1% <-> 12% to **2%<->20%**
 - Decrease the timing of the AMM trading halt close to respective Market Maturity - from 24h to **8h before Market Maturity**
 
## Motivation
 
As of writing this TIP, initially seeded with only 70,000 sUSD of liquidity capital, the beta version of the Thales AMM managed to drive 1.3M sUSD of volume in ~2 months since deployment. On top of this massive show of capital efficiency, the Thales AMM managed to increase its liquidity capital to approximately 200,000 sUSD (growth of almost **300%**). Also important to note that, since being deployed 42 days ago, the SafeBox contract now holds 6,400 sUSD which is the amount equal to almost 10% of initial liquidity seed. This early beta performance and collected data confirms the massive potential of the novel Thales AMM. With further reactive optimizations and development, the Thales AMM can slowly start loosening up strict safety parameters and drive more and more volume while increasing UX quality and maintaining security.  
 
First major architecture change introduced by this TIP to the AMM architecture includes a change to how the Skew Impact is added to the final price of Positional Tokens for the buyer. By having Skew Impact calculated on top of Potential Profit, instead of Base Positional Token Price, the Skew Impact affects the cheaper higher-risk (higher return) Positional Tokens significantly more than it affects the more expensive lower-risk Positional Tokens. While this change fixes the non-trivial discrepancy of pricing between buying from the AMM against minting and then selling to the AMM, there are also some additional benefits. This new mechanism organically incentivises more sUSD volume via the AMM by offering significantly better terms for acquisition of more expensive (more safer) Positional Tokens than it was before. This change also reduces the AMM risk by increasing capital cost required by buyers of high return Positional Tokens.  
 
Second architecture change that introduces linear application of Skew Impact fixes the discovered edge case where a large buy that moves the Skew Impact is nonsensically more profitable if divided to sequenced smaller buys. Prior to this change, the Skew Impact was calculated based on the skew after the potential buy or sell and then applied to the price of all Positional Tokens in the batch. Subsequently with this new mechanism, the total cost of Skew Impact for large buyers will be halved when compared to the initial design. This new mechanism maintains fairness for all traders while also inviting more volume from large traders by effectively offering significantly better pricing. This change also makes room for safely increasing the Skew Impact max limit to twice the old value, while still providing the same amount of risk balancing capabilities.  
 
Third architectural change is to adapt the SafeBox contract to the previously mentioned changes and effectively decouple it from being included into Skew Impact calculations. If implemented, from now on the SafeBox cut will be calculated from the total trade cost after the Skew Impact calculations are priced in.
 
## Specification
 
This TIP entials the Thales Protocol DAO to implement the following changes to the [ThalesAMM.sol](https://github.com/thales-markets/contracts/blob/ThalesAMM/contracts/AMM/ThalesAMM.sol) contract:  
  
 - Implement logic so the Buyer Skew Impact calculation is done against the potential profit of the respective Positional Token.
 - Implement logic so the Skew Impact is calculated as linearly applied for each subsequent token purchased.
 - Implement logic to decouple SafeBox impact from the Skew Impact calculation by introducing it to the final pricing
 - Increase Positional Token supported price range from 0.1 <-> 0.9 to **0.05 <-> 0.95**
 - Increase allowed sUSD risk per market for the AMM from 7k to **10k sUSD** risk per market
 - Increase Skew Impact total range from 1% <-> 12% to **2%<->20%**
 - Decrease the timing of the AMM trading halt close to respective Market Maturity from 24h to **8h before Market Maturity**
 
 
## Test Cases
 
### Buyer Skew Impact change examples:  
 
**Example #1**
 - - Algorithm Price of Positional Tokens - 0.2 sUSD
 - - Skew Impact - 10%
 - - Cost for buyer using the **old method** - 0.2 + 0.2*10% = 0.22 sUSD
 - - Cost for buyer using the **new method** - 0.2 + (1-0.2)*10% = **0.28 sUSD**  
 - - Potential profit using the **old method** - 0.78 sUSD
 - - Potential profit using the **new method** - **0.72 sUSD**
 - - Potential profit if you mint and sell the other side to the AMM using the **old method** - 0.72 sUSD
 - - Potential profit if you mint and sell the other side to the AMM using the **new method** - **0.72 sUSD**
 
 **Example #2**
 - - Algorithm Price of Positional Tokens - 0.5 sUSD
 - - Skew Impact - 10%
 - - Cost for buyer using the **old method** - 0.2 + 0.5*10% = 0.55 sUSD
 - - Cost for buyer using the **new method** - 0.2 + (1-0.5)*10% = **0.55 sUSD**  
 - - Potential profit for the buyer using the **old method** - 0.45 sUSD
 - - Potential profit for the buyer using the **new method** - **0.45 sUSD**
 - - Potential profit if you mint and sell the other side to the AMM using the **old method** - 0.45 sUSD
 - - Potential profit if you mint and sell the other side to the AMM using the **new method** - **0.45 sUSD**
 
**Example #3**
 - - Algorithm Price of Positional Token - 0.8 sUSD
 - - Skew Impact - 10%
 - - Total cost for buyer using the **old method** - 0.8 + 0.8*10% = 0.88 sUSD
 - - Total cost for buyer using the **new method** - 0.8 + (1-0.8)*10% = **0.82 sUSD**
 - - Potential profit for the buyer using the **old method** - 0.12 sUSD
 - - Potential profit for the buyer using the **new method** - **0.18 sUSD**
 - - Potential profit if you mint and sell the other side to the AMM using the **old method** - 0.18 sUSD
 - - Potential profit if you mint and sell the other side to the AMM using the **new method** - **0.18 sUSD**
 
### Linear Skew Impact application example:  
 
**Example #1**
 - - Algorithm Price of Positional Tokens - 0.5 sUSD
 - - Pre-purchase Skew Impact - 0%
 - - Total Positional Tokens to buy - 1000
 - - Quoted Skew Impact for purchase - 10%
 - - Final cost for buyer using the **old method** - **550 sUSD**
 - - Final cost for buyer using the **new method** - **525 sUSD**
 - - Price of the Positional Token for the next subsequent purchase using the **old method** - 0.55 sUSD
 - - Price of the Positional Token for the next subsequent purchase using the **new method** - 0.55 sUSD
 
## Implementation
 
 
## Copyright
 
Copyright and related rights waived via CC0.
 

