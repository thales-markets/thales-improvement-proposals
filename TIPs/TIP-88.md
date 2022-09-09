| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-88 | Allow hot-fixes for critical security vulnerabilities | Draft | BigPenny (@RealBigPenny) | Allow hot-fixes for critical security vulnerabilities | https://discord.gg/tbd | 2022-09-10
 
## Simple Summary

Allow pDAO to apply hot-fixes to Thales smart contracts for critical security vulnerabilities without prior Thales Council approval.

## Abstract

This TIP proposes to grant pDAO permission to apply hot-fixes for critical security vulnerabilities without prior Council approval. Approval for the changes must be aquired via standard TIP approval procedure after the hot-fix has been applied.

## Motivation

Smart contract vulnerabilities are one, if not the biggest attack surface of the Thales protocol, which is true for most EVM based protocols. Given that premise it is of utmost importance that identified security issues get fixed as soon as they are identified and confirmed, especially if such issues pose a substantial threat to the protocol and it's users safety, both monetary and functionally. (critical security vulberability) A security vulnerability remains "critical", even if the likelihood of practical exploitation is considered to be low, as long as the theoretical damage satisfies the aforementioned criteria.

The often times slow nature of Council Governance shall not be limiting pDAO from implementing hot-fixes to the aformentioned class of security vulnerabilities, especially since such contract changes, as long as they are conducted in good faith, should be rarely if ever contentious.

To preserve due process and avoid creating an arbitrary bypass of Council Governance, pDAO shall seek the approval of the Thales Council via standard TIP approval procedure after the hot-fix has been applied.


## Specification

pDAO gets granted permission to apply hot-fixes to Thales smart contracts for critical security vulnerabilities pursuant to the above extend and limitations.

## Copyright

Copyright and related rights waived via CC0.
