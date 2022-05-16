---
description: Overview of governance architecture and smart contracts.
---

# Technical Overview

## Governance Architecture Overview

dYdX on-chain governance supports the following features:

* Creating and voting on proposals
* Snapshotting token holdings at the start of a proposal
* Delegating separate voting and proposing powers
* Setting governance thresholds including proposing, quorum, and vote differential thresholds
* Replacing the “Governance Strategy” smart contract, which determines how votes are counted
* Configuring multiple executor contracts allowing for:
  * rapid protocol upgrades and funds distribution via short time-lock executors;
  * governance upgrades via long time-lock executors.

There are 6 smart contracts that support dYdX Governance:

* **The `DydxToken` contract**: Keeps snapshots which support queries for an address’ voting or proposing power at any block number. Supports separate delegation of voting and proposing powers.
* **The `DydxGovernor` contract**: Tracks proposals and can execute proposals via the Executor smart contracts.
* **The `Executor` contracts**: Can queue, cancel, and execute transactions voted on by Governance. If a proposal passes, the functions calls in the proposal may be executed by the Executor contract specified in the proposal. Queued transactions can be executed after a delay, whose duration is determined by the Executor contract.
* **The** **`Priority Timelock`** **contract**: The same as the timelock contract, but allows a priority controller to execute transactions within the **Priority Period** (7 days) before the end of the timelock delay.
* **The `Governance Strategy` contract**: Contains the logic for counting votes. Currently, counts votes from the DYDX Token and the Safety Module. Can be upgraded via the long time-lock.
* **The `Safety Module` contract**: Contains logics to stake DYDX tokens, tokenize a staked position, and earn rewards, while retaining the voting and proposing rights and delegation functions of the underlying tokens.

{% tabs %}
{% tab title="Mainnet" %}
| Contract                             | Address                                    |
| ------------------------------------ | ------------------------------------------ |
| DydxToken                            | 0x92D6C1e31e14520e676a687F0a93788B716BEff5 |
| DydxGovernor                         | 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2 |
| Short Timelock Executor              | 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc |
| Long Timelock Executor               | 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B |
| Merkle-Pauser Timelock Executor      | 0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52 |
| Starkware Priority Timelock Executor | 0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE |
| Rewards Treasury                     | 0x639192D54431F8c816368D3FB4107Bc168d0E871 |
| Community Treasury                   | 0xE710CEd57456D3A16152c32835B5FB4E72D9eA5b |
| Safety Module                        | 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC |
| GovernanceStrategy                   | 0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9 |
| Rewards Treasury Vester              | 0xb9431E19B29B952d9358025f680077C3Fd37292f |
| Community Treasury Vester            | 0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8 |
| Merkle Distributor                   | 0x01d3348601968aB85b4bb028979006eac235a588 |
| Chainlink Adapter                    | 0x99B0599952a4FD2d1A1561Fa4C010827EaD30354 |
| Liquidity Staking                    | 0x5Aa653A076c1dbB47cec8C1B4d152444CAD91941 |
| Claims Proxy                         | 0x0fd829C3365A225FB9226e75c97c3A114bD3199e |
| StarkEx Helper Governor              | 0x0db9b3F7Dd83e29C9bece8E5e1089bA4369E694a |
| StarkEx Remover Governor V2          | 0xFCAac0F14deA11eDe11Afcb875f29130e1ad5ec0 |
| Rewards Treasury Proxy Admin         | 0x40D6992cbd03E0DC1c2DE9606D29Cb245E737a5d |
| Community Treasury Proxy Admin       | 0x9d51599A6b10f562619D8ef2EFDcA1B68aE80D03 |
| Safety Module Proxy Admin            | 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C |
| Merkle Distributor Proxy Admin       | 0x6C5cd3aD7A16Ae207D221908E6b997d9B0DcD7b0 |
| Liquidity Staking Proxy Admin        | 0xAc5D8bCD13da463bea96c75f9085c4e40037F790 |
| StarkProxy \[0]                      | 0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6 |
| StarkProxy \[1]                      | 0x3e6E9EFb0A677a24F47093a22044dc5451A028cF |
| StarkProxy \[2]                      | 0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2 |
| StarkProxy \[3]                      | 0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06 |
| StarkProxy \[4]                      | 0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874 |
| StarkProxy Proxy Admin \[0]          | 0xE16718eace44e0CB06b9cd164490A69A6425D1e3 |
| StarkProxy Proxy Admin \[1]          | 0x78e899e576C3565C3219dbC9Ea5042A9DBed36d3 |
| StarkProxy Proxy Admin \[2]          | 0x15774D4555fEfD57C9Fc8b11C8beba993eafcc13 |
| StarkProxy Proxy Admin \[3]          | 0x4d9460e5C958f46a1Fe129954A069a37972f16EA |
| StarkProxy Proxy Admin \[4]          | 0xfa45DCDbEc82C94082d283B62506320DB8632054 |
{% endtab %}
{% endtabs %}

## Open-source code & audited

