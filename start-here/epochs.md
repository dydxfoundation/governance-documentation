---
description: An overview of the epoch system
---

# Epochs

All rewards and staking contracts operate on `28 days` cycles, referred to as **epochs**. A new epoch automatically begins when the current epoch ends.

The following will occur at the end of each epoch:

* **Trading Rewards** are distributed. Rewards are claimable at [**dydx.community**](https://dydx.community) approximately `7 days` after the end of the epoch.
* **Liquidity Provider Rewards** are distributed. Rewards are claimable at [**dydx.community**](https://dydx.community) approximately `7 days` after the end of the epoch.
* Requested withdrawals for the **Liquidity Staking Pool** in the ended epoch may be withdrawn.
* Requested withdrawals for the **Safety Staking Pool** in the ended epoch may be withdrawn.

The following will occur only at the end of **Epoch 0**:

* Retroactive Mining Rewards will be distributed. Rewards are claimable at [**dydx.community**](https://dydx.community) approximately `8 days` after the end of Epoch 0.
* Transfers of $ethDYDX are initially restricted. The Initial Transfer Restriction period was lifted approximately `8 days` after the end of Epoch 0.
* **$ethDYDX became transferable on September 8th, 2021 at 15:00:00 UTC.**

**Epoch 0** went live on **August 3rd, 2021 at 15:00:00 UTC**. The following table outlines epoch start and end dates (which can be modified by dYdX v3 governance):

| Epoch | Start Date (UTC)    | End Date (UTC)      | Days | Cumulative Years |
| ----- | ------------------- | ------------------- | ---- | ---------------- |
| 0     | 8/3/2021 15:00:00   | 8/31/2021 15:00:00  | 28   | 0.08             |
| 1     | 8/31/2021 15:00:00  | 9/28/2021 15:00:00  | 28   | 0.15             |
| 2     | 9/28/2021 15:00:00  | 10/26/2021 15:00:00 | 28   | 0.23             |
| 3     | 10/26/2021 15:00:00 | 11/23/2021 15:00:00 | 28   | 0.31             |
| 4     | 11/23/2021 15:00:00 | 12/21/2021 15:00:00 | 28   | 0.38             |
| 5     | 12/21/2021 15:00:00 | 1/18/2022 15:00:00  | 28   | 0.46             |
| 6     | 1/18/2022 15:00:00  | 2/15/2022 15:00:00  | 28   | 0.54             |
| 7     | 2/15/2022 15:00:00  | 3/15/2022 15:00:00  | 28   | 0.61             |
| 8     | 3/15/2022 15:00:00  | 4/12/2022 15:00:00  | 28   | 0.69             |
| 9     | 4/12/2022 15:00:00  | 5/10/2022 15:00:00  | 28   | 0.77             |
| 10    | 5/10/2022 15:00:00  | 6/7/2022 15:00:00   | 28   | 0.84             |
| 11    | 6/7/2022 15:00:00   | 7/5/2022 15:00:00   | 28   | 0.92             |
| 12    | 7/5/2022 15:00:00   | 8/2/2022 15:00:00   | 28   | 1.00             |
| 13    | 8/2/2022 15:00:00   | 8/30/2022 15:00:00  | 28   | 1.07             |
| 14    | 8/30/2022 15:00:00  | 9/27/2022 15:00:00  | 28   | 1.15             |
| 15    | 9/27/2022 15:00:00  | 10/25/2022 15:00:00 | 28   | 1.23             |
| 16    | 10/25/2022 15:00:00 | 11/22/2022 15:00:00 | 28   | 1.30             |
| 17    | 11/22/2022 15:00:00 | 12/20/2022 15:00:00 | 28   | 1.38             |
| 18    | 12/20/2022 15:00:00 | 1/17/2023 15:00:00  | 28   | 1.46             |
| 19    | 1/17/2023 15:00:00  | 2/14/2023 15:00:00  | 28   | 1.53             |
| 20    | 2/14/2023 15:00:00  | 3/14/2023 15:00:00  | 28   | 1.61             |
| 21    | 3/14/2023 15:00:00  | 4/11/2023 15:00:00  | 28   | 1.69             |
| 22    | 4/11/2023 15:00:00  | 5/9/2023 15:00:00   | 28   | 1.76             |
| 23    | 5/9/2023 15:00:00   | 6/6/2023 15:00:00   | 28   | 1.84             |
| 24    | 6/6/2023 15:00:00   | 7/4/2023 15:00:00   | 28   | 1.92             |
| 25    | 7/4/2023 15:00:00   | 8/1/2023 15:00:00   | 28   | 1.99             |
| 26    | 8/1/2023 15:00:00   | 8/29/2023 15:00:00  | 28   | 2.07             |
| 27    | 8/29/2023 15:00:00  | 9/26/2023 15:00:00  | 28   | 2.15             |
| 28    | 9/26/2023 15:00:00  | 10/24/2023 15:00:00 | 28   | 2.22             |
| 29    | 10/24/2023 15:00:00 | 11/21/2023 15:00:00 | 28   | 2.30             |
| 30    | 11/21/2023 15:00:00 | 12/19/2023 15:00:00 | 28   | 2.38             |
| 31    | 12/19/2023 15:00:00 | 1/16/2024 15:00:00  | 28   | 2.45             |
| 32    | 1/16/2024 15:00:00  | 2/13/2024 15:00:00  | 28   | 2.53             |
| 33    | 2/13/2024 15:00:00  | 3/12/2024 15:00:00  | 28   | 2.61             |
| 34    | 3/12/2024 15:00:00  | 4/9/2024 15:00:00   | 28   | 2.68             |
| 35    | 4/9/2024 15:00:00   | 5/7/2024 15:00:00   | 28   | 2.76             |
| 36    | 5/7/2024 15:00:00   | 6/4/2024 15:00:00   | 28   | 2.84             |
| 37    | 6/4/2024 15:00:00   | 7/2/2024 15:00:00   | 28   | 2.92             |
| 38    | 7/2/2024 15:00:00   | 7/30/2024 15:00:00  | 28   | 2.99             |
| 39    | 7/30/2024 15:00:00  | 8/27/2024 15:00:00  | 28   | 3.07             |
| 40    | 8/27/2024 15:00:00  | 9/24/2024 15:00:00  | 28   | 3.15             |
| 41    | 9/24/2024 15:00:00  | 10/22/2024 15:00:00 | 28   | 3.22             |
| 42    | 10/22/2024 15:00:00 | 11/19/2024 15:00:00 | 28   | 3.30             |
| 43    | 11/19/2024 15:00:00 | 12/17/2024 15:00:00 | 28   | 3.38             |
| 44    | 12/17/2024 15:00:00 | 1/14/2025 15:00:00  | 28   | 3.45             |
| 45    | 1/14/2025 15:00:00  | 2/11/2025 15:00:00  | 28   | 3.53             |
| 46    | 2/11/2025 15:00:00  | 3/11/2025 15:00:00  | 28   | 3.61             |
| 47    | 3/11/2025 15:00:00  | 4/8/2025 15:00:00   | 28   | 3.68             |
| 48    | 4/8/2025 15:00:00   | 5/6/2025 15:00:00   | 28   | 3.76             |
| 49    | 5/6/2025 15:00:00   | 6/3/2025 15:00:00   | 28   | 3.84             |
| 50    | 6/3/2025 15:00:00   | 7/1/2025 15:00:00   | 28   | 3.91             |
| 51    | 7/1/2025 15:00:00   | 7/29/2025 15:00:00  | 28   | 3.99             |
| 52    | 7/29/2025 15:00:00  | 8/26/2025 15:00:00  | 28   | 4.07             |
| 53    | 8/26/2025 15:00:00  | 9/23/2025 15:00:00  | 28   | 4.14             |
| 54    | 9/23/2025 15:00:00  | 10/21/2025 15:00:00 | 28   | 4.22             |
| 55    | 10/21/2025 15:00:00 | 11/18/2025 15:00:00 | 28   | 4.30             |
| 56    | 11/18/2025 15:00:00 | 12/16/2025 15:00:00 | 28   | 4.37             |
| 57    | 12/16/2025 15:00:00 | 1/13/2026 15:00:00  | 28   | 4.45             |
| 58    | 1/13/2026 15:00:00  | 2/10/2026 15:00:00  | 28   | 4.53             |
| 59    | 2/10/2026 15:00:00  | 3/10/2026 15:00:00  | 28   | 4.60             |
| 60    | 3/10/2026 15:00:00  | 4/7/2026 15:00:00   | 28   | 4.68             |
| 61    | 4/7/2026 15:00:00   | 5/5/2026 15:00:00   | 28   | 4.76             |
| 62    | 5/5/2026 15:00:00   | 6/2/2026 15:00:00   | 28   | 4.83             |
| 63    | 6/2/2026 15:00:00   | 6/30/2026 15:00:00  | 28   | 4.91             |
| 64    | 6/30/2026 15:00:00  | 7/28/2026 15:00:00  | 28   | 4.99             |
| 65    | 7/28/2026 15:00:00  | 8/25/2026 15:00:00  | 28   | 5.06             |

The dYdX Foundation has created a public Google Calendar with start / end dates for Epochs and Blackout Windows - you can subscribe [**here**](https://calendar.google.com/calendar/u/3?cid=Y19wZjIwYzBoZzQ3dTR2cHRja283NDl1ajQyb0Bncm91cC5jYWxlbmRhci5nb29nbGUuY29t).

## **When will the rewards and staking pools be activated?**

* The [Retroactive Mining Rewards](../rewards/retroactive-mining-rewards.md) were distributed on dYdX v3. These rewards ran until **August 31th, 2021, 15:00:00 UTC**.
* The [Trading Rewards ](https://github.com/dydxfoundation/governance-docs/tree/58816ba822cb40fdbf1128dbbf5b0f6dbaa23cc1/reward-pools-1/trading-rewards.md)are now live on the Protocol. These rewards will run until **August 3rd, 2026, 15:00:00 UTC**.
* The [Liquidity Provider Rewards](../rewards/liquidity-provider-rewards.md) is now live on the Protocol. These rewards will run until **August 3rd, 2026, 15:00:00 UTC**.
* The [Liquidity Staking pool ](../staking-pools/liquidity-staking-pool.md)was wound down on September 29, 2022.&#x20;
* The [Safety Staking pool](../staking-pools/safety-staking-pool.md) was wound down on November 28, 2022.

## Can dYdX governance modify the epoch schedule?

The initial epoch length is `28 days`. dYdX v3 governance can vote to modify epoch lengths, within the specified bounds. The minimum and maximum epoch lengths are `6 days` and `92 days`, respectively.

## What is the Blackout Window?

For the [Liquidity Staking Pool](../staking-pools/liquidity-staking-pool.md) and the [Safety Staking Pool](../staking-pools/safety-staking-pool.md), an epoch schedule is enforced for withdrawals in order to provide predictability and a regular cadence for the availability of funds in the pool. A staker must request to unstake funds before the blackout window in order to be able to withdraw the staker's funds after the end of that epoch. If a staker does not request to withdraw, then the staker's staked funds are rolled over into the next epoch.

The recommended blackout window for each of the Liquidity Staking Pool and the Safety Pool is `14 days`. In [DIP 17](https://dydx.community/dashboard/proposal/9), the dYdX community [voted](https://dydx.community/dashboard/proposal/7) to reduce the length of the Blackout Window from `14 days` to `3 days.` dYdX governance can vote to modify the blackout window, within the specified bounds. The minimum and maximum blackout windows are `3 days` and `46 days`, respectively.

## When can I withdraw and transfer my earned $ethDYDX Rewards?

Earned $ethDYDX tokens via the [Retroactive Mining Rewards](../rewards/retroactive-mining-rewards.md), [Trading Rewards](../rewards/trading-rewards.md), and [Liquidity Provider Rewards](../rewards/liquidity-provider-rewards.md) are transferable at the end of each epoch. $ethDYDX holders are required to wait approximately `7 days` (**Waiting Period**) after the end of the epoch to claim their tokens. Once tokens have been claimed, they can be transferred or delegated to dYdX governance.

Earned $ethDYDX tokens via the Liquidity Staking pool and the Safety Staking pool are claimable every block and can be withdrawn at any time during a given epoch.

On **September 8th, 2021 at 15:00:00 UTC**, 8 days after the end of Epoch 0, the initial transfer restrictions was automatically lifted, at which point approximately **8.11%** of the $ethDYDX supply became liquid.

## What is the purpose of the Waiting Period? How are rewards stored at the end of every epoch?

[Retroactive Mining Rewards](../rewards/retroactive-mining-rewards.md), [Trading Rewards](../rewards/trading-rewards.md), and [Liquidity Provider Rewards](../rewards/liquidity-provider-rewards.md) are stored in a Merkle tree, which contains the cumulative rewards earned by each user since the start of the distribution program.

At the end of each epoch, the Merkle root is updated via the ChainLink oracle system on the `MerkleDistributorV1` smart contract to reflect rewards earned in the last epoch. An update is performed by setting the proposed Merkle root to the latest value returned by the oracle contract. The proposed Merkle root can be made active after a **Waiting Period** of `7 days` has elapsed. During the waiting period, dYdX governance has the opportunity to freeze the Merkle root, in case the proposed root is incorrect or malicious. If the Merkle root is not frozen, the new Merkle root is activated and users can claim their rewards from the past epoch.

Each time the epoch changes, the following occurs in order:

* When an epoch ends, rewards data is calculated for all user activity from the last epoch.
* This data is added to a data structure on IPFS, stored under a fixed IPNS name.
* The ChainLink oracle system, also noticing the change in epoch, queries the latest rewards data using the known IPNS name.
* Each oracle signer uses this rewards data to calculate newly earned rewards for each user.
* Each oracle signer computes the new cumulative Merkle tree and Merkle root.
* Each oracle signer writes the Merkle tree data to IPFS, receiving an IPFS CID. (They should have calculated the same tree and should therefore receive the same CID.)
* If the oracle signers agree on the same values, then the RewardsOracle is updated with the new Merkle root, IPFS CID, and epoch number.
* An oracle signer (or a third party) calls the public function `MerkleDistributorV1.proposeRoot()` to set the proposed Merkle root to the new oracle value.
* A waiting period takes place, during which governance can call `MerkleDistributorV1.pauseRootUpdates()` to prevent the proposed Merkle root from taking effect.
* After the waiting period, an oracle signer (or a third party) calls the public function `MerkleDistributorV1.updateRoot()` causing the proposed Merkle root to become active.
* Once the new Merkle root is active, users are able to claim rewards from the last epoch.
