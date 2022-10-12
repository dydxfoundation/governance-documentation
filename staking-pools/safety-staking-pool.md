---
description: An overview of the Safety Staking Pool
---

# Safety Module

`2.50%` of the initial token supply (`25,000,000 DYDX`) will be distributed to users staking DYDX to a Safety pool for backstopping the system.

**Objectives**

* Bootstrap a decentralized fund to be used in the case of insolvency or other issues with the protocol.
* Incentivize DYDX holders to govern correctly: DYDX holders risk dilutive events as the ultimate backstop and act as the governors of risk in the system.

DYDX staked in the Safety Module retains its proposing and voting rights, as well as delegation abilities.

Start staking at [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*

## Overview

User safety and protection have been a key focus since the launch of the Protocol. For that reason, DYDX will be distributed to users who stake DYDX to the safety pool to create an additional safety net for users of the Protocol. Stakers will receive DYDX continuously proportional to their portion of the total DYDX in the pool.

The Safety pool will go live upon DYDX becoming transferrable on September 8th, 2021, 15:00 UTC.

## Withdrawals

Stakers must request to withdraw funds at least `14 days` **(Blackout Window)** before the end of the epoch in order to be able to withdraw funds after the end of that epoch. If stakers do not request to withdraw, their staked DYDX is rolled over into the next epoch.

## Risks

Staked DYDX may be slashed as a result of a shortfall event. Slashing occurs at the discretion of DYDX governance, and requires a governance vote to enact.

Like participants in any DeFi protocol, stakers in the Safety Module are exposed to smart contract risk if there is a vulnerability in the underlying smart contract code. All DYDX & governance smart contracts have been audited and rigorously tested.

## Shortfall Events

The interpretation for the occurrence of a Shortfall Event is subject to a dYdX governance vote but may include:

* Exchange Solvency (e.g., exchange becoming under-collateralized due to unprofitable liquidations)
* Smart contract attacks
* Other events dYdX governance deems to have resulted in a shortfall

In a Shortfall Event, token holder balances can be slashed and transferred to another address or contract (set by dYdX governance on a case by case basis). dYdX governance must pass a short timelock proposal to slash staked tokens. After a governance vote on slashing staked DYDX tokens, slashed DYDX may be auctioned on the market to be sold against the assets needed to mitigate the incurred deficit.

## FAQ

### How do I earn staking rewards?

Stakers can deposit DYDX at any time to the safety staking pool and start earning rewards immediately. DYDX rewards are earned on a continuous basis according to each staker’s share of the total pool on a second-by-second basis. Rewards can be claimed and withdrawn at any time.

Active funds earn rewards for the period of time that they remain active. This means, after requesting a withdrawal of some funds, those funds will continue to earn rewards until the end of the epoch. This is demonstrated in the following example from the [Liquidity staking pool](https://docs.dydx.community/dydx-governance/staking-pools/liquidity-staking-pool):

![](<../.gitbook/assets/image (65).png>)

In the above scenario, the user would earn rewards for the period from **Time0** to **Time2**, varying with the total staked balance in that period. If the user only requests a withdrawal for a part of their balance, then the remaining balance would continue earning rewards beyond **Time2**.

### How do I deposit and stake DYDX to the Safety Pool?

To stake DYDX to the Safety Pool, follow these steps:

* Go to [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Click on “**Stake**”
* You must enable DYDX the first time you deposit. You will only have to do this once and incur gas fees only once.
* Enter the amount of DYDX you want to stake to the pool.
* Click “**Stake Funds**”. You will need to pay gas fees to stake and unstake funds.

Staked funds are now active and start earning rewards immediately.

To deposit and stake and funds directly on the smart contract, users call the \`stake\` [function](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59). Users can also deposit and stake on behalf of another address by calling the \`stakeFor\` [function](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64).

### What is stkDYDX?

To contribute to the safety of the protocol and receive incentives, DYDX holders will deposit their tokens into the Safety Module. In return, they will receive a tokenized position (**stkDYDX**) that can be withdrawn or transferred as an ERC-20. The **stkDYDX** token has the same proposing and voting rights as DYDX on dYdX governance.

### What is the blackout window?

A blackout window is a period of time during which users cannot request withdrawals of staked funds. An epoch schedule is enforced for withdrawals in order to provide predictability and a regular cadence for the availability of funds in the pool. A staker must request to unstake funds before the blackout window in order to be able to withdraw their funds after the end of that epoch. If a staker does not request to withdraw, their staked funds are rolled over into the next epoch.

The recommended blackout window for the Safety Pool is `14 days`.

### How does staked balance accounting work?

A staked balance is in one of two states:

* **Active**: Available for borrowing; earning staking rewards; cannot be withdrawn by staker.
* **Inactive**: Unavailable for borrowing; does not earn rewards; can be withdrawn by the staker.

A staker may have a combination of active and inactive balances. Funds are accounted for epoch-by-epoch as shown in the following example:

![](<../.gitbook/assets/image (36).png>)

The following operations affect staked balances as follows:

* **Deposit**: Increase active balance.
* **Request** **withdrawal**: At the end of the current epoch, move some active funds to inactive.
* **Withdraw**: Decrease inactive balance.
* **Transfer**: Move some active funds to another staker.

To encode the fact that a balance may be scheduled to change at the end of a certain epoch, we store each balance as a struct of three fields: currentEpoch, currentEpochBalance, and nextEpochBalance.

### How do I withdraw funds from the staking pool? How long does it take?

An epoch schedule is enforced for withdrawals in order to provide predictability and a regular cadence for the availability of funds in the pool. A staker must request to withdraw funds at least `14 days` before the end of an epoch in order to be able to withdraw their funds after the end of that epoch. If stakers do not request to withdraw, their staked DYDX is rolled over into the next epoch.

To withdraw funds, users call the \`requestWithdrawal\` function to request to withdraw funds for the next epoch. User funds will remain staked and not withdrawable for the current epoch. Starting in the next epoch, funds will be “inactive” and available for withdrawal.

In the next epoch, users call the \`withdrawStake\` function to withdraw inactive funds to a specific address. Users can select the amount of inactive funds they want to withdraw or call the \`withdrawMaxStake\` function to withdraw all inactive funds. Note that the \`withdrawMaxStake\` function is less gas-efficient than querying the max via eth\_call and calling \`withdrawStake()\`.

To withdraw DYDX from the Liquidity Pool, follow these steps:

* Go to [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Click on “**Request**”, and enter the amount of DYDX you want to request to withdraw from the pool.
* Click “**Request withdraw**”. You will need to pay gas fees to withdraw funds.
* Stakers who request to withdraw DYDX at least 14 days before the current epoch ends can withdraw their DYDX at the start of the next epoch.

### What are the risks for stakers to the safety staking pool? What happens in the case of a Shortfall Event?

A staker’s decision to lock DYDX into the Safety Pool exposes them to the risk of a shortfall event, which can result in the slashing of staked DYDX funds at the discretion of DYDX governance.

All funds in the contract, active or inactive, are slashable. Within the contract, slashing is implemented via an update to the exchange rate between DYDX and stkDYDX. This means that as slashes occur, the exchange rate between DYDX and stkDYDX will diverge from its initial value of 1:1. Note that the earning of staking rewards is unaffected by slashes.
