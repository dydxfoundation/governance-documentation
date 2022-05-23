---
description: Aperçu des pools de staking de liquidité.
---

# Pool de staking de liquidité

2,5 % \(`25 000 000 DYDX`\) seront distribués aux utilisateurs qui stakent l'USDC dans un pool de staking de liquidités.

### Objectifs

* Effets du réseau de liquidité Bootstrap dYdX

## Aperçu

La liquidité, surtout lorsqu'elle est utilisée correctement, est un composant central de tout échange réussi. Pour promouvoir les effets de réseau de liquidité et inciter les teneurs de marché professionnels, DYDX sera distribué aux utilisateurs qui investissent l'USDC dans le pool de staking de liquidité. Les teneurs de marché connus et approuvés utiliseront l'USDC jalonné pour créer des marchés sur le protocole, augmentant ainsi la liquidité disponible sur les marchés. Les teneurs de marché ne pourront pas retirer l'USDC du protocole, les obligeant à l'utiliser uniquement dans le protocole. Cependant, une partie de l'USDC staké pourrait être perdue si un teneur de marché devait perdre des fonds \(via des transactions non rentables\) et être incapable de reconstituer le pool de staking de liquidités. Les miseurs recevront du DYDX, distribué en continu en fonction de la part de chaque staker du total USDC dans le pool. Un staker doit demander à retirer l'USDC au moins `14 jours` \(**Fenêtre de blocage**\) avant l'époch afin de pouvoir retirer son USDC après la fin de cette époch. Si les stakers ne demandent pas à retirer, leur USDC stkaé est reporté à l'époch suivante.

## Emprunteurs approuvés

Le contrat Liquidity Staking Pool fonctionne comme un système de prêt bilatéral sous-garanti.

Le montant pouvant être retiré dépend du pourcentage d'allocation d'un emprunteur et du total des fonds disponibles mis en jeu dans le pool. Le pourcentage d'allocation et le total des fonds disponibles peuvent changer, à des moments prédéfinis spécifiés par `LS1EpochSchedule`. Les fonds empruntés ne peuvent être utilisés que sur l'échange de couche 2 de dYdX. Ceci est appliqué via le contrat `TrustedBorrowerL2Proxy` qui interagit avec le contrat d'échange L2 \(`StarkPerpetual`\).

Les premiers fournisseurs de liquidités approuvés comprennent `Wintermute`, `Sixtant`, `Kronos`, `Amber` et `MGNR`, qui ont activement tenu le marché sur le protocole depuis son lancement.