All smart contract source code for the governance contracts and staking pools can be found at [https://github.com/dydxfoundation/governance-contracts](https://github.com/dydxfoundation/governance-contracts).

The source code for the governance frontend hosted at dydx.community can be found [here](https://github.com/dydxfoundation/pnyx).

All major new smart contracts have been audited by Peckshield. No significant or high priority security issues were found. The core governance and token contracts are forked from the Aave governance contracts which were audited by [CertiK](https://www.certik.io/), [Certora](https://www.certora.com/), and [Peckshield](https://peckshield.com/en) and have been battle-tested live on mainnet for months.

## Core Governance Contracts

![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.17.43 PM.png>)

### DydxToken

The DydxToken contract was inspired by Aave. Minor changes have been made by the dYdX team.

DYDX is deployed at [0x92D6C1e31e14520e676a687F0a93788B716BEff5](https://etherscan.io/address/0x92d6c1e31e14520e676a687f0a93788b716beff5) on the Ethereum mainnet. It was built from commit \[coming soon].

**ABI**

\[coming soon]

### DydxGovernor

The DydxGovernor contract was inspired by Aave. Minor changes have been made by dYdX.&#x20;

Governor is deployed at [0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2) on the Ethereum mainnet. It was built from commit \[coming soon].

### GovernanceStrategy

The GovernanceStrategy contract was inspired by Aave.

Strategy is deployed at [0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9](https://etherscan.io/address/0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9) on the Ethereum mainnet. It was built from commit \[coming soon].

**ABI**

\[coming soon]

### Executors

The Executor contract was inspired by Aave. Minor changes have been made by dYdX.&#x20;

The **Long Timelock** is deployed at [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) on the Ethereum mainnet. It was built from commit \[coming soon].

**ABI**

\[coming soon]

The **Short Timelock** is deployed at [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) on the Ethereum mainnet. It was built from commit \[coming soon].

**ABI**

\[coming soon]

The **Merkle Timelock** is deployed at [0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52](https://etherscan.io/address/0xd98e7a71bacb6f11438a8271ddb2efd7f9361f52) on the Ethereum mainnet. It was built from commit \[coming soon].

**ABI**

\[coming soon]

The **Starkware Priority Timelock** is deployed  at [0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE](https://etherscan.io/address/0xa306989ba6bcacdeccf3c0614fff2b8c668e3cae) on the Ethereum mainnet. It was built from commit \[coming soon].

**ABI**

\[coming soon]

## DYDX Incentives Contracts

### Merkle Distributor



![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.23.50 PM.png>)

The Merkle Distributor smart contract distributes DYDX token rewards according to a Merkle tree of balances. The tree can be updated periodically with each user's cumulative reward balance, allowing new rewards to be distributed to users over time.

An update is performed by setting the proposed Merkle root to the latest value returned by the oracle contract. The proposed Merkle root can be made active after a waiting period has elapsed. During the waiting period, dYdX Governance has the opportunity to freeze the Merkle root, in case the proposed root is incorrect or malicious. Root updates can be unpaused by ShortTimelockExecutor.

The Merkle Distributor smart contract was inspired by Uniswap and Badger designs. The smart contract is deployed at 0x01d3348601968aB85b4bb028979006eac235a588 on the Ethereum mainnet. It was built from commit \[coming soon].

**ABI**

\[coming soon]

### Safety Module



![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.24.45 PM.png>)

The Safety Module is a staking pool that offers DYDX rewards to users who stake DYDX towards the security of the Protocol.

**ABI**

\[coming soon]



### Liquidity Module



![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.25.30 PM.png>)

The Liquidity Module is a collection of smart contracts for staking and borrowing, which incentivize the allocation of USDC funds for market making purposes on the dYdX layer 2 exchange.

Stakers earn DYDX rewards for staking USDC. The staked funds may be borrowed by certain pre-approved partners, on a reputational basis, without collateral. The funds may only be used on the L2 exchange—this is enforced via the StarkProxy contract which interacts with the StarkEx Perpetual Exchange contract.

![A diagram of the Liquidity module](<../.gitbook/assets/image (66).png>)

### StarkProxy

This contract allows the owner to borrow funds from LiquidityStaking and use those funds on StarkPerpetual. Additional funds may be deposited by the owner, and any funds in excess of the borrowed amount may be withdrawn freely. This contract interacts with the [StarkPerpetual](https://github.com/starkware-libs/starkex-contracts/tree/master/scalable-dex/contracts/src/perpetual) contract which was written by Starkware, and previously audited and deployed.



### Treasury Contracts



![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.26.09 PM.png>)

The TreasuryVester contract was inspired by [Uniswap](https://github.com/Uniswap/governance/blob/master/contracts/TreasuryVester.sol).

The Short Timelock can only execute governance-approved actions.

There are two treasury vesters and treasury contracts, one is for incentive contract rewards and the other is for holding “general purpose” treasury funds.

Since governance controls each treasury, it can transfer funds to any address and/or approve any address to spend funds from either treasury. For example, the rewards programs will need to have token approval limits set by governance.

Each treasury vester will vest tokens linearly over \~5 years (August 3rd 2021 - August 3rd 2026) to the corresponding treasury.



## Peripheral Contracts

### Chainlink Oracle-Powered Rewards (Trading & Liquidity Provider Rewards)

The goal of this system is to calculate and publish, via a decentralized network of oracle signers, the DYDX token rewards earned by traders using the dYdX layer 2 exchange. Rewards are stored in a Merkle tree, which contains the cumulative rewards earned by each user since the start of the distribution program. Each epoch, the Merkle root is updated on the MerkleDistributorV1 smart contract to reflect rewards earned in the last epoch.

We have integrated with the Chainlink Oracle system to post rewards data on-chain. We use IPNS to post the trading data that Chainlink uses to build the Merkle tree. By using IPNS, we can post the trading data for the latest epoch under the same IPNS link as previous epochs, meaning the location of the data won't change.

After calculating the appropriate rewards from the raw trading data, Chainlink posts the Merkle tree of rewards to IPFS. The IPFS CID with the Merkle tree data is stored on the Merkle distributor contract along with the Merkle root for that epoch's rewards.

The following flow chart shows the Chainlink Oracle-Powered Rewards system architecture:

![](<../.gitbook/assets/Merkle Distributor.png>)

### Other Assets

* dYdX Foundation brand assets are available [**here**](https://dydx.foundation/brand)****
