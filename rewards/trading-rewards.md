---
description: Aperçu du programme des récompenses de trading.
---

# Récompenses de trading

`25,00 %` de l'offre initiale de jetons (`250 000 000 DYDX`) seront distribués aux utilisateurs qui tradent sur le protocole de couche 2 de dYdX sur la base d'une combinaison de frais payés et d'intérêts ouverts.

**Objectifs**

* Incitez tous les traders à utiliser le protocole de couche 2 de dYdX.
* Accélérez la liquidité du marché et l'utilisation globale des produits.

## **Aperçu**

![Earn rewards by trading on the dYdX Layer 2 Protocol](<.. /.gitbook/assets/image (17).png>)

DYDX sera distribué aux traders sur la base d'une formule qui récompense une combinaison de frais payés et d'intérêts ouverts sur le protocole de couche 2 de dYdX. DYDX sera distribué sur une période de 28 jours sur cinq ans et n'est soumis à aucune acquisition ou blocage. 3 835 616 DYDX seront distribués par époch.

La fonction Cobb-Douglas est utilisée pour calculer la quantité de DYDX attribuée à chaque trader à chaque époch :

![](../.gitbook/assets/math-20211221.png)

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k $$

| Terme | Définition |
| ---------------------------- | ------------------------------------------------------------------------------------------ |
| r | Récompense pour un trader spécifique. |
| R | Récompense totale à partager entre tous les traders dans le pool pour l'époch. |
| f | Frais totaux payés par un trader dans cette époch. |
| s | Score individuel des traders. |
| $${\sum\limits &lt;g id="1" ctype="italic" equiv-text="_"&gt;{n} w</g>{n}}$$ | Somme de tous les scores des traders. |
| j | L'intérêt ouvert moyen d'un trader (mesuré toutes les minutes) sur tous les marchés à cette époch. |
| k | Nombre total de traders dans cette époch. |
| g | Le stkDYDX moyen détenu par un trader (mesuré au hasard toutes les minutes) tout au long de l'époch |
| a | 0,67 |
| b | 0,28 |
| c | 0,05 |

## FAQ

### Qui est admissible aux récompenses de trading ?

Tous les traders sur le protocole dYdX de couche 2 sont admissibles pour recevoir DYDX en tant que récompenses commerciales.

Le protocole de couche 2 de dYdX n'est pas disponible pour les traders aux États-Unis ou dans les territoires restreints, tels que définis dans les [conditions d'utilisation](https://dydx.exchange/terms) de dYdX Trading Inc.

### Combien de DYDX ai-je gagné dans le cadre du programme de récompenses de trading ?

Dans l'époch actuelle, les utilisateurs peuvent voir les frais payés, l'intérêt ouvert moyen et les récompenses de trading estimées sur [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) où les données de trading des utilisateurs existent.

![Rewards info for the current epoch](<.. /.gitbook/assets/image (18).png>)

Les récompenses des épochs passées peuvent être consultées sur [**dydx.community/history/rewards**](https://dydx.community/history/rewards) **** (bientôt disponible).

### Comment puis-je réclamer mes récompenses de trading ? Quand puis-je retirer et transférer mes DYDX gagnés ?

Les jetons DYDX gagnés via les récompenses de trading seront transférables à la fin de chaque époch. Les détenteurs de jetons DYDX doivent attendre environ `7 jours` (**période d'attente**) après la fin de l'époch pour réclamer leurs jetons. Une fois les jetons réclamés, ils peuvent être utilisés pour la gouvernance dYdX.

Les traders peuvent réclamer leurs récompenses de trading à la fin de chaque époch, après la **période d'attente**, [ici](https://dydx.community/dashboard).

Les utilisateurs devront cliquer sur « Réclamer », signer une transaction et payer les frais de gaz pour réclamer DYDX.

![Portfolio overview of rewards](<.. /.gitbook/assets/image (20).png>)

### Qu'est-ce que l'intérêt ouvert ?

L'intérêt ouvert total est la valeur en USD de toutes les positions longues ou courtes en cours (le total des unités longues est toujours égal au total des unités courtes) pour un marché donné. L'augmentation de l'intérêt ouvert représente de l'argent nouveau ou supplémentaire entrant sur le marché, tandis que la diminution de l'intérêt ouvert indique de l'argent qui sort du marché.

Vous trouverez ci-dessous un tableau de l'activité de trading pour les traders, A, B, C, D et E. L'intérêt ouvert est calculé en termes USDC en fonction de l'activité de trading pour chaque jour :

| Temps | Activité de trading | Intérêt ouvert net total (USDC) |
| ------- | -------------------------------------------------------------------------- | ------------------------------ |
| 1er juillet | **Le trader A** achète 1 BTC à 30 000 $ et **le trader B** vend 1 BTC à 30 000 $ | 30 000 $ |
| 3 juillet | **Le trader C** achète 5 BTC au prix de 30 000 $ et **le trader D** vend 5 BTC au prix de 30 000 $ | 180 000 $ |
| 5 juillet | **Le trader A** vend 1 BTC à 30 000 $ et **le trader D** achète 1 BTC à 30 000 $ | 150 000 $ |
| 10 juillet | **Le trader E** achète 5 BTC au prix de 30 000 $ et **le trader C** vend 5 BTC au prix de 30 000 $ | 150 000 $ |

Dans le contexte de la formule **Récompenses de trading**, l'intérêt ouvert est mesuré chaque minute (à un moment aléatoire à chaque minute) sur tous les marchés et moyenné sur une époch donnée pour calculer les récompenses.

L'intérêt ouvert d'un trader est la valeur en USD de toutes les positions ouvertes de ce trader. Aux fins de **Recompenses de trading**, l'intérêt ouvert d'un trader est mesuré toutes les minutes (à un moment aléatoire à chaque minute) sur tous les marchés et moyenné sur une époch donnée.
