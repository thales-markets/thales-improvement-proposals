
| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-93 | Update on RundownConsumer and adding the circuit breaker | Implemented | @scvija @grujawork | Update the Rundown consumer contract and adding a new verified contract  | https://discord.gg/thales | 2022-10-04

## Simple Summary

Update the Rundown consumer contract and adding a new verified contract

## Motivation  

During the almost 3 months that Overtime markets have been operational, we concluded that we need a circuit breaker if some of the normalized odds have changed more or less than xx %, so we can review them and see why this change occurred.
A **circuit breaker** is a mechanism that **pauses** a market **automatically**, in case the normalized odds for a game change more than a certain threshold. After checking the paused market, we can unpause it manually.


## Specification

For the implementation of this solution, we would need to create a new contract called "**TherundownConsumerVerifier**", which will check the data which comes from "**TherundownConsumer**" contract. Some of the methods were moved from the Consumer to the Verifier contract because they actually have been verifying the data all along. By doing this, we will simultaneously decrease the size of the Consumer contract, freeing up more size for potential future implementations.

The specification of the verified contract has the following important properties:

- `defaultOddsThreshold` - the property which will hold the value for the default circuit breaker threshold, initially set to **20%.**
- `oddsThresholdForSport`- the property which will hold the value for a custom circuit breaker threshold for a specific sport. If the `oddsThresholdForSport` is set, the default value is overwritten.

Checks moved from the Consumer to the Verifier:

- Checking for invalid names
- Checking of market types
- Calculation of normalized odds
- Is the outcome of the game valid
- Is the result of the game valid
- Are odds for the game valid

## Examples

An example of a circuit breaker that is checked using  `areOddsInThreshold`:

Case 1 - When normalized odds are inside the threshold (-10%):

Current normalized odds: 0.50  
New normalized odds: 0.45  
Result - Market **not paused**

Case 2 - When normalized odds are above the threshold (+22%):  

Current normalized odds: 0.50  
New normalized odds: 0.61  
Result - Market **paused**

Case 3 - When normalized odds are above the threshold (-22%): 

Current normalized odds: 0.50  
New normalized odds: 0.39  
Result - Market **paused**


## Copyright

Copyright and related rights waived via CC0.
