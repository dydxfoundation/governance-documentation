---
description: Overview of governance paramaters.
---

# Governance Parameters

At the time of launching governance, DYDX holders have immediate and irrevocable control over:

* The community treasury
* New token listings on the Protocol
* Risk parameters for the Protocol
* Capital allocations to market makers in the liquidity staking pool
* Addition of new market makers to the liquidity staking pool
* Determining safety staking pool payouts in the event of a loss
* Changing any of the rewards and pools existing at launch
* The governance contracts themselves

dYdX Governance has control over the parameters of the following contracts:

* [Timelock](https://github.com/dydxfoundation/governance-docs/tree/28153eacbdaafb32078630fafa7ad64f111ac9ab/voting-and-governance-process/parameters.md#timelock-parameters)
* [Governor](governance-parameters.md#governor-parameters)
* DYDX Token
* Treasury
* Merkle Distributor
* Liquidity Staking
* Safety Module
* Stark Proxy
* Stark Perpetual

## Timelock Parameters

| Parameter | Description | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Proposal Threshold | Minimum tokens held/delegated to create proposal | 0.5% of total supply | 0.5% of total supply | 2% of total supply | 0.5% of total supply |
| Minimum Quorum | Min yes votes for proposal to pass | 2% of total supply | 1% of total supply | 10% of total supply | 2% of total supply |
| Vote Differential | Required yes–no gap for proposal to pass | 0.5% of total supply | 0.5% of total supply | 10% of total supply | 0.5% of total supply |
| Voting Duration | Period during which votes are counted | 4 days | 2 days | 10 days | 7 days |
| Timelock Delay | After proposal passes and is queued, delay before proposal is executed | 2 days | 0 days | 7 days | 2 days |
| Execution Grace Period | Period after vote when proposal can be executed | 7 days | 7 days | 7 days | 7 days |
| Minimum Timelock Delay | Minimum delay before proposal is executed \(after queuing\) | 1 day | 0 days | 5 days | 1 day |
| Maximum Timelock Delay | Maximum delay before proposal is executed \(after queuing\) | 7 days | 1 day | 21 days | 7 days |

## Governor Parameters

| Parameter | Description |  |
| :--- | :--- | :--- |
| Voting Delay | Delay \(in blocks\) between proposal creation and voting on the proposal | 6,570 block |
| Add Executor Admin | Address that can add new executors | Short Timelock |
| Owner role | Can change strategy / voting delay / unauthorize executors + owns other roles | Long Timelock |

## 

<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Short Timelock Executor</th>
      <th style="text-align:left">Merkle-Pauser Executor</th>
      <th style="text-align:left">Long Timelock Executor</th>
      <th style="text-align:left">Starkware Executor</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Voting Delay</td>
      <td style="text-align:left">Delay (in blocks) between proposal creation and voting on the proposal</td>
      <td
      style="text-align:left"></td>
        <td style="text-align:left"></td>
        <td style="text-align:left"></td>
        <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Add Executor Admin</td>
      <td style="text-align:left">
        <ul>
          <li>Add new addresses to the list of authorized executors</li>
        </ul>
      </td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
    </tr>
    <tr>
      <td style="text-align:left">Owner Role</td>
      <td style="text-align:left">
        <ul>
          <li>Set new GovernanceStrategy</li>
          <li>Set new Voting Delay</li>
          <li>Remove addresses to the list of authorized executors</li>
          <li>Owns others roles</li>
        </ul>
      </td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">N</td>
    </tr>
  </tbody>
</table>

## Treasury Vester

| Parameter | Description |  |
| :--- | :--- | :--- |
| Owner | Can update whitelist; can mint | Short Timelock |
| Tranfers restricted before | Minimum timestamp \(in seconds\) that allows transfers | July 14th 15:00 UTC + 28 days + 7 days + 1 day |
| MintMaxPercent | Maximum percentage owner of token can mint \(after minting restrictions end\) | 2 |

## Merkle Distributor

| Parameter | Description | Rewards Treasury | Community Treasury |
| :--- | :--- | :--- | :--- |
| Recipient | Address that receives vested funds | Rewards Treasury | Community Treasury |
| Vesting Amount + Frontloaded Amount | Amount of tokens that will be immediately sent + vested to recipient | 450,000,000 | 50,000,000 |
| Vesting Amount | Amount of tokens that will be vested to recipient | 374,616,438 | 50,000,000 |
| Frontloaded Amount | Amount of tokens to be immediately sent to recipient | 75,383,562 | 0 |
| Vesting Begin | Time when vesting begins | July 14th 15:00 UTC | July 14th 15:00 UTC |
| Vesting Cliff | Time when vesting cliff begins \(and tokens can actually be sent to recipient\) | July 14th 15:00 UTC | July 14th 15:00 UTC |
| Vesting End | Time when vesting ends | July 14th 15:00 UTC + 5 years | July 14th 15:00 UTC + 5 years |
| Treasury Proxy Admin | Can upgrade treasury contract | Short Timelock | Short Timelock |
| Treasury Funds Admin | Can spend treasury funds | Short Timelock | Short Timelock |

## 

| Parameter | Description | Rewards Treasury Initial Parameters | Community Treasury Initial Parameters | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Recipient | Address that receives vested funds | Rewards Treasury | Community Treasury |  |  |  |  |
| Vesting Amount + Frontloaded Amount | Amount of tokens that will be immediately sent + vested to recipient | 450,000,000 | 50,000,000 |  |  |  |  |
| Vesting Amount | Amount of tokens that will be vested to recipient | 374,616,438 | 50,000,000 |  |  |  |  |
| Frontloaded Amount | Amount of tokens to be immediately sent to recipient | 75,383,562 | 0 |  |  |  |  |
| Vesting Begin | Time when vesting begins | July 14th 15:00 UTC | July 14th 15:00 UTC |  |  |  |  |
| Vesting Cliff | Time when vesting cliff begins \(and tokens can actually be sent to recipient\) | July 14th 15:00 UTC | July 14th 15:00 UTC |  |  |  |  |
| Vesting End | Time when vesting ends | July 14th 15:00 UTC + 5 years | July 14th 15:00 UTC + 5 years |  |  |  |  |
| Treasury Proxy Admin | Can upgrade treasury contract | Short Timelock | Short Timelock | Y |  |  |  |
| Treasury Funds Admin | Can spend treasury funds | Short Timelock | Short Timelock | Y |  |  |  |

## Liquidity Staking

|  |  |  |
| :--- | :--- | :--- |
| Epoch Zero Start | Time when epoch zero begins | July 14th 15:00 UTC |
| Epoch Length | Length of each epoch | 28 days |
| Waiting period | Delay between proposing root and activating root | 7 days |
| User trading rewards per epoch | Amount of tokens to distribute per epoch for traders | 3,835,616 |
| Liquidity Provider trading rewards per epoch | Amount of tokens to distribute per epoch for MMs | 1,150,685 |
| Retroactive rewards for epoch 0 | Amount of tokens to distribute for retroactive rewards | 75,000,000 |
| Owner role | Can change epoch parameters and rewards oracle | Short Timelock |
| Pauser role | Can pause pending root \(before it's promoted to active\) | Merkle Timelock |
| Unpauser role | Can unpause a paused pending root | Short Timelock |
| Claim operator role | Can claim on others behalf | Claims proxy |
| Proxy Admin | Can upgrade the contract | Short Timelock |

## Safety Module

| Parameter | Description | Initial Parameter |
| :--- | :--- | :--- |
| Epoch Zero Start | Time when epoch zero begins | July 14th 15:00 UTC |
| Rewards End | Times when rewards stop being distributed to stakers | July 14th 15:00 UTC + 5 years |
| Epoch Length | Length of each epoch | 28 days |
| Blackout Window Length | Time during which users cannot unstake before end of epoch | 7 days |
| Minimum Epoch Length | Smallest allowed epoch length | 6 days |
| Maximum Epoch Length | Largest allowed epoch length | 92 days |
| Minimum Blackout Window Length | Smallest allowed blackout window length | 3 days |
| Maximum Blackout Window Length | Largest allowed blackout window length | 46 days |
| Rewards per second | Tokens to emit as rewards each second when within distribution window | 0.1585342262 = \(383,526 / \(28 \* 24 \* 60 \* 60\)\) |
| Borrower Allocations | Percent funds to allocate to each borrower | TBD |
| Owner role | Admin of all below roles | Short Timelock |
| Epoch parameters role | Can set epoch parameters | Short Timelock |
| Rewards rate role | Can change rewards rate | Short Timelock |
| Borrower admin role | Can change borrower allocations / restrictions | Short Timelock |
| Claim operator role | Can claim on the behalf of others | Claims Proxy |
| Stake operator role | Can stake on the behalf of others | Unassigned |
| Debt operator role | Can manage debt | Unassigned |
| Proxy Admin | Can upgrade the contract | Short Timelock |

## Stark Proxy

| Parameter | Description | Liquidity Staking |  |
| :--- | :--- | :--- | :--- |
| Owner role | Owns owner, funds admin, and delegation admin roles + can add/remove recipients who receive funds + STARK keys | Market Maker |  |
| Funds admin role | May withdraw any funds in excess of borrowed balance to allowed recipient, and may call forced actions | Market Maker |  |
| Delegation admin role | Owns borrower and exchange role | Market Maker |  |
| Borrower role | May call borrow functions on LS1 | Market Maker |  |
| Exchange role | May call exchange functions | Market Maker |  |
| Guardian role | May perform close actions, and force actions if borrower has overdue debt | Short Timelock |  |

## Stark Perpetual

| Parameter | Description | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Add new asset |  | N | N | N | Y |
| Change configuration of existing asset |  | N | N | N | Y |
| Proxy admin |  | N | N | N | Y |
| Add operator |  | N | N | N | Y |
| Remove operator |  | N | N | N | Y |
| Add verifier |  | N | N | N | Y |
| Remove verifier |  | N | N | N | Y |

