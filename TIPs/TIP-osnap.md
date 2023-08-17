
| id      | Title | Status | Author | Description | Discussions to | Created |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| TIP-osnap | Implementing oSnap for Optimistic Governance | Draft | @abg4 | Implementing oSnap for Optimistic Governance | https://discord.gg/thales | 2023-08-17

## Simple Summary
This proposal suggests integrating oSnap, an optimistic governance tool developed by UMA, into the Thales DAO governance system.

## Abstract
Integrating UMA's oSnap module aims to decentralize and automate the onchain execution of governance decisions. oSnap streamlines onchain voting outcomes and allows DAO members to propose and execute Snapshot vote results, validated by UMA's oracle.

## Motivation
The motivation for this proposal is to enhance Thales DAO’s governance system by making it more efficient, secure, and decentralized. By adopting oSnap, Thales DAO can streamline its governance process and empower its token holders, thereby upholding the true spirit of decentralization.

## Specification
UMA’s oSnap is a tool for making onchain transactions based on offchain voting decisions. After the integration of oSnap, the flow works like this:
- A Snapshot proposal can include a transaction payload that is executable if the proposal is approved by the DAO.
- After a vote completes, a bot verifies the Snapshot proposal (vote passed, meets minimum quorum/voting period, accurate voting strategy). For Snapshot proposals that pass the verification process, the bot posts a bond and proposes the transactions to be executed, which starts the challenge period (2 or 3 days).
- If no dispute arises about the proposal’s accuracy during the challenge period, the transactions are automatically executed by the bot.
- In case of a dispute, the proposal is not executed and needs to be re-proposed. UMA token holders will determine who was correct in the dispute, with the correct party rewarded from the opposing party’s bond.

Additional features of the bot that automates proposing and executing transactions are:
- Disputes proposals that do not meet the validation criteria.
- Pays the gas for the full transaction flow which saves DAOs gas costs and avoids the DAO/community needing to post a bond for the duration of the challenge period.

The oSnap integration process is straightforward. We created a video to demonstrate how oSnap could be integrated in less than 1 minute (https://www.youtube.com/watch?v=F7HcuI-oYsY). The steps to integrate oSnap are:
- Install the Zodiac app.
- Deploy an oSnap module through the Zodiac app.
- Add oSnap to the Thales DAO Snapshot space through the SafeSnap plug-in.

Overall Cost: There are no fees associated with the implementation of oSnap. There are also no fees to use UMA’s oracle to verify oSnap requests. Therefore, the overall cost of implementation is zero. In fact, the DAO actually saves money since bots cover the gas cost of executing proposals onchain.

## Rationale
Current DAO governance models often rely on multi-signature wallets for the execution of proposals, which can lead to delays and potential security vulnerabilities. Implementing oSnap, which allows for onchain execution of offchain votes, would eliminate the dependency on multi-sig wallets and the associated issues. Furthermore, oSnap’s dispute mechanism and incentives for correct submissions help maintain the integrity and accuracy of the decision-making process.

The integration of oSnap into Thales DAO’s governance aligns with the DAO’s mission of decentralization and community involvement. Implementing oSnap will not only streamline the governance process but also eliminate the need for reliance on multi-signature wallets, thereby promoting more direct community control. This approach aligns with the DAO’s guiding value of decentralization by reducing the need for intermediaries and giving more power to the token holders. Moreover, oSnap’s dispute mechanism provides an extra layer of security, ensuring that the outcomes of governance votes accurately reflect what was approved on Snapshot. Finally, the integration of oSnap is free and easy, making it a practical choice for enhancing Thales DAO’s governance.

In terms of the verification process, the UMA team has focused a lot of resources on providing robust monitoring: 
- An automated proposal bot has been implemented that uses strict parameters to verify Snapshot proposals. The bot automates:
    - For Snapshot proposals that have passed verification, the bot automates the onchain proposal and execution steps to save DAOs gas costs and avoid the DAO needing to post a bond for the challenge period.
    - Disputing proposals that do not meet the validation criteria.
- Proposals go to the same closely monitored oracle system as Polymarket, Sherlock, Cozy, Across, and other oracle requests. Your DAO proposals will populate in UMA’s oracle dapp (https://oracle.uma.xyz/) making it easy for people to identify and dispute bad proposals. In practice, questionable Polymarket proposals tend to be disputed within 30 minutes, and those proposals are harder to evaluate than oSnap proposals. 
- Your proposals will also be pulled into bot monitoring systems that members of our competitive disputer network have set up, and you can use our open source code to set up Slack, Discord, and PagerDuty alerts. Our internal monitoring utilizes Slack and PagerDuty notifications when transactions are proposed, executed, and disputed. Risk Labs is also notified when there are any admin changes to the oSnap module (rules, collateral, owner, etc.).
- When transactions are proposed, a Discord ticket is automatically created where a verification program made up of UMA community members completes a multi-step verification process that consists of:
    - Verifying the Snapshot proposal passed and follows the oSnap rules
    - The proposed transaction payload matches the Snapshot transaction payload included in the proposal
    - The intent of the transactions matches what is proposed (not interacting with a malicious contract, transaction payload values match the proposal, etc).

Since its launch earlier this year, oSnap has been adopted by Across, BarnBridge, ShapeShift, Layer2DAO, and +DAO to control their on-chain treasuries, securing roughly $50 million in value. oSnap is also being used by Lossless Protocol to secure their next generation of wrapped tokens and is being deployed by Premia and CoW DAO, which will add another $70 million to oSnap’s total value secured in the coming weeks.

## Test Cases
n/a

## Implementation
n/a

## Copyright

Copyright and related rights waived via CC0.
