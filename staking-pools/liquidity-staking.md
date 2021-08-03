---
description: Overview of Liquidity Staking Pools.
---

# Liquidity Staking Pool

2.5% \(`25,000,000 DYDX`\) will be distributed to users staking USDC to a liquidity staking pool.

### Objectives

* Bootstrap dYdX liquidity network effects

## Overview

Liquidity, especially when used properly, is a core component of any successful exchange. To further liquidity network effects and incentivize professional market makers, DYDX will be distributed to users who stake USDC to the liquidity staking pool. Known and approved market makers will use the staked USDC to make markets on the Protocol, furthering liquidity available across the markets. The market makers will not be able to withdraw the USDC from the Protocol, requiring them to use it only in the Protocol. However, a portion of staked USDC could be lost if a market maker were to lose funds \(via unprofitable trading\) and be unable to replenish the liquidity staking pool. Stakers will receive DYDX, distributed continuously according to each staker’s portion of the total USDC in the pool. A staker must request to unstake USDC at least `14 days` \(**Blackout Window**\) before the epoch in order to be able to withdraw their USDC after the end of that epoch. If stakers do not request to withdraw, their staked USDC is rolled over into the next epoch.

## Approved Borrowers

The Liquidity Staking Pool contract operates as a two-sided, undercollateralized lending system.

The amount that can be withdrawn depends on a borrower's allocation percentage and the total available funds staked in the pool. Both the allocation percentage and total available funds can change, at predefined times specified by `LS1EpochSchedule`. The borrowed funds may only be used on dYdX’s Layer 2 exchange. This is enforced via the `TrustedBorrowerL2Proxy` contract which interacts with the L2 exchange contract \(`StarkPerpetual`\).

The initial approved liquidity providers include `Wintermute`, `Sixtant`, `Kronos`, `Amber`, and `MGNR`, who have been actively market-making on the Protocol since launch.