| Emprunteurs préapprouvés | Pourcentage d'allocation initiale | Détails sur les fournisseurs de liquidités |
| :--- | :--- | :--- |
| Wintermute | `X %` TBD | [https://dydx.exchange/blog/ama-recap-wintermute](https://dydx.exchange/blog/ama-recap-wintermute) |
| Sixtant | Y % TBD | [https://dydx.exchange/blog/ama-recap-sixtant](https://dydx.exchange/blog/ama-recap-sixtant) |
| Kronos \(Wootrade\) | Z % TBD | [https://dydx.exchange/blog/ama-recap-wootrade](https://dydx.exchange/blog/ama-recap-wootrade) |
| Amber | Z % TBD |  |
| MGNR | Z % TBD |  |

Lorsque les utilisateurs demandent à retirer des fonds, le solde alloué à un emprunteur pour la prochaine époch peut tomber en dessous de son montant actuellement emprunté. Dans cette situation, l'emprunteur est responsable de rembourser la différence entre leurs soldes empruntés et alloués avant la fin de l'époch. Si le solde emprunté d'un emprunteur est supérieur à son allocation au début de l'époch suivante, on s'attend à ce qu'il restitue la différence avant le début de cette époch et on lui fait confiance.

Au fur et à mesure que les emprunteurs empruntent et remboursent des fonds, leur solde net emprunté est enregistré. Le solde total net emprunté de tous les emprunteurs est également suivi. Le solde restant détenu par le contrat est appelé le solde non emprunté.

L'égalité suivante s'applique à tout moment lorsque l'on considère le contrat dans son ensemble :

total actif + total inactif = total emprunté + total non emprunté

### Gouvernance

La gouvernance dYdX est responsable pour :

* Faire une diligence raisonnable sur les emprunteurs existants
* Ajouter de nouveaux emprunteurs au pool de staking
* Modifier des allocations de fonds empruntés aux emprunteurs approuvés
   * Les fonctions \`setBorrowerAllocations\` et \`setBorrowingRestriction\` sont appelées à modifier les allocations de certains emprunteurs. Elles peuvent être utilisées pour ajouter et supprimer des emprunteurs. Les augmentations prennent effet à l'époch suivante, mais les diminutions restreignent immédiatement les emprunts. Ces fonctions ne peuvent pas être appelées pendant la fenêtre de blocage.
* La durée de l'époch et la fenêtre de blocage sont définies lors de la création du contrat, mais peuvent être modifiées par la gouvernance dYdX

### Comptabilité du solde staké

Un solde staké est dans l'un des deux états suivants :

* Actif : disponible pour emprunt ; gagner des récompenses de mise ; ne peut pas être retiré par le staker.
* Inactif : non disponible pour emprunt ; ne gagne pas de récompenses ; peut être retiré par le staker.

Un staker peut avoir une combinaison de soldes actifs et inactifs. Les fonds sont comptabilisés époch par époch, comme illustré dans l'exemple suivant :

Les opérations suivantes affectent les soldes stakés comme suit :

* Dépôt : augmenter le solde actif.
* Demande de retrait : à la fin de l'époch en cours, déplacez certains fonds actifs vers inactifs.
* Retrait : diminuer le solde inactif.
* Transfert : déplacer quelques fonds actifs vers un autre staker.

Pour coder le fait qu'un solde peut être programmé pour changer à la fin d'une certaine époch, nous stockons chaque solde sous la forme d'une structure de trois champs : currentEpoch, currentEpochBalance et nextEpochBalance. Les soldes des utilisateurs inactifs utilisent également le champ shortfallCounter.

## FAQ

### Comment puis-je gagner des récompenses de staking ?

Les stakers peuvent déposer des USDC à tout moment dans le pool de staking de liquidités et commencer à gagner des récompenses immédiatement. Les récompenses DYDX sont gagnées sur une base continue en fonction de la part de chaque staker dans le pool total. Les récompenses peuvent être réclamées et retirées à tout moment.

### Comment puis-je déposer et staker des USDC dans le pool de liquidités ?

Pour déposer et miser des fonds, les utilisateurs appellent la [fonction](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) \`stake\. Les utilisateurs peuvent également déposer et staker au nom d'une autre adresse en appelant la [fonction](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) \`stakeFor\`.

Pour staker des USDC sur le pool de liquidité, suivez les étapes suivantes :

* Cliquez sur « Staker »
* Vous devez activer les USDC la première fois que vous déposez. Vous n'aurez à le faire qu'une seule fois.
* Entrez le montant de USDC que vous souhaitez staker au pool
* Cliquez sur « Staker des fonds » - vous devrez payer des frais de gaz pour staker et annuler des fonds

![](https://lh4.googleusercontent.com/caSDz783Gi-asRNYP8Gm8L5qv_yAuJZwEmUAfl8I1MfHecIF2In10IQCqZBCIpxeXl90eT28GGLbZyts8-x9U5w4Y6LBC4kyehMEalsZu_-aI11S6V7nwPrwtcc75m2M8847jFvv)

Les fonds stakés sont actifs et commencent à gagner des récompenses immédiatement.

### Comptabilité des récompenses

Les fonds actifs gagnent des récompenses pour la période pendant laquelle ils restent actifs. Cela signifie qu'après avoir demandé le retrait de certains fonds, ces fonds continueront à gagner des récompenses jusqu'à la fin de l'époch. Par exemple :

Dans le scénario ci-dessus, l'utilisateur gagnerait des récompenses pour la période de t\_0 à t\_2, variant avec le solde total staké au cours de cette période. Si l'utilisateur ne demande un retrait que pour une partie de son solde, le solde restant continuera à gagner des récompenses au-delà de t\_2.

### Qu'est-ce qu'une fenêtre de blocage ?

Une fenêtre de blocage est une période de temps pendant laquelle les utilisateurs ne peuvent pas demander de retraits de fonds stakés. La fonction \`requestWithdrawal\` ne peut pas être appelée pendant une fenêtre de blocage, qui est initialement configurée comme les 14 derniers jours d'une époch. Les nouvelles épochs commencent tous les 28 jours. En d'autres termes, les utilisateurs peuvent demander un retrait pour l'époch suivante jusqu'à 7 jours avant la fin d'une époch donnée.

### Comment puis-je retirer des fonds du pool de staking ? Combien de temps cela prend-il ?

Un calendrier d'époch est appliqué pour les retraits afin de fournir une prévisibilité et une cadence régulière pour la disponibilité des fonds dans le pool. Un staker doit demander de retirer des fonds au moins 14 jours avant la fin d'une époch afin de pouvoir retirer ses fonds après la fin de cette époch. Si les stakers ne demandent pas à retirer, leur USDC staké est reporté à l'époch suivante

Pour retirer des fonds, les utilisateurs appellent la [fonction](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L73-L83) \`requestWithdrawal\` pour demander de retirer des fonds pour la prochaine époch. Les fonds des utilisateurs resteront stakés et non retirables pour l'époch actuelle. À partir de la prochaine époch, les fonds seront « inactifs » et disponibles pour retrait.

À l'époch suivante, les utilisateurs appellent la fonction \`[withdrawStake](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L91)\` pour retirer des fonds inactifs à une adresse spécifique. Les utilisateurs peuvent sélectionner le montant des fonds inactifs qu'ils souhaitent retirer ou appeler la fonction \`withdrawMaxStake\` pour retirer tous les fonds inactifs. La fonction \`withdrawMaxStake\` est moins économe en gaz que d'interroger le max via eth\_call et d'appeler \`withdrawStake\(\)\`.

### Quels sont les risques du staking par rapport au pool de staking de liquidité ? Que se passe-t-il si un emprunteur ne rembourse pas sa dette ?

Les prêts non garantis s'accompagnent d'un niveau de confiance beaucoup plus élevé qui doit être respecté par un emprunteur. Les fournisseurs de liquidité ne peuvent pas retirer l'USDC staké du protocole, les obligeant à l'utiliser uniquement dans le protocole. Néanmoins, l'USDC staké pourrait être perdu si un fournisseur de liquidités devait perdre des fonds et être incapable de reconstituer ses allocations empruntées par le biais de sources de financement externes.

Dans ce cas, les fonds inactifs peuvent subir des pertes socialisées au prorata en cas de manque à gagner où un emprunteur tarde à rembourser les fonds dont le retrait a été demandé. En cas de défaut sur un prêt non garanti, un emprunteur mauvais payeur fera face à des dommages importants à sa réputation.

Solvabilité du contrat :

À tout moment, le contrat sera dans l'un des états suivants en fonction de la relation entre les soldes stakés et empruntés :

| ![](https://lh3.googleusercontent.com/nTJuAC4WSmhOiAGkM6r-YWzy6z2MIHQnydr8U0n-TReAh_gfqD6ZyalxQpYv9RNBsJzrlw78QB_wp9utqBc-PQZipwzWpxDifD1_zEtyVBhYXRl_f8V-iDMwLBO70LQsftDlXrsr) | ![](https://lh3.googleusercontent.com/x_Yev8ZJrYYm8FTDSdoj0jDXEBY_b9xOC69lpQudQdoALQ_tuQFEbFc5hAU6TbpGNCB6J2BsjMwHb59GrCqR52747j45jSC_BmyzyiY72gTRk4oamv35gO8PPZalA43COZF1pgtP) |
| :--- | :--- |
| ![](https://lh6.googleusercontent.com/wX37DQoW9oR4OhJzb4hc5ZxPE1X05OPfyETbUv7WTY0b__WH2PydjJoBuQIREHgeWL18GDn7E1ORgGmcre0R6iYPmwSsdFNzBZ7DBPs0wkajjoDBjxDYDPHcet_-dPPAyS1GWL0v) |  |

Le contrat est dit insolvable si :

* le solde total emprunté est supérieur au solde actif total
* de manière équivalente : le solde total inactif est supérieur au solde total non emprunté
* de manière équivalente : le solde total retirable est supérieur au solde USDC du contrat

Dans le cas contraire, le contrat est dit solvable.

Étant donné que l'emprunt est limité à la proportion de fonds actifs alloués à un emprunteur et que le solde inactif ne peut augmenter qu'entre les épochs \ (sauf dans le cas de transferts USDC « nus » vers le contrat \), le contrat ne peut généralement passer que d'un solvable à un état insolvable pendant les transitions entre les épochs.

Un emprunteur individuel aura toujours un préavis d'au moins une semaine avant que son propre solde alloué ne tombe en dessous de son solde emprunté impayé. Une telle transition ne peut se faire qu'entre des épochs.

Tant que le contrat est insolvable, les utilisateurs peuvent ne pas être en mesure de retirer tous les fonds qui leur sont dus. En outre, la situation présente des risques supplémentaires s'il existe une incertitude quant à savoir si le déficit sera comblé et à quelle vitesse :

1. Les utilisateurs peuvent être dissuadés de staker des fonds supplémentaires, car cela peut les mettre dans une position où ils ne peuvent pas récupérer leurs fonds.
2. Les utilisateurs actuellement stakés peuvent être incités à « prendre la porte » et à se retirer dès que possible, afin de maximiser leurs chances de récupérer leurs fonds.

Les pertes sont suivies via des indices qui représentent la fraction des fonds inactifs qui ont été convertis en dette lors d'un événement déficitaire donné. Chaque solde inactif du staker stocke un compteur de déficits mis en cache, représentant le nombre de pénuries qui se sont produites dans le passé par rapport à la dernière mise à jour du solde. Toute perte subie par un solde inactif se traduit par un crédit égal au solde de la dette de ce staker. Consultez LS1DebtAccounting pour plus d'informations sur la façon dont l'indice est calculé.

Si le contrat est insolvable, la fonction markDebt\(\) peut être appelée \(par n'importe qui\), ciblant un emprunteur qui a dépassé son allocation. L'excédent de leur solde emprunté sur leur solde d'allocation est appelé leur solde débiteur. Le montant du solde de la dette est déplacé de leur solde emprunté vers un solde spécial utilisé spécifiquement pour tenir compte de la dette impayée.

Un ajustement égal est effectué sur la comptabilisation des fonds stakés. Un montant égal au montant de la dette est retiré des soldes inactifs et ajouté à un solde spécial comptabilisant la dette manquante due aux stakers. Le solde inactif de chaque staker subira une décote et chaque staker recevra un montant équivalent sous forme de dette. De cette manière, la perte due à l'insolvabilité est socialisée \(au prorata)\ sur tous les stakers détenant des soldes inactifs.

Ce processus est illustré ci-dessous :

![](https://lh5.googleusercontent.com/2b2e67wVF3DL32NU0ykTVV0PJWaJ_bdmRQRKgx-5c3_qr_nWNYsuE77JviLtbBxXzASEfIp2Fw4hvzRPeM1a7TAIxq0NYUfo3dZLUhChilDpa5Ygq-YugSvNXKmyf2ul3GQM22SZ)

Si l'emprunteur endetté rembourse la dette \ (ou si une autre partie, telle que la gouvernance, la rembourse en son nom \), les stakers à qui la dette était due peuvent récupérer les fonds selon le principe du premier arrivé, premier servi.

### Que représente la dette ?

La dette

### Y a-t-il un recours pour les stakers en cas de défaillance d'un emprunteur ?

Lorsque markDebt\(\) est appelé sur un emprunteur, cet emprunteur perd le droit d'emprunter des fonds supplémentaires du contrat. Ce droit peut être réintégré par la gouvernance.

Ajouter potentiellement du contenu sur l'accord de teneur de marché avec la Fondation

