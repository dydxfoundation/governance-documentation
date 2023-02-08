---
description: Un aperçu du pool de staking de liquidité
---

# Module de liquidité

`0,6 %` de la réserve de jetons (`5 753 430 $DYDX)` ont été distribués aux utilisateurs qui mettent en réserve de l'USDC dans le pool de mise en réserve de liquidité. Initialement, `2,50 %` de la réserve de jetons (`25 000 000 DYDX`) ont été alloués pour être distribués aux utilisateurs qui cumulent des $USDC dans le pool de mise en réserve de liquidité. Le pool de staking de liquidité n'est plus actif à compter du 29 septembre 2022. Dans la [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/7) en faveur d'une réduction efficace du pool de mise en réserve de liquidité et du pool d'emprunt en fixant à 0 les récompenses du pool de mise en réserve de liquidité par seconde.\

\Auparavant, la distribution de $DYDX été réservée aux utilisateurs ayant cumulé des $USDC dans le pool de mise en réserve de liquidité. Les fournisseurs de liquidité approuvés par la communauté utilisaient les $USDC cumulés pour créer des marchés sur la couche dYdX du protocole 2, optimisant ainsi la liquidité disponible sur les marchés. Les fournisseurs de liquidité ont fait l'objet d'une restriction concernant l'utilisation de fonds empruntés à l'extérieur de la couche dYdX du protocole 2.

## Aperçu du **staking**

Aujourd'hui, l'$USDC cumulé dans le pool de mise en réserve de liquidité ne gagne aucune récompense.

Les 383 562 $DYDX précédemment distribués aux stakers de $USDC s'accumuleront dans la trésorerie des récompenses et pourront être utilisés par la communauté de dYdX sous réserve d'un [vote de gouvernance](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## Désengagement et retraits des USDC

Un staker doit présenter sa demande de retrait en $USDC au moins `3 jours` (**fenêtre de blocage**) avant la fin d'une [**Epoch**](../start-here/epochs.md), afin de pouvoir retirer ses $USDC après la fin de l'Epoch en question. Les stakers qui ne présentent pas leur demande de retrait verront les $USDC être reportés à l'Epoch suivante.

Les retraits ne peuvent être demandés pendant la **fenêtre de blocage**.

Dans [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/7) pour réduire la durée de la fenêtre de blocage en passant de `14` à `3 jours`.

## Qu'est-ce que $stkUSDC ?

Les détenteurs d'$USDC qui déposent et cumulent leurs $USDC dans le pool de mise en réserve de liquidité recevront une position tokenisée ($**stkUSDC**). $stkUSDC est créé lorsqu'un utilisateur met en réserve des $USDC et est brûlé lorsqu'un utilisateur appelle `withdrawStake`. Dans la même transaction, alors que $USDC quitte le portefeuille d'un staker, $stkUSDC entre dans le portefeuille du staker ; ou vice-versa lors d'un désengagement.

Un solde en $stkUSDC peut être actif ou inactif. Un $stkUSDC actif peut être transféré en tant qu'ERC-20, mais ne peut pas être retiré. Un $stkUSDC inactif peut être retiré, mais ne peut pas être transféré. Par exemple, disons qu'un utilisateur dispose de 100 #stkUSDC actifs et de 100 #stkUSDC inactifs dans son portefeuille. Le solde de l'utilisateur affichera 200 $stkUSDC. Cependant, si l'utilisateur tente de transférer plus de 100 $stkUSD, le transfert sera annulé.

Un solde staké pour lequel le staker a demandé un retrait avant la fin de l'epoch serait considéré comme inactif, et donc non transférable.

## FAQ

### Qu'est-ce qu'une fenêtre de blocage ?

Une fenêtre de blocage correspond au laps de temps pendant lequel les utilisateurs ne peuvent pas solliciter de retraits de $USDC. La fonction `requestWithdrawal` ne peut pas être appelée pendant une fenêtre de blocage, qui est configurée comme les `3 derniers jours` d'une epoch. Les nouvelles epochs commencent tous les 28 jours. En d'autres termes, les utilisateurs peuvent demander un retrait pour l'epoch suivante jusqu'à `3 jours` avant la fin d'une epoch donnée.

### Comment puis-je retirer des $USDC du pool de mise en réserve ? Combien de temps cela prend-il ?

Un staker doit présenter sa demande de retrait de $USDC au moins `3 jours` avant la fin d'une Epoch afin de pouvoir retirer ses $USDC après la fin de l'Epoch en question. Les stakers qui ne présentent pas leur demande de retrait verront les $USDC être reportés à l'Epoch suivante.

Pour retirer de l'$USDC, les utilisateurs doivent appeler la fonction`requestWithdrawal`pour soumettre une demande de retrait de $USDC pour la prochaine Epoch. Les fonds des utilisateurs resteront stakés et non retirables pour l'époch actuelle. À partir de la prochaine époch, les fonds seront « inactifs » et disponibles pour retrait.

À l'Epoch suivante, les utilisateurs doivent appeler la fonction `withdrawStake` pour retirer des $USDC inactifs et les transférer vers une adresse spécifique. Les utilisateurs peuvent sélectionner le montant des fonds inactifs qu'ils souhaitent retirer ou appeler la fonction \`withdrawMaxStake\` pour retirer tous les fonds inactifs. La fonction `withdrawMaxStake` est moins économe en gaz que d'interroger le max via eth\_call et d'appeler `withdrawStake()`.

Pour débloquer des $USDC du pool de liquidité, suivez les étapes suivantes :

* Allez sur [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Cliquez sur « **Demande** », pour ouvrir le modèle suivant :

![Demande de retrait](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* Entrez le montant d'USDC que vous souhaitez demander de retirer du pool, puis cliquez sur "**Demander un retrait**". Vous devrez payer des frais de gaz pour annuler l'USDC.
* Les stakers qui demandent à retirer l'USDC au moins `3 jours` (**fenêtre de blocage**) avant la fin de l'epoch en cours peuvent retirer leur USDC au début de l'epoch suivante.

### Quels paramètres la gouvernance peut-elle changer ?

La gouvernance dYdX est responsable pour :

* Des récompenses par seconde pour le staking d'USDC dans le pool de staking de liquidité
* Ajouter de nouveaux emprunteurs et/ou supprimer des emprunteurs existants du pool de staking de liquidité
* Modification des allocations de l'USDC emprunté aux emprunteurs approuvés
  * Les fonctions `setBorrowerAllocations` et `setBorrowingRestriction` sont appelées à modifier les allocations de certains emprunteurs. Elles peuvent être utilisées pour ajouter et supprimer des emprunteurs. Les augmentations prennent effet à l'epoch suivante, mais les diminutions restreignent immédiatement les emprunts. Ces fonctions ne peuvent pas être appelées pendant la fenêtre de blocage.
* La durée de l'epoch et la fenêtre de blocage sont définies lors de la création du contrat, mais peuvent être modifiées
