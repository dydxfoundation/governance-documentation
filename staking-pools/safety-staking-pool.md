---
description: Un aperçu du pool de staking de sécurité
---

# Module de sécurité

`2,50 %` de l'offre initiale de jetons (`25 000 000 DYDX`) seront distribués aux utilisateurs qui stakent DYDX dans un pool de sécurité pour soutenir le système.

**Objectifs**

* Démarrez un fonds décentralisé à utiliser en cas d'insolvabilité ou d'autres problèmes avec le protocole.
* Inciter les détenteurs de DYDX à gouverner correctement : les détenteurs de DYDX risquent des événements dilutifs en tant que backstop ultime et agissent en tant que gouverneurs du risque dans le système.

DYDX staké dans le module de sécurité conserve ses droits de proposition et de vote, ainsi que ses capacités de délégation.

Commencez à staker sur [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*

## Aperçu

La sécurité et la protection des utilisateurs sont au centre des préoccupations depuis le lancement du Protocole. Pour cette raison, DYDX sera distribué aux utilisateurs qui stakent DYDX dans la pool de sécurité afin de créer un filet de sécurité supplémentaire pour les utilisateurs du protocole. Les stakers recevront DYDX en continu proportionnellement à leur part du DYDX total dans le pool.

Le pool de sécurité sera mis en ligne lorsque DYDX deviendra transférable le 8 septembre 2021, 15 h 00 UTC.

## Retraits

Les stakers doivent demander de retirer des fonds au moins `14 jours` **(Fenêtre de blocage)** avant la fin de l'époch afin de pouvoir retirer des fonds après la fin de cette époch. Si les stakers ne demandent pas de retrait, leur DYDX staké est reporté à l'epoch suivante.

## Risques

Le DYDX staké peut être réduit en raison d'un événement de pénurie. La réduction se produit à la discrétion de la gouvernance de DYDX et nécessite un vote de gouvernance pour être promulguée.

Comme les participants à tout protocole DeFi, les intervenants du module de sécurité sont exposés au risque de contrat intelligent s'il existe une vulnérabilité dans le code de contrat intelligent sous-jacent. Tous les contrats intelligents DYDX et de gouvernance ont été audités et rigoureusement testés.

## Événements de pénurie

L'interprétation de la survenance d'un événement de pénurie est soumise à un vote de gouvernance dYdX mais peut inclure :

* Solvabilité de l'échange (par exemple, l'échange devient sous-garanti en raison de liquidations non rentables)
* Attaques de contrats intelligents
* D'autres événements que la gouvernance dYdX estime avoir entraîné une pénurie

Lors d'un événement de pénurie, les soldes des détenteurs de jetons peuvent être réduits et transférés vers une autre adresse ou un autre contrat (défini par la gouvernance dYdX au cas par cas). La gouvernance dYdX doit passer une courte proposition de verrouillage pour réduire les jetons stakés. Après un vote de gouvernance sur la réduction des jetons DYDX stakés, les jetons DYDX réduits peuvent être vendus aux enchères sur le marché pour être vendus contre les actifs nécessaires pour atténuer la pénurie encouru.

## FAQ

### Comment puis-je gagner des récompenses de staking ?

Les stakers peuvent déposer des DYDX à tout moment dans le pool de staking de sécurité et commencer à gagner des récompenses immédiatement. Les récompenses DYDX sont gagnées sur une base continue en fonction de la part de chaque staker dans le pool total, seconde par seconde. Les récompenses peuvent être réclamées et retirées à tout moment.

