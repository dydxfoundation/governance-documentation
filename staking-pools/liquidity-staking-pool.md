---
description: An overview of the Liquidity Staking Pool
---

# Liquidity Module

`2.50%` of the initial token supply (`25,000,000 DYDX`) will be distributed to users staking USDC to the liquidity staking pool.

### Objectives

* Incentivize the allocation of USDC for market-making purposes on the dYdX Layer 2 protocol.
* Allocate capital to top-performing liquidity providers to increase spread, depth, and uptime on dYdX.

Start staking at [**dydx.community/dashboard/pools/liquidity**](https://dydx.community/dashboard/pools/liquidity)**.**

## **Staking** Overview

Liquidity is a core component of any successful exchange. To promote liquidity network effects and incentivize professional liquidity providers, DYDX will be distributed to users who stake USDC to the liquidity staking pool. Community-approved liquidity providers will use the staked USDC to make markets on the dYdX Layer 2 Protocol, furthering the liquidity available across the markets. Liquidity providers are restricted from using borrowed funds outside of the dYdX Layer 2 Protocol.

Stakers will earn DYDX rewards for staking USDC. DYDX rewards will be distributed continuously according to each staker’s portion of the total USDC in the pool.

Each staker and liquidity provider is required to become party to the Revolving Credit Agreement (link [here](https://dydx.foundation/revolving-credit-agreement)). The agreement puts into natural language the terms of the liquidity staking pool to give each staker an enforceable right against any liquidity provider who does not repay the borrowed USDC. The agreement is only between each staker and each liquidity provider. The dYdX Foundation is not a party to the agreement and has no rights or obligations under it.

## USDC Unstaking & Withdrawals

A staker must request to withdraw USDC at least `14 days` (**Blackout Window**) before the end of an [**epoch**](../start-here/epochs.md) in order to be able to withdraw the staker's USDC after the end of that epoch. If stakers do not request to withdraw, their staked USDC is rolled over into the next epoch.

Withdrawals cannot be requested during the **Blackout Window**.

## Staking Risks

Borrowers from the pool are not required to lock collateral. All borrowers are professional and reputable liquidity providers. The list of allowed borrowers and their pool allocations are updatable by governance.

When users request to withdraw USDC, a borrower’s allocated balance for the next epoch may drop below the borrower's currently borrowed amount. In this situation, the borrower is responsible for paying back the difference between its borrowed and allocated balances before the end of the epoch.

If a borrower fails to repay an owed balance back to the pool by the end of the epoch, it is considered to be in default and is disallowed from borrowing further USDC until the debt is repaid. Stakers may lose USDC in the event a borrower never repays a debt. Stakers can lose a portion of staked USDC if a market maker were to lose USDC and be unable to replenish the liquidity staking pool.

Stakers also are exposed to smart contract risk if there is a vulnerability in the underlying smart contract code. All DYDX & governance smart contracts have been audited and rigorously tested.

To reduce the risk to stakers, each staker and liquidity provider will be required to become party to the Revolving Credit Agreement (link [here](https://dydx.foundation/revolving-credit-agreement)), but entering into the agreement does not ensure that a liquidity provider will repay all amounts borrowed, even if a staker's rights under the agreement are enforced.

## Approved Borrowers

The Liquidity Staking Pool contract operates as a two-sided, under-collateralized, interest-free liquidity system.

The amount that can be withdrawn depends on a borrower's allocation percentage and the total available USDC staked in the pool. Both the allocation percentage and total available USDC can change, at predefined times specified by `LS1EpochSchedule`. The borrowed USDC may only be used on dYdX’s Layer 2 Protocol — this is enforced via the`StarkProxy`contract which interacts with the`StarkEx Perpetual Exchange`contract.

The initially approved liquidity providers include `Wintermute`, `Amber Group`, `Wootrade (Kronos)`, `Sixtant`, and `DAT Trading`, who have been actively market-making on the dYdX Layer 2 Protocol.

| Pre-approved Borrowers | Initial Allocation Percentage | Ethereum Address                                                                                                      | StarkProxy                                                                                                            | Details on Liquidity Providers                                                                                                                                                         |
| ---------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wintermute             | 25%                           | [0x4f3a120E72C76c22ae802D129F599BFDbc31cb81](https://etherscan.io/address/0x4f3a120E72C76c22ae802D129F599BFDbc31cb81) | [0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6](https://etherscan.io/address/0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6) | [https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/](https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/)                             |
| Amber Group            | 25%                           | [0x39Ad99E33ab7Ee85818741dD6076112188bc2611](https://etherscan.io/address/0x39Ad99E33ab7Ee85818741dD6076112188bc2611) | [0x3e6E9EFb0A677a24F47093a22044dc5451A028cF](https://etherscan.io/address/0x3e6E9EFb0A677a24F47093a22044dc5451A028cF) | [https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/](https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/)                           |
| WOO Network (Kronos)   | 20%                           | [0x38d981c3c42b2ec8e9572f560552407d0f1279fb](https://etherscan.io/address/0x38d981c3c42b2ec8e9572f560552407d0f1279fb) | [0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06](https://etherscan.io/address/0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06) | [https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/](https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/) |
| Sixtant                | 20%                           | [0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c](https://etherscan.io/address/0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c) | [0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2](https://etherscan.io/address/0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2) | [https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/](https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/)                                   |
| DAT Trading            | 10%                           | [0x83E8fb8f4DAE0f42d68FdbBf85d4191a5e6f92F8](https://etherscan.io/address/0x83e8fb8f4dae0f42d68fdbbf85d4191a5e6f92f8) | [0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874](https://etherscan.io/address/0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874) | [https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/](https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/)                           |

## Staked Balance Accounting

A staked balance is in one of two states:

* **Active**: Available for borrowing; earns staking rewards; cannot be withdrawn by the staker.
* **Inactive**: Unavailable for borrowing; does not earn rewards; can be withdrawn by the staker.

A staker may have a combination of active and inactive balances. USDC is accounted for epoch-by-epoch as shown in the following example:

![Staked balance accounting](<../.gitbook/assets/image (34).png>)

The following operations affect staked balances as follows:

* **Deposit**: Increase active balance.
* **Request withdrawal**: At the end of the current epoch, move some active USDC to inactive.
* **Withdraw**: Decrease inactive balance.
* **Transfer**: Move some active USDC to another staker.

To encode the fact that a balance may be scheduled to change at the end of a certain epoch, each balance is stored as a struct of three fields: currentEpoch, currentEpochBalance, and nextEpochBalance. Inactive user balances also make use of the shortfallCounter field.

### What is stkUSDC?

USDC holders who deposit and stake their USDC into the Liquidity Staking Pool will receive a tokenized position (**stkUSDC**). stkUSDC is minted when a user stakes USDC, and is burned when a user calls `withdrawStake`. In the same transaction that USDC leaves a staker's wallet, stkUSDC enters the staker's wallet; or vice-versa when unstaking.

A stkUSDC balance can be active or inactive. Active stkUSDC can be transferred as an ERC-20, but cannot be withdrawn. Inactive stkUSDC can be withdrawn, but cannot be transferred. For example, a user may have 100 active and 100 inactive stkUSDC in their wallet, and the user's balance will show 200 stkUSDC, but a transfer will revert if the user tries to transfer more than 100 stkUSDC.

A staked balance for which the staker has requested a withdraw prior to the end of epoch would be considered inactive, and therefore not transferable.

## **Stakers** FAQ

### How do I earn staking rewards?

Stakers can deposit USDC at any time to the liquidity staking pool and start earning rewards immediately. DYDX rewards are earned on a continuous basis according to each staker’s share of the total pool on a second-by-second basis. Rewards can be claimed and withdrawn at any time.

Staked USDC earns rewards for the period of time that it remains active. This means that after requesting a withdrawal of some USDC, that USDC will continue to earn rewards until the end of the epoch. For example:

![Rewards accounting](<../.gitbook/assets/image (65) (1).png>)

In the above scenario, the user would earn rewards for the period from **Time0** to **Time2**, varying with the total staked balance in that period. If the user only requests a withdrawal for a part of the user's balance, then the remaining balance would continue earning rewards beyond **Time2**.

### How do I deposit and stake USDC to the Liquidity Pool?

To stake USDC to the Liquidity Pool, follow these steps:

* Go to [https://dydx.community/dashboard/pools/liquidity](https://dydx.community/dashboard/pools/liquidity)
* Click on “Stake”
* You must enable USDC the first time you deposit. You will only have to do this once and pay gas fees only once.
* Enter the amount of USDC you want to stake to the pool.
* Click “Stake Funds” - you will need to pay gas fees to stake, request to withdraw, and withdraw USDC.

![](<../.gitbook/assets/image (31).png>)

Staked USDC us now active and start earning rewards immediately.

To deposit and stake USDC directly on the smart contract, users call the`stake`function. Users can also deposit and stake USDC on behalf of another address by calling the`stakeFor`function. Even if you stake USDC directly on the smart contract, you will be deemed to have notice of, and reviewed, the Revolving Credit Agreement (link [here](https://dydx.foundation/revolving-credit-agreement)).

### What is the Blackout Window?

A blackout window is a period of time during which users cannot request withdrawals of staked USDC. The`requestWithdrawal`function cannot be called during a blackout window, which is initially configured as the last`14 days`of an epoch. New epochs start every 28 days. In other words, users can request a withdrawal for the next epoch up to`14 days`before the end of a given epoch.

### How do I withdraw USDC from the staking pool? How long does it take?

An epoch schedule is enforced for withdrawals in order to provide predictability and a regular cadence for the availability of USDC in the pool. A staker must request to unstake USDC at least`14 days`before the end of an epoch in order to be able to withdraw the staker's USDC after the end of that epoch. If stakers do not request to withdraw, their staked USDC is rolled over into the next epoch.

To withdraw USDC, users call the`requestWithdrawal`function to request to withdraw USDC for the next epoch. User funds will remain staked and not withdrawable for the current epoch. Starting in the next epoch, funds will be “inactive” and available for withdrawal.

In the next epoch, users call the `withdrawStake` function to withdraw inactive USDC to a specific address. Users can select the amount of inactive funds they want to withdraw or call the \`withdrawMaxStake\` function to withdraw all inactive funds. The `withdrawMaxStake` function is less gas-efficient than querying the max via eth\_call and calling `withdrawStake()`.

To unstake USDC to the Liquidity Pool, following the following steps:

* Go to [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Click on “**Request**”, to open the following modal:

![Requesting withdraw](<../.gitbook/assets/image (68).png>)

* Enter the amount of USDC you want to request to withdraw from the pool, and click "**Request withdraw**". You will need to pay gas fees to unstake USDC.
* Stakers who request to unstake USDC at least 14 days (**Blackout Window**) before the current epoch ends can withdraw their USDC at the start of the next epoch.

### What parameters can governance change?

dYdX governance is responsible for:

* Doing due diligence on existing borrowers
* Adding new borrowers to and/or removing existing borrowers from the Staking Liquidity Pool
* Changing allocations of borrowed USDC to approved borrowers
  * The `setBorrowerAllocations` and `setBorrowingRestriction` functions are called to change the allocations of certain borrowers. They can be used to add and remove borrowers. Increases take effect in the next epoch, but decreases will restrict borrowing immediately. These functions cannot be called during the blackout window.
* Epoch length and blackout window are set upon creating the contract but can be changed

## **Borrowers FAQ**

### **Borrowing**

Staked USDC enters a pool which is allocated to approved borrowers. Each borrower has an allocation percentage controlled by governance and may borrow up to this allocation. Unstaking is subject up an “epoch schedule”—staked USDC may only become withdrawable (i.e. “inactive”) at the start of an epoch.

USDC requested for withdrawal must be returned by borrowers before the end of the epoch. In case of underpayment, the underpaid amount becomes a “debt balance” and the staking contract is re-stabilized. The offending borrower must pay back the debt balance and will be restricted from borrowing until reinstated by governance.

Borrowers are subject to all of the terms of the Revolving Credit Agreement (link [here](https://dydx.foundation/revolving-credit-agreement)).

### **StarkProxy Features**

#### **Auto-Pay**

Borrowers can use `autoPayOrBorrow()` to ensure maximum usage of allocated USDC and timely repayment of requested withdrawals. The function only needs to be called successfully once per epoch for a borrower to ensure they are meeting their responsibilities.

The function will revert if called in the first half of the epoch, since this is outside the blackout window. It will revert if the`StarkProxy`contract does not have enough USDC for repayment. In this case, USDC must be added, or withdrawn from the exchange before calling `autoPayOrBorrow()`.

#### **Borrower-Owned USDC**

A borrower may safely deposit its own USDC to the`StarkProxy`and use its on the dYdX Layer 2 Protocol in the same account as borrowed USDC. USDC may be withdrawn from `StarkProxy` in either of the following situations:

* USDC held within the`StarkProxy`contract in excess of the borrowed balance may be withdrawn at any time.
* Governance may approve a withdrawal of a certain amount.
  * Note: This can be used to allow the borrower to withdraw profits without having to move most USDC off of the dYdX Layer 2 Protocol.

#### **Borrower Roles**

The `StarkProxy`contract supports the following borrower-controlled roles. These may be held by a single address or separate addresses depending on the security needs of the borrower. Each role can be held by any number of addresses.

Owner

* Grant or revoke the delegation admin role.
* Add or remove allowed recipients for USDC withdrawn from `StarkProxy`.
* Add or remove allowed STARK keys for use on the dYdX Layer 2 Protocol.
* Set ERC20 allowances on the `LiquidityStakingV1` and `StarkPerpetual` contracts.
* Call `forcedWithdrawalRequest()` or `forcedTradeRequest()` on the `StarkEx Perpetual Exchange` contract.

Delegation Admin

* Grant or revoke the borrower, exchange operator, and withdrawal operator roles.

Borrower

* Call `autoPayOrBorrow()`, `borrow()`, `repay()`, and `repayDebt()` on the Liquidity Staking contract.

Exchange Operator

* Call `registerUserOnExchange()`, `depositToExchange()`, and `withdrawFromExchange()` on the `StarkEx Perpetual Exchange` contract.

Withdrawal Operator

* Make a valid external withdrawal (see above) out of `StarkProxy` to an allowed recipient.

#### **Limitations**

Layer 2 transfers on the dYdX Layer 2 Protocol are disabled for accounts controlled by a `StarkProxy`.

#### **Guardian Powers**

The guardian role will be controlled by dYdX governance. Its role is to ensure the safety of borrowed USDC and to allow them to be returned to stakers in the case where a borrower’s private key is lost or misused.

The guardian may take the following actions at any time (subject to time-lock):

* Restrict borrowing and depositing of borrowed USDC to the exchange.
* Repay a borrowed balance using USDC in the `StarkProxy` contract.
* Repay a debt balance using USDC in the `StarkProxy` contract.
* Withdraw from the StarkEx contract to the `StarkProxy` contract (e.g. as the second step of a slow withdrawal from the exchange).
* Cancel a forced trade request initiated by the borrower.
* Approve the borrower to withdraw an amount from the `StarkProxy` contract while circumventing the balance check.
* Upgrade the smart contract.

**The guardian may take the following actions if the borrower has an outstanding debt balance (subject to time-lock):**

* Make a forced withdrawal from the dYdX Layer 2 Protocol.
* Make a forced trade (reduce-only) on the dYdX Layer 2 Protocol.

## Staking Risks FAQ

### What are the risks of staking to the liquidity staking pool? What happens if a borrower fails to pay back borrowed funds?

A system for un-collateralized borrowing requires a much higher standard of trust that must be met by a borrower. Liquidity providers borrowing from the liquidity staking pool cannot move borrowed funds outside of the liquidity staking system and dYdX Layer 2 Protocol. Still, staked USDC could be lost if a liquidity provider were to lose funds trading and be unable to replenish its borrowed allocations through external funding sources.

In this event, inactive funds may be subject to socialized losses as laid out below in the event of a shortfall where a borrower is late to pay back funds that have been requested for withdrawal. In case of default on borrowed funds, a delinquent borrower will face significant reputational damage.

Although each staker and borrower is party to the Revolving Credit Agreement (link [here](https://dydx.foundation/revolving-credit-agreement)), this agreement does not provide a guarantee that borrowers will repay their obligations.

### How does the contract maintain solvency?

At any point in time, the contract will be in one of the following states based on the relationship between the staked and borrowed balances:

![Contract Solvency](<../.gitbook/assets/image (80).png>)

The contract is said to be **insolvent**:

* if the total borrowed balance is greater than the total active balance;
* or equivalently, if the total inactive balance is greater than the total unborrowed balance;
* or equivalently, if the total withdrawable balance is greater than the contract’s USDC balance.

Otherwise, the contract is said to be **solvent**.

Because borrowing is limited to a borrower’s allocated proportion of active USDC, and because the inactive balance can only increase between epochs, the contract can typically only move from a solvent to an insolvent state during the transitions between epochs.

If, at the start of a new epoch, the contract is insolvent, is it important to re-stabilize it as soon as possible. Solvency is restored via a mechanism called “debt accounting.” Anytime the contract is insolvent, the `markDebt()` function may be called, by anyone, by specifying a list of borrowers who have exceeded their allocations. The amount by which a borrower's borrowed balance exceeds their allocation is called the borrower's shortfall amount.

When `markDebt()` is called, the shortfall amount of each borrower is moved out of their borrowed balance and into a balance called the debt balance. At the same time, the aggregate of these shortfall amounts is taken out of staker inactive balances and distributed as staker debt receipts. Each staker’s inactive balance will take a haircut, and each staker will receive an equivalent amount in the form of debt. In this way, the loss from insolvency is socialized (pro-rata) across all stakers holding inactive balances.

This process is illustrated below:

![Default](<../.gitbook/assets/image (77).png>)

### What does Debt represent?

In the event of a borrower default, the shortfall amount (up to 100% of inactive balances) is converted from an inactive balance into a debt balance (socialized loss among inactive balance holders). A staker's debt balance does not entitle the staker to withdraw from the pool of staked USDC — it must be paid back specifically in the form of debt repayments.

The Debt represents a receipt for USDC which can later be redeemed for USDC, either when the Borrower makes a debt repayment, or via another means of recuperation as determined by governance.

### What recourses are available to stakers if a borrower defaults?

Stakers and borrowers are parties to the Revolving Credit Agreement (link [here](https://dydx.foundation/revolving-credit-agreement)) which is intended to create an enforceable agreement between each staker and each borrower. In addition, the Liquidity Staking Pool smart contract is designed to give stakers recourse against borrowers, though it cannot guarantee repayment.

When `markDebt()` is called on a borrower, that borrower loses the right to borrow any further funds from the contract. This right can be reinstated by governance.

Once debt has been “marked,” it is removed from the main system of accounting, and can be recovered by stakers in multiple ways. If the indebted borrower pays back the debt (or if another party, such as governance, pays it back on its behalf) then the stakers who were owed the debt may recoup the funds on a first-come, first-served basis. More flexible solutions may be implemented via the “debt operator” interface on the smart contract.

What happens in practice after stakers receive debt will depend on the context. If it was an honest mistake by an approved borrower, stakers can expect to be paid back quickly and in full. If USDC funds were lost, governance can issue a partial repayment to the affected stakers. If the resolution is uncertain, governance may choose to issue an ERC20 receipt to affected stakers, allowing them instant liquidity while waiting for a resolution. If deemed appropriate, governance could choose to issue interest payments to receipt holders until a resolution is reached.

All of these cases are fundamentally supported by the staking contract, but the appropriate response has to be decided on and executed upon by dYdX governance. Depending on the situation, this may require a peripheral smart contract to be written and deployed.
