---
description: Un aperçu du pool de staking de liquidité
---

# Module de liquidité 🔋

Le pool de staking de liquidité n'est plus actif à compter du 29 septembre 2022. Dans [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/7) en faveur de la fermeture effective du pool de staking de liquidité et de la Réserve d'emprunt en fixant à 0 le nombre de récompenses par seconde du pool de staking de liquidité.

All remaining ethDYDX from the Liquidity Module Rewards allocation were migrated to the dYdX Chain Community Treasury.

Pour plus d'informations sur la trésorerie de la communauté de la chaîne dYdX, cliquez [ici](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules-and-parameters/community-treasury).

## Aperçu du **staking**

Aujourd'hui, l'$USDC cumulé dans le pool de staking de liquidité ne gagne aucune récompense.

## Désengagement et retraits des USDC

Un staker doit présenter sa demande de retrait en $USDC au moins `3 jours` (**fenêtre de blocage**) avant la fin d'une [**Epoch**](../start-here/epochs.md), afin de pouvoir retirer ses $USDC après la fin de l'Epoch en question. Les stakers qui ne présentent pas leur demande de retrait verront les $USDC être reportés à l'Epoch suivante.

Les retraits ne peuvent être demandés pendant la **fenêtre de blocage**.

## FAQ

<details>

<summary>Qu'est-ce qu'une fenêtre de blocage ?</summary>

Une fenêtre de blocage correspond au laps de temps pendant lequel les utilisateurs ne peuvent pas solliciter de retraits de $USDC. La fonction `requestWithdrawal` ne peut pas être appelée pendant une fenêtre de blocage, qui est configurée comme les `3 derniers jours` d'une Epoch. Les nouvelles Epochs commencent tous les 28 jours. En d'autres termes, les utilisateurs peuvent demander un retrait pour l'Epoch suivante jusqu'à `3 jours` avant la fin d'une Epoch donnée.

</details>

<details>

<summary>Comment puis-je retirer des $USDC du pool de staking de liquidité ? Combien de temps cela prend-il ?</summary>

Un staker doit présenter sa demande de retrait de $USDC au moins `3 jours` avant la fin d'une Epoch afin de pouvoir retirer ses $USDC après la fin de l'Epoch en question. Les stakers qui ne présentent pas leur demande de retrait verront les $USDC être reportés à l'Epoch suivante.

Pour retirer de l'$USDC, les utilisateurs doivent appeler la fonction`requestWithdrawal`pour soumettre une demande de retrait de $USDC pour la prochaîne Epoch. Les fonds des utilisateurs resteront stakés et non retirables pour l'Epoch actuelle. À partir de la prochaîne Epoch, les fonds seront « inactifs » et disponibles pour retrait.

À l'Epoch suivante, les utilisateurs doivent appeler la fonction `withdrawStake` pour retirer des $USDC inactifs et les transférer vers une adresse spécifique. Les utilisateurs peuvent sélectionner le montant des fonds inactifs qu'ils souhaitent retirer ou appeler la fonction \`withdrawMaxStake\` pour retirer tous les fonds inactifs. La fonction `withdrawMaxStake` est moins économe en gaz que d'interroger le max via eth\_call et d'appeler `withdrawStake()`.

Pour débloquer des $USDC du pool de liquidité, suivez les étapes suivantes :

* Allez sur [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Cliquez sur “**Demande**”
* Entrez le montant de $USDC que vous souhaitez retirer du pool, puis cliquez sur « **Demander un retrait** ». Vous devrez payer des frais de gaz pour annuler le staking de $USDC.
* Les stakers qui demandent à annuler le staking de $USDC à moins de `3 jours` (**fenêtre de blocage**) avant la fin de l'Epoch en cours peuvent retirer leur $USDC au début de l'Epoch suivante.

</details>

###
