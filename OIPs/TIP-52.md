| id | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-52 |  Supply liquidity to Thales Bancor pool | Implemented | Red | Enable Treasury DAO to deposits funds in Thales Bancor pool | https://discord.gg/rPpPcMXSeU | 2022-05-13


## Simple Summary
Fund Thales pool on Bancor with DAO owned THALES tokens.

## Abstract
This TIP proposes Thales treasury DAO funds liquidity in the Thales pool on Bancor. The treasury will add THALES tokens to the pool to seed its liquidity.

## Motivation
This proposal aims to increase sustainable, DAO owned liquidity on L1. Since l2 migration, most liquidity has followed suit and moved toward optimism. This leaves little liquidity on mainnet and therefore restricts access for some traders who may want to access THALES without moving to L2. Two sided liquidity pools can also suffer from large amounts of impermanent loss which is not ideal.

## Specification

### Overview
Bancor provides an excellent solution for protocol owned, L1 liquidity with zero additional emissions or incentives required. This pool gives Thales holders the confidence that they can always efficiently buy and sell their THALES on Bancor at any time on Mainnet.

### Rationale
By funding our own THALES/BNT pool, we can offer consistent liquidity on L1 without paying emissions for the liquidity or using a bonding discount. We can avoid mercenary capital that will farm and dump our token and protect DAO funds from losses with Bancor’s IL protection. 

This initial seeding by the Treasury DAO also strengthens our relationship with Bancor. Allowing liquidity of the pool to be increased in the future via BancorDAO governance. This would allow further liquidity to be supported via Bancor governance enabling THALES holders to provide liquidity without impermanent loss. 

### Technical Specification
Deposit THALES treasury DAO tokens into the pool up to the limit of 100,000 BNT ($150,000 in notional value currently)

### Test Cases
Over 30 DAOs [https://blog.bancor.network/nexus-mutual-joins-30-daos-adopting-bancors-dao-treasury-management-solution-2eb60b762259] have adopted Bancor’s single sided staking for their treasury management.

### Configurable Values

`BNT/THALES Pool Deposit Limit = 100,000 BNT`


## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

