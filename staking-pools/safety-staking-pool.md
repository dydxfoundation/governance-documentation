---
description: Un aperçu du pool de staking de sécurité
---

# Module de sécurité

`0,5 %` de la réserve de jetons (`5 049 079 $DYDX)` a été versé aux utilisateurs qui cumulent des $DYDX dans un pool de sécurité prévu pour soutenir le système. Initialement, `2,50 %` de la réserve de jetons (`25 000 000 dYdX`) ont été affectés en vue d'être répartis entre les utilisateurs qui cumulent des $DYDX dans le module de sécurité. Le module de sécurité n'est plus actif depuis le 28 novembre 2022. Dans [DIP 17](https://dydx.community/dashboard/proposal/9), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/7) pour réduire efficacement le module de sécurité en fixant les récompenses du module de sécurité par seconde à 0.\


Auparavant, $DYDX était distribué aux utilisateurs qui cumulaient des $DYDX dans le module de sécurité. Le module de sécurité était un fonds décentralisé qui devait être utilisé en cas d'insolvabilité ou en cas de problème avec le protocole dYdX.

Un $DYDX staké dans le module de sécurité conserve ses droits de proposition et de vote, tout comme ses capacités de délégation.

## Aperçu

Présentement, le $DYDX placé dans le module de sécurité ne rapporte aucune récompense.

Les 383 562 $DYDX précédemment distribués aux stakers de $DYDX seront versés dans la trésorerie des récompenses et pourront être utilisés par la communauté dYdX au moyen d'un [vote de gouvernance](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## Désengagement et retraits des DYDX

Les stakers doivent présenter une demande de retrait de fonds au moins dans les `3 jours` **(fenêtre de blocage)** qui précèdent la fin de l'Epoch afin de pouvoir retirer des $DYDX après la fin de cette dernière. Les stakers qui ne présentent pas leur demande de retrait verront les $USDC être reportés à l'Epoch suivante.

Les retraits ne peuvent être demandés pendant la **fenêtre de blocage**.

Dans [DIP 17](https://dydx.community/dashboard/proposal/9), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/7) pour réduire la durée de la fenêtre de blocage de `14` à `3 jours`.



## FAQ

### Qu'est-ce qu'une fenêtre de blocage ?

Une fenêtre de blocage correspond au laps de temps pendant lequel les utilisateurs ne peuvent pas solliciter de retraits de $stkDYDX. La fonction `requestWithdrawal` ne peut pas être appelée pendant une fenêtre de blocage, qui est configurée comme les `3 derniers jours` d'une epoch. Les nouvelles epochs commencent tous les 28 jours. En d'autres termes, les utilisateurs peuvent demander un retrait pour l'epoch suivante jusqu'à `3 jours` avant la fin d'une epoch donnée.

### Comment puis-je retirer des fonds du pool de staking ? Combien de temps cela prend-il ?

Un calendrier d'epoch est appliqué pour les retraits afin de fournir une prévisibilité et une cadence régulière pour la disponibilité des fonds dans le pool. Un staker doivent effectuer une demande de retrait de fonds au moins `3 jours` avant la fin d'une époch afin de pouvoir retirer ses fonds après la fin de cette dernière. Les stakers qui ne présentent pas leur demande de retrait verront les $USDC être reportés à l'Epoch suivante.

Pour retirer des fonds, les utilisateurs appellent la fonction \`requestWithdrawal\` pour demander de retirer des fonds pour la prochaine epoch. Les fonds des utilisateurs resteront stakés et non retirables pour l'époch actuelle. À partir de la prochaine époch, les fonds seront « inactifs » et disponibles pour retrait.

À l'epoch suivante, les utilisateurs appellent la fonction \`withdrawStake\` pour retirer des fonds inactifs à une adresse spécifique. Les utilisateurs peuvent sélectionner le montant des fonds inactifs qu'ils souhaitent retirer ou appeler la fonction \`withdrawMaxStake\` pour retirer tous les fonds inactifs. Notez que la fonction \`withdrawMaxStake\` est moins économe en gaz que d'interroger le max via eth\_call et d'appeler \`withdrawStake()\`.

Pour retirer $DYDX du module de sécurité, vous devez procédez de la manière suivante :

* Allez sur [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Cliquez sur « **Demander** » et entrez le montant de DYDX que vous souhaitez retirer du pool.
* Cliquez sur « **Demander un retrait** ». Vous devrez payer des frais de gaz pour retirer des fonds.
* Les stakers qui demandent à retirer des DYDX au moins `3 jours` avant la fin de l'époch actuelle peuvent retirer leurs DYDX au début de l'époch suivante.

