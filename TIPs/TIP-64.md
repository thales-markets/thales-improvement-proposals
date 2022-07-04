TIP-64 Governance Nomination Restriction

| id | Title | Status | Author | Description | Discussions to | Created |
 | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | 
| TIP-63 | Governance Nomination Restriction | Draft | BigPenny | Prohibit the nomination for multiple Thales governance positions by the same person | https://discord.gg/WfYEB98P6c | 2022-07-04

## Simple Summary
Limit the number of Thales governance nominations to one per person. 

## Motivation
Within the THALES DAO only the Thales Council and the Oracle Council members get elected via token governance. Both the Thales Council and the Oracle Council assume different responsibilities within the Thales protocol, however the Thales Council does act as a backstop for the unlikely case that the Oracle Council acts against the protocols interests. This is one of the reasons why the same person is prohibited from serving both on the Thales Council and Oracle Council at the same time. (Conflict of interest.) Despite that prohibition the same person may still nominate and run for both councils during election season. This can lead to the undesirable situation where one person receives enough votes to assume a position in both councils, requiring him or her to forfeit at least one position, effectively nullifying the votes he or she received for the forfeited position.

I propose to close that gap and limit the number of Thales governance nominations to one per person. 

## Specification
One person can only nominate for one council position at a time.

If someone nominates for multiple council positions, the first nomination posted on Discord is considered valid (as long as it fulfills all requirements) and all consecutive nominations of that person are considered void.

If the first nomination gets withdrawn the next nomination in line is considered valid, as long as it fulfills all requirements.

## Copyright Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

