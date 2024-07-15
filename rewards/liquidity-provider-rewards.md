---
description: Aperçu du programme de récompenses des fournisseurs de liquidités.
---

#

Initialement, **7,5%** (`75,000,000 $ethDYDX`) de l'offre de jetons a été alloué pour les récompenses LP.

* Dans [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md), la communauté dYdX [a voté](https://dydx.community/dashboard/proposal/14) pour réduire les récompenses des fournisseurs de liquidité de 50 % de `1,150,685 $ethDYDX` par epoch à 575,343 `$ethDYDX` par epoch. En conséquence, l'allocation de récompenses de trading a baissé, passant de `7,5%` to `5,2%`.
*   

    *
    *
    *

    Après l'Epoch 31, il n'y aura pas de récompenses LP sur dYdX v3.

Comme il n'y a pas de distribution de récompenses de fournisseur de liquidité sur la chaîne dYdX, la communauté dYdX dans DIP 29 a voté pour migrer l'allocation restante pour les récompenses de fournisseur de liquidité vers le Trésor de la communauté de la chaîne dYdX.

**Objectifs**

* Améliorez la liquidité bilatérale et récompensez par programme les fournisseurs de liquidité.

## **Aperçu**

Pour encourager la liquidité du marché, $ethDYDX sera distribué aux fournisseurs de liquidité sur la base de formules de récompense en fonction de la participation aux marchés, le volume du maker, la profondeur bilatérale, la propagation (par rapport au marché intermédiaire) et la disponibilité sur dYdX v3.

Dans [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), la communauté dYdX a voté pour réviser la formule de récompenses des fournisseurs de liquidité en divisant les fonctions pour les Marchés BTC/ETH et les marchés non BTC/ETH. Dans le [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md), la communauté dYdX a voté pour réaffecter le poids de 0,05 stkDYDX à MakerVolume.

Le montant de ethDYDX gagné est déterminé par la part relative des $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​) de chaque participant.

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Les ordres inférieurs à une certaine **profondeur minimale** (taille) ($$MinDepth$$) par marché sont exclus, et les ordres supérieurs à un certain **écart maximum** (écart de marché moyen) ($$MaxSpread$$) sont également exclus.

Avec un échantillonnage minute par minute, chaque Epoch a 28 jours \* 24 heures \* 60 minutes de points de données, soit 40 320 points de données par Epoch au total.

Les fournisseurs de liquidité gagnent des récompenses mensuelles en fonction de leur part relative de $$Q_{FINAL}$$ par Epoch.

La formule ci-dessus est décomposée en calculs étape par étape ci-dessous pour plus de détails :

| _Volume du maker_ | Volume total du maker pour l'epoch. |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/1-qbid-formula.png" alt="" data-size="original"> | <p></p>Supposons qu'un fournisseur de liquidité ait plusieurs ordres d'achat ouverts (1 BTC à 29 900 $, 5 BTC à 29 850 $, 10 BTC à 29 500 $) sur le carnet d'ordres BTC-USD et que le BTC soit actuellement à 30 000 $ (basé sur le marché intermédiaire). Supposons que MinDepth est de 5 000 $ et que MaxSpread par rapport au marché intermédiaire est de 200 $, soit 67 points de base (200 $/30 000). Un BP est un centième de un pour cent.<br><p></p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29,900}{$100/30000}\right)) + (5\ \times \left(\frac{$29,850}{$150/3000}\right))</span><p></p><br><span class="math">Q_{BID}</span> est calculé chaque minute à l'aide d'un échantillonnage aléatoire.<br> |
| <img src="../.gitbook/assets/1-qask-formula.png" alt="" data-size="original"> | <p></p>Supposons qu'un fournisseur de liquidité ait plusieurs ordres de demande ouverts (0,1 BTC à 30 100 $, 5 BTC à 30 150 $, 10 BTC à 30 175 $) sur le carnet d'ordres BTC-USD et que BTC se négocie actuellement à 30 000 $ (basé sur le marché intermédiaire). Supposons que MinDepth est de 5 000 $ et que MaxSpread par rapport au marché intermédiaire est de 200 $, soit 67 points de base (200 $/30 000). Un BP est un centième de un pour cent.<p></p><span class="math">Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/300}\right))</span><p></p><br><span class="math">Q_{ASK}</span> est calculé chaque minute à un intervalle aléatoire. |
| <img src="../.gitbook/assets/1-qmin-formula.png" alt="" data-size="original"> | <p></p>Récompense la liquidité bilatérale en prenant le minimum de <span class="math">Q_{BID}</span> et <span class="math">Q_{ASK}</span>.<br><p></p>Calculé chaque minute. |
| <img src="../.gitbook/assets/1-qpoech-formula.png" alt="" data-size="original"> | $$Q_{EPOCH}$$ est la somme de toutes les $$Q_{MIN}$$ dans une epoch donnée. |
| <img src="../.gitbook/assets/1-q-uptime-epoch-formula.png" alt="" data-size="original"> | $$Uptime_{EPOCH}$$ est la durée d'une epoch pendant laquelle un teneur de marché donné était en direct et cotait à la fois du côté de l'offre et de la demande avec des tailles d'ordre supérieures au minimum d'ordre indiqué (noté ci-dessous par marché) et des spreads inférieurs au maximum indiqué spread (noté ci-dessous par marché). |
| <img src="../.gitbook/assets/1-qfinal-epoch-formula.png" alt="" data-size="original"> | $$Q_{FINAL}$$ normalise $$Q_{FINAL}$$ pour tenir compte de la disponibilité |

