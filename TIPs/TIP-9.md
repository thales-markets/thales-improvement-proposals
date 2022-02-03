Formalizing Core Contributors THALES token allocation and respective rules
==========================================================================

| id  | Title | Status | Author | Description | Discussions to | Created |
| --- | --- | --- | --- | --- | --- | --- |
| TIP-9 | Formalizing Core Contributors THALES token allocation and respective rules | Implemented | Danijel (@Danijel), padzank (@padzank) | This TIP aims to formalize how a CC allocation vesting will work in detail and what are the rules for when a CC vesting can be interrupted | [https://research.thales.io](https://research.thales.io) | 2021-11-04 |

Simple Summary[#](#simple-summary "Direct link to heading")
-----------------------------------------------------------

This TIP aims to formalize how a CC allocation vesting will work in detail and what are the rules for when a CC vesting can be interrupted

Abstract[#](#abstract "Direct link to heading")
-----------------------------------------------

From the THALES tokenomics article, 20,000,000 THALES (20% of total supply) was set aside for core contributions. The vesting rules defined a 1 year cliff and then a 3 year linear unlock.

This TIP proposes a more detailed set of rules on how the vesting would work and when it can be altered, stopped and when a specific allocation can be returned to the treasury.

Motivation[#](#motivation "Direct link to heading")
---------------------------------------------------

It is intuitively clear that bringing in capable and loyal CCs requires incentivizing them with a token allocation. The DeFi space never lacks opportunity, so to offset the opportunity cost, and for long term alignment sake, the token vesting needs to be ongoing and long term.

The initial plan of having the tokens allocated for a given CC never accounted for a scenario in which a CC stops being active and stops contributing to the protocol, but his allocation continues to be lineary vested.

This TIP proposes that Thales ProtocolDAO maintains control over the vesting contract and can stop the vesting of a CC that is no longer contributing to the protocol. The said CC would keep the allocation vested to date, but the remaining allocation is sent back to the treasury and available for reallocation to others/new CCs.

As we have previously announced a large portion of CC tokens were unintentionally locked in a contract:  
[https://thalesmarket.medium.com/a-part-of-thales-core-contributors-tokens-are-locked-and-its-implications-241fcec37888](https://thalesmarket.medium.com/a-part-of-thales-core-contributors-tokens-are-locked-and-its-implications-241fcec37888).

This ended up being a blessing in disguise as it allowed the Thales CCs to come up with a better mechanism of vesting that rewards ongoing loyalty. As Co-Founders carry the largest risk and responsibility to lift the brand new protocol off the grounds, a large percentage of the CCs allocated tokens was to be split by Thales co-founders, as the norm has it in DeFi. As of the time of writing this TIP, one of the co-founders Farmwell has not been contributing to the protocol to any extent and has been unresponsive to any form of communication for more than 2 months. There have been no responses to a single DM from any other CC or Strategic Partner. There is absolutely no certainty on whether the individual at question will come back and in which capacity. As such, the allocation that was planned to go to him, should be reallocated to other CCs that carry the burden of his absence.

Specification[#](#specification "Direct link to heading")
---------------------------------------------------------

This TIP proposes the following points to be formalized:

* Reduce total allocation of THALES token supply towards Thales Core Contributors from 20% to **18%**.
* Co-founder allocation to be set at 5% (reduced from 6%) of total supply and to subsequently start unlocking in April 2022, linearly over 3 years.
* Early core contributor allocation (referred to as Senior Core Contributors in the rest of the TIP) who started contributing in April 2021 and worked hard to deliver the MVP, Token and deployment on L2, to get 1-2% of total supply each, and their unlocking to start in April 2022 linearly over 3 years
* Formation of Thales Senior Core Contributor Committee, with member being Senior Core Contributors that decides CC engagement, disengagement and allocation. As of time of writing this TIP, individual members of the SCCC are to be the most senior Core Contributors with one advisory role for a Core Contributor next in line by seniority and expertise.
* Other existing Core contributors that started contributing later than April 2021 and any future new Core Contributor will get in a range of 100k-500k token allocation based on their performance and responsibility, as evaluated by Senior Core Contributors. Their unlock will begin after at least 6 months has passed since they joined the project and unlock linearly over 3 years
* Core contributors are eligible to have more allocation added to their vesting contracts based on merit as evaluated by Senior Core Contributors
* If a Core Contributor is no longer contributing, either by his own choosing or because Senior Core Contributors find in the the protocols best interest to stop paying a monthly stipend to a Core Contributor effectively terminating his Core Contributor status, the amount of tokens that were supposed to be vesting in the future are to be returned to the treasury and available for reallocation.
* While it cannot be fully controlled what Core Contributors do with the amounts of tokens already vested, there is a clear guideline that no CC allocation is to be market sold. If, for whatever reason, a Core Contributor wishes to be relieved of his tokens, Thales Senior Core Contributors will aim to use Aelin protocol to find a purchaser or use other means to achieve an OTC trade keeping in mind the best interest of the Thales protocol.
* The co-founder allocation to Farmwell of 6% of total supply is to be freed up completely due to his inactivity and lack of communication and contributions for over two months. This freed 6% allocation is to be split 4% to present and future Thales Core Contributors and 2% back to Thales Treasury.

Rationale[#](#rationale "Direct link to heading")
-------------------------------------------------

With one of the cofounders mysteriously disappearing from all known mediums where he maintained active communication in the first few months of the project, it has become clear that a “set & forget” CC token allocation is far from optimal as too many things can change over 4 years. With the introduction of a rule that a specific CC token allocation is only unlocking as long as the said Core Contributor is active and contributing, there is an ongoing and long term incentive for loyal and capable Core Contributors.

Further elaboration on Farmwell’s situation:  
At the end of August 2021, after regular daily meetings, the co-founder Farmwell abruptly wrote that he will be tending to his health for the next few weeks. Thales Core Contributors and Strategic Partners tried reaching out to him by all means available to both get more information out of concern for his well being, but also to get an agreement on how to handle responsibilities that depended on him with the upcoming token launch. No direct message was answered to date. Communications efforts continued to this day, but to na avail.

Farmwell would only come online for a brief instance at the end of September 2021 and at the end of October 2021 to announce an expectation of continuation of being absent for a few more weeks while navigating his health issues.

It's of course human to be empathetic and understanding to anyone that needs to focus on his health first, and any Thales Core Contributor or community member will surely support that someone needs to take as much time as they need to do so. However, not taking a few minutes to discuss things of crucial project significance, while being very active on-chain, does not show much care for Thales.

Active Thales Core Contributors found it very intriguing that Farmwell’s messages at the end of September and end of October were identical, letter to letter, almost as if auto sent. Known online addresses were researched and this showed that Farmwell (or whoever is in control of his known addresses) is very much active daily in various on-chain farming and trading activities. While we do not wish to speculate, it is very clear that it became a protocol and security risk to:

* Keep paying stipends to an individual that does not communicate to other Thales CCs but actively uses his wallets for various on-chain activities.
* Keep previously mentioned address as a treasury signer
* Keep the largest possible CC token allocation to such an address  

First draft of TIP-9 presented the initial idea to leave 1-1.5% allocation of THALES tokens on the table and a certain amount in stable coins to show gratitude should Farmwell come back and discuss his abscence. However, one day after the TIP-9 draft was released publicly on Saturday 6th of November, Farmwell maliciously and suddenly decommissioned the "thales.market" domain he had credentials over and deleted the official Thales Discord. These malicious acts against the protocol removed any possibility of engaging in formal renegotiations and a potential renewal of trust with the Thales Core Contributors.  

Farmwell (or whoever controls his address) is no longer a signer in Thales Treasury, as decided by the active members of Treasury DAO.  

No existing Core Contributor or community member has shown anything but remorse that it has come to this. The circumstances have given the Core Contributors no choice. It is a priority to keep what’s best for Thales in mind.  

Test Cases[#](#test-cases "Direct link to heading")
---------------------------------------------------

n/a

Implementation[#](#implementation "Direct link to heading")
-----------------------------------------------------------

n/a

Copyright[#](#copyright "Direct link to heading")
-------------------------------------------------

Copyright and related rights waived via CC0.
