---
description: Aperçu du programme des récompenses de trading.
---

# Récompenses de trading

`25,00 %` de l'offre de jetons initiale (`250 000 000 DYDX`) ont été alloués pour être distribués aux utilisateurs trade sur le protocole de couche 2 dYdX sur la base des frais payés. Dans [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/8) en faveur d'une réduction.de trading de 25 %. Par conséquent, les récompenses de trading distribuées dans une Epoch donnée ont été réduites de 3 835 616 DYDX à 2 876 712 DYDX dans l'Epoch 15.

**Objectifs**

* Incitez tous les traders à utiliser le protocole de couche 2 de dYdX.
* Accélérez la liquidité du marché et l'utilisation globale des produits.

## **Aperçu**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Frais payés et récompenses estimées dans une Epoch donnée</p></figcaption></figure>

DYDX sera distribué aux traders sur la base des frais payés sur le protocole de layer 2 de dYdX. DYDX sera distribué sur une période de 28 jours sur cinq ans et n'est soumis à aucune acquisition ou blocage. 2 876 712 DYDX seront distribués par Epoch.

Grâce au vote de la communauté en faveur de la réduction des récompenses de trading de 25 %, les faisant passer de 3 835 616 DYDX à 2 876 712 DYDX, les 958 904 DYDX restants qui s'accumulent dans la trésorerie des récompenses peuvent être utilisés/dirigés par la communauté dYdX par le biais d'un [vote de gouvernance](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

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

Tous les traders sur le protocole dYdX de couche 2 sont admissibles pour recevoir DYDX en tant que récompenses commerciales.

Le protocole de couche 2 de dYdX n'est pas disponible pour les traders aux États-Unis ou dans les territoires restreints, tels que définis dans les [conditions d'utilisation](https://dydx.exchange/terms) de dYdX Trading Inc.

### Combien de DYDX ai-je gagné dans le cadre du programme de récompenses de trading ?

À l'époch actuelle, les utilisateurs peuvent voir les frais payés et les récompenses de trading estimées sur [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) où les données de trading des utilisateurs existent.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Frais payés et récompenses estimées dans une Epoch donnée</p></figcaption></figure>

Les récompenses des Epochs passées peuvent être consultées sur [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### Comment puis-je réclamer mes récompenses de trading ? Quand puis-je retirer et transférer mes DYDX gagnés ?

Les tokens DYDX gagnés via les récompenses de trading seront transférables à la fin de chaque époch. Les détenteurs de jetons DYDX doivent attendre environ `7 jours` (**période d'attente**) après la fin de l'époch pour réclamer leurs jetons. Une fois les tokens réclamés, ils peuvent être utilisés pour la gouvernance dYdX.

Les traders peuvent réclamer leurs récompenses de trading à la fin de chaque epoch, après la **période d'attente**, [ici](https://dydx.community/dashboard).

Les utilisateurs devront cliquer sur « Réclamer », signer une transaction et payer les frais de gaz pour réclamer DYDX.

![Aperçu du portefeuille des récompenses](../.gitbook/assets/1-portfolio-overview-rewards.png)