| Pre-approved Borrowers | Initial Allocation Percentage | Details on Liquidity Providers |
| :--- | :--- | :--- |
| Wintermute | `X%` TBD | [https://dydx.exchange/blog/ama-recap-wintermute](https://dydx.exchange/blog/ama-recap-wintermute) |
| Sixtant | Y% TBD | [https://dydx.exchange/blog/ama-recap-sixtant](https://dydx.exchange/blog/ama-recap-sixtant) |
| Kronos \(Wootrade\) | Z% TBD | [https://dydx.exchange/blog/ama-recap-wootrade](https://dydx.exchange/blog/ama-recap-wootrade) |
| Amber | Z% TBD |  |
| MGNR | Z% TBD |  |

When users request to unstake funds, a borrower’s allocated balance for the next epoch may drop below their currently borrowed amount. In this situation, the borrower is responsible for paying back the difference between their borrowed and allocated balances before the end of the epoch. If a borrower's borrowed balance is greater than their allocation at the start of the next epoch then they are expected and trusted to return the difference before the start of that epoch.

As borrowers borrow and repay funds, their net borrowed balance is recorded. The total net borrowed balance across all borrowers is tracked as well. The remaining balance held by the contract is called the unborrowed balance.

The following equality holds true at all times when considering the contract as a whole:

total active + total inactive = total borrowed + total unborrowed

### Governance

dYdX Governance is responsible for:

* Doing due diligence on existing borrowers
* Adding new borrowers to the Staking pool 
* Changing allocations of borrowed funds to approved borrowers
  * The \`setBorrowerAllocations\` and \`setBorrowingRestriction\` functions are called to change the allocations of certain borrowers. They can be used to add and remove borrowers. Increases take effect in the next epoch, but decreases will restrict borrowing immediately. These functions cannot be called during the blackout window.
* Epoch length and blackout window are set upon creating the contract but can be changed by dYdX governance

### Staked Balance Accounting

A staked balance is in one of two states:

* active: Available for borrowing; earning staking rewards; cannot be withdrawn by staker.
* inactive: Unavailable for borrowing; does not earn rewards; can be withdrawn by the staker.

A staker may have a combination of active and inactive balances. Funds are accounted for epoch-by-epoch as shown in the following example:

The following operations affect staked balances as follows:

* deposit: Increase active balance.
* request withdrawal: At the end of the current epoch, move some active funds to inactive.
* withdraw: Decrease inactive balance.
* transfer: Move some active funds to another staker.

To encode the fact that a balance may be scheduled to change at the end of a certain epoch, we store each balance as a struct of three fields: currentEpoch, currentEpochBalance, and nextEpochBalance. Inactive user balances also make use of the shortfallCounter field.

## FAQ

### How do I earn staking rewards?

Stakers can deposit USDC at any time to the liquidity staking pool and start earning rewards immediately. DYDX rewards are earned on a continuous basis according to each staker’s share of the total pool. Rewards can be claimed and withdrawn at any time.

### How do I deposit and stake USDC to the Liquidity Pool?

To deposit and stake and funds, users call the \`stake\` [function](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59). Users can also deposit and stake on behalf of another address by calling the \`stakeFor\` [function](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64).

To stake USDC to the Liquidity Pool, following the following steps:

* Click on “Stake”
* You must enable USDC the first time you deposit. You will only have to do this once.
* Enter the amount of USDC you want to stake to the pool
* Click “Stake Funds” - you will need to pay gas fees to stake and unstake funds

![](https://lh4.googleusercontent.com/caSDz783Gi-asRNYP8Gm8L5qv_yAuJZwEmUAfl8I1MfHecIF2In10IQCqZBCIpxeXl90eT28GGLbZyts8-x9U5w4Y6LBC4kyehMEalsZu_-aI11S6V7nwPrwtcc75m2M8847jFvv)

Staked funds are active and start earning rewards immediately.

### Rewards Accounting

Active funds earn rewards for the period of time that they remain active. This means, after requesting a withdrawal of some funds, those funds will continue to earn rewards until the end of the epoch. For example:

In the above scenario, the user would earn rewards for the period from t\_0 to t\_2, varying with the total staked balance in that period. If the user only requests a withdrawal for a part of their balance, then the remaining balance would continue earning rewards beyond t\_2.

### What is the blackout window?

A blackout window is a period of time during which users cannot request withdrawals of staked funds. The \`requestWithdrawal\` function cannot be called during a blackout window, which is initially configured as the last 14 days of an epoch. New epochs start every 28 days. In other words, users can request a withdrawal for the next epoch up to 7 days before the end of a given epoch.

### How do I withdraw funds from the staking pool? How long does it take?

An epoch schedule is enforced for withdrawals in order to provide predictability and a regular cadence for the availability of funds in the pool. A staker must request to unstake funds at least 14 days before the end of an epoch in order to be able to withdraw their funds after the end of that epoch. If stakers do no request to withdraw, their staked USDC is rolled over into the next epoch

To withdraw funds, users call the \`requestWithdrawal\` [function](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L73-L83) to request to withdraw funds for the next epoch. User funds will remain staked and not withdrawable for the current epoch. Starting in the next epoch, funds will be “inactive” and available for withdrawal.

In the next epoch, users call the \`[withdrawStake](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L91)\` function to withdraw inactive funds to a specific address. Users can select the amount of inactive funds they want to withdraw or call the \`withdrawMaxStake\` function to withdraw all inactive funds. The \`withdrawMaxStake\` function is less gas-efficient than querying the max via eth\_call and calling \`withdrawStake\(\)\`.

### What are the risks of staking to the liquidity staking pool? What happens if a borrower fails to pay back its debt?

Uncollateralized loans come with a much higher standard of trust that must be met by a borrower. Liquidity providers cannot withdraw staked USDC from the Protocol, requiring them to use it only in the Protocol. However, staked USDC could be lost if a liquidity provider were to lose funds trading and be unable to replenish their borrowed allocations through external funding sources.

In this event, inactive funds may be subject to pro-rata socialized losses in the event of a shortfall where a borrower is late to pay back funds that have been requested for withdrawal. In case of default on an uncollateralized loan, a delinquent borrower will face significant reputational damage.

Contract solvency:

At any point in time, the contract will be in one of the following states based on the relationship between the staked and borrowed balances:

| ![](https://lh3.googleusercontent.com/nTJuAC4WSmhOiAGkM6r-YWzy6z2MIHQnydr8U0n-TReAh_gfqD6ZyalxQpYv9RNBsJzrlw78QB_wp9utqBc-PQZipwzWpxDifD1_zEtyVBhYXRl_f8V-iDMwLBO70LQsftDlXrsr) | ![](https://lh3.googleusercontent.com/x_Yev8ZJrYYm8FTDSdoj0jDXEBY_b9xOC69lpQudQdoALQ_tuQFEbFc5hAU6TbpGNCB6J2BsjMwHb59GrCqR52747j45jSC_BmyzyiY72gTRk4oamv35gO8PPZalA43COZF1pgtP) |
| :--- | :--- |
| ![](https://lh6.googleusercontent.com/wX37DQoW9oR4OhJzb4hc5ZxPE1X05OPfyETbUv7WTY0b__WH2PydjJoBuQIREHgeWL18GDn7E1ORgGmcre0R6iYPmwSsdFNzBZ7DBPs0wkajjoDBjxDYDPHcet_-dPPAyS1GWL0v) |  |

The contract is said to be insolvent if:

* the total borrowed balance is greater than the total active balance
* equivalently: the total inactive balance is greater than the total unborrowed balance
* equivalently: the total withdrawable balance is greater than the contract’s USDC balance

Otherwise, the contract is said to be solvent.

Because borrowing is limited to a borrower’s allocated proportion of active funds, and because the inactive balance can only increase between epochs \(except in the case of “naked” USDC transfers to the contract\), the contract can typically only move from a solvent to an insolvent state during the transitions between epochs.

An individual borrower will always have at least a week’s notice before their own allocated balance falls below their outstanding borrowed balance. Such a transition can only happen between epochs.

While the contract is insolvent, users may be unable to withdraw all the funds they are owed. Furthermore, the situation poses additional risks if there is any uncertainty around whether the shortfall will be addressed, and how quickly:

1. Users may be disincentivized from staking additional funds, since doing so may put them in a position where they can’t get their funds back.
2. Currently staked users may be incentivized to “run for the exit” and withdraw as soon as possible, in order to maximize their chances of getting their funds back.

Losses are tracked via indexes which represent the fraction of inactive funds that were converted into debt during a given shortfall event. Each staker inactive balance stores a cached shortfall counter, representing the number of shortfalls that occurred in the past relative to when the balance was last updated. Any losses incurred by an inactive balance translate into an equal credit to that staker's debt balance. See LS1DebtAccounting for more info about how the index is calculated.

If the contract is insolvent, the markDebt\(\) function may be called \(by anyone\), targeting a borrower who has exceeded their allocation. The amount by which their borrowed balance exceeds their allocation balance is called their debt balance. The amount of the debt balance is moved out of their borrowed balance and into a special balance used specifically to account for unpaid shortfall debt.

An equal adjustment is made to the accounting of staked funds. An amount equal to the debt amount is removed from inactive balances and added to a special balance accounting for shortfall debt owed to stakers. Each staker’s inactive balance will take a haircut, and they will receive an equivalent amount in the form of debt. In this way, the loss from insolvency is socialized \(pro-rata\) across all stakers holding inactive balances.

This process is illustrated below:

![](https://lh5.googleusercontent.com/2b2e67wVF3DL32NU0ykTVV0PJWaJ_bdmRQRKgx-5c3_qr_nWNYsuE77JviLtbBxXzASEfIp2Fw4hvzRPeM1a7TAIxq0NYUfo3dZLUhChilDpa5Ygq-YugSvNXKmyf2ul3GQM22SZ)

If the indebted borrower pays back the debt \(or if another party, such as governance, pays it back on their behalf\) then the stakers who were owed the debt may recoup the funds on a first-come first-served basis.

### What does Debt represent?

The Deb

### Is there any recourse for stakers if a borrower defaults?

When markDebt\(\) is called on a borrower, that borrower loses the right to borrow any further funds from the contract. This right can be reinstated by governance.

Potentially add content on market maker agreement with the Foundation

