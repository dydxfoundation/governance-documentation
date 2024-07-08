---
description: An overview of the Safety Staking Pool
---

# 🔐 Safety Module

`0.5%` of the token supply (`5,289,939 $ethDYDX)`was distributed to users staking $ethDYDX to a Safety pool for backstopping the system. Initially, `2.50%` of the token supply (`25,000,000 $ethDYDX`) was allocated to be distributed to users staking ethDYDX to the Safety Module. The Safety Module is no longer active as of November 28, 2022. In [DIP 17](https://dydx.community/dashboard/proposal/9), the dYdX community [voted](https://dydx.community/dashboard/proposal/7) to effectively wind down the Safety Module by setting the Safety Module rewards per second to 0.

Previously, $ethDYDX was distributed to users who staked $ethDYDX to the Safety Module. The Safety module was a decentralized fund which was to be used in the case of insolvency or other issues with the dYdX protocol.&#x20;

$ethDYDX staked in the Safety Module retains its proposing and voting rights, as well as delegation abilities.

## Overview

Currently, $ethDYDX staked in the Safety Module is not earning rewards.&#x20;

The 383,562 $ethDYDX previously distributed to $ethDYDX stakers will accrue in the dYdX Chain Community Treasury and can be used by the dYdX community with a [governance vote](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## DYDX Unstaking & Withdrawals

Stakers must request to withdraw funds at least `3 days` **(Blackout Window)** before the end of the epoch in order to be able to withdraw ethDYDX after the end of that epoch. If stakers do not request to withdraw, their staked $ethDYDX is rolled over into the next epoch.

Withdrawals cannot be requested during the **Blackout Window**.

In [DIP 17](https://dydx.community/dashboard/proposal/9), the dYdX community [voted](https://dydx.community/dashboard/proposal/7) to reduce the length of the Blackout Window from `14 days` to `3 days`.

## FAQ

<details>

<summary>What is the blackout window?</summary>

A blackout window is a period of time during which users cannot request withdrawals of $stkDYDX. The`requestWithdrawal`function cannot be called during a blackout window, which is configured as the last `3 days`of an epoch. New epochs start every 28 days. In other words, users can request a withdrawal for the next epoch up to `3 days`before the end of a given epoch.

</details>

<details>

<summary>How do I withdraw funds from the staking pool? How long does it take?</summary>

An epoch schedule is enforced for withdrawals in order to provide predictability and a regular cadence for the availability of funds in the pool. A staker must request to withdraw funds at least `3 days` before the end of an epoch in order to be able to withdraw their funds after the end of that epoch. If stakers do not request to withdraw, their staked $ethDYDX is rolled over into the next epoch.

To withdraw funds, users call the `` `requestWithdrawal` `` function to request to withdraw funds for the next epoch. User funds will remain staked and not withdrawable for the current epoch. Starting in the next epoch, funds will be “inactive” and available for withdrawal.

In the next epoch, users call the `` `withdrawStake` `` function to withdraw inactive funds to a specific address. Users can select the amount of inactive funds they want to withdraw or call the `` `withdrawMaxStake` `` function to withdraw all inactive funds. Note that the `` `withdrawMaxStake` `` function is less gas-efficient than querying the max via eth\_call and calling `` `withdrawStake()` ``.

To withdraw $ethDYDX from the Safety Module, follow these steps:

* Go to [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Click on “**Request**”, and enter the amount of $ethDYDX you want to request to withdraw from the pool.
* Click “**Request withdraw**”. You will need to pay gas fees to withdraw funds.
* Stakers who request to withdraw $ethDYDX at least `3 days` before the current epoch ends can withdraw their $ethDYDX at the start of the next epoch.

</details>

