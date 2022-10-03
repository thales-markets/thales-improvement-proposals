
| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-92 | Updates on Sports Markets | Draft | @scvija @grujawork @kirilaa | Update the cap per sport and canceled markets cooldown  | https://discord.gg/thales | 2022-09-13

## Simple Summary

Update the cap per sport and canceled markets cooldown

## Motivation  

During the almost 3 months that Overtime markets have been operational, we came to the conclusion that some sports would benefint from having a different cap per market from other. For example, it makes little sense the College Football has the same risks per market as NFL. 

The second update is the cooldown of canceled markets. In case of a market being canceled, we want to have a cooldown period for this cancelation, allowing pDAO to check if this cancelation is valid and actually took place. 

## Specification

  `capPerSport` - the property that wild hold the mapping of the cap per sport
  `setCapPerSport` - setting the value of the capPerSport variable
  `cancelTimeout` - the time after the market was canceled, during which the user can't claim back their investment
  `setCancelTimeout` - setting the value of cancelTimeout

  The `defaultCapPerGame` will be 5k, as is it now. Only if the `capPerSport` is set, the value will be overwritten.

  The value of cancelTimeout will be set to 2 hours originally. In case of a wrongful cancelation, during the cooldown period, whitelisted addresses are able to set a correct result, so the users that have a winning positon can actually claim thier winnings.



## Copyright

Copyright and related rights waived via CC0.
