---
description: An overview of the Liquidity Staking Pool
---

# Liquidity Module

`0.6%` of the token supply (`5,753,430 $ethDYDX)`was distributed to users staking $USDC to the Liquidity Staking Pool. Initially, `2.50%` of the token supply (`25,000,000 $ethDYDX`) was allocated to be distributed to users staking $USDC to the Liquidity Staking Pool. The Liquidity Staking Pool is no longer active as of September 29, 2022. In [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), the dYdX community [voted](https://dydx.community/dashboard/proposal/7) to effectively wind down the Liquidity Staking Pool and the Borrowing Pool by setting the Liquidity Staking Pool rewards per second to 0.\
\
Previously, $ethDYDX was distributed to users who staked $USDC to the Liquidity Staking Pool. Community-approved liquidity providers used the staked $USDC to make markets on dYdX v3, furthering the liquidity available across the markets. Liquidity providers were restricted from using borrowed funds outside of dYdX v3.

## **Staking** Overview

Currently, $USDC staked in the Liquidity Staking Pool is not earning rewards.

The 383,562 $ethDYDX previously distirbuted to USDC stakers will accrue in the Rewards Treasury and can be used by the dYdX community with a [governance vote](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## USDC Unstaking & Withdrawals

A staker must request to withdraw $USDC at least `3 days` (**Blackout Window**) before the end of an [**epoch**](../start-here/epochs.md) in order to be able to withdraw the staker's $USDC after the end of that epoch. If stakers do not request to withdraw, their staked $USDC is rolled over into the next epoch.

Withdrawals cannot be requested during the **Blackout Window**.

In [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), the dYdX community [voted](https://dydx.community/dashboard/proposal/7) to reduce the length of the Blackout Window from `14 days` to `3 days`.

## What is stkUSDC?

USDC holders who deposit and stake their $USDC into the Liquidity Staking Pool will receive a tokenized position ($**stkUSDC**). $stkUSDC is minted when a user stakes USDC, and is burned when a user calls `withdrawStake`. In the same transaction that $USDC leaves a staker's wallet, $stkUSDC enters the staker's wallet; or vice-versa when unstaking.

A $stkUSDC balance can be active or inactive. Active $stkUSDC can be transferred as an ERC-20, but cannot be withdrawn. Inactive $stkUSDC can be withdrawn, but cannot be transferred. For example, a user may have 100 active and 100 inactive $stkUSDC in their wallet, and the user's balance will show 200 $stkUSDC, but a transfer will revert if the user tries to transfer more than 100 $stkUSDC.

A staked balance for which the staker has requested a withdraw prior to the end of epoch would be considered inactive, and therefore not transferable.

## FAQ

### What is the Blackout Window?

A blackout window is a period of time during which users cannot request withdrawals of staked $USDC. The`requestWithdrawal`function cannot be called during a blackout window, which is configured as the last `3 days`of an epoch. New epochs start every 28 days. In other words, users can request a withdrawal for the next epoch up to `3 days`before the end of a given epoch.

### How do I withdraw $USDC from the staking pool? How long does it take?

A staker must request to unstake $USDC at least `3 days`before the end of an epoch in order to be able to withdraw the staker's $USDC after the end of that epoch. If stakers do not request to withdraw, their staked $USDC is rolled over into the next epoch.

To withdraw $USDC, users call the`requestWithdrawal`function to request to withdraw $USDC for the next epoch. User funds will remain staked and not withdrawable for the current epoch. Starting in the next epoch, funds will be “inactive” and available for withdrawal.

In the next epoch, users call the `withdrawStake` function to withdraw inactive $USDC to a specific address. Users can select the amount of inactive funds they want to withdraw or call the \`withdrawMaxStake\` function to withdraw all inactive funds. The `withdrawMaxStake` function is less gas-efficient than querying the max via eth\_call and calling `withdrawStake()`.

To unstake $USDC to the Liquidity Pool, following the following steps:

* Go to [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Click on “**Request**”, to open the following modal:

![Requesting withdraw](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* Enter the amount of $USDC you want to request to withdraw from the pool, and click "**Request withdraw**". You will need to pay gas fees to unstake $USDC.
* Stakers who request to unstake $USDC at least `3 days` (**Blackout Window**) before the current epoch ends can withdraw their $USDC at the start of the next epoch.

### What parameters can governance change?

dYdX governance is responsible for:

* Rewards per second for staking $USDC to the Liquidity Staking Pool
* Adding new borrowers to and/or removing existing borrowers from the Staking Liquidity Pool
* Changing allocations of borrowed $USDC to approved borrowers
  * The `setBorrowerAllocations` and `setBorrowingRestriction` functions are called to change the allocations of certain borrowers. They can be used to add and remove borrowers. Increases take effect in the next epoch, but decreases will restrict borrowing immediately. These functions cannot be called during the blackout window.
* Epoch length and blackout window are set upon creating the contract but can be changed
