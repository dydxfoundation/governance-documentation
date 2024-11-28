---
description: An overview of the Liquidity Staking Pool
---

# 🔋 Liquidity Module

The Liquidity Staking Pool is no longer active as of September 29, 2022. In [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), the dYdX community [voted](https://dydx.community/dashboard/proposal/7) to effectively wind down the Liquidity Staking Pool and the Borrowing Pool by setting the Liquidity Staking Pool rewards per second to 0.

All remaining ethDYDX from the Liquidity Module Rewards allocation were migrated to the dYdX Chain Community Treasury.

More information about the dYdX Chain Community Treasury is available [here](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules-and-parameters/community-treasury).&#x20;

## **Staking** Overview

Currently, $USDC staked in the Liquidity Staking Pool is not earning rewards.

## USDC Unstaking & Withdrawals

A staker must request to withdraw $USDC at least `3 days` (**Blackout Window**) before the end of an [**epoch**](../start-here/epochs.md) in order to be able to withdraw the staker's $USDC after the end of that epoch. If stakers do not request to withdraw, their staked $USDC is rolled over into the next epoch.

Withdrawals cannot be requested during the **Blackout Window**.

## FAQ

<details>

<summary>What is the Blackout Window?</summary>

A blackout window is a period of time during which users cannot request withdrawals of staked $USDC. The`requestWithdrawal`function cannot be called during a blackout window, which is configured as the last `3 days`of an epoch. New epochs start every 28 days. In other words, users can request a withdrawal for the next epoch up to `3 days`before the end of a given epoch.

</details>

<details>

<summary>How do I withdraw $USDC from the staking pool? How long does it take?</summary>

A staker must request to unstake $USDC at least `3 days`before the end of an epoch in order to be able to withdraw the staker's $USDC after the end of that epoch. If stakers do not request to withdraw, their staked $USDC is rolled over into the next epoch.

To withdraw $USDC, users call the`requestWithdrawal`function to request to withdraw $USDC for the next epoch. User funds will remain staked and not withdrawable for the current epoch. Starting in the next epoch, funds will be “inactive” and available for withdrawal.

In the next epoch, users call the `withdrawStake` function to withdraw inactive $USDC to a specific address. Users can select the amount of inactive funds they want to withdraw or call the \`withdrawMaxStake\` function to withdraw all inactive funds. The `withdrawMaxStake` function is less gas-efficient than querying the max via eth\_call and calling `withdrawStake()`.

To unstake $USDC to the Liquidity Pool, following the following steps:

* Go to [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Click on “**Request**”
* Enter the amount of $USDC you want to request to withdraw from the pool, and click "**Request withdraw**". You will need to pay gas fees to unstake $USDC.
* Stakers who request to unstake $USDC at least `3 days` (**Blackout Window**) before the current epoch ends can withdraw their $USDC at the start of the next epoch.

</details>

###
