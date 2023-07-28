
| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-90 | New Overtime incentives module | Implemented | @danthales | Use fees rebates as the basis for Overtime incentives | https://discord.gg/thales | 2022-09-13

## Simple Summary

Change the way Overtime incentives are paid out to use fee rebates as the basis.

## Motivation  
Several community members have shared concerns about a part of the incentives being farmed by wash traders. After some consideration, I believe using FeeRebates as the base for how the OP and THALES rewards are paid out removes any chance of wash trading and ensures only organic traders are rewarded pro rata.   

## Specification
The maximum amount of bi-weekly rewards stays the same as previously established: 8,000 OP tokens and 8,000 THALES tokens.    

The new leaderboard will calculate rewards as 90% rebate of the SafeBox fee, which is 2% of total amount paid in sUSD.  
  
The $ value of OP and THALES will be calculated using a 7 days twap at the start of the period.  

If at the end of the two weeks period the total rebates end up being more than the initial twap value of OP and THALES tokens, the rebate will be reduced proportionally for every trader.  

The new incentives program will start when the current period ends.  

Example1:   
    - TWAP value of 8,000 OP tokens and 8,000 THALES is $15k  
    - Total fees during the period are $10k  
    - 90% rebates means $9k is paid out to all traders in rebates and everyone gets max rebate. The remaining amount of $6k is used to have longer runway of incentives       


Example2:   
    - TWAP value of 8,000 OP tokens and 8,000 THALES is $15k  
    - Total fees during the period are $20k  
    - 90% rebates would be $18k which is more than the max cap of rewards. The rebate is reduced proportionally for all traders by using the formula `myTotalRebates x 15 / 18`        



## Copyright

Copyright and related rights waived via CC0.
