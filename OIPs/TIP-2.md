
## Simple Summary

This TIP proposes to formalize technical agenda items for Thales.

## Abstract

The protocol binary option contract suits will go live on Ethereum mainnet enabling users to interact with the Thales smart contract suite.

Launching the minimal viable product, the native token, native token staking, and migrating Thales systems to Optimism capture the high level technical agenda items for the initial phases Thales will be live.

## Motivation

As one of the earliest TIPs, TIP-2 essentially locks in the high level roadmap for the second half of 2021:

* Launch the binary options minimal viable product
* Launch the native token and staking
* Migrate Thales systems to Optimism

The goal of formalizing the technical agenda item is to ensure legitimate deployment of the contracts onto Ethereum by Thales core contributors. The Thales Council will vote on TIPs. Since the Thales Council is being elected by SNX stakers, the will of tokenholders is being validly expressed through the council. The execution of the early roadmap items that have been under discussion by Thales core contributors for months now can be considered legitimate as well.

[SIP-159](https://github.com/Synthetixio/SIPs/blob/master/sips/sip-159.md), a Synthetix Improvement Proposal, formalized Thales Council governance, while [SIP-149](https://sips.synthetix.io/sips/sip-149) deprecated binary options contracts from the Synthetix codebase. Per SIP-149 the Thales core contributors emerged as the team to provide binary options more love and care and fully explore this financial primitive in the context of the vibrant Synthetix ecosystem. As part of SIP-149, Synthetix stakers will be able to claim 35% of the native tokens of the new binary options protocol.

## Specification

Deployment of the following contracts:

`BinaryOption.sol.`

`BinaryOptionMarket.sol`

`BinaryOptionMarketData.sol`

`BinaryOptionMarketFactory.sol`

`BinaryOptionMarketManager.sol`

`BinaryOptionMarketMastercopy.sol`

`BinaryOptionMastercopy.sol`

`OwnedWithInit.sol`

`SportFeed.sol`

`SportFeedOracleInstance.sol`

## Rationale

n/a

## Test Cases

n/a

## Implementation

n/a

## Copyright

Copyright and related rights waived via CC0.