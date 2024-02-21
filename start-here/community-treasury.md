---
description: An overview of the community treasury.
---

# Community Treasury

**`26.1%`** (`261,133,225 $ethDYDX`) of the token supply is allocated to the community treasury for the dYdX community to use on an ongoing basis for contributor grants, community initiatives, liquidity mining, and other programs. Initially,`5.0%` of the token supply (`50,000,000 $ethDYDX`) was [allocated](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations) to the community treasury, and 766,703 $ethDYDX vested in the community treasury each epoch. Currently, 3,787,251 $ethDYDX vest in the community treasury because several governance proposals resulted in a 3,020,548 $ethDYDX increase in the amount of $ethDYDX available to the dYdX community each epoch:

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

Previously, the Community Treasury Vester (see details [here](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)) vested [`0.3169242627`](tel:03169242627) $ethDYDX to the Community Treasury every second. Once $ethDYDX has been vested, calling the `claim` function on the Community Treasury Vester would transfer the vested $ethDYDX to the Community Treasury. Any dYdX community member could call the `claim` function on Etherscan [here](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) (which would require some ETH for gas fees) to move the vested $ethDYDX from the Community Treasury Vester to the Community Treasury.

Please refer to the dYdX Foundation’s [Terms of Use](https://dydx.foundation/terms) for further details on the control of the community treasury by the dYdX community.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

###

###

