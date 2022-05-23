---
description: Un aperçu du pool de staking de liquidité
---

# Module de liquidité

`2,50 %` de l'offre initiale de jetons (`25 000 000 DYDX`) seront distribués aux utilisateurs stakant des USDC dans le pool de staking de liquidité.

### Objectifs

* Encourager l'allocation d'USDC à des fins de tenue de marché sur le protocole de couche 2 de dYdX.
* Allouez des capitaux aux fournisseurs de liquidités les plus performants pour augmenter la propagation, la profondeur et la disponibilité sur dYdX.

Commencez à miser sur [**dydx.community/dashboard/pools/liquidity**](https://dydx.community/dashboard/pools/liquidity)**.**

## Aperçu **du staking**

La liquidité est un composant central de tout échange réussi. Pour promouvoir les effets de réseau de liquidité et inciter les fournisseurs de liquidité professionnels, DYDX sera distribué aux utilisateurs qui investissent l'USDC dans le pool de staking de liquidité. Les fournisseurs de liquidités approuvés par la communauté utiliseront l'USDC jalonné pour créer des marchés sur le protocole dYdX de couche 2, renforçant ainsi la liquidité disponible sur les marchés. Les fournisseurs de liquidité ne sont pas autorisés à utiliser des fonds empruntés en dehors du protocole de couche 2 de dYdX.

Les stakers gagneront des récompenses DYDX pour avoir staké les USDC. Les récompenses DYDX seront distribuées en continu en fonction de la part de chaque participant du total USDC dans le pool.

Chaque staker et fournisseur de liquidité sont tenus de devenir partie au contrat de crédit renouvelable (lien [ici](https://dydx.foundation/revolving-credit-agreement)). L'accord met en langage naturel les termes du pool de staking de liquidité pour donner à chaque intervenant un droit exécutoire contre tout fournisseur de liquidité qui ne rembourse pas les USDC empruntés. L'accord n'est conclu qu'entre chaque staker et chaque fournisseur de liquidité. La Fondation dYdX n'est pas partie à l'accord et n'a aucun droit ou obligation en vertu de celui-ci.

## Désengagement et retraits des USDC

Un staker doit demander de retirer des USDC au moins `14 jours` (**fenêtre de blocage**) avant la fin d'une [**époch**](../start-here/epochs.md) afin de pouvoir retirer les USDC du staker après la fin de cette époch. Si les stakers ne demandent pas à retirer, leur USDC staké est reporté à l'époch suivante.

Les retraits ne peuvent être demandés pendant la **fenêtre de blocage**.

## Risques du staking

Les emprunteurs du pool ne sont pas tenus de verrouiller les garanties. Tous les emprunteurs sont des fournisseurs de liquidités professionnels et réputés. La liste des emprunteurs autorisés et leurs allocations de pool sont mises à jour par la gouvernance.

Lorsque les utilisateurs demandent à retirer des USDC, le solde alloué d'un emprunteur pour l'époch suivante peut tomber en dessous du montant actuellement emprunté par l'emprunteur. Dans cette situation, l'emprunteur est responsable de rembourser la différence entre ses soldes empruntés et alloués avant la fin de l'époch.

Si un emprunteur ne rembourse pas un solde dû au pool d'ici la fin de l'époque, il est considéré comme en défaut et n'est pas autorisé à emprunter davantage d'USDC jusqu'à ce que la dette soit remboursée. Les stakers peuvent perdre les USDC dans le cas où un emprunteur ne rembourse jamais une dette. Les miseurs peuvent perdre une partie de l'USDC jalonné si un teneur de marché devait perdre l'USDC et être incapable de reconstituer le pool de jalonnement de liquidités.

Les stakers sont également exposés au risque de contrat intelligent s'il existe une vulnérabilité dans le code de contrat intelligent sous-jacent. Tous les contrats intelligents DYDX et de gouvernance ont été audités et rigoureusement testés.

Afin de réduire le risque pour les stakers, chaque staker et fournisseur de liquidités sera tenu de devenir partie à l'accord de crédit renouvelable (lien [ici](https://dydx.foundation/revolving-credit-agreement)), mais la conclusion de l'accord ne garantit pas qu'un fournisseur de liquidités remboursera tous les montants empruntés, même si les droits d'un staker en vertu de l'accord sont appliqués.

## Emprunteurs approuvés

Le contrat Liquidity Staking Pool fonctionne comme un système de liquidité à deux faces, sous-garanti et sans intérêt.

Le montant pouvant être retiré dépend du pourcentage d'allocation d'un emprunteur et du total d'USDC disponible mis en jeu dans le pool. Le pourcentage d'allocation et le total d'USDC disponible peuvent changer, à des heures prédéfinies spécifiées par `LS1EpochSchedule`. Les USDC empruntés ne peuvent être utilisés que sur le protocole de couche 2 de dYdX - ceci est appliqué via le contrat `StarkProxy` qui interagit avec le contrat `StarkEx Perpetual Exchange`.

Les fournisseurs de liquidités initialement approuvés comprennent `Wintermute`, `Amber Group`, `Wootrade (Kronos)`, `Sixtant` et `DAT Trading`, qui ont activement tenu le marché sur le protocole de couche 2 de dYdX.

| Emprunteurs préapprouvés | Pourcentage d'allocation initiale | Adresse Ethereum | StarkProxy | Détails sur les fournisseurs de liquidités |
| ---------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wintermute | 25 % | [0x4f3a120E72C76c22ae802D129F599BFDbc31cb81](https://etherscan.io/address/0x4f3a120E72C76c22ae802D129F599BFDbc31cb81) | [0x0b2B08AC98a1568A34208121c26F41a9e0FbB6](https://etherscan.io/address/0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6) | [https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/](https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/) |
| Groupe Amber | 25 % | [0x39Ad99E33ab7Ee85818741dD6076112188bc2611](https://etherscan.io/address/0x39Ad99E33ab7Ee85818741dD6076112188bc2611) | [0x3e6E9EFb0A677a24F47093a22044dc5451A028cF](https://etherscan.io/address/0x3e6E9EFb0A677a24F47093a22044dc5451A028cF) | [https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/](https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/) |
| Réseau WOO (Kronos) | 20 % | [0x38d981c3c42b2ec8e9572f560552407d0f1279fb](https://etherscan.io/address/0x38d981c3c42b2ec8e9572f560552407d0f1279fb) | [0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06](https://etherscan.io/address/0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06) | [https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/](https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/) |
| Sixtant | 20 % | [0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c](https://etherscan.io/address/0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c) | [0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2](https://etherscan.io/address/0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2) | [https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/](https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/) |
| Trading DAT | 10 % | [0x83E8fb8f4DAE0f42d68FdbBf85d4191a5e6f92F8](https://etherscan.io/address/0x83e8fb8f4dae0f42d68fdbbf85d4191a5e6f92f8) | [0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874](https://etherscan.io/address/0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874) | [https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/](https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/) |

## Comptabilité du solde staké

Un solde staké est dans l'un des deux états suivants :

* **Actif** : disponible pour emprunt ; gagne des récompenses de staking ; ne peut pas être retiré par le staker.
* **Inactif** : non disponible pour emprunt ; ne gagne pas de récompenses ; peut être retiré par le staker.

Un staker peut avoir une combinaison de soldes actifs et inactifs. USDC est comptabilisé époch par époch, comme indiqué dans l'exemple suivant :

![Staked balance accounting](<.. /.gitbook/assets/image (34).png>)

Les opérations suivantes affectent les soldes stakés comme suit :

* **Dépôt** : augmenter le solde actif.
* **Demande de retrait** : à la fin de l'époch en cours, déplacez certains USDC actifs vers inactifs.
* **Retrait** : diminuer le solde inactif.
* **Transfert** : déplacer quelques USDC actifs vers un autre staker.

Pour coder le fait qu'un solde peut être programmé pour changer à la fin d'une certaine époch, nous stockons chaque solde sous la forme d'une structure de trois champs : currentEpoch, currentEpochBalance et nextEpochBalance. Les soldes des utilisateurs inactifs utilisent également le champ shortfallCounter.

### Qu'est-ce que stkUSDC ?

Les détenteurs d'USDC qui déposent et stakent leur USDC dans le pool de staking de liquidité recevront une position tokenisée (**stkUSDC**). stkUSDC est créé lorsqu'un utilisateur stake des USDC et brûlé lorsqu'un utilisateur appelle `withdrawStake`. Dans la même transaction que l'USDC quitte le portefeuille d'un staker, stkUSDC entre dans le portefeuille du staker ; ou vice-versa lors du détachement.

Un solde stkUSDC peut être actif ou inactif. Le stkUSDC actif peut être transféré en tant qu'ERC-20, mais ne peut pas être retiré. Le stkUSDC inactif peut être retiré, mais ne peut pas être transféré. Par exemple, un utilisateur peut avoir 100 stkUSDC actifs et 100 inactifs dans son portefeuille, et le solde de l'utilisateur affichera 200 stkUSDC, mais un transfert sera annulé si l'utilisateur essaie de transférer plus de 100 stkUSDC.

Un solde staké pour lequel le staker a demandé un retrait avant la fin de l'époch serait considéré comme inactif, et donc non transférable.

## FAQ sur les **stakers**

### Comment puis-je gagner des récompenses de staking ?

Les stakers peuvent déposer l'USDC à tout moment dans le pool de staking de liquidités et commencer à gagner des récompenses immédiatement. Les récompenses DYDX sont gagnées sur une base continue en fonction de la part de chaque staker dans le pool total, seconde par seconde. Les récompenses peuvent être réclamées et retirées à tout moment.

L'USDC staké gagne des récompenses pour la période pendant laquelle il reste actif. Cela signifie qu'après avoir demandé un retrait de certains USDC, cet USDC continuera à gagner des récompenses jusqu'à la fin de l'époch. Par exemple :

![Rewards accounting](<.. /.gitbook/assets/image (65).png>)

Dans le scénario ci-dessus, l'utilisateur gagnerait des récompenses pour la période de **Time0** à **Time2**, variant avec le solde total staké au cours de cette période. Si l'utilisateur ne demande un retrait que pour une partie du solde de l'utilisateur, le solde restant continuera à gagner des récompenses au-delà de **Time2**.

### Comment puis-je déposer et staker des USDC dans le pool de liquidités ?

Pour implanter l'USDC dans le pool de liquidités, suivez ces étapes :

* Allez sur [https://dydx.community/dashboard/pools/liquidity](https://dydx.community/dashboard/pools/liquidity)
* Cliquez sur « Staker »
* Vous devez activer l'USDC la première fois que vous déposez. Vous n'aurez à le faire qu'une seule fois et à ne payer qu'une seule fois les frais de gaz.
* Entrez le montant de USDC que vous souhaitez staker sur le pool.
* Cliquez sur « Staker des fonds » - vous devrez payer des frais de gaz pour staker, demander de retirer et retirer les USDC.

![](<.. /.gitbook/assets/image (57).png>)

L'USDC staké est maintenant actif et commence à gagner des récompenses immédiatement.

Pour déposer et staker des USDC directement sur le contrat intelligent, les utilisateurs appellent la fonction `stake`. Les utilisateurs peuvent également déposer et staker des USDC pour le compte d'une autre adresse en appelant la fonction `stakeFor`. Même si vous stakez directement des USDC sur le contrat intelligent, vous serez réputé avoir pris connaissance de l'accord de crédit renouvelable et l'avoir examiné (lien [ici](https://dydx.foundation/revolving-credit-agreement)).

### Qu'est-ce qu'une fenêtre de blocage ?

Une fenêtre de blocage est une période de temps pendant laquelle les utilisateurs ne peuvent pas demander de retraits des USDC stakés. La fonction `requestWithdrawal` ne peut pas être appelée pendant une fenêtre de blocage, qui est initialement configurée comme les `14 derniers jours` d'une époch. Les nouvelles épochs commencent tous les 28 jours. En d'autres termes, les utilisateurs peuvent demander un retrait pour l'époch suivante jusqu'à `14 jours` avant la fin d'une époch donnée.

### Comment puis-je retirer des USDC du pool de staking ? Combien de temps cela prend-il ?

Un calendrier d'époch est appliqué pour les retraits afin de fournir une prévisibilité et une cadence régulière pour la disponibilité des USDC dans le pool. Un staker doit demander à retirer l'USDC au moins `14 jours` avant la fin d'une époch afin de pouvoir retirer les USDC du staker après la fin de cette époch. Si les stakers ne demandent pas à retirer, leur USDC staké est reporté à l'époch suivante.

Pour retirer l'USDC, les utilisateurs appellent la fonction `requestWithdrawal` pour demander de retirer l'USDC pour la prochaine époch. Les fonds des utilisateurs resteront stakés et non retirables pour l'époch actuelle. À partir de la prochaine époch, les fonds seront « inactifs » et disponibles pour retrait.

À la prochaine époch, les utilisateurs appellent la fonction `withdrawStake` pour retirer l'USDC inactif à une adresse spécifique. Les utilisateurs peuvent sélectionner le montant des fonds inactifs qu'ils souhaitent retirer ou appeler la fonction \`withdrawMaxStake\` pour retirer tous les fonds inactifs. La fonction `withdrawMaxStake` est moins économe en gaz que d'interroger le max via eth\_call et d'appeler `withdrawStake()`.

Pour annuler l'USDC sur le pool de liquidité, suivez les étapes suivantes :

* Allez sur [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)****
* Cliquez sur « **Demande** », pour ouvrir le modèle suivant :

![Requesting withdraw](<.. /.gitbook/assets/image (58).png>)

* Entrez le montant d'USDC que vous souhaitez demander de retirer du pool, puis cliquez sur "**Demander un retrait**". Vous devrez payer des frais de gaz pour annuler l'USDC.
* Les stakers qui demandent à retirer l'USDC au moins 14 jours (**fenêtre de blocage**) avant la fin de l'époch en cours peuvent retirer leur USDC au début de l'époch suivante.

### Quels paramètres la gouvernance peut-elle changer ?

La gouvernance dYdX est responsable pour :

* Faire une diligence raisonnable sur les emprunteurs existants
* Ajouter de nouveaux emprunteurs et/ou supprimer des emprunteurs existants du pool de staking de liquidité
* Modification des allocations de l'USDC emprunté aux emprunteurs approuvés
   * Les fonctions `setBorrowerAllocations` et `setBorrowingRestriction` sont appelées à modifier les allocations de certains emprunteurs. Elles peuvent être utilisées pour ajouter et supprimer des emprunteurs. Les augmentations prennent effet à l'époch suivante, mais les diminutions restreignent immédiatement les emprunts. Ces fonctions ne peuvent pas être appelées pendant la fenêtre de blocage.
* La durée de l'époch et la fenêtre de blocage sont définies lors de la création du contrat, mais peuvent être modifiées

## **FAQ sur les emprunteurs**

### **Emprunter**

L'USDC staké entre dans un pool qui est alloué aux emprunteurs approuvés. Chaque emprunteur dispose d'un pourcentage d'allocation contrôlé par la gouvernance et peut emprunter jusqu'à cette allocation. Le désengagement est soumis à un « calendrier d'époch » - l'USDC staké ne peut devenir retirable (c'est-à-dire « inactif ») qu'au début d'une époch.

L'USDC demandé pour le retrait doit être retourné par les emprunteurs avant la fin de l'époch. En cas de sous-paiement, le montant sous-payé devient un « solde débiteur » et le contrat de staking est re-stabilisé. L'emprunteur fautif doit rembourser le solde de la dette et sera interdit d'emprunter jusqu'à ce qu'il soit réintégré par la gouvernance.

Les emprunteurs sont soumis à toutes les conditions du contrat de crédit renouvelable (lien [ici](https://dydx.foundation/revolving-credit-agreement)).

### **Fonctionnalités StarkProxy**

#### **Paiement automatique**

Les emprunteurs peuvent utiliser `autoPayOrBorrow()` pour garantir une utilisation maximale de l'USDC alloué et le remboursement en temps opportun des retraits demandés. La fonction n'a besoin d'être appelée avec succès qu'une seule fois par époch pour qu'un emprunteur s'assure qu'il s'acquitte de ses responsabilités.

La fonction s'annulera si elle est appelée dans la première moitié de l'époch, car c'est en dehors de la fenêtre de blocage. Elle reviendra si le contrat `StarkProxy` n'a pas assez d'USDC pour le remboursement. Dans ce cas, USDC doit être ajouté ou retiré de l'échange avant d'appeler `autoPayOrBorrow()`.

#### **USDC appartenant à l'emprunteur**

Un emprunteur peut déposer en toute sécurité son propre USDC sur le `StarkProxy` et l'utiliser sur le protocole de couche 2 de dYdX dans le même compte que l'USDC emprunté. L'USDC peut être retiré de `StarkProxy` dans l'une des situations suivantes :

* L'USDC détenu dans le contrat `StarkProxy` au-delà du solde emprunté peut être retiré à tout moment.
* La gouvernance peut approuver le retrait d'un certain montant.
   * Remarque : cela peut être utilisé pour permettre à l'emprunteur de retirer des bénéfices sans avoir à déplacer la plupart des USDC hors du protocole de couche 2 de dYdX.

#### **Les rôles d'emprunteur**

Le contrat `StarkProxy` prend en charge les rôles contrôlés par l'emprunteur suivants. Ceux-ci peuvent être détenus par une adresse unique ou des adresses distinctes selon les besoins de sécurité de l'emprunteur. Chaque rôle peut être détenu par n'importe quel nombre d'adresses.

Propriétaire

* Octroyer ou révoquer le rôle d'administrateur de la délégation.
* Ajouter ou supprimer les destinataires autorisés pour l'USDC retiré de `StarkProxy`.
* Ajouter ou supprimer les clés STARK autorisées à utiliser sur le protocole de couche 2 de dYdX.
* Définir les allocations ERC20 sur les contrats `LiquidityStakingV1` et `StarkPerpetual`.
* Appeler `forcedWithdrawalRequest()` ou `forcedTradeRequest()` sur le contrat `StarkEx Perpetual Exchange`.

Administrateur de délégation

* Accorder ou révoquer les rôles d'emprunteur, d'opérateur d'échange et d'opérateur de retrait.

Emprunteur

* Appeler `autoPayOrBorrow()`, `borrow()`, `repay()` et `repayDebt()` sur le contrat de staking de liquidité.

Opérateur d'échange

* Appeler `registerUserOnExchange()`, `depositToExchange()` et `withdrawFromExchange()` sur le contrat `StarkEx Perpetual Exchange`.

Opérateur de retrait

* Effectuer un retrait externe valide (voir ci-dessus) de `StarkProxy` vers un destinataire autorisé.

#### **Limitations**

Les transferts de couche 2 sur le protocole de couche 2 de dYdX sont désactivés pour les comptes contrôlés par un `StarkProxy`.

#### **Pouvoirs du gardien**

Le rôle du gardien sera contrôlé par la gouvernance dYdX. Son rôle est d'assurer la sécurité des USDC empruntés et de permettre leur restitution aux stakers en cas de perte ou d'abus de la clé privée d'un emprunteur.

Le tuteur peut prendre les mesures suivantes à tout moment (sous réserve de blocage horaire) :

* Restreindre l'emprunt et le dépôt d'USDC empruntés à l'échange.
* Rembourser un solde emprunté en utilisant USDC dans le contrat `StarkProxy`.
* Rembourser un solde de dette en utilisant USDC dans le contrat `StarkProxy`.
* Retrait du contrat StarkEx vers le contrat `StarkProxy` (par exemple, comme deuxième étape d'un retrait lent de l'échange).
* Annuler une demande de transaction forcée initiée par l'emprunteur.
* Autoriser l'emprunteur à retirer un montant du contrat `StarkProxy` tout en contournant la vérification du solde.
* Mettez à niveau le contrat intelligent.

**Le tuteur peut prendre les mesures suivantes si l'emprunteur a un solde débiteur impayé (sous réserve de blocage temporel) :**

* Effectuer un retrait forcé du protocole de couche 2 de dYdX.
* Effectuer une transaction forcée (réduction uniquement) sur le protocole de couche 2 de dYdX.

## FAQ sur les risques de staking

### Quels sont les risques de staking par rapport au pool de staking de liquidité ? Que se passe-t-il si un emprunteur ne rembourse pas les fonds empruntés ?

Un système d'emprunt non garanti exige une norme de confiance beaucoup plus élevée qui doit être respectée par un emprunteur. Les fournisseurs de liquidités empruntant auprès du pool de staking de liquidité ne peuvent pas déplacer les fonds empruntés en dehors du système de staking de liquidité et du protocole de couche 2 de dYdX. Néanmoins, l'USDC staké pourrait être perdu si un fournisseur de liquidités devait perdre des fonds et être incapable de reconstituer ses allocations empruntées par le biais de sources de financement externes.

Dans ce cas, les fonds inactifs peuvent être soumis à des pertes socialisées comme indiqué ci-dessous en cas de manque à gagner où un emprunteur est en retard pour rembourser les fonds qui ont été demandés pour le retrait. En cas de défaut sur les fonds empruntés, un emprunteur défaillant fera face à des dommages importants à sa réputation.

Bien que chaque staker et emprunteur soit partie à l'accord de crédit renouvelable (lien [ici](https://dydx.foundation/revolving-credit-agreement)), cet accord ne garantit pas que les emprunteurs rembourseront leurs obligations.

### Comment le contrat maintient-il la solvabilité ?

À tout moment, le contrat sera dans l'un des états suivants en fonction de la relation entre les soldes stakés et empruntés :

![Contract Solvency](<.. /.gitbook/assets/image (41).png>)

Le contrat est dit **insolvable** :

* si le solde total emprunté est supérieur au solde actif total ;
* ou de manière équivalente, si le solde total inactif est supérieur au solde total non emprunté ;
* ou de manière équivalente, si le solde total pouvant être retiré est supérieur au solde USDC du contrat.

Dans le cas contraire, le contrat est dit **solvable**.

Étant donné que l'emprunt est limité à la proportion allouée à un emprunteur d'USDC actif et que le solde inactif ne peut augmenter qu'entre les épochs, le contrat ne peut généralement passer d'un état solvable à un état insolvable que pendant les transitions entre les épochs.

Si, au début d'une nouvelle époch, le contrat est insolvable, il est important de le restabiliser dès que possible. La solvabilité est restaurée via un mécanisme appelé « comptabilité de dette ». Chaque fois que le contrat est insolvable, la fonction `markDebt()` peut être appelée, par n'importe qui, en spécifiant une liste d'emprunteurs qui ont dépassé leurs allocations. Le montant par lequel le solde emprunté d'un emprunteur dépasse son allocation est appelé le montant du manque à gagner de l'emprunteur.

Lorsque la fonction `markDebt()` est appelée, le montant du manque à gagner de chaque emprunteur est déplacé de son solde emprunté vers un solde appelé solde de dette. Dans le même temps, le total de ces montants manquants est retiré des soldes inactifs des stakers et distribué en tant que reçus de dette des miseurs. Le solde inactif de chaque staker subira une décote et chaque staker recevra un montant équivalent sous forme de dette. De cette manière, la perte due à l'insolvabilité est socialisée (au prorata) sur tous les stakers détenant des soldes inactifs.

Ce processus est illustré ci-dessous :

![Default](<.. /.gitbook/assets/image (46).png>)

### Que représente la dette ?

En cas de défaut de l'emprunteur, le montant du manque à gagner (jusqu'à 100 % des soldes inactifs) est converti de solde inactif en solde débiteur (perte socialisée entre détenteurs de soldes inactifs). Le solde de la dette d'un staker n'autorise pas le staker à se retirer du pool d'USDC stakés - il doit être remboursé spécifiquement sous la forme de remboursements de la dette.

La dette représente un reçu pour l'USDC qui peut ensuite être remboursé pour l'USDC, soit lorsque l'emprunteur effectue un remboursement de la dette, soit via un autre moyen de récupération tel que déterminé par la gouvernance.

### Quels sont les recours dont disposent les stakers en cas de défaut d'un emprunteur ?

Les stakers et les emprunteurs sont parties au contrat de crédit renouvelable (lien [ici](https://dydx.foundation/revolving-credit-agreement)) qui vise à créer un accord exécutoire entre chaque staker et chaque emprunteur. De plus, le contrat intelligent Liquidity Staking Pool est conçu pour donner aux stakers un recours contre les emprunteurs, bien qu'il ne puisse pas garantir le remboursement.

Lorsque la fonction `markDebt\(\)` est appelée sur un emprunteur, cet emprunteur perd le droit d'emprunter des fonds supplémentaires du contrat. Ce droit peut être réintégré par la gouvernance.

Une fois que la dette a été « marquée », elle est retirée du système principal de comptabilité et peut être récupérée par les stakers de multiples façons. Si l'emprunteur endetté rembourse la dette (ou si une autre partie, telle que la gouvernance, la rembourse en son nom), les stakers à qui la dette était due peuvent récupérer les fonds selon le principe du premier arrivé, premier servi. Des solutions plus flexibles peuvent être mises en œuvre via l'interface « opérateur de dette » sur le contrat intelligent.

Ce qui se passe dans la pratique après que les stakers ont reçu une dette dépendra du contexte. S'il s'agissait d'une erreur honnête de la part d'un emprunteur agréé, les stakers peuvent s'attendre à être remboursés rapidement et intégralement. Si les fonds USDC étaient perdus, la gouvernance peut émettre un remboursement partiel aux miseurs touchés. Si la résolution est incertaine, la gouvernance peut choisir d'émettre un reçu ERC20 aux stakers concernés, leur permettant une liquidité instantanée en attendant une résolution. Si cela est jugé approprié, la gouvernance pourrait choisir d'émettre des paiements d'intérêts aux détenteurs de reçus jusqu'à ce qu'une résolution soit trouvée.

Tous ces cas sont fondamentalement pris en charge par le contrat de staking, mais la réponse appropriée doit être décidée et exécutée par la gouvernance dYdX. Selon la situation, cela peut nécessiter la rédaction et le déploiement d'un contrat intelligent périphérique.
