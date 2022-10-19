---
description: Un aperçu du pool de staking de liquidité
---

# Module de liquidité

`2,50 %` de l'offre de jetons initiale (`25 000 000 DYDX`) ont été alloués pour être distribués aux utilisateurs stakant des USDC dans le pool de staking de liquidité. Le pool de staking de liquidité n'est plus actif à compter du 29 septembre 2022. Dans [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/7) pour réduire de manière efficace le pool de staking de liquidité et le pool d'emprunt en définissant les récompenses du pool de staking de liquidité par seconde à 0.\
\
Auparavant, DYDX a été distribué aux utilisateurs ayant staké des USDC dans le pool de staking de liquidité. Les fournisseurs de liquidité approuvés par la communauté ont utilisé les USDC stakés pour créer des marchés sur la couche dYdX du protocole 2, ce qui améliore la liquidité disponible sur les marchés. Les fournisseurs de liquidité ont fait l'objet d'une restriction concernant l'utilisation de fonds empruntés à l'extérieur de la couche dYdX du protocole 2.

## Aperçu du **staking**

Actuellement, l'USDC staké dans le pool de staking de liquidité ne gagne pas de récompenses.

Les 383 562 DYDX précédemment distribués aux stakers d'USDC s'accumuleront dans la trésorerie des récompenses et pourront être utilisés par la communauté dYdX grâce à un [vote de gouvernance](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## Désengagement et retraits des USDC

Un staker doit effectuer une demande de retirait d'USDC au moins `3 jours` (**fenêtre de blocage**) avant la fin d'une [**epoch**](../start-here/epochs.md) afin de pouvoir retirer ses USDC après la fin de cette epoch. Si les stakers ne demandent pas à retirer, leur USDC staké est reporté à l'epoch suivante.

Les retraits ne peuvent être demandés pendant la **fenêtre de blocage**.

Dans [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/7) pour réduire la durée de la fenêtre de blocage en passant de `14` à `3 jours`.

## Qu'est-ce que stkUSDC ?

Les détenteurs d'USDC qui déposent et stakent leur USDC dans le pool de staking de liquidité recevront une position tokenisée (**stkUSDC**). stkUSDC est créé lorsqu'un utilisateur stake des USDC et brûlé lorsqu'un utilisateur appelle `withdrawStake`. Dans la même transaction que l'USDC quitte le portefeuille d'un staker, stkUSDC entre dans le portefeuille du staker ; ou vice-versa lors du détachement.

Un solde stkUSDC peut être actif ou inactif. Le stkUSDC actif peut être transféré en tant qu'ERC-20, mais ne peut pas être retiré. Le stkUSDC inactif peut être retiré, mais ne peut pas être transféré. Par exemple, un utilisateur peut avoir 100 stkUSDC actifs et 100 inactifs dans son portefeuille, et le solde de l'utilisateur affichera 200 stkUSDC, mais un transfert sera annulé si l'utilisateur essaie de transférer plus de 100 stkUSDC.

Un solde staké pour lequel le staker a demandé un retrait avant la fin de l'epoch serait considéré comme inactif, et donc non transférable.

## FAQ

### Qu'est-ce qu'une fenêtre de blocage ?

Une fenêtre de blocage est une période de temps pendant laquelle les utilisateurs ne peuvent pas demander de retraits des USDC stakés. La fonction `requestWithdrawal` ne peut pas être appelée pendant une fenêtre de blocage, qui est configurée comme les `3 derniers jours` d'une epoch. Les nouvelles epochs commencent tous les 28 jours. En d'autres termes, les utilisateurs peuvent demander un retrait pour l'epoch suivante jusqu'à `3 jours` avant la fin d'une epoch donnée.

### Comment puis-je retirer des USDC du pool de staking ? Combien de temps cela prend-il ?

Un staker doit demander le retrait d'USDC au moins `3 jours` avant la fin d'une epoch afin retirer ses USDC après la fin de cette dernière. Si les stakers ne demandent pas à retirer, leur USDC staké est reporté à l'epoch suivante.

Pour retirer l'USDC, les utilisateurs appellent la fonction `requestWithdrawal` pour demander de retirer l'USDC pour la prochaine époch. Les fonds des utilisateurs resteront stakés et non retirables pour l'epoch actuelle. À partir de la prochaine epoch, les fonds seront « inactifs » et disponibles pour retrait.

À la prochaine époch, les utilisateurs appellent la fonction `withdrawStake` pour retirer l'USDC inactif à une adresse spécifique. Les utilisateurs peuvent sélectionner le montant des fonds inactifs qu'ils souhaitent retirer ou appeler la fonction \`withdrawMaxStake\` pour retirer tous les fonds inactifs. La fonction `withdrawMaxStake` est moins économe en gaz que d'interroger le max via eth\_call et d'appeler `withdrawStake()`.

Pour annuler l'USDC sur le pool de liquidité, suivez les étapes suivantes :

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
