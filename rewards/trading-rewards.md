---
description: Aperçu du programme des récompenses de trading.
---

# Récompenses de trading

`20,2` **`%`** (`201 883 560 $ethDYDX`) de l'offre de jetons est alloué pour être distribué aux utilisateurs qui font du trading sur dYdX v3 sur la base des frais payés. Initialement, `25,0 %` de la réserve de jetons (`250 000 000 $ethdYdX`) ont été alloués aux récompenses de trading.

* Dans [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/8) en faveur de la réduction des récompenses de trading de 25,0 %. En conséquence, l'allocation de récompenses de trading a baissé, passant de `25,0 %` à `20,2 %`.
* Dans [DIP20](https://dydx.community/dashboard/proposal/11), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/11) en faveur de la réduction des récompenses de trading de 45,0 % supplémentaires. En conséquence, l'allocation de récompenses de trading a baissé, passant de `20,2 %` à `14,5 %`.

Les récompenses de trading distribuées à une epoch donnée ont été réduites de 3 835 616 $ethDYDX à 2 876 712 $ethDYDX à l'epoch 15, et de 2 876 712 $ethDYDX à 1 582 192 $ethDYDX à l'epoch 21.

**Objectifs**

* Incitez tous les traders à utiliser dYdX v3.
* Accélérez la liquidité du marché et l'utilisation globale des produits.

## **Aperçu**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Frais payés et récompenses estimées dans une Epoch donnée</p></figcaption></figure>

$ethDYDX sera distribué aux traders sur la base des frais payés sur dYdX v3. $ethDYDX sera distribué sur une base d'epoch de 28 jours sur cinq ans et n'est pas soumis à des acquisitions ou des blocages. 1 582 192 ethDYDX seront distribués par epoch.

Avec le vote de la communauté pour procéder à une réduction de 25 % de récompenses de trading de 958 904 $ethDYDX dans [DIP16](https://dydx.community/dashboard/proposal/8), et 45 % de plus avec 1 294 520 $ethDYDX dans [DIP20](https://dydx.community/dashboard/proposal/11), les 2 253 424 $ethDYDX restants qui s'accumulent dans le Trésor des récompenses peuvent être utilisés/dirigés par la communauté dYdX avec un [vote de gouvernance](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k $$

| Terme | Définition |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | Récompense pour un trader spécifique. |
| R | Récompense totale à partager entre tous les traders dans le pool pour l'époch. |
| f | Frais totaux payés par un trader dans cette époch. |
| s | Score individuel des traders. |
| $${\sum\limits _{n} w_{n}}$$ | Somme de tous les scores des traders. |
| k | Nombre total de traders dans cette époch. |

Dans [DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md), la communauté dYdX a voté pour simplifier la formule afin qu'elle soit basée sur le total des frais payés par un trader à une Epoch donnée.

## FAQ

### Qui est admissible aux récompenses de trading ?

Tous les traders sur dYdX v3 sont admissibles pour recevoir $ethDYDX en tant que récompenses de trading.

dYdX v3 n'est pas disponible pour les traders aux États-Unis ou dans les territoires restreints, tels que définis dans les [conditions d'utilisation](https://dydx.exchange/terms) de dYdX Trading Inc.

### Combien de $ethDYDX ai-je gagné dans le cadre du programme de récompenses de trading ?

À l'époch actuelle, les utilisateurs peuvent voir les frais payés et les récompenses de trading estimées sur [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) où les données de trading des utilisateurs existent.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Frais payés et récompenses estimées dans une Epoch donnée</p></figcaption></figure>

Les récompenses des Epochs passées peuvent être consultées sur [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### Comment puis-je réclamer mes récompenses de trading ? À quel moment puis-je retirer et transférer les ethDYDX gagnés ?

Les jetons $ethDYDX gagnés via les récompenses de trading seront transférables à la fin de chaque epoch. Les détenteurs de jetons $ethDYDX sont tenus d'attendre environ `7 jours` (**période d'attente**) après la fin de l'epoch pour réclamer leurs jetons $ethDYDX.

Après la période d'attente de 7 jours, tout membre de la communauté peut appeler la fonction `Écrire` sur le paramètre `updateRoot` dans le [contrat du distributeur Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) pour rendre les récompenses $ethDYDX exigibles.

Étapes :

1. Sur la page [contrat du distributeur Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) sur Etherscan, cliquez sur l'onglet `Contrat` et sélectionnez `Ecrire en tant que Proxy.`
2. Cliquez sur le bouton `Se connecter à Web3` et connectez votre portefeuille Web3.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Faites défiler jusqu'au paramètre `updateRoot` et cliquez sur le bouton `Écrire`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Cette transaction nécessitera quelques ETH pour les frais de gaz et la transaction échouera si :**

* Le délai d'attente de 7 jours est toujours en vigueur, ou
* Un membre de la communauté a déjà appelé avec succès le paramètre `updateRoot` dans le [contrat du distributeur Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Une fois la transaction finalisée, les traders peuvent réclamer leurs récompenses de trading [ici](https://dydx.community/dashboard). Les utilisateurs devront cliquer sur `Réclamer`, signer une transaction et payer des frais de gaz pour réclamer $ethDYDX.

![Aperçu du portefeuille des récompenses](../.gitbook/assets/1-portfolio-overview-rewards.png)