Chaque marché aura son propre pool de récompenses qui sera pondéré différemment. Dans le [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), la communauté dYdX a voté pour réduire l'allocation des récompenses totales en BTC-USD et en ETH-USDC à 10 % chacun. L'ensemble de pondérations appliqué à chaque marché est le suivant :

| Marché | % d'allocation du pool total de récompenses |
| ----------------------- | ---------------------------------------------------------------- |
| BTC-USD | 10 % |
| ETH-USD | 10 % |
| Autres marchés perpétuels | ![](../.gitbook/assets/1-other-perpetual-markets-lp-weights.png) |

## FAQ

<details>

<summary>Qui est admissible aux récompenses des fournisseurs de liquidités ?</summary>

Tous les fournisseurs de liquidités qui ont atteint un minimum de 0,25 % de volume de maker sur le protocole dYdX v3 à l'epoch précédente sont admissibles pour recevoir ethDYDX en tant que récompenses à une epoch donnée.

dYdX v3 n'est pas disponible pour les fournisseurs de liquidité aux États-Unis ou dans les territoires restreints, tels que définis dans les [conditions d'utilisation](https://dydx.exchange/terms) de dYdX Trading Inc.

</details>

<details>

<summary>Combien de $ethDYDX ai-je gagné dans le cadre du programme de récompenses des fournisseurs de liquidité ?</summary>

À une époch donnée, les fournisseurs de liquidité gagnent un rendement en fonction de leur $$Q_{SCORE}$$ relatif sur le marché d'une paire donnée. Chaque paire a son propre montant de récompense relatif fixé par la gouvernance. Le montant attendu des ethDYDX gagnés est affiché dans le [tableau de bord des récompenses LP](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) et peut être déterminé en fonction du nombre de fournisseurs de liquidités impliqués, du $$${SCORE}$ relatif et du montant de la récompense disponible pour une paire donnée.

</details>

<details>

<summary>Comment puis-je réclamer mes récompenses de fournisseur de liquidité ?</summary>

Les récompenses des fournisseurs de liquidités sont apparues dans l'[API dYdX](https://docs.dydx.exchange/). Bien qu'elles n'apparaissent pas sur l'interface utilisateur de gouvernance, elles peuvent toujours être réclamées via la gouvernance à la fin de chaque epoch [ici](https://dydx.community/dashboard).

</details>

<details>

<summary>Quand puis-je retirer et transférer mes récompenses de fournisseur de liquidité $ethDYDX réclamées ?</summary>

Les jetons de $ethDYDX attribués via les récompenses de fournisseurs de liquidités peuvent être réclamés et transférés une fois la période de restriction de transfert initiale levée.

À partir de l'epoch 1, les jetons de $ethDYDX attribués via les récompenses de fournisseurs de liquidité peuvent être réclamés dans les `7 jours` (**période d'attente**) qui suivent la fin de chaque epoch.

</details>

<details>

<summary>Comment la profondeur bilatérale, l'écart acheteur-vendeur et le temps de disponibilité sont-ils définis et mesurés ?</summary>

* **Profondeur bilatérale**



* **Écart moyen du marché**



* **Temps de disponibilité**

La disponibilité des fournisseurs de liquidité est essentielle pour les marchés, en particulier en période de forte volatilité. En appliquant un exposant de 5 à $$Uptime_{epoch}$$ comme entrée au $$Q_{FINAL}$$, les récompenses sont faussées vers les fournisseurs de liquidité qui maintiennent constamment une liquidité bilatérale. En d'autres termes, un fournisseur de liquidité qui fournit une disponibilité de 99 % du temps est exponentiellement plus précieux qu'un fournisseur de liquidité qui fournit une disponibilité de 90 %.



</details>

<details>

<summary>Comment les spreads maximaux par marché sont-ils définis ?</summary>

Aucune $$Q_{BID}$$ ou $$Q_{ASK}$$ ne sera générée lorsque le spread est supérieur au $$MaxSpread$$ d'un marché donné.

Les spreads maximaux initiaux sont les suivants :

*
*
*

</details>

<details>

<summary>Comment la profondeur minimale (taille) par marché est-elle définie ?</summary>

Aucune $$Q_{BID}$$ ou $$Q_{ASK}$$ ne sera générée lorsque la taille est inférieure à la $$MinDepth$$ d'un marché donné.

Les profondeurs minimales initiales sont les suivantes :

*
*
*

</details>

