---
description: High-level overview of governance architecture.
---

# Governance Architecture

## Overview

DYDX grants holders the right to propose and vote on changes to the Protocol. DYDX governance is based on the AAVE governance contracts, and supports voting based on DYDX token holdings.

Proposals must pass a given threshold and percent of yes votes based on the type of proposal.

These DYDX tokens can be used to make proposals or vote on governance proposals or be delegated to other Ethereum addresses.

At a high level, there are 5 smart contracts that support dYdX Governance:

* **The `DYDX Token` contract**: has snapshots of each address’ voting power at different blocks in time.
* **The `Governance Strategy` contract**: contains logic to measure users' relative power to propose and vote.
* **The `Staked dYdX` contract**: contains logics to stake DYDX tokens, tokenize the position and get rewards.
* **The `Governor` contract**: tracks proposals and can execute proposals via the Timelock smart contract.
* **The `Timelock` contract**: can queue, cancel, or execute transactions voted by Governance. The functions in a proposal are initiated by the Timelock contract. Queued transactions can be executed after a delay and until Grace period is not over. 

![](https://lh6.googleusercontent.com/WF98fSJYwpE1ouAElQ998tSOlLVxJw7CD4QNkJ9AtsDY-AXvUiiXUvvArUAWXiUT5VDETct7BC5e6eDWMyTw_jTaKwqp7KIXCyYSp7UWc1p7T9bf-n0epVZ3Jy9134YW-gbs8ZZP)

dYdX on-chain governance allows for:

* Snapshotting token holdings at the start of a proposal
* Delegating separate voting and proposing powers
* Setting governance thresholds including proposals, quorums, and vote differential powers
* Voting on proposals
* Replacing the “Governance Strategy” smart contract, including voting power for staked tokens
* Configuring multiple executor contracts

## Proposal Types

There are four types of proposals with different parameters which affect the length and execution of a proposal, i.e. critical proposals that affect governance consensus require more voting time and a higher vote differential, whereas proposals affecting only protocol parameters require less voting time and can be quickly implemented. An executor must validate each type of proposal.

**Short timelock executor**

The short timelock executor can execute proposals that generally change Rewards and Incentive contracts or the Community Treasury that require quick intervention.

**Long timelock executor**

The long timelock executor can execute proposals that generally change parts of the Protocol that affect governance consensus.

**Merkle-pauser executor**

The Merkle-pauser executor can execute proposals that freeze the Merkle root, which is updated periodically with each user's cumulative reward balance, allowing new rewards to be distributed to users over time, in case the proposed root is incorrect or malicious.

**Starkware executor**

The Starkware executor can execute proposals that generally change parts of the Protocol that currently require intervention from Starkware.

