---
description: Un aperçu du pool de staking de sécurité
---

#

Au départ, `2,50 %` de l'approvisionnement en tokens (soit `25 000 000 $ethDYDX`) ont été distribués aux utilisateurs qui stakent les $USDC sur le module de sécurité. Le module de sécurité n'est plus actif depuis le 28 novembre 2022.

Au départ, DYDX était distribué aux utilisateurs qui misaient des ethDYDX dans le module de sécurité. Le module de sécurité était un fonds décentralisé qui devait être utilisé en cas d'insolvabilité ou en cas de problème avec le protocole dYdX.



## Aperçu

Actuellement, $ethDYDX staké dans le module de sécurité est exempt de récompenses.



## Désengagement et retraits des DYDX

Les stakers doivent présenter une demande de retrait de fonds au moins `dans les 3 jours` **(fenêtre de blocage)** qui précèdent la fin de l'Epoch afin de pouvoir retirer des $ethDYDX après la fin de cette dernière. Si les stakers ne demandent pas de retrait, leur $ethDYDX staké est reporté à l'époch suivante.

Les retraits ne peuvent être demandés pendant la **fenêtre de blocage**.

Dans [DIP 17](https://dydx.community/dashboard/proposal/9), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/7) pour réduire la durée de la fenêtre de blocage de `14` à `3 jours`.

## FAQ

<details>

<summary>Qu'est-ce qu'une fenêtre de blocage ?</summary>

Une fenêtre de blocage correspond au laps de temps pendant lequel les utilisateurs ne peuvent pas solliciter de retraits de $stkDYDX. La fonction `requestWithdrawal` ne peut pas être appelée pendant une fenêtre de blocage, qui est configurée comme les `3 derniers jours` d'une epoch. Les nouvelles epochs commencent tous les 28 jours. En d'autres termes, les utilisateurs peuvent demander un retrait pour l'epoch suivante jusqu'à `3 jours` avant la fin d'une epoch donnée.

</details>

<details>

<summary>Comment puis-je retirer des fonds du pool de staking ? Combien de temps cela prend-il ?</summary>

Un calendrier d'epoch est appliqué pour les retraits afin de fournir une prévisibilité et une cadence régulière pour la disponibilité des fonds dans le pool. Un staker doivent effectuer une demande de retrait de fonds au moins `3 jours` avant la fin d'une époch afin de pouvoir retirer ses fonds après la fin de cette dernière. Si les stakers ne demandent pas de retrait, leur $ethDYDX staké est reporté à l'époch suivante.

Pour retirer des fonds, les utilisateurs utilisent la fonction `` \`requestWithdrawal\` `` pour demander de retirer des fonds pour la prochaine epoch. Les fonds des utilisateurs resteront stakés et non retirables pour l'epoch actuelle. À partir de la prochaine epoch, les fonds seront « inactifs » et disponibles pour retrait.

À l'epoch suivante, les utilisateurs utilisent la fonction`` \`withdrawStake\` `` pour retirer des fonds inactifs à une adresse spécifique. Les utilisateurs peuvent sélectionner le montant des fonds inactifs qu'ils souhaitent retirer ou utiliser la fonction `` \`withdrawMaxStake\` `` pour retirer tous les fonds inactifs. Notez que la fonction `` `withdrawMaxStake` `` est moins économe en termes de consommation de gaz que d'interroger le max via eth\_call et d'appeler `` `withdrawStake()` ``.

Pour retirer des $ethDYDX du module de sécurité, procédez comme suit :

* Allez sur [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Cliquez sur « **Demander** » et entrez le montant de $ethDYDX que vous souhaitez retirer du pool.
* Cliquez sur « **Demander un retrait** ». Vous devrez payer des frais de gaz pour retirer des fonds.
* Les stakers qui demandent à retirer des $ethDYDX au moins `3 jours` avant la fin de l'époch en cours peuvent retirer leurs $ethDYDX au début de l'époch suivante.

</details>

