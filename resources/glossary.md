---
description: Overview of key governance-related terms.
---

# Glossary

**DYDX:** The native asset of the DYDX ecosystem, which constitutes the foundation of governance and safety for the dUdX Protocol. DYDX is an ERC-20 token that designates the weight of a user’s voting or proposing power.

**dYdX Protocol:** dYdX’s Layer 2 perpetuals protocol.

**dYdX Foundation:** an independent foundation, headquartered in Zug, Switzerland, was created to participate in propelling the dYdX Protocol into the future.

**DYDX Token contract**: has snapshots of each address’ voting power at different blocks in time.

**DIP: **dYdX Improvements Proposals are on-chain proposals.

**DRC**: dYdX Request for Comments are off-chain proposals and the first required step in the governance improvement process.

**Quorum:** In order for a vote to pass, it must achieve a minimum quorum of DYDX tokens in the affirmative. The purpose of the quorum is to ensure that the only measures that pass have adequate voter participation.

**Epoch:** All other contracts operate on 28-day cycles, referred to as epochs.

**Execution Grace Period: **The period after vote when a DIP proposa becomes executable, during which it must be executed.

**Governance Strategy contract**: contains logic to measure users' relative power to propose and vote.

**Governor contract**: tracks proposals and can execute proposals via the Timelock smart contract.

**Long timelock executor: **The long timelock executor can execute proposals that generally change parts of the Protocol that affect governance consensus.

**Merkle-pauser executor: **The Merkle-pauser executor can execute proposals that freeze the Merkle root, which is updated periodically with each user's cumulative reward balance, allowing new rewards to be distributed to users over time, in case the proposed root is incorrect or malicious.

**Safety Pool:** Component in charge of shielding the protocol from insolvency.

**Staked dYdX contract**: contains logics to stake DYDX tokens, tokenize the position and get rewards.

**Short timelock executor: **The short timelock executor can execute proposals that generally change Rewards and Incentive contracts or the Community Treasury that require quick intervention.

**Starkware executor: **The Starkware executor can execute proposals that generally change parts of the Protocol that currently require intervention from Starkware.

**Timelock contract**: can queue, cancel, or execute transactions voted by Governance. The functions in a proposal are initiated by the Timelock contract. Queued transactions can be executed after a delay and until Grace period is not over.&#x20;

**Timelock Delay: **The delay before a DIP proposal is executed after a proposal passes and is queued.

**Proposal Theshold: **To prevent a system where countless spam proposals are created, a proposal threshold requires an address has a certain number of votes before they can make a proposal.

**Proposing Power:** Token stake giving access to creating and sustaining a proposal.

**Voting Power:** Voting power which is used to vote for or against existing proposals.

**Voting Delay: **This is the length of time between which a proposal can be created and it is available to be voted upon. By requiring at least one block to pass, the governance is protected from Flash Loan attacks that might borrow a large number of tokens, propose a vote, and vote on it all in one block.

**Voting Period:** Once a DIP proposal has been put forward, DYDX community members will have to cast their votes before the end of the Voting Period. This is the length of time for which proposals are available to be voted upon, with time in Ethereum Blocks.

**Proposal Threshold: **Minimum tokens held/delegated required to create a DIP proposal.

**Vote Differential: **Required yes–no gap for DIP proposal to pass.