Les fonds actifs gagnent des récompenses pour la période pendant laquelle ils restent actifs. Cela signifie qu'après avoir demandé le retrait de certains fonds, ces fonds continueront à gagner des récompenses jusqu'à la fin de l'epoch. Ceci est démontré dans l'exemple suivant du [pool de staking de liquidité](https://docs.dydx.community/dydx-governance/staking-pools/liquidity-staking-pool) :

![](<../.gitbook/assets/image (65) (1).png>)

Dans le scénario ci-dessus, l'utilisateur gagnerait des récompenses pour la période de **Time0** à **Time2**, variant avec le solde total staké au cours de cette période. Si l'utilisateur ne demande un retrait que pour une partie de son solde, le solde restant continuera à gagner des récompenses au-delà de **Time2**.

### Comment puis-je déposer et staker DYDX sur le pool de sécurité ?

Pour staker DYDX dans la pool de sécurité, procédez comme suit :

* Allez sur [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Cliquez sur « **Staker** »
* Vous devez activer DYDX la première fois que vous déposez. Vous n'aurez à le faire qu'une seule fois et à ne payer qu'une seule fois les frais de gaz.
* Entrez le montant de DYDX que vous souhaitez staker sur le pool.
* Cliquez sur « **Staker des fonds** ». Vous devrez payer des frais de gaz pour staker et annuler des fonds.

Les fonds stakés sont désormais actifs et commencent à gagner des récompenses immédiatement.

Pour déposer et staker des fonds directement sur le contrat intelligent, les utilisateurs appellent la [fonction](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) \`stake\`. Les utilisateurs peuvent également déposer et staker au nom d'une autre adresse en appelant la [fonction](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) \`stakeFor\`.

### Qu'est-ce que stkDYDX ?

Pour contribuer à la sécurité du protocole et recevoir des incitations, les détenteurs de DYDX déposeront leurs jetons dans le module de sécurité. En retour, ils recevront une position tokenisée (**stkDYDX**) qui peut être retirée ou transférée en tant qu'ERC-20. Le jeton **stkDYDX** a les mêmes droits de proposition et de vote que DYDX sur la gouvernance dYdX.

### Qu'est-ce qu'une fenêtre de blocage ?

Une fenêtre de blocage est une période de temps pendant laquelle les utilisateurs ne peuvent pas demander de retraits de fonds stakés. Un calendrier d'epoch est appliqué pour les retraits afin de fournir une prévisibilité et une cadence régulière pour la disponibilité des fonds dans le pool. Un staker doit demander à retirer des fonds avant la fenêtre de blocage afin de pouvoir retirer leurs fonds après la fin de cette période. Si un staker ne demande pas de retrait, leurs fonds stakés sont reportés à l'époch suivante.

La fenêtre de blocage recommandée pour le pool de sécurité est `de 14 jours`.

### Comment fonctionne la comptabilité du solde staké ?

Un solde staké est dans l'un des deux états suivants :

* **Actif** : disponible pour emprunt ; gagner des récompenses de staking ; ne peut pas être retiré par le staker.
* **Inactif** : non disponible pour emprunt ; ne gagne pas de récompenses ; peut être retiré par le staker.

Un staker peut avoir une combinaison de soldes actifs et inactifs. Les fonds sont comptabilisés époch par époch, comme illustré dans l'exemple suivant :

![](<../.gitbook/assets/image (34) (1) (3).png>)

Les opérations suivantes affectent les soldes stakés comme suit :

* **Dépôt** : augmenter le solde actif.
* **Demande** de **retrait** : à la fin de l'époch en cours, déplacez certains fonds actifs vers inactifs.
* **Retrait** : diminuer le solde inactif.
* **Transfert** : déplacer quelques fonds actifs vers un autre staker.

Pour coder le fait qu'un solde peut être programmé pour changer à la fin d'une certaine epoch, nous stockons chaque solde sous la forme d'une structure de trois champs : currentEpoch, currentEpochBalance et nextEpochBalance.

### Comment puis-je retirer des fonds du pool de staking ? Combien de temps cela prend-il ?

Un calendrier d'époch est appliqué pour les retraits afin de fournir une prévisibilité et une cadence régulière pour la disponibilité des fonds dans le pool. Un staker doit demander de retirer des fonds au moins `14 jours` avant la fin d'une époch afin de pouvoir retirer ses fonds après la fin de cette époch. Si les stakers ne demandent pas de retrait, leur DYDX staké est reporté à l'époch suivante.

Pour retirer des fonds, les utilisateurs appellent la fonction \`requestWithdrawal\` pour demander de retirer des fonds pour la prochaine epoch. Les fonds des utilisateurs resteront stakés et non retirables pour l'époch actuelle. À partir de la prochaine époch, les fonds seront « inactifs » et disponibles pour retrait.

À l'epoch suivante, les utilisateurs appellent la fonction \`withdrawStake\` pour retirer des fonds inactifs à une adresse spécifique. Les utilisateurs peuvent sélectionner le montant des fonds inactifs qu'ils souhaitent retirer ou appeler la fonction \`withdrawMaxStake\` pour retirer tous les fonds inactifs. Notez que la fonction \`withdrawMaxStake\` est moins économe en gaz que d'interroger le max via eth\_call et d'appeler \`withdrawStake()\`.

Pour retirer DYDX du pool de liquidité, procédez comme suit :

* Allez sur [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Cliquez sur « **Demander** » et entrez le montant de DYDX que vous souhaitez retirer du pool.
* Cliquez sur « **Demander un retrait** ». Vous devrez payer des frais de gaz pour retirer des fonds.
* Les stakers qui demandent de retirer DYDX au moins 14 jours avant la fin de l'époch en cours peuvent retirer leur DYDX au début de l'époch suivante.

### Quels sont les risques pour les stakers par rapport au pool de staking de sécurité ? Que se passe-t-il dans le cas d'un événement de pénurie ?

La décision d'un staker de verrouiller DYDX dans le pool de sécurité l'expose au risque d'un événement de pénurie, ce qui peut entraîner la réduction des fonds DYDX stakés à la discrétion de la gouvernance de DYDX.

Tous les fonds du contrat, actifs ou inactifs, peuvent être réduits. Dans le cadre du contrat, la réduction est mise en œuvre via une mise à jour du taux de change entre DYDX et stkDYDX Cela signifie que lorsque des réductions se produisent, le taux de change entre DYDX et stkDYDX divergera de sa valeur initiale de 1:1. Notez que le gain des récompenses de staking n'est pas affecté par les réductions.
