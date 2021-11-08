Formalizing THALES tokenomics
=============================

Simple Summary[#](#simple-summary "Direct link to heading")
-----------------------------------------------------------

This TIP proposes to formalize the following tokenomics model of Thales governance token:

[https://docs.thales.market/getting-started/thales-tokenomics](https://docs.thales.market/getting-started/thales-tokenomics)

Abstract[#](#abstract "Direct link to heading")
-----------------------------------------------

Thales protocol is launching a governance token THALES. It will be a standard ERC20 token that uses the ticker THALES. Thales DAO token is used to govern Thales protocol. Any further utility is to be decided and voted on by Thales DAO token holders or their chosen representatives.

The goal of this TIP is to officially formalize the distribution and vesting periods for the THALES token.

Motivation[#](#motivation "Direct link to heading")
---------------------------------------------------

The first iteration of Thales protocol governing body, the Thales council, was elected in august 2021 by Synthetix community of SNX stakers. With launch and proposed distribution of THALES governance token, future iterations of Thales council will be voted on by stakers of THALES. This way, THALES holders will be the foundation of every key decision regarding the progress of the protocol. This distribution model is set up in a way to incentivise long term alignment with the project and to incentivise future progress of the protocol in the most optimal way.

Specification[#](#specification "Direct link to heading")
---------------------------------------------------------

This proposal entails Thales DAO to launch and distribute THALES governance token in a manner detailed on the following tokenomics article:

[https://docs.thales.market/getting-started/thales-tokenomics](https://docs.thales.market/getting-started/thales-tokenomics)

THALES total supply: 100,000,000

Distribution and vesting schedule:

![updated-tokenomics](https://user-images.githubusercontent.com/67664068/132376752-b0669481-b7f2-4f58-8e5a-6e521d39ec46.png)

This proposal also entails Thales protocol DAO to deploy the following smart contracts:

* Synthetix SNX stakers distribution contracts:

Retro airdrop: [https://github.com/thales-markets/contracts/blob/main/contracts/Airdrop/Airdrop.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Airdrop/Airdrop.sol)

Retro pro rata distribution: [https://github.com/thales-markets/contracts/blob/main/contracts/RetroDistribution/VestingEscrow.sol](https://github.com/thales-markets/contracts/blob/main/contracts/RetroDistribution/VestingEscrow.sol)

Ongoing distribution: [https://github.com/thales-markets/contracts/blob/main/contracts/Airdrop/OngoingAirdrop.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Airdrop/OngoingAirdrop.sol)

* THALES staking and escrow contracts:

[https://github.com/thales-markets/contracts/blob/main/contracts/Staking/StakingThales.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Staking/StakingThales.sol)

[https://github.com/thales-markets/contracts/blob/main/contracts/Staking/EscrowThales.sol](https://github.com/thales-markets/contracts/blob/main/contracts/Staking/EscrowThales.sol)

Rationale[#](#rationale "Direct link to heading")
-------------------------------------------------

n/a

Test Cases[#](#test-cases "Direct link to heading")
---------------------------------------------------

n/a

Implementation[#](#implementation "Direct link to heading")
-----------------------------------------------------------

n/a

Copyright[#](#copyright "Direct link to heading")
-------------------------------------------------

Copyright and related rights waived via CC0.