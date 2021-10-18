---
description: A high-level overview of governance architecture.
---

# Architecture

## Overview

DYDX grants holders the right to propose and vote on changes to the Protocol. DYDX governance is based on the AAVE governance contracts, and supports voting based on DYDX token holdings.

Proposals must pass a given threshold and percent of yes votes based on the type of proposal.

These DYDX tokens can be used to make proposals or vote on governance proposals or be delegated to other Ethereum addresses.

There are 6 smart contracts at the core of dYdX Governance:

* **The `DYDX Token` contract**: has snapshots of each address’ voting power at different blocks in time.
* **The `Governance Strategy` contract**: contains logic to measure users' relative power to propose and vote.
* **The `Safety Module` contract**: contains logics to stake DYDX tokens, tokenize the position and get rewards. Token staked the safety module retain full governance rights.
* **The `Governor` contract**: tracks proposals and can execute proposals via the Timelock smart contract.
* **The `Timelock` contracts**: can queue, cancel, or execute transactions voted by Governance. The functions in a proposal are initiated by the Timelock contract. Queued transactions can be executed after a delay and before the expiration of the grace period.&#x20;
* **The `Priority Timelock` contract**: The same as the timelock contract, but allows a priority controller to execute transactions within the **Priority Period** (7 days) before the end of the timelock delay.&#x20;

![Smart contract architecture](<../.gitbook/assets/image (49).png>)

dYdX on-chain governance allows for:

* Voting on proposals to be executed by any authorized executor contract
* Snapshotting token holdings at the start of a proposal
* Separate delegation of voting and proposing powers
* Setting governance thresholds including proposals, quorums, and vote differential powers
* Changing how votes are counted (by changing the “Governance Strategy” smart contract address on the Governor contract)

## Proposal Types

There are four types of proposals with different parameters which affect the length and execution of a proposal, i.e. critical proposals that affect governance consensus require more voting time and a higher vote differential, whereas proposals affecting only protocol parameters require less voting time and can be quickly implemented. An executor must validate each type of proposal.

#### **Short timelock executor**

The short timelock executor controls the following:

* Incentive contracts including the Liquidity Module, Safety Module, and Merkle Distributor Module
* funds in the Rewards and Community Treasuries
* minting new tokens
* all proxy contracts except the safety module
* guardian roles on stark proxy contracts

**Starkware priority timelock executor**

The Starkware priority timelock executor owns the StarkEx Perpetual Exchange contract. It can execute proposals that control the configuration of the dYdX Layer 2 Exchange.

Depending on the action to be taken, the Starkware team may need to be involved in order to correctly implement the change on the exchange. For this reason, this executor is provided with a “priority controller” role, which provides Starkware with a period of 7 days (**Priority Period**) in which only they have the ability to trigger execution of a proposal.

Starkware does not have control over _which_ protocol changes are made. Only DYDX tokenholders, via dYdX governance, have the ability to approve or deny changes to the exchange protocol.

#### **Long timelock executor**

The long timelock executor can execute proposals that generally change parts of the Protocol that affect governance consensus.

#### **Merkle-pauser executor**

The Merkle-pauser executor can execute proposals that freeze the Merkle root, which is updated periodically with each user's cumulative reward balance, allowing new rewards to be distributed to users over time, in case the proposed root is incorrect or malicious. It can also veto forced trade requests by any of the stark proxy contracts.

The initial timelock parameters are as follows:

![Initial timelock parameters](<../.gitbook/assets/Initial Timelock Parameters.png>)

