---
description: >-
  A step-by-step overview of the governance process: DRC creation, Snapshot poll
  creation, DIP creation, voting on a Snapshot poll, voting on a DIP, queueing a
  DIP, and executing a DIP.
---

# Governance Guide

The dYdX Foundation created this guide to assist the dYdX community with understanding the dYdX governance process. The guide provides a step-by-step overview of:

* [Forum Discussions (off-chain)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [DRC creation (off-chain)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Snapshot poll creation (off-chain)](governance-guide.md#step-2-drc-snapshot-polling-off-chain)
* [Voting on a Snapshot poll](governance-guide.md#how-to-vote-on-a-snapshot-poll)
* [DIP creation (off-chain)](governance-guide.md#step-3-dip-creation-off-chain-proposal)
* [DIP creation (on-chain)](governance-guide.md#step-1-on-chain-dip-drafting)
* [Voting on a DIP (on-chain)](governance-guide.md#how-to-vote-on-a-dip)
* [Queueing a DIP (on-chain)](governance-guide.md#how-to-queue-a-proposal)
* [Executing a DIP (on-chain)](governance-guide.md#how-to-execute-a-proposal)

The two examples featured in the guide are _DIP 2 (off-chain proposal) - Reducing Liquidity Provider Rewards Threshold_ and _DIP 3 (on-chain proposal) - Safety Module Restoration_.

## DIP 2 (Off-Chain Proposal) - Reducing Liquidity Provider Rewards Threshold

_**Summary:**_

In Epoch 6, the dYdX community voted on [Snapshot ](https://commonwealth.im/dydx/snapshot/dydxgov.eth/0x785066561be1e5d170eb28960da5ef2643ee0d0c3d590fd797c028512cc6be43)to reduce the LP rewards volume threshold for market makers from 1% to 0.25%. The reduction of the LP rewards threshold from 5% to 1% in Epoch 2 followed the same process as the reduction in Epoch 6 (1% to 0.25%). The step-by-step overview to reduce the LP rewards volume threshold from 5% to 1% is included below.

The majority of the community (399 voters and 86% of DYDX) voted on [Snapshot](https://forums.dydx.community/snapshot/dydxgov.eth/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN) to reduce the volume threshold to obtain Liquidity Provider rewards from 5% to 1%. An [off-chain DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-2.md) to reduce the Liquidity Provider rewards volume threshold for market makers from 5% to 1% was submitted by Jacob Goh (jteam0x) at DeFiance Capital. Market makers that met the 1% threshold in Epoch 2 were eligible to earn Liquidity Provider rewards in Epoch 3. The proposal did not require any on-chain smart contract changes.

_**Background:**_

As part of the Liquidity Provider [rewards program](https://docs.dydx.community/dydx-governance/rewards/liquidity-provider-rewards), 1,150,685 DYDX is distributed per epoch (28 days) to Liquidity Providers who market make for the protocol. Rewards are distributed based on a formula rewarding a combination of uptime, two-sided depth, bid-ask spreads, and the number of markets supported. To be eligible for this rewards program, liquidity providers need to provide a minimum percentage of the total maker volume during the preceding epoch.

The dYdX community has "immediate and irrevocable control over" the Liquidity Provider rewards threshold. The full list of parameters that the community controls is linked [here](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

The community was motivated to lower the Liquidity Provider rewards threshold because it would incentivize new Market Makers and small to medium size Market Makers to increase liquidity on the dYdX platform. Further, increasing the number of Market Makers on the platform helps the dYdX protocol become more decentralized.

Next, we provide a step-by-step overview of how dYdX governance functions in practice. More information about the dYdX governance process is linked [here](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

### **STEP 1 - Forum Discussions, DRC Creation (Off-Chain), and DRC Feedback**

_**Description:**_

The dYdX Governance Process is fueled by [governance forums](https://forums.dydx.community/). Community members post and comment on discussion threads to reach a rough consensus off-chain. More information about forum discussions and DRC Creation is linked [here](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

_**Application to DIP 2:**_

Su Zhu (zhusu) from Three Arrows Capital created an [off-chain Forum Discussion](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/) to lower the Liquidity Provider Rewards Threshold. Various community members, such as Evgeny from Wintermute, Ben from Kronos, Josh from Sixtant, and many more, participated in the discussion and offered valuable feedback.

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](<../.gitbook/assets/image (50).png>)

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](<../.gitbook/assets/image (26).png>)

#### _How to Post and Comment on Commonwealth:_

* Register on Commonwealth with your Ethereum wallet or Github account and join the dYdX community [here](https://forums.dydx.community/).

![https://forums.dydx.community/](<../.gitbook/assets/Untitled 1 (1)>)

* Select a thread, scroll through the comments, and like or reply to comments by clicking the icons under the respective comment.

![https://forums.dydx.community/discussion/1805-reduce-market-maker-incentives?comment=4988](<../.gitbook/assets/image (17).png>)

* Create a new discussion thread or post a DRC by clicking on “New thread” and selecting the topic category.

![https://forums.dydx.community/new/discussion](<../.gitbook/assets/Untitled 3 (2)>)

* If you are creating a DRC, please follow the template linked [here](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md). As outlined under _DRC Creation_ in the [Proposal Lifecycle](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle), DRCs at a minimum must include the following:
  * A short and concise title of the DRC.
  * A short and concise description of the proposal.
  * The rationale for the DRC (e.g. why?).
  * The title of the forum post must include DRC: \[insert short title of the DRC] (E.g. DRC: New Market Request).
  * A community poll that community members can use to vote on improvements off-chain.

### **STEP 2 - DRC Snapshot Polling (Off-Chain)**

_**Description:**_

After the community achieves a rough consensus, a community member with 10K proposing power can create an off-chain vote for the DRC on [Snapshot](https://snapshot.org/#/). [Proposing power](https://docs.dydx.community/dydx-governance/voting-and-governance/voting) gives access to creating and sustaining a proposal. Snapshot is a simple voting interface that allows users to signal sentiment off-chain. Votes on snapshot are weighted by the number of DYDX held by or delegated to the address used to vote. The community member that creates the Snapshot poll must provide details about the DRC, a voting system, vote start date, vote end date, and snapshot block number. The voting period should be 5 days in length and voting should start after a 1 day voting delay. The voting delay provides time for dYdX community members to learn more about the DRC, purchase DYDX, or delegate the voting power of their DYDX. Community members who hold DYDX or who have been delegated voting power before the Snapshot block number are eligible to vote. More information about Snapshot polling is linked [here](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

_**Application to DIP 2:**_

Community members provided feedback on Su Zhu's post. The following rewards thresholds were suggested by the community:

* [0.5%](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=body) - Su Zhu from Three Arrows Capital,
* [1%](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4972) - Sam from BitTrading,
* [2.5%](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4855) - Ben from Kronos / WOO Network, and
* [5%](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4872) - Evgeny from Wintermute.

Next, Su Zhu created a Snapshot poll with the following options:

* Lower MM threshold to 1%
* Lower MM threshold to 2.5%
* Keep the MM threshold at 5%

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](<../.gitbook/assets/Untitled 4 (1)>)

#### _How to Vote on a Snapshot Poll:_

* Register on Snapshot with your Ethereum wallet and follow dYdX proposals [here](https://snapshot.org/#/dydxgov.eth). Alternatively, you can vote and create a Snapshot poll directly on [Commonwealth](https://forums.dydx.community/snapshot/dydxgov.eth).

![https://snapshot.org/#/dydxgov.eth](<../.gitbook/assets/Untitled 5 (1)>)

* To view active Snapshot Proposals, go to [Snapshot](https://snapshot.org/#/dydxgov.eth) or [Commonwealth](https://forums.dydx.community/snapshot/dydxgov.eth).

![https://snapshot.org/#/dydxgov.eth/create; https://forums.dydx.community/snapshot/dydxgov.eth](<../.gitbook/assets/Untitled 6 (2)>)

* To vote on active Snapshot polls, you need to hold DYDX or have voting power delegated to your address before the Snapshot block number when the Snapshot poll becomes active.

![https://forums.dydx.community/snapshot/dydxgov.eth/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](<../.gitbook/assets/Untitled 7 (1)>)

* To vote, click on the proposal and select “yes” or “no” followed by “vote.”

![https://forums.dydx.community/snapshot/dydxgov.eth/0xfbcb8104dc469cae09727dea89577f89b37df784c3ef2715b26ab77e9ae15161](<../.gitbook/assets/Untitled 8 (2)>)

![https://snapshot.org/#/dydxgov.eth/proposal/0xfbcb8104dc469cae09727dea89577f89b37df784c3ef2715b26ab77e9ae15161](<../.gitbook/assets/Untitled 9 (2) (1)>)

#### _How to Create a Poll on Snapshot:_

* To create a Snapshot poll, you will need to hold a minimum of 10k DYDX and/or have proposing power delegated to the address that you are using to create the proposal.
* The Snapshot proposal can consist of one or multiple actions, up to a maximum of 10 actions per proposal. Actions are changes specified in a proposal.
* If you meet the minimum 10k proposing power requirement, select “New Proposal” and fill in the open fields as per the content requirements below.

![https://snapshot.org/#/dydxgov.eth/create](<../.gitbook/assets/Untitled 10 (2) (1)>)

![https://forums.dydx.community/new/snapshot/dydxgov.eth](<../.gitbook/assets/Untitled 11>)

DRC Snapshot Poll Content Requirements:

* details of the DRC with a link to the forum discussion,
* a voting system,
* vote start date and vote end date set to 4 days in total length, and
* Snapshot poll is posted 1 day (\~6570 blocks) before voting starts.

Requirement for Binding Snapshot Polls:

For most decisions, a Snapshot poll acts as signaling, while an on-chain vote is required for a binding outcome that changes the smart contract(s). For decisions that don’t require an on-chain smart contract call, notably changes to the Trading and Liquidity Provider rewards formulas, Snapshot votes are considered the binding and final vote. In addition to the content requirements above, Snapshot polls that are binding votes for variables controlled off-chain must include:

* Binary voting options. For clarity, an address is either voting for or against a proposal.

![](<../.gitbook/assets/Untitled 12 (2)>)

* After the vote, the related info will be stored on IPFS and a report will be automatically generated and available to download.

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](<../.gitbook/assets/Untitled 13>)

### **STEP 3 - DIP Creation (Off-Chain Proposal)**

_**Description**:_

A DIP needs to be created when (1) a Snapshot poll results in an off-chain parameter (such as modifications to the Trading Rewards or LP Rewards formulas) being updated and (2) when a community member wants to submit a proposal to modify on-chain smart contracts. For votes that do not require any on-chain smart contract updates, the result of the Snapshot poll must be formalized in an off-chain DIP and submitted via a Pull Request to the Pending-DIP branch of the dYdX Foundation’s Github. The DIP should reflect the winning outcome of the Snapshot. The DIP must specify the information included in the template linked [here](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md).

_**Application to DIP 2:**_

In this case, the [DIP](https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md) was authored by @Jteamdc.

![https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md](<../.gitbook/assets/Untitled 14 (2)>)

When the draft proposal for DIP 2 was completed, @Jteamdc created a \*\*\*\* [Pull Request](https://github.com/dydxfoundation/dip/pull/8) from the working branch against the dYdX foundation's Pending-DIPs branch. After the dYdX Foundation reviewed the proposal and signed off, the changes from the Pending-DIPs were merged to the Master Branch.

![https://github.com/dydxfoundation/dip/pulls](<../.gitbook/assets/Untitled 15 (2)>)

Since reducing the liquidity providers' rewards threshold does not require any on-chain smart contract changes, the process is now complete and the changes will be effective during the next epoch.

#### _How to Create a DIP:_

* The DIP should be based on the winning outcome of the off-chain DIP voting on Snapshot and can consist of one or multiple actions, up to a maximum of 10 actions per proposal. Actions are changes specified in a proposal. More information can be found under [DIP Creation](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle#6.-proposal-queuing-and-execution).
* Register for a Github account: [https://github.com/signup](https://github.com/signup).
* Go to the dYdX repo page linked [here](https://github.com/dydxfoundation/dip) and fork the repo under your Github account.

![https://github.com/dydxfoundation/dip](<../.gitbook/assets/image (60).png>)

* In the forked DIP repo, go to the directory that contains the content of the DIPs: [https://github.com/\[user\_name\]/dip/tree/master/content/dips](https://github.com/yt8073/dip/tree/master/content/dips).

![](<../.gitbook/assets/Untitled 16 (1)>)

* Select the dips folder: [https://github.com/\[user\_name\]/dip/tree/master/content](https://github.com/Jwatts15/dip/tree/master/content).

![](<../.gitbook/assets/Untitled 17 (2)>)

The dips folder includes a directory of previous proposals that follow the DIP template linked [here.](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md)

![https://github.com/dydxfoundation/dip/tree/master/content/dips](<../.gitbook/assets/image (86).png>)

* Before you start drafting a proposal, please ensure that the branch that you forked is up to date with the lastet version of the master branch. If you are using an old version of the DIP repo, please confirm that your forked version is up to date with the latest changes. For assistance rebasing your forked version, you can follow the steps here: [https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master](https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master).
* Edit the [DIP template](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) with the information for your proposal. If you did not fork the DIP repo, selecting the edit icon will automatically fork the repo from the master because you are not an admin.

![https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md](<../.gitbook/assets/Untitled 19 (2)>)

* Follow the [template](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) and add your DIP to your fork of the repository in the `content/dips/` directory. Please follow the DIP Statuses naming conventions included below.

![](../.gitbook/assets/20.png)

DIP Statuses:

* WIP - a DIP that is still being developed.
* Proposed - a DIP that is ready to be proposed on-chain.
* Approved - a DIP that has been accepted for implementation by the dYdX community.
* Implemented - a DIP that has been released to mainnet.
* Rejected - a DIP that has been rejected.
* After checking that all of the content is correct, create a Pull Request from your working branch against the dYdX Foundation's Pending-DIPs branch. Please **do not** submit this Pull Request against the dYdX Foundation's master branch because the IPFS job will fail if any external parties want to merge to the master branch. Please use the Pull Request linked [here](https://github.com/dydxfoundation/dip/pull/8) as an example.

![](<../.gitbook/assets/Untitled 15 (1)>)

* After review, the dYdX Foundation will merge the changes from the Pending-DIPs branch to the Master branch.

![https://github.com/dydxfoundation/dip/pull/9](../.gitbook/assets/22.png)

* Before **the merge,** a job will run automatically to upload the DIP to IPFS. You can verify the upload of the DIP to IPFS here: [https://github.com/dydxfoundation/dip/pull/9/checks](https://github.com/dydxfoundation/dip/pull/9/checks).
* The DIP is added under [**`dip`**](https://github.com/dydxfoundation/dip)`/`[`content`](https://github.com/dydxfoundation/dip/tree/master/content)`/`**`dips`**`/`.

![](../.gitbook/assets/23.png)

Since the proposal does not require any on-chain smart contract changes, the process is now complete and the changes will be effective during the next epoch

## DIP 3 (On-Chain Proposal) - Safety Module Restoration

_**Summary:**_

On November 1st, an on-chain [DIP](https://dydx.community/dashboard/proposal/3) was created by Dan Robinson from Paradigm to restore the functionality of the Safety Module staking pool. The majority of the community (251 voters and nearly 142M DYDX) voted in favor of restoring the functionality of the Safety Module. After a 10 day Voting Period, it took almost 3 days for a community member to call the queue and move the proposal into the 7 day long timelock delay. On November 20th, the Safety Module was restored and reset to a clean state.

_**Background:**_

The dYdX Safety Module is a staking contract designed to bootstrap a decentralized pool of funds that can be used to backstop the dYdX protocol. Users stake DYDX into the safety pool and receive stkDYDX (1:1). stkDYDX is a tokenized position transferred as an ERC-20 that has the same voting and proposing rights as DYDX. In the event of a shortfall event, a governance vote is required to slash staked DYDX to mitigate losses. From the DYDX token supply, 2.5% (25,000,000 DYDX) of the token supply will be distributed to users who stake DYDX in the safety staking pool. More information about the safety staking pool can be found [here](https://dydx.foundation/blog/en/safety-staking).

As part of the [safety staking pool rewards](https://docs.dydx.community/dydx-governance/staking-pools/safety-staking-pool), 383,562 DYDX will be distributed per epoch (28 days) to stakers. Rewards are distributed pro-rata every second to stakers.

The dYdX community has "immediate and irrevocable control over" the parameters of the safety module smart contract. The full list of parameters that the community controls is linked [here](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

On September 8th at 15:00 UTC, the transfer restriction on DYDX tokens was lifted and effectively opened staking to the dYdX Safety Module. Over 50 different addresses staked approximately 157K DYDX over the course of almost 1 hour. A bug caused an error in the deployment process and no stkDYDX was issued to the addresses who staked into the Safety Module. As a result, each staker’s funds were stuck in the contract and the dYdX team disabled staking on the dYdX governance UI.

[DIP 1](https://dydx.community/dashboard/proposal/0) proposed restoring functionality to the Safety Module and allowing the affected addresses to recover their funds and receive an additional 10% of their staked tokens as compensation to make them whole. While community sentiment was strongly in favor of [DIP 1 - Safety Module Restoration and Staker Recovery](https://dydx.community/dashboard/proposal/0), the proposal failed because it did not meet the 100M DYDX minimum quorum required for a Long Timelock vote to pass. As a result, Jacob Goh (jteam0x) at DeFiance Capital created [DIP 4 - Safety Module Staker Reimbursement and Compensation](https://dydx.community/dashboard/proposal/2) to reimburse and compensate affected addresses for their missed rewards and inconvenience. [DIP 4](https://dydx.community/dashboard/proposal/2) involved deploying the recovery contract for the users staked tokens and compensating affected addresses an additional 10% from the Rewards Treasury. The DIP was governed by the less stringent governance parameters of a Short Timelock.

The proposal lifecycle of a DIP is generally consistent up until DIP creation. The major difference between DIP 3 (on-chain) and DIP 2 (off-chain) was that DIP 3 required on-chain voting and smart contract deployment. Since the process for forum discussions, DRC creation, and draft DIP creation are the same, we start our step-by-step discussion with the content requirements to draft on-chain DIP. For more information please follow the links below:

* dYdX's governance process - [https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
* Safety Module Incident Report - [https://dydx.foundation/blog/en/outage-1](https://dydx.foundation/blog/en/outage-1).
* Off-Chain Forum discussion **-** [https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause](https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause).
* Off-Chain DRC **-** [https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution](https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution)
* Off-Chain DRC Snapshot Polling **-** [https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn](https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn)
* DIP proposed on Github **-** [https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md)

### **STEP 1 - On-Chain DIP Drafting**

_**Description:**_

Drafting an on-chain DIP that affects governance consensus on the dYdX protocol must outline the specific steps for implementing smart contract changes. After the community achieves rough consensus from Snapshot or a previously failed DIP, a community member with enough proposing power can submit the new DIP on-chain. More information about the proposing power threshold, the timelock executor, and other governance parameters are linked [here](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

_**Application to DIP 3:**_

In this case, the [DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md) was authored by Dan Robinson from Paradigm. Given that the proposal included on-chain smart contract changes, the proposal included a link to the specific smart contract implementations.

![https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](../.gitbook/assets/24.png)

Navigating from the SafetyModuleV2.sol deployment contract to the Safety folder shows the README that contains the specific details of how the proposal will be implemented.

![](../.gitbook/assets/25.png)

The steps to implement the proposal included in the README are linked here: [https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety).

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/26.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/27.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/28.png)

#### _How to draft an On-Chain DIP (WIP):_

* Create a new wallet to create the DIP. The deployment process will require inputting your seed phrase as an environment variable, so we recommend that you use a one-off wallet for on-chain DIP creation.
* Delegate enough proposing power to the one-off wallet for DIP creation. You can delegate proposing power [here.](https://dydx.community/dashboard) The different proposing power thresholds are included below and linked [here](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).
  * Short Timelock: 0.5% of the total supply (5M in proposing power).
  * Starkware Executor: 0.5% of the total supply (5M in proposing power).
  * Long Timelock Executor: 2.0% of the total supply (20M in proposing power).
  * Merkle Pauser Executor: 0.5% of the total supply (5M in proposing power).
* Create an Alchemy Key. With the Alchemy Key, you do not need to run an Ethereum Node to interact with Ethereum and deploy the smart contract. The guide for creating an Alchemy Key is linked [here](https://docs.alchemy.com/alchemy/introduction/getting-started).

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/29.png)

Select Ethereum and “Get Started.”

![](../.gitbook/assets/30.png)

Fill in the required information, select the Ropsten Network and select “create app.”

![](../.gitbook/assets/31.png)

After creating your account, follow the setup instructions linked [here](https://docs.alchemy.com/alchemy/introduction/getting-started).

Under “4. Start Building,” select “try deploying your first smart contract” and follow the guide.

![https://docs.alchemy.com/alchemy/introduction/getting-started](<../.gitbook/assets/32 (1).png>)

* Open Windows command line, the default Terminal App, or download iTerm: [https://iterm2.com/](https://iterm2.com/).
* Download and install Node.js and npm if you have not already: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Hardhat is a development tool to compile and test Ethereum software. Install Hardhat if you have not already: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Draft your proposed smart contract implementation(s).
* The IPFS hash is generated automatically and can be obtained [here](https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips). The IPFS hash will be in the dYdX Foundation's directory under the file name `DIP-[New DIP #]-ipfs-hashes.json`.

![https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips](<../.gitbook/assets/image (40).png>)

* After you select the new file (`DIP-[New DIP #]-ipfs-hashes.jso`), ensure that you use the encodedHash.

![https://github.com/dydxfoundation/dip/blob/master/content/ipfs-dips/DIP-3-Ipfs-hashes.json](<../.gitbook/assets/image (70).png>)

### **STEP 2 - Submit a DIP On-chain**

_**Description:**_

After a community member has confirmed that the proposed smart contract implementation(s) is/are correct and the DIP is finalized, the DIP can be submitted on-chain. When an on-chain DIP is created, the proposal enters a “Pending” state for the Voting Delay that lasts approximately 1 day (approximately 6570 blocks). User snapshots are recorded after the Voting Delay to account for DYDX holdings and delegated voting power. Next, the proposal enters an "Active" state and voting length varies from 2-10 days depending on the proposal type. For a proposal to be implemented, the vote must pass the minimum quorum and minimum vote differential that changes depending on the type of proposal. If the DIP satisfies the minimum quorum, the minimum vote differential, and a majority of voting community members vote in favor of the DIP, any address can call the queue to move the proposal into the timelock queue. The timelock contracts can queue, cancel, or execute transactions voted on by the dYdX community. The length of the timelock queue varies depending on the type of proposal.

_**Application to DIP 3:**_

The Paradigm team finalized the solidity code for `SafetyModuleV2.sol.`

![https://github.com/dydxfoundation/governance-contracts/blob/master/contracts/safety/v2/SafetyModuleV2.sol](../.gitbook/assets/34.png)

The Paradigm team simulated the updates in both a local and forked mainnet environment. The test suite was then run, to ensure that full functionality would be restored, following the execution of the governance proposal on mainnet.

The Paradigm team deployed the smart contract updates by running the scripts below.

**Safety Module Recovery Deployment**

`export ALCHEMY_KEY=<...>`

`export MNEMONIC=<...>`

`npx hardhat --network mainnet deploy:safety-module-recovery`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`

**Governance Proposal: Safety Module Fix**

`export ALCHEMY_KEY=<...>`

`export MNEMONIC=<...>`

`npx hardhat --network mainnet deploy:safety-module-fix-proposal`\
`--proposal-ipfs-hash-hex 0x...`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--long-timelock-address 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B`\
`--safety-module-address 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC`\
`--safety-module-proxy-admin-address 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C`\
`--safety-module-new-impl-address 0x...`

**Governance Proposal: Safety Module Compensation**

`export ALCHEMY_KEY=<...>`

`export MNEMONIC=<...>`

`npx hardhat --network mainnet deploy:safety-module-compensation-proposal`\
`--proposal-ipfs-hash-hex 0x...`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`\
`--safety-module-recovery-address 0x...`

The DIP was simultaneously posted on [https://dydx.community/dashboard](https://dydx.community/dashboard).

![https://dydx.community/dashboard](../.gitbook/assets/35.png)

![https://dydx.community/dashboard](../.gitbook/assets/36.png)

The dYdX Governance contract is 0x7e9b1672616ff6d6629ef2879419aae79a9018d2: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).

The DIP deployment can be confirmed on Etherscan: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

The DIP was created on November 1, 2021, at block 13532376. For 6570 blocks into the future, the DIP status is “Pending.”

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/37.png)

DYDX holders were able to vote on the DIP when it transitioned to an “Active” state at block 13538946.

The first vote was cast on November 2, 2021, at 5:51:22 PM UTC (block 13538959), 6583 blocks from when the DIP was created on-chain.

![https://etherscan.io/tx/0xc3d0ace92be4ac3da40dc17f45a573d4dbd83d31f7a95733071de883ded67a4f](../.gitbook/assets/38.png)

After the 10 day voting period involved with a Long Timelock, any community member can call the queue and move the proposal into the 7 day timelock delay. For DIP 3, it took almost 3 days for a community member to call the queue.

![https://etherscan.io/tx/0x3402372aa549d2270a6b5d4f84884ae2bfec6922fc808703b47d53b27d288c81](../.gitbook/assets/39.png)

After the 7 day timelock delay, the DIP was executed on-chain.

![https://etherscan.io/tx/0xfd332147899fd3ef1db62f262ffae92bbd7d18a5ed4e142eb0407a173dbf0453](../.gitbook/assets/40.png)

At the moment the DIP was executed on-chain the DIPs status at [https://dydx.community/dashboard/proposal/3](https://dydx.community/dashboard/proposal/3) was updated to “Executed.”

![](../.gitbook/assets/41.png)

Note, (1) proposals must be executed within the 7 day Execution Grace Period that starts immediately after the timelock delay and (2) the proposing address must maintain the minimum amount of proposing power required by the respective timelock contract until the DIP is executed (either 5M or 20M in proposing power).

#### _How to Submit a DIP On-Chain:_

* Ensure that you have enough proposing power to create the DIP. More information can be found under[ DIP Creation](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
  * Short Timelock Executor: 0.5% of the total supply (5M in proposing power).
  * Starkware Executor: 0.5% of the total supply (5M in proposing power).
  * Long Timelock Executor: 2.0% of the total supply (20M in proposing power).
  * Merkle Pauser Executor: 0.5% of the total supply (5M in proposing power).
* Ensure that there is ETH in the wallet to pay for the gas fee.
* Create an app on Alchemy for the Ethereum Mainnet network.

![https://dashboard.alchemyapi.io/](../.gitbook/assets/42.png)

* After the app is created, click "View Key" to obtain your Alchemy Key (7LOaQtguSm2kSEcFXQH88B): [https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul](https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul).

![https://dashboard.alchemyapi.io/apps/xogmjmlex8tlmr95](<../.gitbook/assets/image (77).png>)

* Download and install Node.js and npm: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Install Hardhat: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Run the script that you have drafted.
* Check the Governance Contract to verify that the proposal was created on-chain: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).
* With the address that submitted the proposal, you must maintain the minimum amount of proposing power required by the respective timelock contract until the proposal is executed.

#### _How to Vote on a DIP:_

* Ensure that there is ETH in the wallet to pay for the gas fee.
* You may vote on an Active DIP by selecting the DIP from: [https://dydx.community/dashboard](https://dydx.community/dashboard).

![](../.gitbook/assets/43.png)

* In the future, you may also vote on an Active DIP on Commonwealth.

![](../.gitbook/assets/44.png)

The voting length depends on the type of proposal. More information can be found under [DIP Creation](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

* Short Timelock Executor: 4 days.
* Starkware Executor: 4 days.
* Long Timelock Executor: 10 days.
* Merkle Pauser Executor: 2 days.

#### _How to Queue a Proposal:_

A successful proposal can be queued to start the Timelock Delay.

* Ensure that you are using a compatible wallet that contains Eth.
* Go to the "Contract" Tab on Etherscan and click on "Write Contract." The Governance Contract is linked [here](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract).

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/50.png)

* Select queue and submit the “proposalId.”

![](<../.gitbook/assets/Nest (2).png>)

The “proposalId” can be found on Etherscan when the DIP was created: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

* Select “click to see more.”

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/47.png)

* Select “Decode Input Data.”

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/48.png)

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/49.png)

#### _How to Execute a Proposal:_

After the Timelock Delay, a successful proposal can be executed.

* Go to the "Contract" Tab on Etherscan and click on "Write Contract." The Governance Contract is linked [here](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract).

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](<../.gitbook/assets/50 (1).png>)

* Select “execute” and submit the “proposalId.”

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/51.png)

* Follow the steps above (under _How to Queue a Proposal)_ to find the “proposalId.”
* Enter ”0” under “payableAmount (ether).”
