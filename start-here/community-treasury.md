---
description: An overview of the community treasury.
---

# Community Treasury

**`26.1%`** (`261,133,225 $ethDYDX`) of the token supply is allocated to the community treasury for the dYdX community to use on an ongoing basis for contributor grants, community initiatives, liquidity mining, and other programs. Initially,`5.0%` of the token supply (`50,000,000 $ethDYDX`) was [allocated](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations) to the community treasury, and 766,703 $ethDYDX vests in the community treasury each epoch. Currently, 3,787,251 $ethDYDX vest in the community treasury because several governance proposals resulted in a 3,020,548 $ethDYDX increase in the amount of $ethDYDX available to the dYdX community each epoch:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - set the rewards for staking USDC to 0 (383,562 $ethDYDX per epoch),&#x20;
* [DIP 16](https://dydx.community/dashboard/proposal/8) - reduce trading rewards by 25% (958,904 $ethDYDX per epoch),&#x20;
* [DIP 17](https://dydx.community/dashboard/proposal/9) - set the rewards for staking $DYDX to 0 (383,562 $ethDYDX per epoch),
* [DIP 20](https://dydx.community/dashboard/proposal/11) - further reduce trading rewards by 45% (1,294,520 $ethDYDX per epoch), and
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - reduce Liquidity Provider Rewards by 50% (575,342 $ethDYDX per epoch).
*   [DIP 29](https://dydx.community/dashboard/proposal/16) - reduce Liquidity Provider Rewards by ⅓ from Epoch 30-32 on dYdX v3 to the following values:

    * Epoch 30: 383,562 $ethDYDX
    * Epoch 31: 191,781 $ethDYDX
    * Epoch 32: 0 $ethDYDX

    After Epoch 31, there will not be any Liquidity Provider Rewards on dYdX v3. In DIP 29, the dYdX community voted to reduce Trading Rewards by ⅓ from Epoch 30-32 on dYdX v3, however the remaining allocation of Trading Rewards was migrated to the dYdX Chain for Trading Rewards.&#x20;

On November 18, 2023, the dYdX community [voted](https://dydx.community/dashboard/proposal/16) to bridge the ethDYDX balance accrued in the Community Treasury from Ethereum to dYdX Chain. Once bridged, the DYDX can be used by the dYdX community with a governance vote on dYdX Chain.&#x20;



**Objectives**

* Fund programs and initiatives that drive the growth of dYdX.
* Develop grant programs to fund community NFTs, hackathons, analytics dashboards, memes, swag, third-party tools, translations, and other projects.
* Develop a best-in-class governance system and incentivize robust governance.

## Overview

The community treasury will retain $ethDYDX to use as $ethDYDX holders decide, whether it be for grants, new liquidity mining pools, or any other program. $ethDYDX will vest to the community treasury on a continuous basis over the course of five years. A governance vote will be required to spend any ethDYDX from the community treasury.

If, after five years, governance decides to enact perpetual inflation (at a maximum annual inflation of `2%`), any newly minted $ethDYDX will be available to the community treasury.

## FAQ

### How does $ethDYDX vest in the Community Treasury?

Every second, the Community Treasury Vester (see details [here](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)) vests [`0.3169242627`](tel:03169242627) $ethDYDX to the Community Treasury. Once $ethDYDX has been vested, calling the `claim` function on the Community Treasury Vester will transfer the vested $ethDYDX to the Community Treasury. Any dYdX community member can call the `claim` function on Etherscan [here](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) (which would require some ETH for gas fees) to move the vested $ethDYDX from the Community Treasury Vester to the Community Treasury.

Please refer to the dYdX Foundation’s [Terms of Use](https://dydx.foundation/terms) for further details on the control of the community treasury by the dYdX community.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### What is the vested balance of the Community Treasury?

dYdX community members can view the vested balance of the community treasury [here](https://dydx.shippooor.xyz/). \
\
Further, dYdX Foundation publishes for information only the vested balance of the Community Treasury in the [Epoch Review](https://dydx.foundation/blog) at the end of each epoch. In addition to the vested $ethDYDX in the Community Treasury, the dYdX community can also access the ethDYDX accruing in the Rewards Treasury as a result of the votes to:&#x20;

* [DIP 14](https://dydx.community/dashboard/proposal/7) - set the rewards for staking USDC to 0 (383,562 $ethDYDX per epoch),&#x20;
* [DIP 16](https://dydx.community/dashboard/proposal/8) - reduce trading rewards by 25% (958,904 $ethDYDX per epoch),&#x20;
* [DIP 17](https://dydx.community/dashboard/proposal/9) - set the rewards for staking ethDYDX to 0 (383,562 $ethDYDX per epoch),
* [DIP 20](https://dydx.community/dashboard/proposal/11) - further reduce trading rewards by 45% (1,294,520 $ethDYDX per epoch),&#x20;
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - reduce Liquidity Provider Rewards by 50% (575,342 $ethDYDX per epoch), and&#x20;
* &#x20;[DIP 29](https://dydx.community/dashboard/proposal/16) - reduce Liquidity Provider Rewards by ⅓ from Epoch 30-32 on dYdX v3 to the following values:
  * Epoch 30: 383,562 $ethDYDX
  * Epoch 31: 191,781 $ethDYDX
  * Epoch 32: 0 $ethDYDX&#x20;

### Who can submit proposals to spend ethDYDX from the Community Treasury?

Any user with sufficient proposing power can submit proposals. A governance vote will be required to spend any ethDYDX from the community treasury. To submit a proposal, please submit a dYdX Improvement Proposal (DIP) as laid out in the [DIP Proposal Lifecycle](../voting-and-governance/dip-proposal-lifecycle.md).

### How do you go about building a proposal to spend funds from the Community Treasury?

Reverie has put together a comprehensive, technical, step-by-step guide on how any dYdX community member with more than 5M $ethDYDX ([proposal threshold](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) for a [short timelock vote](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)) of proposal power can create a proposal to transfer ethDYDX from the Community Treasury to a destination address. Click [here](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal) to access the technical guide.

### What types of proposals can be submitted to the Community Treasury?

A community-managed treasury opens up a world of possibilities. We hope to see various experiments and initiatives, including ecosystem grants, which can foster dYdX v3's ecosystem growth.
