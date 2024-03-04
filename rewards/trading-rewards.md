---
description: Aperçu du programme des récompenses de trading.
---

# Récompenses de trading

`14,5` **`%`** (14`4 693 506 $ethDYDX`) de l'offre de jetons est allouée pour être distribuée aux utilisateurs qui négocient sur dYdX v3 en fonction des frais payés. Initialement, `25,0 %` de la réserve de jetons (`250 000 000 $ethdYdX`) ont été alloués aux récompenses de trading.

* Dans [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/8) en faveur de la réduction des récompenses de trading de 25,0 %. En conséquence, l'allocation de récompenses de trading a baissé, passant de `25,0 %` à `20,2 %`.
* En conséquence, l'allocation de récompenses de trading a baissé, passant de `20,2 %` à `14,5 %`.
*   

    *
    *
    *

    



*
*
*
*
* 0 $ethDYDX à l'Epoch 32 et après.

Après l'Epoch 31, il n'y aura pas de récompenses de trading sur dYdX v3. Dans le [DIP 29](https://dydx.community/dashboard/proposal/16) sur le dYdX v3 et [la Proposition 2](https://www.mintscan.io/dydx/proposals/2) sur le dYdX Chain, la communauté dYdX a voté pour créditer le montant restant des $ethDYDX non acquis dans le [Vester de trésorerie](https://etherscan.io/address/0xb9431e19b29b952d9358025f680077c3fd37292f) des récompenses du dYdX v3 au Vester de trésorerie des récompenses de la chaîne dYdX [`(dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)`](https://www.mintscan.io/dydx/address/dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk) et pour les distribuer ensuite comme récompenses d'échange sur la chaîne dYdX, sous réserve de l'approbation de la gouvernance de la chaîne dYdX.

**Objectifs**

* Incitez tous les traders à utiliser dYdX v3.
* Accélérez la liquidité du marché et l'utilisation globale des produits.

## **Aperçu**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Frais payés et récompenses estimées dans une Epoch donnée</p></figcaption></figure>

Auparavant, $ethDYDX était distribué aux traders sur la base des frais payés sur dYdX v3. $ethDYDX était distribué sur la base d'une période de 28 jours sur une période de cinq ans et n'était pas soumis à des conditions d'acquisition ou de blocage.

Dans [DIP 29](https://dydx.community/dashboard/proposal/16), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/16) pour réduire les récompenses de trading d'un ⅓ de l'Epoch 30-32 sur dYdX v3 aux valeurs suivantes :

*
* Epoch 31 : 527 398 $ethDYDX
*



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

Tous les traders de dYdX v3 pouvaient recevoir des $ethDYDX en guise de récompense.

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
