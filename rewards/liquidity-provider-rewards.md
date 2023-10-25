---
description: Aperçu du programme de récompenses des fournisseurs de liquidités.
---

# Récompenses des fournisseurs de liquidités

**5.2%** (`52,458,925 $DYDX`) de l'offre de jetons est alloué aux fournisseurs de liquidité ("LP") en fonction de formules qui récompensent une combinaison de volume de fabricant, de temps de disponibilité, de profondeur bilatérale, de spreads bid-ask et du nombre de marchés pris en charge. Initialemen**t, 7**,5`% (75,000,000 $D`YDX) de l'offre de jetons a été alloué pour les récompenses LP.

* Dan[s DIP ](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md)24, la communauté dYd[X a v](https://dydx.community/dashboard/proposal/14)oté pour réduire les récompenses des fournisseurs de `liquidité de 5`0 % de 1,150,6`85 DYDX par `époque à 575,343 DYDX par époque. En conséquence, l'allocation de récompenses de trading a baissé, passant de `7,5%` to `5,2%`.

**Objectifs**

* Améliorez la liquidité bilatérale et récompensez par programme les fournisseurs de liquidité.

## **Aperçu**

Pour encourager la liquidité du marché, $DYDX sera distribué aux fournisseurs de liquidité sur la base de formules de récompense en fonction de la participation aux marchés, le volume du maker, la profondeur bilatérale, la propagation (par rapport au marché intermédiaire) et la disponibilité sur le protocole de couche 2 de dYdX. Toute adresse Ethereum peut gagner ces récompenses, sous réserve d'un seuil de volume minimum du teneur de 0,25 % du volume du teneur à l'epoch précédente. La distribution de $DYDX se fera sur la base d'une Epoch de 28 jours, sur 5 ans et ne sera soumise à aucune acquisition ou aucun blocage. 575 343 DYDX $ seront distribués par Epoch.

Le calcul de la quantité de $DYDX à accorder à chaque fournisseur de liquidité par Epoch se fait à l'aide des fonctions suivantes. Dans [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), la communauté dYdX a voté pour réviser la formule de récompenses des fournisseurs de liquidité en divisant les fonctions pour les Marchés BTC/ETH et les marchés non BTC/ETH. Dans la [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md), la communauté dYdX a voté en faveur d'une réattribution du poids de 0,05 $stkDYDX à MakerVolume.

Dans l'ensemble, la pondération du volume des fonctions a été accrue sur tout les marchés. Le montant de $DYDX gagné est déterminé par la part relative de $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​) de chaque participant.

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Les ordres inférieurs à une certaine **profondeur minimale** (taille) ($$MinDepth$$) par marché sont exclus, et les ordres supérieurs à un certain **écart maximum** (écart de marché moyen) ($$MaxSpread$$) sont également exclus.

Les performances du fournisseur de liquidité sont surveillées et calculées minute par minute (à l'aide d'un échantillonnage aléatoire) et agrégées en un $$Q_{SCORE}$$ ($$Q_{FINAL}$$) pour un marché donné. Avec un échantillonnage minute par minute, chaque Epoch a 28 jours \* 24 heures \* 60 minutes de points de données, soit 40 320 points de données par Epoch au total.

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

### Qui est admissible aux récompenses des fournisseurs de liquidités ?

Tous les fournisseurs de liquidités ayant atteint un minimum de 0,25 % de volume du maker sur le protocole dYdX de couche 2 à l'Epoch précédente sont éligibles au versement de $DYDX à titre de récompense à une Epoch donnée.

Le protocole de couche 2 de dYdX n'est pas disponible pour les fournisseurs de liquidités aux États-Unis ou dans les territoires restreints, tels que définis dans les [conditions d'utilisation](https://dydx.exchange/terms) de dYdX Trading Inc.

### Combien de $DYDX ai-je gagné dans le cadre du programme de récompenses des fournisseurs de liquidité ?

À une Epoch donnée, les fournisseurs de liquidité gagnent un rendement en fonction de leur $$Q_{SCORE}$$ relatif sur le marché d'une paire donnée. Chaque paire a son propre montant de récompense relatif fixé par la gouvernance. Le montant attendu des DYDX gagnés est affiché dans le [tableau de bord des récompenses LP](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) et peut être déterminé en fonction du nombre de fournisseurs de liquidités impliqués, du $$${SCORE}$ relatif et du montant de la récompense disponible pour une paire donnée.

### Comment puis-je réclamer mes récompenses de fournisseur de liquidité ?

Les récompenses des fournisseurs de liquidités sont apparues dans l'[API dYdX](https://docs.dydx.exchange/). Bien qu'elles n'apparaissent pas sur l'interface utilisateur de gouvernance, elles peuvent toujours être réclamées via la gouvernance à la fin de chaque epoch [ici](https://dydx.community/dashboard).

### À quel moment puis-je retirer et transférer mes récompenses de fournisseur de liquidité $DYDX réclamées ?

Les jetons de $DYDX attribués via les récompenses de fournisseurs de liquidités peuvent être réclamés et transférés une fois la période de restriction de transfert initiale levée.

À partir de l'Epoch 1, les jetons de $DYDX attribués via les récompenses de fournisseurs de liquidité peuvent être réclamés dans les `7 jours` (période **d'attente**) qui suivent la fin de chaque Epoch.

### Comment la profondeur bilatérale, l'écart acheteur-vendeur et le temps de disponibilité sont-ils définis et mesurés ?

**Profondeur bilatérale**

Un fournisseur de liquidités bilatéral est une entreprise ou un individu qui cote activement des marchés bilatéraux sur le protocole de couche 2 de  dYdX, en fournissant des offres et des demandes pour un marché donné. Ils fournissent de la liquidité au protocole dans son ensemble.

Par exemple, un fournisseur de liquidité sur le marché BTC-USD peut fournir une cotation de 30 000 $ à 30 100 $, 10x50. Cela signifie qu'ils enchérissent (ils achèteront) 10 BTC pour 30 000 $ et offriront également (ils vendront) 50 BTC à 30 100 $. D'autres participants au marché peuvent alors acheter (lever l'offre) du fournisseur de liquidité à 30 100 $ ou lui vendre (atteindre l'offre) à 30 000 $.

Les fournisseurs de liquidité sont évalués sur leur capacité à fournir à la fois des offres et des demandes sur un marché donné. Les fournisseurs de liquidité qui ne fait une estimation de prix que d'un côté (soit uniquement des offres, soit des demandes) sont exclus de la réception des récompenses en raison de la fonction min().

**Écart moyen du marché**

Une mesure courante de la liquidité est l'écart acheteur-vendeur : l'écart entre le prix acheteur (ordre d'achat) le plus élevé et le prix vendeur (ordre de vente) le plus bas sur un marché. La différence entre l'offre et la demande, le spread, est le principal coût de transaction du trading (hors commissions), et il est collecté par le fournisseur de liquidité en traitant les ordres aux cours acheteur et vendeur. Le spread mesure le coût d'une transaction immédiate pour un utilisateur.

Le spread du marché moyen prend spécifiquement le point médian du marché. Avec cette formule, les ordres inférieurs au montant MinDepth pour chaque marché sont également exclus.

Par exemple, si le cours acheteur d'un fournisseur de liquidité pour BTC-USD est de 30 000 $ et le cours vendeur est de 30 100 $, alors l'écart acheteur-vendeur est de 100 $. Le prix moyen du marché est de 30 050 $ et le spread du marché moyen est de 50 $.

**Temps de disponibilité**

La disponibilité des fournisseurs de liquidité est essentielle pour les marchés, en particulier en période de forte volatilité. En appliquant un exposant de 5 à $$Uptime_{epoch}$$ comme entrée au $$Q_{FINAL}$$, les récompenses sont faussées vers les fournisseurs de liquidité qui maintiennent constamment une liquidité bilatérale. En d'autres termes, un fournisseur de liquidité qui fournit une disponibilité de 99 % du temps est exponentiellement plus précieux qu'un fournisseur de liquidité qui fournit une disponibilité de 90 %.

La disponibilité est définie comme le pourcentage de temps pendant lequel les ordres sont sur un marché donné fournissant de la liquidité minute par minute (avec échantillonnage aléatoire). La disponibilité exclut les périodes de temps pendant lesquelles des pannes existent sur le protocole de couche 2 de dYdX lui-même. Il peut y avoir des cas extrêmes où l'échange est lent ou n'accepte pas les ordres (mais n'est pas une panne) - auquel cas ce qui précède ne s'appliquerait pas (mais cela serait considéré comme un bogue et tous les fournisseurs de liquidités seraient affectés de la même manière, comme avec les pannes).

### Comment les spreads maximaux par marché sont-ils définis ?

Aucune $$Q_{BID}$$ ou $$Q_{ASK}$$ ne sera générée lorsque le spread est supérieur au $$MaxSpread$$ d'un marché donné.

Les spreads maximaux initiaux sont les suivants :

| Marché | Max Spread vs Mid-Market (offre et demande) |
| ----------------------- | -------------------------------------- |
| BTC-USD | 20 bps |
| ETH-USD | 20 bps |
| Autres marchés perpétuels | 40 bps |

### Comment la profondeur minimale (taille) par marché est-elle définie ?

Aucune $$Q_{BID}$$ ou $$Q_{ASK}$$ ne sera générée lorsque la taille est inférieure à la $$MinDepth$$ d'un marché donné.

Les profondeurs minimales initiales sont les suivantes :

| **Marché** | **Profondeur minimale (offre et demande)** |
| ----------------------- | --------------------------- |
| BTC-USD | 5000 $ |
| ETH-USD | 5000 $ |
| Autres marchés perpétuels | 1000 $ |
