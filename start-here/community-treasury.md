---
description: An overview of the community treasury.
---

# Treasury

`5.00%` of the initial token supply (`50,000,000 DYDX`) will be distributed to a community treasury to be allocated on an ongoing basis through contributor grants, community initiatives, liquidity mining, and other programs.

**Objectives**

* Fund programs and initiatives that drive the growth of dYdX.
* Develop grant programs to fund community NFTs, hackathons, analytics dashboards, memes, swag, third-party tools, translations, and other projects.
* Develop a best-in-class governance system and incentivize robust governance.

## Overview

The community treasury will retain DYDX to use as DYDX holders decide, whether it be for grants, new liquidity mining pools, or any other program. DYDX will vest to the community treasury on a continuous basis over the course of five years. A governance vote will be required to spend any DYDX from the community treasury.

If, after five years, governance decides to enact perpetual inflation (at a maximum annual inflation of `2%`), any newly minted DYDX will be available to the community treasury.

## FAQ

### How does DYDX vest in the Community Treasury?

Every second, the Community Treasury Vester (see details [here](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)) vests [`0.3169242627`](tel:03169242627) DYDX to the Community Treasury. Once DYDX has been vested, calling the `claim` function on the Community Treasury Vester will transfer the vested DYDX to the Community Treasury. Any dYdX community member can call the `claim` function on Etherscan [here](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) (which would require some ETH for gas fees) to move the vested DYDX from the Community Treasury Vester to the Community Treasury.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### What is the vested balance of the Community Treasury?

dYdX community members can view the vested balance of the community treasury [here](https://dydx.shippooor.xyz/). \
\
Further, dYdX Foundation publishes the vested balance of the Community Treasury in the [Epoch Review](https://dydx.foundation/blog) at the end of each epoch. In addition to the vested DYDX in the Community Treasury, the dYdX community can also access the DYDX accruing in the Rewards Treasury as a result of the votes to (1) reduce trading rewards by 25% (958,904 DYDX), (2) set the rewards for staking USDC to 0 (383,562 DYDX), and (3) set the rewards for staking DYDX to 0 (383,562 DYDX). Starting in Epoch 17, 1,726,028 DYDX  will accrue in the Rewards Treasury each epoch and can be used by the dYdX community with a [governance vote](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

### Who can submit proposals to spend DYDX tokens from the Community Treasury?

Any user with sufficient proposing power can submit proposals. A governance vote will be required to spend any DYDX from the community treasury. To submit a proposal, please submit a dYdX Improvement Proposal (DIP) as laid out in the [DIP Proposal Lifecycle](../voting-and-governance/dip-proposal-lifecycle.md).

### What types of proposals can be submitted to the Community Treasury?

A community-managed treasury opens up a world of possibilities. We hope to see various experiments and initiatives, including ecosystem grants, which can foster the dYdX Layer 2 Protocol’s ecosystem growth.
