---
description: A high-level overview of governance architecture.
---

# 🏗️ Architecture

## Overview

$ethDYDX, $stkDYDX and $wethDYDX ("Governance Tokens") grant holders the right to propose and vote on changes to dYdX v3. dYdX governance is based on the AAVE governance contracts, and supports voting based on the holdings of the Governance Tokens.

Proposals must pass a given threshold and percent of yes votes based on the type of proposal.

The voting and proposing powers of the Governance Token enable the Governance Token holder to make proposals and vote on governance proposals. Note, the Governance Token holder may delegate such powers to other Ethereum addresses.

There are 8 smart contracts at the core of dYdX Governance:

* **The `$ethDYDX, $stkDYDX and $wethDYDX Token` contracts**: have snapshots of each address’ voting power at different blocks in time.
* **The `Governance Strategy V2` contract**: contains logic to measure users' relative power to propose and vote. The dYdX Community [voted](https://dydx.community/dashboard/proposal/15) to upgrade the `Governance Strategy` contract to `Governance Strategy V2` to endow $wethDYDX with the same governance functionality as ethDYDX for voting and proposing in dYdX v3 governance.
* **The `Safety Module` contract**: contains logic to stake $ethDYDX tokens, tokenize the position and get rewards. Token staked the safety module retains full governance rights.
* **The `Governor` contract**: tracks proposals and can execute proposals via the Timelock smart contract.
* **The `Timelock` contracts**: can queue, cancel, or execute transactions voted by Governance. The functions in a proposal are initiated by the Timelock contract. Queued transactions can be executed after a delay and before the expiration of the grace period.
* **The `Priority Timelock` contract**: The same as the timelock contract, but allows a priority controller to execute transactions within the **Priority Period** (7 days) before the end of the timelock delay.

![Smart contract architecture](../.gitbook/assets/1-smart-contract-architectue.png)

dYdX on-chain governance allows for:

* Voting on proposals to be executed by any authorized executor contract
* Snapshotting token holdings at the start of a proposal
* Separate delegation of voting and proposing powers
* Setting governance thresholds including proposals, quorums, and vote differential powers
* Changing how votes are counted (by changing the “Governance Strategy” smart contract address on the Governor contract)

## Proposal Types

There are four types of proposals with different parameters that affect the length and execution of a proposal, i.e. critical proposals that affect governance consensus require more voting time and a higher vote differential, whereas proposals affecting only protocol parameters require less voting time and can be quickly implemented. An executor must validate each type of proposal.

#### **Short timelock executor**

The short timelock executor controls the following:

* Incentive contracts including the Liquidity Module, Safety Module, and Merkle Distributor Module
* funds in the Rewards and Community Treasuries
* minting new tokens
* all proxy contracts except the safety module
* guardian roles on stark proxy contracts

**Starkware priority timelock executor**

The Starkware priority timelock executor manages the StarkEx Perpetual Exchange contract, executing proposals that configure dYdX v3. Starkware holds a "priority controller" role, allowing them a 7-day Priority Period to trigger proposal execution. However, protocol changes are solely decided by Governance Token holders through dYdX v3 governance.

#### **Long timelock executor**

The long timelock executor can execute proposals that generally change parts of the dYdX v3 that affect governance consensus.

#### **Merkle-pauser executor**

The Merkle-pauser executor can execute proposals that freeze the Merkle root, which is updated periodically with each user's cumulative reward balance, allowing new rewards to be distributed to users over time, in case the proposed root is incorrect or malicious. It can also veto forced trade requests by any of the stark proxy contracts.

The initial timelock parameters are as follows:

![Initial timelock parameters](../.gitbook/assets/1-initial-timelock-parameters.png)
